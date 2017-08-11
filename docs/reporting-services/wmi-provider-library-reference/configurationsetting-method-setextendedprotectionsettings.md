---
title: Metodo SetExtendedProtectionSettings (MSReportServer_ConfigurationSetting WMI) | Documenti Microsoft
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
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c40a79e943e9021e10eb321a45d3a14c0fce1582
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setextendedprotectionsettings"></a>Metodo ConfigurationSetting - SetExtendedProtectionSettings
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
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà RSWindowsExtendedProtectionLevel e RSWindowsExtendedProtectionScenario si applicano quando i tipi di autenticazione nel file RSReportServer.config includono RSWindowNTLM, RSWindowsNegotiate o RSWindowsKerberos. L'impostazione di queste proprietà ha effetto sulla modalità di autenticazione degli utenti e del software client nel server di report. Prima di impostare ExtendedProtectionLevel su **Allow** o **Require**, è consigliabile leggere la documentazione relativa alla protezione estesa.  
  
 Per impostare ExtendedProtectionLevel, è necessario che l'utente sia un membro del gruppo BUILTIN\Administrators nel server di report.  
  
## <a name="requirements"></a>Requisiti  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RSWindowsExtendedProtectionScenario &#40; WMI MSReportServer_ConfigurationSetting &#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [Proprietà RSWindowsExtendedProtectionLevel &#40; WMI MSReportServer_ConfigurationSetting &#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Protezione estesa per l'autenticazione con Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
