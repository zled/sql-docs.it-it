---
title: '*= (assegnazione di moltiplicazione) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '*=_TSQL'
- '*='
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, *=
- assignment operators, *=
- augmented operators, *=
- '*= (multiply equals)'
- '*= (multiplication assignment)'
ms.assetid: 816ff5dc-9a40-4c07-8351-39c194dbc079
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1cfe222e09a69f22d48f529d80da57b4cd2d73cf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36243543"
---
# <a name="-multiplication-assignment-transact-sql"></a>*= (assegnazione di moltiplicazione) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Moltiplica due numeri e imposta un valore sul risultato dell'operazione. Ad esempio, se una variabile @x è uguale a 35, all'espressione @x *= 2 viene assegnato il valore originale di @x, quindi viene moltiplicato per 2 e @x viene impostata sul nuovo valore (70).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression *= expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida di un qualsiasi tipo di dati della categoria numerica, ad eccezione del tipo di dati **bit**.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'argomento con la priorità più alta. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Per altre informazioni, vedere [&#42; &#40;moltiplicazione&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/multiply-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori composti &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
