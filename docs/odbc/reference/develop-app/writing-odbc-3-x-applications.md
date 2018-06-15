---
title: Scrittura nelle applicazioni ODBC 3. x | Documenti Microsoft
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
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee0aa19520ec0d6e3f2f0f6852cb40578f81247c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32919146"
---
# <a name="writing-odbc-3x-applications"></a>Scrittura di applicazioni ODBC 3. x
Quando un'applicazione ODBC 2. *x* applicazione viene aggiornata a ODBC 3. *x*, deve essere scritto in modo che funziona con entrambi ODBC 2. *x* e 3. *x* driver. L'applicazione deve incorporare il codice condizionale per usufruire di ODBC 3. *x* funzionalità.  
  
 L'attributo di ambiente SQL_ATTR_ODBC_VERSION deve essere impostato su SQL_OV_ODBC2. Ciò garantisce che il driver si comporta come un ODBC 2*x* driver per quanto riguarda le modifiche descritte nella sezione [modifiche del comportamento](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Se l'applicazione utilizzerà le funzionalità descritte nella sezione [nuove funzionalità](../../../odbc/reference/develop-app/new-features.md), il codice condizionale deve essere utilizzato per determinare se il driver è un'applicazione ODBC 3. *x* o 2 di ODBC*x* driver. L'applicazione utilizza **SQLGetDiagField** e **SQLGetDiagRec** per ottenere ODBC 3. *x* SQLSTATE durante l'esecuzione di errore durante l'elaborazione in questi frammenti di codice condizionale. È necessario considerare i punti seguenti circa le nuove funzionalità:  
  
-   Un'applicazione interessata dalla modifica del comportamento di dimensioni del set di righe deve prestare attenzione a non chiamare **SQLFetch** quando le dimensioni della matrice sono maggiore di 1. Sostituiscono le chiamate a queste applicazioni **SQLExtendedFetch** con chiamate a **SQLSetStmtAttr** per impostare l'attributo di istruzione SQL_ATTR_ARRAY_STATUS_PTR e **SQLFetchScroll**, in modo che dispongano di un codice comune che funziona con entrambi ODBC 3. *x* e ODBC 2. *x* driver. Poiché **SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE verranno mappati a **SQLSetStmtAttr** con SQL_ROWSET_SIZE per ODBC 2. *x* driver, le applicazioni possono solo impostare SQL_ATTR_ROW_ARRAY_SIZE per le operazioni di recupero su più righe.  
  
-   La maggior parte delle applicazioni che esegue l'aggiornamento non vengono effettivamente interessate dalle modifiche apportate ai codici SQLSTATE. Per le applicazioni che sono interessate, possono eseguire una ricerca meccanica e sostituisci nella maggior parte dei casi, utilizzare la tabella di conversione di errore nella sezione "Mapping di SQLSTATE" per convertire ODBC 3. *x* codici di errore da ODBC 2*x* codici. Poiché ODBC 3*x* Driver Manager eseguirà il mapping da ODBC 2. *x* SQLSTATE per ODBC 3. *x* SQLSTATE, gli autori di tali applicazioni devono solo controllo per ODBC 3. *x* SQLSTATE senza preoccuparsi incluso ODBC 2. *x* SQLSTATE nel codice condizionale.  
  
-   Se un'applicazione utilizza in modo ottimale di data, ora e tipi di dati timestamp, l'applicazione può dichiarare stesso si trovi un ODBC 2. *x* applicazione e l'utilizzo di codice esistenti anziché condizionata codice.  
  
 L'aggiornamento deve includere anche i passaggi seguenti:  
  
-   Chiamare **SQLSetEnvAttr** prima di allocare una connessione per impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
-   Sostituire tutte le chiamate a **SQLAllocEnv**, **SQLAllocConnect**, o **SQLAllocStmt** con chiamate a **SQLAllocHandle** con l'appropriato *HandleType* argomento impostato su SQL_HANDLE_ENV, impostato su SQL_HANDLE_DBC o impostato su SQL_HANDLE_STMT.  
  
-   Sostituire tutte le chiamate a **SQLFreeEnv** o **SQLFreeConnect** con chiamate a **SQLFreeHandle** con l'appropriato *HandleType* argomento impostato su SQL_HANDLE_DBC o impostato su SQL_HANDLE_STMT.  
  
-   Sostituire tutte le chiamate a **SQLSetConnectOption** con chiamate a **SQLSetConnectAttr**. Se l'impostazione di un attributo il cui valore è una stringa, impostare il *StringLength* argomento in modo appropriato. Modifica *attributo* argomento da SQL_XXXX SQL_ATTR_XXXX.  
  
