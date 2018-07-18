---
title: Creare grafici e grafici utilizzando SQL e R (procedura dettagliata) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4d4b573bc2aa0cc48e7c158edafa0dd604e6fc87
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585473"
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>Creare grafici e grafici utilizzando SQL e R (procedura dettagliata)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa parte della procedura dettagliata, si informazioni tecniche per la generazione di grafici e mappe usando R con i dati di SQL Server. Creare un semplice istogramma, per esercitarsi e quindi sviluppare un tracciato mappa più complesso.

### <a name="create-a-histogram"></a>Creare un istogramma

1. Generare il primo tracciato usando la funzione [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) .  La funzione di rxHistogram fornisce funzionalità simili a quelle di pacchetti R open source, ma è possibile eseguire in un contesto di esecuzione in modalità remota.

    ```R
    # Plot fare amount on SQL Server and return the plot
    start.time <- proc.time()
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate plot.", sep=""))
    ```

2. L'immagine viene restituita nel dispositivo grafico R per l'ambiente di sviluppo.  Ad esempio, in RStudio fare clic sulla finestra **Plot** .  In [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]viene aperta una finestra grafica separata.

    ![uso di rxHistogram per tracciare gli importi delle tariffe](media/rsql-e2e-rxhistogramresult.png "uso di rxHistogram per tracciare gli importi delle tariffe")

    > [!NOTE]
    > Il grafico aspetto diverso?
    >  
    > Ciò accade perché _inDataSource_ utilizza solo le prime 1000 righe. L'ordinamento delle righe usando il comando TOP è non deterministico in assenza di una clausola ORDER BY, pertanto è previsto che i dati e il grafico risultante potrebbe variare.
    > Questa particolare immagine è stata generata usando circa 10.000 righe di dati. È consigliabile provare con diversi numeri di righe per ottenere grafici differenti, osservando il tempo necessario alla restituzione dei risultati nell'ambiente in uso.

### <a name="create-a-map-plot"></a>Creare un tracciato di mappa

In genere, i server di database bloccano l'accesso a Internet. Può essere poco pratico quando si usano pacchetti R che è necessario scaricare le mappe o altre immagini per generare i grafici. Tuttavia, è una soluzione alternativa che possono risultare utili durante lo sviluppo di applicazioni personalizzate. In pratica, generare la rappresentazione della mappa sul client e quindi sovrapposizione sulla mappa i punti che vengono archiviati come attributi nella tabella di SQL Server.

1. Definire la funzione che crea l'oggetto tracciato R. La funzione personalizzata *mapPlot* crea un grafico a dispersione che utilizza i percorsi di prelievo taxi e il numero di si basa avviata da ogni località è rappresentata. Usa i pacchetti **ggplot2** e  **ggmap** , che dovrebbero già essere installati e caricati.

    ```R
    mapPlot <- function(inDataSource, googMap){
        library(ggmap)
        library(mapproj)
        ds <- rxImport(inDataSource)
        p <- ggmap(googMap)+
        geom_point(aes(x = pickup_longitude, y =pickup_latitude ), data=ds, alpha =.5,
    color="darkred", size = 1.5)
        return(list(myplot=p))
    }
    ```

    + Il *mapPlot* funzione accetta due argomenti: un oggetto dati esistente, che sono definiti in precedenza mediante RxSqlServerData e la rappresentazione di mappa passate dal client.
    + Nella riga che inizia con il *ds* variabile rxImport viene utilizzato per caricare i dati di memoria dall'origine dati creata in precedenza, *inDataSource*. (Tale origine dati contiene solo 1000 righe, se si desidera creare una mappa con più punti dati, è possibile sostituire un'origine dati diversa).
    + Quando si utilizza **open source di** funzioni R, i dati devono essere caricate nel frame di dati nella memoria locale. Tuttavia, chiamando la [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) funzione, è possibile eseguire nella memoria del contesto di calcolo remoto.

2. Modificare il contesto di calcolo locale e caricare le librerie necessarie per la creazione di mappe.

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + La variabile `gc` memorizza un set di coordinate per Times Square, New York.

    + La riga che inizia con `googmap` genera una mappa con al centro le coordinate specificate.

3. Passare al contesto di calcolo di SQL Server e il rendering dei risultati, eseguendo il wrapping viene tracciato in [rxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec) come illustrato di seguito. La funzione rxExec fa parte di **RevoScaleR** pacchetto e supporta l'esecuzione delle funzioni R arbitrarie in un contesto di calcolo remoto.

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + I dati della mappa in `googMap` viene passato come argomento alla funzione eseguita in modalità remota *mapPlot*. Poiché le mappe sono state generate nell'ambiente locale, deve essere passati alla funzione per creare il tracciato nel contesto di SQL Server.

    + Quando la riga che inizia con `plot` esecuzioni, il rendering dei dati viene nuovamente serializzato nell'ambiente R locale in modo da visualizzare nel client di R.

    > [!NOTE]
    > Se si utilizza SQL Server in una macchina virtuale di Azure, è possibile che venga visualizzato un errore a questo punto. Ciò avviene perché una regola del firewall predefinite in Azure impedisce l'accesso alla rete tramite codice R. Per informazioni dettagliate su come risolvere questo errore, vedere [Installing R Services in una macchina virtuale Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

4. La figura seguente mostra il tracciato di output. I punti di inizio corsa dei taxi vengono aggiunti alla mappa come punti rossi. L'aspetto dell'immagine potrebbe essere diverso, a seconda di quanti indirizzi sono nell'origine dati che è stato utilizzato.

    ![creazione del tracciato delle corse in taxi con una funzione R personalizzata](media/rsql-e2e-mapplot.png "creazione del tracciato delle corse in taxi con una funzione R personalizzata")

## <a name="next-lesson"></a>Lezione successiva

[Creare le funzionalità di dati con R e SQL](walkthrough-create-data-features.md)

## <a name="previous-lesson"></a>Lezione precedente

[Riepilogare i dati con R](walkthrough-view-and-summarize-data-using-r.md)
