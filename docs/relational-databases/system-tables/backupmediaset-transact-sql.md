---
title: backupmediaset (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backupmediaset
- backupmediaset_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], backupmediaset system table
- backupmediaset system table
ms.assetid: d9c18a93-cab9-4db8-ae09-c6bd8145ab8f
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21e327f7c630b106a52a0bd720cbf94f8b4a23fd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="backupmediaset-transact-sql"></a>backupmediaset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni set di supporti di backup. Questa tabella è archiviata nel **msdb** database.  
 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Numero di identificazione univoco del set di supporti. Identità, chiave primaria.|  
|**media_uuid**|**uniqueidentifier**|UUID del set di supporti. Tutti [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di supporti è associato un UUID.<br /><br /> Per le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tuttavia, se un set di supporti contiene solo un gruppo di supporti, il **media_uuid** colonna può essere NULL (**media_family_count** è 1).|  
|**media_family_count**|**tinyint**|Numero di gruppi di supporti nel set di supporti. Può essere NULL.|  
|**name**|**nvarchar(128)**|Nome del set di supporti. Può essere NULL.<br /><br /> Per altre informazioni, vedere MEDIANAME e MEDIADESCRIPTION nell'argomento [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**description**|**nvarchar(255)**|Descrizione in formato testo del set di supporti. Può essere NULL.<br /><br /> Per altre informazioni, vedere MEDIANAME e MEDIADESCRIPTION nell'argomento [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**software_name**|**nvarchar(128)**|Nome del software di backup con cui è stata scritta l'etichetta del supporto. Può essere NULL.|  
|**software_vendor_id**|**int**|Numero di identificazione del produttore del software con cui è stata scritta l'etichetta del supporto di backup. Può essere NULL.<br /><br /> Il valore per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è l'esadecimale 0x1200.|  
|**MTF_major_version**|**tinyint**|Numero principale della versione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format utilizzata per generare il set di supporti. Può essere NULL.|  
|**mirror_count**|**tinyint**|Numero di mirroring nel set di supporti.|  
|**is_password_protected**|**bit**|Set di supporti protetto da password:<br /><br /> 0 = non protetto<br /><br /> 1 = protetto|  
|**is_compressed**|**bit**|Specifica se il backup è compresso:<br /><br /> 0 = non compresso<br /><br /> 1 = compresso<br /><br /> Durante un **msdb** esegue l'aggiornamento, questo valore è impostato su NULL. che indica un backup non compresso.|  
|**is_encrypted**|**Bit**|Specifica se il backup è crittografato:<br /><br /> 0 = Non crittografato<br /><br /> 1 = Crittografato|  
  
## <a name="remarks"></a>Osservazioni  
 RESTORE VERIFYONLY FROM *dispositivo_backup* WITH LOADHISTORY popola le colonne di **backupmediaset** tabella con i valori appropriati dall'intestazione del set di supporti.  
  
 Per ridurre il numero di righe in questa tabella e in altre tabelle di cronologia e di backup, eseguire il [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino di tabelle &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
