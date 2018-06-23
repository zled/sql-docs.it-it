---
title: Configurare e amministrare un server di report (modalità nativa SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 50
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: d5a004993ab886151ce9e3f5e3f7b2a2970f60d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067119"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a>Configurare e amministrare un server di report (modalità nativa SSRS)
  In questo argomento vengono riepilogati gli approcci disponibili per la configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. È inoltre incluso un elenco di argomenti che illustrano come configurare componenti, caratteristiche specifiche o del server. Per configurare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è possibile:  
  
-   Utilizzare Gestione configurazione Reporting Services. Molti degli argomenti di questa sezione contengono informazioni su come configurare caratteristiche specifiche tramite questo strumento.  
  
-   Usare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per personalizzare le proprietà del server, attivare la funzionalità Report personali, attivare i log di traccia e impostare valori predefiniti a livello di sito. Per ulteriori informazioni sulle impostazioni del sito, vedere [del Server di Report di Reporting Services &#40;modalità nativa&#41; ](reporting-services-report-server-native-mode.md) per Management Studio. Si noti che è possibile creare ed eseguire uno script che consente di impostare le proprietà del server a livello di programmazione. Per altre informazioni, vedere [la distribuzione di Script e le attività amministrative](../tools/script-deployment-and-administrative-tasks.md) e [proprietà di sistema di Server di Report](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).  
  
-   Utilizzare Gestione report per concedere autorizzazioni per accedere al server di report. Le autorizzazioni vengono assegnate tramite assegnazioni di ruolo definite per ogni account utente o di gruppo. Per altre informazioni, vedere [Ruoli e autorizzazioni &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).  
  
-   Modificare i file di configurazione per cambiare le impostazioni delle applicazioni (facoltativo). Per ulteriori informazioni su ogni file e le linee guida per la modifica, vedere [del file di configurazione di Reporting Services](reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Configurare gli URL del server di report &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Descrive come definire gli URL utilizzati per accedere al servizio del server di report e a Gestione report.  
  
 [Configurare l'Account del servizio ReportServer &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Include indicazioni e procedure per la modifica dell'account e delle password dei servizi.  
  
 [Creare un database del Server di Report &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Descrive come creare un database del server di report necessario per l'archiviazione di oggetti e metadati del server.  
  
 [Configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Descrive come modificare la stringa di connessione usata dal server di report per la connessione al database.  
  
 [Configurare un Server di Report per il recapito tramite posta elettronica &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Descrive come configurare un server di report in modo da supportare la distribuzione dei report tramite posta elettronica.  
  
 [Configurare l'Account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Descrive come configurare un account utente per l'esecuzione automatica dei report.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare l'accesso a Generatore Report](configure-report-builder-access.md)   
 [File di configurazione di Reporting Services](reporting-services-configuration-files.md)   
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Sicurezza e protezione di Reporting Services](../security/reporting-services-security-and-protection.md)   
 [Server di report di Reporting Services &#40;modalità nativa&#41;](reporting-services-report-server-native-mode.md)  
  
  