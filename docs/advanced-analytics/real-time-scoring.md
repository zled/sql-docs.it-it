---
title: Assegnazione dei punteggi in tempo reale | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: eda95bf4cd16c5c38277e6d139c224f225c9b10a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="realtime-scoring"></a>Assegnazione dei punteggi in tempo reale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo argomento descrive una funzionalità disponibile in SQL Server 2016 e SQL Server 2017 che supporta l'assegnazione dei punteggi su modelli di machine learning in tempo quasi reale.

> [!TIP]
> Punteggio nativo è un'implementazione speciale di in tempo reale di assegnazione dei punteggi che utilizza la funzione di stima di T-SQL nativa per il punteggio molto rapido ed è disponibile solo in SQL Server 2017. Per ulteriori informazioni, vedere [punteggio nativo](sql-native-scoring.md).

## <a name="how-realtime-scoring-works"></a>Funzionamento di assegnazione dei punteggi in tempo reale

Assegnazione dei punteggi in tempo reale è supportata in SQL Server 2017 sia SQL Server 2016, sui tipi di modello specifico creati utilizzando gli algoritmi RevoScaleR o MicrosoftML supportati. Usa librerie native di C++ per generare punteggi, in base all'input fornito a un modello di machine learning archiviato in un formato binario speciale.

Poiché un modello con training può essere utilizzato per il punteggio senza necessità di chiamare un runtime del linguaggio esterno, viene ridotto l'overhead di più processi. Supporta ottenere migliori prestazioni di stima per il punteggio di scenari di produzione. Poiché SQL Server non oltrepassa mai i dati, i risultati possono essere generati e inseriti in una nuova tabella senza conversione dei dati tra R e SQL.

Assegnazione dei punteggi in tempo reale è un processo costituito da più passaggi:

1. È necessario abilitare la stored procedure che esegue l'assegnazione dei punteggi in base al database.
2. Caricare il modello con training preliminare in formato binario.
3. Fornire nuovi dati di input, le righe tabulari o singole, come input per il modello.
4. Per generare punteggi, chiamare il sp_rxPredict stored procedure.

## <a name="get-started"></a>Introduzione

Per istruzioni ed esempi di codice, vedere [come eseguire punteggio native o l'assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md).

Per un esempio di come è possibile rxPredict utilizzati per il punteggio, vedere [End-to End prestito ChargeOff stima compilato utilizzando Azure HDInsight Spark cluster e il servizio SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Se si utilizza esclusivamente nel codice R, è inoltre possibile utilizzare il [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) funzione per il punteggio veloce.

## <a name="requirements"></a>Requisiti

Assegnazione dei punteggi in tempo reale è supportato su queste piattaforme:

+ SQL Server 2017 Machine Learning Services
+ SQL Server R Services 2016, con un aggiornamento dell'istanza di R Services da Microsoft R Server 9.1.0 o versione successiva
+ Machine Learning Server (Standalone)

In SQL Server, è necessario abilitare funzionalità di punteggio in anticipo in tempo reale. Questo avviene perché la funzionalità richiede l'installazione delle librerie basato su CLR in SQL Server.

Per informazioni in tempo reale di punteggio in un ambiente distribuito in base a Microsoft R Server, consultare il [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) disponibile in funzione la [mrsDeploy pacchetto](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), che supporta pubblicazione di modelli per in tempo reale di punteggio come nuovo un servizio web in esecuzione nel Server di R.

### <a name="restrictions"></a>Restrizioni

+ Training del modello deve essere eseguito in precedenza tramite uno dei supportati **rx** algoritmi. Per informazioni dettagliate, vedere [supportati gli algoritmi](#bkmk_rt_supported_algos). In tempo reale di punteggio con `sp_rxPredict` supporta gli algoritmi RevoScaleR sia MicrosoftML.

+ È necessario salvare il modello utilizzando le nuove funzioni di serializzazione: [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) per R, e [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) per Python. Queste funzioni di serializzazione sono state ottimizzate per il supporto di classificazione rapido.

+ Assegnazione dei punteggi in tempo reale non utilizza un interprete interprete; Pertanto, qualsiasi funzionalità che potrebbero richiedere un interprete non è supportata durante il passaggio di assegnazione dei punteggi.  Ad esempio:

  + Modelli di utilizzo di `rxGlm` o `rxNaiveBayes` algoritmi non sono attualmente supportati

  + I modelli che utilizzano una funzione di trasformazione di R, o una formula che contiene una trasformazione, ad esempio RevoScaleR <code>A ~ log(B)</code> non sono supportate nell'assegnazione dei punteggi in tempo reale. Per utilizzare un modello di questo tipo, è consigliabile eseguire la trasformazione di dati di input prima di passare i dati per l'assegnazione dei punteggi in tempo reale.

+ Assegnazione dei punteggi in tempo reale attualmente è ottimizzato per le stime veloce in un set di dati più piccolo, compreso tra alcune righe e centinaia di migliaia di righe. Nel set di dati molto grandi, tramite [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) potrebbero essere più veloci.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-realtime-scoring"></a><a name="bkmk_rt_supported_algos">Algoritmi che supportano l'assegnazione dei punteggi in tempo reale

+ Modelli RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  I modelli è contrassegnato con \* supportano inoltre l'assegnazione dei punteggi native con la funzione di stima.

+ Modelli MicrosoftML

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

Non sono supportati i tipi di modello seguenti:

+ Modelli contenenti non supportati, altri tipi di trasformazioni di R
+ Modelli di utilizzo di `rxGlm` o `rxNaiveBayes` algoritmi RevoScaleR
+ Modelli PMML
+ Modelli creati utilizzando altre librerie di R da CRAN o altri repository
+ Modelli che contiene qualsiasi altro tipo di trasformazione R diversi da quelli elencati di seguito

### <a name="known-issues"></a>Problemi noti

+ `sp_rxPredict` Restituisce un messaggio non accurato quando un valore NULL viene passato come il modello: "System.Data.SqlTypes.SqlNullValueException:Data in Null".

## <a name="next-steps"></a>Passaggi successivi

[Come eseguire l'operazione di assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md)
