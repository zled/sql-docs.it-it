---
title: Esercitazioni su SQL Server R | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 08/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 341ec619ee5976ca7488f3662f010358b4457437
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-r-tutorials"></a>Esercitazioni di SQL Server R

Questo articolo fornisce un elenco di esercitazioni ed esempi che illustrano l'uso di R con SQL Server 2016 o SQL Server 2017. Attraverso questi esempi e demo, si apprenderà:

+ Come eseguire R da T-SQL
+ Che cosa sono i contesti di calcolo remoti e locali, e come è possibile eseguire codice R con il computer SQL Server
+ Come eseguire il wrapping di codice R in una stored procedure
+ Ottimizzazione del codice R per un ambiente di produzione di SQL
+ Scenari reali per l'incorporamento di apprendimento nelle applicazioni

Per informazioni sui requisiti e il programma di installazione, vedere [prerequisiti](#bkmk_Prerequisites).

## <a name="bkmk_sqltutorials"></a>Esercitazioni di R

Se non diversamente indicato, le esercitazioni sono state sviluppate per R Services di SQL Server 2016 e si prevede di lavorare in servizi di SQL Server 2017 Machine Learning senza modifiche significative.

Tutte le esercitazioni usano ampiamente le funzionalità nel pacchetto RevoScaleR per SQL Server contesti di calcolo.

+ [Approfondimento analisi scientifica dei dati con R e SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

  Informazioni su come utilizzare le funzioni nel pacchetto RevoScaleR. Spostare i dati tra R e SQL Server e commutatore contesti per soddisfare una particolare attività di calcolo. Creare modelli e i grafici e spostarli tra l'ambiente di sviluppo e il server di database.

  **Pubblico:** per gli esperti di dati o gli sviluppatori che hanno già familiarità con il linguaggio R e che desiderano apprendere i pacchetti R avanzati e le funzioni R Microsoft da Revolution Analitica.

  **Requisiti:** conoscenza di base R. Accesso a un server con SQL Server R Services o i servizi di Machine Learning con R. Per informazioni sull'installazione, vedere [prerequisiti](#bkmk_Prerequisites).

+ [Analitica R nel database per gli sviluppatori SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)

  Compilare e distribuire una soluzione completa di R, usando solo [!INCLUDE[tsql](../../includes/tsql-md.md)] strumenti.

  È incentrata sullo spostamento di una soluzione nell'ambiente di produzione. Si apprenderà come eseguire il wrapping del codice R in una stored procedure, come salvare un modello R in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e come effettuare chiamate con parametri al modello R per la creazione di stime.

  **Pubblico:** per gli sviluppatori SQL, gli sviluppatori di applicazioni o ai professionisti SQL che supportano soluzioni R e desiderano apprendere come distribuire i modelli R in SQL Server.

  **Requisiti:** non è necessario alcun ambiente R. Viene fornito tutto il codice R ed è possibile compilare la soluzione completa utilizzando solo [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e la familiarità business intelligence e gli strumenti di sviluppo di SQL. Tuttavia, alcune conoscenze di base di R sono utile.

  È necessario avere accesso a SQL Server con il linguaggio R installato e abilitato. Per informazioni sull'installazione, vedere [prerequisiti](#bkmk_Prerequisites).

+ [Guida introduttiva: Uso di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

  Questa Guida introduttiva illustra la sintassi di base per l'uso di R in [!INCLUDE[tsql](../../includes/tsql-md.md)].

  Informazioni su come chiamare il runtime R da T-SQL, eseguire il wrapping di funzioni R nel codice SQL ed eseguire una stored procedure che salva l'output di R e i modelli R a una tabella SQL.

  **Pubblico:** per gli utenti che hanno familiarità con la funzionalità e desiderano apprendere le nozioni di base della chiamata di R da una stored procedure.

  **Requisiti:** alcuna conoscenza di R o istruzioni SQL necessarie. Tuttavia, è necessario SQL Server Management Studio o un altro client in grado di connettersi a un database e di eseguire T-SQL. È consigliabile gratuita [estensione MSSQL per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) se si ha familiarità con le query T-SQL.

  È inoltre necessario avere accesso a un server con SQL Server R Services o i servizi di Machine Learning con R già abilitato. Per informazioni sull'installazione, vedere [prerequisiti](#bkmk_Prerequisites).

+ [Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

  Viene illustrato il processo di analisi scientifica dei dati dall'inizio alla fine, come acquisire i dati e salvarlo in SQL Server, analizzare i dati con R e creare grafici.

  Si apprenderà come spostare gli elementi grafici tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e R e progettazione di funzionalità confronto in T-SQL con le funzioni di R. Infine, si apprenderà come usare il modello predittivo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per assegnazione punteggio batch e assegnazione dei punteggi a riga singola.

  **Pubblico:** per gli utenti che hanno familiarità con R e strumenti di sviluppo, ad esempio SQL Server Management Studio.

  **Requisiti:** deve disporre dell'accesso a un ambiente di sviluppo di R e sapere come eseguire i comandi di R. Per scaricare il set di dati di New York City taxi sia richiesto l'utilizzo di PowerShell. È necessario avere accesso a un server con SQL Server R Services o i servizi di Machine Learning con R già abilitato. Per informazioni sull'installazione, vedere [prerequisiti](#bkmk_Prerequisites).

## <a name ="bkmk_samples"></a>Esempi del prodotto

Questi esempi e demo vengono fornite dal team di sviluppo di SQL Server per evidenziare i diversi modi, che è possibile utilizzare analitica incorporati nelle applicazioni reali.

+ [Compilare un modello predittivo con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Informazioni su come una società di noleggio ski potrebbe utilizzare machine learning per stimare il noleggio di futuro, che consente al piano aziendale e personale per rispondere alla domanda futura.

+ [Clienti di eseguire il clustering con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  Utilizzare apprendimento non supervisionato ai clienti di segmento in base ai dati di vendita.

## <a name="bkmk_Prerequisites"></a>Prerequisiti

Per utilizzare queste esercitazioni ed esempi, è necessario installare uno dei seguenti prodotti server:

+ SQL Server 2016 R Services (In-Database)
  
  Supporta R. Assicurarsi di installare di machine learning funzionalità e quindi abilitare gli script esterni.

+ SQL Server 2017 Machine Learning Services (In-Database)
  
  Supporta R o Python. È necessario selezionare di machine learning funzionalità e la lingua da installare e quindi abilitare gli script esterni.

Dopo l'installazione di SQL Server, non dimenticare questi passaggi importanti:

+ Abilitare la funzionalità di esecuzione di script esterni eseguendo`sp_configure 'external scripts enabled', 1`
+ Riavviare il server
+ Verificare che il servizio che chiama il runtime esterno disponga delle autorizzazioni necessarie
+ Verificare che l'account di accesso SQL o un account utente di Windows disponga delle autorizzazioni necessarie per connettersi al server, per leggere i dati e creare oggetti di database necessari dall'esempio

Se si verificano problemi, vedere questo articolo per alcuni problemi comuni: [risoluzione dei problemi di Machine Learning Services](../machine-learning-troubleshooting-faq.md)
