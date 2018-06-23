---
title: '&amp;&amp; (AND logico) (espressione SSIS) | Microsoft Docs'
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
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9f6cdb28a48a69ee1702b19918b9326ac861eb29
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062654"
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (AND logico) (espressione SSIS)
  Viene eseguita un'operazione con AND logico. Viene restituito TRUE dall'espressione se tutte le condizioni sono TRUE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean _expression1, boolean_expression2*  
 Qualsiasi espressione valida che restituisce TRUE, FALSE o NULL.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 Il risultato dell'operatore && è illustrato nella tabella seguente.  
  
|Risultato|Espressione|Espressione|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono usate le colonne **StandardCost** e **ListPrice** . Viene restituito TRUE se il valore della colonna **StandardCost** è minore di 300 e quello della colonna **ListPrice** è maggiore di 500.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 In questo esempio vengono usate le variabili **SPrice** e **LPrice** anziché valori letterali.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Vedere anche  
 [& &#40;AND bit per bit&#41; &#40;espressione SSIS&#41;](bitwise-and-ssis-expression.md)   
 [Associatività e precedenza operatori](operator-precedence-and-associativity.md)   
 [Gli operatori &#40;espressione SSIS&#41;](operators-ssis-expression.md)  
  
  