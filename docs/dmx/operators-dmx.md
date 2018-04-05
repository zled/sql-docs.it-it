---
title: Operatori (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- operators [DMX]
- DMX [Analysis Services], operators
- Data Mining Extensions [Analysis Services], operators
ms.assetid: e453e570-1ad1-4604-892f-6130308936ac
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8d6ae8c58b610ca5c709e85afaa033d99c8555af
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="operators-dmx"></a>Operatori (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare operatori di Data Mining Extensions (DMX) per eseguire operazioni aritmetiche, di confronto, concatenazione e operazioni logiche in una query in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizza gli operatori per eseguire le azioni seguenti:  
  
-   Ricercare oggetti o valori che soddisfano una specifica condizione.  
  
-   Effettuare una scelta tra due valori o espressioni.  
  
 In DMX sono disponibili diverse categorie di operatori, descritti nelle sezioni seguenti. Per ulteriori informazioni sui singoli operatori, vedere [DMX Data Mining Extensions &#40; &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
|Categoria di operatori|Tipo di operazione|  
|-----------------------|-----------------------|  
|[Aritmetici operatori &#40; DMX &#41;](../dmx/operators-arithmetic.md)|Esecuzione di addizioni, sottrazioni, moltiplicazioni e divisioni.|  
|[Gli operatori di confronto &#40; DMX &#41;](../dmx/operators-comparison.md)|Confronto di un valore con un altro valore o un'espressione.|  
|[Logica operatori &#40; DMX &#41;](../dmx/operators-logical.md)|Stabilire se una condizione è vera, ad esempio AND, OR e NOT.|  
|[Operatori unari &#40; DMX &#41;](../dmx/operators-unary.md)|Esecuzione di un'operazione su un singolo operando.|  
  
 In DMX è possibile utilizzare gli operatori per combinare semplici espressioni in modo da ottenere espressioni più complesse. Nelle espressioni complesse gli operatori vengono valutati nell'ordine definito dalle regole di precedenza degli operatori di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Gli operatori con precedenza superiore vengono eseguiti prima di quelli con precedenza inferiore. Per ulteriori informazioni sulle espressioni, vedere [DMX espressioni &#40; &#41;](../dmx/expressions-dmx.md).  
  
 Quando si combinano espressioni semplici per ottenere un'espressione complessa, il tipo di dati dell'espressione risultante viene determinato combinando le regole degli operatori con le regole sulla precedenza dei tipi di dati. Se il risultato è un carattere o un valore Unicode, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne determina le regole di confronto combinando le regole degli operatori con le regole sulla precedenza delle regole di confronto. Sono previste inoltre regole per determinare precisione, scala e lunghezza del risultato in base alla precisione, alla scala e alla lunghezza delle varie espressioni semplici.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
