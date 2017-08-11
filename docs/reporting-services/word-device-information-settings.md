---
title: Word Device Information Settings | Documenti Microsoft
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
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 491940329df26ba67f447aacb6a32f5d6578c4a5
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="word-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo Word
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Impostazione|Valore|  
|-------------|-----------|  
|**AutoFit**|**False**. L'impostazione di AutoFit è **false** in tutte le tabelle di Word.<br /><br /> **True**. L'impostazione di AutoFit è **true** in tutte le tabelle di Word.<br /><br /> **Never**. I valori di AutoFit non sono impostati in alcuna tabella di Word e viene applicato il comportamento predefinito di Word.<br /><br /> **Default**. AutoFit è impostata per le tabelle più strette rispetto all'area di disegno fisica (larghezza fisica della pagina esclusi i margini) per la pagina logica.|  
|**ExpandToggles**|Indica se per tutti gli elementi che possono essere attivati o disattivati deve venire eseguito il rendering nello stato completamente espanso. Il valore predefinito è **false**.|  
|**FixedPageWidth**|Indica se la larghezza della pagina scritta nel file DOC aumenta in base alla larghezza della pagina più larga nel corpo del report. Il valore predefinito è **false**.|  
|**OmitHyperlinks**|Indica se l'azione collegamento ipertestuale deve essere omessa in tutti gli elementi in cui è impostata. Il valore predefinito è **false**|  
|**OmitDrillthroughs**|Indica se l'azione drill-through deve essere omessa in tutti gli elementi in cui è impostata. Il valore predefinito è **false**|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Il passaggio di impostazioni informazioni dispositivo a estensioni di Rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il Rendering in RSReportServer. config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
