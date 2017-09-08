---
title: Elemento HierarchyUniqueNameStyle (ASSL) | Documenti Microsoft
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
- HierarchyUniqueNameStyle Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- HierarchyUniqueNameStyle element
ms.assetid: 2ac57825-e9e5-4ec4-9856-fa2326d2c43f
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e19b3e412b7330d6ef735bf269b72080e031b024
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchyuniquenamestyle-element-assl"></a>Elemento HierarchyUniqueNameStyle (ASSL)
  Determina i nomi univoci generati per le gerarchie contenute all'interno di [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeDimension>  
   ...  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*IncludeDimensionName*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*IncludeDimensionName*|Il nome della dimensione fa parte del nome della gerarchia.|  
|*ExcludeDimensionName*|Il nome della dimensione non fa parte del nome della gerarchia.|  
  
 L'elemento che corrisponde all'elemento padre **HierarchyUniqueNameStyle** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CUBE &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Elemento Dimension &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
