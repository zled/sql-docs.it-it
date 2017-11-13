---
title: Le applicazioni Unicode | Documenti Microsoft
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
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c99c74a1a294d7d43774fe9d53d169eece98d3ad
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="unicode-applications"></a>Applicazioni Unicode
È possibile ricompilare un'applicazione come un'applicazione Unicode in uno dei due modi:  
  
-   Includere Unicode **#define** contenuti nel file di intestazione sqlucode nell'applicazione.  
  
-   Compilare l'applicazione con l'opzione del compilatore Unicode. (Questa opzione è diversa per i compilatori diversi.)  
  
 Per convertire un'applicazione ANSI a un'applicazione Unicode, scrivere l'applicazione per archiviare e passare i dati Unicode. Inoltre, le chiamate alle funzioni che supportano gli argomenti SQLPOINTER devono essere convertite per utilizzare il numero di byte.  
  
 Dopo che un'applicazione viene compilata come un'applicazione Unicode, se l'applicazione chiama una funzione API ODBC (senza un suffisso), gestione Driver riconosce l'applicazione come un'applicazione Unicode e converte la chiamata di funzione a una funzione Unicode (con il  *W* suffisso) se il driver sottostante supporta Unicode. Quando un'applicazione ANSI esegue una funzione chiamata senza un suffisso, se il driver sottostante supporta ANSI gestione Driver converte in ANSI. Se l'applicazione e il driver supporta la stessa codifica dei caratteri, Gestione driver passa le chiamate al driver (con alcune eccezioni per le applicazioni ANSI).  
  
 Un'applicazione può chiamare entrambe le funzioni Unicode (con il *W* suffisso) e funzioni ANSI (con o senza il *A* suffisso). Unicode e ANSI chiamate di funzione possono essere combinate. Se è necessario utilizzare la libreria di cursori, tuttavia, Unicode e ANSI chiamate di funzione non possono essere combinate. La libreria di cursori è un valore Unicode o ANSI, non una combinazione.  
  
 Un'applicazione può essere scritta in modo che possa essere compilato come un'applicazione Unicode o un'applicazione ANSI. In questo caso, i tipi di dati carattere possono essere dichiarati come SQL_C_TCHAR. Si tratta di una macro che inserisce SQL_C_WCHAR se l'applicazione viene compilata come un'applicazione Unicode o inserisce SQL_C_CHAR se viene compilato come applicazione ANSI. Il programmatore di applicazioni è necessario prestare attenzione di funzioni che accettano SQLPOINTER come argomento, poiché le dimensioni dell'argomento length cambierà (per i tipi di dati stringa) a seconda che l'applicazione sia ANSI o Unicode.  
  
 Una funzione può essere chiamata in uno dei tre modi: come una chiamata di funzione solo Unicode (con il *W* suffisso), come una chiamata di funzione solo ANSI (con il *A* suffisso), o come chiamata di funzione ODBC senza alcun suffisso. Gli argomenti per le tre forme di una funzione sono identici. Solo le funzioni con SQLCHAR \* argomenti o SQLPOINTER che puntano alle stringhe richiedono form Unicode e ANSI. Per le funzioni presentano argomenti che possono essere dichiarati come un tipo di carattere, ad esempio **SQLBindCol** o **SQLGetData** (che non si dispone i form di Unicode e ANSI), l'argomento può essere dichiarato come tipo Unicode, ANSI digitare oppure nel caso di un C argomento, la macro SQL_C_TCHAR. Per ulteriori informazioni, vedere [dati Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Anche se non Unicode sono disponibili driver per funzionare con, un'applicazione può essere scritta come un'applicazione Unicode. Gestione Driver verrà eseguito il mapping tipi di dati e le funzioni Unicode ad ANSI. Esistono alcune restrizioni per Unicode per il mapping ANSI che possono essere eseguite. L'esistenza di un driver di Unicode per l'applicazione di Unicode funzionare con determinerà un miglioramento delle prestazioni e rimuoverà le limitazioni intrinseche in Unicode per il mapping ANSI.

