---
title: EXP (espressione SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c45673700f84d108b3ed9a6f64f780e007c00d7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
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
  
## <a name="remarks"></a>Remarks  
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
 [LOG &#40;espressione SSIS&#41;](../../integration-services/expressions/log-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
