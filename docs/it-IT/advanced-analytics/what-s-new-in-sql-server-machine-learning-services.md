---
title: Cosa&#39;novità di servizi di SQL Server Machine Learning s | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 405e4636525898268c54f1a3d603c9e5da3dc14d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Novità di servizi di SQL Server Machine Learning 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Funzionalità di Machine learning vengono aggiunti a SQL Server in ogni versione, per continuare a espandere, estendere e approfondire l'integrazione tra la piattaforma di dati e di analisi scientifica dei dati, analitica e si desidera implementare sui dati di apprendimento supervisionato. 

## <a name="new-in-sql-server-2017"></a>Novità di SQL Server 2017

Questa versione aggiunto supporto Python e algoritmi di apprendimento automatico leader del settore. Rinominato in modo da riflettere il nuovo ambito, SQL Server 2017 contrassegnato l'introduzione del **SQL Server Machine Learning Services (In-Database)**, con supporto del linguaggio per Python e R. 

Questa versione è stata introdotta anche **Machine Learning Server (Standalone) di SQL Server**completamente indipendente di SQL Server, per carichi di lavoro R e Python che si desidera eseguire in un sistema dedicato. Con il server autonomo, è possibile distribuire e scalare le soluzioni R o Python senza l'utilizzo di SQL Server.

