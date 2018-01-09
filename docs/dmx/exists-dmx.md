---
title: Esiste (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Exists
dev_langs: DMX
helpviewer_keywords: Exists function
ms.assetid: 3b54dd93-f0a8-4f9a-96ae-a38bf977dda1
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6f5fb5dccb91af6409c0ed91796ba5119475ccaf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="exists-dmx"></a>Exists (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce **true** se la sottoquery specificata restituisce almeno una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Argomenti  
 *sottoquery*  
 Un'istruzione SELECT del form SELECT * FROM \<nome colonna > [dove \<elenco predicato >].  
  
## <a name="result-type"></a>Tipo di risultato  
 Restituisce **true** se il set di risultati restituito dalla sottoquery contiene almeno una riga; in caso contrario, restituisce **false**.  
  
## <a name="remarks"></a>Remarks  
 È possibile utilizzare la parola chiave NOT prima di EXISTS: ad esempio, `WHERE NOT EXISTS (<subquery>)`.  
  
 L'elenco di colonne aggiunte all'argomento della sottoquery di EXISTS è irrilevante. Viene solo verificata l'esistenza di una riga che soddisfa la condizione.  
  
## <a name="examples"></a>Esempi  
 È possibile utilizzare EXISTS e NOT EXISTS per verificare le condizioni in una tabella nidificata. Ciò è utile durante la creazione di un filtro che controlla i dati utilizzati per eseguire il training o il testing di un modello di data mining. Per altre informazioni, vedere [Filtri per i modelli di data mining &#40;Analysis Services - Data mining&#41;](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Nell'esempio seguente si basa sul `[Association]` struttura di data mining e il modello di data mining creati nel [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La query restituisce solo i casi in cui il cliente ha acquistato almeno un Patch kit.  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 Per visualizzare gli stessi dati restituiti da questa query è inoltre possibile aprire il modello nel Visualizzatore Association destro del mouse su set di elementi **Patch kit = Existing**, selezionare il **drill-Through** opzione e quindi selezionare **solo case del modello**.  
  
## <a name="see-also"></a>Vedere anche  
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Sintassi del filtro del modello ed esempi &#40; Analysis Services - Data Mining &#41;](../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)  
  
  
