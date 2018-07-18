---
title: Elemento DimensionPermissions (ASSL) | Microsoft Docs
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
- DimensionPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionPermissions
helpviewer_keywords:
- DimensionPermissions element
ms.assetid: cb9fdfbf-2118-423b-ba02-fa36813dbea0
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 605f5055d4fc3939cb8b30f123281e3d920db6fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246328"
---
# <a name="dimensionpermissions-element-assl"></a>Elemento DimensionPermissions (ASSL)
  Contiene la raccolta di autorizzazioni applicabili a un [dimensione](../objects/dimension-element-assl.md) elemento o una [CubePermission](../objects/cubepermission-element-assl.md) elemento.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubePermission](../objects/cubepermission-element-assl.md), [dimensione](../objects/dimension-element-assl.md)|  
|Elementi figlio|[Elemento DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Per gli elementi `CubePermission`, elementi `DimensionPermission` in queste autorizzazioni dell'override della raccolta specificate nella raccolta `DimensionPermissions` di ogni dimensione fatta riferimento in modo esplicito. Se non è fatto riferimento a una dimensione in questa raccolta, l'elemento `CubePermission` eredita le autorizzazioni specificate nella raccolta `DimensionPermissions` della dimensione.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionPermissionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
