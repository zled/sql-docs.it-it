---
title: Elemento Aggregations (ASSL) | Documenti Microsoft
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
manager: kfile
ms.openlocfilehash: d4de0c42e0f03a1539aab76f82a2bcc0a5c860d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="aggregations-element-assl"></a>Elemento Aggregations (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Elemento MeasureGroup &#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [Elemento di partizione &#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
