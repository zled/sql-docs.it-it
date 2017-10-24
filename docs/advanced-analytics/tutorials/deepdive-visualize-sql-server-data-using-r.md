---
title: Visualizzare i dati di SQL Server tramite R (procedura approfondita di data science) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 023958a137515c519fe8d73e1ce1181dc7579356
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="visualize-sql-server-data-using-r"></a>Visualizzare i dati di SQL Server tramite R

I pacchetti avanzati in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] includono più funzioni ottimizzate per la scalabilità e l'elaborazione parallela. In genere queste funzioni sono precedute dal prefisso *rx* o *Rx*.

In questa procedura si userà la funzione **rxHistogram** per visualizzare la distribuzione dei valori nella colonna _creditLine_ in base al sesso.

## <a name="visualize-data-using-rxhistogram"></a>Visualizzare i dati usando rxHistogram

1. Utilizzare il seguente codice R per chiamare la funzione rxHistogram e passare una formula e l'origine dati. È possibile innanzitutto eseguire questa procedura localmente per visualizzare i risultati previsti e il tempo necessario.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Internamente, rxHistogram chiama la funzione rxCube, che è incluso nel **RevoScaleR** pacchetto. La funzione rxCube restituisce un unico elenco o frame di dati contenenti una colonna per ogni variabile specificata nella formula, nonché una colonna di conteggi.
    
2. A questo punto, impostare il contesto di calcolo per il computer SQL Server remoto e rieseguire rxHistogram.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. I risultati sono esattamente gli stessi, poiché si sta usando la stessa origine dati; tuttavia, i calcoli vengono eseguiti nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  I risultati vengono poi restituiti alla workstation locale per eseguire il tracciato.
   
![risultati istogramma](media/rsql-sue-histogramresults.jpg "risultati istogramma")

4. È anche possibile chiamare la funzione rxCube e passare i risultati a una funzione di tracciato R.  Ad esempio, l'esempio seguente usa rxCube per calcolare la media di *fraudRisk* per ogni combinazione di *numTrans* e *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Per specificare i gruppi usati per il calcolo delle medie, usare la notazione `F()` . In questo esempio, `F(numTrans):F(numIntlTrans)` indica che i numeri interi nelle variabili _numTrans_ e _numIntlTrans_ devono essere considerati come variabili di categoria, con un livello per ogni valore intero.
  
    Poiché i livelli bassi e alti sono già stati aggiunti all'origine dati *sqlFraudDS* tramite il parametro *colInfo* , saranno automaticamente usati nell'istogramma.
  
5. Il valore restituito di rxCube è per impostazione predefinita un *rxCube oggetto*, che rappresenta una tabulazione incrociata. È tuttavia possibile usare la funzione **rxResultsDF** per convertire i risultati in un frame di dati che può essere facilmente usato in una delle funzioni di tracciato standard di R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    > [!TIP]
    > 
    > Si noti che la funzione rxCube include un argomento facoltativo, *returnDataFrame* = TRUE, che è possibile utilizzare per convertire i risultati in un frame di dati direttamente. Esempio:
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
    >   
    > Tuttavia, l'output di rxResultsDF è molto più chiara e mantiene i nomi delle colonne di origine.
  
6. Infine, eseguire il codice seguente per creare una mappa di calore utilizzando il `levelplot` funzione la **reticolato** pacchetto, di cui è incluso in tutte le distribuzioni di R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Risultati**
  
    ![risultati grafico a dispersione](media/rsql-sue-scatterplotresults.jpg "risultati grafico a dispersione")
  
Anche da questa analisi veloce, è possibile notare che il rischio di frode aumenta con il numero di transazioni e il numero di transazioni internazionali.

Per ulteriori informazioni sulla funzione rxCube e quelle dei campi incrociati in generale, vedere [riepiloghi dei dati](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries).

## <a name="next-step"></a>Passaggio successivo

[Creazione di modelli](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Passaggio precedente

[Lezione 2: Creare ed eseguire script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)



