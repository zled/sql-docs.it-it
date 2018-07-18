---
title: Proprietà IsSharePointIntegrated (MSReportServer_Instance WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c96d8e6bf204759f9096bd870c72887f9ef26f65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257907"
---
# <a name="issharepointintegrated-property-wmi-msreportserverinstance"></a>Proprietà IsSharePointIntegrated (MSReportServer_Instance WMI)
  Viene specificato se il server di report è in modalità integrata SharePoint. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], questa proprietà restituisce sempre `False` poiché in modalità SharePoint, le istanze [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono servizi condivisi SharePoint e non vengono controllate dai provider WMI.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Valore `Boolean` che indica se il server di report è in modalità integrata SharePoint.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_Instance](msreportserver-instance-members.md)   
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
  
