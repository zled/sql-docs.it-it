---
title: Elemento (ASSL) dell'account | Documenti Microsoft
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
- Account Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0a99dbaee6e1eaec95385295cf1842ffcc336adf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169761"
---
# <a name="account-element-assl"></a>Elemento Account (ASSL)
  Contiene informazioni dettagliate su un tipo di conto all'interno di un [Database](database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Accounts>  
   <Account>  
      <AccountType>...</AccountType>  
      <AggregationFunction>...</AggregationFunction>  
            <Aliases>...</Aliases>  
            <Annotations>...</Annotations>  
   </Account>  
</Accounts>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Accounts](../collections/accounts-element-assl.md)|  
|Elementi figlio|[AccountType](../properties/accounttype-element-assl.md), [AggregationFunction](../properties/aggregationfunction-element-assl.md), [alias](../collections/aliases-element-assl.md), [annotazioni](../collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Le dimensioni, il cui [tipo](../properties/type-element-dimension-assl.md) è impostato su *conti,* possono avere un attributo che specifica il tipo di conto, ad esempio Income, Expense e così via, rappresentato dai membri nella dimensione. Il tipo di conto viene quindi utilizzato da [misura](measure-element-assl.md) elementi, il cui [AggregationFunction](../properties/aggregatefunction-element-assl.md) è impostato su *ByAccount*, per determinare la funzione di aggregazione da utilizzare quando l'aggregazione dei membri di tale dimensione. L'elemento `Account` rappresenta un singolo tipo di conto e la funzione di aggregazione che deve essere utilizzata da tali misure.  
  
 Un tipo di conto deve essere elencato se la funzione di aggregazione è diversa da quello predefinito utilizzato da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per ogni tipo di conto.  
  
 Il set di tipi di conto validi è fisso.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40;ASSL&#41;](database-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  