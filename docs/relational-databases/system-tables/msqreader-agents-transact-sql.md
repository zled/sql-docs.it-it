---
title: MSqreader_agents (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSqreader_agents_TSQL
- MSqreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_agents system table
ms.assetid: dfa1f45e-c531-4385-a097-0a9edd1d7eab
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eb1a85b0a1c81b792f14afd428aa5e46c357b62d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842385"
---
# <a name="msqreaderagents-transact-sql"></a>MSqreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSqreader_agents** tabella contiene una riga per ogni agente di lettura coda eseguito nel server di distribuzione locale. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'agente di lettura coda.|  
|**name**|**Nvarchar(100)**|Nome dell'agente di lettura coda.|  
|**job_id**|**binary(16)**|Il numero di ID processo univoco **sysjobs** tabella.|  
|**profile_id**|**int**|L'ID del profilo dal **MSagent_profiles** tabella.|  
|**job_step_uid**|**uniqueidentifier**|ID univoco del passaggio di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in cui viene avviato l'agente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
