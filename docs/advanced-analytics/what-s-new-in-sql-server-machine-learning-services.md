---
title: Cosa&#39;novità di SQL Server Machine Learning Services s | Microsoft Docs
description: Nuovo gli annunci di funzionalità per ogni versione di SQL Server 2016 R Services, R Server, servizi Machine Learning di SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f01177114dd175767652a9bbd28e15afc3ce812e
ms.sourcegitcommit: c86335a432e109322d718a13c37ff4b948c39d2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43193027"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Novità in servizi di SQL Server Machine Learning 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Funzionalità di Machine learning vengono aggiunti a SQL Server in ogni versione, per continuare a espandere, estendere e approfondire l'integrazione tra la piattaforma di dati e l'analisi scientifica dei dati, analitica e si desidera implementare sui dati di apprendimento supervisionato. 

## <a name="new-in-sql-server-2017"></a>Novità di SQL Server 2017

Questa versione aggiunge [supporto di Python e leader di settore algoritmi di machine learning](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Rinominati per riflettere il nuovo ambito, l'introduzione di segni di SQL Server 2017 [SQL Server Machine Learning Services (In-Database)](what-is-sql-server-machine-learning.md), con supporto del linguaggio per Python e R. 

### <a name="r-enhancements"></a>Miglioramenti di R

Il componente di R di Machine Learning Services di SQL Server 2017 è la prossima generazione di SQL Server 2016 R Services, con le versioni aggiornate di altri pacchetti R di base e RevoScaler.

Le nuove funzionalità per R includono [ **Gestione pacchetti**](r/install-additional-r-packages-on-sql-server.md), con le caratteristiche principali seguenti: 

+ Ruoli predefiniti del database consentono gli amministratori di database di gestire i pacchetti e assegnare le autorizzazioni per l'installazione del pacchetto.
+ [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) gli amministratori di database consente di gestire i pacchetti nel familiare linguaggio T-SQL.
+ [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) funzioni consentono di installare, rimuovere o elencare i pacchetti di proprietà da parte degli utenti. Per altre informazioni, vedere [pacchetti di come usare funzioni RevoScaleR per trovare o installare R in SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>Librerie di R

| Pacchetto | Description |
|---------|-------------|
| [**MicrosoftML**](using-the-microsoftml-package.md) | In questa versione, MicrosoftML è incluso in un'installazione di R predefinita, eliminando la fase di aggiornamento richiesto nella precedente di SQL Server 2016 R Services. MicrosoftML offre d'avanguardia di machine learning algoritmi e trasformazioni dei dati che possono essere ridimensionate o eseguire in contesti di calcolo remoti. Gli algoritmi sono personalizzabili reti neurali profonde, alberi delle decisioni veloci e foreste delle decisioni, regressione lineare e la regressione logistica.  |

### <a name="python-integration-for-in-database-analytics"></a>Integrazione di Python per analitica nel database

Integrazione di T-SQL e Python è ora supportata tramite il [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure di sistema. È possibile chiamare qualsiasi codice Python tramite questa stored procedure. Codice viene eseguito in un'architettura sicura e duale che consente la distribuzione aziendale di script, è possibile chiamare da un'applicazione usando una semplice stored procedure e modelli di Python. È possibile ottenere miglioramenti aggiuntivi relativi alle prestazioni da dati di streaming da SQL per processi Python e la parallelizzazione di anello MPI.

È possibile usare l'istruzione T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) funzione eseguire [assegnazione dei punteggi nativa](sql-native-scoring.md) su un modello con training preliminare che è stato salvato in precedenza nel formato binario richiesto.

### <a name="python-libraries"></a>Librerie Python

| Pacchetto | Description |
|---------|-------------|
[**revoscalepy**](python/what-is-revoscalepy.md)| Python equivalente di RevoScaleR. È possibile creare modelli di Python per la regressione lineare e logistica, alberi delle decisioni, alberi con Boosting e foreste casuali, tutti eseguibili in parallelo e in grado di in esecuzione in contesti di calcolo remoti. Questo pacchetto supporta l'utilizzo di più origini dati e contesti di calcolo remoti. I data scientist o sviluppatore può eseguire codice Python in un Server SQL remoto, per esplorare i dati e compilare modelli senza spostare i dati. |
|[**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) |Python-equivalente del pacchetto MicrosoftML R. |

### <a name="pre-trained-models"></a>Modelli con training preliminare

[**I modelli con training preliminare** ](install/sql-pretrained-models-install.md) sono disponibili per Python e R. questi modelli per il riconoscimento di immagini e analisi del sentiment negativo positivo, utilizzati per generare stime usando dati personalizzati. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Server autonomo come funzionalità condivisa nel programma di installazione di SQL Server

Questa versione aggiunge inoltre [SQL Server Machine Learning Server (Standalone)](r/r-server-standalone.md), un server di analisi scientifica dei dati completamente indipendenti, che supporta analitica predittiva e statistiche in R e Python. Come con R Services. per questo server è la prossima versione di SQL Server 2016 R Server (Standalone). Con il server autonomo, è possibile distribuire e ridimensionare le soluzioni R o Python senza dipendenze in SQL Server.


## <a name="new-in-sql-server-2016"></a>Novità di SQL Server 2016

Questa versione introdotte funzionalità di machine learning in SQL Server attraverso **SQL Server 2016 R Services**, un motore di analitica nel database per lo script di elaborazione R sui dati residenti all'interno di un'istanza del motore di database.

È inoltre **SQL Server 2016 R Server (Standalone)** è stato rilasciato come un modo per installare R Server in un server di Windows. Il programma di installazione di SQL Server fornite inizialmente, l'unico modo per installare R Server per Windows. Nelle versioni successive, gli sviluppatori e data Scientist che volevano R Server in Windows è stato possibile usare un altro programma di installazione autonomo per ottenere lo stesso scopo. Il server autonomo di SQL Server è funzionalmente equivalente al prodotto server autonomo, [Microsoft R Server per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

| Versione |Aggiornamento delle funzionalità |
|---------|----------------|
| CU aggiunte | [**Assegnazione dei punteggi in tempo reale** ](real-time-scoring.md) si basa sulle librerie di C++ native per leggere un modello archiviato in un formato binario ottimizzato e quindi generare stime senza la necessità di chiamare il runtime R. Questo rende molto più veloci le operazioni di assegnazione dei punteggi. Con l'assegnazione dei punteggi in tempo reale, è possibile eseguire una stored procedure o assegnazione dei punteggi in tempo reale dal codice R. Assegnazione dei punteggi in tempo reale è disponibile anche per SQL Server 2016, se l'istanza viene aggiornato alla versione più recente di [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Versione iniziale | [**Integrazione di R per analitica nel database**](r/sql-server-r-services.md). <br/><br/> I pacchetti R per R chiamante funzioni in T-SQL e viceversa. Funzioni RevoScaleR forniscono analitica R su larga scala tramite la suddivisione in blocchi di dati in parti di componente, il coordinamento e gestione di elaborazione distribuita e l'aggregazione di risultati. In SQL Server 2016 R Services (In-Database), il motore di RevoScaleR è integrato con un'istanza del motore di database, salamoia insieme nello stesso contesto di elaborazione analitica e dati. <br/><br/>Integrazione di T-SQL e R attraverso [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). È possibile chiamare qualsiasi codice R tramite questa stored procedure. Questa infrastruttura protetta consente la distribuzione aziendale di Rn modelli e gli script che possono essere chiamati da un'applicazione con una semplice stored procedure. È possibile ottenere miglioramenti aggiuntivi relativi alle prestazioni da dati di streaming da SQL ai processi R e la parallelizzazione di anello MPI. <br/><br/>È possibile usare l'istruzione T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) funzione eseguire [assegnazione dei punteggi nativa](sql-native-scoring.md) su un modello con training preliminare che è stato salvato in precedenza nel formato binario richiesto.|

## <a name="linux-support-roadmap"></a>Guida di orientamento per supporto Linux

Machine learning usando R o Python nel database non è attualmente supportato in SQL Server in Linux. Cercare gli annunci in una versione successiva.

Tuttavia, in Linux è possibile eseguire [assegnazione dei punteggi nativa](sql-native-scoring.md) usando la funzione PREDICT T-SQL. Assegnazione dei punteggi nativa consente di assegnare un punteggio da un modello con training preliminare molto veloce, senza chiamare o anche richiedere un runtime di R. Ciò significa che è possibile usare SQL Server in Linux per generare stime molto rapidamente, per gestire le applicazioni client.

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Roadmap per Database SQL di Azure

È disponibile un supporto limitato per R in Database SQL di Azure: disponibile solo in Stati Uniti centrali, nei servizi creati con il piano Premium. Code coverage esteso, incluso il supporto di Python, è probabile che seguono in una versione futura. Tuttavia, non è Nessuna data di rilascio prevista in questa fase.  

## <a name="next-steps"></a>Passaggi successivi

+ [Installare SQL Server 2017 Machine Learning Services (In-Database)](install/sql-machine-learning-services-windows-install.md)
+ [Esempi ed esercitazioni di machine learning](tutorials/machine-learning-services-tutorials.md)
