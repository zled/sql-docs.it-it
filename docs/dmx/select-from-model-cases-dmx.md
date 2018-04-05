---
title: SELECT FROM &lt;modello&gt;. CASE (DMX) | Documenti Microsoft
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
- SELECT
- CASES
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- SELECT FROM <model>.CASES statement
- drillthrough [DMX]
ms.assetid: d58acb47-aaa6-40b7-b8c4-6a6700fbc1dd
caps.latest.revision: 55
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b40b75f21b77e6dd17cf426be3ea70fe05ac0757
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="select-from-ltmodelgtcases-dmx"></a>SELECT FROM &lt;modello&gt;. CASE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Supporta il drill-through e restituisce i case utilizzati per il training del modello. Se il drill-through è attivato nella struttura di data mining e nel modello di data mining e si dispone di autorizzazioni appropriate, è possibile restituire le colonne della struttura che non sono incluse nel modello.  
  
 Se nel modello di data mining non è attivato il drill-through, l'istruzione non riesce.  
  
> [!NOTE]  
>  In DMX (Data Mining Extensions) è possibile attivare il drill-through solo al momento della creazione del modello. È possibile aggiungere il drill-through a un modello esistente utilizzando [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ma per poter visualizzare o eseguire una query sui case, è necessario rielaborare il modello.  
  
 Per ulteriori informazioni su come abilitare il drill-through, vedere [DMX CREATE MINING MODEL &#40; &#41;](../dmx/create-mining-model-dmx.md), [DMX SELECT INTO &#40; &#41;](../dmx/select-into-dmx.md), e [DMX ALTER MINING STRUCTURE &#40; &#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Facoltativo. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco di espressioni separate da virgola. Un'espressione può includere identificatori di colonna, funzioni definite dall'utente (UDF), funzioni VBA e altro.  
  
 Per includere una colonna della struttura che non è inclusa nel modello di data mining, utilizzare la funzione `StructureColumn('<structure column name>')`.  
  
 *model*  
 Identificatore del modello.  
  
 *espressione della condizione*  
 Condizione per limitare i valori restituiti dall'elenco di colonne.  
  
 *expression*  
 Facoltativo. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Se il drill-through è attivato sia nella struttura di data mining che nel modello di data mining, gli utenti membri di un ruolo con autorizzazioni drill-through sul modello e sulla struttura possono accedere alle colonne della struttura di data mining che non sono incluse nel modello di data mining. Pertanto, per proteggere dati riservati o informazioni personali, è necessario costruire la vista origine dati per mascherare informazioni personali e concedere **AllowDrillthrough** autorizzazioni su una struttura di data mining solo quando è necessario.  
  
 Il [DMX Lag &#40; &#41;](../dmx/lag-dmx.md) funzione può essere utilizzata con i modelli time series per restituire o filtrare l'intervallo di tempo tra ogni case e l'ora iniziale.  
  
 Utilizzando il [IsInNode &#40; DMX &#41;](../dmx/isinnode-dmx.md) funzionare nel **dove** clausola restituisce solo i case associati al nodo specificato dalla colonna NODE_UNIQUE_NAME del set di righe dello schema.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti sono basati sulla struttura di data mining Targeted Mailing, basata sul [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]database e i modelli di data mining associati. Per ulteriori informazioni, vedere [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drillthrough-to-model-cases-and-structure-columns"></a>Esempio 1: Drill-through in case del modello e colonne della struttura  
 Nell'esempio seguente vengono restituite le colonne per tutti i case utilizzati per il test del modello Targeted Mailing. Se la struttura di data mining in base alla quale è compilato il modello non dispone di set di dati di test di controllo, questa query restituisce 0 case. È possibile utilizzare l'elenco di espressioni per restituire solo le colonne necessarie.  
  
```  
SELECT * FROM [TM Decision Tree].Cases  
WHERE IsTestCase();  
```  
  
### <a name="example-2-drillthrough-to-training-cases-in-a-specific-node"></a>Esempio 2: Drill-through in case di training di uno specifico nodo  
 Nell'esempio seguente sono restituiti solo i case utilizzati per il training Cluster 2. Nel nodo relativo a Cluster 2 la colonna NODE_UNIQUE_NAME ha il valore '002'. Nell'esempio è restituita anche una colonna di struttura, [Customer Key], che non apparteneva al modello di data mining, e fornito l'alias `CustomerID` per la colonna. Si osservi che il nome della colonna della struttura viene passato come valore di stringa e pertanto deve essere racchiuso tra virgolette, non parentesi quadre.  
  
```  
SELECT StructureColumn('Customer Key') AS CustomerID, *   
FROM [TM_Clustering].Cases  
WHERE IsTrainingCase()  
AND IsInNode('002')  
```  
  
 Per restituire una colonna di struttura,è necessario che le autorizzazioni drill-through siano attive sia nel modello di data mining sia nella struttura di data mining.  
  
> [!NOTE]  
>  Il drill-through non è supportato da tutti i tipi di modello di data mining. Per informazioni sui modelli che supportano il drill-through, vedere [query drill-through &#40; Data Mining &#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [DMX SELECT &#40; &#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
