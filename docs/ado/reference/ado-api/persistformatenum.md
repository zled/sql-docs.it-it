---
title: PersistFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 851106109d195ae6f5d6f66d3944e486d58504c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753635"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Specifica il formato in cui salvare una [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Indica al formato Microsoft avanzata dei dati viene (ADTG).|  
|**adPersistADO**|1|Indica che verrà utilizzato il formato di Extensible Markup Language (XML) di ADO. Questo valore è lo stesso adPersistXML ed è inclusa per ragioni di compatibilità.|  
|**adPersistXML**|1|Indica il formato Extensible Markup Language (XML).|  
|**adPersistProviderSpecific**|2|Indica che il provider verrà mantenuto il **Recordset** usando un formato specifico.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Save](../../../ado/reference/ado-api/save-method.md)
