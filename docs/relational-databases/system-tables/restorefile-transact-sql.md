---
title: restorefile (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ffb5c6e1457a846bf211dfeb075f3270a7269736
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263044"
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni file ripristinato, compresi i file ripristinati in modo indiretto in base al nome del filegroup. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Numero di identificazione univoco che identifica l'operazione di ripristino corrispondente. Riferimenti **restorehistory (restore_history_id)**.|  
|**file_number**|**Numeric(10,0)**|Numero di identificazione del file ripristinato. Deve essere univoco in ogni database. Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, questo valore viene popolato nello stesso modo previsto per un ripristino completo.|  
|**destination_phys_drive**|**nvarchar(260)**|Unità o partizione in cui è stato ripristinato il file Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, questo valore viene popolato nello stesso modo previsto per un ripristino completo.|  
|**destination_phys_name**|**nvarchar(260)**|Nome del file senza l'indicazione dell'unità o partizione in cui è stato ripristinato il file Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, questo valore viene popolato nello stesso modo previsto per un ripristino completo.|  
  
## <a name="remarks"></a>Osservazioni  
 Per ridurre il numero di righe in questa tabella e in altre tabelle di cronologia e di backup, eseguire il [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino di tabelle &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
