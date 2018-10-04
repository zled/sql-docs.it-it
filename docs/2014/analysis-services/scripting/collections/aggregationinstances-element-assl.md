---
title: Elemento AggregationInstances (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationInstances Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstances element
ms.assetid: e8321aa8-361b-4d8a-bd89-a596eeb814b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e0ed44484d1c8a27eae1495a188843040e28ba4b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050701"
---
# <a name="aggregationinstances-element-assl"></a>Elemento AggregationInstances (ASSL)
  Contiene la raccolta di istanze di aggregazione definite in un [partizione](../objects/partition-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Partition>  
   ...  
   <AggregationInstances>  
      <AggregationInstance>...</AggregationInstance>  
   </AggregationInstances>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|[Elemento AggregationInstance](../objects/aggregationinstance-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationInstanceCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
