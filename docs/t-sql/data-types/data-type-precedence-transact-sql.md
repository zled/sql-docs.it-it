---
title: Tipo di dati precedenza (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/23/2017
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
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f39337e00dfdbcd4a6bb01a00093a61f46a79fa
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-precedence-transact-sql"></a>Precedenza tipo di dati (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
1. **nvarchar** (inclusi **nvarchar (max)** )  
1. **nchar**  
1. **varchar** (inclusi **varchar (max)** )  
1. **char**  
1. **varbinary** (inclusi **varbinary (max)** )  
1. **binario** (minimo)  
  
## <a name="see-also"></a>Vedere anche
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

