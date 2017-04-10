---
title: "Impostazione del livello di compatibilit&#224; per le pubblicazioni di tipo merge | Microsoft Docs"
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
  - "compatibility [SQL Server], replication"
  - "backward compatibility [SQL Server], replication"
  - "pubblicazioni [replica di SQL Server], compatibilità con versioni precedenti"
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Impostazione del livello di compatibilit&#224; per le pubblicazioni di tipo merge
  In questo argomento si illustra come impostare il livello di compatibilità per le pubblicazioni di tipo merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Il livello di compatibilità delle pubblicazioni viene utilizzato nella replica di tipo merge per determinare le funzionalità che possono essere utilizzate dalle pubblicazioni in un determinato database.  
  
 **Contenuto dell'argomento**  
  
-   **Per impostare il livello di compatibilità per le pubblicazioni di tipo merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Impostare il livello di compatibilità nella pagina **Tipi di Sottoscrittore** della Creazione guidata nuova pubblicazione. Per ulteriori informazioni sull'accesso a questa procedura guidata, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md). Dopo la creazione di uno snapshot della pubblicazione, il livello di compatibilità può essere incrementato, ma non ridotto. Aumentare il livello di compatibilità sul **Generale** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Incrementando il livello di compatibilità della pubblicazione, qualsiasi sottoscrizione esistente in server che eseguono versioni che risultano precedenti a tale livello di compatibilità non saranno più in grado di eseguire la sincronizzazione.  
  
> [!NOTE]  
>  Poiché il livello di compatibilità influisce su altre proprietà della pubblicazione e sugli articoli per cui tali proprietà sono valide, non modificare il livello di compatibilità e le altre proprietà in un'unica operazione all'interno della finestra di dialogo. Dopo la modifica della proprietà, lo snapshot per la pubblicazione dovrà essere rigenerato.  
  
#### Per impostare il livello di compatibilità della pubblicazione  
  
-   Nella pagina **Tipi di Sottoscrittore** della Creazione guidata nuova pubblicazione selezionare i tipi di Sottoscrittori che la pubblicazione dovrà supportare.  
  
#### Per incrementare il livello di compatibilità della pubblicazione  
  
-   Nel **Generale** pagina della **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo per **il livello di compatibilità**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile impostare il livello di compatibilità per una pubblicazione di tipo merge a livello di programmazione codice quando una pubblicazione viene creata o modificata a livello di programmazione in un secondo momento. Per impostare o modificare questa proprietà di pubblicazione, è possibile utilizzare le stored procedure di replica.  
  
#### Per impostare il livello di compatibilità per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione, eseguire [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), specificando un valore per **@publication_compatibility_level** per rendere la pubblicazione compatibile con le versioni precedenti di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Per modificare il livello di compatibilità di una pubblicazione di tipo merge  
  
1.  Eseguire [sp_changemergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando **publication_compatibility_level** per **@property** e il livello di compatibilità appropriati per **@value**.  
  
#### Per determinare il livello di compatibilità di una pubblicazione di tipo merge  
  
1.  Eseguire [sp_helpmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), specificando la pubblicazione desiderata.  
  
2.  Individuare il livello di compatibilità nel **backward_comp_level** colonna nel set di risultati.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene creata una pubblicazione di tipo merge e viene impostato il livello di compatibilità della pubblicazione.  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 In questo esempio viene modificato il livello di compatibilità per la pubblicazione di tipo merge.  
  
> [!NOTE]  
>  È possibile che la modifica del livello di compatibilità della pubblicazione non sia consentita se nella pubblicazione vengono utilizzate caratteristiche che richiedono un livello di compatibilità specifico. Per ulteriori informazioni, vedere [compatibilità con le versioni precedenti della replica](../../../relational-databases/replication/replication-backward-compatibility.md).  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 In questo esempio viene restituito il livello di compatibilità corrente per la pubblicazione di tipo merge.  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md)  
  
  