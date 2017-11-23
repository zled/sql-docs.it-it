---
title: dbo.sysjobservers (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a706c537f4f983563dacb1f137314680824dd30
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia l'associazione o la relazione di un determinato processo con uno o più server di destinazione. Questa tabella è archiviata nel database msdb.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Numero di identificazione del processo.|  
|server_id|**int**|Numero di identificazione del server.|  
|last_run_outcome|**tinyint**|Risultato dell'ultima esecuzione del processo:<br /><br /> **0** = esito negativo<br /><br /> **1** = esito positivo<br /><br /> **3** = Annulla|  
|messaggio last_outcome_|**nvarchar (1024)**|Eventuale messaggio associato alla colonna last_run_outcome.|  
|last_run_date|**int**|Data dell'ultima esecuzione del processo.|  
|last_run_time|**int**|Ora dell'ultima esecuzione del processo.|  
|last_run_duration|**int**|Durata di esecuzione del processo, in ore, minuti e secondi. Calcolata mediante la formula: (*ore*\*10000) + (*minuti*\*100) + *secondi*.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di SQL Server Agent &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
