---
title: sp_change_agent_parameter (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d01a06f119a0c1d7669f0c811e8bee03e5eeb912
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32992528"
---
# <a name="spchangeagentparameter-transact-sql"></a>sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le modifiche a un parametro di un profilo di agente di replica archiviato nella [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) tabella di sistema. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione in cui l'agente è in esecuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_id=**] *profile_id*,  
 ID del profilo. *profile_id* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@parameter_name=**] **'***parameter_name***'**  
 Nome del parametro. *parameter_name* viene **sysname**, non prevede alcun valore predefinito. I parametri che è possibile modificare per i profili sistema dipendono dal tipo di agente. Per individuare il tipo di agente in questo *profile_id* rappresenta, individuare il *profile_id* colonna il **Msagent_profiles** tabella e prendere nota di *agent_type*  valore.  
  
> [!NOTE]  
>  Se un parametro è supportato per un determinato *agent_type*, ma non è stato definito nel profilo agente, viene restituito un errore. Per aggiungere un parametro a un profilo agente è necessario eseguire [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 Per un agente Snapshot (*agent_type*=**1**), se definito nel profilo, è possano modificare le proprietà seguenti:  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **Dimensioni del pacchetto**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 Per un agente di lettura Log (*agent_type*=**2**), se definito nel profilo, è possano modificare le proprietà seguenti:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **Dimensioni del pacchetto**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **ReadBatchThreshold**  
  
 Per un agente di distribuzione (*agent_type*=**3**), se definito nel profilo, è possano modificare le proprietà seguenti:  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **Dimensioni del pacchetto**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 Per un agente di Merge (*agent_type*=**4**), se definito nel profilo, è possano modificare le proprietà seguenti:  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **DownloadReadChangesPerBatch**  
  
-   **DownloadWriteChangesPerBatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **FastRowCount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **NumDeadlockRetries**  
  
-   **Output**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **Dimensioni del pacchetto**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **QueueSizeMultiplier**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **UploadWriteChangesPerBatch**  
  
-   **UseInprocLoader**  
  
-   **Convalida**  
  
-   **Oggetto ValidateInterval**  
  
 Per un agente di lettura coda (*agent_type*=**9**), se definito nel profilo, è possano modificare le proprietà seguenti:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 Per visualizzare i parametri che sono stati definiti per un determinato profilo, eseguire **sp_help_agent_profile** e prendere nota di *profile_name* associato il *profile_id*. Con l'appropriato *profile_id*, quindi eseguire **sp_help_agent_parameters** utilizzando tale *profile_id* per visualizzare i parametri associati al profilo. È possibile aggiungere parametri a un profilo eseguendo [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 [  **@parameter_value=**] **'***parameter_value***'**  
 Nuovo valore del parametro *parameter_value* viene **nvarchar(255**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_change_agent_parameter** viene utilizzata in tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_change_agent_parameter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Profili degli agenti di replica](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agente merge repliche](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [la procedura sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
