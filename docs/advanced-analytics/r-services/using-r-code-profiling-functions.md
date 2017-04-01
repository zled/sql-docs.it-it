---
title: "Utilizzando le funzioni di analisi del codice R | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 132db249-b9f1-48f5-a63e-c9806cacc4af
caps.latest.revision: 6
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# Utilizzando le funzioni di analisi del codice R
Oltre a utilizzare risorse di SQL Server e strumenti per monitorare l'esecuzione di script R, è possibile utilizzare gli strumenti di prestazioni forniti da altri pacchetti R per ottenere ulteriori informazioni sulle chiamate di funzione interna. In questo argomento viene fornito un elenco di risorse di base per iniziare. Per indicazioni di esperti, si consiglia il capitolo su [prestazioni](http://adv-r.had.co.nz/Performance.html) nel libro "" Advanced R"", di Hadley Wickham.

## <a name="using-rprof"></a>Utilizzo RPROF

*rprof* è una funzione inclusa nel pacchetto di base **utils**, che viene caricato per impostazione predefinita. Un vantaggio offerto da *rprof* viene eseguito il campionamento, riducendo così il carico delle prestazioni dal monitoraggio.

Per utilizzare l'analisi del codice R, chiamare questa funzione e specificano i parametri, incluso il nome del percorso del file di log che verrà scritto. Vedere la Guida di *rprof* per informazioni dettagliate.

In generale, il *rprof* funzione works scrivendo lo stack di chiamate in un file, a intervalli specificati. È quindi possibile utilizzare il *summaryRprof* funzione per elaborare il file di output. 

Profilatura può essere attivata e disattivata nel codice. Per attivare la profilatura, Sospendi la profilatura e quindi riavviarlo, utilizzare una sequenza di chiamate a *rprof*:

1. Specificare file di output della profilatura.

    ```R
    varOutputFile <- "C:/TEMP/run001.log")
    Rprof(varOutputFile)
    ```
2. Disattivare la profilatura
    ```R
    Rprof(NULL)
    ```
    
3. Riavvio di profilatura
    ```R
    Rprof(append=TRUE)
    ```


> [!NOTE] Utilizzare questa funzione richiede che Perl Windows sia installato nel computer in cui viene eseguito codice. Pertanto, è consigliabile profilare il codice durante lo sviluppo in un ambiente R e quindi distribuire il codice sottoposto a debug in SQL Server.  


## <a name="r-system-functions"></a>R le funzioni di sistema

Il linguaggio R include numerose funzioni di pacchetto di base per la restituzione del contenuto delle variabili di sistema. 

Come parte del codice R, ad esempio, è possibile utilizzare `Sys.timezone` per ottenere il fuso orario corrente, o `Sys.Time` per ottenere l'ora di sistema di R. 

Per ottenere informazioni sulle singole funzioni di sistema di R, digitare il nome della funzione come argomento di R `help()` funzione da un prompt dei comandi di R.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Debug e profilatura in R

La documentazione di Microsoft R Open, che viene installato per impostazione predefinita, include un manuale sullo sviluppo di estensioni per il linguaggio R in cui sono illustrati profilatura e debug in modo dettagliato.

Il capitolo è inoltre disponibile online: [https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>R file della Guida

C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual


