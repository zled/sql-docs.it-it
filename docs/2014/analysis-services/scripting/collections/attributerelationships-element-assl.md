---
title: Elemento AttributeRelationships (ASSL) | Microsoft Docs
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
- AttributeRelationships Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MemberProperties
helpviewer_keywords:
- AttributeRelationships element
ms.assetid: f2ff82f6-6a7f-481a-a1ef-014bef38face
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 357e9ed97ead13619fe66f4415290297feee7fb9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263657"
---
# <a name="attributerelationships-element-assl"></a>Elemento AttributeRelationships (ASSL)
  Contiene la raccolta di [AttributeRelationship](../objects/attributerelationship-element-assl.md) elementi per l'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <AttributeRelationships>  
      <AttributeRelationship>...</AttributeRelationship>  
   </AttributeRelationships>  
   ...  
</Attribute>  
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
|Elementi padre|[Attributo](../objects/attribute-element-assl.md) di tipo [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|[Oggetto AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributeRelationshipCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
