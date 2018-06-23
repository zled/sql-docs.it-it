---
title: Impostare il Database e il sito Web per Master Data Services | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 09e3e92d20182be2feb1c357cc1d3f518c55e5ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157997"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Configurare il database e il sito Web per Master Data Services
  Usare la [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per impostare il database e il sito Web per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)  
  
 Per configurare il database e il sito Web, completare le attività seguenti.  
  
1.  Creare un database mediante il **configurazione del Database** pagina [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Per informazioni, vedere [pagina Configurazione Database &#40;Gestione configurazione Master Data Services&#41; ](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) e [procedura guidata Crea Database &#40;Gestione configurazione Master Data Services&#41; ](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Creare un nuovo sito Web, selezionare il sito Web predefinito o selezionare un altro sito Web esistente, utilizzando il **configurazione Web** pagina [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Associare quindi il database MDS all'applicazione Web selezionata o creata.  
  
     Per informazioni, vedere [pagina configurazione Web &#40;Gestione configurazione Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) e [finestra di dialogo Crea sito Web &#40;Gestione configurazione Master Data Services&#41; ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  (Facoltativo) Abilitare l'integrazione con Data Quality Services usando la **configurazione Web** pagina [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Per altre informazioni, vedere [pagina configurazione Web &#40;Gestione configurazione Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) e [Enable Data Quality Services Integration with Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 È anche possibile usare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per specificare le impostazioni per le applicazioni e servizi web associati al database MDS. Ad esempio, è possibile specificare la frequenza con cui i dati vengono caricati o quella con cui viene inviata la posta elettronica della convalida. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Master Data Services Database](../../2014/master-data-services/master-data-services-database.md)   
 [Applicazione Web Gestione dati master](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  