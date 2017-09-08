---
title: Guida introduttiva con machine learning in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 08/20/2017
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
ms.openlocfilehash: 09d6e887a8c64c98a1c3f68c78b07c26da6ffb76
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-machine-learning-in-sql-server"></a>Guida introduttiva con machine learning in SQL Server

Microsoft fornisce un set integrato, scalabile di soluzioni di machine learning per sia in locale e nel cloud:

+ **Integrata**, in quanto è possibile eseguire R o Python in SQL Server. Ciò consente facilmente processi aziendali di tipo merge per ETL e i report con i dati di attività di analisi scientifica dei quali funzionalità di progettazione, creazione del modello e assegnazione dei punteggi.
+ **Scalabile**, in quanto l'esperto di dati possibile sviluppare e testare una soluzione in un computer portatile e distribuirlo a più piattaforme per distribuite o, ad esempio l'elaborazione parallela di operazioni relative alla chiave del modello di training e assegnazione dei punteggi. Piattaforme supportate includono SQL Server in Windows, Hadoop e Spark.

In questo articolo fornisce collegamenti a risorse per ogni prodotto nella piattaforma Microsoft Machine Learning.

## <a name="machine-learning-in-sql-server"></a>Machine learning in SQL Server

+ SQL Server 2017

  A partire da SQL Server 2017 CTP 2.0, il supporto per Python è stato aggiunto e il nome è stato modificato in Machine Learning Services (In-Database) in modo da riflettere il supporto per una vasta gamma di soluzioni di machine learning. Ora è possibile automatizzare attività di machine learning usando gli strumenti SQL per eseguire codice R o Python. In alternativa, usare il computer SQL Server come il _contesto di calcolo_ per i processi avviati da un ambiente di sviluppo remoto.

    + [Panoramica dell'architettura per Python in SQL Server](python/architecture-overview-sql-server-python.md)
    + [Configurare SQL Server R Services o i servizi di Machine Learning](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

+ SQL Server 2016

  SQL Server 2016 supporta l'esecuzione del codice R in SQL Server tramite le stored procedure. Questo semplifica automatizzare le attività di machine learning usando strumenti SQL. O, è possibile eseguire codice R da un laptop remoto o di un ambiente di sviluppo di R, quando si utilizza il computer SQL Server come il _contesto di calcolo_.

  Questa integrazione fornisce protezione per i dati e consente di gestire e bilanciare le risorse utilizzate da R.

    + [Guida introduttiva wth SQL Server R Services](r/getting-started-with-sql-server-r-services.md)
    + [Configurare SQL Server R Services o i servizi di Machine Learning](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

## <a name="microsoft-machine-learning-server-microsoft-r-server"></a>Microsoft Machine Learning Server (Microsoft R Server)

L'opzione per installare Microsoft Machine Learning Server disponibile in SQL Server 2017 per supportare i clienti aziendali che desiderano eseguire i processi di apprendimento automatico distribuita, scalabile, ma che non necessitano l'integrazione con il motore di database di SQL Server, ad esempio l'utilizzo di contesti di calcolo SQL.

In SQL Server 2016, utilizzare l'opzione per installare Microsoft R Server.
  
  + [Introducing Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver) (Introduzione a Microsoft R Server)
  
È anche possibile installare R Server tramite programmi di installazione specifico della piattaforma disponibile in MSDN:

  + [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (R Server per Windows)
  + [R Server per Linux](https://msdn.microsoft.com/microsoft-r/rserver-install-linux-server)
  + [R Server per Hadoop](https://msdn.microsoft.com/microsoft-r/rserver-install-hadoop)

> [!IMPORTANT]
> Se si desidera eseguire Python mediante R Server, assicurarsi di installare la versione più recente, **Machine Learning Server**, che è disponibile solo tramite il programma di installazione di SQL Server 2017:
> 
>    + [Configurare Microsoft R Server o Server di Machine Learning](../advanced-analytics/r/create-a-standalone-r-server.md)

## <a name="related-products"></a>Prodotti correlati

+ [Configurare un Client di analisi scientifica dei dati](../advanced-analytics/r/set-up-a-data-science-client.md)

  Se già installato uno di machine learning i prodotti server, in questo articolo fornisce informazioni su come configurare un computer separato per lo sviluppo e test di soluzioni, inclusi gli strumenti e librerie necessarie.

+ [Macchina virtuale per operazioni di data science](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

  Avviare la voce in machine learning tramite il recupero di computer completo apprendimento soluzione da Azure Marketplace. La macchina virtuale di analisi scientifica dei dati (spesso abbreviata in "DSVM") include SQL Server, Server di Microsoft Machine Learning e tutti gli strumenti di sviluppo.
  
  La versione più recente della macchina virtuale di analisi scientifica dei dati (DSVM) viene eseguito in Windows 2016 Preview Edition, per fornire l'aspetto di Windows 10 pulizia personalizzabile. È preconfigurato con i driver, CUDA Toolkit 8.0 e la libreria cuDNN NVIDIA per carichi di lavoro GPU NVIDIA.

## <a name="resources-for-learning"></a>Risorse informative

+ [Esercitazioni di Machine learning](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

  Iniziare da qui trovare un elenco di tutte le risorse per acquisire informazioni sulle soluzioni di machine learning utilizzando 2017 di SQL Server e SQL Server 2017.

### <a name="r-tutorials"></a>Esercitazioni di R

+ [Esercitazioni di SQL Server R](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

   Informazioni su come eseguire R in SQL Server, creare e usare contesti di calcolo remoto o eseguire simulazioni in R tramite SQL Server.
   
   Include esercitazioni "tutto il codice fornito" in modo che è possibile eseguire una soluzione completa di R da SQL Server Management Studio, senza mai aprire l'IDE R!

+ [Esplorare R e ridimensionamento in 25 funzioni brevi](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

   Non si ha familiarità con R? Sapere come Microsoft R (o RevoScaleR) Confronta a R standard? Per R Server, vedere questi rapida-avvio.

### <a name="python-tutorials"></a>Esercitazioni di Python

+ [Esercitazioni di SQL Server Python](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

  Informazioni su come eseguire Python in SQL Server. Compilare un modello usando Python e usarlo per assegnare un punteggio dati di SQL Server.

   Una soluzione end-to-end per gli sviluppatori SQL fornisce tutto il codice che è necessario eseguire Python da SQL Server Management Studio.

+ [Pubblicare e utilizzare il codice Python](../advanced-analytics/python/publish-consume-python-code.md)

  Questa procedura dettagliata viene fornito con tutto il codice necessario per distribuire un modello in un servizio web tramite Machine Learning Server.

### <a name="product-samples-with-code"></a>Esempi di codice

Queste soluzioni dal team di sviluppo di SQL Server eseguite in R o Python e vengono illustrati scenari comuni per l'integrazione di apprendimento con applicazioni aziendali.

+ [Compilare un'app intelligente con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

+ [Compilare un'app intelligente con SQL Server e Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

### <a name="data-science-solution-templates"></a>Modelli di soluzioni di analisi scientifica dei dati

I modelli di soluzione dal team di analisi scientifica dei dati di Microsoft rappresentano personalizzate per settori specifici o scenari per soluzioni di esempio completo. Sono progettati per essere utilizzato come blocchi predefiniti che consentono di implementare una soluzione veloce o per illustrare le procedure consigliate. Ogni modello include dati di esempio e codice personalizzabile.

+ [Modelli di soluzioni](../advanced-analytics/tutorials/data-science-scenarios-and-solution-templates.md)

## <a name="next-steps"></a>Passaggi successivi

[Introduzione a servizi di SQL Server Machine Learning](../advanced-analytics/r/getting-started-with-sql-server-r-services.md)

[Introduzione a Microsoft di Machine Learning Server](../advanced-analytics/r/getting-started-with-microsoft-r-server-standalone.md)

