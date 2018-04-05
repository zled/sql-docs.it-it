---
title: (DMX) di flag di modellazione | Documenti Microsoft
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
- REGRESSOR flag
- DMX [Analysis Services], modeling flags
- MODEL_EXISTENCE_ONLY flag
- modeling flags [DMX]
- Data Mining Extensions [Analysis Services], modeling flags
- flags [DMX]
- NOT NULL flag
ms.assetid: 498d25f7-9597-47ae-8717-61ddd1d2fd15
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d7d762425310722d53de8c8bd7e92f497a334c78
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="modeling-flags-dmx"></a>Flag di modellazione (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] è possibile utilizzare flag di modellazione per fornire a un algoritmo di data mining informazioni aggiuntive sui dati definiti in una tabella del case. L'algoritmo può utilizzare tali informazioni per compilare un modello di data mining più accurato. I flag di modellazione possono essere definiti sia sulle colonne della struttura di data mining che su quelle del modello di data mining.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta i flag di modellazione seguenti:  
  
 **NOT NULL**  
 I valori per la colonna attributo non devono mai contenere valori Null. Se durante il processo di training del modello [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] rileva un valore null per la colonna attributo, verrà generato un errore. Questo flag viene definito su una colonna di una struttura di data mining.  
  
 **REGRESSOR**  
 Indica che l'algoritmo può utilizzare la colonna specificata nella formula di regressione degli algoritmi di regressione. Questo flag è supportato dagli algoritmi [!INCLUDE[msCoName](../includes/msconame-md.md)] Linear Regression e [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees ed è definito su una colonna di un modello di data mining.  
  
 **MODEL_EXISTENCE_ONLY**  
 I valori della colonna attributo sono meno importanti rispetto alla presenza dell'attributo. Questo flag viene definito su una colonna di un modello di data mining.  
  
 Gli algoritmi di terze parti possono supportare ulteriori flag di modellazione. Per determinare i flag di modellazione un algoritmo, utilizzare il **SUPPORTED_MODELING_FLAGS** set di righe dello schema. È inoltre possibile eseguire una query sui servizi di data mining nel server per determinare i flag di modellazione supportati per un algoritmo specifico. Ad esempio, la query seguente restituisce i flag di modellazione supportati per l'algoritmo Microsoft Linear Regression nel server corrente:  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 Risultati previsti:  
  
 NOT NULL,REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>Specifica dei flag di modellazione in un modello di data mining  
 Per esempi di sintassi che [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supportati per la specifica di un contrassegno in una colonna della struttura di data mining, vedere [DMX CREATE MINING STRUCTURE &#40; &#41;](../dmx/create-mining-structure-dmx.md).  
  
 Per un esempio della sintassi per la specifica di un flag di modellazione in una colonna del modello di data mining, vedere [DMX ALTER MINING STRUCTURE &#40; &#41;](../dmx/alter-mining-structure-dmx.md).  
  
 Per ulteriori informazioni sull'utilizzo di colonne del modello di data mining, vedere [colonne del modello di Data Mining](../analysis-services/data-mining/mining-model-columns.md).  
  
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
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
