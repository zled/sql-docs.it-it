---
title: "Proprietà SecureConnectionLevel (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SecureConnectionLevel
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: 
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: da2723ebece790589719c18a7137f5c7433c660a
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="configurationsetting-property---secureconnectionlevel"></a>Proprietà di ConfigurationSetting - SecureConnectionLevel
  Restituisce il livello di connessione protetta specificato nel file RSReportServer.config. Di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Valore **Integer** che rappresenta il livello di connessione protetto. I valori restituiti indicano se SSL è o non è configurato. Il valore maggiore di o pari a 1 indica che SSL è abilitato. Il valore 0 indica che SSL è disattivato.  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks

In SQL Server 2008 R2 SecureConnectionLevel diventa un'opzione di attivazione/disattivazione. Per altre informazioni, vedere [Metodo ConfigurationSetting - SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setsecureconnectionlevel.md).

## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
