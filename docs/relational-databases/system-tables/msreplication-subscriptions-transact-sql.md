---
title: MSreplication_subscriptions (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
f1_keywords:
- MSreplication_subscriptions
- MSreplication_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_subscriptions system table
ms.assetid: fd0c5843-4e9b-4448-8bfb-0a4067d1d8d1
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 91f5679147c6432fd5f76574272b8b2cf15f3d0c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msreplicationsubscriptions-transact-sql"></a>MSreplication_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSreplication_subscriptions** tabella contiene una riga di informazioni di replica per ogni agente di distribuzione per la manutenzione del database sottoscrittore locale. Questa tabella è archiviata nel database di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**Pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**independent_agent**|**bit**|Indica se per questa pubblicazione è disponibile un agente di distribuzione autonomo.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> 0 = push<br /><br /> 1 = pull<br /><br /> 2 = anonima|  
|**distribution_agent**|**sysname**|Nome dell'agente di distribuzione.|  
|**Time**|**smalldatetime**|Ora dell'ultimo aggiornamento eseguito dall'agente di distribuzione.|  
|**description**|**nvarchar(255)**|Descrizione della sottoscrizione.|  
|**transaction_timestamp**|**varbinary(16)**|Solo per uso interno.|  
|**update_mode**|**tinyint**|Tipo di aggiornamento.|  
|**agent_id**|**binary(16)**|ID dell'agente.|  
|**subscription_guid**|**binary(16)**|Identificatore globale della versione della sottoscrizione associata alla pubblicazione.|  
|**subid**|**binary(16)**|Identificatore globale di una sottoscrizione anonima.|  
|**immediate_sync**|**bit**|Indica se i file di sincronizzazione vengono creati o aggiornati a ogni esecuzione dell'agente snapshot.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
