---
title: BottomPercent (DMX) | Documenti Microsoft
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
- BOTTOMPERCENT
dev_langs:
- DMX
helpviewer_keywords:
- BottomPercent function
ms.assetid: 984eb18a-c55c-49f3-81fa-918dfc983174
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cdc60cbc61d0c84953f2e80a5896dbd8465bdb8a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="bottompercent-dmx"></a>BottomPercent (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce, in ordine di rango crescente, le ultime righe di una tabella il cui totale cumulativo corrisponde almeno a una percentuale specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BottomPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="arguments"></a>Argomenti  
 *\<Espressione di tabella >*  
 Nome di una colonna della tabella nidificata o espressione valutata a livello di tabella.  
  
 *\<Rank expression >*  
 Colonna della tabella nidificata o espressione che restituisce una colonna.  
  
 *\<% >*  
 Valore Double che indica la percentuale di destinazione totale.  
  
## <a name="result-type"></a>Tipo di risultato  
 Tabella.  
  
## <a name="remarks"></a>Osservazioni  
 Il **BottomPercent** funzione restituisce le righe più in basso nell'ordine di rango crescente. Il rango è basato sul valore valutato del \<rank expression > argomento per ogni riga, in modo che la somma del \<rank expression > valori corrisponde almeno alla percentuale specificata dal \<% > argomento. **BottomPercent** restituisce il più piccolo numero di elementi possibile mentre soddisfa ancora il valore percentuale specificato.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente crea una query di stima sul modello di associazione compilato nel [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
 Per comprendere il funzionamento BottomPercent, potrebbe essere utile eseguire prima una query di stima che restituisce solo la tabella nidificata.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  In questo esempio il valore fornito come input contiene una virgoletta singola, e pertanto è necessario utilizzare il carattere di escape preceduto da un'altra virgoletta singola. Se non si è certi della sintassi per l'inserimento di un carattere di escape, è possibile utilizzare il generatore delle query di stima per creare la query. Quando si seleziona il valore dall'elenco a discesa, viene automaticamente inserito il carattere di escape necessario. Per ulteriori informazioni, vedere [creare una Query Singleton Progettazione modelli di Data Mining](../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md).  
  
 Risultati dell'esempio:  
  
|Modello|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Water Bottle|2866|0.192620472|0.175205052|  
|Patch kit|2113|0.142012232|0.132389356|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Road Tire Tube|1588|0.106727603|0.101229538|  
|Cycling Cap|1473|0.098998589|0.094256014|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
  
 La funzione BottomPercent accetta i risultati della query e restituisce le righe con valori più piccoli che vengono sommate alla percentuale specificata.  
  
```  
SELECT   
BottomPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Il primo argomento alla funzione BottomPercent è il nome di una colonna di tabella. In questo esempio, la tabella nidificata viene restituita chiamando la funzione di stima e utilizzando l'argomento INCLUDE_STATISTICS.  
  
 Il secondo argomento per la funzione BottomPercent è la colonna nella tabella nidificata che consente di ordinare i risultati. In questo esempio l'opzione INCLUDE_STATISTICS restituisce le colonne $SUPPORT, $PROBABILTY e $ADJUSTED PROBABILITY. In questo esempio viene utilizzato $SUPPORT poiché i valori di supporto non sono frazionari e pertanto sono più facili da verificare.  
  
 Il terzo argomento alla funzione BottomPercent specifica la percentuale, come valore double. Per ottenere le righe che rappresentano il 50 percento del supporto con i valori più bassi, digitare 50.  
  
 Risultati dell'esempio:  
  
|Modello|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Cycling Cap|1473|0.098998589|0.094256014|  
|Road Tire Tube|1588|0.106727603|0.101229538|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
  
 **Nota** in questo esempio viene fornito solo per illustrare l'utilizzo di BottomPercent. A seconda della dimensione del set di dati, questa query potrebbe impiegare molto tempo per l'esecuzione.  
  
> [!WARNING]  
>  Le funzioni MDX per TOPPERCENT e BOTTOMPERCENT possono generare risultati imprevisti quando i valori utilizzati per calcolare la percentuale includono numeri negativi. Questo comportamento non influisce sulle funzioni DMX. Per ulteriori informazioni, vedere [BottomPercent &#40; MDX &#41; ](../mdx/bottompercent-mdx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)  
  
  

