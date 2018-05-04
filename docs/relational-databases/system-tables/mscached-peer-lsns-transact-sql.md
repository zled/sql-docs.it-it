---
title: MScached_peer_lsns (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 31e7f3edbed18158ceb2343796796b9491c252fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mscachedpeerlsns-transact-sql"></a>MScached_peer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MScached_peer_lsns** tabella viene utilizzata per rilevare i LSN nel log delle transazioni che vengono utilizzati per determinare i comandi da restituire a un determinato sottoscrittore nella replica peer-to-peer. Questa tabella è archiviata nel database di distribuzione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ID dell'agente di distribuzione.|  
|**originator**|**sysname**|Nome del server di pubblicazione di origine.|  
|**originator_db**|**sysname**|Nome del database di pubblicazione di origine.|  
|**originator_publication_id**|**int**|Identifica la pubblicazione di origine.|  
|**originator_db_version**|**int**|Identifica il numero di versione del database di origine.|  
|**originator_lsn**|**varbinary(16)**|LSN della transazione di origine.|  
  
## <a name="remarks"></a>Osservazioni  
 Gli LSN vengono utilizzati solo immediatamente dopo l'inserimento e non hanno un significato permanente nel sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
