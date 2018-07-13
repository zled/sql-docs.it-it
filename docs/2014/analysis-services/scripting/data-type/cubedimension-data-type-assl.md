---
title: Tipo di dati CubeDimension (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a02ef89f5dac200450faf8151a71aeae703e8b35
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220322"
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
|Elementi figlio|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [gli attributi](../collections/attributes-element-assl.md), [DimensionID](../properties/id-element-assl.md), [gerarchie](../collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md), [ID](../properties/id-element-assl.md), [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md), [Name](../properties/name-element-assl.md), [visibile](../properties/visible-element-assl.md), [Traduzioni](../collections/translations-element-assl.md)|  
|Elementi derivati|[Dimensione](../objects/dimension-element-assl.md) ([quote](../collections/dimensions-element-assl.md) insieme [cubo](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Note  
 Per ogni relazione per le dimensioni in un elemento `CubeDimension` è presente un solo elemento `Cube`. `CubeDimension` include tutti gli elementi `MeasureGroups` del cubo.  
  
 Oggetto `CubeDimension` deve includere una [CubeHierarchy](hierarchy-data-type-assl.md) se la dimensione fornisce informazioni specifiche da dire sulla gerarchia, inclusi la disabilitazione della gerarchia (consentendo in tal modo, selezione delle gerarchie applicate a un particolare utilizzo dimensioni), o invisibili della gerarchia.  
  
 Analogamente, un `CubeDimension` deve includere una [CubeAttribute](cubeattribute-data-type-assl.md) solo se la dimensione fornisce informazioni specifiche sull'attributo. Non è possibile in alcun modo selezionare gli attributi applicati a un utilizzo delle dimensioni specifico, ma gli attributi possono essere resi invisibili.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
