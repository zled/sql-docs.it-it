---
title: DECOMPRIMERE (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 11/30/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7918a9bce5afcd7ce59551a60fc7e3f2f318f492
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="decompress-transact-sql"></a>DECOMPRIMERE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Decomprimere l'espressione di input utilizzando l'algoritmo GZIP. Risultato della compressione è la matrice di byte (tipo varbinary (max)).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un **varbinary (***n***)**, **varbinary (max)**, o **binario (** *n***)**. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di **varbinary (max)** tipo. L'argomento di input viene decompresso utilizzando l'algoritmo ZIP. L'utente deve esplicitamente il cast del risultato a un tipo di destinazione se necessario.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-decompress-data-at-query-time"></a>A. Decomprimere i dati in fase di Query  
 Nell'esempio seguente viene illustrato come visualizzare dati di compressione di una tabella:  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>B. Visualizzare i dati compressi utilizzando la colonna calcolata  
 Nell'esempio seguente viene illustrato come creare una tabella per archiviare dati decompressi:  
  
```  
CREATE TABLE (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS &#40; Transact-SQL &#41;](../../t-sql/functions/compress-transact-sql.md)  
  
  

