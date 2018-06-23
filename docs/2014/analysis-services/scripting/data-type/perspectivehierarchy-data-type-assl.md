---
title: Tipo di dati PerspectiveHierarchy (ASSL) | Documenti Microsoft
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
- PerspectiveHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveHierarchy
helpviewer_keywords:
- PerspectiveHierarchy data type
ms.assetid: 30366bd0-ee1c-4940-8c1f-ca5e0dd5fe4b
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dddceea6ee82d02ef1a68953bd16d6fc728537ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171108"
---
# <a name="perspectivehierarchy-data-type-assl"></a>Tipo di dati PerspectiveHierarchy (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le informazioni su una gerarchia in una [PerspectiveDimension](dimension-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<PerspectiveHierarchy>  
   <HierarchyID>...</HierarchyID>  
      <Annotations>...</Annotations>  
</PerspectiveHierarchy>  
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
|Elementi figlio|[Annotazioni](../collections/annotations-element-assl.md), [HierarchyID](../properties/id-element-assl.md)|  
|Elementi derivati|[Gerarchia](../objects/hierarchy-element-assl.md) ([gerarchie](../collections/hierarchies-element-assl.md) insieme [PerspectiveDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.PerspectiveHierarchy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  