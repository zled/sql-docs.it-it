---
title: Abilitato elemento (ASSL) | Microsoft Docs
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
- Enabled Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Enabled
helpviewer_keywords:
- Enabled element
ms.assetid: dbe57903-75c0-4060-a2b3-eab241d7469f
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dd8206bbf0dffe84a1012a0e47b4c261b15fb4ad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211661"
---
# <a name="enabled-element-assl"></a>Elemento Enabled (ASSL)
  Indica se l'elemento padre è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeHierarchy> <!-- or ProactiveCaching -->  
   ...  
   <Enabled>...</Enabled>  
   ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|True|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Oggetto CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi che corrispondono ai padri di `Enabled` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CubeHierarchy> e <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
