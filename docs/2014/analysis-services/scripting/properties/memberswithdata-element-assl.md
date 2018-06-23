---
title: Elemento MembersWithData (ASSL) | Documenti Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5c0311a774b225234aeb63d4d67680e12b693b0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167942"
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
  
## <a name="remarks"></a>Remarks  
 Il valore della `MembersWithData` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` elemento padre è impostato su *padre*) per determinare se Per visualizzare i membri di dati per i membri non foglia nell'attributo padre. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
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
  
  