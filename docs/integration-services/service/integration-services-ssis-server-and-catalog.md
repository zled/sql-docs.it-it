---
title: Integration Services (SSIS) Server e del catalogo | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 939f31adf1ab0a975bd4339dabab310ef9025049
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-server-and-catalog"></a>Integration Services (SSIS) Server e del catalogo
  Dopo aver progettato e testato i pacchetti in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], è possibile distribuire i progetti contenenti i pacchetti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Il server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui viene ospitato il database di **SSISDB** . Nel database vengono archiviati gli oggetti seguenti: pacchetti, progetti, parametri, autorizzazioni, proprietà del server e cronologia operativa.  
  
 Tramite il database **SSISDB** vengono esposte le informazioni sull'oggetto nelle viste pubbliche su cui è possibile eseguire query. Nel database sono inoltre disponibili stored procedure che è possibile chiamare per gestire gli oggetti.  
  
 Prima di poter distribuire i progetti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è necessario creare il catalogo **SSISDB** .  
  
 Per una panoramica delle funzionalità del catalogo SSISDB, vedere [catalogo SSIS](../../integration-services/service/ssis-catalog.md).  
  
## <a name="high-availability"></a>Disponibilità elevata  
 Analogamente ad altri database utente, il database **SSISDB** supporta il mirroring del database e la replica. Per ulteriori informazioni sul mirroring e replica, vedere [il mirroring del Database &#40; SQL Server &#41; ](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 È anche possibile fornire la disponibilità elevata di SSISDB e il relativo contenuto eseguendo utilizzo di SSIS e i gruppi di disponibilità AlwaysOn. Per ulteriori informazioni, vedere questo post di blog da Matt Masson, [SSIS con AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873), sul sito Web blogs.msdn.com.  
  
##  <a name="ssms"></a> Server Integration Services in SQL Server Management Studio  
 Quando si stabilisce la connessione a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui viene ospitato il database di **SSISDB** , gli oggetti seguenti sono visibili in Esplora oggetti:  
  
-   **Database SSISDB**  
  
     Il database **SSISDB** viene visualizzato nel nodo **Database** in Esplora oggetti. È possibile eseguire una query sulle viste e chiamare le stored procedure tramite cui vengono gestiti il server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli oggetti archiviati nel server.  
  
-   **Cataloghi di Integration Services**  
  
     Nel nodo **Cataloghi di Integration Services** sono presenti cartelle per i progetti e gli ambienti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Visualizzare l'elenco dei pacchetti nel Server Integration Services](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Integration Services (SSIS) di distribuire progetti e pacchetti](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [Eseguire pacchetti di Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>Contenuto correlato  
 Post di blog, [SSIS con AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873), sul sito Web blogs.msdn.com.  
  
  
