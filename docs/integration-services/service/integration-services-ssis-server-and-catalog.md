---
title: "Integration Services (SSIS) Server e del catalogo | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti [Integration Services], gestione"
  - "gestione di pacchetti [Integration Services]"
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Integration Services (SSIS) Server e del catalogo
  Dopo aver progettato e testato i pacchetti in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], è possibile distribuire i progetti contenenti i pacchetti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Il [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server è un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] che ospita il **SSISDB** database. Nel database vengono archiviati gli oggetti seguenti: pacchetti, progetti, parametri, autorizzazioni, proprietà del server e cronologia operativa.  
  
 Tramite il database **SSISDB** vengono esposte le informazioni sull'oggetto nelle viste pubbliche su cui è possibile eseguire query. Nel database sono inoltre disponibili stored procedure che è possibile chiamare per gestire gli oggetti.  
  
 Prima di poter distribuire i progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, è necessario creare il **SSISDB** catalogo.  
  
 Per una panoramica delle funzionalità del catalogo SSISDB, vedere [catalogo SSIS](../../integration-services/service/ssis-catalog.md).  
  
## Disponibilità elevata  
 Analogamente ad altri database utente, il database **SSISDB** supporta il mirroring del database e la replica. Per ulteriori informazioni su mirroring e replica, vedere [il mirroring del Database & #40; SQL Server & #41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 È anche possibile fornire la disponibilità elevata di SSISDB e il relativo contenuto, rendendo l'utilizzo di SSIS e gruppi di disponibilità AlwaysOn. Per ulteriori informazioni, vedere questo post di blog da Matt Masson, [SSIS con AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873), sul sito Web blogs.msdn.com.  
  
##  <a name="ssms"></a> Server Integration Services in SQL Server Management Studio  
 Quando ci si connette a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] che ospita il **SSISDB** database, vedere i seguenti oggetti in Esplora oggetti:  
  
-   **Database SSISDB**  
  
     Il database **SSISDB** viene visualizzato nel nodo **Database** in Esplora oggetti. È possibile eseguire una query sulle viste e chiamare le stored procedure tramite cui vengono gestiti il server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli oggetti archiviati nel server.  
  
-   **Cataloghi di Integration Services**  
  
     Nel nodo **Cataloghi di Integration Services** sono presenti cartelle per i progetti e gli ambienti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## Attività correlate  
  
-   [Creare il catalogo SSIS](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [Visualizzazione dell'elenco di pacchetti nel server Integration Services](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Distribuire progetti nel server Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md)  
  
-   [Eseguire un pacchetto sul server SSIS mediante SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## Contenuto correlato  
 Post di blog, [SSIS con AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873), sul sito Web blogs.msdn.com.  
  
  