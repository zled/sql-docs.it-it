---
title: Mediante il pacchetto MicrosoftML con SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: r-services
ms.service: 
ms.component: advanced-analytics
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 1c377717-e281-431e-8171-3924dcce1cdd
caps.latest.revision: "132"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b802daf9a02734245bc5adb0695fded14063fca5
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>Mediante il pacchetto MicrosoftML con SQL Server

Il [ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) pacchetto che viene fornito con Microsoft R Server e SQL Server 2017 include più algoritmi di machine learning. Queste API sono state sviluppate da Microsoft per applicazioni di apprendimento automatico interno e sono state perfezionate negli anni per supportare ad alte prestazioni sui big data, tramite l'elaborazione multicore e il flusso di dati veloce. MicrosoftML inoltre include numerose trasformazioni per l'elaborazione di immagini e testo.

In SQL Server 2017 CTP 2.0 è stato aggiunto il supporto per la lingua di Python. Il **microsoftml** del pacchetto di Python contiene funzioni equivalenti a quelli nel pacchetto MicrosoftML per R. 

+ **MicrosoftML per R**

    Riferimento di introduzione e pacchetto: [MicrosoftML: computer gli algoritmi di apprendimento R](https://docs.microsoft.com/en-us/r-server/r-reference/microsoftml/microsoftml-package)

    Essendo distinzione maiuscole/minuscole R, assicurarsi che si fa riferimento il nome corretto durante il caricamento del pacchetto.

+ **microsoftml per Python**

    Riferimento di introduzione e pacchetto: [microsoftml (libreria di funzioni per Python)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package). 

## <a name="whats-in-microsoftml"></a>Novità in MicrosoftML

MicrosoftML contiene un'ampia gamma di trasformazioni che sono state ottimizzate per le prestazioni e gli algoritmi di apprendimento automatico.

### <a name="machine-learning-algorithms"></a>Algoritmi di Machine learning

-  Modelli lineari: `rxFastLinear` è uno strumento di apprendimento lineare basato su stocastico ascent coordinate doppio che può essere utilizzato per la regressione o classificazione binaria. Il modello supporta la regolarizzazione L1 ed L2.

- Modelli di foresta delle decisioni e di struttura ad albero delle decisioni: `rxFastTree` è un algoritmo albero delle decisioni con Boosting originariamente noto come FastRank, che è stata sviluppata per l'utilizzo in Bing. È uno degli strumenti di apprendimento più noti e veloci. Supporta la regressione e la classificazione binaria.

  `rxFastForest`un modello di regressione logistica è basato sul metodo foreste casuali. È simile alla funzione `rxLogit` in RevoScaleR, ma supporta la regolarizzazione L1 ed L2. Supporta la regressione e la classificazione binaria.

- La regressione logistica: `rxLogisticRegression` è simile a un modello di regressione logistica il `rxLogit` funzione RevoScaleR, con supporto aggiuntivo per la regolarizzazione L1 e L2. Supporta la classificazione multiclasse o binaria.

- Reti neurali: il `rxNeuralNet` funzione supporta la classificazione binaria, la classificazione multiclasse e regressione reti neurali. Personalizzazione e supporta reti complessa con accelerazione GPU, utilizzando una sola GPU.

- Rilevamento di anomalie.  Il `rxOneClassSvm` funzione si basa sul metodo SVM ma è ottimizzato per la classificazione binaria sbilanciata ai set di dati.

### <a name="transformation-functions"></a>Funzioni di trasformazione

MicrosoftML include numerose funzioni specializzate che sono utili per la trasformazione dei dati e le funzionalità di estrazione.

- Funzionalità di elaborazione di testo includono il `featurizeText` e `getSentiment` funzioni. È possibile contare n-grammi, rileva la lingua utilizzata o eseguire normalizzazione del testo. È anche possibile eseguire la pulizia delle operazioni, ad esempio la rimozione di parole non significative di testo comuni o generare funzioni hash o basate sul conteggio dal testo.

- Selezione delle caratteristiche e funzionalità come le funzioni di trasformazione, `selectFeatures` o `getSentiment`, analizzare i dati e creare le funzionalità più utili per la modellazione.

- Utilizzo di variabili di categoria con, ad esempio `categorical` o `categoricalHash`, che converte valori categorici in matrici indicizzate per migliorare le prestazioni.

- Funzioni specifiche per l'elaborazione di immagini e analitica, ad esempio `extractPixels` o `featurizeImage`, consentono ottenere più informazioni di immagini e tempi di elaborazione immagini.

Per altre informazioni, vedere [MicrosoftML functions](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (Funzioni MicrosoftML).

## <a name="how-to-use-microsoftml"></a>Come usare MicrosoftML

In questa sezione viene descritto come individuare e caricare il pacchetto nel codice R e Python.

+ Il pacchetto MicrosoftML per R è installato per impostazione predefinita con Microsoft R Server 9.1.0 e in SQL Server 2017.

    È inoltre disponibile per l'utilizzo con SQL Server 2016, se si aggiornano i componenti di R per l'istanza, tramite il programma di installazione di Microsoft R Server come descritto qui: [aggiornare un'istanza di SQL Server utilizzando l'associazione](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ Il **microsoftml** per Python è installato per impostazione predefinita con SQL Server 2017 del pacchetto 

   Per utilizzare questo pacchetto, è consigliabile che l'aggiornamento a Release Candidate 2 o versioni successive. Una versione precedente è stata rilasciata dalla versione RC1, ma la libreria ha subito notevoli revisione, incluse le modifiche ai nomi di funzioni. 

Tuttavia, per R e Python, il pacchetto non caricato per impostazione predefinita. di conseguenza, è necessario caricare in modo esplicito il pacchetto come parte del codice per utilizzare le relative funzioni.

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>Chiamata di funzioni MicrosoftML da R in SQL Server

Nel codice R, caricare il pacchetto MicrosoftML e chiamare le funzioni, come qualsiasi altro pacchetto.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**Note**

+ Il pacchetto MicrosoftML è completamente integrato con la pipeline di elaborazione dei dati fornita dal pacchetto RevoScaleR. Di conseguenza, è possibile utilizzare il pacchetto MicrosoftML in qualsiasi contesto di calcolo basate su Windows, tra cui un'istanza di SQL Server che dispone di estensioni di machine learning abilitate.

    Tuttavia, MicrosoftML richiede un riferimento a RevoScaleR e le relative funzioni per poter utilizzare remoto contesti di calcolo.

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>Chiamata di funzioni microsoftml da Python in SQL Server

Per chiamare le funzioni dal pacchetto, nel codice Python, importare il **microsoftml** un pacchetto e importare **revoscalepy** se è necessario utilizzare i contesti di calcolo remoto o un'origine dati o di connettività correlata oggetti. Quindi, fare riferimento le singole funzioni che è necessario.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Note**

+ In SQL Server 2017, **microsoftml** è un modulo Python35 compatibile. 

+ Le funzioni in **microsoftml** sono integrati con le origini dati e i contesti di calcolo sono supportate da **revoscalepy**. Pertanto, è possibile utilizzare il **microsoftml** pacchetto Python per creare e assegnare un punteggio da modelli in qualsiasi contesto di calcolo basate su Windows, tra cui un'istanza di SQL Server che dispone di estensioni di machine learning. abilitata.

    Tuttavia, **microsoftml** per Python richiede un riferimento a **revoscalepy** e contesti di calcolo delle funzioni per poter utilizzare Desktop remoto.

Per ulteriori informazioni su revoscalepy, vedere:

+ [Che cos'è revoscalepy](python/what-is-revoscalepy.md)

+ [libreria di funzioni revoscalepy](https://docs.microsoft.com/en-us/r-server/python-reference/revoscalepy/revoscalepy-package) 
