---
title: Funzioni di aggregazione (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a97d68c641d2a3deb1d3fd3a674f65cafc3854c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="aggregate-functions-transact-sql"></a>Funzioni di aggregazione (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Le funzioni di aggregazione eseguono un calcolo su un set di valori e restituiscono un singolo valore. Ad eccezione della funzione COUNT, le funzioni di aggregazione ignorano i valori Null. Vengono spesso utilizzate con la clausola GROUP BY dell'istruzione SELECT.
  
Tutte le funzioni di aggregazione sono deterministiche. Ciò significa che le funzioni di aggregazione restituiscono lo stesso valore ogni volta che vengono chiamate con un set specifico di valori di input. Per ulteriori informazioni sulle funzioni deterministiche, vedere [funzioni deterministiche e non](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). Il [clausola OVER](../../t-sql/queries/select-over-clause-transact-sql.md) può seguire tutte le funzioni di aggregazione, ad eccezione di GROUPING e GROUPING_ID.
  
È possibile utilizzare le funzioni di aggregazione come espressioni solo nei casi seguenti:
-   Nell'elenco di selezione di un'istruzione SELECT (una sottoquery o una query esterna).  
-   Nella clausola HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] include le funzioni di aggregazione seguenti:
  
|||  
|-|-|  
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[MIN](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[SOMMA](../../t-sql/functions/sum-transact-sql.md)|  
|[CONTEGGIO](../../t-sql/functions/count-transact-sql.md)|[FUNZIONE STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[FUNZIONE STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[RAGGRUPPAMENTO](../../t-sql/functions/grouping-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)||  
  
## <a name="see-also"></a>Vedere anche
[Funzioni predefinite &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)  
[IN una clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  

