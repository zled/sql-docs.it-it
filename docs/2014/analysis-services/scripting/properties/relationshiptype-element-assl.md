---
title: Elemento RelationshipType (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 21ddd4506a2c2a6168779aa40735eb7177406597
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271597"
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
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Rigida*|Le relazioni dei membri tra un attributo e un attributo correlato non possono essere modificate.|  
|*Flessibile*|Le relazioni dei membri tra un attributo e un attributo correlato possono essere modificate.|  
  
 Ad esempio, se `ZipCode` non è possibile passare da uno `City` a un altro, la relazione dal `ZipCode` a `City` è contrassegnato come *rigida*.  
  
 L'enumerazione che corrisponde ai valori consentiti di `RelationshipType` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
