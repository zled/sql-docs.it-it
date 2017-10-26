---
title: 'Appendice e: funzioni scalari | Documenti Microsoft'
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
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aaa110a6a62ca91535e790a267ef714675719bf4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-e-scalar-functions"></a>Appendice e: funzioni scalari
ODBC specifica i tipi seguenti di funzioni scalari, con informazioni dettagliate su ognuno di questi tipi di funzione forniti nelle sezioni corrispondenti di questa appendice. Descrizioni delle funzioni includono sintassi associata.  
  
 Questa appendice contiene gli argomenti seguenti.  
  
-   [Funzioni stringa](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Funzioni numeriche](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Funzioni di intervallo, ora e data](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Funzioni di sistema](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Funzione di conversione di tipi di dati esplicite](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [Funzione CAST SQL-92](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC non implica un tipo di dati per i valori restituiti dalle funzioni scalari in quanto le funzioni sono spesso specifici dell'origine dati. Le applicazioni devono utilizzare la funzione scalare di CONVERTIRE ogni volta che è possibile forzare una conversione di tipi di dati.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Funzioni scalari ODBC e SQL-92  
 Le tabelle in questa appendice includono funzioni che sono stati aggiunti in ODBC 3.0 per la compatibilità con SQL-92. Tali funzioni per un particolare tipo di funzione scalare, come definito in ODBC sono indicati in ogni sezione.  
  
 ODBC e SQL-92 classificare le funzioni scalari in modo diverso. ODBC classifica le funzioni scalari dal tipo di argomento. SQL-92 classifica in base al valore restituito. Ad esempio, la funzione EXTRACT è classificata come funzione timedate da ODBC, in quanto l'argomento di estrazione campo è una parola chiave Data/ora e l'argomento di origine di estrazione è un'espressione datetime o intervallo. SQL-92, d'altra parte, classifica estrazione come una funzione scalare di tipo numerica, perché il valore restituito è un valore numerico.  
  
 Un'applicazione può determinare che un driver supporta chiamando le funzioni scalari **SQLGetInfo**. Tipi di informazioni sono inclusi sia per ODBC per SQL-92 classificazioni di funzioni scalari. Perché le classificazioni sono diverse, il supporto per alcune funzioni scalari può essere indicato in tipi di informazioni che non corrispondono a ODBC e SQL-92. Ad esempio, il supporto per l'estrazione in ODBC è indicato dal tipo di informazioni SQL_TIMEDATE_FUNCTIONS. supporto per l'estrazione in SQL-92, d'altra parte, è indicato dal tipo di informazioni SQL_SQL92_NUMERIC_VALUE_FUNCTIONS.

