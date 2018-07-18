---
title: Elemento RefreshInterval (ASSL) | Microsoft Docs
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
- RefreshInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshInterval
helpviewer_keywords:
- RefreshInterval element
ms.assetid: 2761d26a-5fb0-452c-9a89-12f8dc658c33
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f3fecbe3eef6eb68af256dfcc0a94ddef1ba3aee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315051"
---
# <a name="refreshinterval-element-assl"></a>Elemento RefreshInterval (ASSL)
  Specifica che l'intervallo durante il quale i dati del limite sono associati all'elemento padre è aggiornato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding, ProactiveCachingIncrementalProcessingBinding, ProactiveCachingQueryBinding -->  
   ...  
   <RefreshInterval>...</RefreshInterval>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Durata XML|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
|Valore predefinito|[ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md) oppure [ProactiveCachingQueryBinding](../data-type/querybinding-data-type-assl.md) = PT 1s|  
|Valore predefinito|Tutti gli altri = PT1m|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionBinding](../data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md), [ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md), [ProactiveCachingQueryBinding](../data-type/querybinding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi che corrispondono agli elementi padre di `RefreshInterval` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.DimensionBinding>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding>, <xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding> e <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
