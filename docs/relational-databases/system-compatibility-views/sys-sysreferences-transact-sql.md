---
title: Sys.sysreferences (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysreferences
- sys.sysreferences_TSQL
- sysreferences
- sysreferences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysreferences compatibility view
- sysreferences system table
ms.assetid: 81276f13-202e-4e74-962d-46eb98c98d2e
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 85892a9153039d6e3a4ef3e8c0caa0cdf667db55
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syssysreferences-transact-sql"></a>sys.sysreferences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Include i mapping tra le definizioni del vincolo FOREIGN KEY e le colonne con riferimenti all'interno del database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|ID del vincolo FOREIGN KEY.|  
|**fkeyid**|**int**|ID della tabella di riferimento.|  
|**rkeyid**|**int**|ID della tabella con riferimenti.|  
|**rkeyindid**|**smallint**|ID dell'indice univoco nella tabella con riferimenti che include le colonne chiave con riferimenti.|  
|**keycnt**|**smallint**|Numero di colonne nella chiave.|  
|**forkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**fkeydbid**|**smallint**|Riservato.|  
|**rkeydbid**|**smallint**|Riservato.|  
|**fkey1**|**smallint**|ID della colonna di riferimento.|  
|**fkey2**|**smallint**|ID della colonna di riferimento.|  
|**fkey3**|**smallint**|ID della colonna di riferimento.|  
|**fkey4**|**smallint**|ID della colonna di riferimento.|  
|**fkey5**|**smallint**|ID della colonna di riferimento.|  
|**fkey6**|**smallint**|ID della colonna di riferimento.|  
|**fkey7**|**smallint**|ID della colonna di riferimento.|  
|**fkey8**|**smallint**|ID della colonna di riferimento.|  
|**fkey9**|**smallint**|ID della colonna di riferimento.|  
|**fkey10**|**smallint**|ID della colonna di riferimento.|  
|**fkey11**|**smallint**|ID della colonna di riferimento.|  
|**fkey12**|**smallint**|ID della colonna di riferimento.|  
|**fkey13**|**smallint**|ID della colonna di riferimento.|  
|**fkey14**|**smallint**|ID della colonna di riferimento.|  
|**fkey15**|**smallint**|ID della colonna di riferimento.|  
|**fkey16**|**smallint**|ID della colonna di riferimento.|  
|**rkey1**|**smallint**|ID della colonna con riferimenti.|  
|**rkey2**|**smallint**|ID della colonna con riferimenti.|  
|**rkey3**|**smallint**|ID della colonna con riferimenti.|  
|**rkey4**|**smallint**|ID della colonna con riferimenti.|  
|**rkey5**|**smallint**|ID della colonna con riferimenti.|  
|**rkey6**|**smallint**|ID della colonna con riferimenti.|  
|**rkey7**|**smallint**|ID della colonna con riferimenti.|  
|**rkey8**|**smallint**|ID della colonna con riferimenti.|  
|**rkey9**|**smallint**|ID della colonna con riferimenti.|  
|**rkey10**|**smallint**|ID della colonna con riferimenti.|  
|**rkey11**|**smallint**|ID della colonna con riferimenti.|  
|**rkey12**|**smallint**|ID della colonna con riferimenti.|  
|**rkey13**|**smallint**|ID della colonna con riferimenti.|  
|**rkey14**|**smallint**|ID della colonna con riferimenti.|  
|**rkey15**|**smallint**|ID della colonna con riferimenti.|  
|**rkey16**|**smallint**|ID della colonna con riferimenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
