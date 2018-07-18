---
title: Tipo di dati Action (ASSL) | Microsoft Docs
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
- Action Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Action data type
ms.assetid: 8c4d2ff7-17e1-4e74-bec7-637e0b191acf
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77b4ef3f8507d67090b78c00807278d0d7dc6348
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154972"
---
# <a name="action-data-type-assl"></a>Tipo di dati Action (ASSL)
  Definisce un tipo di dati primitivo astratto che rappresenta un'azione in un [cubo](../objects/cube-element-assl.md) elemento o una [prospettiva](../objects/perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Caption>...</Caption>  
      <CaptionIsMdx>...</CaptionIsMdx>  
      <Translations>...</Translations>  
   <TargetType>...</TargetType>  
   <Target>...</Target>  
   <Condition>...</Condition>  
   <Type>...</Type>  
   <Invocation>...</Invocation>  
   <Application>...</Application>  
      <Description>...</Description>  
      <Annotations>...</Annotations>  
</Action>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[DrillThroughAction](action-data-type-assl.md), [ReportAction](reportaction-data-type-assl.md), [StandardAction](standardaction-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Azioni](../collections/actions-element-assl.md)|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [Application](../properties/application-element-assl.md), [didascalia](../properties/caption-element-assl.md), [CaptionIsMdx](../properties/captionismdx-element-assl.md), [condizione](../properties/condition-element-assl.md), [descrizione ](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [chiamata](../properties/invocation-element-assl.md), [nome](../properties/name-element-assl.md), [destinazione](../properties/target-element-assl.md), [TargetType](../properties/targettype-element-assl.md), [Traduzioni](../collections/translations-element-assl.md), [tipo](../properties/type-element-action-assl.md)|  
|Elementi derivati|[DrillThroughAction](action-data-type-assl.md), [ReportAction](reportaction-data-type-assl.md), [StandardAction](standardaction-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sulle azioni, vedere [Azioni &#40;Analysis Services - Dati multidimensionali&41#;](../../multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento del cubo &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Elemento Perspective &#40;ASSL&#41;](../objects/perspective-element-assl.md)   
 [Tipo di dati PerspectiveAction &#40;ASSL&#41;](perspectiveaction-data-type-assl.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
