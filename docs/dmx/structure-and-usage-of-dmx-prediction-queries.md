---
title: Struttura e l'utilizzo di query di stima DMX | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- prediction joins [DMX]
- empty prediction joins [DMX]
- natural prediction joins [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- queries [DMX], prediction queries
- singleton query predictions [DMX]
- Data Mining Extensions [Analysis Services], prediction queries
ms.assetid: 098bdaa6-9e7d-4e13-a9aa-eb17ce1750e6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fca2ff8ef1e6fbe496d412a82c1d2694005ffe6b
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>Struttura e utilizzo di query di stima DMX
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], è possibile utilizzare la query di stima di Data Mining DMX (Data Extensions) per stimare i valori di colonna sconosciuto in un nuovo set di dati, in base ai risultati di un modello di data mining.  
  
 Il tipo di query da utilizzare dipende dal tipo di informazioni che si desidera ottenere dal modello. Per creare semplici stime in tempo reale, ad esempio per sapere se il profilo di un potenziale cliente su un sito Web è quello di un acquirente di biciclette, è necessario utilizzare una query singleton. Se si desidera creare un batch di stime da un set di case contenuti in un'origine dati, utilizzare una query di stima regolare.  
  
## <a name="prediction-types"></a>Tipi di stima  
 È possibile utilizzare DMX per creare i tipi di stima seguenti:  
  
 Prediction join  
 Consente di creare stime sui dati di input in base ai modelli esistenti nel modello di data mining. Questa istruzione di query deve essere seguita da un **ON** clausola che fornisce le condizioni di join tra le colonne del modello di data mining e le colonne di input.  
  
 Natural prediction join  
 Consente di creare stime basate sui nomi di colonna del modello di data mining che corrispondono esattamente a quelli nella tabella su cui si esegue la query. Questa istruzione di query non richiede un **ON** clausola, perché la condizione di join viene generata automaticamente in base alla corrispondenza dei nomi tra le colonne del modello di data mining e le colonne di input.  
  
 Prediction join vuoto  
 Consente di individuare le stime più probabili, senza che sia necessario specificare dati di input. Viene così restituita una stima basata unicamente sul contenuto del modello di data mining.  
  
 Query singleton  
 Consente di creare una stima inviando i dati direttamente alla query. Questa istruzione è utile perché consente di inviare un singolo case alla query, per ottenere i risultati più rapidamente. È ad esempio possibile utilizzare questa query per stimare la probabilità che una donna sposata di 35 anni acquisti una bicicletta. Questa query non richiede un'origine dati esterna.  
  
## <a name="query-structure"></a>Struttura della query  
 Per compilare una query di stima in DMX è necessario combinare gli elementi seguenti:  
  
-   **SELEZIONARE [BIDIMENSIONALI]**  
  
-   **IN ALTO**  
  
-   **DA***\<modello >***PREDICTION JOIN**   
  
-   **ON**  
  
-   **DOVE**  
  
-   **ORDER BY**  
  
 Il **selezionare** set elemento di una query di stima definisce le colonne e delle espressioni che verranno visualizzato nel risultato, possono includere i dati seguenti:  
  
-   **Stimare** o **PredictOnly** dalle colonne del modello di data mining.  
  
-   Qualsiasi colonna dei dati di input utilizzata per creare le stime.  
  
-   Funzioni mediante le quali viene restituita una colonna di dati.  
  
 Il **FROM**  *\<modello >* **PREDICTION JOIN** elemento definisce i dati di origine da utilizzare per creare la stima. Per una query singleton tale origine è costituita da una serie di valori assegnati alle colonne. Per un prediction join vuoto l'origine dei dati viene lasciata vuota.  
  
 Il **ON** elemento mapping delle colonne che sono definite nel modello di data mining alle colonne in un set di dati esterno. Questo elemento non è necessario per la creazione di una query con prediction join vuoto o natural prediction join.  
  
 È possibile utilizzare il **dove** clausola per filtrare i risultati di una query di stima. È possibile utilizzare un **TOP** o **ORDER BY** clausola per selezionare le stime più probabile. Per ulteriori informazioni sull'utilizzo di queste clausole, vedere [DMX SELECT &#40; &#41;](../dmx/select-dmx.md).  
  
 Per ulteriori informazioni sulla sintassi di un'istruzione di stima, vedere [modello SELECT FROM &#60; &#62; DMX PREDICTION JOIN &#40; &#41; ](../dmx/select-from-model-prediction-join-dmx.md) e [SELECT FROM &#60; DMX modello &#62; &#40; &#41;](../dmx/select-from-model-dmx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Informazioni sull'istruzione Select di DMX](../dmx/understanding-the-dmx-select-statement.md)  
  
  

