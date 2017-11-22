---
title: Sys.dm db_rda_migration_status (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 088300f865265f330a06e40b7712fa63fd89f02a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Estensione Database - Sys.dm db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni batch di dati migrati da ogni tabella abilitata per l'estensione nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Batch sono identificati da ora di inizio e ora di fine.  
  
 **Sys.dm db_rda_migration_status** l'ambito è il contesto del database corrente. Assicurarsi di essere nel contesto del database delle tabelle di abilitazione di estensione per il quale si desidera visualizzare lo stato di migrazione.  
  
 In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], l'output di **Sys.dm db_rda_migration_status** è limitato a 200 righe.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|L'ID della tabella da cui è sono eseguita la migrazione di righe.|  
|**database_id**|**int**|L'ID del database da cui è sono eseguita la migrazione di righe.|  
|**migrated_rows**|**bigint**|Il numero di righe migrate nel batch.|  
|**start_time_utc**|**datetime**|L'ora UTC in cui è iniziato il batch.|  
|**end_time_utc**|**datetime**|L'ora UTC in cui il batch è stata completata.|  
|**error_number**|**int**|Se il batch ha esito negativo, il numero di errore dell'errore che si sono verificati. in caso contrario, null.|  
|**error_severity**|**int**|Se il batch ha esito negativo, il livello di gravità dell'errore che si sono verificati. in caso contrario, null.|  
|**error_state**|**int**|Se il batch ha esito negativo, lo stato dell'errore che si sono verificati. in caso contrario, null.<br /><br /> Il **error_state** indica la condizione o un percorso in cui si è verificato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
