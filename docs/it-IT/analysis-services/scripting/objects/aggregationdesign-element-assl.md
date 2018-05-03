---
title: Elemento AggregationDesign (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregationDesign Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationDesign
helpviewer_keywords:
- AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b47f7bdedcd87b5dc90de314e4d03dc883b9928
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationdesign-element-assl"></a>Elemento AggregationDesign (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un set di definizioni di aggregazione che possono essere condivise tra più partizioni in un database.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationDesigns>  
   <AggregationDesign>  
      <ID>...</ID>  
      <Name>...</Name>  
            <Description>...</Description>  
      <EstimatedRows>...</EstimatedRows>  
      <Dimensions>...</Dimensions>  
            <Aggregations>...</Aggregation>  
      <EstimatedPerformanceGain>...</EstimatedPerformanceGain>  
      <Annotations>...</Annotations>  
   </AggregationDesign>  
</AggregationDesigns>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationDesigns](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md)|  
|Elementi figlio|[Le aggregazioni](../../../analysis-services/scripting/collections/aggregations-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [EstimatedPerformanceGain](../../../analysis-services/scripting/properties/estimatedperformancegain-element-assl.md), [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di partizione &#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Elemento Aggregation & #40; ASSL & #41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)   
 [Elemento Aggregations &#40;ASSL&#41;](../../../analysis-services/scripting/collections/aggregations-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
