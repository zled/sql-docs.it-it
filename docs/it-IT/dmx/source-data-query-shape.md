---
title: FORMA (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
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
- SHAPE
dev_langs:
- DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8b79237879b2e23682bfdd89dcf1d2ba59824aa1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ltsource-data-querygt---shape"></a>&lt;query di dati di origine&gt; -forma
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di combinare query da più origini dei dati in una singola tabella gerarchica, ovvero una tabella con tabelle nidificate, che diventa la tabella dei case per il modello di data mining.  
  
 La sintassi completa del **forma** comando è documentato nel [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argomenti  
 *query master*  
 Query che restituisce la tabella padre.  
  
 *query di tabella figlio*  
 Query che restituisce la tabella nidificata.  
  
 *colonna master*  
 Colonna della tabella padre utilizzata per identificare le righe figlio tra i risultati di una query che restituisce una tabella figlio.  
  
 *colonna figlio*  
 Colonna della tabella figlio utilizzata per identificare le righe padre tra i risultati di una query che restituisce la tabella padre.  
  
 *nome della colonna tabella*  
 Nome della colonna appena aggiunta nella tabella padre per creare la tabella figlio.  
  
## <a name="remarks"></a>Osservazioni  
 Le query devono essere ordinate in base alla colonna che definisce la correlazione tra la tabella padre e la tabella figlio.  
  
## <a name="examples"></a>Esempi  
 È possibile utilizzare l'esempio seguente all'interno di un' [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) istruzione per il training di un modello contenente una tabella nidificata. Le due tabelle all'interno di **forma** istruzione sono correlate tramite il **OrderNumber** colonna.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#60;query di origine dati&#62;](../dmx/source-data-query.md)   
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
