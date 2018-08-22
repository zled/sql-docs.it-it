---
title: Assegnazione dei punteggi nativa in SQL Server machine Learning Services | Microsoft Docs
description: Generare stime utilizzando la funzione di stima T-SQL, valutazione degli input dta rispetto a un modello con training preliminare scritte in R o Python in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf8f9a6362b72efddccbf5c2b0e54096c6e86aa7
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2018
ms.locfileid: "40392800"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Punteggio nativo usando la funzione di stima T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Dopo aver creato un modello con training preliminare, è possibile passare nuovi dati di input alla funzione per generare i valori di stima oppure *punteggi*. In SQL Server 2017 Windows o Linux o in Database SQL di Azure, è possibile usare la funzione PREDICT in Transact-SQL per supportare l'assegnazione dei punteggi nativa. Richiede solo la presenza di un modello già eseguito il training, che è possibile chiamare con T-SQL. 

+ What ' s nativa di assegnazione dei punteggi e l'assegnazione dei punteggi in tempo reale
+ Funzionamento
+ Requisiti e piattaforme supportate

## <a name="what-is-native-scoring-and-how-is-it-different-from-real-time-scoring"></a>Qual è l'assegnazione dei punteggi nativa e cosa è diverso dall'assegnazione dei punteggi in tempo reale?

In SQL Server 2016, Microsoft ha creato un framework di estensibilità che gli script R possono essere eseguite da T-SQL. Il framework supporta qualsiasi operazione che è possibile eseguire in R, compreso tra le funzioni semplici e corsi di formazione complessi modelli di machine learning. Tuttavia, l'architettura dual-process richiede richiamo di un processo R esterno per ogni chiamata, indipendentemente dalla complessità dell'operazione. Se si sta caricando un modello con training preliminare da una tabella e di assegnazione dei punteggi contrastarla sui dati già in SQL Server, l'overhead della chiamata al processo R esterno rappresenta un costo per le prestazioni non necessari.

_Assegnazione dei punteggi_ è un processo in due passaggi. È possibile specificare un modello con training preliminare per caricare da una tabella. In secondo luogo, passare di nuovo i dati alla funzione, per generare i valori di stima di input (o _punteggi_). L'input può essere sia tabulare o per singole righe. È possibile scegliere di generare un valore di colonna singola che rappresenta una probabilità o si potrebbero restituire valori diversi, ad esempio un intervallo di confidenza, errore o di altri complemento utile per la stima.

Quando l'input include molte righe di dati, è in genere più veloce per inserire i valori di stima in una tabella come parte del processo di assegnazione dei punteggi.  La generazione di un singolo punteggio è più adatta in uno scenario in cui ottenere i valori di input da una richiesta di form o utente e restituire il punteggio a un'applicazione client. Per migliorare le prestazioni durante la generazione di punteggi successivi, SQL Server potrebbe memorizzare nella cache il modello in modo che possa essere ricaricato in memoria.

Per supportare l'assegnazione dei punteggi veloce, SQL Server Machine Learning Services (e Microsoft Machine Learning Server) offrono librerie di assegnazione dei punteggi predefinite che funzionano in R o in T-SQL. Sono disponibili opzioni diverse a seconda di quale versione è necessario.

**Punteggio nativo**

+ La funzione PREDICT in Transact-SQL supporta _assegnazione dei punteggi nativa_ in qualsiasi istanza di SQL Server 2017. Richiede solo la presenza di un modello già eseguito il training, che è possibile chiamare con T-SQL. Punteggio nativo usando T-SQL presenta i seguenti vantaggi:

    + Non è richiesta alcuna configurazione aggiuntiva.
    + Il runtime di R non viene chiamato. Non è necessario installare R.

**Punteggio in tempo reale**

+ **sp_rxPredict** è una stored procedure per il punteggio in tempo reale che può essere usato per genera i punteggi da qualsiasi tipo di modello supportati, senza chiamare il runtime di R.

  Questa stored procedure è anche disponibile in SQL Server 2016, se si aggiornano i componenti di R usando il programma di installazione autonomo di Microsoft R Server. sp_rxPredict è supportata anche in SQL Server 2017. Pertanto, è possibile utilizzare questa funzione durante la generazione di punteggi con un tipo di modello non è supportato dalla funzione PREDICT.

