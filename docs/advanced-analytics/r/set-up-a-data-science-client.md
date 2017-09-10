---
title: Configurare un client di data science | Microsoft Docs
ms.custom: 
ms.date: 02/10/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0661b2fcf9b23d3c81cb0d80f0424d87dbde7ef8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-up--a-data-science-client"></a>Configurare un client per l'analisi scientifica dei dati
  Dopo aver configurato un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installando **R Services (In-Database)**, è consigliabile configurare un ambiente di sviluppo R che sia in grado di connettersi al server per l'esecuzione e la distribuzione remote. 
  
  Questo ambiente deve includere i pacchetti ScaleR e, facoltativamente, può includere un ambiente di sviluppo client.
  
 ## <a name="where-to-get-scaler"></a>Dove ottenere ScaleR 
  
  L'ambiente client deve includere Microsoft R Open, oltre ai pacchetti RevoScaleR aggiuntivi che supportano l'esecuzione distribuita di R in SQL Server.  Questi pacchetti possono essere installati in diversi modi:
  
+ Installare [Microsoft R Client](http://aka.ms/rclient/download). Altre istruzioni di configurazione sono disponibili nella pagina [Get Started with Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started) (Introduzione a Microsoft R Client)
+ Installare Microsoft R Server. È possibile ottenere Microsoft R Server tramite il programma di installazione di SQL Server o usando il nuovo programma Windows Installer autonomo. Per altre informazioni, vedere [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md) e [Introduction to R Server](https://msdn.microsoft.com/microsoft-r/rserver) (Introduzione a R Server).

Se si ha un contratto di licenza di R Server, è consigliabile usare Microsoft R Server (Standalone), per evitare limitazioni relative a dati in memoria e thread di elaborazione R.


## <a name="how-to-set-up-the-r-development-environment"></a>Come configurare l'ambiente di sviluppo R

È possibile usare qualsiasi ambiente di sviluppo R di propria scelta compatibile con Windows. 

+ R Tools per Visual Studio supporta l'integrazione con Microsoft R Open
+ RStudio è un ambiente gratuito molto diffuso  

Dopo l'installazione, sarà necessario riconfigurare l'ambiente per usare le librerie Microsoft R Open per impostazione predefinita, altrimenti non si avrà accesso alle librerie ScaleR. Per altre informazioni, vedere [Getting Started with Microsoft R Client](http://msdn.microsoft.com/microsoft-r/r-client-get-started) (Introduzione a Microsoft R Client).
 
## <a name="more-resources"></a>Altre risorse
  
 Per istruzioni dettagliate su come connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione remota di codice R, vedere l'esercitazione [Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md).  
 

Per iniziare a usare Microsoft R Client e i pacchetti ScaleR con SQL Server, vedere [ScaleR Getting Started](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#) (Introduzione a ScaleR).  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare SQL Server R Services &#40;In-Database&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  

