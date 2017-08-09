---
title: Impostazioni personali per integrazione di Power BI (portale web) | Documenti Microsoft
ms.date: 05/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 91be669329ea6d822dcc489584d649e5a01ce018
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="my-settings-for-power-bi-integration-web-portal"></a>Impostazioni personali per Integrazione di Power BI (portale Web)

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../includes/ssrs-appliesto-sql2016-xpreview.md)]

La pagina **Impostazioni personali** di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] viene usata dai singoli utenti per gestire l'accesso con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Quando si eseguono i passaggi per aggiungere un elemento del report, viene richiesto automaticamente di eseguire l'accesso.  Tuttavia, è possibile usare la pagina **Impostazioni personali** per accedere manualmente o per disconnettersi.  Se l'opzione del menu **Impostazioni personali** non è visibile, il server di report non è stato integrato con  [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Per altre informazioni, vedere [Integrazione del server di report e di Power BI &#40;Gestione configurazione&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>Perché eseguire l'accesso  
 Quando si accede, viene stabilita una relazione tra l'account utente [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e l'account [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  L'accesso crea un token di sicurezza valido per 90 giorni. Se il token scade e sono presenti elementi bloccati di Power BI, verrà visualizzata una notifica.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
I riquadri dei dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] non verranno aggiornati fino a quando non si accede nuovamente mediante **Impostazioni personali**.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Dopo aver eseguito l'accesso, verrà creato un nuovo token di sicurezza.  Dopo l'accesso, viene iniziato l'aggiornamento dei riquadri dei dashboard sulla base delle pianificazioni configurate in precedenza.  

## <a name="next-steps"></a>Passaggi successivi

[Integrazione di Power BI Report Server](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Aggiungere elementi di Reporting Services ai dashboard di Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Dashboard in Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[Portale Web](../reporting-services/web-portal-ssrs-native-mode.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
