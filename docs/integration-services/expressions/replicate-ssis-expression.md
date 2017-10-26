---
title: REPLICATE (espressione SSIS) | Documenti Microsoft
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
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c94e5f4221251b3b931ebabc5076620ba6ab0e7e
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="replicate-ssis-expression"></a>REPLICATE (espressione SSIS)
  Viene restituita un'espressione di caratteri ripetuta per il numero di volte specificato. L'argomento *numero di volte* deve restituire un Integer.  
  
> [!NOTE]  
>  La funzione REPLICATE utilizza spesso stringhe lunghe e pertanto è più facile che un'espressione superi il limite di 4000 caratteri di lunghezza. Se il risultato della valutazione di un'espressione ha il tipo di dati Integration Services DT_WSTR o DT_STR, l'espressione verrà troncata a 4000 caratteri. Se il tipo di risultato di una sottoespressione è DT_STR o DT_WSTR, probabilmente la sottoespressione verrà troncata a 4000 caratteri, indipendentemente dal tipo di risultato dell'espressione globale. Le conseguenze del troncamento possono essere gestite normalmente oppure generare un avviso o un errore. Per altre informazioni, vedere [Sintassi &#40;SSIS&#41;](../../integration-services/expressions/syntax-ssis.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da replicare.  
  
 *numero di volte*  
 Espressione Integer che specifica il numero di volte in cui *character_expression* viene replicata.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Osservazioni  
 Se il *numero di volte* ha valore zero, la funzione restituirà una stringa di lunghezza zero.  
  
 Se il *numero di volte* è un numero negativo, la funzione restituirà un errore.  
  
 L'argomento *numero di volte* può usare anche variabili e colonne.  
  
 È possibile utilizzare REPLICATE solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da REPLICATE verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, REPLICATE restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio un valore letterale stringa viene replicato tre volte. Il risultato restituito è "Mountain BikeMountain BikeMountain Bike".  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 In questo esempio i valori nella colonna **Nome** vengono replicati per il numero di volte indicato dal valore della variabile **Numero di volte** . Se **Numero di volte** ha valore 3 e **Nome** contiene Touring Front Wheel, il risultato restituito sarà Touring Front WheelTouring Front WheelTouring Front Wheel.  
  
```  
REPLICATE(Name, @Times)  
```  
  
 In questo esempio i valori nella variabile **Nome** vengono replicati per il numero di volte indicato dal valore nella colonna **Numero di volte** . La variabile**Nome** ha un tipo di dati diverso da Integer e l'espressione include un cast esplicito a un tipo di dati Integer. Se **Nome** contiene il testo Helmet e **Numero di volte** ha valore 2, il risultato restituito sarà "HelmetHelmet".  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

