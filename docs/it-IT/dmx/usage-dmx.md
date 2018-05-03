---
title: Utilizzo (DMX) | Documenti Microsoft
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
- column usage [DMX]
- Data Mining Extensions [Analysis Services], column usage types
- DMX [Analysis Services], column usage types
ms.assetid: 6d7ae72a-f5b5-4744-a3a2-46ccd6432c1a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6087d52cc5e4932a1f21f305213cbfd08775d19f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="usage-dmx"></a>Utilizzo (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Quando si utilizzano estensioni DMX (Data Mining) per definire un nuovo modello di data mining in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], è necessario specificare come algoritmo di data mining che compila il modello di utilizzo di ciascuna colonna. Le colonne possono essere dei tipi seguenti:  
  
-   **Key**  
  
-   **Sequenza di tasti**  
  
-   **Chiave temporale**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 In DMX le colonne non specificate vengono gestite come colonne di input.  
  
 Per elaborare correttamente un modello, è necessario indicare all'algoritmo la colonna chiave che identifica univocamente ogni riga, la colonna di destinazione per la creazione delle stime, se si sta creando un modello stimabile e le colonne da utilizzare come colonne di input per creare le relazioni che consentono di stimare la colonna di destinazione.  
  
 Le colonne specificate come il **Predict** tipo vengono utilizzate come colonne di input e di output. Le colonne specificate come **PredictOnly** vengono utilizzati solo come colonne di output. Determinati algoritmi possono gestire le colonne Predict in modo diverso.  
  
 Per ulteriori informazioni sulla colonna dei tipi di utilizzo che [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supportati, vedere [colonne del modello di Data Mining](../analysis-services/data-mining/mining-model-columns.md).  
  
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
  
  
