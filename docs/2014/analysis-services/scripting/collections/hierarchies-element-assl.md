---
title: Elemento hierarchies (ASSL) | Documenti Microsoft
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
- Hierarchies Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Hierarchies
helpviewer_keywords:
- Hierarchies element
ms.assetid: dc844eea-869c-4217-b9be-e543a76f5e92
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a53cc41d7373bcd60268bd64247eea6caf56753a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168892"
---
# <a name="hierarchies-element-assl"></a>Elemento Hierarchies (ASSL)
  Contiene la raccolta di [gerarchia](../objects/hierarchy-element-assl.md) elementi associati all'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension> <!-- or CubeDimension, PerspectiveDimension -->  
   ...  
   <Hierarchies>  
            <Hierarchy>...</Hierarchy> <!-- parent: Dimension -->  
      <!-- or -->  
      <Hierarchy xsi:type="CubeHierarchy">...</Hierarchy> <!-- parent: CubeDimension -->  
     <!-- or -->  
      <Hierarchy xsi:type="PerspectiveHierarchy">...</Hierarchy> <!-- parent: PerspectiveDimension -->  
   <Hierarchies>  
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
|Elementi padre|[CubeDimension](../data-type/dimension-data-type-assl.md), [dimensione](../objects/dimension-element-assl.md), [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[CubeDimension](../data-type/dimension-data-type-assl.md)|[Gerarchia](../objects/hierarchy-element-assl.md) di tipo [CubeHierarchy](../data-type/hierarchy-data-type-assl.md)|  
|[Dimension](../objects/dimension-element-assl.md)|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|[PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|[Gerarchia](../objects/hierarchy-element-assl.md) di tipo [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.HierarchyCollection>, <xref:Microsoft.AnalysisServices.CubeHierarchyCollection> e <xref:Microsoft.AnalysisServices.PerspectiveHierarchyCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  