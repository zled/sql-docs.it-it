---
title: Spostare un database abilitato per FILESTREAM | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: blob
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1fd75815f23a483bdc3ac407929e411283778b5
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="move-a-filestream-enabled-database"></a>Spostamento di un database abilitato per FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento illustra come spostare un database abilitato per FILESTREAM.  
  
> [!NOTE]  
>  Gli esempi di questo argomento presuppongono l'uso del database Archive creato in [Creare un database abilitato per FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
### <a name="to-move-a-filestream-enabled-database"></a>Per spostare un database abilitato per FILESTREAM  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic su **Nuova query** per aprire l'editor di query.  
  
2.  Copiare lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente nell'editor di query e fare clic su **Esegui**. Lo script consentirà di visualizzare la posizione dei file fisici del database utilizzati dal database FILESTREAM.  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Copiare lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente nell'editor di query e fare clic su **Esegui**. Questo codice consente di attivare la modalità offline per il database `Archive` .  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Creare la cartella `C:\moved_location`, quindi spostarvi i file e le cartelle elencati nel passaggio 2.  
  
5.  Copiare lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente nell'editor di query e fare clic su **Esegui**. Questo script consente di impostare la modalità non online per il database `Archive` .  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
