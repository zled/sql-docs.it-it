---
title: Metodo SetServiceState (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 7fdcc309eca07c8fc29fa80934e6929054a59b44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156619"
---
# <a name="setservicestate-method-wmi-msreportserverconfigurationsetting"></a>Metodo SetServiceState (MSReportServer_ConfigurationSetting WMI)
  Attiva e disattiva i servizi Windows ReportServer e Web ReportServer.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *EnableWindowsService*  
 Oggetto `Boolean` valore che indica lo stato del servizio Windows. Il valore `true` avvia il Server di Report Windows service, il valore `false` Arresta il servizio Windows.  
  
 *EnableWebService*  
 Valore `Boolean` che indica lo stato del servizio Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Un valore `true` avvia il servizio Web ReportServer; un valore `false` arresta il servizio Web.  
  
 *EnableReportManager*  
 Oggetto `Boolean` valore che indica lo stato desiderato di gestione Report.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  