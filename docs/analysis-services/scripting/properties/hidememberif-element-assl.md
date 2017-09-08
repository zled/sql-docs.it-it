---
title: Elemento HideMemberIf (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- HideMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 63e9386cbeb679bef13c87857df9b95a10863099
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Mai*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Mai*|I membri non vengono mai nascosti.|  
|*OnlyChildWithNoName*|Un membro viene nascosto quando è l'unico figlio del relativo padre e il suo nome è vuoto.|  
|*OnlyChildWithParentName*|Un membro viene nascosto quando è l'unico elemento figlio del relativo padre e il nome corrisponde a quello del padre.|  
|*NoName*|Un membro viene nascosto quando il suo nome è vuoto.|  
|*ParentName*|Un membro viene nascosto quando il suo nome è identico a quello del padre.|  
  
## <a name="remarks"></a>Osservazioni  
 L'enumerazione che corrisponde ai valori consentiti per **HideMemberIf** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
