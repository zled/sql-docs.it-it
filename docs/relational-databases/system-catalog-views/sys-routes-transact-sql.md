---
title: Routes (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21420e923b4120f547026c6a6a0d96d86deac782
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Questa vista del catalogo contiene una riga per route. Le route vengono utilizzate da Service Broker per individuare l'indirizzo di rete per un servizio.   

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome della route, univoco all'interno del database. Non ammette i valori Null.|  
|**route_id**|**int**|Identificatore della route. Non ammette i valori Null.|  
|**principal_id**|**int**|Identificatore dell'entità di database proprietaria della route. Ammette valori Null.|  
|**remote_service_name**|**nvarchar(256)**|Nome del servizio remoto. Ammette valori Null.|  
|**broker_instance**|**nvarchar(128)**|Identificatore dell'istanza di Service Broker che ospita il servizio remoto. Ammette valori Null.|  
|**lifetime**|**datetime**|Data e ora di scadenza della route. Questo valore non utilizza il fuso orario locale, bensì corrisponde all'ora di scadenza per UTC. Ammette valori Null.|  
|**address**|**nvarchar(256)**|Indirizzo di rete a cui Service Broker invia messaggi per il servizio remoto. Ammette valori Null. Per l'istanza gestita di Database SQL, l'indirizzo deve essere locale.|  
|**mirror_address**|**nvarchar(256)**|Indirizzo di rete del partner per il mirroring per il server specificato nell'indirizzo. Ammette valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
