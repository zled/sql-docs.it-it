---
title: Introduzione a Microsoft R Server (Standalone) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7874c6900474c7c2f3d927183616b2f5e69699
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-microsoft-r-server-standalone"></a>Introduzione a Microsoft R Server (Standalone)
  Microsoft R Server (Standalone) consente di introdurre il diffuso linguaggio open source R nell'organizzazione, per abilitare soluzioni di analisi ad alte prestazioni e l'integrazione con altre applicazioni aziendali.  

  
## <a name="install-microsoft-r-server"></a>Installare Microsoft R Server 

Il modo in cui installare Microsoft R Server dipende dalla necessità o meno di usare dati di SQL Server nelle applicazioni. In questo caso, eseguire l'installazione tramite il programma di installazione di SQL Server. Se non si intende usare dati di SQL Server o non è necessario eseguire codice R nel database, è possibile usare il programma di installazione di SQL Server oppure il nuovo programma di installazione autonomo.
 
 
+ Installare Microsoft R Server (Standalone) dal programma di installazione di SQL Server. Viene creata un'istanza separata dei file binari R per R Server e questa istanza viene concessa in licenza tramite i criteri di supporto di SQL Server Enterprise Edition. Per altre informazioni, vedere [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  

+ Usare il nuovo programma di installazione di Windows autonomo per creare un'istanza del tutto nuova di Microsoft R Server che usa i criteri di supporto relativi al ciclo di vita del software Microsoft. Per altre informazioni, vedere [Run Microsoft R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (Eseguire Microsoft R Server per Windows).

+ Se si vuole aggiornare un'istanza esistente di R Server (Standalone) o R Services, è necessario scaricare ed eseguire il programma di installazione basato su Windows per l'aggiornamento. Per altre informazioni, vedere [Run Microsoft R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (Eseguire Microsoft R Server per Windows).
  
## <a name="install-additional-r-tools"></a>Installare strumenti R aggiuntivi  

 È consigliabile installare il componente [Microsoft R Client](http://aka.ms/rclient/download) gratuito (download).  

 È possibile usare l'ambiente di sviluppo R preferito per sviluppare soluzioni per SQL Server R Services o Microsoft R Server. Per informazioni dettagliate, vedere [Installare o configurare gli strumenti R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md). 
 

### <a name="location-of-r-server-binaries"></a>Percorso dei file binari di R Server

A seconda del metodo usato per installare Microsoft R Server, il percorso predefinito è diverso. Prima di iniziare a usare l'ambiente di sviluppo preferito, verificare il percorso in cui sono state installate le librerie R:

+ Microsoft R Server installato tramite il nuovo programma di installazione di Windows

  `C:\Program Files\Microsoft\R Server\R_SERVER`

+ R Server (Standalone) installato tramite il programma di installazione di SQL Server

  `C:\Program Files\Microsoft SQL Server\130\R_SERVER`

+ R Services (In-Database)

  `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`
      
## <a name="start-using-r-on-microsoft-r-server"></a>Iniziare a usare R in Microsoft R Server  

 Dopo aver configurato i componenti server e aver configurato l'IDE di R per usare i file binari di R Server, è possibile iniziare a sviluppare la soluzione usando le nuove API, come il pacchetto RevoScaleR, MicrosoftML e olapR.
    
Per iniziare a usare R Server, vedere questa guida in MSDN Library: [R Server - Getting Started](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-node) (R Server - Introduzione)   
  
-   [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-getting-started): esplorare questa raccolta di funzioni analitiche distribuibili che offrono prestazioni e scalabilità elevate per le soluzioni R. Include versioni parallelizzabili di molti dei più diffusi pacchetti di modellazione R, tra cui clustering K-Means, alberi delle decisioni e foreste delle decisioni, nonché strumenti per la modifica dei dati. Per altre informazioni, vedere [Explore R and ScaleR in 25 Functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started-tutorial) (Esplorare R e ScaleR in 25 funzioni)  
    
- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx): il pacchetto MicrosoftML è un set di nuovi algoritmi e trasformazioni di apprendimento automatico rapidi e scalabili sviluppati in Microsoft. Per altre informazioni, vedere [MicrosoftML functions](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (Funzioni MicrosoftML).
  


  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  

