---
title: Assegnazione dei punteggi in tempo reale in SQL Server machine Learning Services | Microsoft Docs
description: Generare stime usando sp_rxPredict, valutazione degli input dta rispetto a un modello con training preliminare scritte in R in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d5a3d0318f925918ef98ae18744e4287d6b81108
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2018
ms.locfileid: "40393334"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>In tempo reale di assegnazione dei punteggi con sp_rxPredict in SQL Server machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo illustra come assegnazione dei punteggi in tempo quasi reale funziona per i dati relazionali di SQL Server, uso di machine learning i modelli scritti in R. 

> [!Note]
> Punteggio nativo è un'implementazione speciale di assegnazione dei punteggi in tempo reale che viene utilizzata la funzione di stima di T-SQL nativa per il punteggio molto veloce. Per altre informazioni e disponibilità, vedere [assegnazione dei punteggi nativa](sql-native-scoring.md).

## <a name="how-real-time-scoring-works"></a>Funzionamento di assegnazione dei punteggi in tempo reale come

Assegnazione dei punteggi in tempo reale è supportato in SQL Server 2017 e SQL Server 2016, sui tipi di modello specifico basati, ad esempio le funzioni RevoScaleR o MicrosoftML [(RevoScaleR) rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) o [rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Usa le librerie C++ native per generare punteggi, in base all'input fornito a un modello di machine learning archiviato in un particolare formato binario.

Poiché un modello con training può essere usato per la valutazione senza dover chiamare un runtime di linguaggio esterno, viene ridotto l'overhead di più processi. Ciò supporta ottenere migliori prestazioni di stima per gli scenari di assegnazione dei punteggi di produzione. Poiché i dati non oltrepassino mai SQL Server, i risultati possono essere generati e inseriti in una nuova tabella senza conversione dei dati tra R e SQL.

Assegnazione dei punteggi in tempo reale è un processo in più passaggi:

1. È necessario abilitare le stored procedure che esegue l'assegnazione dei punteggi in base al database.
2. Caricare il modello con training preliminare in formato binario.
3. Nuovi dati di input, sia tabulare o per singole righe, vengono fornite come input al modello.
4. Per generare punteggi, chiamare il sp_rxPredict stored procedure.

## <a name="get-started"></a>Introduzione

Per istruzioni ed esempi di codice, vedere [come eseguire l'assegnazione dei punteggi nativa o assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md).

Per un esempio di come rxPredict può essere utilizzato per l'assegnazione dei punteggi, vedere [End End prestito prestiti stima compilati tramite Azure HDInsight cluster Spark e di SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Se si lavora esclusivamente nel codice R, è anche possibile usare la [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) funzione per la valutazione rapida.

## <a name="requirements"></a>Requisiti

Assegnazione dei punteggi in tempo reale è supportato su queste piattaforme:

+ SQL Server 2017 Machine Learning Services
+ SQL Server R Services 2016, con un aggiornamento dei componenti di R a 9.1.0 o versioni successive

In SQL Server, è necessario abilitare la funzionalità di assegnazione dei punteggi in tempo reale in anticipo aggiungere le librerie basate su CLR per SQL Server.

Per informazioni sull'assegnazione dei punteggi in tempo reale in un ambiente distribuito basato su Microsoft R Server, vedere la [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) funzione di disponibile nel [pacchetto mrsDeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), che supporta pubblicazione di modelli per il punteggio in tempo reale come nuovo un servizio web in esecuzione nel Server di R.

### <a name="restrictions"></a>Restrictions

+ Il modello deve essere sottoposto a training in anticipo usando uno degli **rx** algoritmi. Per informazioni dettagliate, vedere [supportati gli algoritmi](#bkmk_rt_supported_algos). Assegnazione dei punteggi in tempo reale con `sp_rxPredict` supporta gli algoritmi di RevoScaleR sia MicrosoftML.

+ Il modello deve essere salvato utilizzando le nuove funzioni di serializzazione: [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) per R, e [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) per Python. Queste funzioni di serializzazione sono state ottimizzate per supportare l'assegnazione dei punteggi veloce.

+ Assegnazione dei punteggi in tempo reale non utilizza un interprete; Pertanto, qualsiasi funzionalità che potrebbero richiedere un interprete non è supportata durante il passaggio di assegnazione dei punteggi.  Tali proprietà possono includere:

  + I modelli usando la `rxGlm` o `rxNaiveBayes` algoritmi non sono attualmente supportati

  + I modelli di RevoScaleR che usano una funzione di trasformazione R o una formula che contiene una trasformazione, ad esempio <code>A ~ log(B)</code> non sono supportati nell'assegnazione dei punteggi in tempo reale. Per usare un modello di questo tipo, è consigliabile eseguire la trasformazione di per i dati di input prima di passarli all'assegnazione dei punteggi in tempo reale.

+ Assegnazione dei punteggi in tempo reale è attualmente ottimizzato per le stime rapide in un set di dati più piccolo, compreso tra alcune righe e centinaia di migliaia di righe. In grandi set di dati, tramite [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) potrebbe risultare più veloce.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-real-time-scoring"></a><a name="bkmk_rt_supported_algos">Algoritmi che supportano l'assegnazione dei punteggi in tempo reale

+ Modelli di RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Modelli contrassegnati con \* supportano anche l'assegnazione dei punteggi nativa con la funzione PREDICT.

+ Modelli di MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Trasformazioni fornite da MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Tipi di modello non supportato

Assegnazione dei punteggi in tempo reale non è supportata per le trasformazioni di R diverso da quelli elencati in modo esplicito nella sezione precedente. 

Per gli sviluppatori abituati a lavorare con RevoScaleR e altre librerie specifiche di Microsoft R, includono funzioni non supportate `rxGlm` o `rxNaiveBayes` algoritmi in RevoScaleR, modelli di linguaggio PMML e altri modelli creati con altre librerie di R da CRAN o altri repository.

### <a name="known-issues"></a>Problemi noti

+ `sp_rxPredict` Restituisce un messaggio non accurato quando un valore NULL viene passato come il modello: "System.Data.SqlTypes.SqlNullValueException:Data in Null".

## <a name="next-steps"></a>Passaggi successivi

[Come eseguire questa operazione di assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md)
