---
title: Elemento DataSourcePermissions (ASSL) | Microsoft Docs
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
- DataSourcePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSourcePermissions element
ms.assetid: 6e1cfbec-65b9-4942-a628-f7f7c891e35f
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42f330e28ac9a8bd349660550cee84df075121f5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321181"
---
# <a name="datasourcepermissions-element-assl"></a>Elemento DataSourcePermissions (ASSL)
  Contiene la raccolta di [DataSourcePermission](../objects/datasourcepermission-element-assl.md) gli elementi associati a un [DataSource](../data-type/datasource-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSource>  
   ...  
   <DataSourcePermissions>  
      <DataSourcePermission>...</DataSourcePermission>  
   </DataSourcePermissions>  
   ...  
</DataSource>  
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
|Elementi padre|[Origine dati](../data-type/datasource-data-type-assl.md)|  
|Elementi figlio|[DataSourcePermission](../objects/datasourcepermission-element-assl.md)|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
