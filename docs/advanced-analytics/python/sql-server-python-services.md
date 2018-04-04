---
title: Machine Learning servizi con Python | Documenti Microsoft
ms.date: 03/16/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 47762e531cc3b0f78a17b19da80ad3ea2249a086
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="machine-learning-services-with-python"></a>Machine Learning servizi con Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python è un linguaggio che offre una notevole flessibilità e potenza per un'ampia gamma di attività di apprendimento automatico. Librerie open source per Python includono diverse piattaforme per le reti neurali personalizzabile, nonché le librerie comuni per l'elaborazione in linguaggio naturale. A questo punto, questa lingua ampiamente diffuso è supportata in SQL Server 2017 Machine Learning.

Poiché Python è integrato con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database, è possibile mantenere analitica vicino ai dati ed eliminare i costi e i rischi di sicurezza associati allo spostamento dei dati.  È possibile distribuire soluzioni di apprendimento macchina basate su Python con strumenti familiari pratici, ad esempio Visual Studio. Le applicazioni di produzione possono ottenere stime, modelli, o elementi visivi di runtime di Python 3.5 chiamando semplicemente un T-SQL stored procedure.

Questa versione include la distribuzione Anaconda di Python, nonché il [revoscalepy](../python/what-is-revoscalepy.md) libreria, per migliorare la scalabilità e prestazioni delle soluzioni di apprendimento automatico.

È possibile installare tutto ciò che occorre per iniziare a usare Python tramite l'installazione di SQL Server 2017:

+ [**Machine Learning Services (In-Database)**](../install/sql-machine-learning-services-windows-install.md): installare questa funzionalità, con il motore di database di SQL Server, attivare l'esecuzione sicura degli script Python il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.
  
     Quando si seleziona questa funzionalità, le estensioni vengono installate nel motore di database per supportare l'esecuzione di script Python e viene creato un nuovo servizio, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], per gestire le comunicazioni tra il runtime di Python e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.

+ [**Machine Learning Server (Standalone)**](../install/sql-machine-learning-standalone-windows-install.md): se non è necessario integrazione di SQL Server, installare questa funzionalità per ottenere il supporto di Python e R per l'apprendimento distribuita.

## <a name="see-also"></a>Vedere anche

+ [SQL Server di Machine Learning e R Services (In-Database)](../r/sql-server-r-services.md)
+ [SQL Server di Machine Learning e R Server (Standalone)](../r/r-server-standalone.md)
+ [Architettura di Python](architecture-overview-sql-server-python.md)
+ [Esercitazioni di Python](../tutorials/sql-server-python-tutorials.md)
