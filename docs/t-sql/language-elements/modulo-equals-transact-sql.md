---
title: '% = (Operatore di assegnazione) (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%=_TSQL'
- '%='
dev_langs: TSQL
helpviewer_keywords:
- '%= (modulo equals)'
- '%= (modulus assignment)'
- compound operators, %=
- assignment operators, %=
- augmented operators, %=
ms.assetid: 45e35516-1f4c-406b-a580-70a14b087847
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 064b586b1e6bbf10828ce7dfa1f8d759e5201e85
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="-modulus-assignment-transact-sql"></a>%= (Modulus Assignment) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue la divisione tra due numeri e imposta un valore sul risultato dell'operazione. Ad esempio, se una variabile @x è uguale a 38, quindi @x % = 5 accetta il valore originale di @x, divisione per 5 e imposta @x al resto della divisione (3).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression %= expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno qualsiasi dei dati tipi della categoria numerica, ad eccezione di **bit** tipo di dati.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'argomento con la priorità più alta. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni, vedere [% &#40; Modulo &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/modulo-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
