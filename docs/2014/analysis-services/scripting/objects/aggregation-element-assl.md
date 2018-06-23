---
title: Elemento Aggregation (ASSL) | Documenti Microsoft
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
- Aggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aggregation
helpviewer_keywords:
- Aggregation element
ms.assetid: f37af388-b2b3-4234-a1d6-936ee9b7f2ae
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 59f33b45653f614702b1472e57fe4464cf172b73
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155856"
---
# <a name="aggregation-element-assl"></a>Elemento Aggregation (ASSL)
  Definisce una singola aggregazione per un [partizione](partition-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Aggregations>  
      <Aggregation>  
      <ID>...</ID>  
      <Name>...</Name>  
      <Dimensions>...</Dimensions>  
            <Annotations>...</Annotations>  
      <Description>...</Description>  
   </Aggregation>  
</Aggregations>  
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
|Elemento padre|[Aggregazioni](../collections/aggregations-element-assl.md)|  
|Elementi figlio|[Annotazioni](../collections/annotations-element-assl.md), [descrizione](../properties/description-element-assl.md), [dimensioni](../collections/dimensions-element-assl.md), [ID](../properties/id-element-assl.md), [nome](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Aggregation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di partizione &#40;ASSL&#41;](partition-element-assl.md)   
 [Elemento AggregationDesign &#40;ASSL&#41;](aggregationdesign-element-assl.md)   
 [Elemento MeasureGroup &#40;ASSL&#41;](group-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  