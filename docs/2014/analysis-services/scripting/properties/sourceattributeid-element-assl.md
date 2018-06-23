---
title: Elemento SourceAttributeID (ASSL) | Documenti Microsoft
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
- SourceAttributeID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SourceAttributeID
helpviewer_keywords:
- SourceAttributeID element
ms.assetid: 8973eb62-6142-4ce2-ad42-c8be2b43c04f
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 06da8df2a164ee903b59dc2a154bca926c1b82f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067676"
---
# <a name="sourceattributeid-element-assl"></a>Elemento SourceAttributeID (ASSL)
  Contiene l'identificatore (ID) dell'attributo di origine in cui il [livello](../objects/level-element-assl.md) si basa l'elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Level>  
   ...  
   <SourceAttributeID>...</SourceAttributeID>  
   ...  
</Level>  
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
|Elemento padre|[Level](../objects/level-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento corrispondente dell'elemento padre del `SourceAttributeID` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Level>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  