---
title: "Configurare un client per l&#39;analisi scientifica dei dati | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Configurare un client per l&#39;analisi scientifica dei dati
  Dopo aver configurato un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installando **R Services (In-Database)**, è consigliabile configurare un ambiente di sviluppo R che sia in grado di connettersi al server per l'esecuzione e la distribuzione remote. 
  
  L'ambiente client deve includere Microsoft R Open, oltre ai pacchetti RevoScaleR aggiuntivi che supportano l'esecuzione distribuita di R in SQL Server.  Questi pacchetti possono essere installati in diversi modi:
  
+ Installare [Microsoft R Client](http://aka.ms/rclient/download).
+ Installare Microsoft R Server. È possibile ottenere Microsoft R Server dal programma di installazione di SQL Server o da un programma di installazione autonomo. Per altre informazioni, vedere [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md) o [Introduction to R Server](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver?branch=r-server-nov16-dev) (Introduzione a R Server).

 Per altre informazioni su come usare Microsoft R Client per connettersi a SQL Server tramite i pacchetti ScaleR, vedere [ScaleR Getting Started](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#) (Introduzione a ScaleR).  
  
 Per istruzioni dettagliate su come connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione remota di codice R, vedere l'esercitazione [Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare SQL Server R Services &#40;In-Database&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  