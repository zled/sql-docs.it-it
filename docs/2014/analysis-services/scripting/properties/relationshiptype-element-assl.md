---
title: Elemento RelationshipType (ASSL) | Documenti Microsoft
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
- RelationshipType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RelationshipType
helpviewer_keywords:
- RelationshipType element
ms.assetid: 72e1ab0e-a95d-4ebe-857d-21de1bf9fe03
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a2e5b5ec9e9591a45a80f099397ed6568a986313
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169515"
---
# <a name="relationshiptype-element-assl"></a>Elemento RelationshipType (ASSL)
  Indica se le relazioni tra membri per un [AttributeRelationship](../objects/attributerelationship-element-assl.md) può essere modificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <RelationshipType>...</RelationshipType>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Flessibile*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Oggetto AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Rigida*|Le relazioni dei membri tra un attributo e un attributo correlato non possono essere modificate.|  
|*Flessibile*|Le relazioni dei membri tra un attributo e un attributo correlato possono essere modificate.|  
  
 Ad esempio, se `ZipCode` non è possibile modificare da uno `City` a un'altra, la relazione dal `ZipCode` a `City` è contrassegnata come *rigida*.  
  
 L'enumerazione che corrisponde ai valori consentiti di `RelationshipType` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  