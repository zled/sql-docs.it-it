---
title: 'Lezione 4: Creazione di stime basate su serie temporali utilizzando DMX | Documenti Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a345b37d13ade71baad6635cee0508e97d7755eb
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312409"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>Lezione 4: Creazione di stime basate su serie temporali utilizzando DMX
  In questa lezione e nella lezione seguente si utilizzerà Data Mining DMX (Data Extensions) per creare tipi diversi di stime basate sui modelli time series creato nel [lezione 1: creazione di un modello di Data Mining Time Series e una struttura di Data Mining](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)e [lezione 2: aggiunta di modelli di Data Mining per la struttura di Data Mining Time Series](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).  
  
 Con un modello Time Series si dispone di numerose opzioni per l'esecuzione di stime:  
  
-   Utilizzare gli schemi e i dati esistenti nel modello di data mining.  
  
-   Utilizzare gli schemi esistenti nel modello di data mining, ma fornire nuovi dati.  
  
-   Aggiungere nuovi dati al modello o aggiornare il modello.  
  
 La sintassi per effettuare questi tipi di stima è riportata di seguito:  
  
 Stima basata su serie temporali predefinita  
 Uso [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) per restituire il numero specificato di stime dal modello di data mining sottoposto a training.  
  
 Ad esempio, vedere [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) o [ora Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).  
  
 EXTEND_MODEL_CASES  
 Uso [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) con l'argomento EXTEND_MODEL_CASES per aggiungere nuovi dati, estendere la serie e creare stime basate sul modello di data mining aggiornato.  
  
 Questa esercitazione contiene un esempio dell'utilizzo di EXTEND_MODEL_CASES.  
  
 REPLACE_MODEL_CASES  
 Uso [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) con l'argomento REPLACE_MODEL_CASES per sostituire i dati originali con una nuova serie di dati e quindi creare stime basate su applicazione degli schemi nel modello di data mining per i nuovi dati serie.  
  
 Per un esempio di come utilizzare REPLACE_MODEL_CASES, vedere [lezione 2: compilazione di uno Scenario di previsione &#40;esercitazione intermedia sul Data Mining Data&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione verranno eseguite le attività seguenti:  
  
-   Creare una query per ottenere le stime predefinite sulla base dei dati esistenti.  
  
 Nella lezione successiva verranno eseguite le attività correlate seguenti:  
  
-   Creare una query per fornire nuovi dati e ottenere stime aggiornate.  
  
 Oltre a creare manualmente le query tramite DMX, è anche possibile creare stime tramite il generatore delle query di stima in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="simple-time-series-prediction-query"></a>Semplice query di stima basata su serie temporali  
 Il primo passaggio consiste nell'utilizzare l'istruzione `SELECT FROM` insieme alla funzione `PredictTimeSeries` per creare stime basate su serie temporali. I modelli Time Series supportano una sintassi semplificata per la creazione di stime: non è necessario fornire alcun input, ma è sufficiente specificare il numero di stime da creare. Di seguito è riportato un esempio generico dell'istruzione da utilizzare:  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 Elenco di selezione può contenere colonne del modello, ad esempio il nome del prodotto di riga che si sta creando stime, o funzioni di stima, ad esempio [Lag &#40;DMX&#41; ](/sql/dmx/lag-dmx) o [ &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), che sono specifiche per i modelli di data mining time series.  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>Per creare una semplice query di stima basata su serie temporali  
  
1.  In **Esplora oggetti**, fare doppio clic sull'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], scegliere **nuova Query**, quindi fare clic su **DMX**.  
  
     Verrà avviato l'editor di query con una nuova query vuota.  
  
2.  Copiare l'esempio generico dell'istruzione nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    <select list>   
    ```  
  
     con:  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     La prima riga consente di recuperare il valore del modello di data mining che identifica la serie.  
  
     La seconda e terza riga utilizzano la funzione `PredictTimeSeries`. Ogni riga stima un attributo diverso, `[Quantity]` o `[Amount]`. I numeri dopo i nomi degli attributi stimabili specificano il numero di intervalli temporali da stimare.  
  
     La clausola `AS` viene utilizzata per fornire un nome per la colonna restituita da ogni funzione di stima. Se non si fornisce un alias, per impostazione predefinita entrambe le colonne vengono restituite con l'etichetta `Expression`.  
  
4.  Sostituire quanto segue:  
  
    ```  
    [<mining model>]   
    ```  
  
     con:  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  Sostituire quanto segue:  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     con:  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     L'istruzione completa dovrebbe risultare analoga alla seguente:  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  Nel **File** menu, fare clic su **Salva Dmxquery1.DMX**.  
  
7.  Nel **Salva con nome** finestra di dialogo, selezionare la cartella appropriata e denominare il file `SimpleTimeSeriesPrediction.dmx`.  
  
8.  Sulla barra degli strumenti, fare clic sui **Execute** pulsante.  
  
     La query restituisce sei stime per ognuna delle due combinazioni di prodotto e area specificate nella clausola `WHERE`.  
  
 Nella lezione successiva verrà creata una query che fornisce nuovi dati al modello e confronta i risultati di tale stima con quella appena creata.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Lezione 5: Estendere la serie temporale del modello](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>Vedere anche  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)   
 [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx)   
 [Tempo Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Lezione 2: Compilazione di uno Scenario di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
