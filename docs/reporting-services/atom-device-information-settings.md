---
title: Impostazioni relative alle informazioni sul dispositivo ATOM | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5f5c75583542dd7f2bc62b6de5da2fb457a90296
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="atom-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo ATOM
  Le impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering Atom supportano l'invio del nome di un feed Atom e della codifica dei caratteri da utilizzare.  
  
 Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering in un documento di servizio dati.  
  
|Impostazione|valore|  
|-------------|-----------|  
|**DataFeed**|Se specificato, esegue il rendering del feed Atom che corrisponde al nome del feed fornito in questa impostazione. In caso contrario, esegue il rendering del documento di servizio Atom per il report. Identificatore univoco del feed di dati generato automaticamente. Questo valore viene utilizzato internamente e non deve essere modificato.|  
|**Codifica**|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework. Il valore predefinito è **UTF-8**. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
