---
title: Elemento alias (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 677434b5ea6383e5905a703225edb5e56e3fb4e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267687"
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
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `Aliases` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Vedere anche  
 [Account di elemento &#40;ASSL&#41;](accounts-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
