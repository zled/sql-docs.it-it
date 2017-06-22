---
title: ATOM Device Information Settings | Documenti Microsoft
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
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 847b387a04f302c731ed3cb1d2c31df57e202680
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="atom-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo ATOM
  Le impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering Atom supportano l'invio del nome di un feed Atom e della codifica dei caratteri da utilizzare.  
  
 Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering in un documento di servizio dati.  
  
|Impostazione|Valore|  
|-------------|-----------|  
|**DataFeed**|Se specificato, esegue il rendering del feed Atom che corrisponde al nome del feed fornito in questa impostazione. In caso contrario, esegue il rendering del documento di servizio Atom per il report. Identificatore univoco del feed di dati generato automaticamente. Questo valore viene utilizzato internamente e non deve essere modificato.|  
|**Codifica**|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework. Il valore predefinito è **UTF-8**. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.config.](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Guida di riferimento tecnico &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
