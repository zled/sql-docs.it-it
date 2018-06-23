---
title: Tipo di dati MeasureGroupBinding (out-of-line) (ASSL) | Documenti Microsoft
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
- MeasureGroupBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupBinding
helpviewer_keywords:
- MeasureGroupBinding data type
ms.assetid: e6c65597-89ac-457e-a0e5-01d85449a1b7
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4c467267028e60910be01466754648e216c685d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067758"
---
# <a name="measuregroupbinding-data-type-out-of-line-assl"></a>Tipo di dati MeasureGroupBinding (out-of-line) (ASSL)
  Definisce un tipo di dati primitivo che rappresenta un'associazione a un gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupBinding>  
   <ID>...</ID>  
   <Source>...</Source>  
   <EstimatedRows>...</EstimatedRows>  
   <Dimensions>...</Dimensions>  
   <Measures>...</Measures>  
      <Partitions>...</Partitions>  
</MeasureGroupBinding>  
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
|Elementi figlio|[Le dimensioni](../collections/dimensions-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [ID](../properties/id-element-assl.md), [misure](../collections/measures-element-assl.md), [partizioni](../collections/partitions-element-assl.md), [origine](../properties/source-element-binding-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Per altre informazioni, vedere la sezione, delle associazioni Line, in [origini dati e le associazioni &#40;multidimensionali SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  