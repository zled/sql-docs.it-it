---
title: Impostazioni relative alle informazioni sul dispositivo Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
caps.latest.revision: 40
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8d5da4ae14517e7b2f1ed21d558d4854b664c90f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170242"
---
# <a name="excel-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo Excel
  La tabella seguente elenca le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Impostazione|valore|  
|-------------|-----------|  
|**OmitDocumentMap**|Indica se omettere la mappa documento per i report che la supportano. Il valore predefinito è `false`.|  
|**OmitFormulas**|Indica se omettere le formule dal report visualizzabile. Il valore predefinito è `false`.|  
|`SimplePageHeade`RS|Indica se viene eseguito il rendering dell'intestazione di pagina del report nell'intestazione di pagina di Excel. Un valore di `false` indica che viene eseguito il rendering dell'intestazione di pagina nella prima riga del foglio di lavoro. Il valore predefinito è `false`.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Il passaggio di impostazioni informazioni dispositivo a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
