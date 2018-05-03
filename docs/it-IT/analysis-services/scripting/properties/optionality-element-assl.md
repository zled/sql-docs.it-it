---
title: Elemento optionality (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Optionality Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Optionality element
ms.assetid: 6cd2ef0a-6fbe-4462-ab27-4cdfeb33f8ab
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de9f8dbef5d68fdd7041d45e88b7f25d893830d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="optionality-element-assl"></a>Elemento Optionality (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indica la natura facoltativa dei membri di un [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Obbligatorio*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Oggetto AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Obbligatorio*|Ogni membro nell'attributo correlato deve essere associato almeno un membro nell'attributo che possiede il **AttributeRelationship** elemento.|  
|*Facoltativo*|Ogni membro nell'attributo correlato non deve essere associato almeno un membro nell'attributo che possiede il **AttributeRelationship** elemento.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **cardinalità** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
