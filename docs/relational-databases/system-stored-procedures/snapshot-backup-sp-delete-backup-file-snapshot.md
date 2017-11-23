---
title: sp_delete_backup_file_snapshot (Transact-SQL) | Documenti Microsoft
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cf8bf8484e77c15c951ca548ce00baccfaf5b38
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="snapshot-backup---spdeletebackupfilesnapshot"></a>Backup di snapshot - sp_delete_backup_file_snapshot
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Elimina uno snapshot di backup specificato dal database specificato. Utilizzare stored procedure di sistema in combinazione con il **fn_db_backup_file_snapshots** funzione di sistema per identificare ed eliminare snapshot di backup orfani. Per altre informazioni, vedere [Backup di snapshot di file per i file di database in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N’<database_name>  
    , [ @snapshot_url = ] N’<snapshot_url>  
```  
  
## <a name="arguments"></a>Argomenti  
 *[ @db_name =] database_name*  
 Il nome del database contenente lo snapshot da eliminare, fornito come stringa Unicode.  
  
 *[ @snapshot_url =] snapshot_url*  
 L'URL dello snapshot da eliminare, fornito come stringa Unicode.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY DATABASE.  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. fn_db_backup_file_snapshots &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
