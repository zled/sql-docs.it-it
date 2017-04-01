---
title: "Definizione e modifica di un filtro di riga statico | Microsoft Docs"
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
  - "modifying filters, static row"
  - "static row filters"
  - "filtri [replica di SQL Server], filtro di riga statico"
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Definizione e modifica di un filtro di riga statico
  In questo argomento viene descritto come definire e modificare un filtro di riga statico in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per definire e modificare un filtro di riga statico, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si aggiunge, modifica o elimina un filtro di riga statico dopo che sono state inizializzate sottoscrizioni per la pubblicazione, è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni in seguito alla modifica. Per ulteriori informazioni sui requisiti per le modifiche alle proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
-   Se la pubblicazione è abilitata per la replica transazionale peer-to-peer, non sarà possibile filtrare le tabelle.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Poiché questi filtri sono statici, tutti i sottoscrittori riceveranno lo stesso subset di dati. Se è necessario filtrare dinamicamente le righe in un articolo di tabella appartenente a una tabella di tipo merge, in modo che ogni sottoscrittore riceva una partizione diversa dei dati, vedere [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md). La replica di tipo merge consente inoltre di filtrare righe correlate in base a un filtro di riga esistente. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Definire, modificare ed eliminare filtri di riga statici nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per definire un filtro di riga statico  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo azione intrapresa dipende dal tipo di pubblicazione:  
  
    -   Per una pubblicazione snapshot o transazionale, fare clic su **Aggiungi**.  
  
    -   Per una pubblicazione di tipo merge, fare clic su **Aggiungi**e quindi su **Aggiungi filtro**.  
  
2.  Nel **Aggiungi filtro** la finestra di dialogo, selezionare una tabella da filtrare dall'elenco a discesa.  
  
3.  Creare un'istruzione per il filtro nell'area di testo **Istruzione per il filtro** . È possibile digitare direttamente nell'area di testo nonché trascinare colonne dalla casella di riepilogo **Colonne** .  
  
    > [!NOTE]  
    >  Per la clausola WHERE è consigliabile usare nomi in due parti. I nomi in tre e quattro parti non sono supportati. Se la pubblicazione proviene da un server di pubblicazione Oracle, è necessario che la clausola WHERE sia conforme alla sintassi Oracle.  
  
    -   L'area di testo **Istruzione per il filtro** contiene il testo predefinito, nel formato seguente:  
  
        ```tsql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   Il testo predefinito non può essere modificato. Digitare la clausola di filtro dopo la parola chiave WHERE usando la sintassi SQL standard. La clausola di filtro completa sarà simile alla seguente:  
  
        ```tsql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   In un filtro di riga statico può essere inclusa una funzione definita dall'utente. La clausola di filtro completa per un filtro di riga statico con una funzione definita dall'utente sarà simile alla seguente:  
  
        ```tsql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per modificare un filtro di riga statico  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **modificare**.  
  
2.  Nella finestra di dialogo **Modifica filtro** modificare il filtro.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per eliminare un filtro di riga statico  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **eliminare**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Quando si creano articoli di tabella, è possibile definire una clausola WHERE per escludere le righe di un articolo. È inoltre possibile modificare un filtro di riga dopo che è stato definito. È possibile creare e modificare a livello di programmazione i filtri di riga statici tramite le stored procedure di replica.  
  
#### Per definire un filtro di riga statico per una pubblicazione snapshot o transazionale  
  
1.  Definire l'articolo da filtrare. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articlefilter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md). Specificare il nome dell'articolo per **@article**, il nome della pubblicazione per **@publication**, un nome per il filtro per **@filter_name**, e la clausola di filtro per **@filter_clause** (escluso `WHERE`).  
  
3.  Se non è ancora stato definito un filtro di colonna, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md). In caso contrario, eseguire [sp_articleview & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Specificare il nome della pubblicazione per **@publication**, il nome dell'articolo filtrato per **@article**, e la clausola di filtro specificata nel passaggio 2 per **@filter_clause**. Verranno creati gli oggetti di sincronizzazione per l'articolo filtrato.  
  
#### Per modificare un filtro di riga statico per una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articlefilter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md). Specificare il nome dell'articolo per **@article**, il nome della pubblicazione per **@publication**, un nome per il nuovo filtro per **@filter_name**, e la nuova clausola di filtro per **@filter_clause** (escluso `WHERE`). Poiché questa modifica invaliderà i dati nelle sottoscrizioni esistenti, specificare un valore di **1** per **@force_reinit_subscription**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articleview & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Specificare il nome della pubblicazione per **@publication**, il nome dell'articolo filtrato per **@article**, e la clausola di filtro specificata nel passaggio 1 per **@filter_clause**. Verrà ricreata la vista che definisce l'articolo filtrato.  
  
3.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
4.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Per eliminare un filtro di riga statico per una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articlefilter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md). Specificare il nome dell'articolo per **@article**, il nome della pubblicazione per **@publication**, un valore null per **@filter_name**, e un valore null per **@filter_clause**. Poiché questa modifica invaliderà i dati nelle sottoscrizioni esistenti, specificare un valore di **1** per **@force_reinit_subscription**.  
  
2.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
3.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Per definire un filtro di riga statico per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare la clausola di filtro per **@subset_filterclause** (escluso `WHERE`). Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Se non è ancora stato definito un filtro di colonna, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
#### Per modificare un filtro di riga statico per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare il nome della pubblicazione per **@publication**, il nome dell'articolo filtrato per **@article**, un valore di **subset_filterclause** per **@property**, e la nuova clausola di filtro per **@value** (escluso `WHERE`). Poiché questa modifica invaliderà i dati nelle sottoscrizioni esistenti, specificare un valore pari a 1 per **@force_reinit_subscription**.  
  
2.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
3.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio di replica transazionale l'articolo viene filtrato orizzontalmente per rimuovere tutti i prodotti non più supportati.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_1.sql)]  
  
 In questo esempio di replica di tipo merge gli articoli vengono filtrati orizzontalmente per restituire solo le righe che appartengono al venditore specificato. Viene utilizzato anche un filtro join. Per altre informazioni, vedere [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_2.sql)]  
  
## Vedere anche  
 [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtro dei dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtro dei dati pubblicati per la replica di tipo merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  