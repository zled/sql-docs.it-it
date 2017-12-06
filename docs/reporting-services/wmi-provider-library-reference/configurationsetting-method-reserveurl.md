---
title: Metodo ReserveURL (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
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
helpviewer_keywords: ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
caps.latest.revision: "14"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b9ae852377e60f54274ba065a4f7b087d6a5b9d0
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="configurationsetting-method---reserveurl"></a>Metodo ConfigurationSetting - ReserveURL
  Aggiunge una prenotazione URL per un'applicazione specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *Applicazione*  
 Nome dell'applicazione per la quale riservare l'URL.  
  
 *URLString*  
 URL per la prenotazione.  
  
 *lcid*  
 Impostazioni locali da utilizzare per i messaggi di errore restituiti.  
  
 *Errore*  
 [out] Descrizione dell'errore che si è verificato.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Il valore 0 indica l'esito positivo della chiamata al metodo, mentre un codice di errore ne indica l'esito negativo.  
  
## <a name="remarks"></a>Osservazioni  
 *UrlString* non include il nome della directory virtuale. A tal fine, viene fornito il metodo [SetVirtualDirectory](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md) .  
  
 Le prenotazioni URL vengono create per l'account del servizio Windows corrente. La modifica dell'account del servizio Windows richiede l'aggiornamento manuale di tutte le prenotazioni URL.  
  
 Questo metodo causa l'esecuzione dell'operazione di riciclo pesante da parte di tutti i domini applicazione. Una volta completata l'operazione, i domini applicazione vengono riavviati.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
