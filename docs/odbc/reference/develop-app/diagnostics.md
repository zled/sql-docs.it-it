---
title: Diagnostica | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d2db5f46fc157015f035775ac185fb9005de8a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910166"
---
# <a name="diagnostics"></a>Diagnostica
Funzioni ODBC restituiscono le informazioni di diagnostica in due modi. Il codice restituito indica l'esito positivo o negativo complessivo di funzione, mentre i record di diagnostica forniscono informazioni dettagliate sulla funzione. Almeno un record di diagnostica, ovvero il record di intestazione, viene restituito anche se la funzione ha esito positivo.  
  
 Informazioni di diagnostica viene utilizzate in fase di sviluppo per rilevare gli errori di programmazione quali gli handle non validi ed errori di sintassi nelle istruzioni SQL di livello di codice. E viene utilizzato in fase di esecuzione per rilevare errori di run-time e avvisi, ad esempio il troncamento dei dati, violazioni di accesso e gli errori di sintassi nelle istruzioni SQL immesse dall'utente.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Codici restituiti](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Record di diagnostica](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Utilizzo di SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implementazione di SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Esempi di gestione di diagnostica](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
