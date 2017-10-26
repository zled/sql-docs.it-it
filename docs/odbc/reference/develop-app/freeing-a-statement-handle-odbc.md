---
title: Liberare un Handle di istruzione ODBC | Documenti Microsoft
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
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b33d262c846d9ef8a41bf9440802664ac7d4b75f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="freeing-a-statement-handle-odbc"></a>Liberare un Handle di istruzione ODBC
Come accennato in precedenza, è più efficiente riutilizzare le istruzioni di to eliminarli e allocarne di nuovi. Prima di eseguire una nuova istruzione SQL in un'istruzione, applicazioni devono essere certi che le impostazioni delle istruzioni correnti siano appropriati. Tra le impostazioni sono inclusi gli attributi di istruzione, le associazioni di parametri e le associazioni dei set di risultati. In genere, i parametri e set di risultati per l'istruzione SQL precedente devono essere non associato (chiamando **SQLFreeStmt** con le opzioni SQL_RESET_PARAMS e SQL_UNBIND) e rimbalzo per la nuova istruzione SQL.  
  
 Quando l'applicazione ha terminato di utilizzare l'istruzione, chiama **SQLFreeHandle** per liberare l'istruzione. Dopo aver liberato l'istruzione, è un'applicazione di un errore di programmazione da utilizzare l'handle dell'istruzione in una chiamata a una funzione ODBC; Questa operazione ha conseguenze irreversibili probabilmente ma non definiti.  
  
 Quando **SQLFreeHandle** viene chiamato, le versioni di driver, la struttura utilizzata per archiviare le informazioni sull'istruzione.  
  
 **SQLDisconnect** libera automaticamente tutte le istruzioni in una connessione.

