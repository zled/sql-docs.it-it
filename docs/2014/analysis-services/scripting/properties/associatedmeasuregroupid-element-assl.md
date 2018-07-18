---
title: Elemento AssociatedMeasureGroupID (ASSL) | Microsoft Docs
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
- AssociatedMeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AssociatedMeasureGroupID
helpviewer_keywords:
- AssociatedMeasureGroupID element
ms.assetid: a18ff25b-00a2-4ddf-abcc-ef4d52c8a462
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad28fbc5023c06bdc260e301732bfb1567ce27f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155332"
---
# <a name="associatedmeasuregroupid-element-assl"></a>Elemento AssociatedMeasureGroupID (ASSL)
  Contiene l'ID del [MeasureGroup](../objects/group-element-assl.md) elemento associato a un [CalculationProperty](../objects/calculationproperty-element-assl.md) elemento o un [Kpi](../objects/kpi-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty> <!-- or Kpi -->  
   ...  
   <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CalculationProperty](../objects/calculationproperty-element-assl.md), [Kpi](../objects/kpi-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Quando applicato a `CalculationProperty` elementi, il `AssociatedMeasureGroupID` proprietà si applica a elementi con un [CalculationType](calculationtype-element-assl.md) dei *membro*.  
  
 Gli elementi che corrispondono ai padri di `AssociatedMeasureGroupID` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CalculationProperty> e <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
