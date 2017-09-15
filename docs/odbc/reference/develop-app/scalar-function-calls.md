---
title: Chiamate di funzione scalare | Documenti Microsoft
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
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3fb62d7c916584da7411f398f66a2acf134bfa24
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="scalar-function-calls"></a>Chiamate di funzione scalare
Funzioni scalari restituiscono un valore per ogni riga. Ad esempio, la funzione scalare del valore assoluto accetta una colonna numerica come argomento e restituisce il valore assoluto di ogni valore nella colonna. La sequenza di escape per chiamare una funzione scalare  
  
 **{fn***funzione scalare* **}  **  
  
 dove *funzione scalare* è una delle funzioni elencate [appendice e: le funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Per ulteriori informazioni sulla sequenza di escape funzione scalare, vedere [sequenza di Escape funzione scalare](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) nella grammatica SQL di appendice c:.  
  
 Le istruzioni SQL seguenti, ad esempio, creano lo stesso set di risultati di cliente maiuscolo nomi. La prima istruzione utilizza la sintassi della sequenza di escape. La seconda istruzione utilizza la sintassi nativa per Ingres per OS/2 e non è interoperativa.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Un'applicazione è possibile combinare le chiamate alle funzioni scalari che utilizzano la sintassi native e chiamate alle funzioni scalari che utilizzano la sintassi ODBC. Ad esempio, si supponga che i nomi della tabella Employee vengono archiviati come un cognome, virgola e un nome. L'istruzione SQL seguente crea un set di risultati dei cognomi dei dipendenti nella tabella Employee. L'istruzione utilizza la funzione scalare ODBC **SOTTOSTRINGA** e la funzione scalare di SQL Server **CHARINDEX** e verrà eseguita correttamente solo in SQL Server.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) – 1)} FROM Customers  
```  
  
 Per garantire la massima interoperabilità, le applicazioni devono utilizzare il **CONVERTIRE** funzione scalare per assicurarsi che l'output di una funzione scalare è il tipo richiesto. Il **CONVERTIRE** funzione converte i dati da un tipo di dati SQL per il tipo di dati SQL specificato. La sintassi del **CONVERTIRE** è (funzione)  
  
 **CONVERTIRE (** *value_exp* **,** *data_type***)**  
  
 in cui *value_exp* è un nome di colonna, il risultato di un'altra funzione scalare o un valore letterale, e *data_type* è una parola chiave che soddisfi il **#define** nome utilizzato da un Identificatore di tipo di dati SQL come definito in [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md). Ad esempio, l'istruzione SQL seguente utilizza il **CONVERTIRE** funzione per verificare che l'output del **CURDATE** funzione è una data, anziché un timestamp o caratteri di dati:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Per determinare quali funzioni scalari sono supportate da un'origine dati, un'applicazione chiama **SQLGetInfo** con SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS e SQL_TIMEDATE_ Opzioni di funzioni. Per determinare quali operazioni di conversione sono supportate per il **CONVERTIRE** funzione, un'applicazione chiama **SQLGetInfo** con le opzioni che iniziano con SQL_CONVERT.
