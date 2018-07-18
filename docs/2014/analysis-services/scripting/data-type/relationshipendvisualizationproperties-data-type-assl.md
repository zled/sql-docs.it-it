---
title: Tipo di dati RelationshipEndVisualizationProperties (ASSL) | Microsoft Docs
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
ms.assetid: 11f9a10f-d36c-4faf-b595-3fe969d1935e
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58348251e9ea00c4f6eebc5fcec067683e49a3a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161272"
---
# <a name="relationshipendvisualizationproperties-data-type-assl"></a>Tipo di dati RelationshipEndVisualizationProperties (ASSL)
  Definisce un tipo di dati primitivo che rappresenta un elemento End di una relazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEnd>  
   <FolderPosition>...</FolderPosition>  
   <ContextualNameRule>...</ContextualNameRule>  
   <DefaultDetailsPosition>...</DefaultDetailsPosition>  
   <DisplayKeyPosition>...</DisplayKeyPosition>  
   <CommonIdentifierPosition>...</CommonIdentifierPosition>  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
   <IsDefaultImage>...</IsDefaultImage>  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
</RelationshipEnd>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEnd](relationshipend-data-type-assl.md)|  
|Elementi figlio|[FolderPosition](../../xmla/xml-elements-properties/folderposition-element-xml.md), [ContextualNameRule](../../xmla/xml-elements-properties/contextualnamerule-element-xml.md), [DefaultDetailsPosition](../../xmla/xml-elements-properties/defaultdetailsposition-element-xml.md), [DisplayKeyPosition](../../xmla/xml-elements-properties/displaykeyposition-element-xml.md), [CommonIdentifierPosition ](../../xmla/xml-elements-properties/commonidentifierposition-element-xml.md), [IsDefaultMeasure](../../xmla/xml-elements-properties/isdefaultmeasure-element-xml.md), [IsDefaultImage](../../xmla/xml-elements-properties/isdefaultimage-element-xml.md), [SortPropertiesPosition](../../xmla/xml-elements-properties/sortpropertiesposition-element-xml.md)|  
|Elementi derivati||  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.RelationshipEnd>.  
  
  
