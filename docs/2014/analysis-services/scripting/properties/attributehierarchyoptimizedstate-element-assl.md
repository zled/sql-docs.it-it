---
title: Elemento AttributeHierarchyOptimizedState (ASSL) | Documenti Microsoft
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
- AttributeHierarchyOptimizedState Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyOptimizedState
helpviewer_keywords:
- AttributeHierarchyOptimizedState element
ms.assetid: d87148c8-2011-45ae-94c3-851f48babc5f
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 027bd8713038fd1b090697d8891f93eaabc11f9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054370"
---
# <a name="attributehierarchyoptimizedstate-element-assl"></a>Elemento AttributeHierarchyOptimizedState (ASSL)
  Determina il livello di ottimizzazione applicato alla gerarchia dell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyOptimizedState>...  
   </AttributeHierarchyOptimizedState>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*FullyOptimized*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*FullyOptimized*|L'istanza compila indici per la gerarchia dell'attributo allo scopo di migliorare le prestazioni di esecuzione delle query.|  
|*NotOptimized*|L'istanza non compila indici aggiuntivi.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `AttributeHierarchyOptimizedState` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.OptimizationType>. Gli elementi che corrispondono agli elementi padre di `AttributeHierarchyOptimizedState` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CubeAttribute> e <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  