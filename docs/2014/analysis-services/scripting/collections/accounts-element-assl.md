---
title: Account di elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Accounts Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d0dd0fabf7ebfc6ee020a533149b73e72f7a8a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126141"
---
# <a name="accounts-element-assl"></a>Elemento Accounts (ASSL)
  Contiene la raccolta di tipi di conto definiti in un [Database](../objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database>  
   ...  
   <Accounts>  
      <Account>...</Account>  
   </Accounts>  
   ...  
</Database>  
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
|Elementi padre|[Database](../objects/database-element-assl.md)|  
|Elementi figlio|[account](../objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Le dimensioni, il cui [tipo](../properties/type-element-dimension-assl.md) elemento è impostato su *account*possono avere un attributo che specifica il tipo di account, ad esempio Income, Expense e così via, rappresentato dai membri nella dimensione. Il tipo di conto viene quindi utilizzato dal [Measure](../objects/measure-element-assl.md) gli elementi, il cui [AggregationFunction](../properties/aggregatefunction-element-assl.md) elemento è impostato su *ByAccount*, per determinare la funzione di aggregazione da utilizzare quando l'aggregazione dei membri di tale dimensione. L'elemento `Accounts` contiene una raccolta di elementi `Account` che rappresentano i tipi di conto e la funzione di aggregazione da utilizzare per ciascun tipo di conto.  
  
 Un tipo di conto deve essere elencato se la funzione di aggregazione è diversa da quello predefinito utilizzato da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per ogni tipo di account.  
  
 Il set di tipi di conto validi è fisso.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AccountType &#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
