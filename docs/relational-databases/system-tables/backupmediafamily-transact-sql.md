---
title: backupmediafamily (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs: TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e814887bb97d14d165c39ad4a8d634bf84947b1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
|**logical_device_name**|**nvarchar (128)**|Nome di questo dispositivo di backup in **sys.backup_devices.name**. Se si tratta di un dispositivo di backup temporaneo (anziché un dispositivo di backup permanente presente in **backup_devices**), il valore di **logical_device_name** è NULL.|  
|**physical_device_name**|**nvarchar (260)**|Nome fisico del dispositivo di backup. Può essere NULL.|  
|**device_type**|**tinyint**|Tipo di dispositivo di backup:<br /><br /> 2 = Disco<br /><br /> 5 = Nastro<br /><br /> 7 = Dispositivo virtuale<br /><br /> 105 = Dispositivo di backup permanente<br /><br /> Può essere NULL.<br /><br /> Tutti i nomi dei dispositivi permanenti e i numeri di dispositivo sono reperibile **backup_devices**.|  
|**physical_block_size**|**int**|Dimensioni fisiche del blocco utilizzate per la scrittura del gruppo di supporti. Può essere NULL.|  
|**mirror**|**tinyint**|Numero di mirroring (0-3).|  
  
## <a name="remarks"></a>Osservazioni  
 RESTORE VERIFYONLY FROM *dispositivo_backup* WITH LOADHISTORY popola le colonne di **backupmediaset** tabella con i valori appropriati dall'intestazione del set di supporti.  
  
 Per ridurre il numero di righe in questa tabella e in altre tabelle di cronologia e di backup, eseguire il [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino tabelle &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tabelle di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
