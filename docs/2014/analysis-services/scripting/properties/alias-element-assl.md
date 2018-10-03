---
title: Elemento alias (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Alias Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Alias
helpviewer_keywords:
- Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b894b9883fc2146ba234bccf543a0d08d436bf86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104261"
---
# <a name="alias-element-assl"></a>Elemento Alias (ASSL)
  Definisce un alias per un [Account](../objects/account-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Alias](../collections/aliases-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore dell'elemento `Alias` viene utilizzato come nome alternativo per il conto definito dall'elemento padre `Account` e consente di identificare la combinazione di tipo di conto e funzione di aggregazione in un'interfaccia utente.  
  
 L’elemento che corrisponde al padre della raccolta `Aliases` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
