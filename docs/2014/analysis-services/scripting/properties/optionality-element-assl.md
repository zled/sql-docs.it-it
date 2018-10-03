---
title: Elemento optionality (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Optionality Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Optionality element
ms.assetid: 6cd2ef0a-6fbe-4462-ab27-4cdfeb33f8ab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d59b04dad688d438ca2f4777b404dcc4fe8976b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099171"
---
# <a name="optionality-element-assl"></a>Elemento Optionality (ASSL)
  Indica la natura facoltativa dei membri per un [AttributeRelationship](../objects/attributerelationship-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*obbligatorio*|  
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
|*obbligatorio*|Ogni membro nell'attributo correlato deve essere associato ad almeno un membro nell'attributo che possiede l'elemento `AttributeRelationship`.|  
|*Facoltativo*|Ogni membro nell'attributo correlato non deve essere necessariamente associato ad almeno un membro nell'attributo che possiede l'elemento `AttributeRelationship`.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Cardinality` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
