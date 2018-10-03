---
title: Elemento Persistence (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Persistence Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Persistence
helpviewer_keywords:
- Persistence element
ms.assetid: dafe3df2-4795-48ea-bebe-33c1a3bf18b6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c5e5ce2407b13d343d0490807dac5bdec0aede15
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186421"
---
# <a name="persistence-element-assl"></a>Elemento Persistence (ASSL)
  Determina quali parti dei dati di origine associato sono dinamici e vengono verificate per gli aggiornamenti usando la frequenza specificata per il [RefreshPolicy](refreshpolicy-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Persistence>...</Persistence>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*NotPersisted*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*NotPersisted*|Metadati di origine, membri e dati sono tutti dinamici.|  
|*Metadati*|I metadati di origine sono statici, ma membri e dati sono dinamici.|  
|*Tutto*|Metadati di origine, membri e dati sono tutti statici.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Persistence` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.PersistenceType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
