---
title: Elemento Description (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dadef861a5b54dafddd6f2dcf3072cd4e0d510ad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194131"
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
|Elementi padre|[Azione](../objects/action-element-assl.md), [aggregazione](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [AttributePermission](../objects/attributepermission-element-assl.md), [ CalculationProperty](../objects/calculationproperty-element-assl.md), [CellPermission](../objects/cellpermission-element-assl.md), [cubo](../objects/cube-element-assl.md), [CubeDimensionPermission](../data-type/permission-data-type-assl.md), [Database](../objects/database-element-assl.md) , [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [dimensione](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [gerarchia](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [livello](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [misura](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [ Partizione](../objects/partition-element-assl.md), [autorizzazione](../data-type/permission-data-type-assl.md), [prospettiva](../objects/perspective-element-assl.md), [ruolo](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [ Traccia](../objects/trace-element-assl.md), [traduzione](../objects/translation-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di un elemento `Description` ha le seguenti restrizioni.  
  
-   Il valore non deve contenere spazi iniziali o finali. Se gli spazi iniziali o finali sono inclusi nel valore di una `Description` elemento, tali spazi verranno rimossi implicitamente da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Il valore non può contenere caratteri di controllo. Se nel valore di un elemento `Description` sono inclusi caratteri di controllo, tali spazi verranno rimossi in modo implicito da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Denominare l'elemento &#40;ASSL&#41;](name-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
