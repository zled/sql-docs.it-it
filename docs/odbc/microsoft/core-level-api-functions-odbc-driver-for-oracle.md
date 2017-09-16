---
title: Funzioni API di livello, il Driver ODBC per Oracle, di base | Documenti Microsoft
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
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- core level API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 8596eed7-bda6-4cac-ae1f-efde1aab785f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3bc36063659da3cf0cd6b2b837be0c4fce46c6f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>Funzioni API di livello principale (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Funzioni a questo livello costituiscono il livello minimo di conformità di interfaccia per i driver ODBC.  
  
|Funzione API|Note|  
|------------------|-----------|  
|**SQLAllocConnect**|Alloca memoria per un handle di connessione, *hdbc*, all'interno dell'ambiente identificato da *henv*. Gestione Driver elabora questa chiamata e il driver chiama **SQLAllocConnect** funzione ogni volta che **SQLConnect**, **SQLBrowseConnect**, o ** SQLDriverConnect** viene chiamato.|  
|**SQLAllocEnv**|Visualizza una finestra di dialogo che specifica il requisito per il software Client Oracle e quindi restituisce SQL_NULL_HANDLE. Se non è installato il software Client Oracle, questa funzione alloca memoria per un handle di ambiente, *henv*e inizializza l'interfaccia del livello di chiamata ODBC per l'utilizzo da parte di un'applicazione.|  
|**SQLAllocStmt**|Alloca memoria per un handle di istruzione e associa l'handle di istruzione con la connessione specificata dall'oggetto hdbc. Gestione Driver passa la chiamata al driver, che consente di allocare la memoria per la struttura hstmt.|  
|**SQLBindCol**|Assegna spazio di archiviazione per una colonna di risultati e specifica il tipo del risultato.|  
|**SQLCancel**|Annulla l'elaborazione su un handle di istruzione, hstmt. In alcuni casi, Oracle non consente l'annullamento di un'istruzione in esecuzione. Ciò significa che un'istruzione in esecuzione continua fino al Oracle completa il processo, nel qual caso i risultati dalle istruzioni vengono annullati dal Driver ODBC per Oracle.|  
|**SQLColAttributes**|Restituisce informazioni sul descrittore per una colonna in un set di risultati. Informazioni del descrittore viene restituite come una stringa di caratteri, un dipendente dal descrittore di valore a 32 bit o un valore intero.|  
|**SQLConnect**|Si connette a un'origine dati. Per utilizzare l'autenticazione del sistema operativo di Oracle, specificare "/" come il *szUID* parametro e "" come il *szAuthStr* parametro.|  
|**SQLDescribeCol**|Restituisce il nome, tipo, precisione, scala e supporto di valori null della colonna di risultati specificato. **Nota:****SQLDescribeCol** riporta le colonne calcolate come SQL_VARCHAR.  |  
|**SQLDisconnect**|Chiude una connessione. Se il pool di connessioni è abilitato per un ambiente condiviso e un'applicazione chiama **SQLDisconnect** su una connessione in tale ambiente, la connessione viene restituita al pool di connessioni ed è ancora disponibile per altri componenti utilizzando lo stesso ambiente condiviso.|  
|**SQLError**|Restituisce le informazioni di stato o di errore sull'ultimo errore. Il driver gestisce un stack o un elenco di errori che possono essere restituite per il *hstmt*, *hdbc*, e *henv* argomenti, a seconda di come la chiamata a **SQLError ** viene eseguita. La coda di errore viene svuotata dopo ogni istruzione. In genere recupera un messaggio di errore Oracle e in caso contrario è vuoto.|  
|**SQLExecDirect**|Esegue un'istruzione SQL nuovo, non preparata. Il driver utilizza i valori correnti delle variabili di marcatore di parametro, se sono presenti parametri nell'istruzione. La tabella, vista o i nomi dei campi contengono spazi, racchiudere i nomi di backup offerta contrassegni. Ad esempio, se il database contiene una tabella denominata *tabella personale* e il campo *My Field*, racchiudere ogni elemento dell'identificatore in questo modo:<br /><br /> Selezionare \`tabella\`. \`My Field1\`, \`Tabella\`.\` My Field2\` FROM \`la tabella '|  
|**SQLExecute**|Esegue un'istruzione SQL preparata (un'istruzione già preparata da **SQLPrepare**). Il driver utilizza i valori correnti delle variabili di marcatore di parametro, se sono presenti parametri nell'istruzione.|  
|**SQLFetch**|Recupera una riga da un set di risultati in percorsi specificati dalle chiamate precedenti alla **SQLBindCol**. Prepara il driver per una chiamata a **SQLGetData** per le colonne non associate.|  
|**SQLFreeConnect**|Rilascia un handle di connessione e libera tutta la memoria allocata per l'handle.|  
|**SQLFreeEnv**|Chiude il Driver ODBC per Oracle e rilascia tutta la memoria associata al driver.|  
|**SQLFreeStmt**|Arresta elaborazione associata a un oggetto specifico hstmt, chiude tutti i cursori aperti associati hstmt, Elimina i risultati in sospeso e facoltativamente libera tutte le risorse associate all'handle di istruzione.|  
|**SQLGetCursorName**|Restituisce il nome del cursore associato hstmt specificato.|  
|**SQLNumResultCols**|Restituisce il numero di colonne in un cursore del set di risultati.|  
|**SQLPrepare**|Prepara un'istruzione SQL tramite la pianificazione come ottimizzare ed eseguire l'istruzione. L'istruzione SQL viene compilata per l'esecuzione da **SQLExecDirect**.<br /><br /> La tabella, vista o i nomi dei campi contengono spazi, racchiudere i nomi di backup offerta contrassegni. Ad esempio, se il database contiene una tabella denominata *tabella personale* e il campo *My Field*, racchiudere ogni elemento dell'identificatore, come indicato di seguito:<br /><br /> Selezionare \`tabella\`.\` Campo\` FROM \`la tabella '<br /><br /> Per informazioni sull'utilizzo di set di risultati che contengono matrici di parametri formali, vedere [la restituzione di parametri di matrice dalle Stored procedure](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle non fornisce un modo per determinare il numero di righe nel risultato fino a quando una volta recuperare l'ultima riga, quindi restituisce – 1.|  
|**SQLSetCursorName**|Associa un nome di cursore con un handle di istruzione attiva, *hstmt*.|  
|**SQLSetParam**|Sostituito da SQLBindParameter in ODBC 2. *x*.|  
|**SQLTransact**|Richiede un'operazione di commit o rollback per tutte le operazioni attive in tutti gli handle di istruzione (hstmts) associati a una connessione o per tutte le connessioni associate all'handle di ambiente, *henv*. Se un'operazione di commit ha esito negativo quando è in modalità manuale, la transazione rimane attiva. è possibile scegliere di eseguire il rollback della transazione o ripetere l'operazione di commit. Se un'operazione di commit ha esito negativo quando è in modalità automatica delle transazioni, il rollback della transazione. la transazione non può essere inattiva.|
