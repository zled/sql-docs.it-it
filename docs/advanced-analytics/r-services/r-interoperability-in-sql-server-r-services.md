---
title: "Interoperabilit&#224; di R in servizi SQL Server R | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0506b950-34b3-4f11-8e2f-d067a58015bd
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Interoperabilit&#224; di R in servizi SQL Server R

Questo argomento viene illustrato il meccanismo per l'esecuzione per R all'interno di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], e vengono descritte le differenze tra Microsoft R e open source R. Per informazioni sui componenti aggiuntivi, vedere [nuovi componenti in SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md).

### Componenti R Open Source

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include una distribuzione completa base pacchetti R e degli strumenti. Per ulteriori informazioni su ciò che è incluso nella distribuzione di base, vedere la documentazione installata durante l'installazione nel percorso predefinito seguente:
`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

Come parte dell'installazione di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], è necessario consentire i termini della licenza pubblica GNU. Successivamente, è possibile eseguire pacchetti R standard senza ulteriori modifiche esattamente come si farebbe con qualsiasi altra distribuzione Apri origine r.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] non modificare il runtime di R in alcun modo. Il runtime R viene eseguito all'esterno del [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] elaborare e può essere eseguito in modo indipendente da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Tuttavia, è consigliabile non eseguire questi strumenti durante [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizza R, per evitare conflitti di risorse.

Distribuzione del pacchetto di base R che è associata a uno specifico [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza è reperibile nella cartella associata all'istanza. Ad esempio, se è installato Servizi di R nell'istanza predefinita, le librerie R si trovano `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`.

Analogamente, gli strumenti di R associati all'istanza predefinita sono posizionati `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`,

Per ulteriori informazioni sulla distribuzione di base, vedere [pacchetti installati con Microsoft R Open](https://mran.revolutionanalytics.com/rro/installed/)

### Pacchetti R aggiuntive

Oltre alla distribuzione base R, [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include alcuni pacchetti R proprietarie, nonché un framework per l'esecuzione parallela di R e librerie che supportano l'esecuzione di R in contesti di elaborazione remota. 

Questo set di funzionalità R - la distribuzione di base R oltre le funzionalità avanzate di R e pacchetti - combinato è detto **Microsoft R**. Se si installa Microsoft R Server (autonomo), ottenere esattamente lo stesso set di pacchetti che vengono installati con SQL Server R Services (Database), ma in una cartella diversa. 

Microsoft R include una distribuzione di Intel matematiche Kernel Library, viene utilizzato ogni volta che è possibile per più veloce l'elaborazione matematica. Ad esempio, la libreria di algebra lineare base (BLAS) viene utilizzata per molti dei pacchetti aggiuntivi nonché R stesso. Per ulteriori informazioni, vedere gli articoli:

+ [La modalità Kernel matematiche Intel accelera R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)
+ [Vantaggi del collegamento R a librerie matematiche con multithreading](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)

Tra le aggiunte più importanti per Microsoft R sono il **RevoScaleR** e **RevoPemaR** pacchetti. Si tratta di pacchetti R che sono stati scritti principalmente in C o C++ per ottenere prestazioni migliori.

+ **RevoScaleR.** Include una vasta gamma di API per l'analisi e manipolazione dei dati. Le API sono state ottimizzate per analizzare i set di dati che sono troppo grandi per adattarsi in memoria ed eseguire calcoli distribuiti su più core o processori.

   APIs RevoScaleR supportano inoltre l'utilizzo di subset di dati per una maggiore scalabilità. In altre parole, la maggior parte delle funzioni RevoScaleR possono operare su blocchi di dati e utilizzare l'aggiornamento di algoritmi per aggregare i risultati. Pertanto soluzioni R basate sulle funzioni RevoScaleR possono funzionare con set di dati molto grandi e non sono associate dalla memoria locale.

  Il pacchetto RevoScaleR supporta inoltre il. Formato di file XDF per lo spostamento e l'archiviazione dei dati utilizzati per l'analisi più veloce. Il formato XDF viene utilizzata l'archiviazione a colonne, è portabile e può essere utilizzato per caricare e quindi modificare i dati da diverse origini, tra cui testo, SPSS o una connessione ODBC. In questa esercitazione viene fornito un esempio di come utilizzare il formato XDF: [approfondimento di analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)


+ **RevoPemaR.** PEMA è l'acronimo di un algoritmo parallelo memoria esterna. Il **RevoPemaR** pacchetto fornisce API che è possibile utilizzare per sviluppare i propri algoritmi paralleli. Per ulteriori informazioni, vedere [RevoPemaR Guida introduttiva](https://msdn.microsoft.com/microsoft-r/rserver/rserver-pemar-getting-started).

## Vedere anche
[Panoramica dell'architettura](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)

[Nuovi componenti in SQL Server per supportare i servizi di R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)

[Panoramica della sicurezza](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)
