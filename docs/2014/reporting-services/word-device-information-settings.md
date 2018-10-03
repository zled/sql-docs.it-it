---
title: Impostazioni relative alle informazioni sul dispositivo Word | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7c6a084e7d2093d2f0bfc7d55ef7f16be5b83e1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126877"
---
# <a name="word-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo Word
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Impostazione|valore|  
|-------------|-----------|  
|`AutoFit`|`False` (Indici per tabelle con ottimizzazione per la memoria). AutoFit è `false` in alcun tabelle di Word.<br /><br /> `True` (Indici per tabelle con ottimizzazione per la memoria). L'impostazione di AutoFit è `true` in tutte le tabelle di Word.<br /><br /> `Never` (Indici per tabelle con ottimizzazione per la memoria). I valori di AutoFit non sono impostati in alcuna tabella di Word e viene applicato il comportamento predefinito di Word.<br /><br /> `Default` (Indici per tabelle con ottimizzazione per la memoria). AutoFit è impostata per le tabelle più strette rispetto all'area di disegno fisica (larghezza fisica della pagina esclusi i margini) per la pagina logica.|  
|`ExpandToggles`|Indica se per tutti gli elementi che possono essere attivati o disattivati deve venire eseguito il rendering nello stato completamente espanso. Il valore predefinito è `false`.|  
|`FixedPageWidth`|Indica se la larghezza della pagina scritta nel file DOC aumenta in base alla larghezza della pagina più larga nel corpo del report. Il valore predefinito è `false`.|  
|**OmitHyperlinks**|Indica se l'azione collegamento ipertestuale deve essere omessa in tutti gli elementi in cui è impostata. Il valore predefinito è `false`|  
|`OmitDrillthroughs`|Indica se l'azione drill-through deve essere omessa in tutti gli elementi in cui è impostata. Il valore predefinito è `false`|  
  
## <a name="see-also"></a>Vedere anche  
 [Il passaggio di impostazioni informazioni dispositivo a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
