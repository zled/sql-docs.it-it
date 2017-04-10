---
title: "Definizione e modifica di un filtro di riga con parametri per un articolo di merge | Microsoft Docs"
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
  - "filtri con parametri [replica di SQL Server], definizione"
  - "filtri con parametri [replica di SQL Server], modifica"
  - "replica di tipo merge [replica di SQL Server], filtri dinamici"
  - "filtri con parametri per replica di tipo merge [replica di SQL Server]"
  - "filtri [replica di SQL Server], con parametri"
  - "modifica di filtri, riga con parametri"
  - "filtri dinamici [replica di SQL Server]"
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Definizione e modifica di un filtro di riga con parametri per un articolo di merge
  In questo argomento viene descritto come definire e modificare un filtro di riga con parametri in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Quando si creano articoli di tabella, è possibile usare filtri di riga con parametri. Questi filtri usano una [in](../../../t-sql/queries/where-transact-sql.md) clausola per selezionare i dati appropriati per la pubblicazione. Anziché specificare un valore letterale nella clausola (come avviene con un filtro di riga statico), si specificano una o entrambe le seguenti funzioni di sistema: [SUSER_SNAME](../../../t-sql/functions/suser-sname-transact-sql.md) e [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md). Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per definire e modificare un filtro di riga con parametri, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si aggiunge, modifica o elimina un filtro di riga con parametri dopo che sono state inizializzate sottoscrizioni per la pubblicazione, è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni in seguito alla modifica. Per ulteriori informazioni sui requisiti per le modifiche alle proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Per motivi relativi alle prestazioni è consigliabile evitare di applicare funzioni ai nomi di colonna nelle clausole per filtri di riga con parametri, come `LEFT([MyColumn]) = SUSER_SNAME()`. Se si usano HOST_NAME in una clausola di filtro e si sostituisce il valore HOST_NAME, può essere necessario convertire i tipi di dati tramite l'istruzione CONVERT. Per ulteriori informazioni sulle procedure consigliate in questo caso, vedere la sezione "Si esegue l'override del valore di HOST_NAME ()" nell'argomento [i filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Definire, modificare ed eliminare filtri di riga con parametri in di **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina del **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per definire un filtro di riga con parametri  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, fare clic su **Aggiungi**, e quindi fare clic su **Aggiungi filtro**.  
  
2.  Nel **Aggiungi filtro** la finestra di dialogo, selezionare una tabella da filtrare dall'elenco a discesa.  
  
3.  Creare un'istruzione di filtro nella casella di testo **Istruzione per il filtro** . È possibile digitare direttamente nell'area di testo nonché trascinare colonne dalla casella di riepilogo **Colonne** .  
  
    -   L'area di testo **Istruzione per il filtro** contiene il testo predefinito, nel formato seguente:  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   Il testo predefinito non può essere modificato. Digitare la clausola di filtro dopo la parola chiave WHERE usando la sintassi SQL standard. Un filtro con parametri include una chiamata alla funzione di sistema **HOST_NAME ()** e/o **SUSER_SNAME ()**, o una funzione definita dall'utente che fa riferimento a una o entrambe queste funzioni. Di seguito è riportato un esempio di una clausola di filtro completa per un filtro di riga con parametri:  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         Per la clausola WHERE è consigliabile usare nomi in due parti. I nomi in tre e quattro parti non sono supportati.  
  
4.  Selezionare l'opzione corrispondente alla modalità desiderata di condivisione dei dati tra i Sottoscrittori:  
  
    -   **Una riga di questa tabella verrà inviata a più sottoscrizioni**  
  
    -   **Una riga di questa tabella verrà inviata a una sola sottoscrizione**  
  
     Selezionando **Una riga di questa tabella verrà inviata a una sola sottoscrizione**è possibile ottimizzare le prestazioni della replica di tipo merge archiviando ed elaborando una minore quantità di metadati. È tuttavia necessario garantire che i dati vengano partizionati in modo da non consentire la replica di una riga in più Sottoscrittori. Per altre informazioni, vedere la sezione relativa all'impostazione delle opzioni delle partizioni nell'argomento [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per modificare un filtro di riga con parametri  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **filtro righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **modificare**.  
  
2.  Nella finestra di dialogo **Modifica filtro** modificare il filtro.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per eliminare un filtro di riga con parametri  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **eliminare**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile creare e modificare a livello di programmazione i filtri di riga con parametri tramite le stored procedure di replica.  
  
#### Per definire un filtro di riga con parametri per un articolo in una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare **@publication**, un nome per l'articolo per **@article**, la tabella da pubblicare per **@source_object**, la clausola WHERE che definisce il filtro con parametri per **@subset_filterclause** (escluso `WHERE`), e uno dei seguenti valori per **@partition_options**, che descrive il tipo di partizionamento che verrà generato dal filtro di riga con parametri:  
  
    -   **0** : il filtro per l'articolo è statico oppure non restituisce un subset univoco dei dati per ogni partizione (partizione "sovrapposta").  
  
    -   **1** - partizioni risultante sono sovrapposte e gli aggiornamenti apportati nel Sottoscrittore non possono modificare la partizione a cui appartiene una riga.  
  
    -   **2** : filtro dell'articolo restituisce partizioni non sovrapposte, ma più sottoscrittori ricevono la stessa partizione.  
  
    -   **3** : il filtro per l'articolo restituisce partizioni non sovrapposte sono univoche per ogni sottoscrizione.  
  
#### Per modificare un filtro di riga con parametri per un articolo in una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare **@publication**, **@article**, un valore di **subset_filterclause** per **@property**, l'espressione che definisce il filtro con parametri per **@value** (escluso `WHERE`) e il valore **1** per entrambi **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
2.  Se questa modifica determina un comportamento di partizionamento diverso, quindi eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) nuovamente. Specificare **@publication**, **@article**, un valore di **partition_options** per **@property**, e l'opzione di partizionamento più appropriata per **@value**, che può essere uno dei seguenti:  
  
    -   **0** : il filtro per l'articolo è statico oppure non restituisce un subset univoco dei dati per ogni partizione (partizione "sovrapposta").  
  
    -   **1** - partizioni risultante sono sovrapposte e gli aggiornamenti apportati nel Sottoscrittore non possono modificare la partizione a cui appartiene una riga.  
  
    -   **2** : filtro dell'articolo restituisce partizioni non sovrapposte, ma più sottoscrittori ricevono la stessa partizione.  
  
    -   **3** : il filtro per l'articolo restituisce partizioni non sovrapposte sono univoche per ogni sottoscrizione.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio definisce un gruppo di articoli in una pubblicazione di tipo merge in cui vengono filtrati gli articoli con una serie di filtri join sul `Employee` tabella che è essa stessa un filtro di riga con parametri in di **LoginID** colonna. Durante la sincronizzazione, il valore restituito dal [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) funzione è sottoposta a override. Per ulteriori informazioni, vedere l'override del valore di HOST_NAME () nell'argomento [i filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-para_1.sql)]  
  
## Vedere anche  
 [Definizione e modifica di un filtro di join tra articoli di merge](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtri join](../../../relational-databases/replication/merge/join-filters.md)   
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  