---
title: "(Divisione è uguale a) (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- /=_TSQL
- /=
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, /=
- /= (divide equals)
ms.assetid: 9ab25d1e-5c98-4dd7-b2cd-9f49499c86e7
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 796aa8801ebfff9d1bb3ef6e194eadaa907601d6
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="divide-equals-transact-sql"></a>(Divisione è uguale a) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue la divisione tra due numeri e imposta un valore sul risultato dell'operazione. Ad esempio, se una variabile @x è uguale a 34, quindi `@x /= 2` accetta il valore originale di @x, divisione per 2 e imposta @x nuovo valore (17).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression /= expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno qualsiasi dei dati tipi della categoria numerica, ad eccezione di **bit** tipo di dati.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'argomento con la priorità più alta. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni, vedere [&#40; divisione &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/divide-transact-sql.md).  

## <a name="examples"></a>Esempi  
L'esempio seguente imposta una variabile a 17. Utilizza quindi il `/=` operatore per impostare la variabile alla metà del relativo valore originale.  
```sql  
DECLARE @myVariable decimal(5,2);
SET @myVariable = 17.5;
SET @myVariable /= 2;
SELECT @myVariable AS ResultVariable;  
```
  
[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]  
|ResultVariable | 
|--- |
|8.75 |

## <a name="see-also"></a>Vedere anche  
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

