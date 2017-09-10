---
title: "Attività di formazione macchina SQL Server | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 60272ce672c0a32738b0084ea86f8907ec7fc0a5
ms.openlocfilehash: c0e7a0929d5caa84df1a1fb02894db08313a36bd
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="sql-server-machine-learning-tasks"></a>Attività di Machine Learning di SQL Server

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] combina la potenza e la flessibilità del linguaggio R open source con gli strumenti di livello aziendale per l'archiviazione e la gestione dei dati, lo sviluppo del flusso di lavoro, la creazione e la visualizzazione di report. Questo argomento descrive di machine learning e ciclo di vita, come SQL Server supporta le esigenze di quattro professionisti di dati diversi che sono enagged nell'apprendimento.

## <a name="machine-learning-life-cycle"></a>Ciclo di vita di Machine Learning

Machine learning non è un'attività a breve termine, ma piuttosto un processo a lungo termine che interessa tutti gli aspetti dei dati nell'organizzazione. Apprendimento inizia con l'identificazione di obiettivi aziendali e le regole e raccolta dei dati da sensori e applicazioni aziendali. Machine learning dipendono i processi per l'estrazione, elaborazione e l'archiviazione dei dati e viene sempre più importante quando si considerano i criteri per l'archiviazione e l'estrazione di dati del controllo. Infine, ora machine learning è un'importante omponent delle strategie per reporting e analisi, nonché coinvolgimento e commenti e suggerimenti.



SQL Server è ideale per machine learning, in quanto supera i limiti degli spazi vuoti nel procedimento di machine learning:

+ Funziona in locale o nel cloud
+ Integrato in ogni fase dell'elaborazione dei dati aziendali, tra business intelligence
+ Supporta la protezione ottimale dei dati
+ Fornisce la governance delle risorse e il controllo

## <a name="data-professionals-and-how-they-use-machine-learning"></a>Dati professionisti e come essi usare Machine Learning

### <a name="data-scientists"></a>Esperti di dati

Gli esperti di dati hanno accesso a un'ampia gamma di strumenti per l'analisi dei dati e machine learning, che vanno da Excel o piattaforme open source gratuite, fino a Suite statistiche costose che richiedono conoscenze tecniche approfondite. Tuttavia, l'integrazione con SQL Server offre vantaggi esclusivi:

+ È possibile sviluppare e testare le soluzioni usando l'ambiente di sviluppo R preferito.
+ Trasferire i calcoli a database, evitando lo spostamento dei dati e conformi ai criteri di sicurezza aziendali.
+ Scalabilità e prestazioni vengono migliorate attraverso le API e pacchetti R speciali. Sono massima libertà con l'architettura a thread singolo associata alla memoria di R e può funzionare con grandi set di dati e calcoli multithread, multicore, multiprocesso.
+ Codice R può essere facilmente distribuito nell'ambiente di produzione e chiamato dal dashboard, applicazioni, gli altri database e strumenti enterprise.
+ Gli esperti di dati è possono distribuire e aggiornare qualsiasi soluzione di analisi rispettando i requisiti standard per la gestione dei dati aziendali, tra cui sicurezza e controllo dell'accesso
+ Portabilità del codice: riutilizzare con facilità il codice R su altre origini dati, ad esempio Hadoop

### <a name="application-and-database-developers"></a>Sviluppatori di applicazioni e Database

Gli sviluppatori di database si occupano di integrare più tecnologie e raggruppare i risultati in modo che possano essere condivisi in tutta l'organizzazione. Lo sviluppatore di database collabora con sviluppatori di applicazioni, sviluppatori di SQL ed esperti di dati per progettare soluzioni, metodi di gestione dei dati consigliati, per architettare e distribuire le soluzioni. 

Integrazione con SQL Server offre i seguenti vantaggi agli sviluppatori di dati che lavorano con machine learning:

