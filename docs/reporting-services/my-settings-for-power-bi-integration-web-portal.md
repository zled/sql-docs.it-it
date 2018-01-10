---
title: Impostazioni personali per l'integrazione di Power BI (portale Web) | Microsoft Docs
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
caps.latest.revision: "15"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b2a72fe0100b29daf1a1eaa07172dd88eeacdcab
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="my-settings-for-power-bi-integration-web-portal"></a>Impostazioni personali per Integrazione di Power BI (portale Web)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

La pagina **Impostazioni personali** di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] viene usata dai singoli utenti per gestire l'accesso con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Quando si eseguono i passaggi per aggiungere un elemento del report, viene richiesto automaticamente di eseguire l'accesso.  Tuttavia, è possibile usare la pagina **Impostazioni personali** per accedere manualmente o per disconnettersi.  Se l'opzione di menu **Impostazioni personali** non è visibile, il server di report non è stato integrato con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Per altre informazioni, vedere [Integrazione del server di report e di Power BI &#40;Gestione configurazione&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>Perché eseguire l'accesso

 Quando si accede, viene stabilita una relazione tra l'account utente [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e l'account [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  L'accesso crea un token di sicurezza valido per 90 giorni. Se il token scade e sono presenti elementi bloccati di Power BI, verrà visualizzata una notifica.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
I riquadri dei dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] non verranno aggiornati fino a quando non si accede nuovamente mediante **Impostazioni personali**.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Dopo aver eseguito l'accesso, verrà creato un nuovo token di sicurezza.  Dopo l'accesso, viene iniziato l'aggiornamento dei riquadri dei dashboard sulla base delle pianificazioni configurate in precedenza.  

## <a name="next-steps"></a>Passaggi successivi

[Integrazione del server di report di Power BI](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Aggiungere elementi di Reporting Services ai dashboard di Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Dashboard in Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[Portale Web](../reporting-services/web-portal-ssrs-native-mode.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
