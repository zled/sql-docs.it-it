---
title: Elemento calculation (ASSL) | Microsoft Docs
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
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7900d511cb847a98d9b4f037a39864b0b89c93a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261337"
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
  
  
