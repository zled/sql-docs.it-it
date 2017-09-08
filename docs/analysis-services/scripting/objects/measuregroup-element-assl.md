---
title: Elemento MeasureGroup (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MeasureGroup Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureGroup
helpviewer_keywords:
- MeasureGroup element
ms.assetid: 7aa099db-5dc7-4cac-b437-f73fc0921b24
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5232a3299f269d6f798523d934ca80cff21097df
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="measuregroup-element-assl"></a>Elemento MeasureGroup (ASSL)
  Definisce un set di misure allo stesso livello di granularità.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroups>  
   <MeasureGroup> <!-- ancestor: Cube -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</<Create  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Type>...</Type>  
      <State>...</State>  
      <MeasureQualification>...</MeasureQualification>  
      <Measures>...</Measures>  
      <DataAggregation>...</DataAggregation>  
      <Source>...</Source>  
            <StorageMode>...</StorageMode>  
      <StorageLocation>...</StorageLocation>  
      <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
            <ProactiveCaching>...</ProactiveCaching>  
      <EstimatedRows>...</EstimatedRows>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <EstimatedSize>...</EstimatedSize>  
      <ProcessingMode>...</ProcessingMode>  
      <Dimensions>...</Dimensions>  
      <Partitions>...</Partitions>  
      <AggregationPrefix>...</AggregationPrefix>  
      <ProcessingPriority>...</ProcessingPriority>  
            <AggregationDesigns>...</AggregationDesigns>  
      <Annotations>...</Annotations>  
   </MeasureGroup>  
   <!-- or  -->  
   <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- ancestor: CubeBinding -->  
   <!-- or  -->  
   <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- ancestor: Perspective -->  
</MeasureGroups>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Vedere la tabella riportata di seguito.|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|Nessuno|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elementi MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Elementi figlio|  
|------------------------|--------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[AggregationDesigns](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md), [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [DataAggregation](../../../analysis-services/scripting/properties/dataaggregation-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md), [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md), [EstimatedSize](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [IgnoreUnrelatedDimensions](../../../analysis-services/scripting/properties/ignoreunrelateddimensions-element-assl.md), [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [MeasureQualification](../../../analysis-services/scripting/properties/measurequalificaton-element-assl.md), [misure](../../../analysis-services/scripting/collections/measures-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [Partizioni](../../../analysis-services/scripting/collections/partitions-element-assl.md), [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md), [ProcessingMode](../../../analysis-services/scripting/properties/processingmode-element-assl.md), [ProcessingPriority](../../../analysis-services/scripting/properties/processingpriority-element-assl.md), [origine](../../../analysis-services/scripting/properties/source-element-measure-assl.md), [stato](../../../analysis-services/scripting/properties/state-element-assl.md), [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md), [StorageMode](../../../analysis-services/scripting/properties/storagemode-element-assl.md), [traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md), [tipo](../../../analysis-services/scripting/properties/type-element-measuregroup-assl.md)|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|Nessuno|  
|[Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Tutte le misure di un gruppo di misure devono essere derivate da una singola tabella. Un gruppo di misure può definire associazioni predefinite che possono essere sostituite per ogni partizione.  
  
 L'elemento **MeasureGroup** definisce dettagli comuni ai gruppi di misure in cubi regolari e cubi virtuali. I diversi sottotipi definiscono i dettagli specifici di ogni tipo.  
  
 La proprietà **State** di un elemento **MeasureGroup** ha i valori seguenti:  
  
-   *FullyProcessed* se tutte le partizioni vengono elaborate.  
  
-   *PartiallyProcessed* se almeno una partizione viene elaborata.  
  
-   *Unprocessed* se nessuna partizione viene elaborata.  
  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.MeasureGroup> e <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
