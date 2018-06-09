---
title: Distribuzioni (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e4ffd21a2b507e03af6534296715528d83aac0f6
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841244"
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
  
 Per ulteriori informazioni [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmi di data mining, vedere [algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). I provider di algoritmi di terze parti possono supportare ulteriori tipi di distribuzioni. Per determinare i tipi un algoritmo, utilizzare il **SUPPORTED_DISTRIBUTION_FLAGS** set di righe dello schema.  
  
 Per ulteriori informazioni sui tipi di distribuzione, vedere [distribuzioni delle colonne &#40;Data Mining&#41;](../analysis-services/data-mining/column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [I tipi di contenuto &#40;Data Mining&#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
