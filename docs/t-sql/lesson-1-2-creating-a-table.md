---
title: Creazione di una tabella (esercitazione) | Microsoft Docs
ms.custom: 
ms.date: 04/18/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating tables
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 452150637ddf034ed1b69c2d0a32c9ad4c4e5977
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-1-2---creating-a-table"></a>Lezione 1-2 - Creazione di una tabella
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

Per creare una tabella, è necessario specificare un nome per la tabella e i nomi e i tipi di dati di ogni colonna di quest'ultima. È inoltre consigliabile indicare se sono consentiti valori Null in ogni colonna. Per creare una tabella è necessario avere l'autorizzazione `CREATE TABLE` e l'autorizzazione `ALTER SCHEMA` per lo schema che conterrà la tabella. Il ruolo predefinito del database `db_ddladmin` dispone di tali autorizzazioni.  
  
La maggior parte delle tabelle dispone di una chiave primaria costituita da una o più colonne. La chiave primaria è sempre univoca. In [!INCLUDE[ssDE](../includes/ssde-md.md)] è applicata la limitazione per la quale nessun valore di chiave primaria può essere ripetuto nella tabella.  
  
Per un elenco di tipi di dati e collegamenti alle relative descrizioni, vedere [Tipi di dati &#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> È possibile installare [!INCLUDE[ssDE](../includes/ssde-md.md)] in modo che venga fatta o meno distinzione tra maiuscole e minuscole. Se in [!INCLUDE[ssDE](../includes/ssde-md.md)] tale distinzione è rilevante, i nomi degli oggetti devono essere sempre indicati con le lettere maiuscole e minuscole appropriate. Una tabella denominata OrderData è ad esempio diversa da una tabella denominata ORDERDATA. Se nel [!INCLUDE[ssDE](../includes/ssde-md.md)] non viene fatta distinzione tra maiuscole e minuscole, tali nomi sono considerati equivalenti e quindi il nome stesso può essere utilizzato una sola volta.  
  
### <a name="to-create-a-database-to-contain-the-new-table"></a>Per creare un database in cui includere la nuova tabella  
  
-   Immettere il codice seguente in una finestra dell'editor di query.  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a>Connessione dell'editor di query al database TestData  
  
-   Nella finestra dell'editor di query digitare ed eseguire il codice seguente per connettersi al database `TestData` .  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### <a name="to-create-a-table"></a>Per creare una tabella  
  
-   Nell'editor di query digitare ed eseguire il codice seguente per creare una tabella semplice denominata `Products`. Le colonne nella tabella vengono denominate `ProductID`, `ProductName`, `Price`e `ProductDescription`. La colonna `ProductID` rappresenta la chiave primaria della tabella. `int`, `varchar(25)`, `money`e `text` sono tutti tipi di dati. Le uniche colonne che possono non contenere dati quando viene inserita o modificata un riga sono `Price` e `ProductionDescription` . Questa istruzione contiene un elemento facoltativo (`dbo.`) che corrisponde a uno schema. Lo schema rappresenta l'oggetto di database a cui appartiene la tabella. Se si è un amministratore, `dbo` è lo schema predefinito. `dbo` corrisponde al proprietario del database.  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Inserimento e aggiornamento di dati in una tabella &#40;Esercitazione&#41;](../t-sql/lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
## <a name="see-also"></a>Vedere anche  
[CREATE TABLE &#40;Transact-SQL&#41;](../t-sql/statements/create-table-transact-sql.md)  
  
  
  

