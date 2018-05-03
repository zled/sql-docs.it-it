---
title: Riferimento alla funzione di Data Mining Extensions (DMX) | Documenti Microsoft
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
- DMX [Analysis Services], functions
- functions [DMX]
- Data Mining Extensions [Analysis Services], functions
ms.assetid: fadd105b-9c8e-4118-a1f7-c0518b9ad970
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 025e7cbb2ef6e462da75c2fe9d07f7c7dd8300ff
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-mining-extensions-dmx-function-reference"></a>Guida di riferimento alle funzioni DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta molte funzioni del linguaggio DMX (Data Mining Extensions). Le funzioni consentono di espandere i risultati di una query di stima in modo da includere informazioni che descrivono ulteriormente la stima. Tramite le funzioni è inoltre possibile ottenere un maggiore controllo sulla modalità con cui vengono restituiti i risultati della stima. Nella tabella seguente vengono forniti i collegamenti alle risorse che illustrano come utilizzare le funzioni in DMX.  
  
|Funzione|Description|  
|--------------|-----------------|  
|[Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)|Vengono elencate le funzioni che è possibile utilizzare con tutti i tipi di modelli e vengono forniti i collegamenti a ulteriori informazioni sull'esecuzione di query su tipi specifici di modelli di data mining.|  
|[Struttura e uso di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)|Viene fornita una panoramica della costruzione di una query di stima mediante DMX.|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|Restituisce una tabella che contiene un numero specificato di righe a partire dall'ultima, in ordine di rango crescente in base a un'espressione di rango.|  
  
 Nella tabella seguente vengono elencate le funzioni supportate da DMX.  
  
|Funzione|Description|  
|--------------|-----------------|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|Restituisce una tabella che contiene le ultime righe di n elementi dell'espressione di tabella in ordine crescente in base all'espressione di rango.|  
|[BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)|Restituisce una tabella che contiene il più piccolo numero di righe, a partire dall'ultima, che consente di ottenere la percentuale restituita da un'espressione specificata, in ordine di rango crescente in base a un'espressione di rango.|  
|[BottomSum &#40;DMX&#41;](../dmx/bottomsum-dmx.md)|Restituisce una tabella che contiene il più piccolo numero di righe, a partire dall'ultima, che consente di ottenere la somma restituita da un'espressione specificata, in ordine di rango crescente in base a un'espressione di rango.|  
|[Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)|Restituisce il cluster che con maggiore probabilità contiene il case di input.|  
|[ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)|Restituisce la probabilità che il case di input appartenga al cluster.|  
|[È presente &#40;DMX&#41;](../dmx/exists-dmx.md)|Restituisce true se il set di risultati restituito dall'istruzione SELECT specificata contiene almeno una riga.|  
|[DMX IsDescendant & #40; & #41;](../dmx/isdescendant-dmx.md)|Indica se il nodo corrente discende dal nodo specificato.|  
|[DMX IsInNode & #40; & #41;](../dmx/isinnode-dmx.md)|Indica se il nodo specificato contiene o meno il case specificato.|  
|[IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)|Indica se un case appartiene al set di test case.|  
|[IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)|Indica se un case appartiene al set di case di training.|  
|[DMX Lag & #40; & #41;](../dmx/lag-dmx.md)|Restituisce l'intervallo di tempo tra la data del case corrente e l'ultima data presente nei dati.|  
|[Stimare & #40; DMX & #41;](../dmx/predict-dmx.md)|Esegue una stima su una colonna specificata.|  
|[PredictAdjustedProbability & #40; DMX & #41;](../dmx/predictadjustedprobability-dmx.md)|Restituisce la probabilità adattata della colonna stimabile specificata.|  
|[DMX PredictAssociation & #40; & #41;](../dmx/predictassociation-dmx.md)|Consente di stimare l'appartenenza associativa in una colonna.|  
|[PredictCaseLikelihood &#40;DMX&#41;](../dmx/predictcaselikelihood-dmx.md)|Restituisce la probabilità che un case di input risulti adatto al modello esistente. Questa funzione può essere utilizzata solo con i modelli di clustering.|  
|[DMX PredictHistogram & #40; & #41;](../dmx/predicthistogram-dmx.md)|Restituisce una tabella che rappresenta l'istogramma per una colonna specificata.|  
|[DMX PredictNodeId & #40; & #41;](../dmx/predictnodeid-dmx.md)|Restituisce il NodeID del case selezionato.|  
|[DMX PredictProbability & #40; & #41;](../dmx/predictprobability-dmx.md)|Restituisce la probabilità della colonna specificata.|  
|[PredictSequence &#40;DMX&#41;](../dmx/predictsequence-dmx.md)|Stima i valori successivi in una sequenza.|  
|[PredictStdev & #40; DMX & #41;](../dmx/predictstdev-dmx.md)|Recupera il valore della deviazione standard per una colonna specificata.|  
|[PredictSupport & #40; DMX & #41;](../dmx/predictsupport-dmx.md)|Restituisce il valore di supporto della colonna.|  
|[DMX PredictTimeSeries & #40; & #41;](../dmx/predicttimeseries-dmx.md)|Stima i valori futuri di una serie temporale.|  
|[PredictVariance & #40; DMX & #41;](../dmx/predictvariance-dmx.md)|Restituisce il valore della varianza della colonna specificata.|  
|[RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|Restituisce il limite superiore del bucket stimato individuato per una colonna discretizzata specificata.|  
|[RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)|Restituisce il punto medio del bucket stimato individuato per una colonna discretizzata specificata.|  
|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)|Restituisce il limite inferiore del bucket stimato individuato per una colonna discretizzata specificata.|  
|[StructureColumn &#40;DMX&#41;](../dmx/structurecolumn-dmx.md)|Restituisce il valore della colonna della struttura di data mining della tabella specificata.|  
|[TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)|Restituisce una tabella che contiene un numero specificato di righe a partire dalla prima, in ordine di rango decrescente in base a un'espressione di rango.|  
|[TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)|Restituisce una tabella che contiene il più piccolo numero di righe, a partire dalla prima, che consente di ottenere la percentuale restituita da un'espressione specificata, in ordine di rango decrescente in base a un'espressione di rango.|  
|[TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)|Restituisce una tabella che contiene il più piccolo numero di righe, a partire dalla prima, che consente di ottenere la somma restituita da un'espressione specificata, in ordine di rango decrescente in base a un'espressione di rango.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
