---
title: Utilizzo (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2acfde9b8d7c9d13fc626b006116e9b3760fd432
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="usage-dmx"></a>Utilizzo (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quando si utilizzano estensioni DMX (Data Mining) per definire un nuovo modello di data mining in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], è necessario specificare come algoritmo di data mining che compila il modello di utilizzo di ciascuna colonna. Le colonne possono essere dei tipi seguenti:  
  
-   **Key**  
  
-   **Sequenza di tasti**  
  
-   **Chiave temporale**  
  
-   **Stimare**  
  
-   **PredictOnly**  
  
 In DMX le colonne non specificate vengono gestite come colonne di input.  
  
 Per elaborare correttamente un modello, è necessario indicare all'algoritmo la colonna chiave che identifica univocamente ogni riga, la colonna di destinazione per la creazione delle stime, se si sta creando un modello stimabile e le colonne da utilizzare come colonne di input per creare le relazioni che consentono di stimare la colonna di destinazione.  
  
 Le colonne specificate come il **Predict** tipo vengono utilizzate come colonne di input e di output. Le colonne specificate come **PredictOnly** vengono utilizzati solo come colonne di output. Determinati algoritmi possono gestire le colonne Predict in modo diverso.  
  
 Per ulteriori informazioni sulla colonna dei tipi di utilizzo che [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supportati, vedere [colonne del modello di Data Mining](../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40; Analysis Services - Data Mining &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione Select di DMX](../dmx/understanding-the-dmx-select-statement.md)  
  
  

