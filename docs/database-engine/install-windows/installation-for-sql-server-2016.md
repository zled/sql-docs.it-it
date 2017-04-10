---
title: "Installazione per SQL Server 2016 | Microsoft Docs"
ms.custom: ""
ms.date: "04/13/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.portal.Installation.f1"
helpviewer_keywords: 
  - "installazione di SQL Server, installazione iniziale"
  - "installazione [SQL Server]"
  - "installazione iniziale [SQL Server]"
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Installazione per SQL Server 2016
  L'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce un singolo albero delle funzionalità per installare tutti i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Componenti di connettività  
  
 A partire da SQL Server 2016, Strumenti di gestione di SQL Server non viene più installato dall'albero delle funzionalità principale. Per informazioni dettagliate, vedere [Installare gli strumenti di gestione di SQL Server con SSMS](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md)  
  
 È possibile installare singolarmente ogni componente o selezionare una combinazione dei componenti elencati sopra. Per adottare la scelta migliore tra le edizioni e i componenti disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) e [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## Argomenti della sezione  
 Sia che si utilizzi l'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o il prompt dei comandi per installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il processo di installazione prevede i passaggi seguenti.  
  
 [Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
 Viene descritto come preparare il computer per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Requisiti hardware e software.  
  
-   Requisiti di Controllo configurazione sistema e problemi di blocco.  
  
-   Considerazioni relative alla sicurezza.  
  
 [Installare SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)  
 Vengono descritte le opzioni di installazione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Guida di riferimento all'interfaccia utente del programma di installazione di SQL Server](../Topic/SQL%20Server%20Setup%20User%20Interface%20Reference.md)  
 Vengono descritte le opzioni di installazione disponibili nell'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Eseguire l'aggiornamento a SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
 Vengono descritte le opzioni per l'aggiornamento a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Disinstallare SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)  
 Vengono descritte le routine per disinstallare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [Installazione del cluster di failover di SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 In questa sezione della documentazione relativa al programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono descritte le modalità di installazione e configurazione del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Installare le funzionalità di business intelligence di SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le funzionalità che fanno parte della piattaforma di Microsoft Business Intelligence includono [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e diverse applicazioni client usate per la creazione o l'uso di dati analitici. In questa sezione della documentazione relativa al programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene descritto come installare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## Altre informazioni  
 [Installare le funzionalità di Business Intelligence di SQL Server con SharePoint &#40;Power Pivot e Reporting Services&#41;](../Topic/Install%20SQL%20Server%20BI%20Features%20with%20SharePoint%20\(Power%20Pivot%20and%20Reporting%20Services\).md)  
 In questa sezione viene illustrato come installare funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un ambiente SharePoint. e vengono identificate le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibili in una versione ed edizione specifiche di SharePoint Sono incluse anche le procedure di installazione per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint e per Reporting Services in modalità SharePoint.  
  
 ![ssrs_fyi_note](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) Installare il nuovo database di esempio, [Wide World Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx). 
  
 [Altri esempi e database di esempio di SQL Server](http://sqlserversamples.codeplex.com/)  
 Viene descritto come installare e configurare gli esempi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i database di esempio.  
  
Vedere la [pagina relativa al centro aggiornamenti di SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) per collegamenti e informazioni per tutte le versioni supportate di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
## Vedere anche  
 [Novità relative all'installazione di SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
  
  