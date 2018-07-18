---
title: Elemento ProactiveCaching (ASSL) | Microsoft Docs
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
- ProactiveCaching Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProactiveCaching
helpviewer_keywords:
- ProactiveCaching element
ms.assetid: 85f9ed44-2ede-406f-b0ca-237ab2f49722
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e66238759e38f9f8b42ebf0604b739d74f851832
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211721"
---
# <a name="proactivecaching-element-assl"></a>Elemento ProactiveCaching (ASSL)
  Definisce impostazioni di memorizzazione attiva nella cache per l'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProactiveCaching>  
      <OnlineMode>...</OnlineMode>  
      <AggregationStorage>...</AggregationStorage>  
      <Source>...</Source>  
      <SilenceInterval>...</SilenceInterval>  
      <Latency>...</Latency>  
      <SilenceOverrideInterval>...</SilenceOverrideInterval>  
      <ForceRebuildInterval>...</ForceRebuildInterval>  
      <Enabled >...</Enabled>  
   </ProactiveCaching>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](cube-element-assl.md), [dimensione](dimension-element-assl.md), [MeasureGroup](group-element-assl.md), [partizione](partition-element-assl.md)|  
|Elementi figlio|[AggregationStorage](../properties/aggregationstorage-element-assl.md), [abilitati](../properties/enabled-element-assl.md), [ForceRebuildInterval](../properties/forcerebuildinterval-element-assl.md), [latenza](../properties/latency-element-assl.md), [OnlineMode](../properties/onlinemode-element-assl.md), [ SilenceInterval](../properties/silenceinterval-element-assl.md), [SilenceOverrideInterval](../properties/silenceoverrideinterval-element-assl.md), [origine](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
