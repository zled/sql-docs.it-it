---
title: Elemento TableNotifications (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TableNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#TableNotifications
- microsoft.xml.analysis.tablenotifications
- http://schemas.microsoft.com/analysisservices/2003/engine#TableNotifications
helpviewer_keywords:
- TableNotifications element
ms.assetid: 650f307d-1f11-47ce-9d0e-19cf3b1835b7
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e474472b2b55132667b7ec424d392fccb936d93c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284047"
---
# <a name="tablenotifications-element-xmla"></a>Elemento TableNotifications (XMLA)
  Contiene una raccolta di [TableNotification](tablenotification-element-xmla.md) gli elementi utilizzati per il [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<NotifyTableChange >  
   ...  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
   </TableNotifications>  
   ...  
</NotifyTableChange>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md)|  
|Elementi figlio|[TableNotification](tablenotification-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
