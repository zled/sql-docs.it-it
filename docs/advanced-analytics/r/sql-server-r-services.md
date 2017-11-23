---
title: Computer SQL Server servizi di apprendimento | Documenti Microsoft
ms.date: 11/09/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: "38"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: fb770b52f2cacfc527f6bb89955acfbda243c18a
ms.sourcegitcommit: ec5f7a945b9fff390422d5c4c138ca82194c3a3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2017
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning Services

  SQL Server 2017 Machine Learning Services (precedentemente SQL Server 2016 R Services) offre una piattaforma per lo sviluppo e distribuzione di applicazioni intelligenti che apre nuove prospettive. È possibile usare il linguaggio R, potente e ricco di funzionalità, e i numerosi pacchetti per creare modelli e generare stime tramite i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
  Poiché l'apprendimento è integrato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile mantenere analitica dati ed eliminare i costi e i rischi di protezione associati allo spostamento dei dati.
  
SQL Server supporta il linguaggio R open source con un set completo di strumenti e tecnologie che offrono prestazioni superiori, sicurezza, affidabilità e gestibilità. È possibile distribuire soluzioni R con strumenti SQL semplice e familiari e le applicazioni di produzione possono chiamare il runtime di R e recuperare le stime e gli elementi visivi usando [!INCLUDE[tsql](../../includes/tsql-md.md)]. È anche possibile ottenere il [Microsoft R](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) raccolte per migliorare la scalabilità e prestazioni delle soluzioni R, tra cui RevoScaleR, revoscalepy e MicrososftML.
  
Con l'installazione di SQL Server è possibile installare sia i componenti server che client.
  
## <a name="machine-learning-in-sql-server-2017"></a>Machine learning in SQL Server 2017

+ Installare **Machine Learning Services (In-Database)** durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programma di installazione per attivare l'esecuzione sicura degli script R o Python di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.
  
    Quando si seleziona questa funzionalità, estensioni vengono installate nel motore di database per supportare l'esecuzione del codice scritto in R o Python. Viene creato un nuovo servizio, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], per gestire le comunicazioni tra i runtime esterni e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.
  
+ Installare **Microsoft Machine Learning Server (Standalone)** in un computer separato, se non è necessario utilizzare SQL Server come contesto di calcolo. Server di Machine Learning include gli stessi componenti di machine learning, nonché la possibilità di eseguire i processi di apprendimento macchina scalabile e distribuita come servizio web.
  
+    Installare [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client) in computer remoti per lo sviluppo di soluzioni che possono essere distribuite in SQL Server o al Server di Machine Learning in Windows, Linux o Hadoop.

## <a name="machine-learning-in-sql-server-2016"></a>Machine learning in SQL Server 2016

+ Installare **R Services (In-Database)** durante l'installazione di SQL Server 2016 da attivare l'esecuzione sicura degli script R di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.
  
    Quando si seleziona questa funzionalità, viene visualizzato il possibilità di eseguire script R con SQL Server come contesto di calcolo, o di eseguire script R in una stored procedure.
  
+   Installare **Microsoft R Server (Standalone)** dal programma di installazione di SQL Server 2016, installare i componenti di R in un computer separato che è possibile utilizzare per lo sviluppo o distribuzione di soluzioni R.


## <a name="which-type-of-machine-learning-service-do-i-need"></a>Il tipo di servizio di machine learning necessario

+ Se è necessario eseguire il codice R nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzando stored procedure oppure utilizzando l'istanza di SQL Server come contesto di calcolo, è necessario installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] come descritto [qui](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).

+ Microsoft Machine Learning Server (Standalone) è un'opzione separata progettata per l'utilizzo di [Microsoft R](https://docs.microsoft.com/r-server/r-reference/introducing-r-server-r-package-reference) e [relative librerie Python](../python/what-is-revoscalepy.md) in un computer Windows che non è in esecuzione SQL Server. Tuttavia, richiede una licenza Enterprise Edition per SQL Server.
    
    Si consiglia di installare Microsoft Machine Learning Server (Standalone) in un computer portatile o un altro computer remoto utilizzato per lo sviluppo e utilizzare tale computer per creare e testare le soluzioni di machine learning che possono facilmente essere distribuite in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che esegue servizi di Machine Learning \(In Database\) o altro contesto di calcolo è supportato.
  
    È inoltre possibile utilizzare il **mrsdeploy** pacchetto installato con Server di Machine Learning per pubblicare e distribuire i processi R e Python come un servizio web.

## <a name="additional-resources"></a>Risorse aggiuntive

+ [Introduzione a SQL Server R Services](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    Vengono descritti scenari comuni per utilizzi di R con SQL Server

+ [Configurare Servizi R per SQL Server (In-Database)](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    Installare R e i componenti di database associato come parte del programma di installazione di SQL Server
  
+ [Esercitazioni su SQL Server R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Informazioni su come creare origini dati di SQL Server nel codice R e come usare contesti di calcolo remoti. Altre esercitazioni destinate agli sviluppatori SQL illustrano come eseguire il training e distribuire un modello R in SQL Server.
