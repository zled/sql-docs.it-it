---
title: Elemento KPI (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Kpi Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpi
helpviewer_keywords:
- Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 63b7947785976d41cda112b1c14b3829e3f98e3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124151"
---
# <a name="kpi-element-assl"></a>Elemento Kpi (ASSL)
  Definisce un indicatore di prestazioni chiave (KPI) all'interno di un [cubo](cube-element-assl.md) elemento o una [prospettiva](perspective-element-assl.md) elemento.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|None|  
|[Punto di vista](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Indicatori KPI](../collections/kpis-element-assl.md)|  
  
## <a name="child-elements"></a>Elementi figlio  
  
|Predecessore o padre|Elementi figlio|  
|------------------------|--------------------|  
|[Cubo](../collections/annotations-element-assl.md), [AssociatedMeasureGroupID](../properties/id-element-assl.md), [CurrentTimeMember](member-element-assl.md), [descrizione](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Obiettivo](../properties/goal-element-assl.md), [ID](../properties/id-element-assl.md), [Name](../properties/name-element-assl.md), [stato](../properties/status-element-assl.md), [StatusGraphic](../properties/statusgraphic-element-assl.md), [traduzioni ](../collections/translations-element-assl.md), [Tendenza](../properties/trend-element-assl.md), [TrendGraphic](../properties/trendgraphic-element-assl.md), [valore](../properties/value-element-assl.md)|  
|[Punto di vista](perspective-element-assl.md)|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Kpi> e <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
