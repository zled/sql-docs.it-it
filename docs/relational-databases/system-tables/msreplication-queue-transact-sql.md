---
title: MSreplication_queue (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25bbbc37215010d60cd20a01ea06cb35176eabf5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="msreplicationqueue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSreplication_queue** tabella viene utilizzata dal processo di replica per archiviare i comandi in coda eseguiti da tutte le sottoscrizioni ad aggiornamento in coda che utilizzano basato su SQL in coda. Questa tabella è archiviata nel database di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database di pubblicazione.|  
|**pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**tranid**|**sysname**|ID di transazione utilizzato per l'esecuzione del comando in coda.|  
|**dati**|**varbinary (8000)**|Flusso di byte compresso in cui sono archiviate informazioni sul comando in coda.|  
|**datalen**|**int**|Lunghezza dei dati in byte.|  
|**CommandType**|**int**|Tipo di comando che viene inserito in coda:<br /><br /> 1 = Comando utente nella transazione.<br /><br /> 2 = Comando di sincronizzazione della sottoscrizione.|  
|**insertdate**|**datetime**|Data dell'inserimento.|  
|**oggetto orderkey**|**bigint**|Colonna Identity incrementata in modo monotonico.|  
|**cmdstate**|**bit**|Stato del comando:<br /><br /> 0 = Completo.<br /><br /> 1 = Parziale.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
