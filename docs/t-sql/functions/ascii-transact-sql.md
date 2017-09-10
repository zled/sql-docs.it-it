---
title: ASCII (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASCII_TSQL
- ASCII
dev_langs:
- TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d2c65df1f005b3d624f6a56f689f4125ec8175a7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il codice ASCII del carattere più a sinistra in un'espressione di caratteri.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
*character_expression*  
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) del tipo **char** o **varchar**.
  
## <a name="return-types"></a>Tipi restituiti
 **int**  
  
## <a name="remarks"></a>Osservazioni
ASCII è un'abbreviazione per il codice Standard American interscambio di informazioni. È un carattere di codifica standard utilizzato dai computer. Per un elenco di caratteri ASCII, vedere il **caratteri stampabili** sezione [ASCII](https://www.wikipedia.org/wiki/ASCII).

## <a name="examples"></a>Esempi  
Nell'esempio seguente si presuppone che un set di caratteri ASCII e restituisce il `ASCII` valore di 6 caratteri.
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)
  
  



