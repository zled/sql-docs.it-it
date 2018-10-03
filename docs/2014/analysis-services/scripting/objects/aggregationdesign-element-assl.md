---
title: Elemento AggregationDesign (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationDesign Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesign
helpviewer_keywords:
- AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 430035dd83cf137cb80a5db5d159da027014e6c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075291"
---
# <a name="aggregationdesign-element-assl"></a>Elemento AggregationDesign (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationDesigns](../collections/aggregationdesigns-element-assl.md)|  
|Elementi figlio|[Le aggregazioni](../collections/aggregations-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [descrizione](../properties/description-element-assl.md), [dimensioni](../collections/dimensions-element-assl.md), [EstimatedPerformanceGain](../properties/estimatedperformancegain-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [ID](../properties/id-element-assl.md), [nome](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di partizione &#40;ASSL&#41;](partition-element-assl.md)   
 [Elemento aggregation &#40;ASSL&#41;](aggregation-element-assl.md)   
 [Elemento Aggregations &#40;ASSL&#41;](../collections/aggregations-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
