---
title: sp_add_agent_profile (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords:
- sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 448b07e1538f3d50f0bb2eb48ca5156176605133
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddagentprofile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo profilo per un agente di replica. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_agent_profile [ [ @profile_id= ] profile_id OUTPUT ]  
        , [ @profile_name= ] 'profile_name'   
        , [ @agent_type= ] 'agent_type' ]   
    [ , [ @profile_type= ] profile_type ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @default= ] default ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@profile_id=** ] *profile_id*  
 ID associato al nuovo profilo inserito. *profile_id* viene **int** senza che sia un parametro OUTPUT facoltativo. Se viene specificato, il valore è impostato sull'ID del nuovo profilo.  
  
 [  **@profile_name=** ] **'***profile_name***'**  
 Nome del profilo. *profile_name* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@agent_type=** ] **'***agent_type***'**  
 Tipo di agente di replica. *agent_type* viene **int**e non prevede alcun valore predefinito può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|agente snapshot|  
|**2**|Agente di lettura log|  
|**3**|Agente di distribuzione|  
|**4**|Agente di merge|  
|**9**|Agente di lettura coda|  
  
 [  **@profile_type=** ] *profile_type*  
 È il tipo di profilo. *profile_type* è **int**, il valore predefinito è **1**.  
  
 **0** indica un profilo del sistema. **1** indica un profilo personalizzato. Solo i profili personalizzati possono essere creati utilizzando questa stored procedure. pertanto l'unico valore valido è **1**. Solo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Crea profili del sistema.  
  
 [  **@description=** ] **'***descrizione***'**  
 Descrizione del profilo. *Descrizione* viene **nvarchar(3000)**, non prevede alcun valore predefinito.  
  
 [  **@default=** ] *predefinito*  
 Indica se il profilo è il valore predefinito per *agent_type * *.* *impostazione predefinita* viene **bit**, il valore predefinito è **0**. **1** indica che il profilo da aggiungere diventerà il nuovo profilo predefinito per l'agente specificato da *agent_type*.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_agent_profile** viene utilizzata nella replica snapshot, transazionale e di tipo merge.  
  
 I profili agenti personalizzati vengono aggiunti con valori predefiniti dei parametri degli agenti. Uso [sp_change_agent_parameter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md) per modificare questi valori predefiniti o [sp_add_agent_parameter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md) aggiungere altri parametri.  
  
 Quando si **sp_add_agent_profile** viene eseguita, viene aggiunta una riga per il nuovo profilo personalizzato nel [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) tabella e i parametri predefiniti associati per questo profilo vengono aggiunti per il [MSagent_parameters &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) tabella.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_add_agent_profile**.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i profili agenti di replica](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Profili degli agenti di replica](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [la procedura sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
