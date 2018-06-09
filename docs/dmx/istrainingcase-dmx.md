---
title: IsTrainingCase (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 00344eeb38f3aae5cae7ac25c1b65b403cc85cb9
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842344"
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica se un case viene utilizzato come case di training per il modello o la struttura di data mining specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>Tipo di risultato  
 Restituisce **true** se il case è una parte del set di dati di training; in caso contrario **false**.  
  
## <a name="remarks"></a>Remarks  
 Se si utilizza la Creazione guidata modello di data mining per creare una struttura di data mining e il modello di data mining correlato, per impostazione predefinita il 30% dei case viene riservato per l'utilizzo come set di dati di test. I case rimanenti nell'origine dati specificata vengono utilizzati per eseguire il training del modello. Tuttavia, se si utilizza DMX per creare il modello di data mining, per impostazione predefinita tutti i dati vengono utilizzati per eseguire il training del modello e non viene creato alcun set di testing. Per abilitare la creazione di un set di dati di test, è necessario impostare i parametri della clausola WITH HOLDOUT.  
  
 È possibile determinare se i dati in una particolare struttura di data mining sono stati partizionati in set di training e set di testing visualizzando il valore delle proprietà <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> e <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Se si desidera utilizzare le funzioni IsTrainingCase o IsTestCase per restituire i dettagli sui case nel modello, è necessario attivare il drill-through sul modello. Per altre informazioni, vedere [Abilitazione del drill-through per un modello di data mining](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Per restituire i case che fanno parte del set di dati di test, utilizzare la funzione [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa il modello di data mining clustering dallo scenario di mailing diretto di destinazione nel [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Nella query vengono restituiti solo i case utilizzati per il training del modello di data mining. Inoltre, i case di training sono limitati ai clienti di età inferiore a 40 anni.  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 Per altri esempi di query sui case utilizzati nel data mining, vedere [SELECT FROM &#60;modello&#62;. CASI &#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md) e [SELECT FROM &#60;struttura&#62;. CASI](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Set di training e set di dati di Testing](../analysis-services/data-mining/training-and-testing-data-sets.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Query di Data Mining](../analysis-services/data-mining/data-mining-queries.md)  
  
  
