---
title: '@@MAX_PRECISION (Transact-SQL) | Documenti Microsoft'
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
- '@@MAX_PRECISION_TSQL'
- '@@MAX_PRECISION'
dev_langs:
- TSQL
helpviewer_keywords:
- precision [SQL Server], @@MAX_PRECISION
- numeric data type, precision level
- decimal data type, precision level
- '@@MAX_PRECISION function'
- data types [SQL Server], precision
ms.assetid: 9e7158a1-e503-422a-b326-3c9b06e181b2
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 530dc9cd780d9dae2df1c326fcd1cc070450290a
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40maxprecision-transact-sql"></a>& #x 40; & #x 40; MAX_PRECISION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il livello di precisione utilizzato dai **decimale** e **numerico** tipi di dati è attualmente impostato nel server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@MAX_PRECISION  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **tinyint**  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, la precisione massima restituisce 38.  
  
## <a name="examples"></a>Esempi  
  
```  
SELECT @@MAX_PRECISION AS 'Max Precision'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Decimal e numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [Precisione, scala e lunghezza &#40; Transact-SQL &#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)  
  
  

