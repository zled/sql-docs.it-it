---
title: ClusterProbability (DMX) | Documenti Microsoft
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
- ClusterProbability
dev_langs:
- DMX
helpviewer_keywords:
- ClusterProbability function
ms.assetid: a6447b3c-94ce-4122-a3eb-6f3827598d8f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b7f68000caa8fd90dd2a2396ff17f0fd701b96d2
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce la probabilità che il case di input appartenga al cluster specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>Si applica a  
 È possibile utilizzare questa funzione solo se il modello di data mining sottostante supporta il clustering.  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 La sintassi seguente utilizza il set di righe dello schema relativo al contenuto del modello di data mining per restituire le didascalie dei nodi esistenti nel modello di data mining.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Per ulteriori informazioni sull'utilizzo di questa sintassi, vedere [modello SELECT FROM &#60; &#62;. DMX contenuto &#40; &#41; ](../dmx/select-from-model-content-dmx.md). Per ulteriori informazioni sul set di righe dello schema del contenuto del modello data mining, vedere [set di righe DMSCHEMA_MINING_MODEL_CONTENT](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md).  
  
 Se un \<didascalia del nodo > non è specificato, la funzione restituisce la probabilità che i case di input appartengano al cluster più probabile. Utilizzare il **Cluster** funzione per restituire il cluster più probabile.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la probabilità che il case specificato esista nel cluster con etichetta Cluster 2.  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DMX cluster &#40; &#41;](../dmx/cluster-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

