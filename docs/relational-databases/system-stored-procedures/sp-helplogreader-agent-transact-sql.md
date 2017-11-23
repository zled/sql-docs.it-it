---
title: sp_helplogreader_agent (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords: sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee9020dff1819069c3449bd85cbbf61d440acd91
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelplogreaderagent-transact-sql"></a>sp_helplogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà del processo dell'agente di lettura log per il database di pubblicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'agente.|  
|**name**|**nvarchar (100)**|Nome dell'agente.|  
|**publisher_security_mode**|**smallint**|Modalità di sicurezza utilizzata dall'agente durante la connessione al server di pubblicazione. Le possibili modalità sono le seguenti:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione<br /><br /> **1** = autenticazione di Windows.|  
|**publisher_login**|**sysname**|Account di accesso utilizzato per la connessione al server di pubblicazione.|  
|**publisher_password**|**nvarchar (524)**|Per motivi di sicurezza, un valore di  **\* \* \* \* \* \* \* \* \* \***  è sempre restituito.|  
|**job_id**|**uniqueidentifier**|ID univoco del processo dell'agente.|  
|**job_login**|**nvarchar(512)**|È l'account di Windows con cui viene eseguito l'agente di lettura Log, che viene restituito nel formato *dominio*\\*username*.|  
|**job_password**|**sysname**|Per motivi di sicurezza, un valore di  **\* \* \* \* \* \* \* \* \* \***  è sempre restituito.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helplogreader_agent** viene utilizzata nella replica transazionale.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** al server di pubblicazione o i membri del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di pubblicazione possono eseguire **sp_helplogreader_agent**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
