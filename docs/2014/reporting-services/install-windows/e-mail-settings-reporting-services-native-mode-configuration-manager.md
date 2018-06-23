---
title: Impostazioni di posta elettronica - Gestione configurazione (modalità nativa SSRS) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 96e3318045d058a7d953684fa05bfd72aed9bd69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168687"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>Impostazioni di posta elettronica - Gestione configurazione (modalità nativa SSRS)
  Utilizzare questa pagina per specificare le impostazioni SMTP (Simple Mail Transport Protocol) che consentono il recapito tramite posta elettronica dal server di report. È possibile utilizzare l'estensione per il recapito tramite posta elettronica del server di report per distribuire report o notifiche di elaborazione dei report utilizzando sottoscrizioni tramite posta elettronica. L'estensione per il recapito tramite posta elettronica del server di report richiede un server SMTP e un indirizzo di posta elettronica da utilizzare nel campo Da.  
  
 Le impostazioni di configurazione aggiuntive, incluse quelle che limitano la disponibilità di estensioni per il rendering e gli host del server, possono essere utilizzate per personalizzare ulteriormente le sottoscrizioni alla posta elettronica. Non è possibile specificare queste impostazioni sono presenti il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Per configurare le impostazioni aggiuntive, è necessario modificare manualmente il file RSReportServer.config. Per altre informazioni, vedere [configurare un Server di Report per il recapito tramite posta elettronica &#40;Gestione configurazione SSRS&#41; ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) e [del file di configurazione di Reporting Services](../report-server/reporting-services-configuration-files.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione In linea.  
  
 Per aprire questa pagina, avviare Gestione configurazione Reporting Services e fare clic su **impostazioni di posta elettronica** nel riquadro di spostamento. Per altre informazioni, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Opzioni  
 **Indirizzo mittente**  
 Consente di specificare l'indirizzo di posta elettronica da utilizzare nel campo Da di un messaggio di posta elettronica generato. È necessario specificare un account utente che abbia l'autorizzazione per l'invio di posta elettronica dal server SMTP.  
  
 **Metodo di recapito SMTP corrente**  
 Consente di specificare che il reindirizzamento della posta elettronica del server di report viene eseguito tramite un server SMTP. Si tratta dell'unico metodo di recapito che è possibile specificare in Gestione configurazione Reporting Services.  
  
 In alternativa a questo metodo, è possibile utilizzare una directory di prelievo del servizio SMTP locale, se non è disponibile un servizio SMTP di rete. Per specificare una directory di prelievo del servizio SMTP locale, è necessario modificare il file RSReportServer.config. Se viene modificato il file di configurazione per l'utilizzo di una directory di prelievo del servizio SMTP locale, Gestione configurazione Reporting Services imposterà il **metodo di recapito** opzione *personalizzati* per indicare che il recapito metodo viene specificato nel file di configurazione.  
  
 Nel file di configurazione, il metodo di recapito viene impostato tramite il `SendUsing` impostazione di configurazione. Per ulteriori informazioni su come specificare il `SendUsing` ll'impostazione, vedere [configurare un Server di Report per il recapito tramite posta elettronica &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **Server SMTP**  
 Consente di specificare il server o il gateway SMTP da utilizzare. È possibile utilizzare un server locale o un server SMTP nella rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un Server di Report per il recapito tramite posta elettronica &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Argomenti della Guida F1 di Gestione configurazione di Reporting Services &#40;modalità nativa SSRS&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  