---
title: Elemento KeyColumns (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumns
helpviewer_keywords:
- KeyColumns element
ms.assetid: 03f3ad21-25cb-4afd-9287-cbf942ac1ad9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5c699f95d91cdb48d780875d8f9190114d4b7a5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152637"
---
# <a name="keycolumns-element-assl"></a>Elemento KeyColumns (ASSL)
  Contiene la raccolta di [KeyColumn](../objects/column-element-assl.md) delle definizioni degli elementi per un oggetto padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or AggregationInstanceAttribute, AggregationInstanceCubeDimension, MeasureGroupAttribute, ScalarMiningStructureColumn -->  
   ...  
   <KeyColumns>  
      <KeyColumn xsi:type="DataItem"...</KeyColumn>  
   </KeyColumns>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento AggregationInstanceAttribute](../data-type/aggregationinstanceattribute-data-type-assl.md), [AggregationInstanceCubeDimension](../data-type/dimension-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md), [ ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|[KeyColumn](../objects/column-element-assl.md) di tipo [DataItem](../data-type/dataitem-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 La raccolta `KeyColumns` può contenere più elementi `KeyColumn` che rappresentano una chiave in più parti per un attributo o una colonna della struttura di data mining.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
