---
title: Configurare notifiche di posta elettronica (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6484a5b978a50ab30cf63d00c48573012ad56b6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077593"
---
# <a name="configure-email-notifications-master-data-services"></a>Configurare notifiche di posta elettronica (Master Data Services)
  Per fare in modo che [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] invii automaticamente messaggi di posta elettronica, è necessario configurare messaggi di posta elettronica di notifica.  
  
### <a name="to-configure-notifications"></a>Per configurare le notifiche  
  
1.  Nella pagina [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Database **di** selezionare il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Nella sezione **Impostazioni sistema** fare clic su **Crea profilo**.  
  
3.  Completare tutti i campi obbligatori. Per altre informazioni, vedere [Finestra di dialogo Crea account e profilo di Posta elettronica database &#40;Gestione configurazione Master Data Services&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md).  
  
4.  Fare clic su **OK**.  
  
    > [!NOTE]  
    >  Dopo avere configurato le notifiche, non è possibile usare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per apportare modifiche. È necessario apportare le modifiche direttamente nel database di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Per altre informazioni, vedere [Oggetti di configurazione di Posta elettronica database](../relational-databases/database-mail/database-mail-configuration-objects.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   Alcune impostazioni di [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] hanno effetto sulle notifiche. È possibile regolare tali impostazioni in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] o direttamente nella tabella Impostazioni sistema del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le notifiche &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)   
 [Risoluzione dei problemi relativi alle notifiche di posta elettronica (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)   
 [Configurare le regole di Business per inviare notifiche &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  