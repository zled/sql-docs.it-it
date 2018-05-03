---
title: Elemento AttributeRelationship (ASSL) | Documenti Microsoft
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
- AttributeRelationship Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MemberProperty
helpviewer_keywords:
- AttributeRelationship element
ms.assetid: 2e786109-b8bf-4295-b0fe-9c1997349993
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8bc481663330502d82a2691c9fd43d3e176dccad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="attributerelationship-element-assl"></a>Elemento AttributeRelationship (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AttributeRelationships](../../../analysis-services/scripting/collections/attributerelationships-element-assl.md)|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [cardinalità](../../../analysis-services/scripting/properties/cardinality-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [Facoltatività](../../../analysis-services/scripting/properties/optionality-element-assl.md), [OverrideBehavior ](../../../analysis-services/scripting/properties/overridebehavior-element-assl.md), [RelationshipType](../../../analysis-services/scripting/properties/relationshiptype-element-assl.md), [traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md), [visibile](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributeRelationship>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
