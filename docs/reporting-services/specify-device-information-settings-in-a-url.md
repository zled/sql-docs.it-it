---
title: Specificare impostazioni informazioni dispositivo in un URL | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 09e1655e7945a459cf9d606d24cf7479ee4fc568
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="specify-device-information-settings-in-a-url"></a>Specificare le impostazioni relative alle informazioni sul dispositivo in un URL
  Le impostazioni relative alle informazioni sul dispositivo sono parametri passati a un'estensione per il rendering. Se si usano i metodi del servizio Web ReportServer di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per eseguire il rendering di un report, viene passato un elemento XML **DeviceInfo** come parametro di input. Gli elementi figlio dell'elemento **DeviceInfo** sono specifici delle impostazioni relative alle informazioni sul dispositivo di diverse estensioni per il rendering. È possibile includere le impostazioni relative alle informazioni sul dispositivo in un URL usando la stringa di parametri *rc:tag=value* , dove *tag* è il nome dell'elemento delle impostazioni relative alle informazioni sul dispositivo a cui si accede. Per altre informazioni sulle impostazioni relative alle informazioni sul dispositivo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vedere [Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente imposta il formato del report specificato su JPEG usando l'impostazione relativa alle informazioni sul dispositivo *OutputFormat* dell'estensione per il rendering dell'immagine. Le interruzioni di riga sono state aggiunte per migliorare la leggibilità:  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40; SSRS &#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri URL accesso](../reporting-services/url-access-parameter-reference.md)  
  
  

