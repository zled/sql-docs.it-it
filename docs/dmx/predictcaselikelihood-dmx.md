---
title: PredictCaseLikelihood (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d8159af8ac4b3c9bf21dcdc68a0cfb30c46e33e5
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841779"
---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Questa funzione restituisce la probabilità che un case di input risulti adatto al modello esistente. Utilizzata solo con i modelli di tipo clustering.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictCaseLikelihood([NORMALIZED|NONNORMALIZED])  
```  
  
## <a name="arguments"></a>Argomenti  
 NORMALIZED  
 Il valore restituito contiene la probabilità del case nel modello diviso per la probabilità del case senza il modello.  
  
 NONNORMALIZED  
 Il valore restituito contiene la probabilità non elaborata del case, che rappresenta il prodotto delle probabilità degli attributi del case.  
  
## <a name="applies-to"></a>Si applica a  
 I modelli compilati utilizzando il [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering e [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmi Sequence Clustering.  
  
## <a name="return-type"></a>Tipo restituito  
 Numero a virgola mobile a precisione doppia compreso tra 0 e 1. Un numero più vicino a 1 indica che il case ha una maggiore probabilità di essere presente nel modello. Un numero più vicino a 0 indica che il case ha una minore probabilità di essere presente nel modello.  
  
## <a name="remarks"></a>Remarks  
 Per impostazione predefinita, il risultato di **PredictCaseLikelihood** (funzione) è normalizzata. I valori normalizzati sono in genere più utili come numero di attributi in un aumento del case e le differenze tra le probabilità non elaborate di uno dei due case si riducono notevolmente.  
  
 L'equazione seguente viene utilizzata per calcolare i valori normalizzati, dati x e y:  
  
-   x = probabilità del case in base al modello di clustering  
  
-   y = probabilità marginale del case, calcolata come la probabilità in forma logaritmica del case in base al conteggio dei case di training  
  
-   Z = Exp( log(x) – Log(Y))  
  
 Normalizzato = (z / (1 + z))  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la probabilità che il case specificato si presenti nel modello di clustering, basato sul database [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW.  
  
```  
SELECT  
  PredictCaseLikelihood() AS Default_Likelihood,  
  PredictCaseLikelihood(NORMALIZED) AS Normalized_Likelihood,  
  PredictCaseLikelihood(NONNORMALIZED) AS Raw_Likelihood,  
FROM  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Risultati previsti:  
  
|Default_Likelihood|Normalized_Likelihood|Raw_Likelihood|  
|-------------------------|----------------------------|---------------------|  
|6.30672792729321E-08|6.30672792729321E-08|9.5824454056846E-48|  
  
 La differenza tra questi risultati dimostra l'effetto della normalizzazione. Il valore non elaborato per **CaseLikelihood** suggerisce che la probabilità del case è di circa il 20%, tuttavia, quando si normalizzano i risultati, risulta più evidente che la probabilità del case è molto bassa.  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
