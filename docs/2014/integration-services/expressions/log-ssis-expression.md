---
title: LOG (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0d5a09e2b641828cacefb188859f5bd794d6e105
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085031"
---
# <a name="log-ssis-expression"></a>LOG (espressione SSIS)
  Viene restituito il logaritmo in base 10 di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida strettamente maggiore di zero.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_R8  
  
## <a name="remarks"></a>Note  
 Prima del calcolo del logaritmo viene eseguito il cast dell' *espressione numerica* al tipo di dati DT_R8. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
 Se tramite il parametro *numeric_expression* viene restituito zero o un valore negativo, il risultato sarà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene utilizzato un valore letterale numerico. La funzione restituisce 1,988291341907488.  
  
```  
LOG(97.34)  
```  
  
 In questo esempio viene usata la colonna **Length**. Se il valore della colonna è 101,24, la funzione restituirà 2,005352136486217.  
  
```  
LOG(Length)   
```  
  
 In questo esempio viene usata la variabile **Length**. La variabile deve avere un tipo di dati numeric o l'espressione deve includere un cast esplicito a un tipo di dati numeric di [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Se **Length** ha valore 234,567, la funzione restituirà 2,370266913465859.  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a>Vedere anche  
 [EXP &#40;espressione di SSIS&#41;](exp-ssis-expression.md)   
 [LN &#40;espressione SSIS&#41;](ln-ssis-expression.md)   
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  
