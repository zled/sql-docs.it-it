---
title: Elemento AccountType (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AccountType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8755c1d99da654a89b6d4f636ad4a816f10577f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="accounttype-element-assl"></a>Elemento AccountType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il nome del tipo di conto definito in un [Database](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Account](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Income*|Il conto è di tipo reddito.|  
|*Expense*|Il conto è di tipo spesa.|  
|*Flow*|Il conto è di tipo flusso di cassa.|  
|*Balance*|Il conto è di tipo collettivo.|  
|*Asset*|Il conto è di tipo cespite.|  
|*Liability*|Il conto è di tipo passività.|  
|*Statistiche*|Il conto è di tipo statistico.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **AccountType** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento account &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
