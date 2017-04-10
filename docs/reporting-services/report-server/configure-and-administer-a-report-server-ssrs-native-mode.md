---
title: "Configurare e amministrare un server di report (modalit&#224; nativa SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Reporting Services, componenti"
  - "distribuzione [Reporting Services], opzioni per i componenti"
  - "server di report [Reporting Services], opzioni per i componenti"
  - "opzioni di configurazione [Reporting Services]"
  - "administering Reporting Services"
  - "componenti [Reporting Services], configurazione"
  - "configurazione di server [Reporting Services]"
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 51
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 51
---
# Configurare e amministrare un server di report (modalit&#224; nativa SSRS)
  In questo argomento vengono riepilogati gli approcci disponibili per la configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. È inoltre incluso un elenco di argomenti che illustrano come configurare componenti, caratteristiche specifiche o del server. Per configurare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è possibile:  
  
-   Utilizzare Gestione configurazione Reporting Services. Molti degli argomenti di questa sezione contengono informazioni su come configurare caratteristiche specifiche tramite questo strumento.  
  
-   Usare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per personalizzare le proprietà del server, attivare la funzionalità Report personali, attivare i log di traccia e impostare valori predefiniti a livello di sito. Per altre informazioni sulle impostazioni del sito, vedere [Server di report di Reporting Services &#40;modalità nativa&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md). Si noti che è possibile creare ed eseguire uno script che consente di impostare le proprietà del server a livello di programmazione. Per altre informazioni, vedere [Utilizzare script per l'esecuzione di attività di distribuzione e di amministrazione](../../reporting-services/tools/script-deployment-and-administrative-tasks.md) e [Proprietà di sistema del server di report](../Topic/Report%20Server%20System%20Properties.md).  
  
-   Utilizzare Gestione report per concedere autorizzazioni per accedere al server di report. Le autorizzazioni vengono assegnate tramite assegnazioni di ruolo definite per ogni account utente o di gruppo. Per altre informazioni, vedere [Ruoli e autorizzazioni &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md).  
  
-   Modificare i file di configurazione per cambiare le impostazioni delle applicazioni (facoltativo). Per altre informazioni su ogni file e le linee guida per modificarli, vedere [File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## Contenuto della sezione  
 [Configurare gli URL del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Descrive come definire gli URL utilizzati per accedere al servizio del server di report e a Gestione report.  
  
 [Configurare l'account del servizio del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Include indicazioni e procedure per la modifica dell'account e delle password dei servizi.  
  
 [Creare un database del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/create-a-report-server-database-ssrs-configuration-manager.md)  
 Descrive come creare un database del server di report necessario per l'archiviazione di oggetti e metadati del server.  
  
 [Configurare una connessione del database del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Descrive come modificare la stringa di connessione usata dal server di report per la connessione al database.  
  
 [Configurare un server di report per il recapito tramite posta elettronica (Gestione configurazione SSRS)](http://msdn.microsoft.com/it-it/b838f970-d11a-4239-b164-8d11f4581d83)  
 Descrive come configurare un server di report in modo da supportare la distribuzione dei report tramite posta elettronica.  
  
 [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Descrive come configurare un account utente per l'esecuzione automatica dei report.  
  
## Vedere anche  
 [Configurare l'accesso a Generatore report](../../reporting-services/report-server/configure-report-builder-access.md)   
 [File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Sicurezza e protezione di Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Server di report di Reporting Services &#40;modalità nativa&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)  
  
  