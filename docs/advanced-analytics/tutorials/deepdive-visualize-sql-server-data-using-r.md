---
title: Visualizzare i dati di SQL Server tramite R (amp;#40;procedura approfondita di R e SQL) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0d34ece68c421dbb7aabd845e117c9f07e00d013
ms.sourcegitcommit: 2420c57d2952add3697dbe0467ee1d755c5c2ee5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47217516"
---
#  <a name="visualize-sql-server-data-using-r-sql-and-r-deep-dive"></a>Visualizzare i dati di SQL Server tramite R (amp;#40;procedura approfondita di R e SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondita di Data Science, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

I pacchetti avanzati in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] includono più funzioni ottimizzate per la scalabilità e l'elaborazione parallela. In genere queste funzioni sono precedute dal prefisso **rx** o **Rx**.

Per questa procedura dettagliata, si utilizza il **rxHistogram** funzione per visualizzare la distribuzione dei valori di _creditLine_ colonna in base al sesso.

## <a name="visualize-data-using-rxhistogram"></a>Visualizzare i dati tramite rxHistogram

1. Usare il codice di R seguente per chiamare la funzione [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) e per passare una formula e l'origine dati. È possibile innanzitutto eseguire questa procedura localmente per visualizzare i risultati previsti e il tempo necessario.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Internamente, **rxHistogram** chiama la funzione [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) inclusa nel pacchetto **RevoScaleR** . **rxCube** restituisce un singolo elenco (o un frame di dati) contenente una colonna per ogni variabile specificata nella formula, e una colonna di conteggi.
    
2. A questo punto, impostare il contesto di calcolo al computer SQL Server remoto ed eseguire **rxHistogram** nuovamente.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. I risultati sono esattamente gli stessi, poiché si sta usando la stessa origine dati; tuttavia, i calcoli vengono eseguiti nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  I risultati vengono poi restituiti alla workstation locale per eseguire il tracciato.
   
![risultati istogramma](media/rsql-sue-histogramresults.jpg "risultati istogramma")

4. È inoltre possibile chiamare il **rxCube** funzione e passare i risultati a funzioni di tracciato di R.  Ad esempio, è possibile usare **rxCube** per calcolare la media di *fraudRisk* per ogni combinazione di *numTrans* e *numIntlTrans*, come illustrato nell'esempio seguente:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Per specificare i gruppi usati per il calcolo delle medie, usare la notazione `F()` . In questo esempio `F(numTrans):F(numIntlTrans)` indica che i numeri interi nelle variabili `numTrans` e `numIntlTrans` considerare come variabili categoriche, con un livello per ogni valore intero.
  
    Poiché i livelli bassi e alti sono già stati aggiunti all'origine dati `sqlFraudDS` (usando il `colInfo` parametro), i livelli vengono automaticamente usati nell'istogramma.
  
5. Il valore predefinito restituito pari **rxCube** è un *oggetto rxCube*, che rappresenta una tabulazione incrociata. È tuttavia possibile usare la funzione [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) per convertire i risultati in un frame di dati che può essere facilmente usato in una delle funzioni di tracciato standard di R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Il **rxCube** funzione include un argomento facoltativo *returnDataFrame* = **TRUE**, che è possibile usare per convertire direttamente i risultati in un frame di dati. Esempio:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    L'output di **rxResultsDF** è comunque molto più chiaro e mantiene i nomi delle colonne di origine.
  
6. Infine, eseguire il codice seguente per creare una mappa termica usando la `levelplot` funzione il **reticolo** pacchetto, incluso in tutte le distribuzioni di R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Risultati**
  
    ![risultati grafico a dispersione](media/rsql-sue-scatterplotresults.jpg "risultati grafico a dispersione")
  
Anche da questa analisi veloce, è possibile notare che il rischio di frode aumenta con il numero di transazioni e il numero di transazioni internazionali.

Per altre informazioni sul **rxCube** funzione e quelle dei campi incrociati in generale, vedere [riepiloghi dei dati con RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-step"></a>Passaggio successivo

[Creare modelli R con dati di SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Passaggio precedente

[Creare ed eseguire script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
