---
title: FLOOR (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb7c221ddca8bd07b0e75b616267f8efaaa8427e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199611"
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
  
## <a name="remarks"></a>Note  
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
 [CEILING &#40;espressione di SSIS&#41;](ceiling-ssis-expression.md)   
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  
