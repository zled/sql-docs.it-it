---
title: Metodo GetAdminSiteUrl (WMI) | Documenti Microsoft
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
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
caps.latest.revision: 14
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ae40992c6a864a73bb758a3ce336624917a68a96
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---getadminsiteurl"></a>Metodo ConfigurationSetting - GetAdminSiteUrl
  Ottiene l'URL assoluto per il sito Web di Amministrazione centrale per la farm di Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] con la quale il server di report è integrato.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *AdminSiteUrl*  
 [out] Stringa che contiene l'URL assoluto per il sito Web di Amministrazione centrale per la farm di SharePoint con la quale il server di report è integrato.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="requirements"></a>Requisiti  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-methods.md)  
  
  
