---
title: MSmerge_contents (Transact-SQL) | Documenti Microsoft
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
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 14f004eea5240962740a544756301de6895a8bf8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_contents** tabella contiene una riga per ogni riga modificata nel database corrente perché è stato pubblicato. Questa tabella viene utilizzata durante il processo di unione per determinare le righe modificate. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Nome alternativo della tabella pubblicata.|  
|**ROWGUID**|**uniqueidentifier**|Identificatore della riga specificata.|  
|**generazione**|**bigint**|La generazione della riga identificata dal **tablenick** e **rowguid**.|  
|**partchangegen**|**bigint**|Generazione associata all'ultima modifica dei dati che potrebbe aver modificato l'appartenenza della riga a una pubblicazione filtrata.|  
|**derivazione**|**varbinary(501)**|Coppie di nome alternativo del Sottoscrittore e numero di versione utilizzate per memorizzare una cronologia delle modifiche apportate alla riga.|  
|**colvl**|**varbinary(7489)**|Informazioni sulla versione della colonna.|  
|**marcatore**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifica la riga padre di livello principale in **MSmerge_contents** (da **rowguid**) per ogni riga figlio corrispondente in un record logico.|  
|**logical_record_lineage**|**varbinary(501)**|Coppie di nome alternativo del Sottoscrittore e numero di versione utilizzate per memorizzare una cronologia delle modifiche apportate alla riga padre di livello principale in un record logico. Per tutte le righe figlio in un record logico, questo valore è NULL.|  
|**logical_relation_change_gen**|**bigint**|Valore di generazione associato all'ultima modifica che ha comportato il riallineamento nel record logico, in cui una riga esistente è stata inserita o eliminata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
