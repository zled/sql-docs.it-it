---
title: Modificare le proprietà di un modello di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2533de57dd2baee8297cd0f277c4538d16fbc16a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172771"
---
# <a name="change-the-properties-of-a-mining-model"></a>Modificare le proprietà di un modello di data mining
  Alcune proprietà dei modelli di data mining si applicano all'intero modello, altre solo a singole colonne. Esempi di proprietà che si applicano all'intero modello sono le `Drillthrough` proprietà, che specifica se i dati del case devono essere disponibili per l'esecuzione di query, e il `Description` proprietà. Le proprietà che si applicano alle singole colonne sono `Usage` e `ModelingFlags`, che controllano il modo in cui i dati della colonna vengono utilizzati all'interno del modello.  
  
 Le proprietà del modello seguenti sono associate a editor avanzati che è possibile utilizzare per creare espressioni o configurare proprietà più complesse. Di seguito sono elencate queste proprietà.  
  
-   `Filter` proprietà: apre la [filtro dei Set di dati o finestra di dialogo Filtro modello](../data-set-filter-or-model-filter-dialog-box.md).  
  
-   `AlgorithmParameters` proprietà: apre la [finestra di dialogo parametri algoritmo &#40;visualizzazione di modelli di Data Mining&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).  
  
 Per informazioni su come impostare le proprietà in un modello di data mining, vedere [Colonne del modello di data mining](mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>Per modificare le proprietà di un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sull'intestazione di colonna che contiene il nome del modello di data mining o sulla riga della griglia che contiene il nome dell'algoritmo di data mining e quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** a destra dello schermo evidenziare il valore corrispondente alla proprietà da modificare e quindi immettere il nuovo valore.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>Per modificare le proprietà di un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla cella della griglia in corrispondenza dell'intersezione tra la colonna della struttura di data mining e il modello di data mining e quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** a destra dello schermo evidenziare il valore corrispondente alla proprietà da modificare e quindi immettere il nuovo valore.  
  
    > [!NOTE]  
    >  Se l'utilizzo della colonna è impostata su `Ignore`, il **proprietà** finestra per la colonna è vuota.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](mining-model-tasks-and-how-tos.md)  
  
  
