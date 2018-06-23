---
title: Elemento HideMemberIf (ASSL) | Documenti Microsoft
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
- HideMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2b1540a3b7f5d1e1a93ea3b4628bfbde186e5bb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068328"
---
# <a name="hidememberif-element-assl"></a>Elemento HideMemberIf (ASSL)
  Indica se e quando un membro di un livello deve essere nascosto per le applicazioni client.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Mai*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Level](../objects/level-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Mai*|I membri non vengono mai nascosti.|  
|*OnlyChildWithNoName*|Un membro viene nascosto quando è l'unico figlio del relativo padre e il suo nome è vuoto.|  
|*OnlyChildWithParentName*|Un membro viene nascosto quando è l'unico elemento figlio del relativo padre e il nome corrisponde a quello del padre.|  
|*NoName*|Un membro viene nascosto quando il suo nome è vuoto.|  
|*ParentName*|Un membro viene nascosto quando il suo nome è identico a quello del padre.|  
  
## <a name="remarks"></a>Remarks  
 L'enumerazione che corrisponde ai valori consentiti di `HideMemberIf` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  