---
title: "Novità &#39; s novità di servizi di Machine Learning | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/08/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 36
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: fffe2ab906f659a2fb0e2996363ac8e7da000707
ms.openlocfilehash: 34a404511d72c5775f25dd182b018926b6d0d62e
ms.contentlocale: it-it
ms.lasthandoff: 09/18/2017

---
# <a name="whats-new-in-machine-learning-services-in-sql-server"></a>Novità di servizi di Machine Learning in SQL Server

In SQL Server 2016, Microsoft ha introdotto SQL Server R Services, una funzionalità che supporta l'analisi scientifica dei dati su larga scala, integrando il linguaggio R con il motore di database di SQL Server.

In SQL Server 2017, l'apprendimento diventa ancora più potente, con l'aggiunta del supporto per il linguaggio Python diffuso. Insieme al supporto per nuove lingue viene fornito un nuovo nome: **Machine Learning Services (In-Database)**.

Rilevare l'annuncio più recente qui! [Python in SQL Server 2017: avanzato nel database machine learning](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="whats-new-in-sql-server-2017"></a>Novità di SQL Server 2017

Server Microsoft di Machine Learning in SQL Server fornisce ora supporto completo per la compilazione e distribuzione di soluzioni di machine learning in R o Python. Di seguito vengono evidenziate di questa versione:

> [!IMPORTANT]
> 
> Servizi di Machine learning, incluso l'uso di R o Python, non sono attualmente supportati quando si esegue SQL Server in Linux o in database SQL di Azure. Cercare le modifiche in una versione successiva.
> 
> Punteggio nativa utilizzando la funzione di stima è attualmente supportato nell'edizione Linux.
 
### <a name="in-database-python-integration"></a>Integrazione di Python nel database

È possibile eseguire Python nelle stored procedure, o eseguire Python in remoto utilizzando il computer SQL Server come contesto di calcolo. Questa integrazione apre nuove strade per la vasta community di sviluppatori di Python e gli esperti di dati per utilizzare le funzionalità di SQL Server. 

Gli sviluppatori di SQL Server ottengono l'accesso alle librerie Python estese da dell'ecosistema di origine aperti, inclusi Framework famosi come scikit-informazioni su, Tensorflow Caffe e Theano/Keras. E assicurarsi di esplorare le innovazioni da Microsoft, ad esempio **revoscalepy** e **microsoftml**!

Python in esecuzione nel database non è quasi di machine learning, dalla modalità. Esistono numerose di altre applicazioni potenziali per l'integrazione di Python con SQL e utilizzando la potenza di ogni linguaggio per fornire potenti soluzioni più intelligenti.

+ **revoscalepy**

    Questa versione include la versione finale di **revoscalepy**, che fornisce gli equivalenti di Python degli algoritmi in RevoScaleR. È possibile creare modelli di Python per la regressione lineare e logistica, gli alberi delle decisioni, alberi con Boosting e foreste casuali, tutti gli eseguibili in parallelo e in grado di in esecuzione in contesti di calcolo remoto.

    Per ulteriori informazioni, vedere [novità revoscalepy](python/what-is-revoscalepy.md).

+ Contesti di calcolo remoti per Python

    Questa versione supporta l'utilizzo di più origini dati e i contesti di calcolo remoto. L'esperto di dati o lo sviluppatore può eseguire codice Python in un Server SQL remoto, per esplorare i dati e compilare modelli senza spostare i dati. L'uso di contesti di calcolo remoto richiede **revoscalepy**.

+ Supporto Python in Microsoft Machine Learning Server (Standalone)

    SQL Server 2017 include l'opzione per installare una versione autonoma di Microsoft machine learning piattaforma. Tramite i Server di Machine Learning, è possibile distribuire e scalare R o Python codice senza l'utilizzo di SQL Server.

    Per un esempio di codice Python in esecuzione nel Server di Microsoft Machine Learning, vedere [pubblica e utilizzare il codice Python](python/publish-consume-python-code.md).

### <a name="new-algorithms"></a>Nuovi algoritmi

Il **MicrosoftML** package di R e di Python contiene algoritmi avanzati di machine learning e la trasformazione dei dati che può essere scalato o eseguito in remoto i contesti di calcolo. Gli algoritmi sono logistic regression, gli alberi delle decisioni veloce e foreste delle decisioni, la regressione lineare e reti neurali profonde personalizzabile.

Il pacchetto MicrosoftML viene fornito con interfacce di R sia Python e si basa su Microsoft Machine Learning Server versione 9.2.0.

