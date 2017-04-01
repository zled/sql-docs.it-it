---
title: "Visualizzare i dati di SQL Server tramite R (Procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Visualizzare i dati di SQL Server tramite R (Procedura approfondita per l&#39;analisi scientifica dei dati)
I pacchetti avanzati in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] includono più funzioni ottimizzate per la scalabilità e l'elaborazione parallela. In genere queste funzioni sono precedute dal prefisso *rx* o *Rx*.  
  
In questa procedura si userà la funzione *rxHistogram* per visualizzare la distribuzione dei valori nella colonna _creditLine_ in base al sesso.  
  
## Visualizzare i dati tramite rxHistogram e rxCube  
  
1.  Usare il codice di R seguente per chiamare la funzione *rxHistogram* e per passare una formula e l'origine dati. È possibile innanzitutto eseguire questa procedura localmente per visualizzare i risultati previsti e il tempo necessario.
  
    ```R  
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")   
    ```  
 
    Internamente, *rxHistogram* chiama la funzione *rxCube* inclusa nel pacchetto **RevoScaleR**. La funzione *rxCube* restituisce un singolo elenco (o un frame di dati), contenente una colonna per ogni variabile specificata nella formula, e una colonna di conteggi.
    
2. A questo punto, impostare il contesto di calcolo per il computer SQL Server remoto ed eseguire di nuovo *rxHistogram*.
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
 
3.    I risultati sono esattamente gli stessi, poiché si sta usando la stessa origine dati; tuttavia, i calcoli vengono eseguiti nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  I risultati vengono poi restituiti alla workstation locale per eseguire il tracciato.  
   
![histogram results](../../advanced-analytics/r-services/media/rsql-sue-histogramresults.jpg "histogram results")  

  
4.  È inoltre possibile chiamare la funzione *rxCube* e passare i risultati a funzioni di tracciato di R.  Ad esempio, è possibile usare *rxCube* per calcolare la media di *fraudRisk* per ogni combinazione di *numTrans* e *numIntlTrans*, come illustrato nell'esempio seguente:  
  
    ```R  
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)   
    ```  
  
    Per specificare i gruppi usati per il calcolo delle medie, usare la notazione `F()`. In questo esempio, `F(numTrans):F(numIntlTrans)` indica che i numeri interi nelle variabili _numTrans_ e _numIntlTrans_ devono essere considerati come variabili di categoria, con un livello per ogni valore intero.  
  
    Poiché i livelli bassi e alti sono già stati aggiunti all'origine dati *sqlFraudDS* tramite il parametro *colInfo*, saranno automaticamente usati nell'istogramma.  
  
5.  Il valore restituito di *rxCube* è per impostazione predefinita un *oggetto rxCube* che rappresenta una tabulazione incrociata. È tuttavia possibile usare la funzione *rxResultsDF* per convertire i risultati in un frame di dati che può essere facilmente usato in una delle funzioni di tracciato standard di R.  
  
    ```R  
    cubePlot <- rxResultsDF(cube1)   
    ```  
  
    > [!TIP]  
    > Si noti che la funzione *rxCube* include l'argomento facoltativo *returnDataFrame* = TRUE, che è possibile usare per convertire direttamente i risultati in un frame di dati. Esempio:  
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`  
    >   
    > L'output di *rxResultsDF* è comunque molto più chiaro e mantiene i nomi delle colonne di origine.  
  
6.  Eseguire infine il codice seguente per creare una mappa termica usando la funzione *levelplot* del pacchetto **lattice** incluso in tutte le distribuzioni di R.  
  
    ```R  
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)   
    ```  
  
    **Risultati**  
  
    ![scatterplot results](../../advanced-analytics/r-services/media/rsql-sue-scatterplotresults.jpg "scatterplot results")  
  
Anche da questa analisi veloce, è possibile notare che il rischio di frode aumenta con il numero di transazioni e il numero di transazioni internazionali.

Per altre informazioni sulla funzione *rxCube* e sulle funzioni a campi incrociati in generale, vedere [Data Summaries](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries) (Riepiloghi dei dati).  
  
## Passaggio successivo  
[Creare modelli &#40;procedura approfondita per l'analisi scientifica dei dati &#41;](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Lezione 2: Creare ed eseguire script R &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
