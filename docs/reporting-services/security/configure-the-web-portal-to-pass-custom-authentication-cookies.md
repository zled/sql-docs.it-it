---
title: Configurare il portale Web per passare i cookie di autenticazione personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 0f1131c191fa64c6dc6f2a074a9cd5db7a8b0e1b
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="configure-the-web-portal-to-pass-custom-authentication-cookies"></a>Configurare il portale Web per il passaggio di cookie di autenticazione personalizzati

Se si utilizza un'estensione di autenticazione personalizzato, è necessario configurare il portale web per la trasmissione di cookie di autenticazione personalizzati. In caso contrario, il portale web verrà trasmessi solo i cookie tramite richieste HTTP specifiche per il server di report. Se si desidera trasmettere ulteriori cookie, è necessario modificare il file RSReportServer.Config.

## <a name="modifying-the-rsreportserverconfig-file"></a>Modifica del file RSReportServer.config

È possibile abilitare il [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] per trasmettere ulteriori cookie al server di report mediante l'aggiunta di un \< **PassThroughCookies**> elemento per le impostazioni di configurazione del portale web nel file RSReportServer. config. La trasmissione di cookie aggiuntivi è utile in una soluzione di autenticazione Single Sign-On che, insieme ai cookie di autenticazione del server di report, richiede anche cookie di un sistema di autenticazione di terze parti.

Per abilitare ulteriori cookie deve essere trasmesso tramite richieste HTTP quando si usa il portale web, impostare gli elementi seguenti nel file RSReportServer. config:
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a>Vedere anche

[Autenticazione con il server di report](../../reporting-services/security/authentication-with-the-report-server.md)   
[File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Panoramica sulle estensioni di sicurezza](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
[Configurare e amministrare un Server di Report &#40; Modalità nativa SSRS &#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
Ulteriori domande? [Provare il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
