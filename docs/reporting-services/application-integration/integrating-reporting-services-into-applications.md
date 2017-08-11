---
title: Integrazione di Reporting Services nelle applicazioni | Documenti Microsoft
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
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
caps.latest.revision: 57
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8a1cabc088c7c0ec6c69c8290549e035a4cec7bb
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-into-applications"></a>Integrazione di Reporting Services nelle applicazioni
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è una piattaforma di creazione di report aperta ed estendibile progettata per fornire agli sviluppatori un set completo di API per lo sviluppo di soluzioni.  
  
 Sono disponibili tre opzioni per l'integrazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni personalizzate: servizio Web ReportServer, anche noto come il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] i controlli ReportViewer per l'API SOAP [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]e l'accesso con URL. Ogni opzione fornisce un approccio diverso per l'integrazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni.  
  
## <a name="report-server-web-service"></a>servizio Web ReportServer  
 Il servizio Web ReportServer è l'interfaccia principale per lo sviluppo in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Sia che si sviluppi codice per gestire il catalogo di report o che si sviluppi codice per il rendering dei report in un formato supportato, il servizio Web espone tutti i metodi necessari per integrare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni. Un esempio di tale applicazione è Gestione Report, incluso in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; viene utilizzato il servizio Web per gestire il database del server di report.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Controlli ReportViewer per Visual Studio  
 I controlli ReportViewer inclusi in [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] vengono utilizzati per l'integrazione delle funzionalità di visualizzazione dei report nelle applicazioni. Sono disponibili due controlli, uno per le applicazioni basate su Windows Form e uno per le applicazioni Web Form. Ogni controllo fornisce funzionalità per la visualizzazione dei report distribuiti in un server di report e consente di eseguire il rendering dei report presenti in un ambiente in cui non è stato installato un server di report.  
  
## <a name="url-access"></a>Accesso con URL  
 L'accesso con URL rappresenta un'altra opzione per l'integrazione delle funzionalità di visualizzazione dei report nelle applicazioni se non sono disponibili i controlli ReportViewer. L'accesso con URL è inoltre utile per inviare agli utenti collegamenti ai report tramite posta elettronica.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Integrazione di Reporting Services tramite SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 Viene descritto come integrare le funzionalità di navigazione e gestione dei report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni aziendali esistenti utilizzando il servizio Web ReportServer.  
  
 [Integrazione di Reporting Services utilizzando i controlli ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Viene descritto come integrare le funzionalità di visualizzazione dei report nelle applicazioni esistenti utilizzando i controlli ReportViewer.  
  
 [Integrazione di Reporting Services tramite l'accesso con URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 Viene descritto come integrare le funzionalità di navigazione dei report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni esistenti utilizzando l'accesso con URL.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione report &#40; Modalità nativa SSRS &#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Scelta tra SOAP e l'accesso con URL](../../reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)   
 [Servizio Web ReportServer](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
