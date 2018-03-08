---
title: PredictHistogram (DMX) | Documenti Microsoft
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
f1_keywords: PredictHistogram
dev_langs: DMX
helpviewer_keywords: PredictHistogram function
ms.assetid: 85ffc542-96e7-4f58-aaa3-34d76befcedf
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b967498b2ea2cf742eca67c8557230ed80c78055
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
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
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]algoritmi di data mining non supportano **$ProbabilityVariance**. Per gli algoritmi [!INCLUDE[msCoName](../includes/msconame-md.md)] questa colonna contiene sempre 0.  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]algoritmi di data mining non supportano **$ProbabilityStdev**. Per gli algoritmi [!INCLUDE[msCoName](../includes/msconame-md.md)] questa colonna contiene sempre 0.  
  
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
 [DMX cluster &#40; &#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40; DMX &#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40; DMX &#41;](../dmx/predictadjustedprobability-dmx.md)   
 [DMX PredictProbability &#40; &#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40; DMX &#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40; DMX &#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40; DMX &#41;](../dmx/predictvariance-dmx.md)   
 [Algoritmi di Data Mining &#40; Analysis Services - Data Mining &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
