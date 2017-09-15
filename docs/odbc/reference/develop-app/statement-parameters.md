---
title: Parametri dell'istruzione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement parameters [ODBC]
ms.assetid: 58d5b166-2578-4699-a560-1f1e6d86c49a
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5e56b61d47581f98f37560875de920c45029c2e9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="statement-parameters"></a>Parametri dell'istruzione
Oggetto *parametro* è una variabile in un'istruzione SQL. Si supponga, ad esempio, che in una tabella include colonne denominate PartID, la descrizione e prezzo. Per aggiungere una parte senza parametri richiederebbe la costruzione di un'istruzione SQL, ad esempio:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Sebbene questa istruzione consente di inserire un nuovo ordine, non è un'ottima soluzione per un'applicazione di immissione ordini perché i valori da inserire non possono essere hardcoded nell'applicazione. In alternativa è possibile creare l'istruzione SQL in fase di esecuzione utilizzando i valori da inserire. Questo non è una buona soluzione a causa della complessità di costruzione di istruzioni in fase di esecuzione. La soluzione migliore consiste nel sostituire gli elementi del **valori** clausola con punti interrogativi (?), o *marcatori di parametro*:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Gli indicatori di parametro vengono quindi associati a variabili dell'applicazione. Per aggiungere una nuova riga, l'applicazione deve solo impostare i valori delle variabili ed eseguire l'istruzione. Il driver recupera quindi i valori correnti delle variabili e li invia all'origine dati. Se l'istruzione viene eseguita più volte, l'applicazione può rendere ancora più efficiente il processo preparando l'istruzione.  
  
 L'istruzione riportata solo potrebbe essere a livello di codice in un'applicazione di immissione ordini per inserire una nuova riga. Tuttavia, i marcatori di parametro non sono limitati a applicazioni verticali. Per qualsiasi applicazione, consentono di semplificare le difficoltà di costruzione di istruzioni SQL in fase di esecuzione, evitando di conversioni da e verso il testo. Ad esempio, l'ID di parte riportata solo è probabilmente archiviati nell'applicazione come un numero intero. Se l'istruzione SQL viene creata senza i marcatori di parametro, l'applicazione deve convertire l'ID di parte di testo e l'origine dati deve convertire i dati in un numero intero. Un marcatore di parametro, l'applicazione può inviare l'ID di parte del driver come valore intero che in genere possibile inviarlo all'origine dati come un numero intero. In questo modo due conversioni. Per i valori di dati di tipo long, questo è molto importante, poiché i formati di testo di tali valori spesso superano la lunghezza consentita di un'istruzione SQL.  
  
 I parametri sono validi solo in determinate posizioni nelle istruzioni SQL. Ad esempio, non sono consentite nell'elenco di selezione (l'elenco di colonne deve essere restituito da un **selezionare** istruzione), né sono consentiti come entrambi gli operandi dell'operatore binario, ad esempio il segno di uguale (=), perché sarebbe impossibile per determinare il tipo di parametro. In genere, i parametri sono validi solo nelle istruzioni Data Manipulation Language (DML) e non in istruzioni Data Definition Language (DDL). Per ulteriori informazioni, vedere [marcatori di parametro](../../../odbc/reference/appendixes/parameter-markers.md) nella grammatica SQL di appendice c:.  
  
 Può essere utilizzato quando l'istruzione SQL richiama una stored procedure, i parametri denominata. I parametri denominati sono identificati dai relativi nomi, non in base alla posizione nell'istruzione SQL. Possono essere associate da una chiamata a **SQLBindParameter**, ma il parametro è identificato dal campo SQL_DESC_NAME di IPD (descrizione del parametro di implementazione), non dal *ParameterNumber* argomento di **SQLBindParameter**. Può inoltre essere associati chiamando **SQLSetDescField** o **SQLSetDescRec**. Per ulteriori informazioni sui parametri denominati, vedere [Binding Parameters by Name (Named Parameters)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md), più avanti in questa sezione. Per ulteriori informazioni sui descrittori, vedere [descrittori](../../../odbc/reference/develop-app/descriptors.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Parametri di associazione](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [Impostazione dei valori di parametro](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [L'invio di dati Long](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [Il recupero dei parametri di Output da SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [Parametri di routine](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [Matrici di valori di parametro](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)
