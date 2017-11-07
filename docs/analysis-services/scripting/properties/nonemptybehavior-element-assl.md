---
title: Elemento NonEmptyBehavior (ASSL) | Documenti Microsoft
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
- NonEmptyBehavior Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NonEmptyBehavior
helpviewer_keywords:
- NonEmptyBehavior element
ms.assetid: b4c78af4-b049-4189-a35b-206e3938d1db
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bafd21bcaf9fc7ebfb06f6f37dbf87a0598cf31f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="nonemptybehavior-element-assl"></a>Elemento NonEmptyBehavior (ASSL)
  Determina il comportamento non vuoto associato al padre del [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty>  
  
   <NonEmptyBehavior>...</NonEmptyBehavior>  
  
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
|Elemento padre|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **NonEmptyBehavior** proprietà si applica a **CalculationProperty** gli elementi con un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) impostato su *membro*.  
  
 L'elemento che corrisponde all'elemento padre **NonEmptyBehavior** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

