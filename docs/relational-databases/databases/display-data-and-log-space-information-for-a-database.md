---
title: "Visualizzare le informazioni sullo spazio allocato ai dati e ai log per un database | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "log [SQL Server], spazio"
  - "informazioni sullo stato [SQL Server], spazio"
  - "visualizzazione di informazioni sullo spazio"
  - "spazio su disco [SQL Server], visualizzazione"
  - "database [SQL Server], spazio utilizzato"
  - "visualizzazione di informazioni sullo spazio"
  - "allocazione dello spazio [SQL Server], visualizzazione"
  - "spazio dei dati [SQL Server]"
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Visualizzare le informazioni sullo spazio allocato ai dati e ai log per un database
  In questo argomento si illustra come visualizzare le informazioni sullo spazio allocato ai dati e ai log per un database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  

  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 L'autorizzazione per eseguire **sp_spaceused** è concessa al ruolo **public**. Solo i membri del ruolo predefinito del database **db_owner** possono specificare il parametro **@updateusage**.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per visualizzare le informazioni sullo spazio allocato ai dati e ai log per un database  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , quindi espanderla.  
  
2.  Espandere **Database**.  
  
3.  Fare clic con il pulsante destro del mouse su un database, scegliere **Report**, **Report standard**, quindi fare clic su **Utilizzo disco**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per visualizzare le informazioni sullo spazio allocato ai dati e ai log per un database utilizzando sp_spaceused  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene usata la stored procedure di sistema [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) per fornire le informazioni sullo spazio su disco per la tabella `Vendor` e i relativi indici.  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### Per visualizzare le informazioni sullo spazio allocato ai dati e ai log per un database eseguendo una query su sys.database_files  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si esegue una query sulla vista del catalogo [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) per restituire informazioni specifiche sui file di dati e di log nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [Aggiungere file di dati o file di log a un database](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Eliminare file di dati o file di log da un database](../../relational-databases/databases/delete-data-or-log-files-from-a-database.md)  
  
  