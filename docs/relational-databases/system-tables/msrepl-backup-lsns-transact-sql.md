---
title: MSrepl_backup_lsns (Transact-SQL) | Documenti Microsoft
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
applies_to:
- SQL Server
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e7890061f190404c98862dc17a1f7ba2f52ebf33
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msreplbackuplsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSrepl_backup_lsns** tabella contiene i numeri di sequenza del log delle transazioni (LSN) per supportare l'opzione 'sync with backup' del database di distribuzione. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|ID del database del server di pubblicazione.|  
|**valid_xact_id**|**varbinary(16)**|ID della transazione da inviare al server di pubblicazione per contrassegnare il punto di troncamento del log. Viene utilizzato solo se il database di distribuzione è in modalità 'sync with backup'. Corrisponde all'ID dell'ultima transazione replicata nel database di distribuzione di cui è stato eseguito il backup. Viene inviato al server di pubblicazione per consentire all'agente di lettura log di contrassegnare il punto di troncamento del log.|  
|**valid_xact_seqno**|**varbinary(16)**|Numero di sequenza della transazione da inviare al server di pubblicazione per contrassegnare il punto di troncamento del log. Viene utilizzato solo se il database di distribuzione è in modalità 'sync with backup'. Corrisponde al numero di sequenza del file di log (LSN) dell'ultima transazione di replica nel database di distribuzione di cui è stato eseguito il backup. Viene inviato al server di pubblicazione per consentire all'agente di lettura log di contrassegnare il punto di troncamento del log.|  
|**next_xact_id**|**varbinary(16)**|Numero di sequenza del file di log (LSN) temporaneo utilizzato nelle operazioni di backup.|  
|**nextx_xact_seqno**|**varbinary(16)**|Numero di sequenza del file di log (LSN) temporaneo utilizzato nelle operazioni di backup.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
