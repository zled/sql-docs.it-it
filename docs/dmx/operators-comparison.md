---
title: Operatori di confronto (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8049f2bad6e78ff301b460b1375a0a73807ccd8d
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842464"
---
# <a name="operators---comparison"></a>Operatori di confronto-
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare gli operatori di confronto con dati scalari in qualsiasi espressione di Data Mining Extensions (DMX) [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Questi operatori restituiscono un tipo di dati Boolean, ovvero TRUE o FALSE a seconda che venga soddisfatta o meno la condizione specificata.  
  
 Gli operatori di confronto supportati da DMX sono indicati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[&#60;&#40;Minore di&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è minore di quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#62;&#40;Maggiore di&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è maggiore di quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[= &#40;Uguale a&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#60;&#62;&#40;Non è uguale a&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è diverso da quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#60;= &#40;Minore o uguale a&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è minore o uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#62;= &#40;Maggiore o uguale a&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è maggiore o uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
  
 Nelle istruzioni e nelle funzioni DMX è possibile utilizzare gli operatori di confronto anche per stabilire se una condizione è verificata o meno.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Le espressioni &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Gli operatori &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
