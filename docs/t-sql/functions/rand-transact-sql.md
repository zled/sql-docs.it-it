---
title: RAND (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1d358122487d3568167021ac3a296e1eb2d1974
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Restituisce una pseudo-casuali **float** valore compreso tra 0 e 1, esclusivo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *valore di inizializzazione*  
 È un numero intero [espressione](../../t-sql/language-elements/expressions-transact-sql.md) (**tinyint**, **smallint**, o **int**) che fornisce il valore di inizializzazione. Se *valore di inizializzazione* non viene specificato, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] assegna un valore di inizializzazione in modo casuale. Per un valore di inizializzazione specificato, il risultato restituito è sempre lo stesso.  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Osservazioni  
 Le chiamate ripetute della funzione RAND() con lo stesso valore di inizializzazione restituiscono gli stessi risultati.  
  
 Per una connessione, se si chiama RAND() con un valore di inizializzazione specificato, tutte le chiamate successive di RAND() restituiscono risultati basati sulla chiamata RAND() inizializzata. Ad esempio, la query seguente restituirà sempre la stessa sequenza di numeri.  
  
```  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti quattro numeri casuali diversi generati dalla funzione RAND.  
  
```  
DECLARE @counter smallint;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni matematiche &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
