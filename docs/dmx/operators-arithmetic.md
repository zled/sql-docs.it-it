---
title: Operatori aritmetici (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords: arithmetic operators
ms.assetid: befe4f0c-e5dd-4ae1-b88e-6ac7aab2181a
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c256882453ca3536a21babb2d87b774e9aab3d6d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="operators---arithmetic"></a>Operatori di aritmetica-
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare gli operatori aritmetici in DMX Data Mining Extensions () per eseguire calcoli aritmetici in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], inclusi l'addizione, sottrazione, moltiplicazione e divisione.  
  
 Gli operatori aritmetici supportati da DMX sono indicati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[+ &#40; Aggiungi &#41; &#40; DMX &#41;](../dmx/add-dmx.md)|Somma due numeri.|  
|[-&#40; Sottrarre &#41; &#40; DMX &#41;](../dmx/subtract-dmx.md)|Sottrae un numero da un altro.|  
|[&#42; &#40; Moltiplicare &#41; &#40; DMX &#41;](../dmx/multiply-dmx.md)|Esegue una moltiplicazione tra due numeri.|  
|[&#40; divisione &#41; &#40; DMX &#41;](../dmx/divide-dmx.md)|Esegue una divisione di un numero per un altro.|  
  
 L'ordine di precedenza per gli operatori aritmetici in un'espressione DMX è determinato dalle regole seguenti:  
  
-   Se un'espressione include più operatori aritmetici, verranno eseguite per prime le operazioni di moltiplicazione e divisione, seguite da sottrazione e addizione.  
  
-   Se tutti gli operatori aritmetici di un'espressione hanno la stessa precedenza, le operazioni verranno eseguite da sinistra a destra.  
  
-   Le espressioni tra parentesi hanno la precedenza su tutte le altre operazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Espressioni &#40; DMX &#41;](../dmx/expressions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
