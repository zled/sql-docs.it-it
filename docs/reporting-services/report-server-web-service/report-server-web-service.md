---
title: Servizio Web ReportServer | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 5fd4d415e452549e80aa12b9eb1397bf83ce6557
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service"></a>servizio Web ReportServer
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fornisce l'accesso alle funzionalità complete del server di report tramite il servizio Web ReportServer. Il servizio Web ReportServer è un servizio Web XML con un'API SOAP. Il servizio usano SOAP su HTTP e funge da interfaccia di comunicazione tra i programmi client e il server di report. Il servizio Web fornisce due endpoint, uno per l'esecuzione dei report e uno per la gestione dei report, con metodi che espongono le funzionalità del server di report e consentono di creare strumenti personalizzati per qualsiasi parte del ciclo di vita del report.  
  
 Esistono tre modi per sviluppare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applicazioni basate sul servizio Web. È possibile effettuare le operazioni seguenti:  
  
-   Sviluppare applicazioni usando [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK. Per ulteriori informazioni sull'utilizzo di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] per compilare applicazioni di servizio Web, vedere [compilazione di applicazioni tramite il servizio Web e .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Sviluppare applicazioni che usano il **rs** utilità (RS.exe), il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ambiente di script. Con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] script, è possibile eseguire una delle operazioni di servizio Web ReportServer. Per ulteriori informazioni sulla creazione di script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vedere [Script con rs.exe Utilità e il servizio Web](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Sviluppare applicazioni usando qualsiasi set di strumenti di sviluppo abilitato per SOAP. Per ulteriori informazioni, vedere [The Role of SOAP in Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Diagramma di programmazione  
 ![Opzioni di sviluppo del servizio Server Web di report](../../reporting-services/report-server-web-service/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")  
Opzioni di sviluppo dei servizi Web disponibili in Reporting Services  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Metodi del servizio Web ReportServer](../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)  
 Vengono descritti i metodi e le caratteristiche di ogni servizio Web ReportServer.  
  
 [Il ruolo di SOAP in Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Viene fornita una panoramica su SOAP e sul suo utilizzo nei servizi Web ReportServer.  
  
 [L'accesso all'API SOAP](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)  
 Viene descritto il linguaggio WSDL (Web Service Description Language) e vengono forniti gli URL per l'accesso a un file WSDL di Reporting Services.  
  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Sono incluse informazioni sullo sviluppo di applicazioni e servizi Web che chiamano l'API SOAP di Reporting Services.  
  
 [Script con l'utilità rs.exe e il servizio Web](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Viene fornita una panoramica sull'ambiente di scripting [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Riferimento tecnico &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
 È incluso materiale di riferimento specifico dei metodi dei servizi Web ReportServer e dei tipi complessi corrispondenti.  
  
## <a name="user-requirements-for-web-service-development"></a>Requisiti utente per lo sviluppo del servizio Web  
 Per sviluppare applicazioni usando il servizio Web ReportServer, è necessario quanto segue:  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer 5.5 o versione successiva installato in un computer con una connessione Internet e l'accesso al server di report.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK installato in un computer, se si desidera sviluppare e distribuire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applicazioni che usano il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   Una conoscenza approfondita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] caratteristiche e funzionalità.  
  
-   Buona conoscenza di SOAP e [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].  
  
-   Esperienza di sviluppo di un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-linguaggio compatibile, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], se si prevede di utilizzare il [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] come piattaforma di sviluppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio Web ReportServer](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
