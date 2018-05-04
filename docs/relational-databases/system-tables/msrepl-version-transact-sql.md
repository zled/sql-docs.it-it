---
title: MSrepl_version (Transact-SQL) | Documenti Microsoft
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
- MSrepl_version
- MSrepl_version_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_version system table
ms.assetid: c1330f03-940b-4564-ac42-6030c6e21173
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 72d1d8bd2bc774a3e00087611b3f5f5bacdbb3ee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msreplversion-transact-sql"></a>MSrepl_version (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSrepl_version** tabella contiene una riga con la versione corrente della replica installata. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**versione_principale**|**int**|Numero di versione principale del database di distribuzione.|  
|**versione_secondaria**|**int**|Numero di versione secondario del database di distribuzione.|  
|**Revisione**|**int**|Numero di revisione.|  
|**db_existed**|**bit**|Indica se il database di distribuzione esiste prima **sp_adddistributiondb** viene chiamato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
