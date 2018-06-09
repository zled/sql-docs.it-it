---
title: ClusterDistance (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2d8eb879d23a344e5de6bad3c9fb6042fdadb3e7
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841514"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Il **ClusterDistance** funzione restituisce la distanza del case di input dal cluster specificato, o se viene specificato alcun cluster, la distanza del case di input dal cluster più probabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>Si applica a  
 È possibile utilizzare questa funzione solo se il modello di data mining sottostante supporta il clustering. La funzione può essere utilizzata con qualsiasi tipo di modello di clustering (EM, K-medie, ecc.), ma i risultati variano in base all'algoritmo.  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare.  
  
## <a name="remarks"></a>Remarks  
 Il **ClusterDistance** funzione restituisce la distanza tra il case di input e il cluster con la probabilità più elevata per case di input.  
  
 Poiché con il clustering K-medie un case può appartenere solo a un cluster, la distanza del cluster è sempre 0 con un peso di appartenenza di 1.0. Tuttavia, in K-medie si presuppone che per ogni cluster sia presente un centro. È possibile ottenere il valore del centro esplorando o eseguendo una query sulla tabella nidificata NODE_DISTRIBUTION nel contenuto del modello di data mining. Per altre informazioni, vedere [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md).  
  
 Con il metodo di clustering predefinito EM tutti i punti nel cluster presentano la stessa probabilità; pertanto, per motivi strutturali non è previsto un centro per il cluster. Il valore di **ClusterDistance** tra un case specifico e un determinato cluster *N* viene calcolata come segue:  
  
 ClusterDistance(N) =1–(membershipWeight(N))  
  
 Oppure:  
  
 ClusterDistance(N) = 1 – ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>Funzioni di stima correlate  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sono disponibili le seguenti funzioni aggiuntive per l'esecuzione di query sui modelli di clustering:  
  
-   Usare la [Cluster &#40;DMX&#41; ](../dmx/cluster-dmx.md) funzione per restituire il cluster più probabile.  
  
-   Usare la [ClusterProbability &#40;DMX&#41; ](../dmx/clusterprobability-dmx.md) funzione per ottenere la probabilità che un case appartenga a un cluster specifico. Questo valore viene utilizzato come valore inverso della distanza del cluster.  
  
-   Usare la [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) funzione per restituire un istogramma della probabilità del case di input in ognuno dei cluster del modello.  
  
-   Usare la [PredictCaseLikelihood &#40;DMX&#41; ](../dmx/predictcaselikelihood-dmx.md) funzione per restituire una misura da 0 a 1 che indica la probabilità un case di input è presente prendendo in considerazione il modello appreso dall'algoritmo.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>Esempio 1: Acquisizione della distanza del cluster rispetto al cluster più probabile  
 Nell'esempio seguente viene restituita la distanza dal case specificato al cluster a cui appartiene il case più probabile.  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Risultati dell'esempio:  
  
|Espressione|  
|----------------|  
|0.0477390930705145|  
  
 Per individuare il tipo di cluster, è possibile utilizzare `Cluster` al posto di `ClusterDistance` nell'esempio precedente.  
  
 Risultati dell'esempio:  
  
|$CLUSTER|  
|--------------|  
|Cluster 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>Esempio 2: Acquisizione della distanza rispetto a un cluster specificato  
 La sintassi seguente utilizza il set di righe dello schema relativo al contenuto del modello di data mining per restituire l'elenco degli ID dei nodi e le didascalie dei nodi per i cluster del modello di data mining. È quindi possibile utilizzare la didascalia del nodo come argomento di identificatore di cluster nel **ClusterDistance** (funzione).  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 Risultati dell'esempio:  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|Cluster 1|  
|002|Cluster 2|  
  
 Nell'esempio di sintassi seguente viene restituita la distanza del case specificato dal cluster con etichetta Cluster 2.  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Risultati dell'esempio:  
  
|Cluster 2 Distance|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>Vedere anche  
 [Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Contenuto del modello di data mining per i modelli di Clustering &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
