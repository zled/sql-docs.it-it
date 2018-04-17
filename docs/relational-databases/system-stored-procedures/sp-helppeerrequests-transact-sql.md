---
title: sp_helppeerrequests (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5266359d366acad62f7ef5e4def8c176ea12682
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sphelppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su tutte le richieste di state ricevute dai partecipanti a una topologia di replica peer-to-peer, in cui tali richieste sono state iniziate eseguendo [sp_requestpeerresponse &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) qualsiasi database pubblicato della topologia. Questa stored procedure viene eseguita nel database di pubblicazione di un server di pubblicazione che partecipa a una topologia di replica peer-to-peer. Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publication**=] **'***pubblicazione***'**  
 Nome della pubblicazione in una topologia peer-to-peer per cui sono state inviate richieste dello stato. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@description**=] **'***descrizione***'**  
 Valore che può essere usato per identificare richieste dello stato individuali, che consente di filtrare le risposte restituite in base all'utente definite informazioni fornite durante la chiamata [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Descrizione* viene **nvarchar(4000**, il valore predefinito è **%**. Per impostazione predefinita, tutte le richieste dello stato per la pubblicazione vengono restituite. Questo parametro viene utilizzato per restituire solo le richieste di stato con una descrizione corrisponde al valore specificato *descrizione*, in cui vengono confrontate le stringhe di caratteri tramite un [come &#40;Transact-SQL&#41; ](../../t-sql/language-elements/like-transact-sql.md)clausola.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifica una richiesta.|  
|**Pubblicazione**|**sysname**|Nome della pubblicazione per cui è stata inviata la richiesta dello stato.|  
|**sent_date**|**datetime**|Data e ora dell'invio della richiesta dello stato.|  
|**description**|**nvarchar(4000)**|Informazioni definite dall'utente che possono essere utilizzate per identificare richieste dello stato individuali.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helppeerrequests** viene utilizzata nella replica transazionale peer-to-peer.  
  
 **sp_helppeerrequests** viene utilizzato quando si ripristina un database pubblicato in una topologia peer-to-peer.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_helppeerrequests**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
