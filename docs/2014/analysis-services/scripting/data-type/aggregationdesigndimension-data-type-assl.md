---
title: Tipo di dati AggregationDesignDimension (ASSL) | Microsoft Docs
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
- AggregationDesignDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesignDimension
helpviewer_keywords:
- AggregationDesignDimension data type
ms.assetid: 06a0d418-014c-4f40-a63a-5cfeee3f6a41
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74a28002d7074ad58c044b4af57310c22518a87d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247251"
---
# <a name="aggregationdesigndimension-data-type-assl"></a>Tipo di dati AggregationDesignDimension (ASSL)
  Definisce un tipo di dati primitivo che rappresenta la relazione tra una dimensione del cubo e un [AggregationDesign](../objects/aggregationdesign-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationDesignDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDesignDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [attributi](../collections/attributes-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md)|  
|Elementi derivati|[Dimensione](../objects/dimension-element-assl.md) ([quote](../collections/dimensions-element-assl.md) insieme [AggregationDesign](../objects/aggregationdesign-element-assl.md))|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationDesignDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AggregationDesign &#40;ASSL&#41;](../objects/aggregationdesign-element-assl.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
