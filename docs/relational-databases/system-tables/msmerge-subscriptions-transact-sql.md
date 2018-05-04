---
title: MSmerge_subscriptions (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e985f871e1409dc9e837fcbc192b136365d212d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msmergesubscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_subscriptions** tabella contiene una riga per ogni sottoscrizione gestita dall'agente di Merge nel Sottoscrittore. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**publication_id**|**int**|ID della pubblicazione.|  
|**subscriber_id**|**smallint**|ID del Sottoscrittore.|  
|**subscriber_db**|**sysname**|Nome del database di sottoscrizione.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> 0 = push<br /><br /> 1 = pull<br /><br /> 2 = anonima|  
|**sync_type**|**tinyint**|Tipo di sincronizzazione:<br /><br /> 1 = Automatica.<br /><br /> 2 = Nessuna.|  
|**status**|**tinyint**|Stato della sottoscrizione.|  
|**subscription_time**|**datetime**|Ora di aggiunta della sottoscrizione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
