---
title: Proprietà RSWindowsExtendedProtectionLevel (MSReportServer_ConfigurationSetting WMI) | Documenti Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 9e96011dc05f0bc21708f8759aa715dbc4ca79a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169559"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserverconfigurationsetting"></a>Proprietà RSWindowsExtendedProtectionLevel (MSReportServer_ConfigurationSetting WMI)
  Restituisce un valore stringa che indica il livello di protezione supportato dalla configurazione del server di report. Questa proprietà è di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>Remarks  
 Restituisce un valore stringa che indica il livello di protezione supportato dalla configurazione del server di report. Se il server di report al quale il provider WMI è connesso non supporta la protezione estesa, viene restituita una stringa vuota (""). Nell'elenco seguente sono indicati i valori validi:  
  
 `“Off” | “Allow” | “Require”`  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Metodo SetExtendedProtectionSettings &#40;MSReportServer_ConfigurationSetting WMI&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Protezione estesa per l'autenticazione con Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [File di configurazione RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  