---
title: Elemento OrderByAttributeID (ASSL) | Documenti Microsoft
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
- OrderByAttributeID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OrderByAttributeID
helpviewer_keywords:
- OrderByAttributeID element
ms.assetid: 41d7b650-ac40-4f1a-850d-2f81a19b28cb
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 42d8e9246340b72fad871e92bc30008c68ce786a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158300"
---
# <a name="orderbyattributeid-element-assl"></a>Elemento OrderByAttributeID (ASSL)
  Identifica un altro attributo in base al quale ordinare i membri del [dimensione](../data-type/dimensionattribute-data-type-assl.md) attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderByAttributeID>...</OrderByAttributeID>  
   ...  
</DimensionAttribute>  
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
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il `OrderByAttributeID` elemento viene utilizzato solo quando il valore della [OrderBy](orderby-element-assl.md) elemento per il `DimensionAttribute` è impostato su *AttributeKey* o *AttributeName*.  
  
 L'elemento che corrisponde al padre di `OrderByAttributeID` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  