---
title: Elemento MeasureID (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MeasureID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureID
helpviewer_keywords:
- MeasureID element
ms.assetid: 8457aebc-8fdd-4683-8640-baaf9d89b2a2
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 70b7695644f2aa0da85050bb9db96ac277ede298
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063920"
---
# <a name="measureid-element-assl"></a>Elemento MeasureID (ASSL)
  Associa un [misure](../objects/measure-element-assl.md) elemento con l'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureBinding> <!-- or AggregationInstanceMeasure, PerspectiveMeasure -->  
   ...  
   <MeasureID>...</MeasureID>  
   ...  
</MeasureBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AggregationInstanceMeasure](../data-type/aggregationinstancemeasure-data-type-assl.md), [MeasureBinding](../data-type/binding-data-type-assl.md), [PerspectiveMeasure](../data-type/perspectivemeasure-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Gli elementi che corrispondono ai padri di `MeasureID` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AggregationInstanceMeasure>, <xref:Microsoft.AnalysisServices.MeasureBinding> e <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  