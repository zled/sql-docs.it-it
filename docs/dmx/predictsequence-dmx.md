---
title: PredictSequence (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 813641b7fa72405a0ba5a026e255f03feb94bd05
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841554"
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vengono stimati i valori di sequenza futuri per un set specificato di dati in sequenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Oggetto \<espressione di tabella >.  
  
## <a name="remarks"></a>Remarks  
 Se il *n* parametro viene specificato, restituisce i valori seguenti:  
  
-   Se *n* è maggiore di zero, i valori di sequenza più probabili nella prossima *n* passaggi.  
  
-   Se entrambi *n-inizio* e *n-end* vengono specificati, la sequenza di valori da *n-inizio* a *n-end*.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita una sequenza dei cinque prodotti che più probabilmente verranno acquistati da un cliente nel database [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] in base al modello di data mining Sequence Clustering.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
