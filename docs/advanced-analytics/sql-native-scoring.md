---
title: Punteggio nativa | Documenti Microsoft
ms.custom: 
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: fe571e3e432d6445c76133c4c2a9c56f2f67eff0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="native-scoring"></a>Assegnazione dei punteggi nativo

In questo argomento vengono descritte funzionalità SQL Server 2017 che forniscono punteggi in modelli di machine learning in tempo quasi reale.

+ Che cos'è native di classificazione e assegnazione dei punteggi in tempo reale
+ Funzionamento
+ Requisiti e piattaforme supportate

## <a name="what-is-native-scoring-and-how-is-it-different-from-realtime-scoring"></a>Che cos'è il punteggio nativo e come è diversa dall'assegnazione dei punteggi in tempo reale?

In SQL Server 2016, Microsoft ha creato un framework di estendibilità che consentono agli script R di essere eseguite da T-SQL. Questo framework supporta qualsiasi operazione effettuata in R, comprese tra funzioni semplici e formazione complesso modelli di machine learning. Tuttavia, l'architettura dual-process richiede richiamare un processo esterno R per ogni chiamata, indipendentemente dalla complessità dell'operazione. Se si sta caricando un modello con training preliminare da una tabella e l'assegnazione dei punteggi rispetto ai dati già in SQL Server, l'overhead della chiamata al processo R esterno rappresenta una riduzione delle prestazioni non necessari.

_Assegnazione dei punteggi_ è un processo in due passaggi. È possibile specificare un modello con training preliminare per il caricamento da una tabella. In secondo luogo, nuovo passaggio di dati rispetto alla funzione, per generare i valori di stima di input (o _punteggi_). L'input può essere righe tabulari o singole. È possibile scegliere di restituire un valore di colonna singola che rappresenta una probabilità o si potrebbero restituire valori diversi, ad esempio un intervallo di confidenza, errore o altri complemento utile per la stima.

Quando l'input include molte righe di dati, è in genere più veloce per inserire i valori di stima in una tabella come parte del processo di assegnazione dei punteggi.  Generazione di un singolo punteggio è più comune di comunicazione in uno scenario in cui ottenere i valori di input da una richiesta di modulo o un utente e restituire il punteggio a un'applicazione client. Per migliorare le prestazioni durante la generazione di punteggi successivi, SQL Server potrebbe memorizzare nella cache del modello in modo che possa essere ricaricato in memoria.

Per supportare il punteggio veloce, servizi di SQL Server Machine Learning (e i Server di Microsoft Machine Learning) forniscono librerie punteggio incorporate che funzionano in R o in T-SQL. Esistono diverse opzioni a seconda della versione.

**Punteggio nativo**

+ La funzione di stima in Transact-SQL supporta _punteggio native_ in qualsiasi istanza di SQL Server 2017. Richiede solo che si dispone di un modello già eseguito il training, che è possibile chiamare utilizzando T-SQL. Punteggio nativa utilizzando T-SQL è i seguenti vantaggi:

    + Non è richiesta alcuna configurazione aggiuntiva.
    + Il runtime di R non viene chiamato. Non è necessario per installare R.

**Assegnazione dei punteggi in tempo reale**

+ **sp_rxPredict** è una stored procedure per in tempo reale di punteggio che può essere utilizzato per generare punteggi da qualsiasi tipo di modello supportati, senza chiamare il runtime di R.

  Questa stored procedure è anche disponibile in SQL Server 2016, se si aggiornano i componenti di R usando il programma di installazione autonomo di Microsoft R Server. sp_rxPredict è supportato anche in SQL Server 2017. Pertanto, è possibile utilizzare questa funzione per la generazione di punteggi con un tipo di modello non è supportato dalla funzione di stima.

+ La funzione rxPredict utilizzabile per il punteggio rapido all'interno del codice R.

Per tutti i metodi di valutazione, è necessario utilizzare un modello che è stato eseguito il training utilizzando uno degli algoritmi supportati RevoScaleR o MicrosoftML.

Per un esempio di in tempo reale di punteggio in azione, vedere [End-to End prestito ChargeOff stima compilato utilizzando Azure HDInsight Spark cluster e il servizio SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>Funzionamento del punteggio nativo

Punteggio nativa Usa librerie native di C++ di Microsoft che è possibile leggere il modello da un particolare formato binario e generare punteggi. Poiché un modello può essere pubblicato e utilizzato per il punteggio senza necessità di chiamare l'interprete R, viene ridotto l'overhead delle interazioni di processo più. Di conseguenza, punteggio native supporta ottenere migliori prestazioni di stima in scenari di produzione dell'organizzazione.

Per generare punteggi tramite questa raccolta, chiamare la funzione di assegnazione dei punteggi e passare l'input obbligatori seguenti:

+ Un modello compatibile. Vedere il [requisiti](#Requirements) sezione per informazioni dettagliate.
+ Dati di input, in genere definiti come una query SQL

La funzione restituisce stime per i dati di input, insieme a tutte le colonne di dati di origine che si desidera pass-through.

Per esempi di codice, oltre a istruzioni su come preparare i modelli nel formato binario richiesto, vedere l'articolo:

+ [Come eseguire l'assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md)

Per una soluzione completa che include il punteggio nativo, vedere questi esempi dal team di sviluppo di SQL Server:

+ Distribuire lo script di ML: [utilizzando un modello di Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Distribuire lo script di ML: [utilizzando un modello R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)

## <a name="requirements"></a>Requisiti

Piattaforme supportate sono i seguenti:

+ Servizi SQL Server 2017 Machine Learning (include Microsoft R Server 9.1.0)
    
    Punteggio nativa utilizzando PREDICT richiede SQL Server 2017.
    Funziona in qualsiasi versione di SQL Server 2017, tra cui Linux.

    È inoltre possibile eseguire in tempo reale di punteggio usando sp_rxPredict. Per utilizzare questa stored procedure, è necessario abilitare [integrazione CLR di SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ SQL Server 2016

   In tempo reale di punteggio usando sp_rxPredict è possibile con SQL Server 2016 e può anche essere eseguito su Microsoft R Server. Questa opzione richiede SQLCLR deve essere abilitata e che si installa l'aggiornamento di Microsoft R Server.
   Per ulteriori informazioni, vedere [assegnazione dei punteggi in tempo reale](Real-time-scoring.md)

### <a name="model-preparation"></a>Preparazione del modello

+ Training del modello deve essere eseguito in precedenza tramite uno dei supportati **rx** algoritmi. Per informazioni dettagliate, vedere [supportati gli algoritmi](#bkmk_native_supported_algos).
+ È necessario salvare il modello utilizzando la nuova funzione di serializzazione disponibile in Microsoft R Server 9.1.0. La funzione di serializzazione è ottimizzata per supportare il punteggio veloce.

### <a name="bkmk_native_supported_algos"></a>Algoritmi che supportano il punteggio nativo

+ Modelli RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Se è necessario utilizzare i modelli dalla MicrosoftML, utilizzare in tempo reale con sp_rxPredict di punteggio.

### <a name="restrictions"></a>Restrizioni

Non sono supportati i tipi di modello seguenti:

+ Modelli contenenti non supportati, altri tipi di trasformazioni di R
+ Modelli di utilizzo di `rxGlm` o `rxNaiveBayes` algoritmi RevoScaleR
+ Modelli PMML
+ Modelli creati utilizzando altre librerie di R da CRAN o altri repository
+ Modelli che contiene tutte le altre trasformazioni di R
