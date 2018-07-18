---
title: Elemento Calculationproperty (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CalculationProperties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationProperties
helpviewer_keywords:
- CalculationProperties element
ms.assetid: dccfe036-0b1b-4877-8bdd-4b128ccb55c9
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d28f9c0b2c11cd317db723317ebc356d8847aea
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200121"
---
# <a name="calculationproperties-element-assl"></a>Elemento CalculationProperty (ASSL)
  Contiene la raccolta di [CalculationProperty](../objects/calculationproperty-element-assl.md) gli elementi associati a un [MdxScript](../objects/mdxscript-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MdxScript>  
   ...  
   <CalculationProperties>  
      <CalculationProperty>...</CalculationProperty>  
   </CalculationProperties>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento MdxScript](../objects/mdxscript-element-assl.md)|  
|Elementi figlio|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CalculationPropertyCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
