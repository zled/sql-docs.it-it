---
title: SELECT FROM &lt;modello&gt; (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SELECT
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- empty prediction joins [DMX]
- SELECT FROM <model> statement
ms.assetid: dc5b9a01-e308-4ee8-84fc-ba4b991c60aa
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 064c5514e014b8ba976c21001665626bcb71722e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="select-from-ltmodelgt-dmx"></a>SELECT FROM &lt;modello&gt; (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un prediction join vuoto e restituisce il valore o i valori più probabili per le colonne specificate. Per creare la stima viene utilizzato solo il contenuto del modello di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente espressioni o colonne di tipo PREDICT o PREDICT ONLY.  
  
 *n*  
 Facoltativa. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *model*  
 Identificatore del modello.  
  
 *elenco delle condizioni*  
 Facoltativa. Condizioni per limitare i valori restituiti dall'elenco di colonne.  
  
 *espressione*  
 Facoltativa. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Le colonne di *elenco di espressioni* devono essere definite come predict o predict only oppure correlata a una colonna stimabile.  
  
## <a name="naive-bayes-example"></a>Esempio sull'algoritmo Naive Bayes  
 Nell'esempio seguente viene eseguito un prediction join vuoto sulla colonna Bike Buyer e viene restituito lo stato più probabile nel modello di data mining TM_Naive_Bayes.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Esempio sull'algoritmo Time Series  
 Nell'esempio seguente viene eseguita una stima sulla colonna Amount nel modello Forecasting e vengono restituiti i quattro intervalli temporali successivi. La colonna Model Region combina modelli di biciclette e regioni in un singolo identificatore. La query utilizza il [PredictTimeSeries &#40;DMX&#41; ](../dmx/predicttimeseries-dmx.md) funzione per eseguire la stima.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELEZIONARE &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
