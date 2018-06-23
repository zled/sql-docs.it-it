---
title: 'Lezione 2: Compilazione di uno Scenario di previsione (esercitazione intermedia di Data Mining) | Documenti Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 94f73737c1d67a69c4b740371c578b2f41d97a13
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312349"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Lezione 2: Compilazione di uno scenario di previsione (Esercitazione intermedia sul data mining)
  In qualità di analista delle vendite di [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], si supponga di aver ricevuto la richiesta di stimare le vendite dei prodotti del prossimo anno. In particolare, viene richiesto di confrontare le previsioni per le diverse regioni e linee di prodotti. È stato inoltre richiesto di determinare se le vendite dei singoli prodotti sono da mettere in relazione al periodo dell'anno.  
  
 Per trovare le informazioni richieste, in questa lezione si riepilogano i dati di vendita mensili dell'azienda e le cifre sulle vendite verranno suddivise in tre regioni: Europa, America del nord e Pacifico.  
  
 Dopo aver completato le attività di questa lezione, sarà possibile rispondere alle domande seguenti:  
  
-   In che modo le vendite di modelli diversi di biciclette cambiano nel corso del tempo?  
  
-   Esistono differenze tra i modelli di vendita nelle tre aree?  
  
-   È possibile prevedere i periodi di massima vendita?  
  
 È possibile completare la lezione in due parti:  
  
-   Nella prima parte si illustrano i concetti di base relativi alla creazione e all'utilizzo di un modello Time Series.  
  
-   Nella seconda parte viene illustrata la creazione di un modello Time Series generale, basato su tutte le aree. È possibile utilizzare questo modello generale per *Stima incrociata*.  
  
 Per completare le attività in questa lezione, elencate di seguito, si utilizzerà la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] dell'origine dati creata nel [lezione 1: creazione della soluzione di Data Mining dati intermedi &#40;esercitazione intermedia sul Data Mining Data&#41; ](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Le date di [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] database di esempio sono stati aggiornati per questa versione. Se si utilizza una versione precedente di [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], è possibile compilare il modello seguendo questi passaggi, ma è possibile che vengano visualizzati risultati diversi.  
  
 **Creazione di un modello di stima semplice**  
  
-   [Aggiunta di dati di un vista di origine per la previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [Creazione di una struttura di previsione e un modello &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Modifica della struttura di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [Personalizzazione ed elaborazione del modello di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Esplorazione del modello di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Creazione di stime basate su serie temporali &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **Creazione di un modello di previsione generale per la stima incrociata**  
  
-   [Stime basate su serie temporali avanzate &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [Stime basate su serie utilizzando dati aggiornati temporali &#40;esercitazione intermedia sul Data Mining Data&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [Stime basate su serie utilizzando dati di sostituzione temporali &#40;esercitazione intermedia sul Data Mining Data&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [Confronto delle stime per i modelli di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Aggiunta di dati di un vista di origine per la previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [Informazioni sui requisiti per una serie temporale del modello &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Tutte le lezioni  
 [Lezione 1: Creazione della soluzione intermedia di Data Mining &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Lezione 2: Scenario di previsione (Esercitazione intermedia sul data mining)  
  
 [Lezione 3: Compilazione di uno Scenario Market Basket &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lezione 4: Compilazione di una Scenario di Clustering delle sequenze &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Lezione 5: Compilazione di modelli di regressione logistica e di rete neurale &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazione di base di Data Mining](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Intermedi dell'esercitazione sul Data Mining &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Algoritmo Microsoft Time Series](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  