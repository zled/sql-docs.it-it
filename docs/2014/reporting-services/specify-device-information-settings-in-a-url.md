---
title: Specificare le impostazioni relative alle informazioni sul dispositivo in un URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: dacc371522447f3af056fcde3a48b6d4fca886c9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169825"
---
# <a name="specify-device-information-settings-in-a-url"></a>Specificare le impostazioni relative alle informazioni sul dispositivo in un URL
  Le impostazioni relative alle informazioni sul dispositivo sono parametri passati a un'estensione per il rendering. Se si utilizzano i metodi del servizio Web ReportServer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per eseguire il rendering di un report, come parametro di input viene passato un elemento `DeviceInfo` XML. Gli elementi figlio del `DeviceInfo` elemento sono specifici per le impostazioni informazioni dispositivo delle estensioni di rendering diverso. È possibile includere le impostazioni relative alle informazioni sul dispositivo in un URL usando la stringa di parametri *rc:tag=value* , dove *tag* è il nome dell'elemento delle impostazioni relative alle informazioni sul dispositivo a cui si accede. Per ulteriori informazioni sulle impostazioni informazioni dispositivo [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vedere [passando Device Information Settings alle estensioni di Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente imposta il formato del report specificato su JPEG usando l'impostazione relativa alle informazioni sul dispositivo *OutputFormat* dell'estensione per il rendering dell'immagine. Le interruzioni di riga sono state aggiunte per migliorare la leggibilità:  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso con URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](url-access-parameter-reference.md)  
  
  