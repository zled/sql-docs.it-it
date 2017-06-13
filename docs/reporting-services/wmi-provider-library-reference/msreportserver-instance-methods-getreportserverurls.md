---
title: Metodo GetReportServerUrls (MSReportServer_Instance WMI) | Documenti Microsoft
ms.custom: 
ms.date: 06/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a4b7067d9e6360902bf76b1bfe27c7ed6541f481
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="msreportserverinstance-methods---getreportserverurls"></a>Metodi MSReportServer_Instance - GetReportServerUrls
  Restituisce un elenco degli URL che è possibile usare per accedere al server di report e [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *ApplicationName[]*  
 Matrice che contiene le applicazioni installate. I valori validi sono **ReportServerWebService** e **ReportServerWebApp**.  
  
 *URLs[]*  
 Matrice che contiene gli URL registrati correttamente.  
  
 *Lunghezza*  
 Valore intero che contiene la lunghezza delle matrici restituite.  
  
 *HRESULT*  
 Valore che indica l'esito positivo o un codice di errore.  
  
## <a name="return-values"></a>Valori restituiti  
  
## <a name="remarks"></a>Osservazioni  
 I metodi esposti dagli oggetti di gestione WMI vengono chiamati tramite la funzione InvokeMethod. Per altre informazioni, vedere gli argomenti relativi all'esecuzione di metodi in oggetti di gestione all'interno della documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  

