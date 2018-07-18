---
title: Elemento DataSourcePermission (ASSL) | Microsoft Docs
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
- DataSourcePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d88f18a752e96e5081462056d831bc968dc605df
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241361"
---
# <a name="datasourcepermission-element-assl"></a>Elemento DataSourcePermission (ASSL)
  Definisce le autorizzazioni predefinite in un [DataSource](../data-type/datasource-data-type-assl.md) tipo di dati per uno specifico [ruolo](role-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../data-type/permission-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DataSourcePermissions](../collections/datasourcepermissions-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli oggetti `DataSourcePermission` possono essere presenti solo per i ruoli posseduti dal database e per ogni ruolo può essere presente un solo oggetto `DataSourcePermission`.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](role-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
