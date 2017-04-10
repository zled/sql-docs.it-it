---
title: "Panoramica dell&#39;architettura (SQL Server R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c4a4f66-ea3e-4a73-acf2-6c8aeafc94b0
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# Panoramica dell&#39;architettura (SQL Server R Services)
In questa sezione viene fornita una panoramica dell'architettura di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], inclusa la sicurezza, nuovi componenti aggiunti nel motore di database SQL Server ai componenti di supporto R e l'interoperabilità di script R open source in esecuzione in SQL Server.


## Obiettivi


L'architettura di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] è progettato per supportare il linguaggio R open source. Gli utenti correnti di R devono essere in grado di trasferire il proprio codice R e eseguirla in T-SQL con relativamente piccole modifiche.

Tuttavia, SQL Server R Services fornisce anche innovazioni che offrono un miglioramento delle prestazioni e maggiore integrazione di database per il linguaggio R, per abilitare più veloce di velocità effettiva dei dati e l'elaborazione e di ridurre gli ostacoli per lo sviluppo aziendale delle soluzioni di R. Queste innovazioni sono entrambi open source e proprietari componenti sviluppati da Microsoft.


Gli obiettivi principali di integrazione con SQL Server sono utili per fornire prestazioni e scalabilità migliori per R, mentre la gestione dei dati in modo sicuro. Verso questo obiettivo, SQL Server R Services fornisce un'infrastruttura più processo che supporta l'autenticazione Windows integrata e basata su password account di accesso SQL. 

+ [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] fornisce una distribuzione di base di R, con i pacchetti di ridimensionamento e la possibilità di eseguire attività di R in parallelo.
+ Nuovi componenti in SQL Server forniscono un framework sicuro e ad alte prestazioni per l'esecuzione di script esterni.
+ Le attività di R vengono eseguite all'esterno del processo di SQL Server, per garantire la sicurezza e maggiore facilità di gestione.
+ [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] gestisce la protezione di tutti i processi R. 

Per ottimizzare il codice R esistente e sfruttare questi miglioramenti, gli argomenti in questa sezione descrivono la nuova architettura in dettaglio. Per informazioni su come viene gestita l'elaborazione dati e l'analisi da [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], è possibile effettuare scelte appropriate su come inserire dati, come in modo più efficiente eseguire progettazione di funzionalità e come utilizzare i risultati.
 

## Argomenti della sezione
+ [R l'interoperabilità](../../advanced-analytics/r-services/r-interoperability-in-sql-server-r-services.md)
+ [Nuovi componenti in SQL Server per i servizi di R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)
+ [Panoramica della sicurezza](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)

## Vedere anche
[Esercitazioni su Services R](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)
