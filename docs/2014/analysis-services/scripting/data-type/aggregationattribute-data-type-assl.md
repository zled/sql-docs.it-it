---
title: Tipo di dati AggregationAttribute (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationAttribute
helpviewer_keywords:
- AggregationAttribute data type
ms.assetid: 636827c7-938d-4b7d-9827-46da3bc60d9a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05b0f2f1bc4ed517c289cb4e68810265118d9ea7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078671"
---
# <a name="aggregationattribute-data-type-assl"></a>Tipo di dati AggregationAttribute (ASSL)
  Definisce un tipo di dati primitivo che rappresenta l'associazione tra un [aggregazione](../objects/aggregation-element-assl.md) elemento e un attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationAttribute>  
   <AttributeID>...</AttributeID>  
      <Annotations>...</Annotations>  
</AggregationAttribute>  
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
|Elementi figlio|[Elemento AttributeID](../properties/id-element-assl.md), [annotazioni](../collections/annotations-element-assl.md)|  
|Elementi derivati|[Attributo](../objects/attribute-element-assl.md) ([attributi](../collections/attributes-element-assl.md) insieme [AggregationDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Note  
 La classe corrispondente nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.AggregationAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento aggregation &#40;ASSL&#41;](../objects/aggregation-element-assl.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
