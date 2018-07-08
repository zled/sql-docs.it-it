---
title: Elemento RefreshPolicy (ASSL) | Microsoft Docs
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
- RefreshPolicy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshPolicy
helpviewer_keywords:
- RefreshPolicy element
ms.assetid: f4c36280-1a39-4f1c-a3ab-fbeb81742d6d
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf0aa9478a44e7479b20357ae56317b90801f77f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277617"
---
# <a name="refreshpolicy-element-assl"></a>Elemento RefreshPolicy (ASSL)
  Determina la frequenza la parte dinamica del gruppo di misure o dimensioni (come specificato dal [persistenza](persistence-element-assl.md) elemento) viene verificata la modifica.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
|Predecessore o padre|Valore predefinito|  
|------------------------|-------------------|  
|[DimensionBinding](../data-type/binding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|None|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*ByQuery*|Ogni query controlla se i dati di origine sono modificati.|  
|*ByInterval*|I dati di origine viene verificati solo per le modifiche nell'intervallo specificato da [RefreshInterval](refreshinterval-element-assl.md).|  
  
 L'enumerazione che corrisponde ai valori consentiti di `RefreshPolicy` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.RefreshPolicy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Persistence &#40;ASSL&#41;](persistence-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
