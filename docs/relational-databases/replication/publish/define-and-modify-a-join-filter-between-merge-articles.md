---
title: "Definizione e modifica di un filtro di join tra articoli di merge | Microsoft Docs"
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
  - "filtri [replica di SQL Server], join"
  - "filtri di join per replica di tipo merge [replica di SQL Server]"
  - "modifica dei filtri, join"
  - "filtri di join"
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Definizione e modifica di un filtro di join tra articoli di merge
  In questo argomento viene descritto come definire e modificare un filtro di join tra articoli di merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La replica di tipo merge supporta i filtri di join, solitamente utilizzati in combinazione con filtri con parametri per estendere il partizionamento della tabella ad altri articoli correlati.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per definire e modificare di un filtro di join tra articoli di merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Per creare un filtro di join, la pubblicazione deve contenere almeno due tabelle correlate. Dal momento che i filtri join rappresentano un'estensione dei filtri di riga, è necessario definire prima un filtro di riga in una tabella da estendere con un join a un'altra tabella. Dopo aver definito un filtro di join, è possibile estenderlo con un altro filtro di join se la pubblicazione contiene ulteriori tabelle correlate.  
  
-   Se si aggiunge, modifica o elimina un filtro di join dopo che sono state inizializzate sottoscrizioni per la pubblicazione, è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni in seguito alla modifica. Per ulteriori informazioni sui requisiti per le modifiche alle proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   È possibile creare manualmente filtri di join per un set di tabelle oppure generare automaticamente i filtri tramite la replica in base alle relazioni tra le chiavi esterne e le chiavi primarie definite nelle tabelle. Per ulteriori informazioni sulla generazione automatica di un set di filtri di join, vedere [Genera automaticamente un Set di Join filtri tra articoli di Merge & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Definire, modificare ed eliminare filtri di join nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per definire un filtro di join  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro di riga esistente o filtro di join **tabelle filtrate** riquadro.  
  
2.  Fare clic su **Aggiungi**e quindi su **Aggiungi join per estendere il filtro selezionato**.  
  
3.  Creare l'istruzione per il join. Selezionare **Per compilare l'istruzione verrà utilizzato il generatore** o **L'istruzione per il join verrà scritta manualmente**.  
  
    -   Se si sceglie di utilizzare il generatore, utilizzare le colonne nella griglia (**insieme**, **colonna tabella filtrata**, **operatore**, e **colonna della tabella unita in join**) per compilare un'istruzione join.  
  
         Ogni colonna della griglia contiene una casella combinata a discesa, che consente di selezionare due colonne e un operatore (**=**, **<>**, **<=**, **\<**, **>=**, **>**, e **come**). I risultati vengono visualizzati nell'area di testo **Anteprima** . Se il join include più di una coppia di colonne, selezionare una congiunzione (e o OR) dal **insieme** colonna, quindi immettere altre due colonne e un operatore.  
  
    -   Se si sceglie di scrivere manualmente l'istruzione per il join, digitarla nell'area di testo **Istruzione per il join** . Utilizzare le caselle di riepilogo **Colonne tabella filtrata** e **Colonne tabella unita in join** per trascinare le colonne nell'area di testo **Istruzione per il join** .  
  
    -   L'istruzione per il join completa sarà simile alla seguente:  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         Per la clausola JOIN è necessario utilizzare nomi composti da due parti, in quanto la denominazione a tre e quattro parti non è supportata.  
  
4.  Specificare le opzioni per il join:  
  
    -   Se la colonna in cui creare un join della tabella filtrata (tabella padre) è univoca, selezionare **chiave univoca**.  
  
        > [!CAUTION]  
        >  Selezionando questa opzione si indica che la relazione tra la tabella padre e le tabelle figlio in un filtro join è uno-a-uno o uno-a-molti. Utilizzare questa opzione solo se esiste un vincolo nella colonna di join della tabella figlio che garantisce l'univocità. Se l'opzione è impostata in modo errato può impedire la convergenza dei dati.  
  
    -   Per impostazione predefinita, durante la sincronizzazione la replica di tipo merge elabora le modifiche riga per riga. Per avere relative modifiche nelle righe della tabella filtrata sia la tabella unita in join elaborate come unità, selezionare **record logici** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e solo le versioni successive). Questa opzione è disponibile solo se sono soddisfatti i requisiti relativi all'utilizzo dei record logici negli articoli e nelle pubblicazioni. Per ulteriori informazioni vedere la sezione "Considerazioni sull'utilizzo dei record logici" in [modifiche a un gruppo di righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per modificare un filtro join  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **filtro righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **modificare**.  
  
2.  Nella finestra di dialogo **Modifica join** modificare il filtro.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per eliminare un filtro join  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **eliminare**. Se il filtro di join eliminato è esteso da altri join, anch'essi verranno eliminati.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Tali procedure indicano un filtro con parametri su un articolo padre con filtri di join tra questo articolo e gli articoli figlio correlati. I filtri join possono essere definiti e modificati a livello di programmazione tramite le stored procedure di replica.  
  
#### Per definire un filtro join per estendere un filtro di articolo agli articoli correlati in una pubblicazione di tipo merge  
  
1.  Definire il filtro per l'articolo da unire in join, ovvero l'articolo padre.  
  
    -   Per un articolo a cui viene applicato un filtro di riga con parametri, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
    -   Per un articolo a cui viene applicato un filtro di riga statico, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per definire uno o più articoli correlati, che sono anche noti come gli articoli figlio, per la pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergefilter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Specificare **@publication**, un nome univoco per questo filtro per **@filtername**, il nome dell'articolo figlio creato nel passaggio 2 per **@article**, il nome dell'articolo padre viene aggiunto per **@join_articlename**, e uno dei seguenti valori per **@join_unique_key**:  
  
    -   **0** -indica un join molti-a-uno o molti-a-molti tra gli articoli padre e figlio.  
  
    -   **1** -indica un join uno a uno o uno-a-molti tra gli articoli padre e figlio.  
  
     In questo modo viene definito un filtro join tra i due articoli.  
  
    > [!CAUTION]  
    >  Impostare solo **@join_unique_key** a **1** Se si dispone di un vincolo nella colonna di join della tabella sottostante per l'articolo padre che garantisce l'univocità. Se **@join_unique_key** è impostato su **1** in modo non corretto, può verificarsi non convergenza dei dati.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene definito un articolo per una pubblicazione di tipo merge, in cui all'articolo della tabella `SalesOrderDetail` viene applicato un filtro sulla tabella `SalesOrderHeader` , che presenta essa stessa un filtro di riga statico. Per altre informazioni, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-join_1.sql)]  
  
 In questo esempio definisce un gruppo di articoli in una pubblicazione di tipo merge in cui vengono filtrati gli articoli con una serie di filtri join sul `Employee` tabella stessa un filtro di riga con parametri con il valore di [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) nel **LoginID** colonna. Per altre informazioni, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-join_2.sql)]  
  
## Vedere anche  
 [Filtri join](../../../relational-databases/replication/merge/join-filters.md)   
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtro dei dati pubblicati per la replica di tipo merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)   
 [Procedura: Definizione e modifica di un filtro join tra articoli di merge (SQL Server Management Studio)](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Definizione di una relazione tra record logici degli articoli di tabelle di merge](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  