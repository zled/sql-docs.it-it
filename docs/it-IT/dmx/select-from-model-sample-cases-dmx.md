---
title: SELECT FROM &lt;modello&gt;. SAMPLE_CASES (DMX) | Documenti Microsoft
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
- SAMPLE_CASES
- SELECT
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- SELECT FROM <model>.SAMPLE_CASES statement
- mining models [Analysis Services], sample cases
- sample cases [DMX]
- training mining models
ms.assetid: e7a34b9b-3562-4503-bfa7-dd9b12db480a
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 61057143a92c54dbe89342f5d9c666f38e194546
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM &lt;modello&gt;. SAMPLE_CASES (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce case di esempio rappresentativi dei case utilizzati per il training del modello di data mining.  
  
 Per utilizzare questa istruzione, è necessario attivare il drill-through alla creazione del modello di data mining. Per ulteriori informazioni su come abilitare il drill-through, vedere [CREATE MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md), e [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Facoltativa. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente identificatori di colonna correlati.  
  
 *model*  
 Identificatore del modello.  
  
 *elenco delle condizioni*  
 Facoltativa. Condizioni per limitare i valori restituiti dall'elenco di colonne.  
  
 *espressione*  
 Facoltativa. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 I case di esempio potrebbero essere generati e potrebbero non esistere effettivamente nei dati utilizzati per il training. Il case restituito è rappresentativo del nodo di contenuto specificato.  
  
 Sebbene il [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo Sequence Clustering è l'unico [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo che supporta l'utilizzo di SELECT FROM \<modello >. SAMPLE_CASES, algoritmi di terze parti possono anche supportarla.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti i case di esempio utilizzati per il training del modello di data mining Target Mail. Utilizzando il [IsInNode &#40;DMX&#41; ](../dmx/isinnode-dmx.md) funzionare nel **in cui** clausola restituisce solo i case associati con il nodo '000000003'. La stringa del nodo si trova nella colonna NODE_UNIQUE_NAME del set di righe dello schema.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELEZIONARE &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
