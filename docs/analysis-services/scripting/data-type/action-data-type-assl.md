---
title: Tipo di dati Action (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed8742f9a7f0544baf65a9f51f9e510eb4855e1d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="action-data-type-assl"></a>Tipo di dati Action (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo astratto che rappresenta un'azione in un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento o un [prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md) elemento.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md), [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Azioni](../../../analysis-services/scripting/collections/actions-element-assl.md)|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [applicazione](../../../analysis-services/scripting/properties/application-element-assl.md), [didascalia](../../../analysis-services/scripting/properties/caption-element-assl.md), [CaptionIsMdx](../../../analysis-services/scripting/properties/captionismdx-element-assl.md), [condizione](../../../analysis-services/scripting/properties/condition-element-assl.md), [descrizione ](../../../analysis-services/scripting/properties/description-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [chiamata](../../../analysis-services/scripting/properties/invocation-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [destinazione](../../../analysis-services/scripting/properties/target-element-assl.md), [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md), [Traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md), [tipo](../../../analysis-services/scripting/properties/type-element-action-assl.md)|  
|Elementi derivati|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md), [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per altre informazioni sulle azioni, vedere [Azioni &#40;Analysis Services - Dati multidimensionali&41#;](../../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Elemento Perspective & #40; ASSL & #41;](../../../analysis-services/scripting/objects/perspective-element-assl.md)   
 [Tipo di dati PerspectiveAction & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
