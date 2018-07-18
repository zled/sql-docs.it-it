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
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a77fe212fc4637c384a8328aa1094db91b9a8d11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255573"
---
# <a name="specify-device-information-settings-in-a-url"></a>Specificare le impostazioni relative alle informazioni sul dispositivo in un URL
  Le impostazioni relative alle informazioni sul dispositivo sono parametri passati a un'estensione per il rendering. Se si utilizzano i metodi del servizio Web ReportServer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per eseguire il rendering di un report, come parametro di input viene passato un elemento `DeviceInfo` XML. Gli elementi figlio del `DeviceInfo` sono specifici per le impostazioni informazioni dispositivo delle estensioni di rendering diverso. È possibile includere le impostazioni relative alle informazioni sul dispositivo in un URL usando la stringa di parametri *rc:tag=value* , dove *tag* è il nome dell'elemento delle impostazioni relative alle informazioni sul dispositivo a cui si accede. Per altre informazioni sulle impostazioni informazioni dispositivo [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vedere [passando Device Information Settings alle estensioni di Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente imposta il formato del report specificato su JPEG usando l'impostazione relativa alle informazioni sul dispositivo *OutputFormat* dell'estensione per il rendering dell'immagine. Le interruzioni di riga sono state aggiunte per migliorare la leggibilità:  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](url-access-parameter-reference.md)  
  
  