Per ulteriori informazioni, vedere [Introduzione a MicrosoftML](using-the-microsoftml-package.md) e [microsoftml per Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="operationalization"></a>Rendere operativo

Questa versione contiene più opzioni e funzionalità che consentono di implementare e distribuire l'attività di machine learning:

+ Distribuire e integrare soluzioni di Python macchina, utilizzando T-SQL

    L'integrazione di Python con T-SQL significa che è possibile chiamare qualsiasi codice Python usando `sp_execute_external_script`. Questa infrastruttura sicura consente una distribuzione aziendale di modelli di Python e script che può essere chiamato da un'applicazione utilizzando una stored procedure semplice. Aggiuntivi relativi alle prestazioni è streaming i dati contenuti in SQL per i processi di Python e parallelizzazione anello MPI.

+ **mrsdeploy** per Python

    Il **mrsdeploy** dal pacchetto per Microsoft R Server ora supporta la distribuzione di modelli di Python e gli script come servizi web ed è disponibile come un'opzione in Machine Learning Server (Standalone). Per un esempio di come funziona, vedere [pubblica e utilizzare il codice Python](python/publish-consume-python-code.md).

+ Prestazioni

    Microsoft ha inserito i limiti delle prestazioni per il punteggio. Con l'assegnazione dei punteggi nel database, elaborazione un milione di righe al secondo tramite modelli R. In questa versione, le nuove funzionalità per **assegnazione dei punteggi in tempo reale** e **punteggio native** supportare prestazioni migliori in una singola riga e dell'assegnazione punteggio batch. 

### <a name="realtime-scoring-and-native-scoring"></a>Assegnazione dei punteggi in tempo reale e i punteggi nativo

Assegnazione dei punteggi in tempo reale si basa su librerie di C++ native per leggere un modello archiviato in un formato binario ottimizzato e quindi generare stime senza necessità di chiamare il runtime di R. Ciò rende le operazioni di assegnazione dei punteggi molto più veloce.

Inoltre, questa versione di SQL Server 2017 include una funzione Transact-SQL nativa per il punteggio veloce che può essere eseguita in qualsiasi edizione di SQL Server, anche in Linux. La funzione non richiede alcuna installazione di R o configurazione aggiuntiva. Ciò significa che è possibile eseguire il training di un modello in un' posizione, salvarlo in SQL Server e quindi eseguire l'assegnazione dei punteggi senza mai chiamare R. Questa funzionalità è definita come _punteggio nativo_.

  - Punteggio nativa è disponibile solo in SQL Server 2017. Usa una funzione di T-SQL che possono essere eseguiti in qualsiasi edizione di SQL Server, tra cui Linux.
 - Assegnazione dei punteggi in tempo reale è supportata in SQL Server 2017 e nel Server di Microsoft Machine Learning. È possibile eseguire una stored procedure o eseguire in tempo reale dal codice R di punteggio.
 - Assegnazione dei punteggi in tempo reale è disponibile anche per SQL Server 2016, se l'istanza viene aggiornato alla versione più recente di Microsoft R Server.

Per altre informazioni, vedere gli articoli seguenti:

 + [Assegnazione dei punteggi in tempo reale](real-time-scoring.md)
 + [Punteggio nativo](sql-native-scoring.md)
 + [Come eseguire l'assegnazione dei punteggi in tempo reale o punteggio nativo](r/how-to-do-realtime-scoring.md)

### <a name="upgrade-your-machine-learning-experience-and-get-pre-trained-models"></a>Aggiornamento del computer esperienza di apprendimento e ottenere i modelli con training preliminare

Se è installata una versione precedente di SQL Server 2016 R Services, è possibile aggiornare la versione più recente ora passando il server per utilizzare i criteri del ciclo di vita di Software più recenti. In questo modo, è possibile usufruire di un ciclo di rilascio più veloce per R e l'aggiornamento automatico di tutti i componenti di R. Per altre informazioni, vedere [Microsoft R Server 9.0.1](https://docs.microsoft.com/r-server/whats-new-in-r-server).

Il programma di installazione offre inoltre la possibilità di installare una raccolta di modelli con training preliminare in formato binario. Questi modelli supportano l'apprendimento negli scenari, ad esempio riconoscimento di immagini, in cui potrebbe essere difficile ai clienti di trovare grandi set di dati per il training di un modello. Dopo aver installato uno dei modelli con training preliminare, è possibile utilizzare per la stima sui dati senza i tempi e costi coinvolti nel training di tale modello grande e complessi.

Per ulteriori informazioni, vedere [installare modelli con training preliminare in SQL Server](r/install-pretrained-models-sql-server.md)

### <a name="package-management"></a>Gestione dei pacchetti

Questa versione include numerosi miglioramenti introdotti nella gestione dei pacchetti per SQL Server. tra cui:

- ruoli predefiniti del database per gestire e controllare le autorizzazioni all'amministratore di database
- L'istruzione CREATE libreria esterna in T-SQL, per gestire i pacchetti senza dover sapere R gli amministratori di database
- Un set completo di funzioni R per l'installazione, rimuovere o elencare i pacchetti di proprietà degli utenti

Per ulteriori informazioni, vedere [pacchetto gestione](r/r-package-management-for-sql-server-r-services.md).

### <a name="get-started"></a>Introduzione

+ [Impostare Python in servizi di SQL Server Machine Learning](../advanced-analytics/python/setup-python-machine-learning-services.md)

+ [Impostare R in servizi di SQL Server Machine Learning](r/set-up-sql-server-r-services-in-database.md)

+ [Esempi ed esercitazioni di machine learning](tutorials/machine-learning-services-tutorials.md)
