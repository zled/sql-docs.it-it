---
title: Elemento Aggregations (ASSL) | Documenti Microsoft
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
- Aggregations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Aggregations
helpviewer_keywords:
- Aggregations element
ms.assetid: 79b7de7a-53b2-4202-bc0f-de1daaf1b179
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5ef3e8dc2ba27d7d016b236b36fd892e74ea434
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="aggregations-element-assl"></a>Elemento Aggregations (ASSL)
  Contiene la raccolta di aggregazioni definite per un [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationDesign>  
   ...  
   <Aggregations>  
      <Aggregation>...</Aggregation>  
   </Aggregations>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)|  
|Elementi figlio|[Aggregazione](../../../analysis-services/scripting/objects/aggregation-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MeasureGroup &#40; ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [Elemento Partition &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Raccolte &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
