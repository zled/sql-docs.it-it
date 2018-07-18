---
title: Elemento (ASSL) del cubo | Microsoft Docs
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
- Cube Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Cube
helpviewer_keywords:
- Cube element
ms.assetid: 2d801066-6cca-4a99-bbd8-56a38d762108
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eab8cc56de346540491664a60c644ef868b02a25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165262"
---
# <a name="cube-element-assl"></a>Elemento Cube (ASSL)
  Definisce un cubo regolare, virtuale o collegato in una [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [Database](database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cubes>  
   <Cube>  
            <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
            <Description>...</Description>  
            <Language>...</Language>  
            <Collation>...</Collation>  
            <Translations>...</Translations>  
      <Dimensions>...</Dimensions>  
            <CubePermissions>...</CubePermissions>  
      <MdxScripts>...</MdxScripts>  
      <Perspectives>...</Perspectives>  
      <State>...</State>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Visible>...</Visible>  
      <MeasureGroups>...</MeasureGroups>  
      <DataSourceView >...</Source>  
      <AggregationPrefix>...</AggregationPrefix>  
      <ProcessingPriority>...</ProcessingPriority>  
            <StorageMode>...</StorageMode>  
      <ProcessingMode>...</ProcessingMode>  
      <ScriptCacheProcessingMode>...</ScriptCacheProcessingMode>  
      <ProactiveCaching>...</ProactiveCaching>  
            <Kpis>...</Kpis>  
            <ErrorConfiguration>...</ErrorConfiguration>  
            <Actions>...</Actions>  
      <StorageLocation>...</StorageLocation>  
      <EstimatedRows>...</EstimatedRows>  
      <LastProcessed>...</LastProcessed>  
      <Annotations>...</Annotations>  
   </Cube>  
</Cubes>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubi](../collections/cubes-element-assl.md)|  
|Elementi figlio|[Le azioni](../collections/actions-element-assl.md), [AggregationPrefix](../properties/aggregationprefix-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [delle regole di confronto](../properties/collation-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [ CubePermissions](../collections/cubepermissions-element-assl.md), [DefaultMeasure](measure-element-assl.md), [descrizione](../properties/description-element-assl.md), [dimensioni](../collections/dimensions-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md) , [EstimatedRows](../properties/estimatedrows-element-assl.md), [ID](../properties/id-element-assl.md), [KPI](../collections/kpis-element-assl.md), [lingua](../properties/language-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [ LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MdxScripts](../collections/mdxscripts-element-assl.md), [MeasureGroups](../collections/groups-element-assl.md), [nome](../properties/name-element-assl.md), [prospettive](../collections/perspectives-element-assl.md), [ProactiveCaching](proactivecaching-element-assl.md), [ProcessingMode](../properties/processingmode-element-assl.md), [ProcessingPriority](../properties/processingpriority-element-assl.md), [ScriptCacheProcessingMode](../properties/scriptcacheprocessingmode-element-assl.md), [dello stato ](../properties/state-element-assl.md), [StorageLocation](../properties/storagelocation-element-assl.md), [StorageMode](../properties/storagemode-element-assl.md), [traduzioni](../collections/translations-element-assl.md), [visibili](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Cube>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
