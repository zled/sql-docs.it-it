---
title: ABS (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b68fad1ec73daeb19690adefbfe3a2e5b0bac05b
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="abs-ssis-expression"></a>ABS (espressione SSIS)
  Restituisce il valore positivo assoluto di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica con o senza segno.  
  
## <a name="result-types"></a>Tipi restituiti  
 Tipo di dati dell'espressione numerica inviata alla funzione.  
  
## <a name="remarks"></a>Remarks  
 Se l'argomento è Null, ABS restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi la funzione ABS viene applicata a un numero positivo e a un numero negativo. In entrambi i casi viene restituito 1,23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 In questo esempio la funzione ABS viene applicata a un'espressione che esegue una sottrazione tra i valori delle variabili **HighTemperature** e **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
