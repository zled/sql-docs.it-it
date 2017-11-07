---
title: Associazione del tipo di dati (ASSL) | Documenti Microsoft
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
- Binding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- BINDING
helpviewer_keywords:
- Binding data type
ms.assetid: 0a777219-b885-4961-ac66-b76faeb520db
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d252931193ef06109c1d353ddc8fa42b3e4b6dfb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="binding-data-type-assl"></a>Tipo di dati Binding (ASSL)
  Definisce un tipo di dati primitivo astratto che rappresenta una relazione di dipendenza tra due oggetti in cui i dati o i metadati di un oggetto dipendono dai dati o dai metadati di un oggetto associato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md), [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md), [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md), [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md), [TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md), [TimeAttributeBinding](../../../analysis-services/scripting/data-type/timeattributebinding-data-type-assl.md), [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md), [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|Nessuno|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Binding>.  
  
 Per ulteriori informazioni sull'associazione dati, vedere [origini dati e associazioni &#40; SSAS multidimensionale &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Elementi di tipo Binding  
 Nella tabella seguente sono elencati gli elementi di tipo **associazione**.  
  
|Elemento padre|Elemento di tipo **associazione**|Commenti|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md) di [CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md) (di tipo [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|Tipo di **associazione** deve essere [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) o [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (out-of-line)](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|Tipo di **associazione** deve essere [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|**Associazione** possono essere di qualsiasi tipo|  
|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), o [ TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) o [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|[Colonna](../../../analysis-services/scripting/objects/column-element-assl.md)|Tipo di **associazione** deve essere [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md) o [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[Misura](../../../analysis-services/scripting/objects/measure-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md) (di tipo [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|Tipo di **associazione** deve essere [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), o [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|  
|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md) di [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) (di tipo [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|Tipo di **associazione** deve essere [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) o [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), o [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|Tipo di **associazione** deve essere [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Misura](../../../analysis-services/scripting/objects/measure-element-assl.md)|Tipo di **associazione** deve essere [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Partizione](../../../analysis-services/scripting/objects/partition-element-assl.md)|Tipo di **associazione** deve essere [PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (out-of-line)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), o [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|  
|[Partizione](../../../analysis-services/scripting/objects/partition-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Tipo di **associazione** deve essere [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md), [il tipo di dati CubeAttributeBinding &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md), o [tipo di dati MeasureBinding &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[SourceMeasureGroup](../../../analysis-services/scripting/objects/sourcemeasuregroup-element-assl.md)|Tipo di **associazione** deve essere [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

