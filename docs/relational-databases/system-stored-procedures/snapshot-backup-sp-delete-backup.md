---
title: sp_delete_backup (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1dc3339403f7f39fef0e8fee4e3dbb05ea0a94b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="snapshot-backup---spdeletebackup"></a>Backup di snapshot - sp_delete_backup
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Elimina tutti gli snapshot e il file di backup che costituiscono un backup di snapshot impostato dal database specificato. Questa stored procedure di sistema è l'unico metodo consigliato per la gestione dei set di backup di snapshot. Per altre informazioni, vedere [Backup di snapshot di file per i file di database in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *[ @backup_url =] backup_meta_file_url*  
 L'URL del backup da eliminare, che elimina tutti gli snapshot che include il set incluso il file di backup di backup specificato.  
  
 *[ @db_name =] database_name*  
 Il nome del database contenente lo snapshot da eliminare. Quando viene fornito un nome di database, il sistema verifica che l'URL di backup fornito è un URL di backup per il database specificato e Usa [sp_delete_backup_file_snapshot &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) eliminare ogni snapshot. Se non viene specificato alcun nome di database, è possibile che questo controllo database non viene eseguito.  
  
## <a name="permissions"></a>Permissions  
 Richiede autorizzazione ALTER ANY DATABASE o l'autorizzazione ALTER per il database specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. fn_db_backup_file_snapshots &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
