---
title: Metodo SetExtendedProtectionSettings (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 81b0ea8c7142f33ef9fc91622d899e54f21fe756
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076214"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserverconfigurationsetting"></a>Metodo SetExtendedProtectionSettings (MSReportServer_ConfigurationSetting WMI)
  Il metodo SetExtendedProtectionSettings viene usato per impostare le proprietà RSWindowsExtendedProtectionLevel e RSWindowsExtendedProtectionScenario nel file di configurazione RSReportServer.config di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *ExtendedProtectionLevel*  
 Imposta RSWindowsExtendedProtectionLevel nel file RSRreportserver.config. Il valore obbligatorio non supporta la distinzione tra maiuscole e minuscole.  
  
 Nell'elenco seguente sono indicati i valori validi:  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 Imposta RSWindowsExtendedProtectionScenario nel file RSReportserver.config. Il valore obbligatorio non supporta la distinzione tra maiuscole e minuscole.  
  
 Nell'elenco seguente sono indicati i valori validi:  
  
 `”Any” | “Proxy” | “Direct”`  
  
## <a name="remarks"></a>Note  
 Le proprietà RSWindowsExtendedProtectionLevel e RSWindowsExtendedProtectionScenario si applicano quando i tipi di autenticazione nel file RSReportServer.config includono RSWindowNTLM, RSWindowsNegotiate o RSWindowsKerberos. L'impostazione di queste proprietà ha effetto sulla modalità di autenticazione degli utenti e del software client nel server di report. È consigliabile leggere la documentazione per la protezione estesa prima di impostare ExtendedProtectionLevel su `Allow` o `Require`.  
  
 Per impostare ExtendedProtectionLevel, è necessario che l'utente sia un membro del gruppo BUILTIN\Administrators nel server di report.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Proprietà RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Protezione estesa per l'autenticazione con Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [File di configurazione RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
