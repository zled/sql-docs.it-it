---
title: Elemento KeyColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumn
helpviewer_keywords:
- KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1cc42afde5212befbbd2a16a81340fb7e1f629bb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090319"
---
# <a name="keycolumn-element-assl"></a>Elemento KeyColumn (ASSL)
  Contiene la definizione di una colonna che corrisponde alla, o fa parte della, chiave per un attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<KeyColumns>  
   <KeyColumn xsi:type="DataItem">...</KeyColumn>  
<KeyColumns>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[KeyColumns](../collections/columns-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `DataItem` tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del `DataItem` del tipo, vedere [tipo di dati DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Gli elementi che corrispondono agli elementi padre della raccolta `KeyColumns` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati AggregationInstanceAttribute &#40;ASSL&#41;](../data-type/aggregationinstanceattribute-data-type-assl.md)   
 [Tipo di dati AggregationInstanceCubeDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Tipo di dati DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Tipo di dati MeasureGroupAttribute &#40;ASSL&#41;](../data-type/measuregroupattribute-data-type-assl.md)   
 [Tipo di dati ScalarMiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
