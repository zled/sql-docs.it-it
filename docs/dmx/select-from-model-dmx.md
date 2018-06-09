---
title: SELECT FROM &lt;modello&gt; (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aac800e225eb5323b1bffeafda77d059f0a837e2
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842174"
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
 Facoltativo. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *model*  
 Identificatore del modello.  
  
 *elenco delle condizioni*  
 Facoltativo. Condizioni per limitare i valori restituiti dall'elenco di colonne.  
  
 *expression*  
 Facoltativo. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Remarks  
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
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
