---
title: Elemento AggregationDesigns (ASSL) | Documenti Microsoft
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
- AggregationDesigns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesigns
helpviewer_keywords:
- AggregationDesigns element
ms.assetid: 7291956a-9c53-41fe-af2e-2418e26956c5
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6dfddae8284e32f08edc4cf1e0868c7c71c97db2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171101"
---
# <a name="aggregationdesigns-element-assl"></a>Elemento AggregationDesigns (ASSL)
  Contiene la raccolta di progettazioni di aggregazioni che possono essere condivise tra più partizioni in un database.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroup>  
   ...  
   <AggregationDesigns>  
      <AggregationDesign>...</AggregationDesign>  
   </AggregationDesigns>  
   ...  
</MeasureGroup>  
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
|Elementi padre|[Gruppo di misure](../objects/group-element-assl.md)|  
|Elementi figlio|[AggregationDesign](../objects/aggregationdesign-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationDesignCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di partizione &#40;ASSL&#41;](../objects/partition-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  