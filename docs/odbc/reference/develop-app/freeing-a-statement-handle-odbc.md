---
title: Liberare un Handle di istruzione ODBC | Documenti Microsoft
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
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f05d09175f245d8136c7c36dce1794f4dd97410
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909656"
---
# <a name="freeing-a-statement-handle-odbc"></a>Liberare un Handle di istruzione ODBC
Come accennato in precedenza, è più efficiente riutilizzare le istruzioni di to eliminarli e allocarne di nuovi. Prima di eseguire una nuova istruzione SQL in un'istruzione, applicazioni devono essere certi che le impostazioni delle istruzioni correnti siano appropriati. Tra le impostazioni sono inclusi gli attributi di istruzione, le associazioni di parametri e le associazioni dei set di risultati. In genere, i parametri e set di risultati per l'istruzione SQL precedente devono essere non associato (chiamando **SQLFreeStmt** con le opzioni SQL_RESET_PARAMS e SQL_UNBIND) e rimbalzo per la nuova istruzione SQL.  
  
 Quando l'applicazione ha terminato di utilizzare l'istruzione, chiama **SQLFreeHandle** per liberare l'istruzione. Dopo aver liberato l'istruzione, è un'applicazione di un errore di programmazione da utilizzare l'handle dell'istruzione in una chiamata a una funzione ODBC; Questa operazione ha conseguenze irreversibili probabilmente ma non definiti.  
  
 Quando **SQLFreeHandle** viene chiamato, le versioni di driver, la struttura utilizzata per archiviare le informazioni sull'istruzione.  
  
 **SQLDisconnect** libera automaticamente tutte le istruzioni in una connessione.
