---
title: dbo.sysjobsteps (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
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
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1c044af6f1e6af5b8338dc200bd1041ba062614a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni relative a tutti i passaggi di un processo da eseguire tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID del processo.|  
|**step_id**|**int**|ID del passaggio del processo.|  
|**step_name**|**sysname**|Nome del passaggio del processo.|  
|**subsystem**|**nvarchar(40)**|Nome del sottosistema utilizzato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per eseguire il passaggio del processo|  
|**comando**|**nvarchar(max)**|Comando deve essere eseguito da **sottosistema**.|  
|**flags**|**int**|Riservato.|  
|**additional_parameters**|**ntext**|Riservato.|  
|**cmdexec_success_code**|**int**|Valore a livello di errore restituito da **CmdExec** passaggi del sottosistema per indicare l'esito positivo.|  
|**on_success_action**|**tinyint**|Azione da eseguire quando un passaggio viene eseguito correttamente.|  
|**on_success_step_id**|**int**|ID del passaggio successivo da eseguire quando un passaggio viene eseguito correttamente.|  
|**on_fail_action**|**tinyint**|Azione da eseguire quando un passaggio non viene eseguito correttamente.|  
|**on_fail_step_id**|**int**|ID del passaggio successivo da eseguire quando un passaggio non viene eseguito correttamente.|  
|**server**|**sysname**|Riservato.|  
|**database_name**|**sysname**|Nome del database in cui **comando** viene eseguita se **sottosistema** è TSQL.|  
|**database_user_name**|**sysname**|Nome dell'utente del database di cui viene utilizzato l'account quando si esegue il passaggio.|  
|**retry_attempts**|**int**|Numero di tentativi in caso di esecuzione errata del passaggio.|  
|**retry_interval**|**int**|Periodo di attesa tra un tentativo e il successivo.|  
|**os_run_priority**|**int**|Riservato.|  
|**output_file_name**|**nvarchar(200)**|Nome del file in cui l'output dei passaggi viene salvato quando **sottosistema** è TSQL, PowerShell o **CmdExec * * *.*|  
|**last_run_outcome**|**int**|Risultato dell'esecuzione precedente del passaggio del processo.<br /><br /> **0** = non è riuscita<br /><br /> **1** = ha avuto esito positivo<br /><br /> **2** = nuovo tentativo<br /><br /> **3** = annullato<br /><br /> **5** = sconosciuto|  
|**last_run_duration**|**int**|Durata (hhmmss) dell'ultima esecuzione del passaggio.|  
|**last_run_retries**|**int**|Numero di tentativi durante l'ultima esecuzione del passaggio del processo.|  
|**last_run_date**|**int**|Data (yyyymmdd) di inizio dell'ultima esecuzione del passaggio.|  
|**last_run_time**|**int**|Ora (hhmmss) di inizio dell'ultima esecuzione del passaggio.|  
|**proxy_id**|**int**|Proxy per il passaggio del processo.|  
|**step_uid**|**uniqueidentifier**|Identificatore per il passaggio del processo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
