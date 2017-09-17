---
title: Elemento CalculationType (ASSL) | Documenti Microsoft
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
- CalculationType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CalculationType
helpviewer_keywords:
- CalculationType element
ms.assetid: b974b3d3-fbf7-4d77-8f6e-4e05a258fe84
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35ef2ca152038a71474a62d2ae7a5b23678f1997
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="calculationtype-element-assl"></a>Elemento CalculationType (ASSL)
  Descrive il tipo di calcolo definito nell'oggetto associato [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationType>...</CalculationType>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Membro*|La proprietà di calcolo si applica alla definizione di un membro calcolato.|  
|*Set*|La proprietà di calcolo si applica alla definizione di un set denominato|  
|*Celle*|La proprietà di calcolo si applica alla definizione di una cella calcolata.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **CalculationType** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CalculationType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
