---
title: Metodo ListReservedURLs (MSReportServer_ConfigurationSetting WMI) | Documenti Microsoft
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
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: cf6f31340eaba5654e2c5fd125eefba07a39d8e5
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="configurationsetting-method---listreservedurls"></a>Metodo ConfigurationSetting - ListReservedURLs
  Elenca gli URL riservati per tutte le applicazioni presenti nel server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *Application[]*  
 [out] Applicazioni che dispongono di prenotazioni URL.  
  
 *UrlString[]*  
 [out] URL riservati.  
  
 *Account[]*  
 [out] Nomi account associati all'account per le prenotazioni URL.  
  
 *AccountSID[]*  
 [out] SID di account associati all'account per le prenotazioni URL.  
  
 *Length*  
 [out] Lunghezza delle matrici restituite dal metodo.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Il valore 0 indica l'esito positivo della chiamata al metodo, mentre un codice di errore ne indica l'esito negativo.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
