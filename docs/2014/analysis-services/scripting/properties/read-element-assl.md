---
title: Leggere l'elemento (ASSL) | Documenti Microsoft
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
- Read Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1e7f26c9064f754633420cd58a0f15197189d1ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077865"
---
# <a name="read-element-assl"></a>Elemento Read (ASSL)
  Determina se è possono leggere i dati o metadati per un determinato [CubeDimensionPermission](../data-type/permission-data-type-assl.md) oppure [autorizzazione](../data-type/permission-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubeDimensionPermission](../objects/cubepermission-element-assl.md), [autorizzazione](../data-type/permission-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Non è permesso alcun accesso a dati o metadati dall'oggetto padre.|  
|*È consentito*|È consentito l'accesso in scrittura a dati e metadati dall'oggetto padre.|  
  
## <a name="remarks"></a>Remarks  
 Gli elementi che corrispondono ai padri di `Read` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CubeDimensionPermission> e <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento del cubo &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Elemento della dimensione &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Elemento CubePermission &#40;ASSL&#41;](../objects/cubepermission-element-assl.md)   
 [Tipo di dati di autorizzazione &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  