---
title: backupmediafamily (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da7d59170e9ed3ed9a1808e03e792474c22afddd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Include una riga per ogni gruppo di supporti. Se un gruppo di supporti risiede in un set di supporti con mirroring, il gruppo includerà una riga distinta per ciascun mirror del set di supporti. Questa tabella è archiviata nel **msdb** database.  
    
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Numero di identificazione univoco del set di supporti in cui è incluso il gruppo. Riferimenti **backupmediaset (media_set_id)**|  
|**family_sequence_number**|**tinyint**|Posizione del gruppo di supporti nel set di supporti.|  
|**media_family_id**|**uniqueidentifier**|Numero di identificazione univoco del gruppo di supporti. Può essere NULL.|  
|**media_count**|**int**|Numero di supporti nel gruppo. Può essere NULL.|  
|**logical_device_name**|**nvarchar(128)**|Nome di questo dispositivo di backup in **sys.backup_devices.name**. Se si tratta di un dispositivo di backup temporaneo (anziché un dispositivo di backup permanente presente in **backup_devices**), il valore di **logical_device_name** è NULL.|  
|**physical_device_name**|**nvarchar(260)**|Nome fisico del dispositivo di backup. Può essere NULL. Questo campo è condivisa tra il processo di backup e ripristino. Può contenere il percorso di destinazione di backup originale o il percorso di origine originale del ripristino. A seconda se il backup o ripristino si è verificato prima in un server per un database. Si noti che consecutivi ripristini dal file di backup stesso non aggiornerà il percorso indipendentemente dalla posizione in fase di ripristino. Per questo motivo, **physical_device_name** campo non può essere utilizzato per visualizzare il percorso di ripristino utilizzato.|  
|**device_type**|**tinyint**|Tipo di dispositivo di backup:<br /><br /> 2 = Disco<br /><br /> 5 = Nastro<br /><br /> 7 = Dispositivo virtuale<br /><br /> 9 = archiviazione di azure<br /><br /> 105 = Dispositivo di backup permanente<br /><br /> Può essere NULL.<br /><br /> Tutti i nomi dei dispositivi permanenti e i numeri di dispositivo sono reperibile **backup_devices**.|  
|**physical_block_size**|**int**|Dimensioni fisiche del blocco utilizzate per la scrittura del gruppo di supporti. Può essere NULL.|  
|**Mirror**|**tinyint**|Numero di mirroring (0-3).|  
  
## <a name="remarks"></a>Osservazioni  
 RESTORE VERIFYONLY FROM *dispositivo_backup* WITH LOADHISTORY popola le colonne di **backupmediaset** tabella con i valori appropriati dall'intestazione del set di supporti.  
  
 Per ridurre il numero di righe in questa tabella e in altre tabelle di cronologia e di backup, eseguire il [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino di tabelle &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
