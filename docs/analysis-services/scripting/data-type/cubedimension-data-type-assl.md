---
title: Il tipo di dati CubeDimension (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0910e7bbad6797a2e34c9684589a47203bde0b30
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="cubedimension-data-type-assl"></a>Tipo di dati CubeDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[AllMemberAggregationUsage](../../../analysis-services/scripting/properties/allmemberaggregationusage-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [attributi](../../../analysis-services/scripting/collections/attributes-element-assl.md), [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md), [gerarchie](../../../analysis-services/scripting/collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../../../analysis-services/scripting/properties/hierarchyuniquenamestyle-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [MemberUniqueNameStyle](../../../analysis-services/scripting/properties/memberuniquenamestyle-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [visibile](../../../analysis-services/scripting/properties/visible-element-assl.md), [traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Elementi derivati|[Dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md) insieme di [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 È presente **CubeDimension** per ogni relazione tra dimensioni in un **cubo**. Il **CubeDimension** include tutte le **MeasureGroups** del cubo.  
  
 Oggetto **CubeDimension** deve includere un [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md) se la dimensione fornisce informazioni specifiche di pronunciare sulla gerarchia, inclusi la disabilitazione della gerarchia (in tal modo, consente di selezionare quale gerarchie si applicano a un determinato utilizzo delle dimensioni), o invisibili della gerarchia.  
  
 Analogamente, un **CubeDimension** deve includere un [CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md) solo se la dimensione fornisce informazioni specifiche sull'attributo. Non è possibile in alcun modo selezionare gli attributi applicati a un utilizzo delle dimensioni specifico, ma gli attributi possono essere resi invisibili.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
