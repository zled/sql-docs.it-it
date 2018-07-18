---
title: sysdbmaintplan_history (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70afaf6e607f5c8455747a42429f815a6616a8a5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdbmaintplanhistory-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa tabella è archiviata nel **msdb** database.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Sequenza della cronologia relativa ai piani di manutenzione del database.|  
|**plan_id**|**uniqueidentifier**|ID del piano di manutenzione del database.|  
|**plan_name**|**sysname**|Nome del piano di manutenzione del database.|  
|**database_name**|**sysname**|Nome del database associato al piano di manutenzione del database.|  
|**server_name**|**sysname**|Nome di sistema.|  
|**Attività**|**nvarchar(128)**|Attività eseguita dal piano di manutenzione del database, ad esempio Backup del log delle transazioni e così via.|  
|**succeeded**|**bit**|**0** = esito positivo **1** = esito negativo|  
|**end_time**|**datetime**|Ora in cui l'azione è stata completata.|  
|**duration**|**int**|Periodo di tempo richiesto per completare l'azione del piano di manutenzione del database.|  
|**start_time**|**datetime**|Ora in cui l'azione è iniziata.|  
|**error_number**|**int**|Numero di errore segnalato in caso di esito negativo.|  
|**message**|**nvarchar(512)**|Messaggio generato da **sqlmaint**.|  
  
  