+ Usare strumenti comuni per interagire con gli script R. Consente agli esperti di dati di lavoro in RStudio mentre lo sviluppatore di dati consente di distribuire la soluzione utilizzando SQL Server Management Studio. Non sono più presenti registrazione delle soluzioni R o Python.
+ Ottimizzare l'utilizzo di una stessa SQL e R, o SQL e Python. In molti casi, possono eseguire operazioni complesse su grandi set di dati in modo molto più efficiente utilizzando le funzionalità di SQL Server, ad esempio columnstoreindexes in memoria o aggregazioni molto veloce in T-SQL. Utilizzare un machine learning lingua in cui ha senso e SQL per spostare ed elaborare dati.
+ Automatizzare facilmente le attività che deve essere eseguito più volte su grandi quantità di dati, ad esempio la generazione di punteggi di stima sui dati di produzione.
+ Eseguire script R o Python da qualsiasi applicazione che utilizza [!INCLUDE[tsql](../../includes/tsql-md.md)]. Solo chiamare una stored procedure per creare un modello con parametri, generare un tracciato complesso o restituire stime.
+ Il **RevoScaleR** e **revoscalepy** API possono operare su grandi set di dati e trarre vantaggio da multithread, multicore, multiprocesso nel database.

Per informazioni sulle attività correlate, vedere:
+ [Operationalizing Your R Code](../../advanced-analytics/r-services/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>Amministratori di database

Gli amministratori del database devono integrare progetti e priorità in concorrenza all'interno di un singolo punto di contatto: il server di database. È necessario specificare l'accesso ai dati non solo per gli esperti, ma per un'ampia gamma di sviluppatori di report, analisti aziendali e fruitori dei dati aziendali, mantenendo l'integrità degli archivi dei dati operativi e dei report. Nell'organizzazione, l'amministratore di database è una parte fondamentale della compilazione e distribuzione di un'infrastruttura efficace per l'analisi scientifica dei dati. 

SQL Server fornisce funzionalità univoche per l'amministratore di database che deve supportare il ruolo della scienza dei dati:

+ Protezione da SQL Server: l'architettura di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] mantiene i database protetti e isola l'esecuzione delle sessioni dello script esterno dall'operazione dell'istanza del database. È possibile specificare gli utenti autorizzati a eseguire gli script di machine learning e utenti autorizzati a installare nuovi pacchetti di R, usando i ruoli del database.

+ Le sessioni di R e Python vengono eseguite in un processo separato per garantire che il server continui a funzionare normalmente anche se lo script esterno rileva i problemi.

+ Governance delle risorse utilizzando SQL Server consente di controllare la memoria e i processi allocati al runtime esterni, per evitare che calcoli di grande entità possano compromettere le prestazioni complessive del server.

Per informazioni sulle attività correlate, vedere:
+ [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)

### <a name="architects-and-etl-designers"></a>Architetti e progettisti ETL

Gli architetti progettano flussi di lavoro integrati che si estendono su tutti gli aspetti del ciclo di vita di machine learning. Gli ingegneri dei dati di progettare e creare soluzioni ETL e determinare come ottimizzare la progettazione di funzionalità completo di attività fanno parte del procedimento di machine learning. Spesso, la piattaforma di dati complessivo deve essere progettata per soddisfare esigenze di business di concorrenza e completezza.

Grazie alla stretta integrazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] con altri strumenti Microsoft, come lo stack di data warehouse e business intelligence, strumenti di mobilità e cloud aziendali e Hadoop, gli ingegneri dei dati o agli architetti di sistema che vogliono promuovere analisi avanzate hanno a disposizione numerosi vantaggi.

+ Strumenti di sviluppo noto per lo sviluppo di soluzioni R e Python. È possibile chiamare qualsiasi script Python o R tramite stored procedure di sistema, per popolare i set di dati, creare grafici o ottenere stime. Non più Progettazione flussi di lavoro paralleli analisi scientifica dei dati e gli strumenti ETL. Supporto per Data Factory di Azure e Database SQL di Azure semplifica trasformare e gestire i dati e utilizzare origini dati cloud in flussi di lavoro di apprendimento automatico.

+ Pianificazione e la gestione tramite le funzionalità di rendere operativo il in Microsoft R Server.

Per informazioni sulle attività correlate, vedere:

+ [Creazione di flussi di lavoro che usano R in SQL Server](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md)


