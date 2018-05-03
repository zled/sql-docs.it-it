---
title: SELECT FROM &lt;struttura&gt;. CASI | Documenti Microsoft
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
- SELECT FROM <structure> statements
ms.assetid: 36f50213-14dc-42da-b899-20240b781e1a
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 792f2d89dc1f0cecc7aba0b001266b2308a14c9f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="select-from-ltstructuregtcases"></a>SELECT FROM &lt;struttura&gt;. CASI
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce i case utilizzati per creare la struttura di data mining.  
  
 Se nella struttura non è attivato il drill-through, l'istruzione non riesce. Inoltre, l'istruzione non riuscirà se l'utente non dispone di autorizzazioni drill-through sulla struttura di data mining.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], drill-through su nuove strutture di data mining è abilitato per impostazione predefinita. Per verificare se il drill-through è abilitato per una determinata struttura, controllare se il valore di **CacheMode** è impostata su **KeepTrainingCases**.  
  
 Se il valore di **CacheMode** viene modificato in **ClearAfterProcessing**, case della struttura sono cancellati dalla cache e non è possibile utilizzare il drill-through.  
  
> [!NOTE]  
>  Non è possibile attivare o disabilitare il drill-through sulla struttura di data mining mediante DMX (Data Mining Extensions).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Facoltativa. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco di espressioni separate da virgola.  
  
 Un'espressione può includere identificatori di colonna, funzioni definite dall'utente e funzioni VBA.  
  
 *struttura*  
 Nome della struttura.  
  
 *Espressione della condizione*  
 Condizione per limitare i valori restituiti dall'elenco di colonne.  
  
 *espressione*  
 Facoltativa. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Se il drill-through è attivato sia nella struttura che nel modello, qualsiasi membro di un ruolo che dispone di autorizzazioni drill-through per il modello di data mining e per la struttura di data mining può restituire le colonne della struttura non incluse nel modello utilizzando la sintassi seguente:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Pertanto, per proteggere dati riservati o informazioni personali, è necessario costruire la vista origine dati per mascherare informazioni personali e concedere **AllowDrillthrough** l'autorizzazione per una struttura di data mining o un modello di data mining solo quando necessario.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti sono basati sulla struttura di data mining, Targeted Mailing, basata sul [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] database e i modelli di data mining associati. Per ulteriori informazioni, vedere [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drill-through-to-structure-cases"></a>Esempio 1: Esecuzione del drill-through nei case della struttura  
 Nell'esempio seguente viene restituito l'elenco dei 500 clienti meno recenti nella struttura di data mining, Targeted Mailing. La query restituisce tutte le colonne nel modello di data mining, ma limita le righe ai clienti che hanno acquistato una bicicletta e li ordina per età. È anche possibile modificare l'elenco di espressioni per specificare le colonne da restituire.  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>Esempio 2: Esecuzione del drill-through solo in case di test o training  
 Nell'esempio seguente viene restituito l'elenco dei case della struttura per Targeted Mailing riservato per l'esecuzione di test. Se la struttura di data mining non contiene un set di test di controllo, per impostazione predefinita tutti i case sono trattati come case di training e la query restituisce 0 case.  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 Per la restituzione dei case di training, sostituire la funzione `IsTrainingCase()`.  
  
## <a name="see-also"></a>Vedere anche  
 [SELEZIONARE &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
