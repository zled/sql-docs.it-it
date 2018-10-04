---
title: Impostazioni relative alle informazioni sul dispositivo di acquisizione immagini | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6737a32eb7597f8115a7ee6797bcf1aedbd006b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220781"
---
# <a name="image-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo di acquisizione immagini
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato IMAGE.  
  
|Impostazione|valore|  
|-------------|-----------|  
|**Colonne**|Numero di colonne da impostare per il report. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**ColumnSpacing**|Spaziatura delle colonne da impostare per il report. Questo valore ha la priorità sulle impostazioni originali del report.|  
|`DpiX`|Risoluzione orizzontale dell'immagine di output. Il valore predefinito è **96**. Si applica a `BMP`, `GIF`, `PNG`, e `TIFF` formati di output.|  
|`DpiY`|Risoluzione verticale dell'immagine di output. Il valore predefinito è **96**. Si applica a `BMP`, `GIF`, `PNG`, e `TIFF` formati di output.|  
|**EndPage**|Ultima pagina del report di cui eseguire il rendering. Il valore predefinito è il valore di `StartPage`.|  
|**MarginBottom**|Valore in pollici del margine inferiore da impostare per il report. È necessario includere un valore intero o decimale seguito da "in" (ad esempio, `1in`). Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginLeft**|Valore in pollici del margine sinistro da impostare per il report. È necessario includere un valore intero o decimale seguito da "in" (ad esempio, `1in`). Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginRight**|Valore in pollici del margine destro da impostare per il report. È necessario includere un valore intero o decimale seguito da "in" (ad esempio, `1in`). Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginTop**|Valore in pollici del margine superiore da impostare per il report. È necessario includere un valore intero o decimale seguito da "in" (ad esempio, `1in`). Questo valore ha la priorità sulle impostazioni originali del report.|  
|**OutputFormat**|Uno dei [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) formati di output supportati: `BMP`, `EMF`, `GIF`, `JPEG`, `PNG`, o `TIFF`.|  
|**PageHeight**|Altezza di pagina in pollici da impostare per il report. È necessario includere un valore intero o decimale seguito da "in" (ad esempio, `11in`). Questo valore ha la priorità sulle impostazioni originali del report.|  
|**PageWidth**|Larghezza di pagina in pollici da impostare per il report. È necessario includere un valore intero o decimale seguito da "in" (ad esempio, `8.5in`). Questo valore ha la priorità sulle impostazioni originali del report.|  
|**PrintDpiX**|Risoluzione orizzontale dell'immagine di output. Il valore predefinito è `300`. Si applica a Enhanced MetaFile (`EMF`) formato di output.|  
|**PrintDpiY**|Risoluzione verticale dell'immagine di output. Il valore predefinito è `300`. Si applica a Enhanced MetaFile (`EMF`) formato di output.|  
|`StartPage`|Prima pagina del report di cui eseguire il rendering. Il valore `0` indica che viene eseguito il rendering di tutte le pagine. Il valore predefinito è `1`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Il passaggio di impostazioni informazioni dispositivo a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
