---
title: Uso del pacchetto MicrosoftML con SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 51ffa33bef7ab880704c9c1391a69feb3e194202
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984563"
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>Uso del pacchetto MicrosoftML con SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Il [ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) pacchetto fornito con Microsoft R Server e SQL Server 2017 include più algoritmi di machine learning. Queste API sono state sviluppate da Microsoft per le applicazioni di apprendimento interne e sono state perfezionate nel corso degli anni per supportare prestazioni elevate sui big data, tramite l'elaborazione multicore e flusso rapido dei dati. MicrosoftML include anche numerose trasformazioni per l'elaborazione di immagini e testo.

In SQL Server 2017 CTP 2.0, è stato aggiunto il supporto per il linguaggio Python. Il **microsoftml** dal pacchetto per Python contiene funzioni equivalenti a quelli del pacchetto MicrosoftML per R. 

+ **MicrosoftML per R**

    Introduzione e pacchetto riferimento: [MicrosoftML: machine learning R algoritmi](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    Poiché R è tra maiuscole e minuscole, assicurarsi di fare riferimento il nome correttamente il caricamento del pacchetto.

+ **microsoftml per Python**

    Riferimento di introduzione e pacchetto: [microsoftml (libreria di funzioni per Python)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package). 

## <a name="whats-in-microsoftml"></a>Quali sono le novità MicrosoftML

MicrosoftML contiene un'ampia gamma di trasformazioni che sono state ottimizzate per le prestazioni e gli algoritmi di machine learning.

### <a name="machine-learning-algorithms"></a>Algoritmi di Machine learning

-  I modelli lineari: `rxFastLinear` è uno strumento di apprendimento lineare basato su stochastic dual ascent coordinate che può essere utilizzato per la regressione o classificazione binaria. Il modello supporta la regolarizzazione L1 ed L2.

- La decisione di modelli di foresta delle decisioni e struttura ad albero: `rxFastTree` è un algoritmo di albero delle decisioni con Boosting originariamente noto come FastRank, sviluppato per l'utso in Bing. È uno degli strumenti di apprendimento più noti e veloci. Supporta la regressione e la classificazione binaria.

  `rxFastForest` un modello di regressione logistica è basato sul metodo di foresta casuale. È simile alla funzione `rxLogit` in RevoScaleR, ma supporta la regolarizzazione L1 ed L2. Supporta la regressione e la classificazione binaria.

- La regressione logistica: `rxLogisticRegression` è simile a un modello di regressione logistica il `rxLogit` funzione in RevoScaleR con supporto aggiuntivo per la regolarizzazione L1 ed L2. Supporta la classificazione multiclasse o binaria.

- Le reti neurali: il `rxNeuralNet` supporta la funzione di classificazione binaria, classificazione multiclasse e regressione usando le reti neurali. Reti complesse personalizzabili e supporta l'accelerazione GPU, con una singola GPU.

- Rilevamento delle anomalie.  Il `rxOneClassSvm` funzione si basa sul metodo SVM, ma è ottimizzato per la classificazione binaria in set di dati bilanciati.

### <a name="transformation-functions"></a>Funzioni di trasformazione

MicrosoftML include numerose funzioni specializzate che sono utili per la trasformazione dei dati e le funzionalità di estrazione.

- Le funzionalità di elaborazione di testo includono il `featurizeText` e `getSentiment` funzioni. È possibile contare n-grammi, rilevare la lingua utilizzata o eseguire la normalizzazione di testo. È anche possibile eseguire testo comune operazioni, ad esempio la rimozione di parole non significative di pulizia o generare funzionalità con hash o sul conteggio dal testo.

- Selezione delle caratteristiche e funzionalità di funzioni di trasformazione, ad esempio `selectFeatures` o `getSentiment`, analizzare i dati e creare le funzionalità più utili per la modellazione.

- Utilizzo di variabili categoriche con, ad esempio `categorical` o `categoricalHash`, che converte i valori categorici in matrici indicizzate per migliorare le prestazioni.

- Funzioni specifiche per l'elaborazione di immagini e analitica, ad esempio `extractPixels` o `featurizeImage`, consentono di ottenere più informazioni delle immagini ed elaborare immagini più rapidamente.

Per altre informazioni, vedere [MicrosoftML functions](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (Funzioni MicrosoftML).

## <a name="how-to-use-microsoftml"></a>Come usare MicrosoftML

In questa sezione viene descritto come individuare e caricare il pacchetto nel codice R e Python.

+ Il pacchetto MicrosoftML per R è installato per impostazione predefinita con Microsoft R Server 9.1.0 e in SQL Server 2017.

    È anche disponibile per l'uso con SQL Server 2016, se si aggiornano i componenti di R per l'istanza, tramite il programma di installazione di Microsoft R Server come descritto qui: [aggiornare un'istanza di SQL Server utilizzando l'associazione](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ Il **microsoftml** dal pacchetto per Python è installato per impostazione predefinita con SQL Server 2017 

   Per usare questo pacchetto, è consigliabile eseguire l'aggiornamento a Release Candidate 2 o versioni successive. Una versione precedente è stata rilasciata con RC1, ma la libreria ha subito un notevole revisione, incluse le modifiche ai nomi di funzioni. 

Tuttavia, per R e Python, il pacchetto non è caricato per impostazione predefinita. di conseguenza, è necessario caricare in modo esplicito il pacchetto come parte del codice per usare le funzioni.

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>Chiamata di funzioni di MicrosoftML da R in SQL Server

Nel codice R, caricare il pacchetto MicrosoftML e chiamare le funzioni, come qualsiasi altro pacchetto.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**Note**

+ Il pacchetto MicrosoftML è completamente integrato con la pipeline di elaborazione dei dati fornita dal pacchetto RevoScaleR. Di conseguenza, è possibile usare il pacchetto MicrosoftML in qualsiasi contesto di calcolo basate su Windows, tra cui un'istanza di SQL Server che dispone di machine learning estensioni abilitate.

    Tuttavia, MicrosoftML richiede un riferimento a RevoScaleR e le relative funzioni per poter utilizzare Desktop remoto i contesti di calcolo.

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>Chiamata di funzioni di microsoftml da Python in SQL Server

Per chiamare le funzioni dal pacchetto, nel codice Python, importare il **microsoftml** del pacchetto e importare **revoscalepy** se è necessario usare contesti di calcolo remoti o origine dati o di connettività correlati oggetti. Quindi, fare riferimento a singole funzioni che è necessario.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Note**

+ In SQL Server 2017 **microsoftml** è un modulo Python35 compatibile. 

+ Le funzioni **microsoftml** sono integrati con le origini dati e contesti di calcolo supportati da **revoscalepy**. Di conseguenza, è possibile usare la **microsoftml** pacchetto Python per creare e assegnare un punteggio da modelli in qualsiasi contesto di calcolo basate su Windows, tra cui un'istanza di SQL Server che contiene le estensioni di machine learning. Abilitata.

    Tuttavia **microsoftml** for Python richiede un riferimento a **revoscalepy** e contesti di calcolo relative funzioni per poter utilizzare Desktop remoto.

Per ulteriori informazioni su revoscalepy, vedere:

+ [Che cos'è revoscalepy](python/what-is-revoscalepy.md)

+ [libreria revoscalepy (funzione)](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
