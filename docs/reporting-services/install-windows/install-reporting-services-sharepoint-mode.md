---
title: "Installare Reporting Services in modalità SharePoint | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b2c77f21304b04b5349691b6c464026fe944a4eb
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="install-reporting-services-sharepoint-mode"></a>Installare la modalità SharePoint di Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint abilita la creazione e la visualizzazione dei report nelle raccolte documenti, il recapito di report della sottoscrizione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] con la posta elettronica,  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], gli avvisi dati e le funzionalità di gestione report, tutto in un'unica distribuzione basata su [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint. Per altre informazioni sulle funzionalità in modalità SharePoint, vedere la sezione "Supporto della funzionalità e differenze di comportamento in base alla modalità server" in [Server di report di Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md).  
  
 Ci sono due componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] principali da installare per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint:  
  
|Installazione|Descrizione|  
|------------------|-----------------|  
|**Server di report:** il server di report di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installato in modalità SharePoint|Il server di report gestisce l'elaborazione di dati e report e del rendering, oltre all'elaborazione delle sottoscrizioni e degli avvisi dati. Il server di report in modalità SharePoint è progettato e installato come un servizio condiviso SharePoint.<br /><br /> **Procedura:** usare i supporti di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per installare il server di report.|  
|**Add-in:** The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, **rssharepoint.msi**.|Il componente aggiuntivo installa le pagine dell'interfaccia utente (Interfaccia utente) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e funzionalità in un server Web front-end di SharePoint. Le funzionalità dell'interfaccia utente includono [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], pagine dell'amministrazione in Amministrazione centrale SharePoint, pagine delle funzionalità utilizzate nelle raccolte documenti di SharePoint e pagine di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avvisi dati.<br /><br /> **Procedura:**  il componente aggiuntivo può essere installato con un download Web o dai supporti di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per altre, vedere [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Combinazioni supportate di SharePoint, server Reporting Services e componente aggiuntivo &#40;SQL Server 2016&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Installare il primo server di report in modalità SharePoint](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Aggiungere un ulteriore server di report a una farm &#40;con scalabilità orizzontale SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Aggiungere un ulteriore front-end Web di Reporting Services a una farm](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Configurare le impostazioni di posta elettronica per l'applicazione di servizio Reporting Services &#40;SharePoint 2013 e SharePoint 2016&#41;](http://msdn.microsoft.com/en-us/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [Provisioning di sottoscrizioni e avvisi per le applicazioni di servizio SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Attestazioni per il servizio token Windows &#40;c2WTS&#41; e Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura e flusso di lavoro degli avvisi dati](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [Gestione avvisi dati per gli amministratori di avvisi](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  
  
  

