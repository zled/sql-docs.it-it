---
title: sp_help_agent_default (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
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
- sp_help_agent_default
- sp_help_agent_default_TSQL
helpviewer_keywords: sp_help_agent_default
ms.assetid: 7ba55e39-05dd-43c7-b5da-b268ed8426dd
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94a7dd084b2df3a67e9b63b3781440dfa2f0f887
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpagentdefault-transact-sql"></a>sp_help_agent_default (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'ID della configurazione predefinita per il tipo di agente passato come parametro. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_agent_default [ @profile_id= ] profile_id OUTPUT   
        , [ @agent_type = ] agent_type  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_id=**] *profile_id***OUTPUT**  
 ID della configurazione predefinita per il tipo di agente. *profile_id* è **int**, non prevede alcun valore predefinito. *profile_id* è anche un parametro di OUTPUT e restituisce l'ID della configurazione predefinita per il tipo di agente.  
  
 [  **@agent_type=**] **'***agent_type***'**  
 Tipo di agente. *agent_type* è **int**e non prevede alcun valore predefinito può essere uno dei valori seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Agente snapshot.|  
|**2**|Agente di lettura log.|  
|**3**|Agente di distribuzione.|  
|**4**|Agente di merge.|  
|**9**|Agente di lettura coda|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_agent_default** viene utilizzata in tutti i tipi di replica.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **replmonitor** ruolo predefinito del database possono eseguire **sp_help_agent_default**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
