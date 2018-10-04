---
title: Tipo di elemento (MeasureGroupAttribute) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (MeasureGroupAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 93740504-297a-4a06-ab3e-b598e466eebb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dfe3b0cda9061e18b9a275eac98e02ed90453adc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087919"
---
# <a name="type-element-measuregroupattribute-assl"></a>Elemento tipo (MeasureGroupAttribute) (ASSL)
  Contiene il tipo di un [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupAttribute>  
   ...  
   <Type>...</Type>  
   ...  
</MeasureGroupAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regolare*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Regolare*|Rappresenta un attributo regolare.|  
|*granularità*|Rappresenta un attributo di granularità.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Type` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MeasureGroupAttributeType>.  
  
 L'elemento che corrisponde al padre di `Type` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Attributes &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Tipo di dati RegularMeasureGroupDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
