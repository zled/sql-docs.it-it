---
title: SELECT (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: def96304f13f57095679056e6eab0a004b5c47d9
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842644"
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
  
-   [SELECT FROM &#60;modello&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
-   [SELECT FROM &#60;modello&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 Il primo tipo consente di creare stime complesse in tempo reale o in batch.  
  
 Il secondo consente di creare un prediction join vuoto su una colonna stimabile in un modello di data mining e restituisce lo stato più probabile della colonna. I risultati di questa query sono completamente basati sul contenuto del modello di data mining.  
  
 È possibile inserire un'istruzione select nella query di origine di un'istruzione SELECT FROM PREDICTION JOIN utilizzando la sintassi seguente.  
  
```  
SELECT FROM PREDICTION JOIN (<SELECT statement>) AS t, WHERE <SELECT statement>  
```  
  
 Per ulteriori informazioni sulla creazione di query di stima, vedere [struttura e utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md).  
  
## <a name="clause-syntax"></a>Sintassi delle clausole  
 A causa della complessità della visualizzazione con il **selezionare** istruzione, gli elementi della sintassi e gli argomenti sono descritti dalla clausola. Per ulteriori informazioni su ciascuna clausola, fare clic su un argomento indicato nell'elenco seguente:  
  
 [SELECT DISTINCT FROM &#60;modello &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
 [SELECT FROM &#60;modello&#62;. CONTENUTO &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
 [SELECT FROM &#60;modello&#62;. CASI &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
 [SELECT FROM &#60;modello&#62;. SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
 [SELECT FROM &#60;modello&#62;. DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
 [SELECT FROM &#60;modello&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
 [SELECT FROM &#60;modello&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 [SELECT FROM &#60;struttura&#62;. CASI](../dmx/select-from-structure-cases.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)  
  
  