| Versione | Aggiornamento delle funzionalità |
|---------|----------------|
| AGGIORNAMENTO CUMULATIVO 6 | Correzioni di bug e l'aggiornamento del pacchetto, ma non nuove funzionalità di annunci. Correzioni includono il supporto per i tipi di dati DateTime in query SPEES per Python e messaggi di errore migliorata microsoftml quando non sono presenti modelli con training preliminare. |
| AGGIORNAMENTO CUMULATIVO 5 | Correzioni di bug e l'aggiornamento del pacchetto, ma non nuove funzionalità di annunci. Correzioni sono stati introdotti miglioramenti per trasformare le funzioni e variabili in revoscalepy, la correzione di errori di tempo relativo al percorso in rxInstallPackages, correzione di connessioni in un loopback per RxExec e rx_exec funzioni e le revisioni per i messaggi di avviso. |
| CU 4 | Correzioni di bug e l'aggiornamento del pacchetto, ma non nuove funzionalità di annunci. |
| CU 3 | Serializzazione in revoscalepy, Python del modello utilizzando il [rx_serialize_model funzione](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/><br/>[Punteggio native](sql-native-scoring.md) più miglioramenti apportati a [assegnazione dei punteggi in tempo reale](real-time-scoring.md). Con l'assegnazione dei punteggi nel database, velocità effettiva è un milione di righe al secondo tramite modelli R. In questo aggiornamento, assegnazione dei punteggi in tempo reale e i punteggi native offrono anche prestazioni migliori in una singola riga e dell'assegnazione punteggio batch. Native punteggio utilizza una funzione di T-SQL per il punteggio veloce che può essere eseguita in qualsiasi edizione di SQL Server, anche in Linux. La funzione non richiede alcuna installazione di R o configurazione aggiuntiva. Ciò significa che è possibile eseguire il training di un modello in un' posizione, salvarlo in SQL Server e quindi eseguire l'assegnazione dei punteggi senza mai chiamare R. Per ulteriori informazioni sulle metodologie di punteggio, vedere [come eseguire l'assegnazione dei punteggi in tempo reale o punteggio nativo](r/how-to-do-realtime-scoring.md). |
| CU 2 | Correzioni di bug e l'aggiornamento del pacchetto, ma non nuove funzionalità di annunci. |
| CU 1 | In revoscalepy, aggiunge rx_create_col_info per la restituzione di informazioni sullo schema da un'origine dati SQL Server, simile a [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) per R. <br/><br/>Miglioramenti apportati a [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) per supportare scenari paralleli tramite il `RxLocalParallel` contesto di calcolo.|
| Versione iniziale |[**Integrazione di Python per analitica nel database**](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) <br/><br/>Il [revoscalepy](python/what-is-revoscalepy.md) pacchetto è l'equivalente di Python di RevoScaleR. È possibile creare modelli di Python per la regressione lineare e logistica, gli alberi delle decisioni, alberi con Boosting e foreste casuali, tutti gli eseguibili in parallelo e in grado di in esecuzione in contesti di calcolo remoto. Questo pacchetto supporta l'utilizzo di più origini dati e i contesti di calcolo remoto. L'esperto di dati o lo sviluppatore può eseguire codice Python in un Server SQL remoto, per esplorare i dati e compilare modelli senza spostare i dati. <br/><br/>Il [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) pacchetto è l'equivalente di Python del pacchetto R MicrosoftML.<br/><br/>Integrazione di T-SQL e Python tramite [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). È possibile chiamare qualsiasi codice Python tramite questa stored procedure. Questa infrastruttura sicura consente una distribuzione aziendale di modelli di Python e script che può essere chiamato da un'applicazione utilizzando una stored procedure semplice. Ulteriori miglioramenti delle prestazioni si ottengono dal flusso dati da SQL a processi di Python e parallelizzazione anello MPI. <br/><br/>È possibile utilizzare l'istruzione T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) funzione per eseguire [punteggio native](sql-native-scoring.md) su un modello con training preliminare che è stato salvato in precedenza nel formato binario richiesto.|
| Versione iniziale | [**MicrosoftML (R)** ](using-the-microsoftml-package.md) contiene lo stato dell'arte di machine learning trasformazioni dei dati e gli algoritmi che possono essere contesti di calcolo remoto scalato o eseguirlo in. Gli algoritmi sono logistic regression, gli alberi delle decisioni veloce e foreste delle decisioni, la regressione lineare e reti neurali profonde personalizzabile. |
| Versione iniziale | [**I modelli con training preliminare** ](r/install-pretrained-models-sql-server.md) per l'analisi di valutazione positivi, negativi e riconoscimento di immagini. Questi modelli possono essere utilizzati per generare stime sui propri dati. |
| Versione iniziale | [**Pacchetto di gestione**](r/r-package-management-for-sql-server-r-services.md), incluse le caratteristiche principali seguenti: i ruoli per gestire i pacchetti e assegnare le autorizzazioni per installare i pacchetti, l'amministratore di database del database [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione T-SQL per gestione i pacchetti senza dover sapere R Guida gli amministratori di database e le funzioni di un'ampia gamma di R in [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) consentono di installare, rimuovere o elencare i pacchetti di proprietà degli utenti. |
| Versione iniziale | [**Rendere operativo il tramite mrsdeploy** ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package) per la distribuzione e l'hosting di script R come servizio web. Si applica solo script R (alcun equivalente di Python). Deve essere l'opzione server (Standalone) evitare conflitti di risorse con altre operazioni di SQL Server. |


## <a name="new-in-sql-server-2016"></a>Novità di SQL Server 2016

Questa macchina versione introdotto apprendimento delle funzionalità in SQL Server tramite **R Services di SQL Server 2016**, un motore di database analitica per script di elaborazione R sui dati residenti all'interno di un'istanza del motore di database.

Inoltre, **SQL Server 2016 R Server (Standalone)** è stato rilasciato come un modo per installare R Server in un server di Windows. Il programma di installazione di SQL Server fornite inizialmente, l'unico modo per installare R Server per Windows. Nelle versioni successive, gli sviluppatori e gli esperti di dati che volevano R Server in Windows potrebbero utilizzare un altro programma di installazione autonomo per raggiungere lo stesso obiettivo. Il server in SQL Server autonomo è funzionalmente equivalente al prodotto server autonomo, [Microsoft R Server per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

| Versione |Aggiornamento delle funzionalità |
|---------|----------------|
| CU | [**Assegnazione dei punteggi in tempo reale** ](real-time-scoring.md) si basa su librerie native di C++ per leggere un modello archiviato in un formato binario ottimizzato e quindi generare stime senza necessità di chiamare il runtime di R. Ciò rende le operazioni di assegnazione dei punteggi molto più veloce. Con l'assegnazione dei punteggi in tempo reale, è possibile eseguire una stored procedure o eseguire in tempo reale dal codice R di punteggio. Assegnazione dei punteggi in tempo reale è disponibile anche per SQL Server 2016, se l'istanza viene aggiornato alla versione più recente di [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Versione iniziale | [**Integrazione di R per analitica nel database**](r/sql-server-r-services.md). <br/><br/> Pacchetti R per R chiamante funziona in T-SQL e viceversa. Le funzioni RevoScaleR forniscono analitica R a livello di scalabilità per la suddivisione in blocchi di dati in parti di componente, il coordinamento e gestione di elaborazione distribuita e l'aggregazione dei risultati. In SQL Server 2016 R Services (In-Database), il motore RevoScaleR è integrato con un'istanza di motore di database, salamoia insieme nello stesso contesto di elaborazione analitica e dati. <br/><br/>Integrazione di T-SQL e R tramite [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). È possibile chiamare qualsiasi codice R tramite questa stored procedure. Questa infrastruttura sicura consente una distribuzione aziendale di Rn modelli e gli script che possono essere chiamati da un'applicazione che utilizza una stored procedure semplice. Ulteriori miglioramenti delle prestazioni si ottengono dal flussi dati da SQL a processi R e la parallelizzazione anello MPI. <br/><br/>È possibile utilizzare l'istruzione T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) funzione per eseguire [punteggio native](sql-native-scoring.md) su un modello con training preliminare che è stato salvato in precedenza nel formato binario richiesto.|

## <a name="linux-support-roadmap"></a>Guida di orientamento per il supporto Linux

Machine learning che usano R o Python nel database non è attualmente supportato in SQL Server in Linux. Cercare gli annunci in una versione successiva.

In Linux, tuttavia, è possibile eseguire [punteggio native](sql-native-scoring.md) utilizzando la funzione di stima di T-SQL. Punteggio nativa consente di assegnare un punteggio da un modello con training preliminare molto veloce, senza chiamare o anche un runtime di R. Ciò significa che è possibile utilizzare SQL Server in Linux per generare stime molto veloci, per gestire le applicazioni client.

## <a name="next-steps"></a>Passaggi successivi

+ [Installare SQL Server 2017 Machine Learning Services (In-Database)](install/sql-machine-learning-services-windows-install.md)
+ [Esempi ed esercitazioni di machine learning](tutorials/machine-learning-services-tutorials.md)
