---
title: Embedded SQL | Documenti Microsoft
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
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7e27c80832143ff9907878ffc35c9479ce39ce1e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="embedded-sql"></a>Embedded SQL
La prima tecnica per l'invio di istruzioni SQL per il sistema DBMS è incorporata SQL. Poiché SQL non utilizza le variabili e le istruzioni del flusso di controllo, viene spesso utilizzato come un sottolinguaggio di database che può essere aggiunti a un programma scritto in un linguaggio di programmazione tradizionale, ad esempio C o COBOL. Si tratta di un'idea centrale di embedded SQL: inserimento di istruzioni SQL in un programma scritto in un host di linguaggio di programmazione. In breve, le tecniche seguenti vengono usate per incorporare le istruzioni SQL in un linguaggio host:  
  
-   Istruzioni SQL incorporate vengono elaborate da un speciale precompilatore SQL. Tutte le istruzioni SQL iniziano con un'introduzione e terminano con un carattere di terminazione, che contrassegna l'istruzione SQL per il precompilatore. L'introduzione e un carattere di terminazione variano con il linguaggio host. Ad esempio, l'introduzione è c "EXEC SQL" e "& SQL (" agli ORECCHIONI, e il carattere di terminazione è un punto e virgola (;) in C e una parentesi chiusa agli ORECCHIONI.  
  
-   Ogni volta che le costanti sono consentite, è possono utilizzare le variabili di applicazione, chiamata di variabili host, nelle istruzioni SQL incorporate. Possono essere usati per l'input per personalizzare un'istruzione SQL per una determinata situazione e nell'output di ricevere i risultati di una query.  
  
-   Le query che restituiscono una singola riga di dati vengono gestite con un'istruzione SELECT singleton. Questa istruzione specifica sia la query e le variabili di host in cui restituire i dati.  
  
-   Le query che restituiscono più righe di dati vengono gestite con i cursori. Un cursore tiene traccia della riga corrente all'interno di un set di risultati. L'istruzione DECLARE CURSOR definisce la query, l'istruzione OPEN inizia l'elaborazione di query, l'istruzione FETCH recupera le righe successive dei dati e l'istruzione CLOSE termina l'elaborazione delle query.  
  
-   Mentre un cursore è aperto, per gli aggiornamenti posizionati e le istruzioni delete posizionate consente di aggiornare o eliminare la riga attualmente selezionata dal cursore.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Esempio di Embedded SQL](../../odbc/reference/embedded-sql-example.md)  
  
-   [Compila un programma SQL incorporato](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [SQL statico](../../odbc/reference/static-sql.md)  
  
-   [SQL dinamico](../../odbc/reference/dynamic-sql.md)
