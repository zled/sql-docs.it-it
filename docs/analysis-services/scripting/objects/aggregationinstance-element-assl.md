---
title: Elemento AggregationInstance (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AggregationInstance Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f9a3840c481d63b06357fa8c76b9f3fc7c2ae6bc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationInstances](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)|  
|Elementi figlio|[AggregationID](../../../analysis-services/scripting/properties/aggregationid-element-assl.md), [AggregationType](../../../analysis-services/scripting/properties/aggregationtype-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [misure](../../../analysis-services/scripting/collections/measures-element-assl.md), [ Origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Quando un [partizione](../../../analysis-services/scripting/objects/partition-element-assl.md) elemento utilizza un [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) per generare aggregazioni per la partizione, ogni [aggregazione](../../../analysis-services/scripting/objects/aggregation-element-assl.md) nel  **AggregationDesign** viene creata un'istanza per la partizione. Più partizioni possono utilizzare la stessa progettazione delle aggregazioni per generare più istanze di un'aggregazione definita. Il **AggregationInstance** elemento rappresenta un'istanza di un'aggregazione definita.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

