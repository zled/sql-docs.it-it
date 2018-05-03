---
title: PredictAssociation (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 09/14/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PredictAssociation
dev_langs:
- DMX
helpviewer_keywords:
- PredictAssociation function
ms.assetid: 33eb66b5-84c6-449f-aaae-316345bc4ad5
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 3a3fd8d22cd601fc26b53af35a4d101ffcaea3e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="predictassociation-dmx"></a>PredictAssociation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di stimare l'appartenenza associativa.  
  
Ad esempio, è possibile utilizzare la funzione PredictAssociation per ottenere il set dei consigli forniti lo stato corrente del carrello per un cliente. 
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>Si applica a  
 Algoritmi che contengono tabelle nidificate stimabili, tra cui l'associazione e alcuni algoritmi di classificazione. Gli algoritmi di classificazione che supportano le tabelle nidificate includono il [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees, [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, e [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmi Neural Network.  
  
## <a name="return-type"></a>Tipo restituito  
 \<espressione di tabella >  
  
## <a name="remarks"></a>Osservazioni  
 Le opzioni per il **PredictAssociation** funzione includono EXCLUDE_NULL, INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (predefinita), INPUT_ONLY, INCLUDE_STATISTICS e INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY e INCLUDE_STATISTICS sono applicabili solo a riferimenti a colonne di tabella, mentre EXCLUDE_NULL e INCLUDE_NULL sono applicabili solo a riferimenti a colonne scalari.  
  
 INCLUDE_STATISTICS restituisce solo **$Probability** e **$AdjustedProbability**.  
  
 Se il parametro numerico *n* è specificato, il **PredictAssociation** funzione restituisce i primi n valori più probabili in base alla probabilità:  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 Se si includono **$AdjustedProbability**, l'istruzione restituisce le prime *n* valori basati sul **$AdjustedProbability**.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa il **PredictAssociation** funzione per restituire i quattro prodotti Adventure Works di database che sono più probabilmente verranno venduti insieme.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
Nell'esempio seguente viene illustrato come è possibile utilizzare una tabella nidificata come input per la funzione di stima utilizzando la clausola SHAPE. Query SHAPE crea un set di righe con customerId come una colonna e una tabella nidificata come una seconda colonna che contiene l'elenco dei prodotti che un cliente ha già evidenziato. 

~~~~
SELECT T.[CustomerId], PredictAssociation(MyNestedTable, 5) // returns top 5 associated items
FROM My Model
PREDICTION JOIN
SHAPE {
    OPENQUERY([Adventure Works DW],'SELECT CustomerID, OrderNumber
    FROM vAssocSeqOrders ORDER BY OrderNumber')
} APPEND (
    {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, model FROM 
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}
  RELATE OrderNumber to OrderNumber) AS T
~~~~  

  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
