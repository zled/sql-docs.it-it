---
title: sys.dm_db_rda_schema_update_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ddbabbfd19d95412e07a4fd1fb56f73661f37581
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Estensione Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni attività di aggiornamento dello schema per l'archivio dati remoto di ogni tabella abilitata per l'estensione nel database corrente. Le attività sono identificate dai relativi ID di attività.  
  
 **dm_db_rda_schema_update_status** ha come ambito il contesto del database corrente. Verificare di disporre nel contesto del database della tabella abilitata per l'estensione per il quale si desidera visualizzare lo stato di aggiornamento dello schema.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|L'ID della tabella abilitata per l'estensione locale i cui dati remoti archiviare dello schema viene aggiornato.|  
|**database_id**|**int**|L'ID del database che contiene la tabella abilitata per l'estensione locale.|  
|**task_id**|**bigint**|ID dell'attività Aggiorna schema archivio dati remoto.|  
|**task_type**|**int**|Il tipo di attività Aggiorna schema archivio dati remoto.|  
|**task_type_desc**|**nvarchar**|La descrizione del tipo di attività Aggiorna schema archivio dati remoto.|  
|**task_state**|**int**|Stato dell'attività Aggiorna schema archivio dati remoto.|  
|**task_state_des**|**nvarchar**|Descrizione dello stato dell'attività Aggiorna schema archivio dati remoto.|  
|**start_time_utc**|**datetime**|L'ora UTC in cui i dati remoti archiviare aggiornamento dello schema di avvio.|  
|**end_time_utc**|**datetime**|L'ora UTC in cui i dati remoti archiviare aggiornamento dello schema completata.|  
|**error_number**|**int**|Se l'aggiornamento dello schema di archivio dati remoto non riesce, il numero di errore dell'errore che si sono verificati. in caso contrario, null.|  
|**error_severity**|**int**|Se l'aggiornamento dello schema di archivio dati remoto non riesce, la gravità dell'errore che si sono verificati. in caso contrario, null.|  
|**error_state**|**int**|Se l'aggiornamento dello schema di archivio dati remoto non riesce, lo stato dell'errore che si sono verificati. in caso contrario, null. Il error_state indica la condizione o un percorso in cui si è verificato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
