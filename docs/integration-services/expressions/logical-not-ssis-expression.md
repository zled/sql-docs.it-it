---
title: '! (Not logico) (espressione SSIS) | Microsoft Docs'
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
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ed910ae4b31c3fc9cc3a48202a2267025469056
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="-logical-not-ssis-expression"></a>! (Not logico) (espressione SSIS)
  NOT logico di un operando booleano.  
  
> [!NOTE]  
>  L'operatore ! non può essere utilizzato in combinazione con altri operatori. Non è ad esempio possibile combinare gli operatori ! e > in modo da formare l'operatore !> .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression*  
 Qualsiasi espressione valida che restituisce un valore booleano. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 Il risultato dell'operazione ! è illustrato nella tabella seguente .  
  
|Espressione booleana originale|Dopo l'applicazione dell'operatore ! operatore|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito FALSE se il valore della colonna **Color** è "red".  
  
```  
!(Color == "red")  
```  
  
 In questo esempio viene restituito TRUE se il valore della variabile **MonthNumber** è uguale all'Integer che rappresenta il mese corrente. Per altre informazioni, vedere [MONTH &#40;espressione SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md) e [GETDATE &#40;espressione SSIS&#41;](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
