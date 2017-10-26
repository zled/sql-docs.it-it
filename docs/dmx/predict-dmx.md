---
title: Stima (DMX) | Documenti Microsoft
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
- PREDICT
dev_langs:
- DMX
helpviewer_keywords:
- Predict function
ms.assetid: f02ff4b3-9bd7-409d-ad14-ead67b3206c4
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a976011c3b892d826d29038fb0501e57db4c5008
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="predict-dmx"></a>Predict (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **Predict** funzione restituisce un valore stimato o set di valori, per una colonna specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>Si applica a  
 Riferimento a colonna scalare o a colonna di tabella.  
  
## <a name="return-type"></a>Tipo restituito  
 \<riferimento a colonna scalare >  
  
 o  
  
 \<tabella di riferimento di colonna >  
  
 Il tipo restituito dipende dal tipo di colonna a cui è applicata la funzione.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY e INCLUDE_STATISTICS sono applicabili solo a riferimenti a colonne di tabella, mentre EXCLUDE_NULL e INCLUDE_NULL sono applicabili solo a riferimenti a colonne scalari.  
  
## <a name="remarks"></a>Osservazioni  
 Le opzioni disponibili includono EXCLUDE_NULL (predefinita), INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (predefinita), INPUT_ONLY e INCLUDE_STATISTICS.  
  
> [!NOTE]  
>  Per i modelli time series, la funzione di stima non supporta INCLUDE_STATISTICS.  
  
 Se è specificato il parametro INCLUDE_NODE_ID, nel risultato verrà restituita la colonna $NODEID. NODE_ID è il nodo di contenuto su cui viene eseguita la stima per un case specifico. Questo parametro è facoltativo quando si utilizza Predict sulle colonne della tabella.  
  
 Il  *n*  parametro si applica alle colonne della tabella. Imposta il numero delle righe restituite in base al tipo di stima. Se la colonna sottostante è una sequenza, chiama il **PredictSequence** (funzione). Se la colonna sottostante contiene una serie temporale, chiama il **PredictTimeSeries** (funzione). Per i tipi di stima associativi viene chiamata la **PredictAssociation** (funzione).  
  
 Il **Predict** funzione supporta il polimorfismo.  
  
 Vengono spesso utilizzate le seguenti forme abbreviate alternative:  
  
-   [Gender] è un'alternativa per **Predict**([Gender], EXCLUDE_NULL).  
  
-   [Products Purchases] è un'alternativa per **Predict**([Products Purchases], EXCLUDE_NULL, EXCLUSIVE).  
  
    > [!NOTE]  
    >  Il tipo restituito da questa funzione viene a sua volta gestito come riferimento a colonna. Ciò significa che il **Predict** funzione può essere utilizzata come argomento in altre funzioni che accettano un riferimento a colonna come argomento (tranne che per il **Predict** funzione stessa).  
  
 Passando INCLUDE_STATISTICS a una stima per una colonna con valori di tabella aggiunge le colonne **$Probability** e **$Support** per la tabella risultante. che descrivono la probabilità dell'esistenza del record della tabella nidificata associato.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa la funzione di stima per restituire i quattro prodotti nel database Adventure Works che più probabilmente verranno venduti insieme. Poiché la funzione è stima basata su un modello di data mining delle regole di associazione, viene automaticamente utilizzata la **PredictAssociation** funzionano come descritto in precedenza.  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 Risultati dell'esempio:  
  
 Questa query restituisce una singola riga di dati con una sola colonna, `Expression`, che però contiene la seguente tabella nidificata.  
  
|Modello|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Water Bottle|2866|0.192620471805901|0.175205052318795|  
|Patch Kit|2113|0.142012232004839|0.132389356196586|  
|Mountain Tire Tube|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

