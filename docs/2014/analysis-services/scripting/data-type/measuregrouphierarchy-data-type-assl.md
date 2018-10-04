---
title: Tipo di dati MeasureGroupHierarchy (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroupHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupHierarchy
helpviewer_keywords:
- MeasureGroupHierarchy data type
ms.assetid: 63c2fd97-d7ad-4715-8c49-24d684bc92d7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d2dafbeb5f423836c444490c21134cc64a402e6c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133351"
---
# <a name="measuregrouphierarchy-data-type-assl"></a>Tipo di dati MeasureGroupHierarchy (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le informazioni su una gerarchia in un gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupHierarchy>  
   <HierarchyID>...</HierarchyID>  
      <Annotations>...</Annotations>  
</MeasureGroupHierarchy>  
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
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [HierarchyID](../properties/id-element-assl.md)|  
|Elementi derivati|[Gerarchia](../objects/hierarchy-element-assl.md) ([gerarchie](../collections/hierarchies-element-assl.md) insieme [RegularMeasureGroupDimension](dimension-data-type-assl.md))|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
