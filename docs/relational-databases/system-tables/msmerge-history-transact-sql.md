---
title: MSmerge_history (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1e28c0aae7f29099ebef75d5c0aa7ef81eec0379
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_history** tabella contiene righe di cronologia con descrizioni dettagliate dei risultati delle precedenti sessioni dei processi dell'agente di Merge. Questa tabella contiene una riga per ogni riga dell'output dell'agente. Questa tabella viene utilizzata nel database di distribuzione e in ogni database di sottoscrizione. Nel database di distribuzione contiene la cronologia per tutte le pubblicazioni di tipo merge e le sottoscrizioni che utilizzano il server di distribuzione. In ogni database di sottoscrizione contiene la cronologia per le pubblicazioni sottoscritte dal Sottoscrittore.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID del processo dell'agente di merge.|  
|**agent_id**|**int**|ID dell'agente di merge.|  
|**Commenti**|**nvarchar(255)**|Testo del messaggio.|  
|**error_id**|**int**|L'ID di un errore nel [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) tabella di sistema.|  
|**timestamp**|**timestamp**|Colonna timestamp della tabella.|  
|**updatable_row**|**bit**|Impostare su **1** se la riga di cronologia può essere sovrascritto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
