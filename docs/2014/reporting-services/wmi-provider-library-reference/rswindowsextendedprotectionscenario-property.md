---
title: Proprietà RSWindowsExtendedProtectionScenario (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3eca2ad0b54e6efad5e197528b7aa0c48ecb3489
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309086"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserverconfigurationsetting"></a>Proprietà RSWindowsExtendedProtectionScenario (MSReportServer_ConfigurationSetting WMI)
  Restituisce un valore stringa che indica lo scenario di protezione estesa consentito dalla configurazione del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Note  
 Restituisce un valore stringa che indica lo scenario di protezione estesa consentito dalla configurazione del server di report. Se il server di report al quale il provider WMI è connesso non supporta la protezione estesa, viene restituita una stringa vuota ("").  
  
 Nell'elenco seguente sono indicati i valori validi:  
  
 `”Any | Proxy | Direct”`  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Metodo SetExtendedProtectionSettings &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Protezione estesa per l'autenticazione con Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [File di configurazione RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
