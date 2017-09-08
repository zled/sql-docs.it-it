---
title: Elemento AssociatedMeasureGroupID (ASSL) | Documenti Microsoft
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
- AssociatedMeasureGroupID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AssociatedMeasureGroupID
helpviewer_keywords:
- AssociatedMeasureGroupID element
ms.assetid: a18ff25b-00a2-4ddf-abcc-ef4d52c8a462
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 087d37ca42db39e3a8c040412c6a016d56aaf794
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="associatedmeasuregroupid-element-assl"></a>Elemento AssociatedMeasureGroupID (ASSL)
  Contiene l'ID del [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) elemento associato a un [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) elemento o un [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty> <!-- or Kpi -->  
   ...  
   <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Quando applicato a **CalculationProperty** elementi, il **AssociatedMeasureGroupID** proprietà si applica agli elementi con un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) di *membro* .  
  
 Gli elementi che corrispondono ai padri di **AssociatedMeasureGroupID** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.CalculationProperty> e <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
