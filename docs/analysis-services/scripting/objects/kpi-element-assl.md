---
title: Elemento KPI (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Kpi Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Kpi
helpviewer_keywords: Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8d9725fb94595fde02b0f0d176f361dfd0875d8c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="kpi-element-assl"></a>Elemento Kpi (ASSL)
  Definisce un indicatore di prestazioni chiave (KPI) all'interno di un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento o un [prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Kpis>  
   <Kpi> <!-- ancestor: Cube -->  
            <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DisplayFolder>...</DisplayFolder>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <Value>...</Value>  
            <Goal>...</Goal>  
      <Status>...</Status>  
      <Trend>...</Trend>  
      <TrendGraphic>...</TrendGraphic>  
      <StatusGraphic>...</StatusGraphic>  
      <CurrentTimeMember>...</CurrentTimeMember>  
      <Annotations>...</Annotations>  
   </Kpi>  
   <!-- or -->  
   <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- ancestor: Perspective -->  
   </Kpi>  
</Kpis>  
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
|[Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[PerspectiveKpi](../../../analysis-services/scripting/data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Indicatori KPI](../../../analysis-services/scripting/collections/kpis-element-assl.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Elementi figlio|  
|------------------------|--------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AssociatedMeasureGroupID](../../../analysis-services/scripting/properties/associatedmeasuregroupid-element-assl.md), [CurrentTimeMember](../../../analysis-services/scripting/properties/currenttimemember-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md), [obiettivo](../../../analysis-services/scripting/properties/goal-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [stato](../../../analysis-services/scripting/properties/status-element-assl.md), [StatusGraphic](../../../analysis-services/scripting/properties/statusgraphic-element-assl.md), [traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md), [tendenza](../../../analysis-services/scripting/properties/trend-element-assl.md), [TrendGraphic](../../../analysis-services/scripting/properties/trendgraphic-element-assl.md), [valore](../../../analysis-services/scripting/properties/value-element-assl.md)|  
|[Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Kpi> e <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
