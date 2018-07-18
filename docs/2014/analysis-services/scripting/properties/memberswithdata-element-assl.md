---
title: Elemento MembersWithData (ASSL) | Microsoft Docs
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
- MembersWithData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0c2e35549f4db2de489916ad1760954d4f6dfd5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218231"
---
# <a name="memberswithdata-element-assl"></a>Elemento MembersWithData (ASSL)
  Determina se visualizzare i membri dei dati per i membri non foglia nell'attributo padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*NonLeafDataVisible*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore del `MembersWithData` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore della [utilizzo](usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` elemento padre è impostato su *padre*) per determinare se Per visualizzare i membri di dati per i membri non foglia nell'attributo padre. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*NonLeafDataHidden*|I dati non foglia sono nascosti.|  
|*NonLeafDataVisible*|I dati non foglia sono visibili.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `MembersWithData` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MembersWithDataCaption &#40;ASSL&#41;](caption-element-assl.md)   
 [Tipo di dati DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
