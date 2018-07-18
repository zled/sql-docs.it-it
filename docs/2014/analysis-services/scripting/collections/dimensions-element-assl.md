---
title: Dimensioni elemento (ASSL) | Microsoft Docs
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
- Dimensions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Dimensions
helpviewer_keywords:
- Dimensions element
ms.assetid: 104e3154-92e9-4c6b-9cf3-e3f3fc712b28
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ff15cecd5e5d4451a580d8ee73922dc4ab05364
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241611"
---
# <a name="dimensions-element-assl"></a>Elemento Dimensions (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Aggregazione](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [AggregationInstance](../objects/aggregationinstance-element-assl.md), [cubo](../objects/cube-element-assl.md), [Database](../objects/database-element-assl.md), [ Elemento MeasureGroup](../objects/group-element-assl.md), [prospettiva](../objects/perspective-element-assl.md)|  
|Elementi figlio|[Dimension](../objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
