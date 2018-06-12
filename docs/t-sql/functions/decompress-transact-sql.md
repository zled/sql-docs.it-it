---
title: DECOMPRESS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2b6412856e373c3b1ad5ac838f9b15486d451a2b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779197"
---
# <a name="decompress-transact-sql"></a>DECOMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Questa funzione decomprime il valore di un'espressione di input usando l'algoritmo GZIP. `DECOMPRESS` restituisce una matrice di byte (tipo VARBINARY(MAX)).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
Valore **varbinary(***n***)**, **varbinary(max)** o **binary(***n***)**. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
Un valore con tipo di dati **varbinary(max)**. Per decomprimere l'argomento di input, `DECOMPRESS` usa l'algoritmo ZIP. Se necessario, l'utente deve eseguire esplicitamente il cast del risultato a un tipo di destinazione.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-decompress-data-at-query-time"></a>A. Decompressione dei dati al momento della query  
Questo esempio viene illustra come restituire i dati di una tabella compressa:  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>B. Visualizzare i dati compressi usando una colonna calcolata  
Questo esempio illustra come creare una tabella per l'archiviazione dei dati decompressi:  
  
```  
CREATE TABLE example_table (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni stringa &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS &#40;Transact-SQL&#41;](../../t-sql/functions/compress-transact-sql.md)  
  
  
