---
title: MSmerge_identity_range (Transact-SQL) | Documenti Microsoft
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
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 07dbde0d56a787a3361f77b2d231cb0b2e48ee5f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_identity_range** tabella viene utilizzata per tenere traccia degli intervalli numerici assegnati alle colonne di identità per la sottoscrizione di pubblicazioni in cui la replica gestisce automaticamente tali assegnazioni di intervalli. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Numero di identificazione univoco per la sottoscrizione specificata.|  
|**artid**|**uniqueidentifier**|Identificatore univoco per l'articolo specificato.|  
|**range_begin**|**Numeric(38)**|Valore Identity all'inizio dell'intervallo corrente.|  
|**range_end**|**Numeric(38)**|Valore Identity alla fine dell'intervallo corrente.|  
|**next_range_begin**|**Numeric(38)**|Valore Identity all'inizio dell'intervallo successivo da assegnare.|  
|**next_range_end**|**Numeric(38)**|Valore Identity alla fine dell'intervallo successivo da assegnare.|  
|**is_pub_range**|**bit**|Il valore **1** se l'intervallo di valori identity viene assegnato alla pubblicazione.|  
|**max_used**|**Numeric(38)**|Valore Identity massimo che può essere assegnato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
