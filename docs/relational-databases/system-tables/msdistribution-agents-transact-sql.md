---
title: MSdistribution_agents (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistribution_agents_TSQL
- MSdistribution_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_agents system table
ms.assetid: 0e8f0653-1351-41d1-95d2-40f6d5a050ca
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2bb6aa8917a34946eeaab0d79ccb7a9ed04dcf0d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msdistributionagents-transact-sql"></a>MSdistribution_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdistribution_agents** tabella contiene una riga per ogni agente di distribuzione eseguito nel server di distribuzione locale. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'agente di distribuzione.|  
|**name**|**Nvarchar (100)**|Nome dell'agente di distribuzione.|  
|**publisher_database_id**|**int**|ID del database del server di pubblicazione.|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**Pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**subscriber_id**|**smallint**|ID del Sottoscrittore, utilizzato solo da agenti noti. Per gli agenti anonimi questa colonna è riservata.|  
|**subscriber_db**|**sysname**|Nome del database di sottoscrizione.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> **0** = push.<br /><br /> **1** = pull.<br /><br /> **2** = anonimo.|  
|**local_job**|**bit**|Indica se è presente un processo di SQL Server Agent nel server di distribuzione locale.|  
|**job_id**|**binary(16)**|Numero di identificazione del processo.|  
|**subscription_guid**|**binary(16)**|ID delle sottoscrizioni dell'agente.|  
|**profile_id**|**int**|L'ID di configurazione di [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) tabella.|  
|**anonymous_subid**|**uniqueidentifier**|ID di un agente anonimo.|  
|**subscriber_name**|**sysname**|Nome del Sottoscrittore utilizzato solo dagli agenti anonimi.|  
|**virtual_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**anonymous_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**creation_date**|**datetime**|Data e ora in cui è stato creato l'agente di distribuzione o di merge.|  
|**queue_id**|**sysname**|Identificatore per l'individuazione della coda per le sottoscrizioni ad aggiornamento in coda. Per le sottoscrizioni non impostate per l'aggiornamento in coda il valore è NULL. Per le pubblicazioni basate sul servizio di accodamento messaggi [!INCLUDE[msCoName](../../includes/msconame-md.md)], corrisponde a un valore GUID che identifica in modo univoco la coda da utilizzare per la sottoscrizione. Per le pubblicazioni in coda basato su SQL Server, la colonna contiene il valore **SQL**.<br /><br /> Nota: L'utilizzo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Accodamento messaggi è stato deprecato e non è più supportata.|  
|**queue_status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offload_enabled**|**bit**|Indica se è possibile attivare l'agente in remoto.<br /><br /> **0** specifica che l'agente non può essere attivato in remoto.<br /><br /> **1** specifica che l'agente verrà attivato in remoto nel computer remoto specificato nella *offload_server* proprietà.|  
|**offload_server**|**sysname**|Nome di rete del server da utilizzare per l'attivazione remota dell'agente.|  
|**dts_package_name**|**sysname**|Nome del pacchetto DTS. Ad esempio, per un pacchetto denominato **DTSPub_Package**, specificare `@dts_package_name = N'DTSPub_Package'`.|  
|**dts_package_password**|**nvarchar(524**|Password del pacchetto.|  
|**dts_package_location**|**int**|Posizione del pacchetto. Il percorso del pacchetto può essere **distributore** o **sottoscrittore**.|  
|**sid**|**varbinary(85)**|ID di sicurezza (SID) dell'agente di distribuzione o di merge durante la prima esecuzione dell'agente.|  
|**queue_server**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**subscriber_security_mode**|**smallint**|Modalità di sicurezza utilizzata dall'agente per la connessione al Sottoscrittore. I possibili valori sono i seguenti:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] autenticazione di SQL Server<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l'autenticazione di Windows.|  
|**subscriber_login**|**sysname**|Account di accesso utilizzato per la connessione al Sottoscrittore.|  
|**subscriber_password**|**nvarchar(524**|Valore crittografato della password utilizzata per la connessione al Sottoscrittore.|  
|**reset_partial_snapshot_progress**|**bit**|Indica se uno snapshot scaricato parzialmente deve essere scartato in modo da consentire il riavvio dell'intero processo di snapshot.|  
|**job_step_uid**|**uniqueidentifier**|ID univoco del processo di SQL Server Agent passaggio in cui viene avviato l'agente.|  
|**subscriptionstreams**|**tinyint**|Imposta il numero di connessioni consentite per ogni agente di distribuzione per l'applicazione parallela di più batch di modifiche in un Sottoscrittore. È supportato un intervallo di valori compreso tra 1 e 64.|  
|**memory_optimized**|**bit**|1 indica il sottoscrittore può essere utilizzato per le tabelle con ottimizzazione per la memoria.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
