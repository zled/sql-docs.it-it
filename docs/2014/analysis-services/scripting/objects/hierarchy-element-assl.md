---
title: Elemento Hierarchy (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Hierarchy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy element
ms.assetid: ac54d74a-5e6c-4c24-83bf-766440478f6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e64d63e6dbb297571eb10f5e198a627a9828764e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200631"
---
# <a name="hierarchy-element-assl"></a>Elemento Hierarchy (ASSL)
  Definisce una gerarchia in una dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Hierarchies>  
   <Hierarchy xsi:type="Hierarchy">...</Hierarchy> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <Hierarchy xsi:type="CubeHierarchy">...</Hierarchy> <!-- ancestor: CubeDimension -->  
   <!-- or -->  
   <Hierarchy xsi:type="PerspectiveHierarchy">...</Hierarchy> <!-- ancestor: PerspectiveDimension -->  
   <!-- or -->  
   <Hierarchy xsi:type="MeasureGroupHierarchy">...</Hierarchy> <!-- ancestor: RegularMeasureGroupDimension -->  
</Hierarchies>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza||  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="data-type-and-length"></a>Tipo di dati e lunghezza  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[Dimension](../data-type/hierarchy-data-type-assl.md)|  
|[CubeDimension](../data-type/cubehierarchy-data-type-assl.md)|  
|[Elemento PerspectiveDimension](../data-type/perspectivehierarchy-data-type-assl.md)|  
|[RegularMeasureGroupDimension](../data-type/measuregrouphierarchy-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Gerarchie](../collections/hierarchies-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.CubeHierarchy> e <xref:Microsoft.AnalysisServices.PerspectiveHierarchy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
