---
title: Metodo GetReportServerUrls (MSReportServer_Instance WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 148e0ece44e97bd4c559bbed9cc95aa97092dffb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171051"
---
# <a name="getreportserverurls-method-wmi-msreportserverinstance"></a>Metodo GetReportServerUrls (MSReportServer_Instance WMI)
  Restituisce un elenco degli URL che è possibile utilizzare per accedere al server di report e alla gestione report.  
  
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
 Matrice che contiene le applicazioni installate. I valori sono `ReportServerWebService` o `ReportManager`.  
  
 *URLs[]*  
 Matrice che contiene gli URL registrati correttamente.  
  
 *Lunghezza*  
 Valore intero che contiene la lunghezza delle matrici restituite.  
  
 *HRESULT*  
 Valore che indica l'esito positivo o un codice di errore.  
  
## <a name="return-values"></a>Valori restituiti  
  
## <a name="remarks"></a>Note  
 I metodi esposti dagli oggetti di gestione WMI vengono chiamati tramite la funzione InvokeMethod. Per altre informazioni, vedere gli argomenti relativi all'esecuzione di metodi in oggetti di gestione all'interno della documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
