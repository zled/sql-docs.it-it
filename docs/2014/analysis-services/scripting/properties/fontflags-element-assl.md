---
title: Elemento FontFlags (ASSL) | Microsoft Docs
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
- FontFlags Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FontFlags
helpviewer_keywords:
- FontFlags element
ms.assetid: ea608da9-ab05-42ab-8872-c52cd9f3f546
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1896d01c47f7c2e2fa4289f09c10ef859eff1d4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156842"
---
# <a name="fontflags-element-assl"></a>Elemento FontFlags (ASSL)
  Descrive le caratteristiche di visualizzazione correlate al carattere la [CalculationProperty](../objects/calculationproperty-element-assl.md) oppure [misura](../objects/measure-element-assl.md) elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
      <FontFlags>...</FontFlags>  
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
|Elementi padre|[CalculationProperty](../objects/calculationproperty-element-assl.md), [misura](../objects/measure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `FontFlags` proprietà contiene un'espressione MDX (Multidimensional Expressions) e si applica a `CalculationProperty` gli elementi aventi un [CalculationType](calculationtype-element-assl.md) dei *membro* o *celle* .  
  
 Gli elementi che corrispondono ai padri di `FontFlags` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CalculationProperty> e <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
