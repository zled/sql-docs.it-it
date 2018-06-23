---
title: Elemento AccountType (ASSL) | Documenti Microsoft
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
- AccountType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff7203d2882689b21a6ab3171880c26a8d385f7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158540"
---
# <a name="accounttype-element-assl"></a>Elemento AccountType (ASSL)
  Contiene il nome di un tipo di conto definito in un [Database](../objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Account](../objects/account-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Reddito*|Il conto è di tipo reddito.|  
|*Nota spese*|Il conto è di tipo spesa.|  
|*Flusso*|Il conto è di tipo flusso di cassa.|  
|*Saldo*|Il conto è di tipo collettivo.|  
|*Asset*|Il conto è di tipo cespite.|  
|*Responsabilità*|Il conto è di tipo passività.|  
|*Statistica*|Il conto è di tipo statistico.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `AccountType` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento account &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  