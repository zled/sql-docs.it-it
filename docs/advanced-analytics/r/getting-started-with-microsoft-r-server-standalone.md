---
title: Introduzione a Microsoft R Server (Standalone) | Microsoft Docs
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: b7a9ec054b512e8825bf5cf9208a0c1deb3abbb8
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="getting-started-with-machine-learning-server-standalone"></a>Getting Started with Machine Learning Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
In SQL Server 2016, Microsoft R Server (Standalone) consente di portare il diffuso linguaggio open source R nell'organizzazione, per abilitare soluzioni analitica ad alte prestazioni e l'integrazione con altre applicazioni aziendali.  

In SQL Server 2017, il nome è stato modificato in Machine Learning Server (standalone) in modo da riflettere l'aggiunta del supporto per il linguaggio Python. Entrambe le versioni sono disponibili gratuitamente per gli utenti della Enterprise Edition o Software Assurance.

Questo articolo fornisce una panoramica generale del modo in cui è possibile utilizzare Machine Learning Server (o R Server) e su come iniziare a usare l'installazione ed esempi.

## <a name="why-use-a-standalone-server-for-machine-learning"></a>Perché usare un server autonomo per machine learning

Se non è necessario integrare soluzioni con dati di SQL Server di apprendimento automatico, Machine Learning Server offre lo stesso supporto distribuito, scalabile per R, Python e supporta inoltre la distribuzione di soluzioni in Hadoop, Spark o Linux.

Server di Machine Learning include anche i modelli con training preliminare per l'analisi delle immagini e analisi del sentiment, che è possibile utilizzare immediatamente nelle applicazioni.

Le funzionalità di rendere operativo il di Machine Learning Server supportano la distribuzione e la distribuzione di soluzioni R e Python usando i servizi web con esecuzione in modalità remota, topologie cluster Spark e Hadoop MapReduce e supportano per Windows o Linux.

**SQL Server 2016**

+ Installare Microsoft R Server (Standalone) dal programma di installazione di SQL Server 2016.

    Questa opzione Crea un server autonomo che è completamente indipendente da R Services (In-Database). Questa versione supporta solo R. Il programma di installazione di un server autonomo è incluso nei criteri di supporto di SQL Server Enterprise Edition. Per altre informazioni, vedere [Creare un server R autonomo](../../advanced-analytics/r/create-a-standalone-r-server.md).

+ Installare R Server utilizzando il programma di installazione di Windows separato.

    Questo programma di installazione crea una nuova istanza di Microsoft R Server che utilizza i criteri di supporto Microsoft moderna ciclo di vita di Software. È anche possibile installare R Server per Linux, Cloudera, Teradata e Hadoop.
    
    Per altre informazioni, vedere [installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

**SQL Server 2017**

+ Installare Machine Learning Server (Standalone) dal programma di installazione di SQL Server 2017. 

    Questa opzione Crea un server autonomo per supportare rendere operativo il di machine learning in R, Python o entrambi. Il programma di installazione di un server autonomo è incluso nei criteri di supporto di SQL Server Enterprise Edition. Per altre informazioni, vedere [Creare un server R autonomo](../../advanced-analytics/r/create-a-standalone-r-server.md).  

+ Utilizzare il nuovo autonoma Windows installer.

    Questo metodo di installazione crea una nuova istanza della macchina Server di apprendimento che utilizza i criteri di supporto Microsoft moderna ciclo di vita di Software. È anche possibile installare Machine Learning Server in Hadoop, Spark o Linux senza alcun costo aggiuntivo.
    
    Per altre informazioni, vedere [installare Machine Learning per Windows ReportServer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

**Aggiornare un server esistente**

+ Se si dispone di un server esistente o un'istanza che si desidera aggiornare, scaricare ed eseguire il programma di installazione basati su Windows per ottenere gli aggiornamenti. 

    Per altre informazioni, vedere [SqlBindR utilizzando per aggiornare un'istanza](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="start-using-machine-learning-server"></a>Iniziare a usare Machine Learning Server

 Dopo aver configurato i componenti server e configurato l'IDE per utilizzare i file binari del Server di Machine Learning, è possibile iniziare a sviluppare la soluzione usando le nuove API, ad esempio il RevoScaleR e revoscalepy MicrosoftML e olapR.
    
Per un'introduzione, vedere le guide seguenti:

+ [Modelli di soluzioni](https://docs.microsoft.com/machine-learning-server/r/sample-solutions)

    Gli esempi theses sono soluzioni che illustrano come applicare apprendimento in settori specifici. Gli scenari correnti sono in definitiva, finanza, sanità e marketing.

+ [Esplorare R e ScaleR nelle 25 funzioni](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): esplorare questa raccolta di funzioni analitiche distribuibile che forniscono prestazioni elevate e scalabilità per soluzioni R. Include versioni parallelizzabili di molti dei più diffusi pacchetti di modellazione R, tra cui clustering K-Means, alberi delle decisioni e foreste delle decisioni, nonché strumenti per la modifica dei dati.

- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx)

    Il pacchetto MicrosoftML è un set di nuovo di machine learning algoritmi e le trasformazioni sviluppate da Microsoft che sono veloci e scalabili. È possibile utilizzarlo in R o Python. Per altre informazioni, vedere [MicrosoftML per Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) e [MicrosoftML per R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package).

## <a name="see-also"></a>Vedere anche

[Introduzione a SQL Server apprendimento automatico servizi](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)