---
title: Elemento MeasureGroupID (ASSL) | Microsoft Docs
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
- MeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupID
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: 3b075f86-dbbc-4285-8d2d-61fa722181c7
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 45ec91eee187e7ea0264eded7c92954822b49810
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37239641"
---
# <a name="measuregroupid-element-assl"></a>Elemento MeasureGroupID (ASSL)
  Associa un [MeasureGroup](../objects/group-element-assl.md) con l'elemento padre, associazione o associazione out-of-line.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ManyToManyMeasureGroupDimension> <!-- or MeasureGroupAttributeBinding, MeasureGroupBinding, PerspectiveMeasureGroup -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità||  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
|Elementi figlio - padre o predecessore|Cardinalità|  
|------------------------------------------|-----------------|  
|[ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
|[MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md) e [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="remarks"></a>Note  
 Gli elementi che corrispondono ai padri di `MeasureGroupID` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding> e <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
