---
title: "Abilitare l&#39;integrazione di Data Quality Services con Master Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# Abilitare l&#39;integrazione di Data Quality Services con Master Data Services
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] la funzionalità di corrispondenza viene fornita da Data Quality Services (DQS). Questa funzionalità deve essere abilitata per essere utilizzata.  
  
## Prerequisiti  
  
-   È necessario che siano disponibili un database e un'applicazione Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
-   La funzionalità Data Quality Services e il client Data Quality devono essere installati nella stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database MDS. Per altre informazioni, vedere [Installare Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### Per abilitare l'integrazione con Data Quality Services  
  
1.  Aprire [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Nel riquadro sinistro fare clic su **Configurazione Web**.  
  
3.  Nella pagina **Configurazione Web** selezionare il sito Web e l'applicazione Web.  
  
4.  Nella sezione **Abilita integrazione DQS** fare clic su **Abilitare l'integrazione con Data Quality Services**.  
  
5.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
## Vedere anche  
 [Corrispondenza Data Quality nel componente aggiuntivo MDS per Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Componente aggiuntivo Master Data Services per Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Installazione di Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  