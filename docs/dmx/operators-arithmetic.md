---
title: Operatori aritmetici (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: edbe8a3404217f330b5b62a9d433c7d560b28656
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842224"
---
# <a name="operators---arithmetic"></a>Operatori di aritmetica-
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare gli operatori aritmetici in DMX Data Mining Extensions () per eseguire calcoli aritmetici in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], inclusi l'addizione, sottrazione, moltiplicazione e divisione.  
  
 Gli operatori aritmetici supportati da DMX sono indicati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[+ &#40;Aggiungi&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Somma due numeri.|  
|[- &#40;Sottrarre&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Sottrae un numero da un altro.|  
|[&#42;&#40;Moltiplica&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Esegue una moltiplicazione tra due numeri.|  
|[&#40;Dividere&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|Esegue una divisione di un numero per un altro.|  
  
 L'ordine di precedenza per gli operatori aritmetici in un'espressione DMX è determinato dalle regole seguenti:  
  
-   Se un'espressione include più operatori aritmetici, verranno eseguite per prime le operazioni di moltiplicazione e divisione, seguite da sottrazione e addizione.  
  
-   Se tutti gli operatori aritmetici di un'espressione hanno la stessa precedenza, le operazioni verranno eseguite da sinistra a destra.  
  
-   Le espressioni tra parentesi hanno la precedenza su tutte le altre operazioni.  
  
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
  
  
