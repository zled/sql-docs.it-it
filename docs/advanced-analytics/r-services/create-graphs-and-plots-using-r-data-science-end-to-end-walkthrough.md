---
title: "Creare grafici e tracciati con R (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
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
ms.assetid: 5f70f0a6-fd4a-410f-9f44-1605503f77ec
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Creare grafici e tracciati con R (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
In questa lezione verranno illustrate tecniche per la generazione di grafici e mappe usando R con dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Si apprenderà come visualizzare facilmente tracciati creati nel server e come passare oggetti grafici al server.  
  
## <a name="creating-graphics"></a>Creazione di oggetti grafici
In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]gli oggetti grafici, i modelli e i risultati vengono serializzati tra il computer e il contesto di calcolo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Quando si usa un contesto di calcolo di SQL Server, potrebbe non essere possibile scaricare la rappresentazione della mappa perché la maggior parte dei server di database di produzione bloccano completamente l'accesso a Internet.  Pertanto, per creare il secondo set di tracciati si genera la rappresentazione della mappa nel client, quindi si sovrappongono a tale rappresentazione i punti archiviati come attributi nella tabella *nyctaxi_sample*.   

A tale scopo, in primo luogo si crea la rappresentazione della mappa mediante chiamate in mappe Google, quindi si passa la rappresentazione della mappa al contesto SQL.  
  
Questo approccio può risultare utile per lo sviluppo di applicazioni personalizzate.   
  
### <a name="create-a-histogram"></a>Creare un istogramma  
Per creare un istogramma si userà l'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creata in precedenza, insieme alla funzione `rxHistogram` inclusa in R Services.  
  
1.  Generare il primo tracciato usando la funzione *rxHistogram*.  La funzione *rxHistogram* fornisce funzionalità simili a quelle presenti nei pacchetti R open source, ma può essere eseguita in un contesto di esecuzione remota. 
  
    ```R  
    #Plot fare amount on SQL Server and return the plot  
    start.time <- proc.time()  
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```         
  
2.  L'immagine viene restituita nel dispositivo grafico R per l'ambiente di sviluppo.  Ad esempio, in RStudio fare clic sulla finestra **Plot** .  In [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]viene aperta una finestra grafica separata.  
  
    ![using rxHistogram to plot fare amounts](../../advanced-analytics/r-services/media/rsql-e2e-rxhistogramresult.png "using rxHistogram to plot fare amounts")  
  
    > [!NOTE]  Dato che l'ordinamento delle righe mediante TOP non è deterministico se non è presente una clausola ORDER BY, i risultati ottenuti possono essere molto diversi. È consigliabile provare con diversi numeri di righe per ottenere grafici differenti, osservando il tempo necessario alla restituzione dei risultati nell'ambiente in uso.  Questa particolare immagine è stata generata usando ~10.000 righe di dati.
  
### <a name="create-a-map-plot"></a>Creare un tracciato mappa  
In questo esempio si genera un oggetto tracciato usando l'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come contesto di calcolo, quindi si restituisce l'oggetto tracciato al contesto di calcolo locale per il rendering.  
   
1.  In primo luogo definire la funzione che crea l'oggetto tracciato.  

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
    + La funzione R personalizzata *mapPlot* crea un grafico a dispersione che usa i punti di inizio corsa dei taxi per tracciare il numero di corse avviate da ogni posizione. Usa i pacchetti **ggplot2** e  **ggmap** , che dovrebbero già essere installati e caricati.  
    + La funzione *mapPlot* accetta due argomenti: un oggetto dati esistente (definito in precedenza tramite *RxSqlServerData*) e la rappresentazione della mappa passata dal client.    
    + Si noti l'uso della variabile *ds* per caricare i dati dall'origine dati creata in precedenza *inDataSource*.  Quando si usano funzioni R open source è necessario che i dati siano caricati in memoria in data frame. A tale scopo è possibile usare la funzione *rxImport* nel pacchetto **RevoScaleR**.  Tuttavia questa funzione viene eseguita in memoria nel contesto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definito in precedenza. Pertanto la funzione non usa la memoria della workstation locale.  
  
2.  Caricare le librerie necessarie per la creazione delle mappe nell'ambiente R locale.  
  
    ```R  
    library(ggmap)  
    library(mapproj)  
    gc <- geocode("Times Square", source = "google")  
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color';    
    ```  
    + Questo codice viene eseguito sul client R. Si noti la chiamata ripetuta delle librerie **ggmap** e **mapproj**. Ciò avviene perché la definizione di funzione precedente veniva eseguita nel contesto del server e le librerie non venivano mai caricate in locale, mentre ora la gestione tracciato viene riportata sulla workstation.  
  
    -   La variabile *gc* memorizza un set di coordinate per Times Square, New York.  
  
    -   La riga che inizia con *googmap* genera una mappa con al centro le coordinate specificate.  
          
  
3.  Eseguire la funzione di creazione tracciato e quindi il rendering dei risultati nell'ambiente R locale. A tale scopo, eseguire il wrapping della funzione tracciato in *rxExec* come illustrato di seguito.  La funzione *rxExec* è inclusa nel pacchetto **RevoScaleR** e supporta l'esecuzione di funzioni R arbitrarie in un contesto di elaborazione remota. 
  
    ```R  
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)  
    plot(myplots[[1]][["myplot"]]);  
  
    ```  
    + Nella prima riga è possibile vedere che i dati della mappa vengono passati come argomento (*googMap*) alla funzione *mapPlot* eseguita in modalità remota. Ciò accade perché le mappe sono state generate nell'ambiente locale e devono essere passate alla funzione per creare il tracciato nel contesto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   
  
        I dati sottoposti a rendering vengono quindi nuovamente serializzati nell'ambiente R locale in modo che sia possibile visualizzarli mediante la finestra **Plot** in RStudio o in un altro dispositivo grafico R.  
  
  
4.  Ecco il tracciato di output, che visualizza i punti di inizio corsa come punti rossi sulla mappa.  
  
    ![plotting taxi rides using a custom R function](../../advanced-analytics/r-services/media/rsql-e2e-mapplot.png "plotting taxi rides using a custom R function")  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 3: Creare funzionalità di dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  
