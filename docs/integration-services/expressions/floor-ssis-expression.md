---
title: FLOOR (espressione SSIS) | Documenti Microsoft
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
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9a4c5ee6351735c7f133cc93c082f7497b9b0dc1
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="floor-ssis-expression"></a>FLOOR (espressione SSIS)
  Restituisce il più alto valore integer minore o uguale a un'espressione numerica specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
## <a name="result-types"></a>Tipi restituiti  
 Tipo di dati numeric dell'espressione passata come argomento. Il risultato è rappresentato dalla parte intera del valore calcolato con tipo di dati corrispondente al tipo del parametro *numeric_expression*.  
  
## <a name="remarks"></a>Osservazioni  
 Se l'argomento è Null, FLOOR restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi la funzione FLOOR viene applicata a valori positivi, negativi e zero.  
  
```  
FLOOR(123.45)  
```  
  
 Restituisce 123,00.  
  
```  
FLOOR(-123.45)  
```  
  
 Restituisce -124,00.  
  
```  
FLOOR(0.00)  
```  
  
 Restituisce 0,00.  
  
## <a name="see-also"></a>Vedere anche  
 [CEILING &#40; Espressione SSIS &#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
