---
title: Elemento Description (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Description Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Description
helpviewer_keywords:
- Description element
ms.assetid: 34d67e7c-e79a-429b-8cc3-6ca13b9cf9c3
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 43e54f7c6f72703c0ddaff7776594fe0ac80ac64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077869"
---
# <a name="description-element-assl"></a>Elemento Description (ASSL)
  Contiene la descrizione dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Description>...</Description>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Action](../objects/action-element-assl.md), [Aggregation](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [AttributePermission](../objects/attributepermission-element-assl.md), [CalculationProperty](../objects/calculationproperty-element-assl.md), [CellPermission](../objects/cellpermission-element-assl.md), [Cube](../objects/cube-element-assl.md), [CubeDimensionPermission](../data-type/permission-data-type-assl.md), [Database](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Hierarchy](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [Level](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Measure](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [Partition](../objects/partition-element-assl.md), [Permission](../data-type/permission-data-type-assl.md), [Perspective](../objects/perspective-element-assl.md), [Role](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [Trace](../objects/trace-element-assl.md), [Translation](../objects/translation-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di un elemento `Description` ha le seguenti restrizioni.  
  
-   Il valore non deve contenere spazi iniziali o finali. Se gli spazi iniziali o finali sono inclusi nel valore di un `Description` elemento, tali spazi verranno rimossi implicitamente da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Il valore non può contenere caratteri di controllo. Se nel valore di un elemento `Description` sono inclusi caratteri di controllo, tali spazi verranno rimossi in modo implicito da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Nome di elemento &#40;ASSL&#41;](name-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  