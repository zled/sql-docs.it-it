---
title: PredictHistogram (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e7129985eac09d741ea9d00c551a9507ee92c9
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842144"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce una tabella che rappresenta un istogramma per la stima di una colonna specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>Si applica a  
 Riferimento a colonna scalare o riferimento a colonna cluster. Può essere utilizzata con tutti i tipi di algoritmi, a eccezione di [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules.  
  
## <a name="return-type"></a>Tipo restituito  
 Tabella.  
  
## <a name="remarks"></a>Remarks  
 Un istogramma genera colonne di statistiche. La struttura della colonna dell'istogramma restituito dipende dal tipo di riferimento di colonna che viene utilizzato con il **PredictHistogram** (funzione).  
  
## <a name="scalar-columns"></a>Colonne scalari  
 Per un \<riferimento alla colonna scalare >, l'istogramma che il **PredictHistogram** funzione restituisce costituito dalle colonne seguenti:  
  
-   Valore stimato.  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmi di data mining non supportano **$ProbabilityVariance**. Per gli algoritmi [!INCLUDE[msCoName](../includes/msconame-md.md)] questa colonna contiene sempre 0.  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmi di data mining non supportano **$ProbabilityStdev**. Per gli algoritmi [!INCLUDE[msCoName](../includes/msconame-md.md)] questa colonna contiene sempre 0.  
  
-   **$AdjustedProbability**  
  
     Il **$AdjustedProbability** colonna è un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] estensione per il [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB per Data Mining specifica.  
  
## <a name="cluster-columns"></a>Colonne cluster  
 L'istogramma che il **PredictHistogram** funzione restituisce per un \<cluster riferimento di colonna > include le colonne seguenti:  
  
-   **$Cluster** (rappresenta il nome del cluster)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito lo stato stimato della colonna Bike Buyer in una query singleton. La query restituisce anche gli stati probabilmente prime due dell'attributo Bike Buyer, in base alla probabilità adattata ottenuta mediante il **PredictHistogram** (funzione).  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
