---
title: Configurazione e amministrazione di un server di report di SQL Server Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: b521a0a2198d74c8766f18fb8d7a199b25005efe
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="configuration-and-administration-of-a-sql-server-reporting-services-report-server"></a>Configurazione e amministrazione di un server di report di SQL Server Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services è una piattaforma di creazione di report basata su server che fornisce una gamma completa di strumenti e servizi pronti per l'uso che consentono di creare, distribuire e gestire report per l'organizzazione nonché di programmare caratteristiche che consentono di estendere e personalizzare la funzionalità di report. È possibile integrare l'ambiente di gestione dei report con un prodotto SharePoint per sfruttare i vantaggi dell'utilizzo dell'ambiente di collaborazione fornito dai siti di SharePoint.

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

Nelle sezioni seguenti per comprendere i concetti, scenari di distribuzione, procedure e informazioni per l'integrazione dell'ambiente di Reporting Services con un prodotto o tecnologia SharePoint.  
  
-   Opzioni di menu in una raccolta documenti di SharePoint  
  
    -   [Gestione avvisi dati per utenti di SharePoint](../../reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [Create and Manage Subscriptions for SharePoint Mode Report Servers](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [Aggiornare le credenziali nelle origini dati dei report da un sito di SharePoint](../../reporting-services/report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [Gestire set di dati condivisi](../../reporting-services/report-data/manage-shared-datasets.md)  
  
    -   [Impostazione dei parametri per un report pubblicato &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [Impostare le opzioni di elaborazione &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
    -   [Opzioni di aggiornamento cache &#40;Gestione report&#41;](http://msdn.microsoft.com/library/227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6)  
  
-   [Funzionalità della raccolta siti di Reporting Services](../../reporting-services/report-server-sharepoint/site-collection-features-reporting-services.md)  
  
-   [Attivare le funzionalità di integrazione per Power View e server di report in SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)  
  
-   [Funzionalità e impostazioni del sito di Reporting Services &#40;modalità SharePoint&#41;](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)  
  
-   [Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  
  
-   [Aggiungere i tipi di contenuto di Reporting Services a una libreria SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [Report in modalità locale e con connessione nel visualizzatore di report &#40;Reporting Services in modalità SharePoint&#41;](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md)  
  
-   [Caricare documenti in una raccolta di SharePoint &#40;Reporting Services in modalità SharePoint&#41;](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [Impostare le opzioni di elaborazione &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 Per ulteriori informazioni su Reporting Services, vedere [Reporting Services](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione in linea. Per informazioni su altri componenti, strumenti e risorse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere la [Documentazione online di SQL Server](../../sql-server/sql-server-technical-documentation.md).  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
