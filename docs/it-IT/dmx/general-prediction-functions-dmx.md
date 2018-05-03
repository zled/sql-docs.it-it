---
title: Funzioni di stima (DMX) | Documenti Microsoft
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
- mapping functions to query types [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- SELECT statement [DMX]
- Data Mining Extensions [Analysis Services], functions
- Data Mining Extensions [Analysis Services], prediction queries
ms.assetid: e128159a-0458-43c9-bfe9-129cb6cfbe1c
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: fcfebc92ade967c1598ccc5f3fff11622b93dbf6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="general-prediction-functions-dmx"></a>Funzioni di stima correlate (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare il **selezionare** istruzione in estensioni DMX (Data Mining) per creare diversi tipi di query. Una query può essere utilizzata per restituire informazioni sul modello di data mining stesso, per eseguire nuove stime o per modificare il modello eseguendone il training con i nuovi dati. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] offre un'ampia gamma di funzioni specializzate che consentono di controllare il tipo di informazioni restituite in una query. Aggiungendo queste funzioni a una query DMX, è possibile recuperare statistiche o colonne di dati aggiuntive. Tuttavia, ogni tipo di query e ogni tipo di modello supportano solo determinate funzioni.  
  
## <a name="common-functions"></a>Funzioni comuni  
 È possibile utilizzare le funzioni per estendere i risultati restituiti da un modello di data mining. È possibile utilizzare le seguenti funzioni per qualsiasi **selezionare** istruzione che restituisce un'espressione di tabella:  
  
|||  
|-|-|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)|  
|[BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)|[TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)|  
|[Stimare & #40; DMX & #41;](../dmx/predict-dmx.md)|[TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)|  
|[RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|[TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)|  
|[RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)||  
  
 Inoltre, le funzioni seguenti sono supportate per quasi tutti i tipi di modello:  
  
-   [È presente &#40;DMX&#41;](../dmx/exists-dmx.md)  
  
-   [DMX IsDescendant & #40; & #41;](../dmx/isdescendant-dmx.md)  
  
-   [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)  
  
-   [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)  
  
-   [Stimare & #40; DMX & #41;](../dmx/predict-dmx.md)  
  
-   [RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)  
  
-   [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)  
  
-   [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
-   [StructureColumn &#40;DMX&#41;](../dmx/structurecolumn-dmx.md)  
  
 I singoli algoritmi possono supportare funzioni aggiuntive. Per un elenco delle funzioni supportate da ogni tipo di modello, vedere [query di Data Mining](../analysis-services/data-mining/data-mining-queries.md).  
  
## <a name="functions-specific-to-select-syntax"></a>Funzioni specifiche per la sintassi SELECT  
 Nella tabella seguente sono elencate le funzioni che è possibile utilizzare per ogni tipo di **selezionare** istruzione.  
  
 Per informazioni generali sulla funzioni in DMX, vedere [DMX &#40;DMX&#41; di riferimento alle funzioni](../dmx/data-mining-extensions-dmx-function-reference.md).  
  
|Tipo di query|Funzioni supportate|Osservazioni|  
|----------------|-------------------------|-------------|  
|[SELECT DISTINCT FROM \<modello >](../dmx/select-distinct-from-model-dmx.md)|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)<br /><br /> [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)<br /><br /> [RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|Queste funzioni possono essere utilizzate per fornire valori massimi, valori minimi e medie per qualsiasi colonna che contenga un tipo di dati numerico, indipendentemente dal fatto che sia continua o sia stata discretizzata.|  
|[SELECT FROM \<modello >. CONTENUTO](../dmx/select-from-model-content-dmx.md)<br /><br /> o<br /><br /> [SELECT FROM \<modello >. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)|[DMX IsDescendant & #40; & #41;](../dmx/isdescendant-dmx.md)|Questa funzione recupera i nodi figlio per il nodo specificato nel modello e può essere utilizzata, ad esempio, per scorrere i nodi nel contenuto del modello di data mining. La disposizione dei nodi nel contenuto del modello di data mining dipende dal tipo di modello. Per informazioni sulla struttura per ogni tipo di modello di data mining, vedere [contenuto del modello di Data Mining &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).<br /><br /> Se il contenuto del modello di data mining è stato salvato come dimensione, è anche possibile utilizzare altre funzioni MDX (Multidimensional Expression) disponibili per l'esecuzione di query su una gerarchia di attributo.|  
|[SELECT FROM \<modello >. CASI](../dmx/select-from-model-cases-dmx.md)|[DMX IsInNode & #40; & #41;](../dmx/isinnode-dmx.md)<br /><br /> [Classe ClientSettingsGeneralFlag](../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md)<br /><br /> [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)<br /><br /> [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)|La funzione Lag è supportata solo per i modelli time series.<br /><br /> La funzione IsTestCase è supportata nei modelli basati su una struttura che è stata creata utilizzando l'opzione di controllo, per creare un set di dati di testing. Se il modello non è basato su una struttura con un set di test di controllo, tutti i case vengono considerati case di training.|  
|[SELECT FROM \<modello >. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)|[DMX IsInNode & #40; & #41;](../dmx/isinnode-dmx.md)|In questo contesto, la funzione IsInNode restituisce un caso appartenente a un set di esempio idealizzati.|  
|SELECT FROM \<modello >. PMML|Non applicabile. Utilizzare la funzione XML.|Le rappresentazioni PMML sono supportate solo per i tipi di modello seguenti:<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering|  
|[SELECT FROM \<modello > PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)|Funzioni di stima specifiche dell'algoritmo utilizzato per compilare il modello.|Per un elenco di funzioni di stima per ogni tipo di modello, vedere [query di Data Mining](../analysis-services/data-mining/data-mining-queries.md).|  
|[SELECT FROM \<modello >](../dmx/select-from-model-dmx.md)|Funzioni di stima specifiche dell'algoritmo utilizzato per compilare il modello.|Per un elenco di funzioni di stima per ogni tipo di modello, vedere [query di Data Mining](../analysis-services/data-mining/data-mining-queries.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions & #40; DMX & #41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
