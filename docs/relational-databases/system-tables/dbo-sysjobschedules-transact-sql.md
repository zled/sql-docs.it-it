---
title: dbo. sysjobschedules (Transact-SQL) | Documenti Microsoft
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
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2818512730a99bf7352c87f7d651d3084870767f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "33252706"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Include informazioni di pianificazione per i processi da eseguire tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa tabella è archiviata nel **msdb** database.  
  
> **Nota:** il **sysjobschedules** tabella viene aggiornata ogni 20 minuti, che potrebbero influire sui valori restituiti dal **sp_help_jobschedule** stored procedure.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID della pianificazione.|  
|**job_id**|**uniqueidentifier**|ID del processo.|  
|**next_run_date**|**int**|Data pianificata per la successiva esecuzione del processo. La data è nel formato AAAAMMGG.|  
|**next_run_time**|**int**|Ora pianificata per l'esecuzione del processo. L'ora è nel formato HHMMSS, a 24 ore.|  
  
## <a name="see-also"></a>Vedere anche  
 [dbo.sysschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
