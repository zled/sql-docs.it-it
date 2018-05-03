---
title: Dimensioni elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
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
- Dimensions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Dimensions
helpviewer_keywords:
- Dimensions element
ms.assetid: 104e3154-92e9-4c6b-9cf3-e3f3fc712b28
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d26e194155f0c9ae1be102116bb8d2a1bfa4808c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dimensions-element-assl"></a>Elemento Dimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di dimensioni associate all'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database> <!-- or Aggregation, AggregationDesign, AggregationInstance, Cube, MeasureGroup, Perspective -->  
   ...  
   <Dimensions>  
      <Dimension>...</Dimension>  
   </Dimensions>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Aggregazione](../../../analysis-services/scripting/objects/aggregation-element-assl.md), [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md), [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), [Database](../../../analysis-services/scripting/objects/database-element-assl.md), [ MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Elementi figlio|[Dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
