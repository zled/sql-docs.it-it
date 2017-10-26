---
title: Diagnostica | Documenti Microsoft
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
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: adb6f66ecfbff558fd163437a56453efb4265185
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="diagnostics"></a>Diagnostica
Funzioni ODBC restituiscono le informazioni di diagnostica in due modi. Il codice restituito indica l'esito positivo o negativo complessivo di funzione, mentre i record di diagnostica forniscono informazioni dettagliate sulla funzione. Almeno un record di diagnostica, ovvero il record di intestazione, viene restituito anche se la funzione ha esito positivo.  
  
 Informazioni di diagnostica viene utilizzate in fase di sviluppo per rilevare gli errori di programmazione quali gli handle non validi ed errori di sintassi nelle istruzioni SQL di livello di codice. E viene utilizzato in fase di esecuzione per rilevare errori di run-time e avvisi, ad esempio il troncamento dei dati, violazioni di accesso e gli errori di sintassi nelle istruzioni SQL immesse dall'utente.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Codici restituiti](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Record di diagnostica](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Utilizzando SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implementazione SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Esempi di gestione di diagnostica](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)

