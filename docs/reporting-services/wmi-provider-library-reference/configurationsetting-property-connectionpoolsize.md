---
title: Proprietà ConnectionPoolSize (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- ConnectionPoolSize
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ConnectionPoolSize property
ms.assetid: b80c8e5d-b725-4fe4-aec6-02fb18ec4434
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c50f2113290ac6ce74d2d31ce676351f1d0e0232
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031688"
---
# <a name="configurationsetting-property---connectionpoolsize"></a>Proprietà di ConfigurationSetting - ConnectionPoolSize
  Dimensione del pool di connessioni usato dal server di report per comunicare con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database del server di report. Di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim ConnectionPoolSize As UInt32  
```  
  
```csharp  
public UInt32 ConnectionPoolSize;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Un oggetto **integer** di sola lettura che restituisce un valore di **768**.  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
