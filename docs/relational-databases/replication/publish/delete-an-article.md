---
title: "Eliminazione di un articolo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "articles [SQL Server replication], dropping"
  - "sp_droparticle"
  - "sp_dropmergearticle"
  - "deleting articles"
  - "removing articles"
  - "rimozione di articoli"
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Eliminazione di un articolo
  In questo argomento viene descritto come eliminare un articolo in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects). Per informazioni sulle condizioni in cui gli articoli possono essere eliminati e l'eliminazione di un articolo che richiede un nuovo snapshot o la reinizializzazione delle sottoscrizioni, vedere [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 **Contenuto dell'argomento**  
  
-   **Per eliminare un articolo tramite:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile eliminare gli articoli a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene l'articolo.  
  
#### Per eliminare un articolo da una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_droparticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md) Per eliminare un articolo, specificato da **@article**, da una pubblicazione, specificata da **@publication**. Specificare un valore di **1** di **@force_invalidate_snapshot**.  
  
2.  (Facoltativo) Per rimuovere completamente l'oggetto pubblicato dal database, eseguire il comando `DROP <objectname>` nel database di pubblicazione del server di pubblicazione.  
  
#### Per eliminare un articolo da una pubblicazione di tipo merge  
  
1.  Eseguire [sp_dropmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md) Per eliminare un articolo, specificato da **@article**, da una pubblicazione, specificata da **@publication**. Se necessario, specificare un valore di **1** per **@force_invalidate_snapshot** e il valore **1** per **@force_reinit_subscription**.  
  
2.  (Facoltativo) Per rimuovere completamente l'oggetto pubblicato dal database, eseguire il comando `DROP <objectname>` nel database di pubblicazione del server di pubblicazione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Nell'esempio seguente un articolo viene eliminato da una pubblicazione transazionale. Poiché questa modifica consente di invalidare lo snapshot esistente, il valore **1** specificato per il **@force_invalidate_snapshot** parametro.  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article AS sysname;  
SET @publication = N'AdvWorksProductTran';   
SET @article = N'Product';   
  
-- Drop the transactional article.  
USE [AdventureWorks]  
EXEC sp_droparticle   
  @publication = @publication,   
  @article = @article,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
 Nell'esempio seguente due articoli vengono eliminati da una pubblicazione di tipo merge. Poiché queste modifiche invalidano lo snapshot esistente, il valore **1** specificato per il **@force_invalidate_snapshot** parametro.  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article1 AS sysname;  
DECLARE @article2 AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @article1 = N'SalesOrderDetail';   
SET @article2 = N'SalesOrderHeader';   
  
-- Remove articles from a merge publication.  
USE [AdventureWorks]  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article1,  
  @force_invalidate_snapshot = 1;  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article2,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile eliminare articoli a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per l'eliminazione di un articolo dipendono dal tipo di pubblicazione cui appartiene l'articolo.  
  
#### Per eliminare un articolo che appartiene a una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransArticle> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare che l'articolo esista. Se il valore di questa proprietà è **false**, le proprietà dell'articolo non sono state definite in modo corretto nel passaggio 3 oppure l'articolo non esiste.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> metodo.  
  
7.  Chiudere tutte le connessioni.  
  
#### Per eliminare un articolo che appartiene a una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeArticle> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Controllare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> proprietà per verificare che l'articolo esista. Se il valore di questa proprietà è **false**, le proprietà dell'articolo non sono state definite in modo corretto nel passaggio 3 oppure l'articolo non esiste.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> metodo.  
  
7.  Chiudere tutte le connessioni.  
  
## Vedere anche  
 [Aggiunta ed eliminazione di articoli a e da pubblicazioni esistenti](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  