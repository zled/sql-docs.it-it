---
title: Tipo di dati CubeDimension (ASSL) | Documenti Microsoft
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
- CubeDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4a043895929e09a59d3ae14c5995804c4fa5c7eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055395"
---
# <a name="cubedimension-data-type-assl"></a>Tipo di dati CubeDimension (ASSL)
  Definisce un tipo di dati primitivo che rappresenta la relazione tra una dimensione e un cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [attributi](../collections/attributes-element-assl.md), [DimensionID](../properties/id-element-assl.md), [gerarchie](../collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md), [ID](../properties/id-element-assl.md), [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md), [nome](../properties/name-element-assl.md), [visibile](../properties/visible-element-assl.md), [Traduzioni](../collections/translations-element-assl.md)|  
|Elementi derivati|[Dimensione](../objects/dimension-element-assl.md) ([dimensioni](../collections/dimensions-element-assl.md) insieme [cubo](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 Per ogni relazione per le dimensioni in un elemento `CubeDimension` è presente un solo elemento `Cube`. `CubeDimension` include tutti gli elementi `MeasureGroups` del cubo.  
  
 Un `CubeDimension` deve includere un [CubeHierarchy](hierarchy-data-type-assl.md) se la dimensione fornisce informazioni specifiche di pronunciare sulla gerarchia, inclusi la disabilitazione della gerarchia (in tal modo, consentire la selezione delle gerarchie applicate a un determinato utilizzo dimensioni), o invisibilità della gerarchia.  
  
 Analogamente, un `CubeDimension` deve includere un [CubeAttribute](cubeattribute-data-type-assl.md) solo se la dimensione fornisce informazioni specifiche sull'attributo. Non è possibile in alcun modo selezionare gli attributi applicati a un utilizzo delle dimensioni specifico, ma gli attributi possono essere resi invisibili.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  