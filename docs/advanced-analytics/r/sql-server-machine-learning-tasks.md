---
title: Computer del ciclo di vita e il processo di apprendimento | Documenti Microsoft
ms.date: 11/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: bfe2fb19481c78e982d69303af1dec8041283324
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="machine-learning-lifecycle-and-personas"></a>Utenti tipo e ciclo di vita di machine learning

Progetti di Machine learning possono essere complessi, poiché richiedono le competenze e collaborazione di un set diverso di professionisti. In questo articolo descrive le attività principali nel ciclo di vita di apprendimento macchina, il tipo di professionisti di dati coinvolti in machine learning e come SQL Server supporta le esigenze.

> [!TIP]
> 
> Prima di iniziare in un progetto di machine learning, si consiglia di rivedere gli strumenti e procedure consigliate fornite dal [processo di analisi scientifica dei dati di Microsoft Team](https://blogs.technet.microsoft.com/machinelearning/2017/10/09/the-microsoft-team-data-science-process-tdsp-recent-updates/), o TDSP. Questo processo è stato creato da consulenti Microsoft consolidare le procedure consigliate intorno alla pianificazione e l'iterazione di machine learning progetti di apprendimento automatico. Il TDSP secondo gli standard del settore, ad esempio metodologia, ma include procedure recenti, ad esempio DevOps e la visualizzazione.

## <a name="machine-learning-life-cycle"></a>Ciclo di vita di Machine learning

Machine learning è un processo complesso che interessa tutti gli aspetti dei dati nell'organizzazione e molti progetti di machine learning finiscono richiede più tempo ed è più complessa del previsto. Ecco alcuni dei modi che l'apprendimento richiede il supporto dei professionisti di dati nell'organizzazione:

+ Apprendimento inizia con l'identificazione degli obiettivi e le regole di business.
+ I professionisti di Machine learning necessario considerare di criteri per l'archiviazione e l'estrazione di dati del controllo.
+ Raccolta di dati potenzialmente applicabili è successivo.  Origini dati devono essere identificate e i dati appropriati estratti da sensori e applicazioni aziendali. 
+ La qualità delle attività di machine learning è elevata dipende non solo il tipo di dati che sono disponibili, ma i processi molto usati per l'estrazione, l'elaborazione e l'archiviazione dei dati. 
+ Nessun progetto di machine learning sarebbe incompleta senza una strategia per reporting e analisi e probabilmente coinvolgimento e commenti e suggerimenti.

SQL Server consente di effettuare il bridging molti degli spazi vuoti tra i professionisti di dati dell'organizzazione e gli esperti di machine learning:

+ I dati possono essere archiviata in locale o nel cloud
+ SQL Server è integrato in ogni fase dell'elaborazione dei dati aziendali, creazione di report ed ETL
+ SQL Server supporta la protezione dei dati, la ridondanza dei dati e controllo
+ Fornisce la governance delle risorse

## <a name="data-scientists"></a>Esperti di dati

Gli esperti di dati usano un'ampia gamma di strumenti per l'analisi dei dati e machine learning, che vanno da Excel o piattaforme open source gratuite, fino a Suite statistiche costose che richiedono conoscenze tecniche approfondite. Tuttavia, l'uso di R o Python con SQL Server offre alcuni importanti vantaggi rispetto a questi strumenti tradizionali:

+ È possibile sviluppare e testare una soluzione con l'ambiente di sviluppo di propria scelta, quindi distribuire il codice R o Python come parte del codice T-SQL.
+ Spostare i calcoli complessi il portatile dell'esperto di dati e al server, evitando lo spostamento di dati per soddisfare i criteri di sicurezza aziendali.
+ Scalabilità e prestazioni vengono migliorate attraverso le API e pacchetti R speciali. Sono massima libertà con l'architettura a thread singolo associata alla memoria di R e può funzionare con grandi set di dati e calcoli multithread, multicore, multiprocesso.
+ Portabilità del codice: soluzioni è possono eseguire in SQL Server o in Hadoop o in Linux, usando [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Una volta il codice, distribuire remoto via Internet.

## <a name="application-and-database-developers"></a>Sviluppatori di applicazioni e database

Gli sviluppatori di database si occupano di integrare più tecnologie e raggruppare i risultati in modo che possano essere condivisi in tutta l'organizzazione. Lo sviluppatore del database funziona con gli sviluppatori di applicazioni, gli sviluppatori SQL e gli esperti di dati per progettare soluzioni, metodi di gestione dati, è consigliabile e progettare o distribuire soluzioni.

Integrazione con SQL Server offre numerosi vantaggi agli sviluppatori di dati:

+ L'esperto di dati è possibile lavorare in RStudio, mentre lo sviluppatore di dati consente di distribuire la soluzione utilizzando SQL Server Management Studio. Non sono più presenti registrazione delle soluzioni R o Python.
+ Ottimizzare le soluzioni tramite il meglio di T-SQL, R e Python. È possibile eseguire operazioni complesse su grandi set di dati in modo molto più efficiente utilizzando SQL Server in R. usare la conoscenza dei professionisti del database per migliorare le prestazioni delle soluzioni di machine learning, tramite gli indici columnstore in memoria, e aggregazioni tramite operazioni basate su set SQL. 
+ Automatizzare facilmente le attività che deve essere eseguito più volte su grandi quantità di dati, ad esempio la generazione di punteggi di stima sui dati di produzione. 
+ Accesso con script R o Python da qualsiasi applicazione che utilizza parametri [!INCLUDE[tsql](../../includes/tsql-md.md)]. Solo chiamare una stored procedure per eseguire il training di un modello, generare un tracciato o restituire stime.
+ API possono trasmettere grandi set di dati e trarre vantaggio da multithread, multicore, multiprocesso nel database.

Per informazioni sulle attività correlate, vedere:
+ [Operatività del codice R](../../advanced-analytics/r/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>Amministratori di database

Gli amministratori del database devono integrare progetti e priorità in concorrenza all'interno di un singolo punto di contatto: il server di database. È necessario specificare l'accesso ai dati non solo per gli esperti, ma per un'ampia gamma di sviluppatori di report, analisti aziendali e fruitori dei dati aziendali, mantenendo l'integrità degli archivi dei dati operativi e dei report. Nell'organizzazione, l'amministratore di database è una parte fondamentale della compilazione e distribuzione di un'infrastruttura efficace per l'analisi scientifica dei dati. 

SQL Server fornisce funzionalità univoche per l'amministratore di database che deve supportare il ruolo della scienza dei dati:

+ Protezione da SQL Server: l'architettura di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] mantiene i database protetti e isola l'esecuzione delle sessioni dello script esterno dall'operazione dell'istanza del database. È possibile specificare gli utenti autorizzati a eseguire gli script di machine learning e utilizzare i ruoli di database per gestire i pacchetti.

+ Le sessioni di R e Python vengono eseguite in un processo separato per garantire che il server continui a funzionare normalmente anche se lo script esterno rileva i problemi.

+ Governance delle risorse utilizzando SQL Server consente di controllare la memoria e i processi allocati al runtime esterni, per evitare che calcoli di grande entità possano compromettere le prestazioni complessive del server.

Per informazioni sulle attività correlate, vedere:
+ [Gestione e monitoraggio delle soluzioni di apprendimento automatico](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

## <a name="architects-and-data-engineers"></a>Gli architetti e i dati tecnici

Gli architetti progettano flussi di lavoro integrati che si estendono su tutti gli aspetti del ciclo di vita di machine learning. Gli ingegneri dei dati progettare e creare soluzioni ETL e determinano come ottimizzare le attività di progettazione di funzionalità per machine learning. La piattaforma di dati complessivo deve essere progettata per soddisfare esigenze di business concorrenti.

Grazie alla stretta integrazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] con altri strumenti Microsoft, come lo stack di data warehouse e business intelligence, strumenti di mobilità e cloud aziendali e Hadoop, gli ingegneri dei dati o agli architetti di sistema che vogliono promuovere analisi avanzate hanno a disposizione numerosi vantaggi.

+ Chiamare uno script Python o R tramite stored procedure di sistema, per popolare i set di dati, creare grafici o ottenere stime. Non più Progettazione flussi di lavoro paralleli analisi scientifica dei dati e gli strumenti ETL. Supporto per Data Factory di Azure e Database SQL di Azure, è facile usare origini dati cloud in flussi di lavoro di apprendimento automatico.

+ Per la pianificazione e gestione delle attività di apprendimento automatico, utilizzare i flussi di lavoro di automazione standard in SQL Server, in base a Integration Services, SQL Agent o Data Factory di Azure. In alternativa, usare il [funzionalità rendere operativo il](https://docs.microsoft.com/machine-learning-server/operationalize/how-to-deploy-web-service-publish-manage-in-r) in Machine Learning Server.

Per informazioni sulle attività correlate, vedere:

+ [Creazione di flussi di lavoro di machine learning in SQL Server](../../advanced-analytics/r/creating-workflows-that-use-r-in-sql-server.md)

