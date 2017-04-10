---
title: "Ottimizzazione dei filtri di riga con parametri | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partizioni pre-calcolate [replica di SQL Server]"
  - "filtri [replica di SQL Server], con parametri"
  - "partizioni pre-calcolate della replica di tipo merge [replica di SQL Server], SQL Server Management Studio"
  - "filtri con parametri [replica di SQL Server], ottimizzazione"
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Ottimizzazione dei filtri di riga con parametri
  In questo argomento si descrive come ottimizzare i filtri di riga con parametri in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per ottimizzare i filtri di riga con parametri, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Quando si utilizzano filtri con parametri, è possibile controllare in che modo i filtri vengono elaborati dalla replica di tipo merge specificando l'opzione **use partition groups** o **keep partition changes** durante la creazione di una pubblicazione. Queste opzioni consentono di migliorare le prestazioni di sincronizzazione delle pubblicazioni con gli articoli filtrati tramite l'archiviazione di metadati aggiuntivi nel database di pubblicazione. È possibile controllare la modalità di condivisione dei dati tra i Sottoscrittori impostando l'opzione **partition options** durante la creazione di un articolo. Per altre informazioni su tali requisiti, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
     Con i Sottoscrittori [!INCLUDE[ssEW](../../../includes/ssew-md.md)], keep_partition_changes deve essere impostato su true per assicurarsi che le eliminazioni vengano propagate correttamente. Se impostato su false, nel Sottoscrittore potrebbero essere presenti più righe rispetto al previsto.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 È possibile utilizzare le impostazioni seguenti per ottimizzare i filtri di riga con parametri:  
  
 **Opzioni partizioni**  
 Impostare questa opzione per la **proprietà** pagina della **Proprietà articolo - \< articolo>** nella finestra di dialogo o nel **Aggiungi filtro** la finestra di dialogo. Entrambe le finestre di dialogo sono disponibili nella creazione guidata pubblicazione e la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Il **Proprietà articolo - \< articolo>** la finestra di dialogo consente di specificare altri valori per questa opzione che non sono disponibili nel **Aggiungi filtro** la finestra di dialogo.  
  
 **Pre-calcola partizioni**  
 Questa opzione è impostata su **True** per impostazione predefinita se gli articoli nella pubblicazione sono conformi a un set di requisiti. Per ulteriori informazioni su questi requisiti, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md). Modificare questa opzione sul **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
 **Ottimizza sincronizzazione**  
 Questa opzione deve essere impostata su **True** solo se **Pre-calcola partizioni** è impostato su **False**. Impostare questa opzione per il **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
 Per ulteriori informazioni sull'utilizzo di creazione guidata pubblicazione e l'accesso di **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per impostare le opzioni delle partizioni nella finestra di dialogo Aggiungi filtro o Modifica filtro  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo fare clic su **Aggiungi**, e quindi fare clic su **Aggiungi filtro**.  
  
