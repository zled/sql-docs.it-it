---
title: Elemento MemberUniqueNameStyle (ASSL) | Documenti Microsoft
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
- MemberUniqueNameStyle Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MemberUniqueNameStyle element
ms.assetid: f0771c81-0127-4203-9501-ae4f864730fa
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ca327bceaddce4c0f7ac1b7a726d321a02cdffc1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166931"
---
# <a name="memberuniquenamestyle-element-assl"></a>Elemento MemberUniqueNameStyle (ASSL)
  Determina i nomi univoci vengono generati per i membri delle gerarchie contenute all'interno di [CubeDimension](../data-type/dimension-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeDimension>  
   ...  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Native*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeDimension](../data-type/dimension-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Native*|L'istanza determina automaticamente i nomi univoci dei membri.|  
|*NamePath*|L'istanza genera un nome composto costituito dal nome di ogni livello e dalla didascalia del membro.|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `MemberUniqueNameStyle` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento del cubo &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Elemento della dimensione &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Tipo di dati CubeDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)  
  
  