---
title: Elemento AttributeRelationship (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeRelationship Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MemberProperty
helpviewer_keywords:
- AttributeRelationship element
ms.assetid: 2e786109-b8bf-4295-b0fe-9c1997349993
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5c242f8946d2230bae9e40a847dd5cbe6f494603
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196831"
---
# <a name="attributerelationship-element-assl"></a>Elemento AttributeRelationship (ASSL)
  Fornisce informazioni dettagliate sulla relazione tra due attributi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeRelationships>  
      <AttributeRelationship>  
      <AttributeID>...</AttributeID>  
            <RelationshipType>...</RelationshipType>  
      <Cardinality>...</Cardinality>  
      <Optionality >...</Optionality>  
      <OverrideBehavior >...</OverrideBehavior>  
            <Annotations>...</Annotations>  
      <Name>...</Name>  
      <Visible>...</Visible>  
      <Translations>...</Translations>  
   </AttributeRelationship>  
</AttributeRelationships>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AttributeRelationships](../collections/relationships-element-assl.md)|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [AttributeID](../properties/id-element-assl.md), [cardinalità](../properties/cardinality-element-assl.md), [nome](../properties/name-element-assl.md), [Facoltatività](../properties/optionality-element-assl.md), [OverrideBehavior ](../properties/overridebehavior-element-assl.md), [RelationshipType](../properties/relationshiptype-element-assl.md), [traduzioni](../collections/translations-element-assl.md), [visibili](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributeRelationship>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
