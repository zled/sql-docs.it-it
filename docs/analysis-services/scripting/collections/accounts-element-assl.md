---
title: Account elemento (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bf3d3b56e9cc2b299ddcdec1c0a506e0168f8741
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030502"
---
# <a name="accounts-element-assl"></a>Elemento Accounts (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di tipi di conto definiti in un [Database](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Database](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|Elementi figlio|[Account](../../../analysis-services/scripting/objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Le dimensioni, il cui [tipo](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) è impostato su *account*possono avere un attributo che specifica il tipo di conto, ad esempio Income, Expense e così via, rappresentato dai membri della dimensione. Il tipo di conto viene quindi utilizzato da [misura](../../../analysis-services/scripting/objects/measure-element-assl.md) elementi, il cui [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) è impostato su *ByAccount*, per determinare la funzione di aggregazione da utilizzare quando l'aggregazione dei membri della dimensione. L'elemento **Accounts** contiene una raccolta di elementi **Account** che rappresentano i tipi di conto e la funzione di aggregazione da utilizzare per ciascun tipo di conto.  
  
 Un tipo di conto deve essere elencato se la funzione di aggregazione è diversa da quello predefinito utilizzato da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per ogni tipo di conto.  
  
 Il set di tipi di conto validi è fisso.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AccountType &#40;ASSL&#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)   
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
