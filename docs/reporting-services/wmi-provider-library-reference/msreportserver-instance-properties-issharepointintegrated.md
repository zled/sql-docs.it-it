---
title: Proprietà IsSharePointIntegrated (MSReportServer_Instance WMI) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e19153908927173c81a8d56a0f5db7ca1a2161c2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33030818"
---
# <a name="msreportserverinstance-properties---issharepointintegrated"></a>Proprietà di MSReportServer_Instance - IsSharePointIntegrated
  Viene specificato se il server di report è in modalità integrata SharePoint. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], questa proprietà restituisce sempre **False** poiché in modalità SharePoint le istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono servizi condivisi SharePoint e non vengono controllate dai provider WMI.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Valore **Boolean** che indica se il server di report è in modalità integrata SharePoint.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
