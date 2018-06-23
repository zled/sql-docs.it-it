---
title: Tipo di dati CubeHierarchy (ASSL) | Documenti Microsoft
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
- CubeHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeHierarchy
helpviewer_keywords:
- CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48176b4096b7fa7ba8e1847750410be0f65da552
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155861"
---
# <a name="cubehierarchy-data-type-assl"></a>Tipo di dati CubeHierarchy (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le informazioni su un [gerarchia](../objects/hierarchy-element-assl.md) elemento in un [cubo](../objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|Elementi figlio|[Annotazioni](../collections/annotations-element-assl.md), [abilitata](../properties/enabled-element-assl.md), [HierarchyID](../properties/id-element-assl.md), [nome](../properties/name-element-assl.md), [OptimizedState](../properties/state-element-assl.md), [visibile](../properties/visible-element-assl.md)|  
|Elementi derivati|[Gerarchia](../objects/hierarchy-element-assl.md) ([gerarchie](../collections/hierarchies-element-assl.md) insieme [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 Questo tipo di dati non presenta alcuna restrizione e può essere utilizzato in qualsiasi modalità di distribuzione: 0-Multidimensionale e Data Mining, 1-SharePoint e 2-Tabulare.  
  
 In [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)], il *Enabled* proprietà non può essere impostata su `False` per *CubeHierarchy*.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Discover &#40;XMLA&#41;](../../xmla/xml-elements-methods-discover.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  