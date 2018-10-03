---
title: Elemento HierarchyUniqueNameStyle (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- HierarchyUniqueNameStyle Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- HierarchyUniqueNameStyle element
ms.assetid: 2ac57825-e9e5-4ec4-9856-fa2326d2c43f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04776eb3c9f20e0fa8c870621020c466ba625826
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196871"
---
# <a name="hierarchyuniquenamestyle-element-assl"></a>Elemento HierarchyUniqueNameStyle (ASSL)
  Determina i nomi univoci come vengono generati per le gerarchie contenute all'interno di [CubeDimension](../data-type/dimension-data-type-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeDimension>  
   ...  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*IncludeDimensionName*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeDimension](../data-type/dimension-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*IncludeDimensionName*|Il nome della dimensione fa parte del nome della gerarchia.|  
|*ExcludeDimensionName*|Il nome della dimensione non fa parte del nome della gerarchia.|  
  
 L'elemento che corrisponde al padre di `HierarchyUniqueNameStyle` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento del cubo &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Elemento della dimensione &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
