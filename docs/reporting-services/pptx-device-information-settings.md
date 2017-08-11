---
title: PPTX Device Information Settings | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 09/11/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- render
- powerpoint
- pptx
- export
ms.assetid: 4dc2045f-8025-41a3-8f9d-5635fb24cf4a
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3aa67165e961e76569daadff1fc610c4d16a1e63
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="pptx-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo PPTX
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering dei report di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nel formato PPTX.  
  
|Impostazione|Value|  
|-------------|-----------|  
|**Colonne**|Numero di colonne da impostare per il report. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**ColumnSpacing**|Spaziatura delle colonne da impostare per il report. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**DpiX**|Risoluzione orizzontale dell'immagine di output. Il valore predefinito è **96**. Si applica ai formati di output **BMP**, **GIF**, **PNG**e **TIFF** .|  
|**DpiY**|Risoluzione verticale dell'immagine di output. Il valore predefinito è **96**. Si applica ai formati di output **BMP**, **GIF**, **PNG**e **TIFF** .|  
|**EndPage**|Ultima pagina del report di cui eseguire il rendering. Il valore predefinito è il valore di **StartPage**.|  
|**MarginBottom**|Valore in pollici del margine inferiore da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginLeft**|Valore in pollici del margine sinistro da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginRight**|Valore in pollici del margine destro da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginTop**|Valore in pollici del margine superiore da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**PageHeight**|Altezza di pagina in pollici da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **11in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**PageWidth**|Larghezza di pagina in pollici da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **8.5in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**StartPage**|Prima pagina del report di cui eseguire il rendering. Il valore **0** indica che viene eseguito il rendering di tutte le pagine. Il valore predefinito è **1**.|  
|**UseReportPageSize**|Se UseReportPageSize =**false** , le dimensioni predefinite delle diapositive corrispondono a quelle predefinite di PowerPoint, ovvero 33,86 cm x 19,05 cm (formato 16:9). Se UseReportPageSize =true, le dimensioni predefinite delle diapositive corrispondono alle dimensioni di pagina definite del report.<br /><br /> Il valore predefinito è **false**<br /><br /> Si noti che le impostazioni PageHeight e PageWidth sostituiscono la larghezza e l'altezza predefinite.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Il passaggio di impostazioni informazioni dispositivo a estensioni di Rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il Rendering in RSReportServer. config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../reporting-services/technical-reference-ssrs.md)  
  
  