+ La funzione rxPredict utilizzabile per la valutazione rapida all'interno del codice R.

Per tutti i metodi di valutazione, è necessario usare un modello di cui è stato eseguito il training usando uno degli algoritmi supportati RevoScaleR o MicrosoftML.

Per un esempio di assegnazione dei punteggi in tempo reale in azione, vedere [End End prestito prestiti stima compilati tramite Azure HDInsight cluster Spark e di SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>Funzionamento del punteggio nativo

Assegnazione dei punteggi nativa Usa le librerie native di C++ da Microsoft che possono leggere il modello da un particolare formato binario e generare i punteggi. Poiché un modello può essere pubblicato e usato per la valutazione senza la necessità di chiamare l'interprete R, viene ridotto l'overhead di più le interazioni di processo. Di conseguenza, assegnazione dei punteggi nativa supporta ottenere migliori prestazioni stima negli scenari di produzione dell'organizzazione.

Per generare punteggi tramite questa raccolta, chiamare la funzione di assegnazione dei punteggi e passare gli input necessari seguenti:

+ Un modello compatibile. Vedere le [requisiti](#Requirements) sezione per informazioni dettagliate.
+ Dati di input, in genere definiti come una query SQL

La funzione restituisce stime per i dati di input, insieme a tutte le colonne di dati di origine che si desidera pass-through.

Per esempi di codice, oltre a istruzioni su come preparare i modelli nel formato binario richiesto, vedere questo articolo:

+ [Come eseguire l'assegnazione dei punteggi in tempo reale](r/how-to-do-realtime-scoring.md)

Per una soluzione completa che include l'assegnazione dei punteggi nativa, vedere questi esempi dal team di sviluppo di SQL Server:

+ Distribuire lo script di Machine Learning: [usando un modello Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Distribuire lo script di Machine Learning: [usando un modello R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)

## <a name="requirements"></a>Requisiti

Piattaforme supportate sono i seguenti:

+ SQL Server 2017 Machine Learning Services (che include Microsoft R Server 9.1.0)
    
    Punteggio nativo usando PREDICT richiede SQL Server 2017.
    Funziona in qualsiasi versione di SQL Server 2017, tra cui Linux.

    È anche possibile eseguire in tempo reale di assegnazione dei punteggi usando sp_rxPredict. Utilizzare questa stored procedure richiede l'abilitazione [integrazione CLR di SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ SQL Server 2016

   In tempo reale di assegnazione del punteggio utilizzando sp_rxPredict è possibile eseguire con SQL Server 2016 e può essere eseguita anche in Microsoft R Server. Questa opzione richiede SQLCLR da abilitare e installare l'aggiornamento di Microsoft R Server.
   Per altre informazioni, vedere [assegnazione dei punteggi in tempo reale](Real-time-scoring.md)

### <a name="model-preparation"></a>Preparazione del modello

+ Il modello deve essere sottoposto a training in anticipo usando uno degli **rx** algoritmi. Per informazioni dettagliate, vedere [supportati gli algoritmi](#bkmk_native_supported_algos).
+ Il modello deve essere salvato con la nuova funzione di serializzazione fornita in Microsoft R Server 9.1.0. La funzione di serializzazione è ottimizzata per supportare l'assegnazione dei punteggi veloce.

### <a name="bkmk_native_supported_algos"></a> Algoritmi che supportano l'assegnazione dei punteggi nativa

+ Modelli di RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Se è necessario usare i modelli da MicrosoftML, usare l'assegnazione dei punteggi in tempo reale con sp_rxPredict.

### <a name="restrictions"></a>Restrictions

Non sono supportati i tipi di modello seguente:

+ Modelli contenenti non supportati, gli altri tipi di trasformazioni di R
+ I modelli usando la `rxGlm` o `rxNaiveBayes` algoritmi in RevoScaleR
+ Modelli di linguaggio PMML
+ Modelli creati con altre librerie di R da CRAN o ad altri repository
+ Modelli che contiene tutte le altre trasformazioni di R

## <a name="see-also"></a>Vedere anche

[In tempo reale di assegnazione dei punteggi in SQL Server machine Learning Services ](real-time-scoring.md)