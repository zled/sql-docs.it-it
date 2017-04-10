---
title: "Ottimizzazione delle prestazioni di SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf6f3b7d-f9f9-4e45-b0d1-07850b53e0c5
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Ottimizzazione delle prestazioni di SQL Server R Services
[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] rende disponibile una piattaforma per lo sviluppo di applicazioni intelligenti che apre nuove prospettive. Un data scientist è possibile utilizzare la potenza del linguaggio R per eseguire il training e creare modelli che utilizzano dati archiviati all'interno di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Quando il modello è pronto per la produzione, un data scientist possibile lavorare con gli amministratori di database e degli ingegneri di SQL per distribuire la soluzione nell'ambiente di produzione. Le informazioni contenute in questa sezione vengono fornite indicazioni di livello elevato sulla regolazione di migliorare le prestazioni durante la creazione e modelli di training e durante la distribuzione di modelli nell'ambiente di produzione.

Le informazioni contenute in questo documento si prevedono che si ha familiarità con [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] concetti e terminologia. Per informazioni generali sui servizi di R, vedere [servizi di SQL Server R](../../advanced-analytics/r-services/sql-server-r-services.md).

> [!NOTE]
> Mentre la maggior parte delle informazioni in questa sezione è indicazioni generali sulla configurazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], alcune informazioni sono specifiche per le funzioni analitiche RevoScaleR.

## Argomenti della sezione

* [Configurazione di SQL Server](../../advanced-analytics/r-services/sql-server-configuration-r-services.md): in questo documento vengono fornite indicazioni per la configurazione dell'hardware che [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è installato. Ed è particolarmente utile per __gli amministratori di Database__.

* [R e ottimizzazione dei dati](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md): in questo documento vengono fornite indicazioni sull'uso di script R con i servizi di R. È più utile __Data Scientist__.

* [Case Study di prestazioni](../../advanced-analytics/r-services/performance-case-study-r-services.md): in questo documento fornisce dati di test e gli script R che possono essere utilizzati per verificare l'impatto delle indicazioni fornite nei documenti precedenti.

## Riferimenti

Di seguito vengono forniti collegamenti a informazioni utilizzate nello sviluppo di questo documento.

* [Come determinare le dimensioni di file della pagina sia appropriato per le versioni a 64 bit di Windows](https://support.microsoft.com/kb/2860880)

* [Compressione dei dati](../../relational-databases/data-compression/data-compression.md)

* [Abilitare la compressione in una tabella o un indice](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [Disabilitare la compressione in una tabella o un indice](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

* [Strumento di test DISKSPD archiviazione load generator/prestazioni](https://github.com/microsoft/diskspd)

* [Riferimento utilità FSUtil](https://technet.microsoft.com/library/cc753059.aspx)

* [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

* [R Services](../../advanced-analytics/r-services/r-services.md)

* [Opzioni di ottimizzazione delle prestazioni per rxDForest e rxDTree](https://support.microsoft.com/kb/3104235)

* [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)

* [Guida dell'utente RevoScaleR](https://packages.revolutionanalytics.com/doc/7.0.0/win/RevoScaleR_Users_Guide.pdf)

* [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

## Vedere anche

 
 [Configurazione di SQL Server per i servizi di R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [Case Study di prestazioni](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R e ottimizzazione dei dati](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)