---
title: '! (Not logico) (espressione SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
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
manager: jhubbard
ms.openlocfilehash: 7de99bf9dc767c5f4f6e47abd88f66f874ebb1be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055943"
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
 Qualsiasi espressione valida che restituisce un valore booleano. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
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
  
 In questo esempio viene restituito TRUE se il valore della variabile **MonthNumber** è uguale all'Integer che rappresenta il mese corrente. Per altre informazioni, vedere [MONTH &#40;espressione SSIS&#41;](month-ssis-expression.md) e [GETDATE &#40;espressione SSIS&#41;](getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Associatività e precedenza operatori](operator-precedence-and-associativity.md)   
 [Gli operatori &#40;espressione SSIS&#41;](operators-ssis-expression.md)  
  
  