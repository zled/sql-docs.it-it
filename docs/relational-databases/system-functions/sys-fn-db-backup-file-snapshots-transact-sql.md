---
title: Sys. fn_db_backup_file_snapshots (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30988d44e03a40ffcb8317a603b99633c21c8068
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>Sys. fn_db_backup_file_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce gli snapshot di Azure associati ai file di database. Se il database specificato non è stato trovato o se non sono archiviati i file di database nel servizio di archiviazione Blob di Microsoft Azure, viene restituita alcuna riga. Utilizzare questa funzione di sistema in combinazione con il **sp_delete_backup_file_snapshot** stored procedure per identificare ed eliminare gli snapshot di backup orfani di sistema. Per altre informazioni, vedere [Backup di snapshot di file per i file di database in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Database_name*  
 Il nome del database sottoposto a query. Se NULL, questa funzione viene eseguita nell'ambito del database corrente.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|ID File per il database. Non ammette i valori Null.|  
|snapshot_time|**nvarchar (260)**|Il timestamp dello snapshot, perché viene restituito dall'API REST. Restituisce NULL se non esiste alcuno snapshot.|  
|snapshot_url|**nvarchar(360)**|L'URL completo per lo snapshot di file. Restituisce NULL se nessun snapshot esistono.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DATABASE STATE per il database.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_delete_backup_file_snapshot &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
