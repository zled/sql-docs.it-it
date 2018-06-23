---
title: Impostazioni relative alle informazioni sul dispositivo ATOM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f2742b7507eecaadc26604f4217b1c6b2f1def1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067982"
---
# <a name="atom-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo ATOM
  Le impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering Atom supportano l'invio del nome di un feed Atom e della codifica dei caratteri da utilizzare.  
  
 Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering in un documento di servizio dati.  
  
|Impostazione|valore|  
|-------------|-----------|  
|`DataFeed`|Se specificato, esegue il rendering del feed Atom che corrisponde al nome del feed fornito in questa impostazione. In caso contrario, esegue il rendering del documento di servizio Atom per il report. Identificatore univoco del feed di dati generato automaticamente. Questo valore viene utilizzato internamente e non deve essere modificato.|  
|**Codifica**|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework. Il valore predefinito è `UTF-8`. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio Device Information Settings a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  