---
title: COUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COUNT_BIG_TSQL
- COUNT_BIG
dev_langs:
- TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT_BIG function
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT_BIG function
ms.assetid: f2e3601f-487e-4917-bb01-47b1047908cd
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0701b86454205e9b83733f034b708bb18f45feff
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="countbig--sql"></a>COUNT_BIG (-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Consente di restituire il numero di elementi di un gruppo. Il funzionamento di COUNT_BIG è analogo a quello della funzione COUNT. L'unica differenza è il valore restituito. COUNT_BIG restituisce sempre un valore con tipo di dati **bigint**. COUNT restituisce sempre un valore con tipo di dati **int**.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT_BIG ( { [ ALL | DISTINCT ] expression } | * )  
   [ OVER ( [ partition_by_clause ] [ order_by_clause ] ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Aggregation Function Syntax  
COUNT_BIG ( { [ [ ALL | DISTINCT ] expression ] | * } )  
  
-- Analytic Function Syntax  
COUNT_BIG ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Argomenti  
ALL  
Applica la funzione di aggregazione a tutti i valori. Il valore predefinito è ALL.
  
DISTINCT  
Specifica che COUNT_BIG deve restituire il numero di valori univoci non Null.
  
*expression*  
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo. Non è possibile utilizzare funzioni di aggregazione e sottoquery.
  
*\**  
Specifica il conteggio di tutte le righe in modo che venga restituito il numero totale delle righe di una tabella. COUNT_BIG(*\**) non accetta parametri e non può essere usata con DISTINCT. Inoltre COUNT_BIG(*\**) non richiede un parametro *expression* perché per definizione non usa informazioni relative a colonne particolari. COUNT_BIG(*\**) restituisce il numero di righe della tabella specificata senza eliminare i duplicati. Ogni riga viene contata separatamente, incluse le righe contenenti valori Null.
  
ALL  
Applica la funzione di aggregazione a tutti i valori. Il valore predefinito è ALL.
  
DISTINCT  
Indica che la funzione AVG deve essere eseguita solo in ogni istanza univoca di un valore, indipendentemente dal numero di occorrenze del valore.
  
*expression*  
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) della categoria di tipi di dati numerici esatti o numerici approssimativi, ad eccezione del tipo di dati **bit**. Non è possibile utilizzare funzioni di aggregazione e sottoquery.
  
OVER **(** [ *partition_by_clause* ] [ *order_by_clause* ] **)**  
*partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni alle quali viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine logico in cui viene eseguita l'operazione. Per altre informazioni, vedere [Clausola OVER &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Tipi restituiti
**bigint**
  
## <a name="remarks"></a>Remarks  
COUNT_BIG(*) restituisce il numero di elementi in un gruppo, inclusi valori NULL e duplicati.
  
COUNT_BIG (ALL *expression*) valuta *expression* per ogni riga in un gruppo e restituisce il numero di valori non Null.
  
COUNT_BIG (DISTINCT *expression*) valuta *expression* per ogni riga in un gruppo e restituisce il numero di valori univoci non Null.
  
COUNT_BIG è una funzione deterministica quando viene utilizzata senza le clausole ORDER BY e OVER. Non è deterministica quando viene specificata con le clausole ORDER BY e OVER. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Esempi  
Per esempi, vedere [COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche
[Funzioni di aggregazione &#40;Transact-SQL&#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md)  
[int, bigint, smallint e tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
[Clausola OVER &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
