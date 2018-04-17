---
title: dbo.sysjobhistory (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/03/2016
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
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6a798495b06a4a981f37dcf8031cb2ef13185d63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sull'esecuzione di processi pianificati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questa tabella è archiviata nel **msdb** database.  
  
> **Nota:** dati vengono aggiornati solo dopo il completamento di jobstep.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Identificatore univoco della riga.|  
|**job_id**|**uniqueidentifier**|ID del processo.|  
|**step_id**|**int**|ID del passaggio del processo.|  
|**step_name**|**sysname**|Nome del passaggio.|  
|**sql_message_id**|**int**|ID di un messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito se l'esecuzione del processo ha esito negativo.|  
|**sql_severity**|**int**|Gravità di qualsiasi errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**message**|**nvarchar(4000)**|Eventuale testo di un messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**run_status**|**int**|Stato di esecuzione del processo:<br /><br /> **0** = non è riuscita<br /><br /> **1** = ha avuto esito positivo<br /><br /> **2** = nuovo tentativo<br /><br /> **3** = annullato|  
|**run_date**|**int**|Data di avvio dell'esecuzione del processo o del passaggio. Per una cronologia dei processi o dei passaggi in corso, rappresenta la data/ora di scrittura della cronologia.|  
|**run_time**|**int**|Ora di inizio dell'esecuzione del processo o del passaggio.|  
|**run_duration**|**int**|Tempo trascorso nell'esecuzione del processo o passaggio **HHMMSS** formato.|  
|**operator_id_emailed**|**int**|ID dell'operatore che ha ricevuto una notifica tramite posta elettronica al termine dell'esecuzione del processo.|  
|**operator_id_netsent**|**int**|ID dell'operatore che ha ricevuto un messaggio al termine dell'esecuzione del processo.|  
|**operator_id_paged**|**int**|ID dell'operatore che ha ricevuto una notifica tramite cercapersone al termine dell'esecuzione del processo.|  
|**retries_attempted**|**int**|Numero di tentativi di esecuzione del processo o del passaggio.|  
|**server**|**sysname**|Nome del server in cui è stato eseguito il processo.|  
  
  ## <a name="example"></a>Esempio
 Nell'esempio [!INCLUDE[tsql](../../includes/tsql-md.md)] query convertirà il **fase di esecuzione** e **durata** le colonne in un formato più intuitivo.  Eseguire lo script in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 
 ```sql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
