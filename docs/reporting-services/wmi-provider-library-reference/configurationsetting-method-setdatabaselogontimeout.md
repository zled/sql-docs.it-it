---
title: Metodo SetDatabaseLogonTimeout (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SetDatabaseLogonTimeout method
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
caps.latest.revision: "19"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3233579b566e940a3444e929ef3a59983788cc3c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="configurationsetting-method---setdatabaselogontimeout"></a>Metodo di ConfigurationSetting - SetDatabaseLogonTimeout
  Specifica il valore di timeout predefinito per le connessioni al database del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *LogonTimeout*  
 Valore di timeout predefinito, espresso in secondi, per le connessioni al database del server di report.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
