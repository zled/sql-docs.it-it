---
title: Elemento MembersWithDataCaption (ASSL) | Microsoft Docs
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
- MembersWithDataCaption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithDataCaption
helpviewer_keywords:
- MembersWithDataCaption element
ms.assetid: a5d59efd-5d67-485b-a360-67d54a1fe394
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd8884d67717267e44751841203ce2f73d07ecfb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202301"
---
# <a name="memberswithdatacaption-element-assl"></a>Elemento MembersWithDataCaption (ASSL)
  Fornisce una stringa modello usata per la creazione di didascalie per i membri dei dati generati dal sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
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
|Elementi padre|[AttributeTranslation](../data-type/translation-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore del `MembersWithDataCaption` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore della [utilizzo](usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` elemento padre è impostato su *padre*) per determinare il didascalia di membri dati nell'attributo padre. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Gli elementi che corrispondono ai padri di `MembersWithDataCaption` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AttributeTranslation> e <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MembersWithData &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Tipo di dati AttributeTranslation &#40;ASSL&#41;](../data-type/translation-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
