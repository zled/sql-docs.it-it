---
title: 'Lezione 4: Compilazione di un Sequence Clustering (esercitazione intermedia di Data Mining) Scenario | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e594e44dd3c8af8ade94c549d8b489f31623553
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251203"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Lezione 4: Compilazione di uno scenario di clustering delle sequenze (Esercitazione intermedia sul data mining)
  Il reparto marketing del [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] intende comprendere in modo i clienti visitano il [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sito Web. L'azienda ritiene che esista un modello in base al quale i clienti inseriscono i prodotti nei rispettivi carrelli della spesa. Desidera quindi analizzare l'ordine delle sequenze di acquisto per sapere in che modo i clienti includono i prodotti tra gli acquisti. L'azienda può quindi utilizzare queste informazioni per rendere il sito Web più efficiente in modo da indurre i clienti ad acquistare altri prodotti.  
  
 Dopo aver completato le attività incluse in questa lezione, si avrà creato un modello di data mining che utilizza l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering per prevedere quale sarà il prodotto successivo che il cliente inserirà tra gli acquisti. Verranno utilizzate due versioni del modello: una analizza solo l'ordine dei prodotti inclusi tra gli acquisti e l'altra contiene dati demografici aggiuntivi del cliente per il clustering. Infine, si utilizzeranno i modelli per creare stime da utilizzare per consigliare prodotti ai clienti.  
  
 Per completare le attività nella lezione, si userà la struttura di data mining market basket creata nella [lezione 3: compilazione di uno Scenario Market Basket &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). In questa lezione sono incluse le attività seguenti:  
  
-   [Creazione di una struttura modello di Data Mining Sequence Clustering &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Elaborazione del modello Sequence Clustering](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Esplorazione del modello Sequence Clustering &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Creazione di un modello Sequence Clustering correlato &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Creazione di stime su un modello Sequence Clustering &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Creazione di una struttura modello di Data Mining Sequence Clustering &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Tutte le lezioni  
 [Lezione 1: Creazione della soluzione intermedia di Data Mining &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lezione 2: Compilazione di uno Scenario di previsione &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lezione 3: Compilazione di uno Scenario Market Basket &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Lezione 4: Scenario di clustering delle sequenze (Esercitazione intermedia sul data mining)  
  
 [Lezione 5: Creazione di reti neurali e modelli di regressione logistica &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazione di base di Data Mining](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Esercitazione intermedia sul Data Mining &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
