---
title: Elemento Goal (ASSL) | Documenti Microsoft
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
- Goal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Goal
helpviewer_keywords:
- Goal element
ms.assetid: 75fa5b57-418e-43ad-8704-764e4f0a40cf
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8b408e73bd8cb376afe0b8cf36157628be908780
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055372"
---
# <a name="goal-element-assl"></a>Elemento Goal (ASSL)
  Identifica l'obiettivo desiderato in un [Kpi](../objects/kpi-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Kpi>  
   ...  
   <Goal>...</Goal>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Indicatore KPI](../objects/kpi-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento `Goal` contiene un'espressione MDX (Multidimensional Expressions).  
  
 L'elemento che corrisponde al padre di `Goal` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Status &#40;ASSL&#41;](status-element-assl.md)   
 [Elemento di tendenza &#40;ASSL&#41;](trend-element-assl.md)   
 [Valore elemento &#40;ASSL&#41;](value-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  