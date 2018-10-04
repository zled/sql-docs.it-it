---
title: Associazione tipo di dati (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Binding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- BINDING
helpviewer_keywords:
- Binding data type
ms.assetid: 0a777219-b885-4961-ac66-b76faeb520db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e46d48f94035a59c54a3e9bb9c8ccb087226660
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135901"
---
# <a name="binding-data-type-assl"></a>Tipo di dati Binding (ASSL)
  Definisce un tipo di dati primitivo astratto che rappresenta una relazione di dipendenza tra due oggetti in cui i dati o i metadati di un oggetto dipendono dai dati o dai metadati di un oggetto associato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[AttributeBinding](binding-data-type-assl.md), [ColumnBinding](columnbinding-data-type-assl.md), [CubeAttributeBinding](cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), [InheritedBinding](inheritedbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), [MeasureGroupBinding](measuregroupbinding-data-type-assl.md), [ MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md), [RowBinding](rowbinding-data-type-assl.md), [TabularBinding](tabularbinding-data-type-assl.md), [ TimeAttributeBinding](timeattributebinding-data-type-assl.md), [TimeBinding](timebinding-data-type-assl.md), [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Binding>.  
  
 Per altre informazioni sul data binding, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Elementi di tipo Binding  
 Nella tabella seguente sono elencati elementi di tipo `Binding`.  
  
|Elemento padre|Elemento di tipo `Binding`|Commenti|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../properties/source-element-binding-assl.md) dei [CaptionColumn](../objects/column-element-assl.md) (di tipo [DataItem](dataitem-data-type-assl.md))|Tipo dei `Binding` deve essere [AttributeBinding](binding-data-type-assl.md) o [ColumnBinding](columnbinding-data-type-assl.md)|  
|[Cube](../objects/cube-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (out-of-line)](../objects/group-element-assl.md)|Tipo dei `Binding` deve essere [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[DataItem](dataitem-data-type-assl.md)|[Origine](../properties/source-element-binding-assl.md)|`Binding` può essere di qualsiasi tipo|  
|[Dimension](../objects/dimension-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), o [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](dimensionattribute-data-type-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [AttributeBinding](binding-data-type-assl.md) o [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](action-data-type-assl.md)|[Colonna](../objects/column-element-assl.md)|Tipo dei `Binding` deve essere [CubeAttributeBinding](cubeattributebinding-data-type-assl.md) o [MeasureBinding](measurebinding-data-type-assl.md)|  
|[Misura](../objects/measure-element-assl.md)|[Origine](../properties/source-element-binding-assl.md) (di tipo [DataItem](dataitem-data-type-assl.md))|Tipo dei `Binding` deve essere [ColumnBinding](columnbinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), o [RowBinding](rowbinding-data-type-assl.md)|  
|[Gruppo di misure](../objects/measuregroup-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[Origine](../properties/source-element-binding-assl.md) dei [KeyColumn](../objects/keycolumn-element-assl.md) (di tipo [DataItem](dataitem-data-type-assl.md))|Tipo dei `Binding` deve essere [AttributeBinding](binding-data-type-assl.md) oppure [ColumnBinding](columnbinding-data-type-assl.md), o [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../objects/dimension-element-assl.md)|Tipo dei `Binding` deve essere [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](measuregroupbinding-data-type-out-of-line-assl.md)|[Misura](../objects/measure-element-assl.md)|Tipo dei `Binding` deve essere [MeasureBinding](measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](../objects/partition-element-assl.md)|Tipo dei `Binding` deve essere [PartitionBinding](partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](measuregroupbinding-data-type-out-of-line-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [TableBinding](tablebinding-data-type-assl.md)|  
|[Elemento MeasureGroupDimension](dimension-data-type-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[Elemento MiningStructure](../objects/miningstructure-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), o [DimensionBinding](dimensionbinding-data-type-assl.md)|  
|[Partizione](../objects/partition-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [TabularBinding](tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[Origine](../properties/source-element-binding-assl.md)|Tipo dei `Binding` deve essere [AttributeBinding](binding-data-type-assl.md), [tipo di dati CubeAttributeBinding &#40;ASSL&#41;](cubeattributebinding-data-type-assl.md), oppure [tipo di dati MeasureBinding &#40;ASSL&#41;](measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/sourcemeasuregroup-element-assl.md)|Tipo dei `Binding` deve essere [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
