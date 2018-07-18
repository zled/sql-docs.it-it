---
title: Elemento AggregationInstance (ASSL) | Microsoft Docs
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
- AggregationInstance Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 089fcff4b01b66f3b2bc1ac98de2f5cb4ba88319
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229771"
---
# <a name="aggregationinstance-element-assl"></a>Elemento AggregationInstance (ASSL)
  Definisce un'istanza di aggregazione per una partizione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationInstances>  
   <AggregationInstance>  
      <AggregationType>...</AggregationType>  
      <AggregationID>...</AggregationID>  
      <Source>...</Source>  
      <Dimensions>...</Dimensions>  
      <Measures>...</Measures>  
      <Annotations>...</Annotations>  
   </AggregationInstance>  
</AggregationInstances>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationInstances](../collections/aggregationinstances-element-assl.md)|  
|Elementi figlio|[AggregationID](../properties/id-element-assl.md), [AggregationType](../properties/aggregationtype-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [dimensioni](../collections/dimensions-element-assl.md), [misure](../collections/measures-element-assl.md), [origine](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Note  
 Quando un [Partition](partition-element-assl.md) elemento Usa un [AggregationDesign](aggregationdesign-element-assl.md) elemento per generare aggregazioni per la partizione, ogni [aggregazione](aggregation-element-assl.md) nel `AggregationDesign` è creare un'istanza per la partizione. Più partizioni possono utilizzare la stessa progettazione delle aggregazioni per generare più istanze di un'aggregazione definita. L'elemento `AggregationInstance` rappresenta un'istanza di un'aggregazione definita.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
