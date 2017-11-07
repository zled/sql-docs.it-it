---
title: Elemento DimensionPermissions (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DimensionPermissions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DimensionPermissions
helpviewer_keywords:
- DimensionPermissions element
ms.assetid: cb9fdfbf-2118-423b-ba02-fa36813dbea0
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23915ccc9ebc496be05c9ae2c0d092961e9db615
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dimensionpermissions-element-assl"></a>Elemento DimensionPermissions (ASSL)
  Contiene la raccolta di autorizzazioni applicabili a un [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md) elemento o un [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension> <!-- or CubePermission -->  
   ...  
   <DimensionPermissions>  
            <DimensionPermission>...</DimensionPermission> <!-- parent: Dimension -->  
      <!-- or -->  
      <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- parent: CubePermission -->  
      </DimensionPermissions>  
   ...  
</Dimension>  
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
|Elementi padre|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Elementi figlio|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per **CubePermission** elementi, **DimensionPermission** le autorizzazioni specificate in l'override di elementi nella raccolta di **DimensionPermissions** insieme di ogni dimensione in modo esplicito a cui fa riferimento. Se una dimensione non viene fatto riferimento in questa raccolta, il **CubePermission** elemento eredita le autorizzazioni specificate nel **DimensionPermissions** raccolta della dimensione.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionPermissionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

