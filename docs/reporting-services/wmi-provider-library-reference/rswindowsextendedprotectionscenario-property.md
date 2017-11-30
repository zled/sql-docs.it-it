---
title: "Proprietà RSWindowsExtendedProtectionScenario | Microsoft Docs"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
caps.latest.revision: "6"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 06257c6bc32ba8ae073eb78518c4298c724834b0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="rswindowsextendedprotectionscenario-property"></a>Proprietà RSWindowsExtendedProtectionScenario
  Restituisce un valore stringa che indica lo scenario di protezione estesa consentito dalla configurazione del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce un valore stringa che indica lo scenario di protezione estesa consentito dalla configurazione del server di report. Se il server di report al quale il provider WMI è connesso non supporta la protezione estesa, viene restituita una stringa vuota ("").  
  
 Nell'elenco seguente sono indicati i valori validi:  
  
 `”Any | Proxy | Direct”`  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RSWindowsExtendedProtectionLevel &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Metodo SetExtendedProtectionSettings &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Protezione estesa per l'autenticazione con Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
