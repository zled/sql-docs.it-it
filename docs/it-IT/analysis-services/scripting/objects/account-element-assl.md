---
title: Account elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- Account Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 54da4e03516002762f0312e50bcf1256279be58f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="account-element-assl"></a>Elemento Account (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene informazioni dettagliate su un tipo di account all'interno di un [Database](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Accounts](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|Elementi figlio|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md), [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md), [alias](../../../analysis-services/scripting/collections/aliases-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Le dimensioni, il cui [tipo](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) è impostato su *account* possono avere un attributo che specifica il tipo di conto, ad esempio Income, Expense e così via, rappresentato dai membri nella dimensione. Il tipo di conto viene quindi utilizzato da [misura](../../../analysis-services/scripting/objects/measure-element-assl.md) elementi, il cui [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) è impostato su *ByAccount*, per determinare la funzione di aggregazione da utilizzare quando l'aggregazione dei membri della dimensione. Il **Account** elemento rappresenta un singolo tipo di conto e la funzione di aggregazione che deve essere utilizzata da tali misure.  
  
 Un tipo di conto deve essere elencato se la funzione di aggregazione è diversa da quello predefinito utilizzato da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per ogni tipo di conto.  
  
 Il set di tipi di conto validi è fisso.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
