---
title: Tipo di dati RelationshipEnd (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 3a974dd4-e1d6-45b2-b8c8-1a914bc13a02
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23d0fce8a0856c178ef6933093400ca67ea4f9d3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197544"
---
# <a name="relationshipend-data-type-assl"></a>Tipo di dati RelationshipEnd (ASSL)
  Definisce un tipo di dati primitivo che rappresenta un elemento End di una relazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEnd>  
   <Role>...</Role>  
   <Multiplicity>...</Multiplicity>  
   <DimensionID>...</DimensionID>  
   <Attributes>...</Attributes>  
   <Translations>...</Translations>  
   <VisualizationProperties>...</VisualizationProperties>  
</Relationship>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Relazione](relationship-data-type-assl.md)|  
|Elementi figlio|[Ruolo](../../xmla/xml-elements-properties/role-element-xmla.md), [molteplicità](../properties/multiplicity-element-assl.md), [DimensionID](../properties/id-element-assl.md), [attributi](../collections/attributes-element-assl.md), [traduzioni](../collections/translations-element-assl.md), [ VisualizationProperties](relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementi derivati||  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.RelationshipEnd>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
