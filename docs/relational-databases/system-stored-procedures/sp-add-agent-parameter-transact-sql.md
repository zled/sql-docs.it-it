---
title: la procedura sp_add_agent_parameter (Transact-SQL) | Documenti Microsoft
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
- sp_add_agent_parameter_TSQL
- sp_add_agent_parameter
helpviewer_keywords:
- sp_add_agent_parameter
ms.assetid: 055f4765-0574-47c3-bf7d-6ef6e9bd8b34
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: efcfb48b6c39bc65c3e281baea01d8f4fe3fd1ed
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddagentparameter-transact-sql"></a>sp_add_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un nuovo parametro e il relativo valore a un profilo agente. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_agent_parameter [ @profile_id = ] profile_id  
        , [ @parameter_name = ] 'parameter_name'   
        , [ @parameter_value = ] 'parameter_value'   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@profile_id=** ] *profile_id*  
 È l'ID del profilo di **MSagent_profiles** tabella il **msdb** database. *profile_id* viene **int**, non prevede alcun valore predefinito.  
  
 Per scoprire quale agente digitare quanto *profile_id* rappresenta, trovare il *profile_id* nel [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) tabella e prendere nota di *agent_type* valore del campo. Sono disponibili i valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|agente snapshot|  
|**2**|Agente di lettura log|  
|**3**|Agente di distribuzione|  
|**4**|Agente di merge|  
|**9**|Agente di lettura coda|  
  
 [  **@parameter_name=** ] **'***parameter_name***'**  
 Nome del parametro. *parameter_name* viene **sysname**, non prevede alcun valore predefinito. Per un elenco di parametri già definiti nei profili del sistema, vedere [profili agenti di replica](../../relational-databases/replication/agents/replication-agent-profiles.md). Per un elenco completo dei parametri validi per ogni agente, vedere gli argomenti seguenti:  
  
-   [Agente snapshot repliche](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Agente distribuzione repliche](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Agente merge repliche](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 [  **@parameter_value=**] **'***parameter_value***'**  
 Valore da assegnare al parametro. *parameter_value* viene **nvarchar(255**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **la procedura sp_add_agent_parameter** viene utilizzata nella replica snapshot, transazionale e di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_add_agent_parameter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i profili agenti di replica](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Profili degli agenti di replica](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)  
  
  
