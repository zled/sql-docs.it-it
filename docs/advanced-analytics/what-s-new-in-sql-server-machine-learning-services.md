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
ms.openlocfilehash: 8d3dc4c730ea9c7c9ba0126a50ed4bb8129efc9c
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152581"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Novità in servizi di SQL Server Machine Learning 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Funzionalità di Machine learning vengono aggiunti a SQL Server in ogni versione, per continuare a espandere, estendere e approfondire l'integrazione tra la piattaforma di dati e l'analisi scientifica dei dati, analitica e si desidera implementare sui dati di apprendimento supervisionato. 

## <a name="new-in-sql-server-2017"></a>Novità di SQL Server 2017

Questa versione aggiunge [supporto di Python e leader di settore algoritmi di machine learning](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Rinominati per riflettere il nuovo ambito, l'introduzione di segni di SQL Server 2017 [SQL Server Machine Learning Services (In-Database)](what-is-sql-server-machine-learning.md), con supporto del linguaggio per Python e R. 

Questa versione sono stati introdotta [SQL Server Machine Learning Server (Standalone)](r/r-server-standalone.md)e completamente indipendente di SQL Server, per carichi di lavoro R e Python che si desidera eseguire in un sistema dedicato. Con il server autonomo, è possibile distribuire e ridimensionare le soluzioni R o Python senza l'utilizzo di SQL Server.

### <a name="python-integration-for-in-database-analytics"></a>Integrazione di Python per analitica nel database

Integrazione di T-SQL e Python è ora supportata tramite il [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure di sistema. È possibile chiamare qualsiasi codice Python tramite questa stored procedure. Codice viene eseguito in un'architettura sicura e duale che consente la distribuzione aziendale di script, è possibile chiamare da un'applicazione usando una semplice stored procedure e modelli di Python. È possibile ottenere miglioramenti aggiuntivi relativi alle prestazioni da dati di streaming da SQL per processi Python e la parallelizzazione di anello MPI.

È possibile usare l'istruzione T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) funzione eseguire [assegnazione dei punteggi nativa](sql-native-scoring.md) su un modello con training preliminare che è stato salvato in precedenza nel formato binario richiesto.

### <a name="python-libraries"></a>Librerie Python

| Pacchetto | Description |
|---------|-------------|
[**revoscalepy**](python/what-is-revoscalepy.md)| Python equivalente di RevoScaleR. È possibile creare modelli di Python per la regressione lineare e logistica, alberi delle decisioni, alberi con Boosting e foreste casuali, tutti eseguibili in parallelo e in grado di in esecuzione in contesti di calcolo remoti. Questo pacchetto supporta l'utilizzo di più origini dati e contesti di calcolo remoti. I data scientist o sviluppatore può eseguire codice Python in un Server SQL remoto, per esplorare i dati e compilare modelli senza spostare i dati. |
|[**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) |Python-equivalente del pacchetto MicrosoftML R. |

### <a name="r-libraries"></a>Librerie di R

| Pacchetto | Description |
|---------|-------------|
| [**MicrosoftML (R)**](using-the-microsoftml-package.md) | Contesti di calcolo di algoritmi di apprendimento automatico dello stato dell'arte e trasformazione dei dati che può essere ridimensionato o eseguito in remoto. Gli algoritmi sono personalizzabili reti neurali profonde, alberi delle decisioni veloci e foreste delle decisioni, regressione lineare e la regressione logistica.  |
| [**Gestione dei pacchetti R**](r/install-additional-r-packages-on-sql-server.md) | Miglioramenti in questa versione, con le caratteristiche principali seguenti: ruoli per gestire i pacchetti e assegnare le autorizzazioni per installare i pacchetti, l'amministratore di database del database [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione T-SQL per gestire i pacchetti senza gli amministratori di database necessità di conoscere R e un set completo di funzioni R nel [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) per installare, rimuovere o elencare i pacchetti di proprietà da parte degli utenti. |

### <a name="pre-trained-models"></a>Modelli con training preliminare

[**I modelli con training preliminare** ](install/sql-pretrained-models-install.md) sono disponibili per Python e R. questi modelli per il riconoscimento di immagini e analisi del sentiment negativo positivo, utilizzati per generare stime usando dati personalizzati. 


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
