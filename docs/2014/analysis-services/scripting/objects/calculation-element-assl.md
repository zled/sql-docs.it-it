---
title: Elemento calculation (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Calculation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Calculation
helpviewer_keywords:
- Calculation element
ms.assetid: c96e37cf-b7ff-4296-a043-f9a5a5c444ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c33adc47ad29224753109d1666f0f579d146409
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049881"
---
# <a name="calculation-element-assl"></a>Elemento Calculation (ASSL)
  Associa un calcolo con a una [prospettiva](perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Calculations>  
   <Calculation xsi:type="PerspectiveCalculation">  
      </Calculation>  
</Calculations>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Calcoli](../collections/calculations-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CalculationType> e <xref:Microsoft.AnalysisServices.PerspectiveCalculationType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
