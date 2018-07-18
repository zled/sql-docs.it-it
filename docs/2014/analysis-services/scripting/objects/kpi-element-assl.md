---
title: Elemento KPI (ASSL) | Microsoft Docs
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
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27b0bcbe2ddaabcc7b3f9ef16f3fa620a8c2db38
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235641"
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
  
  
