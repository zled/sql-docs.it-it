---
title: Contenuto di tipi (DMX) | Documenti Microsoft
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
- Data Mining Extensions [Analysis Services], content types
- content types [DMX]
- DMX [Analysis Services], content types
ms.assetid: ab9dd887-df8d-4878-96b0-635881892573
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8e11c1d602743cd65c436ae7e6e47c14be4bb0a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="content-types-dmx"></a>Tipi di contenuto (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Per funzionare correttamente, oltre al tipo di dati gli algoritmi di data mining richiedono anche altre informazioni, ad esempio il tipo di contenuto. Il tipo di contenuto consente all'algoritmo di determinare come utilizzare i dati nella colonna.  
  
 Ogni algoritmo supporta tipi di contenuto specifici. L'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, ad esempio, non può utilizzare colonne continue. Per utilizzare colonne continue in un modello [!INCLUDE[msCoName](../includes/msconame-md.md)], è necessario discretizzarne i dati. Per funzionare correttamente alcuni algoritmi richiedono tipi di contenuto specifici. L'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series, ad esempio, richiede una colonna chiave temporale per identificare il periodo di tempo in cui sono stati raccolti i dati.  
  
 Per tipi di una descrizione completa del contenuto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supportati, vedere [tipi di contenuto &#40;Data Mining&#41;](../analysis-services/data-mining/content-types-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining & #40; Analysis Services - Data Mining & #41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
