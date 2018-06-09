---
title: SELECT FROM &lt;modello&gt;. SAMPLE_CASES (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4443f05fbee790f5f1d266f451e1105b9c00197
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841524"
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
 Facoltativo. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente identificatori di colonna correlati.  
  
 *model*  
 Identificatore del modello.  
  
 *elenco delle condizioni*  
 Facoltativo. Condizioni per limitare i valori restituiti dall'elenco di colonne.  
  
 *expression*  
 Facoltativo. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Remarks  
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
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
