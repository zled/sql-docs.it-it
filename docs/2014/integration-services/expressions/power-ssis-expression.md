---
title: POWER (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f9c5a718c7a7eef173bcd7c6beae33cda1e3323
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155671"
---
# <a name="power-ssis-expression"></a>POWER (espressione SSIS)
  Restituisce il risultato dell'elevamento a potenza di un'espressione numerica. Il parametro power deve restituire un valore integer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
 *power*  
 Espressione numerica valida.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_R8  
  
## <a name="remarks"></a>Note  
 Prima del calcolo della potenza, viene eseguito il cast degli argomenti *numeric_expression* e *power* nel tipo di dati DT_R8. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
 Se *numeric_expression* restituisce zero e *power* è negativo, l'analizzatore di espressioni restituisce un errore e imposta il risultato restituito su Null.  
  
 Se *numeric_expression* o *power* restituisce risultati indeterminati, viene restituito Null.  
  
 L'argomento *power* può essere una frazione. ad esempio 0,5.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene utilizzato un valore letterale numerico. La funzione eleva 4 all'esponente 3 e restituisce 64.  
  
```  
POWER(4,3)  
```  
  
 Questo esempio usa la colonna **Length** e la variabile **DimensionCount** . Se **Length** è 8 e **DimensionCount** è 2, il risultato restituito è 64.  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  
