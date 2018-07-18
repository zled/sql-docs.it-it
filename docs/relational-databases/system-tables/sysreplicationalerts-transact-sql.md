---
title: sysreplicationalerts (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a6579b75ab8d8af66ed62bd9af021f65235423f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33007258"
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sulle condizioni che provocano l'attivazione di un avviso di replica. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID dell'avviso.|  
|**status**|**int**|Valore definito dall'utente:<br /><br /> **0** = non gestito.<br /><br /> **1** = servite.|  
|**agent_type**|**int**|Tipo di agente:<br /><br /> **1** = agente snapshot.<br /><br /> **2** = agente di lettura log.<br /><br /> **3** = agente di distribuzione.<br /><br /> **4** = agente di merge.|  
|**agent_id**|**int**|L'ID dell'agente dalle tabelle **MSsnapshot_agents**, **MSlogreader_agents**, **MSdistribution_agents**, o **MSmerge_agents**.|  
|**error_id**|**int**|L'ID dell'errore archiviato **MSrepl_errors**.|  
|**alert_error_code**|**int**|ID di messaggio dell'avviso generato durante la registrazione del record.|  
|**time**|**datetime**|Ora di inserimento del record.|  
|**publisher**|**sysname**|Nome del server di pubblicazione associato all'agente che ha attivato l'avviso.|  
|**publisher_db**|**sysname**|Database del server di pubblicazione associato all'agente che ha attivato l'avviso.|  
|**Pubblicazione**|**sysname**|Pubblicazione associata all'agente che ha attivato l'avviso.|  
|**publication_type**|**int**|Tipo di pubblicazione:<br /><br /> **0** = snapshot.<br /><br /> **1** = transazionale.<br /><br /> **2** = unione nell'indice.|  
|**subscriber**|**sysname**|Nome del Sottoscrittore associato all'agente che ha attivato l'avviso.|  
|**subscriber_db**|**sysname**|Nome del database del Sottoscrittore associato all'agente che ha attivato l'avviso.|  
|**article**|**sysname**|Nome dell'articolo associato all'agente che ha attivato l'avviso.|  
|**destination_object**|**sysname**|Nome della tabella di sottoscrizione associata all'avviso.|  
|**source_object**|**sysname**|Nome della tabella pubblicata associata all'avviso.|  
|**alert_error_text**|**ntext**|Testo dell'avviso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
