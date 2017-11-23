---
title: sp_help_agent_parameter (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_help_agent_parameter
- sp_help_agent_parameter_TSQL
helpviewer_keywords: sp_help_agent_parameter
ms.assetid: 8fb4a9c3-19af-4a34-8004-572729ba3d15
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c9e97d300b834c6f8182379cf2265d9fd5327d7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpagentparameter-transact-sql"></a>sp_help_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce tutti i parametri di un profilo di [MSagent_parameters &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) tabella di sistema. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione in cui l'agente è in esecuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_agent_parameter [ [ @profile_id = ] profile_id ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_id=**] *profile_id*  
 È l'ID del profilo di [MSagent_parameters &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) tabella. *profile_id* è **int**, il valore predefinito è **-1**, che restituisce tutti i parametri.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|ID del profilo agente.|  
|**parameter_name**|**sysname**|Nome del parametro.|  
|**valore**|**nvarchar(255)**|Valore del parametro.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_agent_parameter** viene utilizzata in tutti i tipi di replica.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **replmonitor** ruolo predefinito del database possono eseguire **sp_help_agent_parameter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i profili agenti di replica](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [la procedura sp_add_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
