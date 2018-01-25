---
title: Introduzione a SQL Server Management Studio per BI | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.assetid: ffaa77b7-03d0-4d7a-aa42-c5091a4f2ceb
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4fc26ef0feb4ff86087bd0ddc571299621207464
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="introduction-to-sql-server-management-studio-for-business-intelligence"></a>Introduzione a SQL Server Management Studio per Business Intelligence
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Per accedere, configurare, gestire e amministrare [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] e [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)], usare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]. Sebbene le tre tecnologie di Business Intelligence si basino tutte su [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], le attività amministrative associate a ciascuna di esse sono leggermente diverse.  
  
> [!NOTE]  
> Per creare e modificare soluzioni [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)]e [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] , utilizzare [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)]e non [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)] è un ambiente di sviluppo basato su [!INCLUDE[msCoName](../includes/msconame_md.md)][!INCLUDE[vsprvs](../includes/vsprvs_md.md)].  
  
## <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Gestione di soluzioni Analysis Services tramite SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] consente di gestire oggetti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] , ad esempio eseguendo backup ed elaborando oggetti.  
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] include un progetto script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] in cui è possibile sviluppare e salvare script creati in MDX (Multidimensional Expressions), DMX (Data Mining Extensions) e XMLA (XML per Analysis). Usare i progetti script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] per eseguire attività di gestione o ricreare oggetti, ad esempio database e cubi in istanze di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] . È possibile, ad esempio, sviluppare uno script XMLA in un progetto script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] per la creazione diretta di nuovi oggetti in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] esistente. È possibile salvare i progetti script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] come parte di una soluzione e integrarli con il controllo del codice sorgente.  
  
Per altre informazioni su come usare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], vedere [Sviluppo e implementazione tramite SQL Server Management Studio](http://msdn.microsoft.com/en-us/c4f5a06b-e2e4-4660-a3a8-6fd356742c02).  
  
## <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Gestione di soluzioni Integration Services tramite SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] consente di usare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] per gestire i pacchetti e monitorare i pacchetti in esecuzione. È inoltre possibile utilizzare [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] per organizzare pacchetti in cartelle, eseguire pacchetti, importare ed esportare pacchetti, eseguire la migrazione di pacchetti DTS (Data Transformation Services) e aggiornare pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] .  
  
## <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Gestione di progetti di Reporting Services tramite SQL Server Management Studio  
Utilizzare SQL Server Management Studio per abilitare le funzionalità di Reporting Services, amministrare il server e i database e gestire ruoli e processi.  
  
Lo strumento consente di gestire pianificazioni condivise tramite la cartella Pianificazioni condivise e di gestire i database del server di report (ReportServer e ReportServerTempdb). È inoltre possibile creare un ruolo RSExecRole nel database di sistema Master quando si sposta un database del server di report in un'istanza nuova o diversa del Motore di database SQL Server ([!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] [!INCLUDE[ssDE](../includes/ssde_md.md)]). Per ulteriori informazioni su queste attività, vedere gli argomenti seguenti:  
  
-   [Procedure per SQL Server Management Studio](http://msdn.microsoft.com/en-us/60685458-9108-47bf-820a-5e7db454d408)  
  
-   [Amministrazione del database del server di report](http://msdn.microsoft.com/en-us/97b2e1b5-3869-4766-97b9-9bf206b52262)  
  
-   [Procedura: Creazione di RSExecRole](http://msdn.microsoft.com/en-us/7ac17341-df7e-4401-870e-652caa2859c0)  
  
Per gestire il server è inoltre possibile abilitare e configurare numerose funzionalità, configurare le impostazioni predefinite del server e gestire ruoli e processi. Per ulteriori informazioni su queste attività, vedere gli argomenti seguenti:  
  
-   [Procedura: Impostazione delle proprietà di un server di report (Management Studio)](http://msdn.microsoft.com/en-us/1ed0f84b-b12a-4e49-b65c-a11a99f9093f)  
  
-   [Procedura: Creazione, eliminazione o modifica di un ruolo (Management Studio)](http://msdn.microsoft.com/en-us/3d1d56e6-a283-44a7-8417-36cb4d2c74d1)  
  
-   [Attivazione e disabilitazione della stampa sul lato client per Reporting Services](http://msdn.microsoft.com/en-us/0e709c96-7517-4547-8ef6-5632f8118524)  
  
## <a name="see-also"></a>Vedere anche  
[Sviluppo e implementazione tramite SQL Server Management Studio](http://msdn.microsoft.com/en-us/132ed779-3ec8-4734-9698-802116d1b017)  
[Reporting Services in SQL Server Data Tools](http://msdn.microsoft.com/en-us/0903c7b2-ac59-45f1-b7d0-922ecd9d76f8)  
  
