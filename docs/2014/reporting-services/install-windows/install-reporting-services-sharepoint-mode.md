---
title: Installazione in modalità SharePoint (SharePoint 2010 e SharePoint 2013) di Reporting Services | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: f0e75a75ffb14f720f2b421d659fa6142b579019
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054496"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Installazione della modalità SharePoint di Reporting Services (SharePoint 2010 e SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint è una raccolta di componenti server che forniscono la generazione del report e il recapito, in base alle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[msCoName](../../includes/msconame-md.md)] prodotti SharePoint.  
  
 L'esecuzione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint fornisce [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] e funzionalità di avvisi dati. Per altre informazioni sulle funzionalità in modalità SharePoint, vedere la sezione "Supporto della funzionalità e differenze di comportamento in base alla modalità server" in [Server di report di Reporting Services](../reporting-services-report-server.md).  
  
 Esistono due installazioni fondamentali necessarie per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint:  
  
|Installazione|Description|  
|------------------|-----------------|  
|Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aggiuntivo per prodotti SharePoint.|Il componente aggiuntivo installa le pagine dell'interfaccia utente (Interfaccia utente) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e funzionalità in un server Web front-end di SharePoint. Le funzionalità dell'interfaccia utente includono [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], pagine dell'amministrazione in Amministrazione centrale SharePoint, pagine delle funzionalità utilizzate nelle raccolte documenti di SharePoint e pagine di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avvisi dati.|  
|Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server di report installato in modalità SharePoint|Il server di report gestisce l'elaborazione di dati e report e del rendering, oltre all'elaborazione delle sottoscrizioni e degli avvisi dati. Il server di report della modalità SharePoint è configurato e installato come un servizio Shared SharePoint.|  
  
 Per installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], utilizzare i supporti di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per istruzioni su scenari di distribuzione avanzati, vedere [elenco di controllo distribuzione: Reporting Services, Power View e PowerPivot per SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) e [distribuzione elenco di controllo: installare Reporting Services in un'esistente Farm di SharePoint](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Combinazioni supportate di SharePoint e Server Reporting Services e componente aggiuntivo &#40;SQL Server 2014&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Installare Reporting Services SharePoint Mode for SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [Installare la modalità SharePoint di Reporting Services per SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Installare o disinstallare il componente aggiuntivo di servizi Reporting per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Dove trovare il componente aggiuntivo di Reporting Services per prodotti SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Aggiungere un ulteriore Server di Report a una Farm di &#40;con scalabilità orizzontale SSRS&#41;](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Aggiungere un ulteriore front-end Web di Reporting Services a una farm](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Configurare la posta elettronica per l'applicazione di servizio di Reporting Services &#40;SharePoint 2010 e SharePoint 2013&#41;](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Provisioning di sottoscrizioni e avvisi per le applicazioni di servizio SSRS](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Servizio di Token delle attestazioni a Windows &#40;C2WTS&#41; e Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura e flusso di lavoro degli avvisi dati](../reporting-services-data-alerts.md#AlertingWF)   
 [Gestione avvisi dati per gli amministratori di avvisi](../data-alert-manager-for-alerting-administrators.md)  
  
  