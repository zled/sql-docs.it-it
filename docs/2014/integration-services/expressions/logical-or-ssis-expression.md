---
title: '|| (OR logico) (espressione SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e63c829e1865213b29aca6e75d1de52021b4d5ac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052321"
---
# <a name="-logical-or-ssis-expression"></a>|| (OR logico) (espressione SSIS)
  Viene eseguita un'operazione con OR logico. Viene restituito TRUE dall'espressione se una o entrambe le condizioni sono TRUE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression1, boolean_expression2*  
 Qualsiasi espressione valida che restituisce TRUE, FALSE o NULL.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_BOOL  
  
## <a name="remarks"></a>Note  
 Il risultato dell'operatore || è illustrato nella tabella seguente.  
  
|Risultato|Espressione|Espressione|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Esempi di espressione SSIS  
 In questo esempio vengono utilizzate le colonne **StandardCost** e **ListPrice** . Viene restituito TRUE se il valore della colonna **StandardCost** è minore di 300 o quello della colonna **ListPrice** è maggiore di 500.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 In questo esempio vengono utilizzate le variabili **SPrice** e **LPrice** anziché valori letterali numerici.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#124;&#40;Bit per bit Inclusivo&#41; &#40;espressione di SSIS&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;OR esclusivo bit per bit&#41; &#40;Espressione SSIS&#41;](bitwise-exclusive-or-ssis-expression.md)   
 [Precedenza e associatività degli operatori](operator-precedence-and-associativity.md)   
 [Gli operatori &#40;espressione di SSIS&#41;](operators-ssis-expression.md)  
  
  
