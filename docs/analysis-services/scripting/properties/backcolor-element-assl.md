---
title: Elemento BackColor (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BackColor Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- BackColor
helpviewer_keywords:
- BackColor element
ms.assetid: 9024d131-74cc-4815-833a-f8cae57b7453
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8200729e8a2b9378a21b228b2ed3fd60863f40c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="backcolor-element-assl"></a>Elemento BackColor (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive le caratteristiche di visualizzazione dell'elemento padre correlate al colore.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <BackColor>...</BackColor>  
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
|Elemento padre|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [misura](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **BackColor** proprietà contiene un'espressione del linguaggio MDX (Multidimensional Expressions) e si applica a **CalculationProperty** gli elementi con un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) di *membro* o *celle*.  
  
 L'elemento che corrisponde all'elemento padre **BackColor** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
