---
title: Elemento CubePermissions (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubePermissions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubePermissions
helpviewer_keywords:
- CubePermissions element
ms.assetid: 75a3a0c2-e1d4-4896-b0f5-2ea9c769b927
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0b2b01298fb0c7e9c24ae029d2675c26735d90d3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cubepermissions-element-assl"></a>Elemento CubePermissions (ASSL)
  Contiene la raccolta di autorizzazioni applicabili a un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube>  
   ...  
   <CubePermissions>  
      <CubePermission>...</CubePermission>  
   </CubePermissions>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|  
|Elementi figlio|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubePermissionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati Permission &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Raccolte &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

