---
title: Gestione degli errori e messaggi | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 41e489021da15dc54e076467f5b366bef87a26a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156921"
---
# <a name="handling-errors-and-messages"></a>Gestione di errori e messaggi
  Quando un'applicazione chiama una funzione ODBC, il driver esegue la funzione e restituisce le informazioni di diagnostica in due modi: un codice restituito indica l'esito positivo o negativo complessivo di una funzione ODBC e i record di diagnostica forniscono informazioni dettagliate sulla funzione. I record di diagnostica includono un record di intestazione e record di stato. Anche se la funzione riesce, viene restituito almeno un record di diagnostica, ovvero il record di intestazione.  
  
 Le informazioni di diagnostica vengono utilizzate in fase di sviluppo per rilevare errori di programmazione, ad esempio handle ed errori di sintassi non validi nelle istruzioni SQL hard-coded. Vengono utilizzate anche in fase di esecuzione per rilevare avvisi ed errori di runtime, ad esempio troncamento di dati, violazioni di regole ed errori di sintassi nelle istruzioni SQL immesse dall'utente. La logica del programma si basa generalmente sui codici restituiti.  
  
 Ad esempio, dopo che un'applicazione chiama **SQLFetch** per recuperare le righe in un set di risultati, il codice restituito indica se è stata raggiunta la fine del set di risultati (SQL_NO_DATA), se sono stati restituiti (SQL_SUCCESS_ eventuali messaggi informativi WITH_INFO), o se si è verificato un errore (SQL_ERROR).  
  
 Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client restituisce un valore diverso da SQL_SUCCESS, l'applicazione può chiamare **SQLGetDiagRec** per recuperare informativi o messaggi di errore. Uso **SQLGetDiagRec** spostarsi su e giù il messaggio impostato se è presente più di un messaggio.  
  
 Il codice restituito SQL_INVALID_HANDLE indica sempre un errore di programmazione e non dovrebbe essere mai rilevato in fase di esecuzione. Tutti gli altri codici restituiti forniscono informazioni di runtime, anche se SQL_ERROR potrebbe indicare un errore di programmazione.  
  
 Originale [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] API native, DB-Library per C, consente a un'applicazione installare Gestione degli errori di callback e le funzioni di gestione dei messaggi che restituiscono errori o messaggi. Alcune istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio PRINT, RAISERROR, DBCC e SET, restituiscono i risultati alla funzione di gestione dei messaggi di DB-Library anziché a un set di risultati. L'API ODBC invece non presenta alcuna funzionalità di callback di questo tipo. Quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client rileva messaggi che provengono da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], imposta il codice restituito di ODBC su SQL_SUCCESS_WITH_INFO o SQL_ERROR e restituisce il messaggio come uno o più record di diagnostica. Pertanto, un'applicazione ODBC deve testare attentamente questi codici restituiti e chiamare **SQLGetDiagRec** per recuperare i dati del messaggio.  
  
 Per informazioni sulla traccia degli errori, vedere [traccia di accesso ai dati](http://go.microsoft.com/fwlink/?LinkId=125805). Per informazioni sui miglioramenti apportati alla traccia di errori aggiunta in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vedere [l'accesso a informazioni di diagnostica nel Log degli eventi estesi](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Elaborazione di istruzioni che generano messaggi](processing-statements-that-generate-messages.md)  
  
-   [Campi e record di diagnostica](diagnostic-records-and-fields.md)  
  
-   [Numeri di errori nativi](native-error-numbers.md)  
  
-   [SQLSTATE &#40;codici di errore ODBC&#41;](sqlstate-odbc-error-codes.md)  
  
-   [Messaggi di errore](error-messages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  