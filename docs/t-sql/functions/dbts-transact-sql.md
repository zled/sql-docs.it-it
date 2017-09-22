---
title: '@@DBTS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 4a90150c55cdeb89788fdb86faf8aef8a1efdcd2
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40dbts-transact-sql"></a>& #x 40; & #x 40; DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il valore corrente a cui è associato il tipo di dati **timestamp** per il database corrente. Il timestamp è sicuramente univoco nel database.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>Tipi restituiti
**varbinary**
  
## <a name="remarks"></a>Osservazioni  
@@DBTS restituisce il valore utilizzato per ultimo timestamp del database corrente. Un nuovo valore timestamp viene generato quando si inserisce o si aggiorna una riga che include una colonna di tipo **timestamp** .
  
Il @@DBTS funzione non è interessata dalle modifiche apportate ai livelli di isolamento delle transazioni.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente restituisce l'attuale **timestamp** dal [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni di configurazione &#40; Transact-SQL &#41;](../../t-sql/functions/configuration-functions-transact-sql.md)  
[Concorrenza dei cursori &#40; ODBC &#41;](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40; Transact-SQL &#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  

