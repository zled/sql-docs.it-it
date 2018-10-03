---
title: LOWER (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1468e205f6d7a368b9b4af2a693fd369e11af233
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050084"
---
# <a name="lower-ssis-expression"></a>LOWER (espressione SSIS)
  Viene restituita un'espressione di caratteri dopo aver convertito i caratteri maiuscoli in caratteri minuscoli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da convertire in caratteri minuscoli.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Note  
 È possibile utilizzare LOWER solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da LOWER verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](cast-ssis-expression.md).  
  
 Se l'argomento è Null, LOWER restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio un valore letterale stringa viene convertito in caratteri minuscoli. Il risultato restituito è "new york".  
  
```  
LOWER("New York")  
```  
  
 In questo esempio tutti i caratteri della colonna di input **Color** , ad eccezione del primo, vengono convertiti in caratteri minuscoli. Se Color ha valore YELLOW, il risultato restituito sarà "Yellow". Per altre informazioni, vedere [SUBSTRING &#40;espressione SSIS&#41;](substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 In questo esempio il valore della variabile **CityName** viene convertito in caratteri minuscoli.  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTO &#40;espressione di SSIS&#41;](upper-ssis-expression.md)   
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  
