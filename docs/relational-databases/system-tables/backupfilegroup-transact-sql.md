---
title: backupfilegroup (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backupfilegroup_TSQL
- backupfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], backupfilegroup system table
- backupfilegroup system table
ms.assetid: d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9
caps.latest.revision: 53
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3a0ffb005b52f4460415f166a6edc197218671d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni filegroup in un database al momento del backup. **backupfilegroup** viene archiviato nel **msdb** database.  
  
> [!NOTE]  
>  Il **backupfilegroup** tabella viene illustrata la configurazione di filegroup del database, non del set di backup. Per identificare se un file è incluso nel set di backup, utilizzare il **is_present** colonna il [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md) tabella.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|Set di backup contenente questo filegroup.|  
|**name**|**sysname**|Nome del filegroup|  
|**filegroup_id**|**int**|ID del filegroup, univoco all'interno del database. Corrisponde a **data_space_id** in **Sys. FileGroups**.|  
|**filegroup_guid**|**uniqueidentifier**|Identificatore univoco globale per il filegroup. Può essere NULL.|  
|**type**|**char(2)**|Tipo di contenuto, può corrispondere a:<br /><br /> FG = Filegroup "Rows"<br /><br /> SL = Filegroup di log [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**type_desc**|**nvarchar(60)**|Descrizione del tipo di funzione, può corrispondere a:<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP|  
|**is_default**|**bit**|Il filegroup predefinito, utilizzato quando non è specificato alcun filegroup in CREATE TABLE o CREATE INDEX.|  
|**is_readonly**|**bit**|1 = Il filegroup è di sola lettura.|  
|**log_filegroup_guid**|**uniqueidentifier**|Può essere NULL.|  
  
## <a name="remarks"></a>Osservazioni  
  
> [!IMPORTANT]  
>  Lo stesso nome di filegroup può apparire in diversi database, ogni filegroup dispone tuttavia di un GUID proprio. Pertanto, **(backup_set_id, filegroup_guid)** è una chiave univoca che identifica un filegroup in **backupfilegroup**.  
  
 RESTORE VERIFYONLY FROM *dispositivo_backup* WITH LOADHISTORY popola le colonne di **backupmediaset** tabella con i valori appropriati dall'intestazione del set di supporti.  
  
 Per ridurre il numero di righe in questa tabella e in altre tabelle di cronologia e di backup, eseguire il [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino di tabelle &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
