---
title: Elemento Relationships (ASSL) | Documenti Microsoft
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
ms.assetid: e78882c9-b14e-4044-848e-ea7fddd3b75d
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 987b35a09670908e5604693c2b42b4a014d5eda6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158287"
---
# <a name="relationships-element-assl"></a>Elemento Relationships (ASSL)
  Contiene la raccolta di relazioni per la dimensione associata.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
  </Attributes>  
   ...  
</CubeDimension>  
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
|Elementi padre|[CubeDimension](../data-type/dimension-data-type-assl.md), [dimensione](../objects/dimension-element-assl.md), [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md), [RegularMeasureGroupDimension](../data-type/measuregroupdimension-data-type-assl.md)|  
|Elementi figlio|[Relazione](../data-type/relationship-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Gli elementi corrispondenti nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.RelationshipCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  