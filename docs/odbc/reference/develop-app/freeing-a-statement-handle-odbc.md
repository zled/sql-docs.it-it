---
title: Liberare un Handle di istruzione ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a26d7745756904ab8da492cbb96b8714dd969e1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="freeing-a-statement-handle-odbc"></a>Liberare un Handle di istruzione ODBC
Come accennato in precedenza, è più efficiente riutilizzare le istruzioni di to eliminarli e allocarne di nuovi. Prima di eseguire una nuova istruzione SQL in un'istruzione, applicazioni devono essere certi che le impostazioni delle istruzioni correnti siano appropriati. Tra le impostazioni sono inclusi gli attributi di istruzione, le associazioni di parametri e le associazioni dei set di risultati. In genere, i parametri e set di risultati per l'istruzione SQL precedente devono essere non associato (chiamando **SQLFreeStmt** con le opzioni SQL_RESET_PARAMS e SQL_UNBIND) e rimbalzo per la nuova istruzione SQL.  
  
 Quando l'applicazione ha terminato di utilizzare l'istruzione, chiama **SQLFreeHandle** per liberare l'istruzione. Dopo aver liberato l'istruzione, è un'applicazione di un errore di programmazione da utilizzare l'handle dell'istruzione in una chiamata a una funzione ODBC; Questa operazione ha conseguenze irreversibili probabilmente ma non definiti.  
  
 Quando **SQLFreeHandle** viene chiamato, le versioni di driver, la struttura utilizzata per archiviare le informazioni sull'istruzione.  
  
 **SQLDisconnect** libera automaticamente tutte le istruzioni in una connessione.
