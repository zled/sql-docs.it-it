---
title: Distribuzioni (DMX) | Documenti Microsoft
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
helpviewer_keywords:
- column distributions [DMX]
- distributions [DMX]
- DMX [Analysis Services], distributions
- Data Mining Extensions [Analysis Services], distributions
ms.assetid: cfbb9f38-ae71-401e-867f-15c6a2b6fb97
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4bc79c9a1c641f625a6a0dae11c17aba4188b5e8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="distributions-dmx"></a>Distribuzioni (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  In [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], è possibile definire il contenuto delle colonne in una struttura di data mining per determinare come gli algoritmi elaborano i dati in tali colonne quando si creano modelli di data mining. Per alcuni algoritmi è utile definire la distribuzione dei dati nelle colonne continue prima di elaborare il modello, se è noto che tali colonne contengono valori con distribuzioni comuni. Se non si definiscono le distribuzioni, i modelli di data mining risultanti possono produrre stime meno accurate, perché gli algoritmi dispongono di meno informazioni per l'interpretazione dei dati.  
  
 Gli algoritmi di data mining [!INCLUDE[msCoName](../includes/msconame-md.md)] supportano i tipi di distribuzioni seguenti:  
  
 **NORMALE**  
 I valori della colonna continua formano un istogramma con una distribuzione di Gauss normale.  
  
 **Logaritmica normale**  
 I valori della colonna continua formano un istogramma in cui i logaritmi dei valori seguono una distribuzione normale.  
  
 **UNIFORM**  
 I valori della colonna continua formano una curva uniforme, in cui tutti i valori hanno la stessa probabilità.  
  
 Per ulteriori informazioni su [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmi di data mining, vedere [algoritmi di Data Mining &#40; Analysis Services - Data Mining &#41; ](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). I provider di algoritmi di terze parti possono supportare ulteriori tipi di distribuzioni. Per determinare i tipi un algoritmo, utilizzare il **SUPPORTED_DISTRIBUTION_FLAGS** set di righe dello schema.  
  
 Per ulteriori informazioni sui tipi di distribuzione, vedere [distribuzioni delle colonne &#40; Data Mining &#41;](../analysis-services/data-mining/column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Contenuto di Data Mining tipi &#40; &#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
