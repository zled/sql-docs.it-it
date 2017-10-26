---
title: Limitazioni di istruzione di inserimento | Documenti Microsoft
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
- ODBC SQL grammar, INSERT statement limitations
- INSERT statement limitations [ODBC]
- truncation of data [ODBC]
ms.assetid: dea05698-527a-41ab-8729-bbed85556185
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f9233e7582083ba08fb1239120e63db819b8724b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="insert-statement-limitations"></a>INSERIRE le limitazioni di istruzione
I dati inseriti viene troncati a destra senza visualizzare alcun avviso se è troppo lunga per rientrare nella colonna.  
  
 Il tentativo di inserire un valore che è compreso nell'intervallo del tipo di dati di una colonna che fa sì che un valore NULL da inserire nella colonna.  
  
 Quando viene utilizzato un file dBASE, Microsoft Excel, Paradox o Textdriver, inserire una stringa di lunghezza zero in una colonna effettivamente inserisce un valore NULL invece.  
  
 Quando viene utilizzato il driver di Microsoft Excel, se una stringa vuota viene inserita in una colonna, una stringa vuota verrà convertita in un valore NULL. viene eseguita un'istruzione di seleziona che viene eseguita con una stringa vuota nella clausola WHERE non verrà eseguita su tale colonna.  
  
 Una tabella non è aggiornabile dal driver Paradox in due condizioni:  
  
-   Quando non è definito un indice univoco nella tabella. Ciò non è possibile per una tabella vuota, che può essere aggiornata con una singola riga, anche se non è definito un indice univoco nella tabella. Se una singola riga viene inserita in una tabella vuota che non dispone di un indice univoco, un'applicazione non è possibile creare un indice univoco o inserire dati aggiuntivi dopo aver inserita la singola riga.  
  
-   Se il motore di Database di Borland non viene implementato, solo leggere e aggiungere le istruzioni sono consentite nella tabella Paradox.  
  
 Quando viene utilizzato il driver di testo, i valori NULL sono rappresentati da una stringa vuota a spaziatura nei file di lunghezza fissa, ma sono rappresentati in un file delimitato da virgole senza spazi. Nella seguente riga contenente tre campi, ad esempio, il secondo campo è un valore NULL:  
  
```  
"Smith:,, 123  
```  
  
 Quando viene utilizzato il driver di testo, tutti i valori di colonna possono essere riempiti con spazi iniziali. La lunghezza di qualsiasi riga deve essere minore o uguale a 65,543 byte.

