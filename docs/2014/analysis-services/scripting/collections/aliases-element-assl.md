---
title: Elemento alias (ASSL) | Documenti Microsoft
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
- Aliases Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aliases
helpviewer_keywords:
- Aliases element
ms.assetid: 9de9e683-d30d-4d61-b32d-c5a946825742
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 60673c26bf4a430c842da0fb61c98de7242ccd1c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156572"
---
# <a name="aliases-element-assl"></a>Elemento Alias (ASSL)
  Contiene la raccolta di [Alias](../properties/alias-element-assl.md) gli elementi associati a un [Account](../objects/account-element-assl.md) elemento  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Account>  
      ...  
   <Aliases>  
      <Alias>...</Alias>  
      </Aliases>  
      ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Account](../objects/account-element-assl.md)|  
|Elementi figlio|[Alias](../properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento corrispondente dell'elemento padre del `Aliases` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento account &#40;ASSL&#41;](accounts-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  