---
title: Precedenza dei tipi di dati (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5041c1a8603493f22a5fccd63c089ba11e9a8be0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-type-precedence-transact-sql"></a>Precedenza dei tipi di dati (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Quando due espressioni di tipi di dati diversi vengono combinate da un operatore, le regole per la precedenza dei tipi di dati specificano che i tipi con precedenza inferiore vengano convertiti nei tipi con precedenza superiore. Se la conversione non è una conversione implicita supportata, viene generato un errore. Se a entrambe le espressioni dell'operando è associato lo stesso tipo di dati, quest'ultimo viene assegnato al risultato dell'operazione.
  
Per i tipi di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza l'ordine di precedenza seguente:
  
1.  Tipi di dati definiti dall'utente (superiore)  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **data**  
1. **time**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (incluso **nvarchar(max)** )  
1. **nchar**  
1. **varchar** (incluso **varchar(max)** )  
1. **char**  
1. **varbinary** (incluso **varbinary(max)** )  
1. **binary** (inferiore)  
  
## <a name="see-also"></a>Vedere anche
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
