---
title: SELECT (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SELECT
dev_langs: DMX
helpviewer_keywords:
- browsing mining model [Analysis Services]
- TOP clause, SELECT
- FLATTENED option
- predictions [DMX]
- ORDER BY clause [DMX]
- SELECT statement [DMX]
- mining models [Analysis Services], browsing
- statements [DMX], SELECT statement
- WHERE clause, DMX
ms.assetid: 32d9e8fd-796b-4e1c-ae59-73cd6f645485
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 79fb3f8ce7766130ced9a8353a83e34bbbf007d1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="select-dmx"></a>SELECT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Il **selezionare** istruzione in estensioni DMX (Data Mining) viene utilizzata per le attività seguenti nel data mining:  
  
-   Visualizzazione del contenuto di un modello di data mining esistente  
  
-   Creazione di stime da un modello di data mining esistente.  
  
-   Creazione di una copia di un modello di data mining esistente.  
  
-   Visualizzazione della struttura di data mining  
  
 Sebbene la sintassi completa di questa istruzione sia complessa, le principali clausole utilizzate per la visualizzazione di un modello e della struttura sottostante possono essere riepilogate come segue:  
  
```  
SELECT [FLATTENED] [TOP <n>] <select list>  
FROM <model/structure>[.aspect]  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
## <a name="flattened"></a>FLATTENED  
 Alcuni client di data mining non possono accettare set di risultati in formato gerarchico da un provider di data mining. Il client potrebbe non essere in grado di gestire una gerarchia o potrebbe essere necessario archiviare i risultati in una singola tabella denormalizzata. Per convertire i dati da tabelle nidificate in tabelle in formato flat, è necessario richiedere che i risultati della query siano convertiti in formato flat.  
  
 Per unire i risultati della query, utilizzare il **selezionare** sintassi con il **FLATTENED** opzione, come illustrato nell'esempio seguente:  
  
```  
SELECT FLATTENED <select list> FROM ...  
```  
  
## <a name="top-n-and-order-by"></a>INIZIO \<n > e ORDER BY  
 È possibile ordinare i risultati di una query utilizzando un'espressione e quindi restituire un subset dei risultati utilizzando una combinazione del **ORDER BY** e **TOP** clausole. Questo è utile ad esempio in uno scenario di mailing diretto in cui si desidera inviare i risultati solo ai destinatari che hanno la maggiore probabilità di rispondere. È possibile ordinare i risultati di una destinazione mailing query di stima per la probabilità di stima e quindi restituire solo le prime \<n > risultati.  
  
## <a name="select-list"></a>Elenco di selezione  
 Il  *\<l'elenco di selezione >* possono includere riferimenti a colonne scalari, funzioni di stima ed espressioni. Le opzioni disponibili variano in base all'algoritmo e ai contesti seguenti:  
  
-   È in corso l'esecuzione di una query su una struttura di data mining o su un modello di data mining  
  
-   È in corso l'esecuzione di una query sul contenuto o sui case  
  
-   L'origine dati è una tabella relazionale o un cubo  
  
-   È in corso l'esecuzione di stime  
  
 In molti casi, è possibile utilizzare alias o creare espressioni semplici basate sugli elementi nell'elenco di selezione. Nell'esempio seguente viene illustrata un'espressione nelle colonne del modello:  
  
```  
SELECT [CustomerID], [Last Name] + ', ' + [FirstName] AS FullName  
FROM <model>.CASES  
```  
  
 Nell'esempio seguente viene creato un alias per una colonna che contiene i risultati di una funzione di stima:  
  
```  
SELECT Predict([Column1], 'Value') as Column1Prediction  
FROM MyModel  
JOIN <source data query>  
```  
  
## <a name="where"></a>WHERE  
 È possibile limitare i case restituiti dalla query utilizzando un **dove** clausola. Il **in cui** clausola specifica fa riferimento a tale colonna nel **in** l'espressione deve avere la stessa semantica di riferimenti a colonne il  *\<elenco di selezione >* del **selezionare** istruzione e possono restituire solo un'espressione booleana. La sintassi per la **dove** clausola è indicato di seguito  
  
```  
WHERE < condition expression >  
```  
  
 Elenco di selezione e **in** clausola di un **selezionare** istruzione deve seguire le regole seguenti:  
  
-   L'elenco di selezione deve contenere un'espressione che non restituisce un risultato booleano. L'espressione può essere modificata, ma deve comunque restituire risultati non booleani.  
  
-   Il **dove** clausola deve contenere un'espressione che restituisce un risultato booleano. La clausola può essere modificata, ma deve comunque restituire un risultato booleano.  
  
## <a name="predictions"></a>Stime  
 Esistono due tipi di sintassi che è possibile utilizzare per la creazione di stime:  
  
-   [SELECT FROM &#60; modello di &#62; DMX PREDICTION JOIN &#40; &#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
-   [SELECT FROM &#60; modello di &#62; &#40; DMX &#41;](../dmx/select-from-model-dmx.md)  
  
 Il primo tipo consente di creare stime complesse in tempo reale o in batch.  
  
 Il secondo consente di creare un prediction join vuoto su una colonna stimabile in un modello di data mining e restituisce lo stato più probabile della colonna. I risultati di questa query sono completamente basati sul contenuto del modello di data mining.  
  
 È possibile inserire un'istruzione select nella query di origine di un'istruzione SELECT FROM PREDICTION JOIN utilizzando la sintassi seguente.  
  
```  
SELECT FROM PREDICTION JOIN (<SELECT statement>) AS t, WHERE <SELECT statement>  
```  
  
 Per ulteriori informazioni sulla creazione di query di stima, vedere [struttura e utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md).  
  
## <a name="clause-syntax"></a>Sintassi delle clausole  
 A causa della complessità della visualizzazione con il **selezionare** istruzione, gli elementi della sintassi e gli argomenti sono descritti dalla clausola. Per ulteriori informazioni su ciascuna clausola, fare clic su un argomento indicato nell'elenco seguente:  
  
 [SELECT DISTINCT FROM &#60; modello di &#62; &#40; DMX &#41;](../dmx/select-distinct-from-model-dmx.md)  
  
 [SELECT FROM &#60; modello di &#62;. DMX contenuto &#40; &#41;](../dmx/select-from-model-content-dmx.md)  
  
 [SELECT FROM &#60; modello di &#62;. DMX casi &#40; &#41;](../dmx/select-from-model-cases-dmx.md)  
  
 [SELECT FROM &#60; modello di &#62;. DMX SAMPLE_CASES &#40; &#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
 [SELECT FROM &#60; modello di &#62;. DMX DIMENSION_CONTENT &#40; &#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
 [SELECT FROM &#60; modello di &#62; DMX PREDICTION JOIN &#40; &#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
 [SELECT FROM &#60; modello di &#62; &#40; DMX &#41;](../dmx/select-from-model-dmx.md)  
  
 [SELECT FROM &#60; struttura &#62;. CASI](../dmx/select-from-structure-cases.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)  
  
  
