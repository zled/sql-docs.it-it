---
title: Metodo SetUnattendedExecutionAccount (MSReportServer_ConfigurationSetting WMI) | Documenti Microsoft
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
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1c94627129ed2e6706112aad013a3395c4a1e68a
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setunattendedexecutionaccount"></a>Metodo ConfigurationSetting - SetUnattendedExecutionAccount
  Specifica l'account utilizzato per l'esecuzione automatica dei report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *UserName*  
 Account di Windows da utilizzare per le esecuzioni automatiche.  
  
 *Password*  
 Password per l'account specificato.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo SetUnattendedExecutionAccount non verifica se il server di report può accedere come utente specificato.  
  
 Non è possibile usare il metodo SetUnattendedExecutionAccount per effettuare esecuzioni automatiche nel contesto del servizio Windows del server di report.  
  
## <a name="requirements"></a>Requisiti  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
