---
title: Computer SQL Server servizi di apprendimento | Documenti Microsoft
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: "38"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 136df79ded4c86a183d78ecc39821550ca9c24c9
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning Services

SQL Server 2017 Machine Learning Services (precedentemente SQL Server 2016 R Services) offre una piattaforma per lo sviluppo e distribuzione di applicazioni intelligenti che apre nuove prospettive. Poiché l'apprendimento è integrato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile mantenere analitica dati ed eliminare i costi e i rischi di protezione associati allo spostamento dei dati.
  
+ In SQL Server 2016, è possibile sviluppare e distribuire facilmente soluzioni basate sul popolare linguaggio R per analisi scientifica dei dati. 

    Le funzionalità includono la [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) librerie, che forniscono nuove scalabilità e prestazioni per le soluzioni R e algoritmi avanzati di [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package).
+ In SQL Server 2017, è possibile utilizzare sia R e Python per sviluppare e rendere operative le soluzioni di analisi scientifica dei dati. 

    Il [revoscalepy](../python/what-is-revoscalepy.md) libreria per Python fornisce scalabilità simili a quelli di RevoScaleR e contesti di calcolo remoto.

SQL Server supporta miglioramento delle prestazioni, sicurezza e gestibilità per i carichi di lavoro di machine learning tramite un set completo di strumenti e tecnologie. È possibile distribuire R o soluzioni utilizzo pratico di Python, familiarità metodologia SQL e gli strumenti. Usare semplicemente [!INCLUDE[tsql](../../includes/tsql-md.md)] per chiamare i runtime R o Python da applicazioni di produzione, per compilare modelli o recuperare gli oggetti visivi. Se già stato eseguito un modello, è possibile generare stime da esso utilizzando solo T-SQL, tramite [punteggio nativo](../sql-native-scoring.md).

## <a name="machine-learning-in-sql-server-2017"></a>Machine learning in SQL Server 2017

+ Installare **Machine Learning Services (In-Database)** durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programma di installazione per attivare l'esecuzione sicura degli script R o Python di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.
  
    Quando si seleziona questa funzionalità, estensioni vengono installate nel motore di database per supportare l'esecuzione del codice scritto in R o Python. Viene creato un nuovo servizio, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], per gestire le comunicazioni tra i runtime esterni e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.
  
+ Installare **Microsoft Machine Learning Server (Standalone)** in un computer separato, se non è necessario utilizzare SQL Server come contesto di calcolo. Server di Machine Learning include gli stessi componenti di machine learning, nonché la possibilità di eseguire i processi di apprendimento macchina scalabile e distribuita come servizio web.
  
+ Installare [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) in computer remoti per lo sviluppo di soluzioni che possono essere distribuite in SQL Server o al Server di Machine Learning in Windows, Linux o Hadoop.

## <a name="machine-learning-in-sql-server-2016"></a>Machine learning in SQL Server 2016

+ Installare **R Services (In-Database)** durante l'installazione di SQL Server 2016 da attivare l'esecuzione sicura degli script R di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.
  
    Quando si seleziona questa funzionalità, viene visualizzato il possibilità di eseguire script R con SQL Server come contesto di calcolo, o di eseguire script R in una stored procedure.
  
+ Installare **Microsoft R Server (Standalone)** dal programma di installazione di SQL Server 2016, installare i componenti di R in un computer separato che è possibile utilizzare per lo sviluppo o distribuzione di soluzioni R.

## <a name="how-to-get-started"></a>Come iniziare

Installazione di SQL Server sono disponibili due opzioni:

+ Installazione di analitica nel database di funzionalità che è integrato con SQL Server, o
+ Installare la versione autonoma di Machine Learning Server (o Microsoft R Server) che supporta l'apprendimento su larga scala senza un'istanza di SQL Server.

Se è necessario eseguire il codice R nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzando stored procedure oppure utilizzando l'istanza di SQL Server come contesto di calcolo, è necessario installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] come descritto nel [Guida all'installazione](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md). Questa opzione offre la protezione dei dati massima e l'integrazione con strumenti di SQL Server.

Microsoft Machine Learning Server (Standalone) è un'opzione separata progettata per l'utilizzo di [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) e [relative librerie Python](../python/what-is-revoscalepy.md) in un computer Windows che non è in esecuzione SQL Server. Questa opzione richiede una licenza Enterprise Edition per SQL Server.
    
È consigliabile installare Machine Learning Server (Standalone) in un computer portatile o un altro computer remoto utilizzato per lo sviluppo e utilizzare tale computer per creare e testare le soluzioni di apprendimento che possono facilmente essere distribuite in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ovvero in esecuzione servizi di Machine Learning \(In Database\) o altro contesto di calcolo è supportato.
  
È inoltre possibile utilizzare il **mrsdeploy** pacchetto installato con Server di Machine Learning per pubblicare e distribuire i processi R e Python come un servizio web.

## <a name="additional-resources"></a>Risorse aggiuntive

+ [Introduzione a servizi di SQL Server Machine Learning](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    Vengono descritti scenari comuni per utilizzi di R con SQL Server

+ [Configurare servizi di SQL Server Machine Learning o i servizi R nel Database](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    Installare R e i componenti di database associato come parte del programma di installazione di SQL Server
  
+ [Esercitazioni di SQL Server e R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Informazioni su come creare origini dati di SQL Server nel codice R e come usare contesti di calcolo remoti. Altre esercitazioni destinate agli sviluppatori SQL illustrano come eseguire il training e distribuire un modello R in SQL Server.