2.  Creare un filtro con parametri. Per altre informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
3.  Selezionare l'opzione corrispondente alla modalità desiderata di condivisione dei dati tra i Sottoscrittori:  
  
    -   **Una riga di questa tabella verrà inviata a più sottoscrizioni**  
  
    -   **Una riga di questa tabella verrà inviata a una sola sottoscrizione**  
  
     Selezionando **Una riga di questa tabella verrà inviata a una sola sottoscrizione**è possibile ottimizzare le prestazioni della replica di tipo merge archiviando ed elaborando una minore quantità di metadati. È tuttavia necessario garantire che i dati vengano partizionati in modo da non consentire la replica di una riga in più Sottoscrittori. Per altre informazioni, vedere la sezione relativa all'impostazione delle opzioni delle partizioni nell'argomento [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per impostare le opzioni di partizione nella finestra Proprietà articolo - \< articolo> la finestra di dialogo  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella e quindi fare clic su **Proprietà articolo**.  
  
2.  Fare clic su **Imposta proprietà dell'articolo di tabelle evidenziato** o su **Imposta proprietà di tutti gli articoli di tabelle**.  
  
3.  Nel **oggetto di destinazione** sezione il **proprietà** scheda del **Proprietà articolo - \< articolo>** finestra di dialogo specificare uno dei valori seguenti per **Opzioni partizioni**:  
  
    -   **Sovrapposte**  
  
    -   **Sovrapposte, non ammesse modifiche dei dati fuori partizione**  
  
    -   **Non sovrapposte, sottoscrizione unica**  
  
    -   **Non sovrapposte, condivise dalle sottoscrizioni**  
  
     Per ulteriori informazioni su queste opzioni e sulla loro relazione con le opzioni disponibili nelle finestre di dialogo **Aggiungi filtro** e **Modifica filtro** , vedere la sezione relativa all'impostazione delle opzioni partizioni nell'argomento [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per impostare Pre-calcola partizioni  
  
1.  Nel **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un valore per il **Pre-calcola partizioni** opzione. Questa proprietà è in sola lettura se:  
  
    -   La pubblicazione non soddisfa i requisiti delle partizioni pre-calcolate.  
  
    -   Non è ancora stato generato lo snapshot per la pubblicazione. In questo caso, l'opzione visualizza il valore **Imposta automaticamente alla creazione di uno snapshot**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per impostare Ottimizza sincronizzazione  
  
1.  Nel **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un valore di **True** per il **Ottimizza sincronizzazione** opzione.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Per le definizioni delle opzioni di filtro per **@keep_partition_changes** e **@use_partition_groups**, vedere [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
#### Per specificare le ottimizzazioni del filtro di merge durante la creazione di una nuova pubblicazione  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Specificare **@publication** e il valore **true** per uno dei parametri seguenti:  
  
    -   **@use_partition_groups**:-l'ottimizzazione delle prestazioni più elevato, purché gli articoli siano conformi ai requisiti per le partizioni precalcolate. Per ulteriori informazioni, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   **@keep_partition_changes** -utilizzare questa ottimizzazione se non possono utilizzare partizioni precalcolate.  
  
2.  Aggiungere un processo snapshot per la pubblicazione. Per ulteriori informazioni vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), specificando i parametri seguenti:  
  
    -   **@publication** -il nome della pubblicazione ottenuto al passaggio 1.  
  
    -   **@article** -un nome per l'articolo  
  
    -   **@source_object** - l'oggetto di database da pubblicare.  
  
    -   **@subset_filterclause** -la clausola di filtro con parametri facoltativa utilizzata per filtrare in senso orizzontale l'articolo.  
  
    -   **@partition_options** -le opzioni di partizione per l'articolo filtrato.  
  
4.  Ripetere il passaggio 3 per ogni articolo della pubblicazione.  
  
5.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) per definire un filtro di join tra due articoli. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
#### Per visualizzare e modificare i comportamenti del filtro di merge per una pubblicazione esistente  
  
1.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), specificando **@publication**. Prendere nota del valore di **keep_partition_changes** e **use_partition_groups** nel set di risultati.  
  
2.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Specificare un valore di **use_partition_groups** per **@property** e **true** o **false** per **@value**.  
  
3.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Specificare un valore di **keep_partition_changes** per **@property** e **true** o **false** per **@value**.  
  
    > [!NOTE]  
    >  Quando si abilita **keep_partition_changes**, è prima necessario disattivare **use_partition_groups** e specificare un valore di **1** per **@force_reinit_subscription**.  
  
4.  (Facoltativo) Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **partition_options** per **@property** e il valore appropriato per **@value**. Vedere [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) per le definizioni di queste opzioni di filtro.  
  
5.  (Facoltativo) Avviare l'agente snapshot per rigenerare lo snapshot se necessario. Per informazioni sulle modifiche necessarie a generare un nuovo snapshot, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## Vedere anche  
 [Generare automaticamente un Set di filtri Join tra articoli di Merge & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md)   
 [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  