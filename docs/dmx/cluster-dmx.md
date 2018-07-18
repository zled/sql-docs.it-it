---
title: Cluster (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41f835a93e5976945281b6b04258c516b0322236
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841304"
---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il cluster che con maggiore probabilità contiene il case di input.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Si applica a  
 È possibile utilizzare questa funzione solo se il modello di data mining sottostante supporta il clustering.  
  
## <a name="return-type"></a>Tipo restituito  
 Il **Cluster** funzione non richiede parametri.  
  
 Il **Cluster** funzione restituisce un valore scalare di un nome di cluster. Tuttavia, se si utilizza questa funzione come argomento di un'altra funzione, è necessario considerare come un \<cluster riferimento di colonna >.  
  
## <a name="remarks"></a>Remarks  
 **Cluster** può essere utilizzato anche come un `<`riferimento a una colonna del cluster`>` per un **PredictHistogram** (funzione).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata una query singleton con il [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) e funzioni per restituire la distanza del singolo case da ogni cluster del modello di data mining TM Clustering del Cluster e il probabilità che il singolo case esista in ogni cluster.  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
