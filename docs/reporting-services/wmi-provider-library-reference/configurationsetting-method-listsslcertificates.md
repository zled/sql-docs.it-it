---
title: Metodo ListSSLCertificates (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
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
helpviewer_keywords: ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
caps.latest.revision: "12"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5fb7ce1a50f310d7d83114fbc02c4b6c596ac1c7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="configurationsetting-method---listsslcertificates"></a>Metodo di ConfigurationSetting - ListSSLCertificates
  Restituisce un elenco dei certificati presenti nel computer del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *CertificateHash[]*  
 [out] Hash del certificato.  
  
 *CertName[]*  
 [out] Nomi del certificato.  
  
 *HostName[]*  
 [out] Nomi host per i certificati.  
  
 *Length*  
 [out] Rappresenta la lunghezza delle matrici *CertificateHash*, *CertName* e *HostName* .  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Il valore 0 indica l'esito positivo della chiamata al metodo, mentre un codice di errore ne indica l'esito negativo.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
