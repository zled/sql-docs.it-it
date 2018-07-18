---
title: 'Passaggio 4: recuperare i risultati | Documenti Microsoft'
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
- application process [ODBC], fetching results
- fetches [ODBC], fetching results
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d8d2e5bd80e47db5a5e3484aebfe2bf1d6fff9a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915746"
---
# <a name="step-4a-fetch-the-results"></a>Passaggio 4: recuperare i risultati
Il passaggio successivo è per recuperare i risultati, come illustrato nella figura seguente.  
  
 ![Recupero di risultati in un'applicazione ODBC](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Se l'istruzione eseguita in "Passaggio 3: compilazione ed eseguire un'istruzione SQL" è un **selezionare** istruzione o una funzione di catalogo, l'applicazione chiama innanzitutto **SQLNumResultCols** per determinare il numero di colonne nel set di risultati. Questo passaggio non è necessario se l'applicazione ha già conosce il numero di risultati di set di colonne, ad esempio quando l'istruzione SQL è hardcoded in un'applicazione personalizzata o verticale.  
  
 Successivamente, l'applicazione recupera il nome, tipo di dati, precisione e scala di ogni colonna del set di risultati con **SQLDescribeCol**. Nuovamente, questa operazione è necessario per le applicazioni, ad esempio applicazioni verticale e personalizzate che già conoscono queste informazioni. L'applicazione passa l'informazione a **SQLBindCol**, che associa una variabile di applicazione a una colonna nel set di risultati.  
  
 L'applicazione ora chiama **SQLFetch** per recuperare la prima riga di dati e inserire i dati da tale riga in variabili associate con **SQLBindCol**. Se sono presenti dati lungo nella riga, quindi chiama **SQLGetData** per recuperare i dati. L'applicazione continua a chiamare **SQLFetch** e **SQLGetData** per recuperare dati aggiuntivi. Al termine del recupero dei dati, chiama **SQLCloseCursor** per chiudere il cursore.  
  
 Per una descrizione completa di recupero dei risultati, vedere [il recupero dei risultati (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md) e [il recupero dei risultati (avanzate)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 A questo punto l'applicazione torna al "Passaggio 3: compilazione ed eseguire un'istruzione SQL" per l'esecuzione di un'altra istruzione nella stessa transazione; o procede al "Passaggio 5: Commit di transazioni" per eseguire il commit o il rollback della transazione.
