---
title: Traccia e la riproduzione degli eventi | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 514c1dd7bf0bd2d3e8708368391d61bc39c0ed62
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tracing-and-replaying-events"></a>Traccia e riproduzione di eventi
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO il **traccia** e **riproduzione** gli oggetti di <xref:Microsoft.SqlServer.Management.Trace> dello spazio dei nomi forniscono l'accesso programmatico al [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] funzionalità, viene utilizzata per il monitoraggio di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. È possibile acquisire e salvare i dati di ogni evento in un file o in una tabella per operazioni di analisi successive. È ad esempio possibile monitorare un ambiente di produzione per verificare le stored procedure che influiscono sulle prestazioni a causa di un'esecuzione troppo lenta.  
  
 Il **traccia** e **riproduzione** oggetti forniscono un set di oggetti che può essere usato per creare tracce in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Questi oggetti possono essere utilizzati all'interno di applicazioni personalizzate per creare tracce in modo manuale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Inoltre, SMO **traccia** oggetti possono essere utilizzati per leggere i file di traccia SQL e le tabelle create mediante il monitoraggio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], o la registrazione DTS.  
  
 SMO **traccia** oggetti consentono di eseguire le funzioni seguenti:  
  
-   Creare una traccia.  
  
-   Impostare i filtri nella traccia.  
  
-   Impostare gli eventi per la traccia.  
  
-   Avviare o arrestare una traccia.  
  
-   Leggere file di traccia e tabelle di traccia.  
  
-   Ottenere informazioni sugli eventi in una traccia.  
  
-   Ottenere informazioni sui filtri in una traccia.  
  
-   Modificare i dati di traccia a livello di programmazione.  
  
-   Scrivere file di traccia e tabelle di traccia.  
  
-   Riprodurre file di traccia o tabelle di traccia.  
  
 I dati di traccia di **traccia** e **riproduzione** oggetti possono essere utilizzati dall'applicazione SMO o possono essere esaminato manualmente mediante [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). I dati di traccia sono inoltre compatibili con la [traccia SQL](../../../relational-databases/sql-trace/sql-trace.md) stored procedure che forniscono anche le funzionalità di traccia.  
  
 Gli oggetti di traccia SMO risiedono nello spazio dei nomi <xref:Microsoft.SqlServer.Management.Trace>, che richiede un riferimento al file Microsoft.SQLServer.ConnectionInfo.dll.  
  
 Il **traccia** e **riproduzione** oggetti richiedono un [ServerConnection](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> oggetto per stabilire una connessione con l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il [ServerConnection](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.common.serverconnection.aspx) risiede nell'oggetto di [Microsoft.SqlServer.Management.Common](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.common) spazio dei nomi, che richiede un riferimento al file Microsoft.SQLServer.ConnectionInfo.dll.  
  
> [!NOTE]  
>  Il **traccia** e **riproduzione** oggetti non sono supportati in una piattaforma a 64 bit.  
  
  
