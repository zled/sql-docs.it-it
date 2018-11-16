---
title: Uso di funzioni (SQL Server Machine Learning) la profilatura del codice R | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 64f065df5f5769e37bb1d5a8dbc2fba2d5f936ee
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703969"
---
# <a name="using-r-code-profiling-functions"></a>Uso delle funzioni di profiling del codice R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Oltre a usare risorse e strumenti di SQL Server per monitorare l'esecuzione di script R, è possibile usare gli strumenti per le prestazioni forniti da altri pacchetti R per ottenere altre informazioni sulle chiamate di funzioni interne. Questo argomento contiene un elenco di alcune risorse di base per iniziare. Per indicazioni di esperti, è consigliabile il capitolo sul [prestazioni](https://adv-r.had.co.nz/Performance.html) nel libro "Advanced R", di Hadley Wickham.

## <a name="using-rprof"></a>Uso di RPROF

*rprof* è una funzione inclusa nel pacchetto di base **utils**, caricato per impostazione predefinita. Un vantaggio di *rprof* è il fatto di eseguire il campionamento, riducendo il carico delle prestazioni sul monitoraggio.

Per usare il profiling R nel codice, chiamare questa funzione e specificarne i parametri, incluso il percorso del file di log che verrà scritto. Per informazioni dettagliate, vedere la Guida di *rprof*.

In generale, la funzione *rprof* opera scrivendo lo stack di chiamate in un file a intervalli specificati. È quindi possibile usare la funzione *summaryRprof* per elaborare il file di output. 

È possibile attivare o disattivare il profiling nel codice. Per attivare il profiling, sospenderlo e quindi riavviarlo, è necessario usare una sequenza di chiamate a *rprof*:

1. Specificare il file di output del profiling.

    ```R
    varOutputFile <- "C:/TEMP/run001.log")
    Rprof(varOutputFile)
    ```
2. Disattivare il profiling
    ```R
    Rprof(NULL)
    ```
    
3. Riavviare il profiling
    ```R
    Rprof(append=TRUE)
    ```


> [!NOTE]
> Per poter usare questa funzione, è necessario che Windows Perl sia installato nel computer in cui viene eseguito il codice. Di conseguenza, è consigliabile profilare il codice durante lo sviluppo in un ambiente R e quindi distribuire il codice sottoposto a debug in SQL Server.  


## <a name="r-system-functions"></a>Funzioni di sistema R

Il linguaggio R include molte funzioni di pacchetto di base per la restituzione del contenuto delle variabili di sistema. 

Come parte del codice R, ad esempio, è possibile usare `Sys.timezone` per ottenere il fuso orario corrente o `Sys.Time` per ottenere l'ora di sistema da R. 

Per ottenere informazioni su singole funzioni di sistema R, digitare il nome della funzione come argomento per la funzione R `help()` da un prompt dei comandi di R.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Debug e profiling in R

La documentazione per Microsoft R Open, installata per impostazione predefinita, include un manuale sullo sviluppo di estensioni per il linguaggio R, che descrive il profiling e il debug in modo dettagliato.

Questo capitolo è anche disponibile online: [https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>Percorso dei file della Guida di R

C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual



