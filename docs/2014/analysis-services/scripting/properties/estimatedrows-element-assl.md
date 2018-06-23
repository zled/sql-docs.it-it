---
title: Elemento EstimatedRows (ASSL) | Documenti Microsoft
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
- EstimatedRows Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EstimatedRows
helpviewer_keywords:
- EstimatedRows element
ms.assetid: 08a66481-6479-4a93-aa7e-15e8b1f854f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0348e39cf3528c34028677a22c2bf7ec25697705
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156279"
---
# <a name="estimatedrows-element-assl"></a>Elemento EstimatedRows (ASSL)
  Contiene il numero stimato di righe rappresentate dall'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationDesign> <!-- or Cube, MeasureGroup, MeasureGroupBinding, Partition -->  
   ...  
   <EstimatedRows>...</EstimatedRows>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Long|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationDesign](../objects/aggregationdesign-element-assl.md), [cubo](../objects/cube-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Gli elementi che corrispondono agli elementi padre di `EstimatedRows` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AggregationDesign>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding> e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  