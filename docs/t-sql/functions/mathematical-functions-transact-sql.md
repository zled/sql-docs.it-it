---
title: Funzioni matematiche (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- calculations [SQL Server]
- mathematical functions [SQL Server]
- functions [SQL Server], mathematical
ms.assetid: 46495a2e-81d0-4677-9d72-9db083cd1023
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ec4a6767acab606d6459b439683a88a0cae1caf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mathematical-functions-transact-sql"></a>Funzioni matematiche (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Le funzioni scalari elencate di seguito eseguono un calcolo basato in genere su valori di input passati come argomenti, e restituiscono un valore numerico:  
  
||||  
|-|-|-|  
|[ABS](../../t-sql/functions/abs-transact-sql.md)|[GRADI](../../t-sql/functions/degrees-transact-sql.md)|[RAND](../../t-sql/functions/rand-transact-sql.md)|  
|[ACOS](../../t-sql/functions/acos-transact-sql.md)|[EXP](../../t-sql/functions/exp-transact-sql.md)|[FUNZIONE ROUND](../../t-sql/functions/round-transact-sql.md)|  
|[ASIN](../../t-sql/functions/asin-transact-sql.md)|[FLOOR](../../t-sql/functions/floor-transact-sql.md)|[ACCESSO](../../t-sql/functions/sign-transact-sql.md)|  
|[ATAN](../../t-sql/functions/atan-transact-sql.md)|[LOG](../../t-sql/functions/log-transact-sql.md)|[SIN](../../t-sql/functions/sin-transact-sql.md)|  
|[ATN2](../../t-sql/functions/atn2-transact-sql.md)|[LOG10](../../t-sql/functions/log10-transact-sql.md)|[SQRT](../../t-sql/functions/sqrt-transact-sql.md)|  
|[LIMITE MASSIMO](../../t-sql/functions/ceiling-transact-sql.md)|[PI](../../t-sql/functions/pi-transact-sql.md)|[QUADRATO](../../t-sql/functions/square-transact-sql.md)|  
|[COS](../../t-sql/functions/cos-transact-sql.md)|[RISPARMIO ENERGIA](../../t-sql/functions/power-transact-sql.md)|[TAN](../../t-sql/functions/tan-transact-sql.md)|  
|[COT](../../t-sql/functions/cot-transact-sql.md)|[RADIANTI](../../t-sql/functions/radians-transact-sql.md)||  
  
> [!NOTE]  
>  Le funzioni aritmetiche, quali ABS, CEILING, DEGREES, FLOOR, POWER, RADIANS e SIGN, restituiscono un valore dello stesso tipo di dati del valore di input. Trigonometriche e altre funzioni, tra cui EXP, LOG, LOG10, SQUARE e SQRT, eseguire il cast dei relativi valori di input **float** e restituire un **float** valore.  
  
 Tutte le funzioni matematiche, ad eccezione di RAND, sono deterministiche, ovvero restituiscono sempre lo stesso risultato ogni volta che vengono chiamate con un set specifico di valori di input. RAND risulta deterministica solo quando si specifica un parametro per il valore di inizializzazione. Per ulteriori informazioni sulle funzioni deterministiche, vedere [funzioni deterministiche e non](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="see-also"></a>Vedere anche  
  [Operatori aritmetici &#40; Transact-SQL &#41;](../../t-sql/language-elements/arithmetic-operators-transact-sql.md)  
  [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  

