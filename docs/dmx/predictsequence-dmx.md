---
title: PredictSequence (DMX) | Documenti Microsoft
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
- PredictSequence
dev_langs:
- DMX
helpviewer_keywords:
- PredictSequence function
ms.assetid: c2992dfc-b99d-4430-8dcd-21ad3ffd4590
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e9ddd402be082937ec828a86d82a238d121e55dd
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono stimati i valori di sequenza futuri per un set specificato di dati in sequenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Oggetto \<espressione di tabella >.  
  
## <a name="remarks"></a>Osservazioni  
 Se il  *n*  viene specificato, restituisce i valori seguenti:  
  
-   Se  *n*  è maggiore di zero, i valori di sequenza più probabili nella prossima  *n*  passaggi.  
  
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
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

