---
title: Integration Services Server (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 67a74b8b9958eb52426a4f2bc8f36cd14c005f87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074997"
---
# <a name="integration-services-ssis-server"></a>Server Integration Services (SSIS)
  Dopo aver progettato e testato i pacchetti in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], è possibile distribuire i progetti contenenti i pacchetti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Il server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui viene ospitato il database di `SSISDB`. Nel database vengono archiviati gli oggetti seguenti: pacchetti, progetti, parametri, autorizzazioni, proprietà del server e cronologia operativa.  
  
 Tramite il database `SSISDB` vengono esposte le informazioni sull'oggetto nelle viste pubbliche su cui è possibile eseguire query. Nel database sono inoltre disponibili stored procedure che è possibile chiamare per gestire gli oggetti.  
  
 Prima di poter distribuire i progetti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è necessario creare il catalogo `SSISDB`.  
  
 Per una panoramica della funzionalità del catalogo SSISDB, vedere [Catalogo SSISDB](ssis-catalog.md).  
  
## <a name="high-availability"></a>Disponibilità elevata  
 Analogamente ad altri database utente, il `SSISDB` database supporta il mirroring del database e la replica. Per altre informazioni sul mirroring e la replica, vedere [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 È inoltre possibile fornire la disponibilità elevata di SSISDB e i relativi contenuti utilizzando i gruppi di disponibilità SSIS e AlwaysOn. Per ulteriori informazioni, vedere il post sul blog di Matt Masson relativo a [SSIS con AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873)sul sito Web blogs.msdn.com.  
  
##  <a name="ssms"></a> Server Integration Services in SQL Server Management Studio  
 Quando si stabilisce la connessione a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database `SSISDB`, gli oggetti seguenti sono visibili in Esplora oggetti:  
  
-   **Database SSISDB**  
  
     Il `SSISDB` database viene visualizzato sotto la **database** nodo in Esplora oggetti. È possibile eseguire una query sulle viste e chiamare le stored procedure tramite cui vengono gestiti il server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli oggetti archiviati nel server.  
  
-   **Cataloghi di Integration Services**  
  
     Nel nodo **Cataloghi di Integration Services** sono presenti cartelle per i progetti e gli ambienti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Creare il catalogo SSIS](../create-the-ssis-catalog.md)  
  
-   [Visualizzare l'elenco di pacchetti nel server Integration Services](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Distribuire progetti nel server Integration Services](../deploy-projects-to-integration-services-server.md)  
  
-   [Eseguire un pacchetto sul server SSIS mediante SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>Contenuto correlato  
 Intervento sul blog relativo a [SSIS con AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873)sul sito Web blogs.msdn.com.  
  
  
