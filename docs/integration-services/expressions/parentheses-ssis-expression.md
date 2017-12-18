---
title: () (parentesi) (espressione SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: "36"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1dde4602208caf4bd12218903af8972ca01f7410
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="-parentheses-ssis-expression"></a>() (parentesi) (espressione SSIS)
  Viene identificato l'ordine di valutazione delle espressioni. Le espressioni racchiuse tra parentesi hanno la massima precedenza di valutazione. Le espressioni nidificate racchiuse tra parentesi vengono valutate procedendo dall'interno verso l'esterno.  
  
 È possibile utilizzare le parentesi anche per semplificare la comprensione delle espressioni complesse.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Qualsiasi espressione valida.  
  
## <a name="result-types"></a>Tipi restituiti  
 Tipo di dati di *espressione*. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene illustrato come l'utilizzo delle parentesi modifichi la precedenza degli operatori. La prima espressione restituisce 100, mentre la seconda restituisce 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
