---
title: '&amp; (assegnazione AND bit per bit) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '&='
- '&=_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, &=
- assignment operators, &=
- augmented operators, &=
- '&= (bitwise AND equals)'
ms.assetid: f374c885-3fee-434a-93fb-dfe6e0bcd100
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a49fe5eeeab887425d3f8a5f47feb0a166dcc1f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668069"
---
# <a name="amp-bitwise-and-assignment-transact-sql"></a>&amp; (assegnazione AND bit per bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]


  Esegue un'operazione con AND logico bit per bit tra due valori integer e imposta un valore sul risultato dell'operazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression &= expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida di un qualsiasi tipo di dati della categoria numerica, ad eccezione del tipo di dati **bit**.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'argomento con la priorità più alta. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Per altre informazioni, vedere [& &#40;AND bit per bit&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori composti &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
