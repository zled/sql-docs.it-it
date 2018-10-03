---
title: dbo. cdc_jobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 321e6b1809f6dc8f30710c98665316c50a6ab50a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719755"
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia i parametri di configurazione dell'acquisizione dei dati delle modifiche per processi di acquisizione e pulizia. Questa tabella è archiviata **msdb**.  
  
 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database nel quale viene eseguito il processo.|  
|**job_type**|**nvarchar(20)**|Tipo di processo, "acquisizione" o "pulizia".|  
|**job_id**|**uniqueidentifier**|ID univoco associato al processo.|  
|**maxtrans**|**int**|Numero massimo di transazioni da elaborare in ogni ciclo di analisi.<br /><br /> **maxtrans** è valida solo per i processi di acquisizione.|  
|**maxscans**|**int**|Numero massimo di cicli di analisi da eseguire per estrarre tutte le righe dal log.<br /><br /> **maxscans** è valida solo per i processi di acquisizione.|  
|**continua**|**bit**|Flag che indica se l'esecuzione del processo di acquisizione deve essere continua (1) o come singola occorrenza (0). Per altre informazioni, vedere [Sys. sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **Continua** è valida solo per i processi di acquisizione.|  
|**pollingInterval**|**bigint**|Numero di secondi tra cicli di analisi del log.<br /><br /> **pollingInterval** è valida solo per i processi di acquisizione.|  
|**conservazione**|**bigint**|Numero di minuti per i quali vengono conservate le righe delle modifiche nelle tabelle delle modifiche.<br /><br /> **conservazione** è valida solo per i processi di pulizia.|  
|**soglia**|**bigint**|Numero massimo di voci che possono essere eliminate utilizzando un'unica istruzione nel processo di pulizia.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [Sys. sp_cdc_change_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [Sys. sp_cdc_help_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [Sys. sp_cdc_drop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
