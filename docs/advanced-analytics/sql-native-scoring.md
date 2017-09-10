---
title: Punteggio nativa | Documenti Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e1cb06223e5274c1fa439eb9f7d82a005e93a47d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---

# <a name="native-scoring"></a>Assegnazione dei punteggi nativo

In questo argomento vengono descritte funzionalità SQL Server 2017 che forniscono punteggi in modelli di machine learning in tempo quasi reale.

+ Che cos'è native di classificazione e assegnazione dei punteggi in tempo reale
+ Funzionamento
+ Requisiti e piattaforme supportate

## <a name="what-is-native-scoring-and-how-is-it-different-from-realtime-scoring"></a>Che cos'è il punteggio nativo e come è diversa dall'assegnazione dei punteggi in tempo reale?

In SQL Server 2016, Microsoft ha creato un framework di estendibilità che consentono agli script R di essere eseguite da T-SQL. Questo framework supporta qualsiasi operazione effettuata in R, comprese tra funzioni semplici e formazione complesso modelli di machine learning. L'architettura dual-process che le coppie di R con SQL Server, tuttavia, significa che i processi R esterni devono essere richiamati per ogni chiamata, indipendentemente dalla complessità dell'operazione. Se si sta caricando un modello con training preliminare da una tabella e l'assegnazione dei punteggi rispetto ai dati già in SQL Server, l'overhead della chiamata al processo R esterno rappresenta una riduzione delle prestazioni non necessari.

_Assegnazione dei punteggi_ è un processo in due fasi: un modello con training preliminare viene caricato da una tabella, e nuovi dati di input, le righe tabulari o singole, viene passati al modello, che genera i nuovi valori (o _punteggi_). L'output potrebbe essere un valore di colonna singola che rappresenta una probabilità o più valori, inclusi altri complemento utile per la stima, errore o un intervallo di confidenza.

Quando l'assegnazione dei punteggi di numerose righe di dati, i nuovi valori vengono inseriti in genere in una tabella come parte della procedura di assegnazione dei punteggi.  Tuttavia, è inoltre possibile recuperare un singolo punteggio in tempo reale. Quando l'assegnazione dei punteggi di input successivo, il modello può essere memorizzati nella cache in modo che possa essere ricaricato in memoria rapida.

Per supportare il punteggio veloce, servizi di SQL Server Machine Learning (e i Server di Microsoft Machine Learning) forniscono librerie punteggio incorporate che funzionano in R o in T-SQL. Esistono diverse opzioni a seconda della versione.

**Assegnazione dei punteggi nativo**

+ La funzione di stima in Transact-SQL può essere utilizzata per _punteggio native_ da qualsiasi istanza di SQL Server 2017. Richiede solo la presenza di un modello già eseguito il training e salvato in una tabella o possono essere chiamati tramite T-SQL. È un tipo di assegnazione dei punteggi in tempo reale che Usa funzioni native di T-SQL. non è stata necessaria alcuna configurazione aggiuntiva.

   Il runtime di R non viene chiamato e non devono essere installati.

**Assegnazione dei punteggi in tempo reale**

+ **sp_rxPredict** è una stored procedure per in tempo reale di punteggio che può essere utilizzato per generare punteggi da qualsiasi tipo di modello supportati, senza chiamare il runtime di R.

  Questa opzione per utilizzare l'assegnazione dei punteggi in tempo reale è anche disponibile in SQL Server 2016, se si aggiornano i componenti di R usando il programma di installazione autonomo di Microsoft R Server. sp_rxPredict è supportato anche in SQL Server 2017 e potrebbe essere un'ottima scelta se si assegna un punteggio a un tipo di modello non è supportato dalla funzione di stima.

+ La funzione rxPredict utilizzabile per il punteggio rapido all'interno del codice R.

Per tutti i metodi di valutazione, è necessario utilizzare un modello che è stato eseguito il training utilizzando uno degli algoritmi supportati RevoScaleR o MicrosoftML.

Per un esempio di in tempo reale di punteggio in azione, vedere [End-to End prestito ChargeOff stima compilato utilizzando Azure HDInsight Spark cluster e il servizio SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>Funzionamento del punteggio nativo

Punteggio nativa Usa librerie native di C++ di Microsoft che è possibile leggere il modello da un particolare formato binario e generare punteggi. Poiché un modello può essere pubblicato e utilizzato per il punteggio senza necessità di chiamare l'interprete R, viene ridotto l'overhead delle interazioni di processo più. Negli scenari di produzione enterprise supporta ottenere migliori prestazioni di stima.

Per generare punteggi tramite questa raccolta, chiamare la funzione di assegnazione dei punteggi e passare l'input obbligatori seguenti:

+ Un modello compatibile. Vedere il [requisiti](#Requirements) sezione per informazioni dettagliate.
+ Dati di input, in genere definiti come una query SQL

La funzione restituisce stime per i dati di input, insieme a tutte le colonne di dati di origine che si desidera pass-through.

Per esempi di codice, oltre a istruzioni su come preparare i modelli nel formato binario richiesto, vedere l'articolo:

+ [Come eseguire l'assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md)

## <a name="requirements"></a>Requisiti

Piattaforme supportate sono i seguenti:

+ Servizi SQL Server 2017 Machine Learning (include Microsoft R Server 9.1.0)
    
    Punteggio nativa utilizzando PREDICT richiede SQL Server 2017.
    Funziona in qualsiasi versione di SQL Server 2017, tra cui Linux.

    È inoltre possibile eseguire in tempo reale di punteggio usando sp_rxPredict, che richiede l'abilitazione di CLR SQL.

+ SQL Server 2016

   E in tempo reale di punteggio usando sp_rxPredict è possibile con SQL Server 2016, può anche essere eseguito su Microsoft R Server. Questa opzione richiede SQLCLR deve essere abilitata e che si installa l'aggiornamento di Microsoft R Server.
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
  + [rxdForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Se è necessario utilizzare i modelli dalla MicrosoftML, utilizzare in tempo reale con sp_rxPredict di punteggio.

### <a name="restrictions"></a>Restrizioni

Non sono supportati i tipi di modello seguenti:

+ Modelli contenenti non supportati, altri tipi di trasformazioni di R
+ Modelli di utilizzo di `rxGlm` o `rxNaiveBayes` algoritmi RevoScaleR
+ Modelli PMML
+ Modelli creati utilizzando altre librerie di R da CRAN o altri repository
+ Modelli che contiene qualsiasi altro tipo di trasformazione di R

