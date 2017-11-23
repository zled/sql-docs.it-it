---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
caps.latest.revision: "10"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb41140783d4c334e7ee701f44d523ec68e41435
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Visualizza le dimensioni e il numero di righe per ogni partizione di una tabella in un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database.
  
![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ *database_name* . [ *schema_name* ]. | *schema_name* . ] *table_name*  
 L'una, due o tre parti della tabella da visualizzare.  Per due o nomi di tabella composto da tre parti, il nome devono essere racchiusa tra virgolette doppie (""). Utilizzo delle virgolette che racchiudono un nome di tabella composto da una parte è facoltativo.  
  
## <a name="permissions"></a>Permissions
Richiede **VIEW SERVER STATE** autorizzazione.
  
## <a name="result-sets"></a>Set di risultati  
Si tratta i risultati per il comando DBCC PDW_SHOWPARTITIONSTATS.
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|partition_number|int|Numero di partizioni.|  
|used_page_count|bigint|Numero di pagine utilizzate per i dati.|  
|reserved_page_count|bigint|Numero di pagine allocate alla partizione.|  
|row_count|bigint|Numero di righe nella partizione.|  
|pdw_node_id|int|Nodo di calcolo per i dati.|  
|distribution_id|int|Id di distribuzione per i dati.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Esempi di sintassi di base PDW_SHOWPARTITIONSTATS DBCC  
Gli esempi seguenti mostrano il numero di righe e di spazio utilizzato dalla partizione per la tabella FactInternetSales il [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] database.
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>Vedere anche
[Operazione DBCC PDW_SHOWEXECUTIONPLAN &#40; Transact-SQL &#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40; Transact-SQL &#41;](dbcc-pdw-showspaceused-transact-sql.md)  
  
