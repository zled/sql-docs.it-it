---
title: " Visualizzare i dati di SQL Server usando R (SQL e R approfondimento) | Documenti Microsoft"
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 77321589a87230535502cc37a75bf09722abb66d
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
#  <a name="visualize-sql-server-data-using-r-sql-and-r-deep-dive"></a>Visualizzare i dati di SQL Server usando R (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

I pacchetti avanzati in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] includono più funzioni ottimizzate per la scalabilità e l'elaborazione parallela. In genere queste funzioni sono precedute dal prefisso **rx** o **Rx**.

Questa procedura dettagliata, utilizza il **rxHistogram** funzione per visualizzare la distribuzione dei valori di _creditLine_ colonna in base al sesso.

## <a name="visualize-data-using-rxhistogram"></a>Visualizzare i dati usando rxHistogram

1. Usare il codice di R seguente per chiamare la funzione [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) e per passare una formula e l'origine dati. È possibile innanzitutto eseguire questa procedura localmente per visualizzare i risultati previsti e il tempo necessario.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Internamente, **rxHistogram** chiama la funzione [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) inclusa nel pacchetto **RevoScaleR** . **rxCube** restituisce un unico elenco o frame di dati contenenti una colonna per ogni variabile specificata nella formula, nonché una colonna di conteggi.
    
2. A questo punto, impostare il contesto di calcolo per il computer SQL Server remoto ed eseguire **rxHistogram** nuovamente.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. I risultati sono esattamente gli stessi, poiché si sta usando la stessa origine dati; tuttavia, i calcoli vengono eseguiti nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  I risultati vengono poi restituiti alla workstation locale per eseguire il tracciato.
   
![risultati istogramma](media/rsql-sue-histogramresults.jpg "risultati istogramma")

4. È inoltre possibile chiamare il **rxCube** funzione e passare i risultati a una tracciato funzione di R.  Ad esempio, è possibile usare **rxCube** per calcolare la media di *fraudRisk* per ogni combinazione di *numTrans* e *numIntlTrans*, come illustrato nell'esempio seguente:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Per specificare i gruppi usati per il calcolo delle medie, usare la notazione `F()` . In questo esempio, `F(numTrans):F(numIntlTrans)` indica che i numeri interi nelle variabili di `_numTrans` e `numIntlTrans` devono essere considerate come variabili categoriche, con un livello per ogni valore intero.
  
    Poiché i livelli bassi e alti sono già sono aggiunti all'origine dati `sqlFraudDS` (utilizzando la `colInfo` parametro), i livelli vengono usati automaticamente nell'istogramma.
  
5. Il valore di restituito predefinito **rxCube** è un *rxCube oggetto*, che rappresenta una tabulazione incrociata. È tuttavia possibile usare la funzione [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) per convertire i risultati in un frame di dati che può essere facilmente usato in una delle funzioni di tracciato standard di R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Il **rxCube** funzione include un argomento facoltativo, *returnDataFrame* = **TRUE**, che è possibile utilizzare per convertire i risultati in un frame di dati direttamente. Ad esempio
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    L'output di **rxResultsDF** è comunque molto più chiaro e mantiene i nomi delle colonne di origine.
  
6. Infine, eseguire il codice seguente per creare una mappa di calore utilizzando il `levelplot` funzione la **reticolato** pacchetto, di cui è incluso in tutte le distribuzioni di R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Risultati**
  
    ![risultati grafico a dispersione](media/rsql-sue-scatterplotresults.jpg "risultati grafico a dispersione")
  
Anche da questa analisi veloce, è possibile notare che il rischio di frode aumenta con il numero di transazioni e il numero di transazioni internazionali.

Per ulteriori informazioni sul **rxCube** funzione e quelle dei campi incrociati in generale, vedere [i riepiloghi dei dati con RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-step"></a>Passaggio successivo

[Creare modelli R con i dati di SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare ed eseguire script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
