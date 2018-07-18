---
title: dbo.sysjobservers (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f960176ea1c0aea2dcc0251f9bc17a7aeb889846
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259671"
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia l'associazione o la relazione di un determinato processo con uno o più server di destinazione. Questa tabella è archiviata nel database msdb.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Numero di identificazione del processo.|  
|server_id|**int**|Numero di identificazione del server.|  
|last_run_outcome|**tinyint**|Risultato dell'ultima esecuzione del processo:<br /><br /> **0** = esito negativo<br /><br /> **1** = esito positivo<br /><br /> **3** = annullato|  
|messaggio last_outcome_|**nvarchar(1024)**|Eventuale messaggio associato alla colonna last_run_outcome.|  
|last_run_date|**int**|Data dell'ultima esecuzione del processo.|  
|last_run_time|**int**|Ora dell'ultima esecuzione del processo.|  
|last_run_duration|**int**|Durata di esecuzione del processo, in ore, minuti e secondi. Calcolata mediante la formula: (*ore*\*10000) + (*minuti*\*100) + *secondi*.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
