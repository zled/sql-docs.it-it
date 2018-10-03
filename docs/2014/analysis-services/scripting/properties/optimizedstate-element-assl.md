---
title: Elemento OptimizedState (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OptimizedState Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OptimizedState
helpviewer_keywords:
- OptimizedState element
ms.assetid: 120dcc4c-8fe8-4471-bbd6-99ad534364f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 484164e3c792a103dd7eabe9b860d539bc4b121e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160911"
---
# <a name="optimizedstate-element-assl"></a>Elemento OptimizedState (ASSL)
  Determina il livello di ottimizzazione applicato alla gerarchia.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeHierarchy>  
   ...  
   <OptimizedState>...</OptimizedState>  
   ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*FullyOptimized*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeHierarchy](../data-type/hierarchy-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*FullyOptimized*|L'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni di esecuzione delle query.|  
|*NotOptimized*|L'istanza non compila indici aggiuntivi.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `OptimizedState` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.OptimizationType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
