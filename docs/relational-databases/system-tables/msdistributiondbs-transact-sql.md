---
title: MSdistributiondbs (Transact-SQL) | Documenti Microsoft
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
- MSdistributiondbs_TSQL
- MSdistributiondbs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistributiondbs system table
ms.assetid: d7ffa9df-bf1d-41b8-837e-b762c17c2764
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a616111951170d264e61bc40ff0691806ca2ebaf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33004158"
---
# <a name="msdistributiondbs-transact-sql"></a>MSdistributiondbs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdistributiondbs** tabella contiene una riga per ogni database di distribuzione nel server di distribuzione locale. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del database di distribuzione.|  
|**min_distretention**|**int**|Periodo di memorizzazione minimo, espresso in ore, che deve trascorrere prima dell'eliminazione delle transazioni.|  
|**max_distretention**|**int**|Periodo di memorizzazione massimo, espresso in ore, trascorso il quale le transazioni vengono eliminate.|  
|**history_retention**|**int**|Numero di ore di memorizzazione della cronologia.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
