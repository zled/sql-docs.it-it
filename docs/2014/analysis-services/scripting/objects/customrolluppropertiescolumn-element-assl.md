---
title: Elemento CustomRollupPropertiesColumn (ASSL) | Documenti Microsoft
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
- CustomRollupPropertiesColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CustomRollupPropertiesColumn
helpviewer_keywords:
- CustomRollupPropertiesColumn element
ms.assetid: 7f4a9825-c768-4523-acb3-511a5160fd44
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c9452dbc1d6c3104fe76760ad4460e636fdd45fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068335"
---
# <a name="customrolluppropertiescolumn-element-assl"></a>Elemento CustomRollupPropertiesColumn (ASSL)
  Definisce i dettagli di una colonna che forniscono le proprietà di una formula personalizzata di rollup.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <CustomRollupPropertiesColumn xsi:type="DataItem">...</CustomRollupPropertiesColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sul `DataItem` tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del `DataItem` del tipo, vedere [tipo di dati DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L'elemento che corrisponde al padre di `CustomRollupPropertiesColumn` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CustomRollupColumn &#40;ASSL&#41;](column-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  