-   Sostituire tutte le chiamate a **SQLGetConnectOption** con chiamate a **SQLGetConnectAttr**. Se una stringa o un attributo binario, impostare *BufferLength* per il valore appropriato e passare un *StringLength* argomento. Modifica *attributo* argomento da SQL_XXXX SQL_ATTR_XXXX.  
  
-   Sostituire tutte le chiamate a **SQLSetStmtOption** con chiamate a **SQLSetStmtAttr**. Se l'impostazione di un attributo il cui valore è una stringa, impostare il *StringLength* argomento in modo appropriato. Modifica *attributo* argomento da SQL_XXXX SQL_ATTR_XXXX.  
  
-   Sostituire tutte le chiamate a **SQLGetStmtOption** con chiamate a **SQLGetStmtAttr**. Se una stringa o un attributo binario, impostare *BufferLength* per il valore appropriato e passare un *StringLength* argomento. Modifica *attributo* argomento da SQL_XXXX SQL_ATTR_XXXX.  
  
-   Sostituire tutte le chiamate a **SQLTransact** con chiamate a **SQLEndTran**. Se l'handle valido a destra il **SQLTransact** chiamata è un handle di ambiente, un *HandleType* argomento impostato su SQL_HANDLE_ENV deve essere usato nel **SQLEndTran** chiamata con appropriata *gestire* argomento. Se l'handle valido a destra il **SQLTransact** chiamata è un handle di connessione, un *HandleType* argomento impostato su SQL_HANDLE_DBC deve essere usato nel **SQLEndTran** chiamata con appropriata *gestire* argomento.  
  
-   Sostituire tutte le chiamate a **SQLColAttributes** con chiamate a **SQLColAttribute**. Se il *FieldIdentifier* argomento è SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE o SQL_COLUMN_LENGTH, non modificare qualsiasi elemento diverso dal nome della funzione. In caso contrario, modificare *FieldIdentifier* da SQL_COLUMN_XXXX a SQL_DESC_XXXX. Se *FieldIdentifier* è SQL_DESC_CONCISE_TYPE e il tipo di dati è un tipo di dati datetime, modificare per il corrispondente di ODBC 3*x* tipo di dati.  
  
-   Se si utilizza cursori a blocchi, i cursori scorrevoli o entrambi, l'applicazione effettua quanto segue:  
  
    -   Imposta le dimensioni del set di righe, il tipo di cursore e concorrenza cursore utilizzando **SQLSetStmtAttr**.  
  
    -   Chiamate **SQLSetStmtAttr** Impostare SQL_ATTR_ROW_STATUS_PTR affinché punti a una matrice di record di stato.  
  
    -   Chiamate **SQLSetStmtAttr** impostare SQL_ATTR_ROWS_FETCHED_PTR affinché faccia riferimento a un SQLINTEGER.  
  
    -   Esegue le associazioni necessarie ed esegue l'istruzione SQL.  
  
    -   Chiamate **SQLFetchScroll** impostato in un ciclo per recuperare righe e spostarsi nel risultato.  
  
    -   Se si desidera recuperare dal segnalibro, l'applicazione chiama **SQLSetStmtAttr** impostare SQL_ATTR_FETCH_BOOKMARK_PTR a una variabile che conterrà il segnalibro per la riga che desidera recuperare, quindi chiama **SQLFetchScroll** con un *FetchOrientation* argomento impostato su sql_fetch_bookmark.  
  
-   Se l'utilizzo delle matrici di parametri, l'applicazione effettua quanto segue:  
  
    -   Chiamate **SQLSetStmtAttr** per impostare l'attributo SQL_ATTR_PARAMSET_SIZE alle dimensioni della matrice di parametri.  
  
    -   Chiamate **SQLSetStmtAttr** impostare SQL_ATTR_ROWS_PROCESSED_PTR in modo che punti a una variabile UDWORD interna.  
  
    -   Esegue preparare, associare ed eseguire operazioni come appropriato.  
  
    -   Se l'esecuzione si interrompe per qualche motivo (ad esempio SQL_NEED_DATA), è possibile trovare la riga "corrente" dei parametri controllando il percorso a cui puntato SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Mapping di funzioni di sostituzione per la compatibilità con le versioni precedenti delle applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Chiamata di SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Chiamata di SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Chiamata di SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Operazioni della libreria di cursori](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Mapping degli attributi del cursore1 Tipi di informazioni](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
