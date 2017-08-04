---
title: EXP (espressione SSIS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ad14b1426435034ef5f4371cc8bb6904b536798
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="exp-ssis-expression"></a>EXP (espressione SSIS)
  Viene restituito l'esponente in base e di un'espressione numerica. EXP è la funzione inversa della funzione LN ed è talvolta chiamata antilogaritmo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_R8  
  
## <a name="remarks"></a>Osservazioni  
 Prima del calcolo dell'esponente viene eseguito il cast dell'espressione numerica al tipo di dati DT_R8. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Il risultato restituito è sempre un numero positivo.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi la funzione EXP viene applicata a valori positivi e negativi e allo zero.  
  
```  
EXP(74)  
```  
  
 Restituisce 1,373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Restituisce 1,879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Restituisce 1.  
  
## <a name="see-also"></a>Vedere anche  
 [LOG &#40; Espressione SSIS &#41;](../../integration-services/expressions/log-ssis-expression.md)   
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
