---
title: sys.dm_db_rda_schema_update_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbd99f97902dbbd3c097b76b1f119f400f97c6f6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420060"
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Stretch Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni attività di aggiornamento dello schema per l'archivio dati remoto di ogni tabella abilitata per Stretch nel database corrente. Le attività vengono identificate con i relativi ID di attività.  
  
 **dm_db_rda_schema_update_status** ha come ambito il contesto del database corrente. Assicurarsi che trovano nel contesto di database della tabella abilitata per l'estensione per il quale si desidera visualizzare lo stato di aggiornamento dello schema.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|L'ID della tabella abilitata per l'estensione locale i cui dati remoti archiviare dello schema viene aggiornato.|  
|**database_id**|**int**|L'ID del database contenente la tabella abilitata per l'estensione locale.|  
|**task_id**|**bigint**|ID dell'attività Aggiorna schema archivio dati remoto.|  
|**task_type**|**int**|Tipo dell'attività di aggiornamento dello schema di archivio dati remoto.|  
|**task_type_desc**|**nvarchar**|La descrizione del tipo dell'attività di aggiornamento dello schema di archivio dati remoto.|  
|**task_state**|**int**|Lo stato dell'attività aggiornamento dello schema archivio dati remoto.|  
|**task_state_des**|**nvarchar**|La descrizione dello stato dell'attività Aggiorna schema archivio dati remoto.|  
|**start_time_utc**|**datetime**|L'ora UTC in cui i dati remoti archiviare aggiornamento dello schema di avvio.|  
|**end_time_utc**|**datetime**|L'ora UTC in cui i dati remoti archiviare aggiornamento dello schema completata.|  
|**error_number**|**int**|Se l'aggiornamento dello schema di archivio dati remoto non riesce, il numero di errore dell'errore che si sono verificati. in caso contrario, null.|  
|**error_severity**|**int**|Se l'aggiornamento dello schema di archivio dati remoto non riesce, la gravità dell'errore che si sono verificati. in caso contrario, null.|  
|**error_state**|**int**|Se l'aggiornamento dello schema di archivio dati remoto non riesce, lo stato dell'errore che si sono verificati. in caso contrario, null. Il error_state indica la condizione o un percorso in cui si è verificato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
