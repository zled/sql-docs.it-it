---
title: PredictCaseLikelihood (DMX) | Documenti Microsoft
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
- PredictCaseLikelihood
dev_langs:
- DMX
helpviewer_keywords:
- PredictCaseLikelihood function
ms.assetid: b00180e5-b2eb-49e2-891d-e39fb378f50a
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99a6d2927d0164f4c23dbb2c34d1d9ab6bab511f
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Osservazioni  
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
 [Algoritmi di Data Mining &#40; Analysis Services - Data Mining &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

