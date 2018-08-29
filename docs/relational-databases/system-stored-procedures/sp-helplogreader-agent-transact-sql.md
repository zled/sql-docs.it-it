---
title: sp_helplogreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef9fd50728a4bc9ebf661b2dbb22ad8ca4e9f4ad
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031822"
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
 [ **@publisher**=] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'agente.|  
|**name**|**Nvarchar(100)**|Nome dell'agente.|  
|**publisher_security_mode**|**smallint**|Modalità di sicurezza utilizzata dall'agente durante la connessione al server di pubblicazione. Le possibili modalità sono le seguenti:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione<br /><br /> **1** = autenticazione di Windows.|  
|**publisher_login**|**sysname**|Account di accesso utilizzato per la connessione al server di pubblicazione.|  
|**publisher_password**|**nvarchar(524**|Per motivi di sicurezza, un valore pari **\* \* \* \* \* \* \* \* \* \*** è sempre restituito.|  
|**job_id**|**uniqueidentifier**|ID univoco del processo dell'agente.|  
|**job_login**|**nvarchar(512)**|L'account di Windows con cui viene eseguito l'agente di lettura Log, viene restituito nel formato *domain*\\*username*.|  
|**job_password**|**sysname**|Per motivi di sicurezza, un valore pari **\* \* \* \* \* \* \* \* \* \*** è sempre restituito.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_helplogreader_agent** viene utilizzata nella replica transazionale.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** nel server di pubblicazione o i membri del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di pubblicazione possono eseguire **sp_helplogreader_agent**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
