---
title: "Configurare Gestione report per il passaggio di cookie di autenticazione personalizzati | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "autenticazione [Reporting Services]"
  - "estensioni [Reporting Services], sicurezza personalizzata"
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# Configurare Gestione report per il passaggio di cookie di autenticazione personalizzati
  Se si sta utilizzando un'estensione di autenticazione personalizzata, è necessario configurare il [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] per la trasmissione di cookie di autenticazione personalizzati. In caso contrario, il [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] trasmetterà i cookie solo mediante richieste HTTP specifiche del server di report. Se si desidera trasmettere ulteriori cookie, è necessario modificare il file RSReportServer.Config.  
  
## Modifica del file RSReportServer.config  
 È possibile consentire al [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] di trasmettere ulteriori cookie al server di report aggiungendo un elemento \<**PassThroughCookies**> alle impostazioni di configurazione del [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] nel file RSReportServer.config. La trasmissione di cookie aggiuntivi è utile in una soluzione di autenticazione Single Sign-On che, insieme ai cookie di autenticazione del server di report, richiede anche cookie di un sistema di autenticazione di terze parti.  
  
 Per consentire la trasmissione di ulteriori cookie tramite richieste HTTP quando si usa il [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)], impostare gli elementi seguenti nel file RSReportServer.config:  
  
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
  
## Vedere anche  
 [Autenticazione con il server di report](../../reporting-services/security/authentication-with-the-report-server.md)   
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Panoramica sulle estensioni di sicurezza](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
 [Configurare e amministrare un server di report &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  