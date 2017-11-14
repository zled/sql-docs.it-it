---
title: PersistFormatEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c981037637b85e23e6b871116291aa8eb607c99
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="persistformatenum"></a>PersistFormatEnum
Specifica il formato in cui salvare un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Indica il formato di Microsoft Advanced dati viene (ADTG).|  
|**adPersistADO**|1|Indica che verrà utilizzato il formato di Extensible Markup Language (XML) di ADO. Questo valore è lo stesso adPersistXML ed è inclusa per ragioni di compatibilità.|  
|**valore adPersistXML**|1|Indica il formato di Extensible Markup Language (XML).|  
|**adPersistProviderSpecific**|2|Indica che il provider verrà mantenuta la **Recordset** utilizzando il proprio formato.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Si applica a  
 [Save (metodo)](../../../ado/reference/ado-api/save-method.md)

