---
title: MSrepl_identity_range (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a6e439f85f10242d8c11fa24ba74326f8986bdc4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005988"
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSrepl_identity_range** tabella fornisce il supporto di gestione di identità intervallo. Questa tabella è archiviata nei database di pubblicazione, distribuzione e sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database di pubblicazione.|  
|**TableName**|**sysname**|Nome della tabella.|  
|**identity_support**|**int**|Specifica se è attivata la gestione automatica degli intervalli di valori Identity. 0 specifica che tale gestione non è attivata.|  
|**next_seed**|**bigint**|Se la gestione automatica degli intervalli di valori Identity è attivata, indica il punto iniziale dell'intervallo successivo.|  
|**pub_range**|**bigint**|Dimensioni dell'intervallo di valori Identity del server di pubblicazione.|  
|**intervallo**|**bigint**|Dimensioni dei valori Identity consecutivi che verrebbero assegnati nei Sottoscrittori durante un intervento di regolazione.|  
|**max_identity**|**bigint**|Limite massimo dell'intervallo di valori Identity.|  
|**Soglia**|**int**|Percentuale di soglia dell'intervallo di valori Identity.|  
|**current_max**|**bigint**|Valore massimo corrente che è possibile assegnare, ma che non viene necessariamente assegnato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
