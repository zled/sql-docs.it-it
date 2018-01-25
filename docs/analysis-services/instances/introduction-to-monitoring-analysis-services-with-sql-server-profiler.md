---
title: Introduzione al monitoraggio di Analysis Services con SQL Server Profiler | Documenti Microsoft
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 568ec549-5ddc-493a-b9f8-3bdc548b562e
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 193b7d2907fe41c35560f23e204a3f56e209802d
ms.sourcegitcommit: 3206a31870f8febab7d1718fa59fe0590d4d45db
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="introduction-to-monitoring-analysis-services-with-sql-server-profiler"></a>Introduzione al monitoraggio di Analysis Services tramite SQL Server Profiler
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] è possibile monitorare eventi generati da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], è possibile eseguire le operazioni seguenti:  
  
-   Monitorare le prestazioni di un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Eseguire il debug di istruzioni MDX (Multidimensional Expressions).  
  
-   Identificare istruzioni MDX che vengono eseguite lentamente.  
  
-   Verificare il funzionamento di istruzioni MDX nelle fasi di sviluppo di un progetto tramite l'esecuzione passaggio per passaggio delle istruzioni per assicurarsi che il codice funzioni come previsto.  
  
-   Risolvere problemi in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso l'acquisizione di eventi in un sistema di produzione e la relativa riproduzione in un sistema di prova. Ciò risulta utile per eseguire verifiche e debug e consentire agli utenti di continuare a utilizzare il sistema di produzione senza interferenze.  
  
-   Controllare ed esaminare l'attività verificatasi in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Un amministratore responsabile della sicurezza può rivedere qualsiasi evento controllato, ad esempio l'esito positivo o negativo di un tentativo di accesso e l'esito positivo o negativo dell'accesso a istruzioni e oggetti.  
  
-   Visualizzare dati sugli eventi acquisiti o acquisire e salvare dati su ciascun evento su un file o una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per consentirne l'analisi o l'esecuzione in futuro. Durante la riproduzione dei dati è possibile rieseguire fedelmente gli eventi salvati in tempo reale o passaggio per passaggio.  
  
## <a name="using-sql-server-profiler"></a>Utilizzo di SQL Server Profiler  
 Per creare o riprodurre tracce utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , è necessario essere membro del ruolo di server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Se si è membri del ruolo di server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile avviare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] dal gruppo di programmi [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del menu **Start** .  
  
 Quando si utilizza [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], notare quanto segue:  
  
-   Le definizioni di traccia sono archiviate nel database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso l'istruzione CREATE.  
  
-   È possibile eseguire più tracce contemporaneamente.  
  
-   Gli eventi di una medesima traccia possono essere ricevuti da più connessioni.  
  
-   Una traccia può continuare anche quando si arresta e riavvia [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Le password non sono rivelate negli eventi di traccia ma vengono sostituite da ****** nell'evento.  
  
 Per ottenere prestazioni ottimali, utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per monitorare solo gli eventi a cui si è maggiormente interessati. Il monitoraggio di un numero troppo elevato di eventi determina un aumento dell'overhead e può portare alla creazione di una tabella o di un file di traccia di grandi dimensioni, soprattutto quando il monitoraggio viene eseguito per un lungo periodo di tempo. È inoltre consigliabile utilizzare filtri per limitare la quantità di dati raccolta ed evitare che le tracce diventino troppo grandi.  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [Creare tracce del Profiler per Replay &#40; Analysis Services &#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)  
  
  
