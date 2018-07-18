---
title: RAND (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dc446b6a3c858f62db20ca14ec54ddf2188cf163
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792152"
---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Restituisce un valore **float** pseudocasuale compreso tra 0 e 1 (esclusi).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *seed*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) Integer (**tinyint**, **smallint** o **int**) che specifica il valore di inizializzazione. Se *seed* è omesso, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] assegna un valore di inizializzazione in modo casuale. Per un valore di inizializzazione specificato, il risultato restituito è sempre lo stesso.  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Remarks  
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
 [Funzioni matematiche &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
