---
title: Elemento Cardinality (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Cardinality Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Cardinality element
ms.assetid: 60ac8a26-7c8b-4011-9b9b-a29863779428
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7446923efc15a2fe05f3e8bf8c86a2e9f429a2c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325081"
---
# <a name="cardinality-element-assl"></a>Elemento Cardinality (ASSL)
  Indica la cardinalità della relazione descritta da un [AttributeRelationship](../objects/attributerelationship-element-assl.md) oppure [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeRelationship> <!-- or RegularMeasureGroupDimension -->  
   ...  
   <Cardinality>...</Cardinality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Molti*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Oggetto AttributeRelationship](../objects/attributerelationship-element-assl.md), [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Molti*|Relazione molti-a-uno|  
|*Uno*|Relazione uno-a-uno|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Cardinality` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.Cardinality>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
