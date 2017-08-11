---
title: "Proprietà DatabaseLogonAccount (MSReportServer_ConfigurationSetting WMI) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- DatabaseLogonAccount
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
caps.latest.revision: 24
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bc718404b4bb79c03028ce8507d7fef4f788b72a
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-property---databaselogonaccount"></a>Proprietà ConfigurationSetting - DatabaseLogonAccount
  Specifica l'account di accesso utilizzato dal server di report al momento della connessione al database del server di report. Sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Oggetto **String** che rappresenta il nome dell'account di accesso.  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 I valori validi per questa proprietà varieranno a seconda del valore della proprietà [DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogontype.md) .  
  
 Questa proprietà viene ignorata se la proprietà [DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogontype.md) è impostata su **2 (Service)**.  
  
## <a name="requirements"></a>Requisiti  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
