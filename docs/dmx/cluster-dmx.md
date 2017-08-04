---
title: Cluster (DMX) | Documenti Microsoft
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
f1_keywords:
- Cluster
dev_langs:
- DMX
helpviewer_keywords:
- Cluster function
ms.assetid: 14b2942a-6dec-4dfa-98a6-697a3c89036a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 65e0d6942d48657f99d5cff3365a80d4853c66d4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Osservazioni  
 **Cluster** può anche essere utilizzato come un `<`riferimento a colonna cluster`>` per un **PredictHistogram** (funzione).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata una query singleton con il [PredictHistogram &#40; DMX &#41;](../dmx/predicthistogram-dmx.md) e funzioni per restituire la distanza del singolo case da ogni cluster del modello di data mining TM Clustering e la probabilità che il singolo case esista in ogni cluster del Cluster.  
  
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
 [ClusterProbability &#40; DMX &#41;](../dmx/clusterprobability-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

