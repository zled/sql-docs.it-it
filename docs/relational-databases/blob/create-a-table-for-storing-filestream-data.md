---
title: "Creazione di una tabella per archiviare dati FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], archiviazione tabelle"
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# Creazione di una tabella per archiviare dati FILESTREAM
  In questo argomento viene illustrato come creare una tabella per archiviare dati FILESTREAM.  
  
 Quando il database presenta un filegroup FILESTREAM, è possibile creare o modificare tabelle per archiviare i dati FILESTREAM. Per specificare che una colonna contiene dati FILESTREAM, creare una colonna **varbinary(max)** e aggiungere l'attributo FILESTREAM.  
  
### Per creare una tabella per archiviare dati FILESTREAM  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic su **Nuova query** per visualizzare l'editor di query.  
  
2.  Copiare il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] dall'esempio seguente e incollarlo nell'Editor di query. Tramite il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] viene creata una tabella abilitata per FILESTREAM denominata Records.  
  
3.  Per creare la tabella, fare clic su **Esegui**.  
  
## Esempio  
 Nel codice di esempio seguente viene descritto come creare una tabella denominata `Records`. La colonna `Id` è una colonna `ROWGUIDCOL` ed è necessaria per utilizzare dati FILESTREAM con API Win32. La colonna `SerialNumber` è di tipo `UNIQUE INTEGER`. La colonna `Chart` è una colonna `FILESTREAM` e viene utilizzata per archiviare `Chart` nel file system.  
  
> [!NOTE]  
>  Questo esempio fa riferimento al database Archive creato in [Creazione di un database abilitato per FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../relational-databases/blob/codesnippet/tsql/create-a-table-for-stori_1.sql)]  
  
## Vedere anche  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  