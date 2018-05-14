---
title: Elemento AggregationInstance (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c8f24bbaf0660c690697dad015fa28c412a633a3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationinstance-element-assl"></a>Elemento AggregationInstance (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Elementi figlio|[AggregationID](../../../analysis-services/scripting/properties/aggregationid-element-assl.md), [AggregationType](../../../analysis-services/scripting/properties/aggregationtype-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [misure](../../../analysis-services/scripting/collections/measures-element-assl.md), [origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Quando un [partizione](../../../analysis-services/scripting/objects/partition-element-assl.md) elemento utilizza un [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) per generare aggregazioni per la partizione, ogni [aggregazione](../../../analysis-services/scripting/objects/aggregation-element-assl.md) nel  **AggregationDesign** viene creata un'istanza per la partizione. Più partizioni possono utilizzare la stessa progettazione delle aggregazioni per generare più istanze di un'aggregazione definita. Il **AggregationInstance** elemento rappresenta un'istanza di un'aggregazione definita.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
