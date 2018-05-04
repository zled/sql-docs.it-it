---
title: Funzione SQLGetInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLGetInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInfo
helpviewer_keywords:
- SQLGetInfo function [ODBC]
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
caps.latest.revision: 48
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ddc8bc66f3c20b544872be49e7b7cfa6a7420520
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetinfo-function"></a>Funzione SQLGetInfo
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLGetInfo** restituisce informazioni generali sul driver e l'origine dati associata a una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *InfoType*  
 [Input] Tipo di informazioni.  
  
 *InfoValuePtr*  
 [Output] Puntatore a un buffer in cui si desidera restituire le informazioni. A seconda di *InfoType* richiesto, le informazioni restituite sarà uno dei seguenti: una stringa di caratteri con terminazione null, un valore SQLUSMALLINT, una maschera di bit SQLUINTEGER, un flag SQLUINTEGER, un valore binario SQLUINTEGER, o Valore SQLULEN.  
  
 Se il *InfoType* argomento è SQL_DRIVER_HDESC o SQL_DRIVER_HSTMT, il *InfoValuePtr* argomento è sia di input e output. (Vedere i descrittori SQL_DRIVER_HDESC o SQL_DRIVER_HSTMT più avanti in questa descrizione della funzione per altre informazioni).  
  
 Se *InfoValuePtr* è NULL, *StringLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui fa riferimento *InfoValuePtr*.  
  
 *BufferLength*  
 [Input] Lunghezza di \* *InfoValuePtr* buffer. Se il valore in  *\*InfoValuePtr* non è una stringa di caratteri o se *InfoValuePtr* è un puntatore null, il *BufferLength* argomento viene ignorato. Il driver presuppone che le dimensioni di  *\*InfoValuePtr* è SQLUSMALLINT o SQLUINTEGER, in base il *InfoType*. Se  *\*InfoValuePtr* è una stringa Unicode (quando si chiama **SQLGetInfoW**), il *BufferLength* argomento deve essere un numero pari; se non, SQLSTATE HY090 ( Lunghezza della stringa o di buffer non valido) viene restituito.  
  
 *StringLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile per restituire **InfoValuePtr*.  
  
 Per i dati di tipo carattere, se il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength*, le informazioni contenute in \* *InfoValuePtr* viene troncato a  *BufferLength* byte meno la lunghezza di una terminazione null di caratteri ed è con terminazione null dal driver.  
  
 Per tutti gli altri tipi di dati, il valore di *BufferLength* viene ignorato e il driver presuppone che le dimensioni di \* *InfoValuePtr* è SQLUSMALLINT o SQLUINTEGER, a seconda di  *InfoType*.  
  
## <a name="return-value"></a>Valore restituito  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetInfo** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLGetInfo** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *InfoValuePtr* non sia abbastanza grande per restituire tutte le informazioni richieste. Pertanto, le informazioni sono state troncate. Viene restituita la lunghezza delle informazioni richieste nella forma non troncato **StringLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08003|Connessione non aperta|(DM) il tipo di informazioni di richiesta *InfoType* richiede una connessione aperta. Tra i tipi di informazioni riservati da ODBC, solo SQL_ODBC_VER può essere restituito senza una connessione aperta.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY024|Valore dell'attributo non valido|(DM) il *InfoType* argomento è stato SQL_DRIVER_HSTMT e il valore a cui puntava *InfoValuePtr* non è un handle di istruzione valida.<br /><br /> (DM) il *InfoType* argomento è stato SQL_DRIVER_HDESC e il valore a cui puntava *InfoValuePtr* non è un handle di descrittore valido.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *BufferLength* era minore di 0.<br /><br /> (DM) il valore specificato per *BufferLength* è un numero dispari, e  *\*InfoValuePtr* stato di un tipo di dati Unicode.|  
|HY096|Tipo di informazioni non compreso nell'intervallo|Il valore specificato per l'argomento *InfoType* non valido per la versione di ODBC supportati dal driver.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Campo facoltativo non implementato|Il valore specificato per l'argomento *InfoType* è un valore specifico del driver che non è supportato dal driver.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver che corrisponde alla *ConnectionHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Vengono visualizzati i tipi di informazioni attualmente definiti in "Tipi di informazioni," più avanti in questa sezione; è previsto che più definiti per sfruttare i vantaggi di origini dati diverse. Una gamma di tipi di informazioni è riservata da ODBC. gli sviluppatori di driver è necessario riservare i valori per l'uso di specifici del driver da Open Group. **SQLGetInfo** Nessuna conversione Unicode o *thunk* (vedere [appendice a: i codici di errore ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) del *riferimento per programmatori ODBC*) per definiti dal driver *tipi*. Per ulteriori informazioni, vedere [tipi di dati specifici del Driver, descrittore di tipi, tipi di informazioni, tipi di diagnostica e gli attributi](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Il formato delle informazioni restituite \* *InfoValuePtr* dipende il *InfoType* richiesto. **SQLGetInfo** restituirà informazioni in uno dei cinque diversi formati:  
  
-   Una stringa di caratteri con terminazione null  
  
-   Un valore SQLUSMALLINT  
  
-   Maschera di bit SQLUINTEGER  
  
-   Un valore SQLUINTEGER  
  
-   Un valore binario SQLUINTEGER  
  
 Il formato di ciascuno dei seguenti tipi di informazioni viene indicato nella descrizione del tipo. L'applicazione deve eseguire il cast di valore restituito in **InfoValuePtr* di conseguenza. Per un esempio di come un'applicazione può recuperare i dati da una maschera di bit SQLUINTEGER, vedere "Esempio di codice".  
  
 Un driver deve restituire un valore per ogni tipo di informazioni che è definito nelle tabelle seguenti. Se un tipo di informazioni non si applica a una origine dati o il driver, il driver restituisce uno dei valori elencati nella tabella seguente.  
  
 Stringa di caratteri ("Y" o "N")  
 "N"  
  
 Stringa di caratteri (non "Y" o "N")  
 Stringa vuota  
  
 SQLUSMALLINT  
 0  
  
 Maschera di bit SQLUINTEGER o valore binario SQLUINTEGER  
 G 0  
  
 Ad esempio, se un'origine dati non supporta le procedure, **SQLGetInfo** restituisce i valori elencati nella tabella seguente per i valori di *InfoType* correlate alle procedure.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Stringa vuota  
  
 **SQLGetInfo** restituisce SQLSTATE HY096 (valore dell'argomento non valido) per i valori di *InfoType* che rientrano nell'intervallo dei tipi di informazioni riservati per l'utilizzo da ODBC, ma non sono definiti dalla versione di ODBC supportati dal driver. Per determinare quale versione di ODBC è un driver conforme con, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_DRIVER_ODBC_VER. **SQLGetInfo** restituisce SQLSTATE HYC00 (funzionalità facoltativa non implementata) per i valori di *InfoType* che rientrano nell'intervallo dei tipi di informazioni riservati per l'uso di specifici del driver, ma non sono supportate dal driver.  
  
 Tutte le chiamate a **SQLGetInfo** richiedono una connessione aperta, tranne quando la *InfoType* è SQL_ODBC_VER, che restituisce la versione di gestione Driver.  
  
## <a name="information-types"></a>Tipi di informazioni  
 In questa sezione sono elencati i tipi di informazioni supportati da **SQLGetInfo**. Tipi di informazioni sono raggruppati in modo categorico ed elencati in ordine alfabetico. Tipi di informazioni che sono state aggiunte o rinominati per ODBC 3*x* sono inoltre elencati.  
  
## <a name="driver-information"></a>Informazioni sul driver  
 I valori seguenti del *InfoType* argomento restituiscono informazioni sul driver ODBC, ad esempio il numero di istruzioni attive, il nome dell'origine dati e il livello di conformità agli standard di interfaccia:  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_FILE_USAGE|  
|SQL_ASYNC_MODE|SQL_GETDATA_EXTENSIONS|  
|SQL_ASYNC_NOTIFICATION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_BATCH_ROW_COUNT|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_BATCH_SUPPORT|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_DATA_SOURCE_NAME|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_DRIVER_AWARE_POOLING_SUPPORTED|SQL_MAX_CONCURRENT_ACTIVITIES|  
|SQL_DRIVER_HDBC|SQL_MAX_DRIVER_CONNECTIONS|  
|SQL_DRIVER_HDESC|SQL_ODBC_INTERFACE_CONFORMANCE|  
|SQL_DRIVER_HENV|SQL_ODBC_STANDARD_CLI_CONFORMANCE|  
|SQL_DRIVER_HLIB|SQL_ODBC_VER|  
|SQL_DRIVER_HSTMT|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_DRIVER_NAME|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DRIVER_ODBC_VER|SQL_ROW_UPDATES|  
|SQL_DRIVER_VER|SQL_SEARCH_PATTERN_ESCAPE|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|SQL_SERVER_NAME|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_STATIC_CURSOR_ATTRIBUTES2|  
  
> [!NOTE]  
>  Quando si implementa **SQLGetInfo**, un driver può migliorare le prestazioni riducendo il numero di volte in cui vengono inviati o richieste dal server.  
  
## <a name="dbms-product-information"></a>Informazioni sui prodotti DBMS  
 I valori seguenti del *InfoType* argomento restituiscono informazioni sul prodotto DBMS, ad esempio il nome DBMS e la versione:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Informazioni sull'origine dati  
 I valori seguenti del *InfoType* argomento restituire le informazioni sull'origine dati, ad esempio delle caratteristiche del cursore e le funzionalità di transazione:  
  
|||  
|-|-|  
|SQL_ACCESSIBLE_PROCEDURES|SQL_MULT_RESULT_SETS|  
|SQL_ACCESSIBLE_TABLES|SQL_MULTIPLE_ACTIVE_TXN|  
|SQL_BOOKMARK_PERSISTENCE|SQL_NEED_LONG_DATA_LEN|  
|SQL_CATALOG_TERM|SQL_NULL_COLLATION|  
|SQL_COLLATION_SEQ|SQL_PROCEDURE_TERM|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_SCHEMA_TERM|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_SCROLL_OPTIONS|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_TABLE_TERM|  
|SQL_CURSOR_SENSITIVITY|SQL_TXN_CAPABLE|  
|SQL_DATA_SOURCE_READ_ONLY|SQL_TXN_ISOLATION_OPTION|  
|SQL_DEFAULT_TXN_ISOLATION|SQL_USER_NAME|  
|SQL_DESCRIBE_PARAMETER||  
  
## <a name="supported-sql"></a>SQL supportate  
 I valori seguenti del *InfoType* argomento restituiscono informazioni sulle istruzioni SQL supportati dall'origine dati. La sintassi SQL di ogni funzionalità descritto da questi tipi di informazioni è la sintassi SQL-92. Questi tipi di informazioni non descrivono reputano tutta la grammatica SQL-92. Al contrario, vengono descritte le parti della grammatica per i dati di origini in genere offrono diversi livelli di supporto. In particolare, vengono descritte la maggior parte delle istruzioni DDL in SQL-92.  
  
 Applicazioni devono determinare il livello generale di grammatica supportata dal tipo di informazioni SQL_SQL_CONFORMANCE e utilizzare gli altri tipi di informazioni per determinare le variazioni del livello di conformità standard indicati.  
  
|||  
|-|-|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DROP_TABLE|  
|SQL_ALTER_DOMAIN|SQL_DROP_TRANSLATION|  
|SQL_ALTER_SCHEMA|SQL_DROP_VIEW|  
|SQL_ALTER_TABLE|SQL_EXPRESSIONS_IN_ORDERBY|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_GROUP_BY|  
|SQL_CATALOG_LOCATION|SQL_IDENTIFIER_CASE|  
|SQL_CATALOG_NAME|SQL_IDENTIFIER_QUOTE_CHAR|  
|SQL_CATALOG_NAME_SEPARATOR|SQL_INDEX_KEYWORDS|  
|SQL_CATALOG_USAGE|SQL_INSERT_STATEMENT|  
|SQL_COLUMN_ALIAS|SQL_INTEGRITY|  
|SQL_CORRELATION_NAME|SQL_KEYWORDS|  
|SQL_CREATE_ASSERTION|SQL_LIKE_ESCAPE_CLAUSE|  
|SQL_CREATE_CHARACTER_SET|SQL_NON_NULLABLE_COLUMNS|  
|SQL_CREATE_COLLATION|SQL_SQL_CONFORMANCE|  
|SQL_CREATE_DOMAIN|SQL_OJ_CAPABILITIES|  
|SQL_CREATE_SCHEMA|SQL_ORDER_BY_COLUMNS_IN_SELECT|  
|SQL_CREATE_TABLE|SQL_OUTER_JOINS|  
|SQL_CREATE_TRANSLATION|SQL_PROCEDURES|  
|SQL_DDL_INDEX|SQL_QUOTED_IDENTIFIER_CASE|  
|SQL_DROP_ASSERTION|SQL_SCHEMA_USAGE|  
|SQL_DROP_CHARACTER_SET|SQL_SPECIAL_CHARACTERS|  
|SQL_DROP_COLLATION|SQL_SUBQUERIES|  
|SQL_DROP_DOMAIN|SQL_UNION|  
|SQL_DROP_SCHEMA||  
  
## <a name="sql-limits"></a>Limiti SQL  
 I valori seguenti del *InfoType* argomento restituiscono informazioni sui limiti applicati per gli identificatori e le clausole nelle istruzioni SQL, ad esempio la lunghezza massima di identificatori e il numero massimo di colonne in un elenco di selezione. Possono essere imposte limitazioni per il driver o l'origine dati.  
  
|||  
|-|-|  
|SQL_MAX_BINARY_LITERAL_LEN|SQL_MAX_IDENTIFIER_LEN|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAX_INDEX_SIZE|  
|SQL_MAX_CHAR_LITERAL_LEN|SQL_MAX_PROCEDURE_NAME_LEN|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAX_ROW_SIZE|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAX_ROW_SIZE_INCLUDES_LONG|  
|SQL_MAX_COLUMNS_IN_INDEX|SQL_MAX_SCHEMA_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAX_STATEMENT_LEN|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAX_TABLE_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAX_TABLES_IN_SELECT|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAX_USER_NAME_LEN|  
  
## <a name="scalar-function-information"></a>Informazioni sulle funzioni scalari  
 I valori seguenti del *InfoType* argomento restituiscono informazioni sulle funzioni scalari supportati da origine dati e il driver. Per ulteriori informazioni sulle funzioni scalari, vedere [appendice e: le funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Informazioni sulla conversione  
 I valori seguenti del *InfoType* argomento restituire un elenco dei tipi di dati SQL in cui l'origine dati è possibile convertire il tipo di dati SQL specificato con il **CONVERTIRE** funzione scalare:  
  
|||  
|-|-|  
|SQL_CONVERT_BIGINT|SQL_CONVERT_LONGVARBINARY|  
|SQL_CONVERT_BINARY|SQL_CONVERT_LONGVARCHAR|  
|SQL_CONVERT_BIT|SQL_CONVERT_NUMERIC|  
|SQL_CONVERT_CHAR|SQL_CONVERT_REAL|  
|SQL_CONVERT_DATE|SQL_CONVERT_SMALLINT|  
|SQL_CONVERT_DECIMAL|SQL_CONVERT_TIME|  
|SQL_CONVERT_DOUBLE|SQL_CONVERT_TIMESTAMP|  
|SQL_CONVERT_FLOAT|SQL_CONVERT_TINYINT|  
|SQL_CONVERT_INTEGER|SQL_CONVERT_VARBINARY|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_CONVERT_VARCHAR|  
|SQL_CONVERT_INTERVAL_DAY_TIME||  
  
## <a name="information-types-added-for-odbc-3x"></a>Tipi di informazioni aggiunte per ODBC 3. x  
 I valori seguenti del *InfoType* argomento sono state aggiunte per ODBC 3*x*:  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_DRIVER_AWARE_POOLING_SUPPORTED|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DRIVER_HDESC|  
|SQL_ALTER_DOMAIN|SQL_DROP_ASSERTION|  
|SQL_ALTER_SCHEMA|SQL_DROP_CHARACTER_SET|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_DROP_COLLATION|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_DROP_DOMAIN|  
|SQL_ASYNC_MODE|SQL_DROP_SCHEMA|  
|SQL_ASYNC_NOTIFICATION|SQL_DROP_TABLE|  
|SQL_BATCH_ROW_COUNT|SQL_DROP_TRANSLATION|  
|SQL_BATCH_SUPPORT|SQL_DROP_VIEW|  
|SQL_CATALOG_NAME|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|  
|SQL_COLLATION_SEQ|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|  
|SQL_CONVERT_INTERVAL_DAY_TIME|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_ASSERTION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_CREATE_CHARACTER_SET|SQL_INSERT_STATEMENT|  
|SQL_CREATE_COLLATION|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_CREATE_DOMAIN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_SCHEMA|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_CREATE_TABLE|SQL_MAX_IDENTIFIER_LEN|  
|SQL_CREATE_TRANSLATION|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_CURSOR_SENSITIVITY|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DDL_INDEX|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_DESCRIBE_PARAMETER|SQL_STATIC_CURSOR_ATTRIBUTES2|  
|SQL_DM_VER|SQL_XOPEN_CLI_YEAR|  
  
## <a name="information-types-renamed-for-odbc-3x"></a>Tipi di informazioni rinominati per ODBC 3. x  
 I valori seguenti del *InfoType* argomento sono stati rinominati per ODBC 3*x*.  
  
 SQL_ACTIVE_CONNECTIONS  
 SQL_MAX_DRIVER_CONNECTIONS  
  
 SQL_ACTIVE_STATEMENTS  
 SQL_MAX_CONCURRENT_ACTIVITIES  
  
 SQL_MAX_OWNER_NAME_LEN  
 SQL_MAX_SCHEMA_NAME_LEN  
  
 SQL_MAX_QUALIFIER_NAME_LEN  
 SQL_MAX_CATALOG_NAME_LEN  
  
 SQL_ODBC_SQL_OPT_IEF  
 SQL_INTEGRITY  
  
 SQL_OWNER_TERM  
 SQL_SCHEMA_TERM  
  
 SQL_OWNER_USAGE  
 SQL_SCHEMA_USAGE  
  
 SQL_QUALIFIER_LOCATION  
 SQL_CATALOG_LOCATION  
  
 SQL_QUALIFIER_NAME_SEPARATOR  
 SQL_CATALOG_NAME_SEPARATOR  
  
 SQL_QUALIFIER_TERM  
 SQL_CATALOG_TERM  
  
 SQL_QUALIFIER_USAGE  
 SQL_CATALOG_USAGE  
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Tipi di informazioni deprecati in ODBC 3. x  
 I valori seguenti del *InfoType* argomento sono state deprecate in ODBC 3*x*. ODBC 3*x* driver necessario continuare a supportare questi tipi di informazioni per la compatibilità con ODBC 2*x* applicazioni. (Per ulteriori informazioni su questi tipi, vedere [supporto SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Descrizioni dei tipi di informazioni  
 Nella tabella seguente sono elencati in ordine alfabetico in ogni tipo di informazioni, la versione di ODBC in cui è stato introdotto e la relativa descrizione.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Una stringa di caratteri: "Y" se l'utente può eseguire tutte le procedure restituite dal **SQLProcedures**; "N" se vi sono procedure restituito che l'utente non è possibile eseguire.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Una stringa di caratteri: "Y" se è garantito che l'utente **selezionare** privilegi per tutte le tabelle restituite da **SQLTables**; "N" se vi sono tabelle restituito che l'utente non può accedere.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di ambienti in grado di supportare il driver. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di supporto per le funzioni di aggregazione:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **ALTER dominio** istruzione, come definito in SQL-92, supportato dall'origine dati. Un driver conforme a livello di SQL-92 completo restituirà sempre tutte le maschere di bit. Il valore restituito pari a "0" indica che il **ALTER dominio** istruzione non è supportata.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = aggiunta è supportato un vincolo di dominio (livello completo)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter dominio > \<clausola default di set domain > è supportato (livello completo)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<clausola del nome della definizione di vincolo > è supportato per la denominazione dei vincoli di dominio (livello intermedio)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<clausola di vincolo dominio drop > è supportato (livello completo)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter dominio > \<clausola default di rilascio domain > è supportato (livello completo)  
  
 I bit seguenti specificano supportati \<attributi vincolo > Se \<aggiungere vincoli di dominio > è supportato (è impostato il bit SQL_AD_ADD_DOMAIN_CONSTRAINT):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (livello completo) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (livello completo) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (livello completo) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (livello completo)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **ALTER TABLE** supportati dall'origine dati.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<aggiungere colonna > clausola è supportata, con funzionalità per specificare regole di confronto colonna (livello completo) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<aggiungere colonna > clausola è supportata, con possibilità di specificare i valori predefiniti delle colonne (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<aggiungere colonna > è supportato (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<aggiungere colonna > clausola è supportata, con funzionalità per specificare i vincoli di colonna (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<Aggiungi vincolo di tabella > clausola è supportata (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<definizione di vincolo nome > è supportato per la denominazione dei vincoli di colonna e tabella (livello intermedio) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<eliminare la colonna > è supportato in serie (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<modificare la colonna > \<clausola default di rilascio colonna > è supportato (livello intermedio) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<eliminare la colonna > è supportato RESTRICT (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<eliminare la colonna > è supportato RESTRICT (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<modificare la colonna > \<clausola default di set di colonna > è supportato (livello intermedio) (ODBC 3.0)  
  
 Il supporto di specificare i bit seguenti \<attributi vincolo > Se è consentito specificare vincoli di colonna o una tabella (è impostato il bit SQL_AT_ADD_CONSTRAINT):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (livello completo) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (livello completo) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (livello completo) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (livello completo) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 Un valore SQLUINTEGER che indica se il driver può operare in modo asincrono nell'handle di connessione.  
  
 SQL_ASYNC_DBC_CAPABLE = il driver può eseguire funzioni di connessione in modo asincrono.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = il driver non può eseguire funzioni di connessione in modo asincrono.  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 Un valore SQLUINTEGER che indica il livello di supporto asincrono nel driver:  
  
 SQL_AM_CONNECTION = connessione è supportata l'esecuzione asincrona di livello. Tutti gli handle di istruzione associati all'handle di connessione sono in modalità asincrona o tutti sono in modalità sincrona. Un handle di istruzione su una connessione non può essere in modalità asincrona, mentre un altro handle di istruzione nella stessa connessione è in modalità sincrona e viceversa.  
  
 SQL_AM_STATEMENT = è supportata l'esecuzione asincrona di livello di istruzione. Alcuni handle di istruzione associati a un handle di connessione possono essere in modalità asincrona, mentre altri handle di istruzione nella stessa connessione sono in modalità sincrona.  
  
 SQL_AM_NONE = asincrono in modalità non è supportata.  
  
 SQL_ASYNC_NOTIFICATION  
 Un valore SQLUINTEGER che indica se il driver supporta la notifica asincrona:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** notifica esecuzione asincrona è supportata dal driver.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** notifica esecuzione asincrona non è supportata dal driver.  
  
 Esistono due categorie di operazioni asincrone ODBC: operazioni asincrone di livello di istruzione e le operazioni asincrone livello di connessione.  Se un driver restituisce SQL_ASYNC_NOTIFICATION_CAPABLE, deve supportare la notifica per tutte le API che possono essere eseguite in modo asincrono.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Maschera di bit SQLUINTEGER che enumera il comportamento del driver rispetto alla disponibilità della riga di conteggi. Le maschere di bit seguenti vengono utilizzate insieme al tipo di informazioni:  
  
 SQL_BRC_ROLLED_UP = i conteggi delle righe delle istruzioni INSERT, DELETE o UPDATE consecutive vengono raggruppate in una sola. Se questo bit non è impostato, i conteggi delle righe sono disponibili per ogni istruzione.  
  
 SQL_BRC_PROCEDURES = i conteggi delle righe, se presente, sono disponibili quando un batch viene eseguito in una stored procedure. Se sono disponibili i conteggi delle righe, è possibile eseguire il rollback verso l'alto o singolarmente disponibile, a seconda di bit SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = i conteggi delle righe, se presente, sono disponibili quando un batch viene eseguito chiamando direttamente **SQLExecute** o **SQLExecDirect**. Se sono disponibili i conteggi delle righe, è possibile eseguire il rollback verso l'alto o singolarmente disponibile, a seconda di bit SQL_BRC_ROLLED_UP.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di supporto del driver per i batch. Le maschere di bit seguenti vengono utilizzati per determinare il livello è supportato:  
  
 SQL_BS_SELECT_EXPLICIT = il driver supporta esplicita batch possono avere set di risultati la generazione di istruzioni.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = driver supporta esplicita batch contenenti istruzioni di generazione di conteggio delle righe.  
  
 SQL_BS_SELECT_PROC = il driver supporta esplicita procedure che possono avere set di risultati la generazione di istruzioni.  
  
 SQL_BS_ROW_COUNT_PROC = i driver supporta esplicita procedure contenenti le istruzioni di generazione di conteggio delle righe.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle operazioni tramite la quale la persistenza dei segnalibri.  
  
 Le maschere di bit seguenti vengono utilizzati con il flag per determinare tramite il quale la persistenza dei segnalibri opzioni:  
  
 SQL_BP_CLOSE = i segnalibri sono validi dopo un'applicazione chiama **SQLFreeStmt** con l'opzione SQL_CLOSE, o **SQLCloseCursor** per chiudere il cursore associato a un'istruzione.  
  
 SQL_BP_DELETE = il segnalibro per una riga è valida dopo che la riga è stata eliminata.  
  
 SQL_BP_DROP = i segnalibri sono validi dopo un'applicazione chiama **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_STMT per un'istruzione drop.  
  
 SQL_BP_TRANSACTION = i segnalibri sono validi dopo un'applicazione esegue il commit o il rollback di una transazione.  
  
 SQL_BP_UPDATE = il segnalibro per una riga è valida dopo qualsiasi colonna in tale riga è stata aggiornata, incluse le colonne chiave.  
  
 SQL_BP_OTHER_HSTMT = un segnalibro associato a una sola istruzione può essere utilizzata con un'altra istruzione. A meno che non viene specificato SQL_BP_CLOSE o SQL_BP_DROP, il cursore nella prima istruzione deve essere aperto.  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 Un valore SQLUSMALLINT che indica la posizione del catalogo in un nome di tabella qualificati:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Ad esempio, un driver Xbase restituisce SQL_CL_START perché il nome di directory (catalogo) all'inizio del nome della tabella, come \EMPDATA\EMP. DBF. Un driver del Server ORACLE restituisce SQL_CL_END perché il catalogo è alla fine del nome della tabella, come in ADMIN.EMP@EMPDATA.  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre SQL_CL_START. Se i cataloghi non sono supportati dall'origine dati, viene restituito un valore pari a 0. Per determinare se sono supportati i cataloghi, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_CATALOG_NAME.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME (ODBC 3.0)  
 Una stringa di caratteri: "Y" se il server supporta i nomi di catalogo, o "N", in caso contrario.  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre "Y".  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 Una stringa di caratteri: uno o più caratteri che definisce l'origine dati come separatore tra un nome di catalogo e l'elemento di nome completo che precede o che segue.  
  
 Se i cataloghi non sono supportati dall'origine dati, viene restituita una stringa vuota. Per determinare se sono supportati i cataloghi, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_CATALOG_NAME. Restituisce sempre un driver di livello conforme allo standard SQL-92 completo ".".  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 Una stringa di caratteri con il nome del fornitore di origine dati per un catalogo. ad esempio, "database" o "directory". Questa stringa può essere in caso di superiore, inferiore o misto.  
  
 Se i cataloghi non sono supportati dall'origine dati, viene restituita una stringa vuota. Per determinare se sono supportati i cataloghi, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_CATALOG_NAME. Un driver di livello conforme allo standard SQL-92 completo restituirà sempre "catalogo".  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 Maschera di bit SQLUINTEGER enumerazione le istruzioni in cui è possibile utilizzare i cataloghi.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare dove si possono utilizzare cataloghi:  
  
 SQL_CU_DML_STATEMENTS = i cataloghi sono supportati in tutte le istruzioni Data Manipulation Language: **selezionare**, **inserire**, **aggiornamento**, **DELETE**e, se supportato **selezionare per aggiornare** e posizionato aggiornamento e istruzioni delete.  
  
 SQL_CU_PROCEDURE_INVOCATION = i cataloghi sono supportati nell'istruzione di chiamata di procedura ODBC.  
  
 SQL_CU_TABLE_DEFINITION = i cataloghi sono supportati in tutte le istruzioni di definizione di tabella: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE** , e **DROP VIEW**.  
  
 SQL_CU_INDEX_DEFINITION = i cataloghi sono supportati in tutte le istruzioni di definizione di indice: **CREATE INDEX** e **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = i cataloghi sono supportati in tutte le istruzioni di definizione dei privilegi: **GRANT** e **revocare**.  
  
 Se i cataloghi non sono supportati dall'origine dati, viene restituito un valore pari a 0. Per determinare se sono supportati i cataloghi, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_CATALOG_NAME. Un driver di livello conforme allo standard SQL-92 completo restituirà sempre una maschera di bit con tutti questi set di bit.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 Il nome della sequenza di regole di confronto. Si tratta di una stringa di caratteri che indica il nome delle regole di confronto predefinito per il carattere predefinito impostato per il server (ad esempio, ' ISO 8859-1' o EBCDIC). Se questo è sconosciuto, verrà restituita una stringa vuota. Un driver di livello conforme allo standard SQL-92 completo restituirà sempre una stringa non vuota.  
  
 SQL_COLUMN_ALIAS (ODBC 2.0)  
 Una stringa di caratteri: "Y" se l'origine dati supporta gli alias di colonna; in caso contrario, "N".  
  
 Un alias di colonna è un nome alternativo che può essere specificato per una colonna nell'elenco di selezione utilizzando la clausola AS. Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre "Y".  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1.0)  
 Un valore SQLUSMALLINT che indica il modo in cui l'origine dati gestisce la concatenazione Null con valori di colonne di tipo di dati di caratteri con colonne di tipo di dati carattere con valori non NULL:  
  
 SQL_CB_NULL = risultato viene valutato come NULL.  
  
 SQL_CB_NON_NULL = risultato è la concatenazione delle colonne con valori non NULL.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_ DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Maschera di bit SQLUINTEGER. La maschera di bit indica le conversioni supportate dall'origine dati con il **CONVERTIRE** funzione scalare per i dati del tipo denominato nel *InfoType*. Se la maschera di bit uguale a zero, l'origine dati non supporta tutte le conversioni da dati del tipo denominato, inclusa la conversione nello stesso tipo di dati.  
  
 Per determinare se un'origine dati supporta la conversione dei dati SQL_INTEGER al tipo di dati SQL_BIGINT, ad esempio, un'applicazione chiama **SQLGetInfo** con il *InfoType* di SQL_CONVERT_INTEGER. L'applicazione esegue un **AND** operazione con la maschera di bit restituita e SQL_CVT_BIGINT. Se il valore risultante è diverso da zero, la conversione è supportata.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali conversioni sono supportati:  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL SQL_CVT_ SQL_CVT_TIME (ODBC 1.0) DI (ODBC 1.0) SQL_CVT_SMALLINT _CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) TIMESTAMP (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni di conversione scalare supportate dal driver origine dati associata.  
  
 La maschera di bit seguente viene utilizzato per determinare le funzioni di conversione supportate:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 Valore SQLUSMALLINT che indica se i nomi di correlazione di tabella sono supportati:  
  
 SQL_CN_NONE = non sono supportati nomi di correlazione.  
  
 SQL_CN_DIFFERENT = correlazione nomi sono supportati ma devono essere diverso dai nomi delle tabelle che rappresentano.  
  
 SQL_CN_ANY = correlazione nomi sono supportati e possono essere qualsiasi nome definito dall'utente valido.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **creare ASSERZIONE** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_CA_CREATE_ASSERTION  
  
 I bit seguenti specificano l'attributo di vincolo supportato se è supportata la possibilità di specificare in modo esplicito gli attributi di vincolo (vedere i tipi di informazioni SQL_ALTER_TABLE e SQL_CREATE_TABLE):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre tutte queste opzioni come supportati. Il valore restituito pari a "0" indica che il **creare ASSERZIONE** istruzione non è supportata.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **creare SET di caratteri** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre tutte queste opzioni come supportati. Il valore restituito pari a "0" indica che il **creare SET di caratteri** istruzione non è supportata.  
  
 SQL_CREATE_COLLATION (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **creare regole di confronto** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 La maschera di bit seguente viene utilizzato per determinare le clausole sono supportate:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre questa opzione supportata. Il valore restituito pari a "0" indica che il **creare regole di confronto** istruzione non è supportata.  
  
 SQL_CREATE_DOMAIN (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **crea dominio** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_CDO_CREATE_DOMAIN = dominio di creare l'istruzione è supportata (livello intermedio).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<definizione di vincolo nome > è supportato per la denominazione dei vincoli di dominio (livello intermedio).  
  
 I bit seguenti specificano la possibilità di creare i vincoli di colonna: SQL_CDO_DEFAULT = è consentito specificare vincoli di dominio (livello intermedio) SQL_CDO_CONSTRAINT = è consentito specificare valori predefiniti di dominio (livello intermedio) SQL_CDO_COLLATION = È consentito specificare le regole di confronto di dominio (livello completo)  
  
 I bit seguenti specificano gli attributi di vincolo supportato se è consentito specificare vincoli di dominio (SQL_CDO_DEFAULT è impostato):  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (livello completo) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (livello completo) SQL_CDO_CONSTRAINT_DEFERRABLE (livello completo) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (livello completo)  
  
 Il valore restituito pari a "0" indica che il **crea dominio** istruzione non è supportata.  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **CREATE SCHEMA** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Un driver conforme allo standard livello intermedio di SQL-92 restituirà sempre le opzioni SQL_CS_CREATE_SCHEMA e SQL_CS_AUTHORIZATION supportato. Questi deve essere supportati anche a livello di voce di SQL-92, ma non necessariamente come istruzioni SQL. Un driver di livello conforme allo standard SQL-92 completo restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **CREATE TABLE** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_CT_CREATE_TABLE = tabella di creare l'istruzione è supportata. (Entry level)  
  
 SQL_CT_TABLE_CONSTRAINT = è consentito specificare vincoli di tabella (livello FIPS transizione)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = il \<definizione nome vincolo > clausola è supportata per la denominazione dei vincoli di colonna e tabella (livello intermedio)  
  
 I bit seguenti specificano la possibilità di creare tabelle temporanee:  
  
 SQL_CT_COMMIT_PRESERVE = eliminato righe vengono mantenute in caso di commit. (Livello completo) SQL_CT_COMMIT_DELETE = eliminate le righe vengono eliminate al momento del commit. (Livello completo) SQL_CT_GLOBAL_TEMPORARY = globale è possibile creare tabelle temporanee. (Livello completo) SQL_CT_LOCAL_TEMPORARY = locale è possibile creare tabelle temporanee. (Livello completo)  
  
 I bit seguenti specificano la possibilità di creare vincoli di colonna:  
  
 SQL_CT_COLUMN_CONSTRAINT = specificano i vincoli di colonna è supportata (livello FIPS transizione) SQL_CT_COLUMN_DEFAULT = è consentito specificare valori predefiniti delle colonne (livello FIPS transizione) SQL_CT_COLUMN_COLLATION = specificando regole di confronto colonna è supportata (livello completo)  
  
 I bit seguenti specificano gli attributi di vincolo supportato se è consentito specificare vincoli di colonna o tabella:  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (livello completo) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (livello completo) SQL_CT_CONSTRAINT_DEFERRABLE (livello completo) SQL_CT_CONSTRAINT_NON_DEFERRABLE (livello completo)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **creare traduzione** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 La maschera di bit seguente viene utilizzato per determinare le clausole sono supportate:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre queste opzioni come supportati. Il valore restituito pari a "0" indica che il **creare traduzione** istruzione non è supportata.  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **CREATE VIEW** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Il valore restituito pari a "0" indica che il **CREATE VIEW** istruzione non è supportata.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre le opzioni SQL_CV_CREATE_VIEW e SQL_CV_CHECK_OPTION supportato.  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 Un valore SQLUSMALLINT che indica come un **COMMIT** operazione interessa i cursori e le istruzioni preparate nell'origine dati (il comportamento dell'origine dati quando si esegue il commit di una transazione).  
  
 Il valore di questo attributo riflette lo stato corrente dell'impostazione Avanti: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = cursori Chiudi ed eliminare le istruzioni preparate. Per utilizzare il cursore nuovamente, l'applicazione deve reprepare e rieseguire l'istruzione.  
  
 SQL_CB_CLOSE = chiuso cursori. Per le istruzioni preparate, l'applicazione può chiamare **SQLExecute** nell'istruzione senza chiamare **SQLPrepare** nuovamente. Il valore predefinito per il driver ODBC di SQL è SQL_CB_CLOSE. Ciò significa che il driver ODBC SQL chiuderà i cursori quando si esegue il commit di una transazione.  
  
 SQL_CB_PRESERVE = Preserve cursori nella stessa posizione come prima il **COMMIT** operazione. L'applicazione può continuare a recuperare i dati oppure è possibile chiudere il cursore ed eseguire nuovamente l'istruzione senza preparazione nuovamente.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 Un valore SQLUSMALLINT che indica come un **ROLLBACK** operazione interessa i cursori e le istruzioni preparate nell'origine dati:  
  
 SQL_CB_DELETE = cursori Chiudi ed eliminare le istruzioni preparate. Per utilizzare il cursore nuovamente, l'applicazione deve reprepare e rieseguire l'istruzione.  
  
 SQL_CB_CLOSE = chiuso cursori. Per le istruzioni preparate, l'applicazione può chiamare **SQLExecute** nell'istruzione senza chiamare **SQLPrepare** nuovamente.  
  
 SQL_CB_PRESERVE = Preserve cursori nella stessa posizione come prima il **ROLLBACK** operazione. L'applicazione può continuare a recuperare i dati oppure è possibile chiudere il cursore e rieseguire l'istruzione senza repreparing.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 Un valore SQLUINTEGER che indica il supporto per la sensibilità del cursore:  
  
 SQL_INSENSITIVE = tutti i cursori la presentazione di handle di istruzione il set di risultati senza che riflette le modifiche apportate a esso da qualsiasi altro cursore all'interno della stessa transazione.  
  
 SQL_UNSPECIFIED = non viene specificato se i cursori dell'handle di istruzione rendere visibili le modifiche apportate a un gruppo di risultati da un altro cursore all'interno della stessa transazione. I cursori dell'handle di istruzione potrebbero rendere visibili nessuno, alcuni o tutti tali modifiche.  
  
 SQL_SENSITIVE = cursori sono sensibili alle modifiche apportate da altri cursori all'interno della stessa transazione.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre l'opzione SQL_UNSPECIFIED supportato.  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre l'opzione SQL_INSENSITIVE supportato.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1.0)  
 Una stringa di caratteri con il nome dell'origine dati che è stata utilizzata durante la connessione. Se l'applicazione ha chiamato **SQLConnect**, questo è il valore del *szDSN* argomento. Se l'applicazione ha chiamato **SQLDriverConnect** o **SQLBrowseConnect**, questo è il valore della parola chiave DSN nella stringa di connessione passata al driver. Se la stringa di connessione non contiene il **DSN** (parola chiave) (ad esempio quando questo contiene il **DRIVER** parola chiave), si tratta di una stringa vuota.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1.0)  
 Una stringa di caratteri. "Y" se l'origine dati è impostato su modalità READ ONLY, "N", se è in caso contrario.  
  
 Questa caratteristica si riferisce solo all'origine dati stessa. non è una caratteristica del driver che consente l'accesso all'origine dati. Un driver che è in lettura/scrittura può essere utilizzato con un'origine dati che è di sola lettura. Se un driver è di sola lettura, tutte le relative origini dati deve essere di sola lettura e deve restituire SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME (ODBC 1.0)  
 Una stringa di caratteri con il nome del database corrente in uso, se l'origine dati definisce un oggetto denominato "database".  
  
> [!NOTE]  
>  In ODBC 3*x*, il valore restituito per questo *InfoType* possono essere restituiti chiamando **SQLGetConnectAttr** con un *attributo* argomento di SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di valori letterali datetime di SQL-92 supportati dall'origine dati. Si noti che questi sono i valori letterali di data/ora elencati nella specifica di SQL-92 e sono separati dalle clausole di escape valore letterale datetime definite da ODBC. Per ulteriori informazioni sulle clausole di escape di ODBC datetime letterale, vedere [Date, Time e Timestamp letterali](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un driver di livello – conforme a FIPS transizione restituirà sempre il valore "1" nella maschera di bit per bit nell'elenco seguente. Un valore pari a "0" indica che non sono supportati valori letterali datetime di SQL-92.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali valori letterali sono supportati:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_ SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1.0)  
 Una stringa di caratteri con il nome del prodotto DBMS a cui accede il driver.  
  
 SQL_DBMS_VER (ODBC 1.0)  
 Una stringa di caratteri che indica la versione del prodotto DBMS a cui accede il driver. La versione è nel formato # #. # #. # # #, dove le prime due cifre indicano la versione principale, le due cifre successive alla versione secondaria, mentre le ultime quattro cifre sono la versione di rilascio. Il driver deve eseguire il rendering la versione del prodotto DBMS in questo modulo tuttavia anche possibile aggiungere la versione DBMS specifici del prodotto. Ad esempio, "04.01.0000 Rdb 4.1".  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 Valore SQLUINTEGER che indica il supporto per la creazione e l'eliminazione di indici:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1.0)  
 Un valore SQLUINTEGER che indica che il livello di isolamento predefinito supportato dal driver o l'origine dati, oppure zero se l'origine dati non supporta le transazioni. Per definire i livelli di isolamento delle transazioni, vengono utilizzati i termini seguenti:  
  
 **Lettura dirty** 1 transazione modifica una riga. La transazione 2 legge la riga modificata prima che la transazione 1 viene eseguito il commit della modifica. Se 1 rollback della transazione di modifica, la transazione 2 verrà letta una riga che viene considerata non previsti.  
  
 **Lettura non ripetibile** 1 transazione legge una riga. La transazione 2 aggiorna o elimina tale riga e viene eseguito il commit di questa modifica. Se la transazione 1 tenta di leggere nuovamente la riga, verrà ricevere i valori di riga diversi oppure individuare la riga eliminata.  
  
 **Righe fantasma** 1 transazione legge un set di righe che soddisfa alcuni criteri di ricerca. La transazione 2 genera una o più righe (tramite gli inserimenti o aggiornamenti) che corrispondono ai criteri di ricerca. Se la transazione 1 reexecutes l'istruzione che legge le righe, riceve un set diverso di righe.  
  
 Se l'origine dati supporta le transazioni, il driver restituisce uno delle maschere di bit seguenti:  
  
 SQL_TXN_READ_UNCOMMITTED = Dirty righe fantasma, letture non ripetibili e letture è possibili.  
  
 SQL_TXN_READ_COMMITTED = Dirty letture non sono possibili. Righe fantasma e letture non ripetibili è possibili.  
  
 SQL_TXN_REPEATABLE_READ = Dirty letture e letture non ripetibili non sono possibili. Righe fantasma è possibili.  
  
 SQL_TXN_SERIALIZABLE = le transazioni sono serializzabili. Le transazioni serializzabili non consentono le letture dirty, letture non ripetibili o righe fantasma.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 Una stringa di caratteri: "Y", se i parametri possono essere descritti; "N", se non.  
  
 Un driver di livello conforme allo standard SQL-92 completa in genere restituisce "Y" perché supporterà il **INPUT DESCRIVONO** istruzione. Poiché non si specifica direttamente il supporto SQL sottostante, tuttavia, che descrive i parametri potrebbero non essere supportati, anche in un driver di livello conforme allo standard SQL-92 completo.  
  
 SQL_DM_VER (ODBC 3.0)  
 Una stringa di caratteri con la versione di gestione Driver. La versione è nel formato # #. # #. # # #. # # #, dove:  
  
 Il primo set di due cifre è la versione ODBC principale, come determinato da SQL_SPEC_MAJOR la costante.  
  
 Il secondo set di due cifre è la versione ODBC secondaria, come determinato da SQL_SPEC_MINOR la costante.  
  
 Il terzo set di quattro cifre è il numero di build principale di gestione Driver.  
  
 L'ultimo set di quattro cifre è il numero di build secondaria del Driver Manager.  
  
 La versione di gestione Driver di Windows 7 è 03.80. La versione di gestione Driver di Windows 8 è 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 Un valore SQLUINTEGER che indica se il driver supporta il pool compatibile con il driver. (Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE indica che il driver può supportare meccanismo del pool di connessioni compatibile con il driver.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE indica che il driver non supporta il meccanismo del pool di connessioni compatibile con il driver.  
  
 Un driver non è necessario implementare SQL_DRIVER_AWARE_POOLING_SUPPORTED gestione Driver non verrà applicata al valore restituito del driver.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 Un handle di ambiente o handle di connessione, determinata dall'argomento valore SQLULEN, il driver *InfoType*.  
  
 Questi tipi di informazioni vengono implementati da Gestione Driver da solo.  
  
 SQL_DRIVER_HDESC (ODBC 3.0)  
 Valore di un SQLULEN, determinato dall'handle di descrittore del Driver Manager, che deve essere passata in input nell'handle di descrittore del driver \* *InfoValuePtr* dall'applicazione. In questo caso, *InfoValuePtr* entrambi un argomento di input e output. L'handle di descrittore di input passato \* *InfoValuePtr* devono avere stato implicitamente o esplicitamente allocati il *ConnectionHandle*.  
  
 L'applicazione è necessario effettuare una copia del descrittore di Driver Manager di gestire prima di chiamare **SQLGetInfo** con questo tipo di informazioni, per assicurarsi che l'handle non viene sovrascritto nell'output.  
  
 Questo tipo viene implementato da Gestione Driver da solo.  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 Un valore, SQLULEN il *hinst* dalla libreria carico restituite a gestione Driver quando caricato la DLL del driver in un sistema operativo Microsoft Windows o l'equivalente in un altro sistema operativo. L'handle è valido solo per l'handle di connessione specificato nella chiamata a **SQLGetInfo**.  
  
 Questo tipo viene implementato da Gestione Driver da solo.  
  
 SQL_DRIVER_HSTMT (ODBC 1.0)  
 Valore di un SQLULEN, determinato dall'handle di istruzione di gestione Driver, deve essere passato in input nell'handle di istruzione del driver \* *InfoValuePtr* dall'applicazione. In questo caso, *InfoValuePtr* è di input e un argomento di output. L'handle di istruzione di input passato \* *InfoValuePtr* necessario aver assegnato per l'argomento *ConnectionHandle*.  
  
 L'applicazione è necessario effettuare una copia dell'istruzione di Driver Manager di gestire prima di chiamare **SQLGetInfo** con questo tipo di informazioni, per garantire che l'handle non viene sovrascritto nell'output.  
  
 Questo tipo viene implementato da Gestione Driver da solo.  
  
 SQL_DRIVER_NAME ODBC (1.0)  
 Una stringa di caratteri con il nome del file del driver utilizzato per accedere all'origine dati.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2.0)  
 Una stringa di caratteri con la versione di ODBC supportate dal driver. La versione è nel formato # #. # #, dove le prime due cifre indicano la versione principale e le due cifre successive sono la versione secondaria. SQL_SPEC_MAJOR e SQL_SPEC_MINOR definiscono i numeri di versione principale e secondaria. Per la versione di ODBC descritto in questo documento, si tratta di 3 e 0 e il driver deve restituire "03.00".  
  
 Gestione Driver ODBC non modificherà il valore restituito di SQLGetInfo(SQL_DRIVER_ODBC_VER) per mantenere la compatibilità con le versioni precedenti per le applicazioni esistenti. Il driver specifica quale valore verrà restituito. Tuttavia, un driver che supporta l'estendibilità del tipo di dati C deve restituire 3.8 (o versione successiva) quando un'applicazione chiama **SQLSetEnvAttr** su cui impostare SQL_ATTR_ODBC_VERSION 3.8. Per ulteriori informazioni, vedere [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 Una stringa di caratteri con la versione del driver e, facoltativamente, una descrizione del driver. Come minimo, la versione è nel formato # #. # #. # # #, dove le prime due cifre indicano la versione principale, le due cifre successive alla versione secondaria, mentre le ultime quattro cifre sono la versione di rilascio.  
  
 SQL_DROP_ASSERTION (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **DROP ASSERZIONE** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 La maschera di bit seguente viene utilizzato per determinare le clausole sono supportate:  
  
 SQL_DA_DROP_ASSERTION  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre questa opzione supportata.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **eliminare SET di caratteri** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 La maschera di bit seguente viene utilizzato per determinare le clausole sono supportate:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre questa opzione supportata.  
  
 SQL_DROP_COLLATION (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **eliminare le regole di confronto** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 La maschera di bit seguente viene utilizzato per determinare le clausole sono supportate:  
  
 SQL_DC_DROP_COLLATION  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre questa opzione supportata.  
  
 SQL_DROP_DOMAIN (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **dominio DROP** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Un driver conforme allo standard livello intermedio di SQL-92 restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **DROP SCHEMA** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Un driver conforme allo standard livello intermedio di SQL-92 restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_DROP_TABLE (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **DROP TABLE** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Un driver di livello – conforme a FIPS transizione restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_DROP_TRANSLATION (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **DROP traduzione** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 La maschera di bit seguente viene utilizzato per determinare le clausole sono supportate:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre questa opzione supportata.  
  
 SQL_DROP_VIEW (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **DROP VIEW** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Un driver di livello – conforme a FIPS transizione restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore dinamico sono supportati dal driver. La maschera di bit contiene il primo subset di attributi. per il subset di secondo, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA1_NEXT = A *FetchOrientation* argomento di SQL_FETCH_NEXT è supportato in una chiamata a **SQLFetchScroll** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* gli argomenti di SQL_FETCH_FIRST, SQL_FETCH_LAST e SQL_FETCH_ABSOLUTE sono supportati in una chiamata a **SQLFetchScroll** quando il cursore si trova un cursore dinamico. (Il set di righe che verranno recuperati è indipendente dalla posizione corrente del cursore).  
  
 SQL_CA1_RELATIVE = *FetchOrientation* gli argomenti di SQL_FETCH_PRIOR e SQL_FETCH_RELATIVE sono supportati in una chiamata a **SQLFetchScroll** quando il cursore si trova un cursore dinamico. (Il set di righe che verranno recuperati varia a seconda posizione corrente del cursore. Si noti che questo sia separato dalle SQL_FETCH_NEXT quanto un cursore forward-only, è supportato solo SQL_FETCH_NEXT.)  
  
 SQL_CA1_BOOKMARK = A *FetchOrientation* argomento impostato su sql_fetch_bookmark è supportato in una chiamata a **SQLFetchScroll** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_LOCK_EXCLUSIVE = A *LockType* argomento di SQL_LOCK_EXCLUSIVE è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_LOCK_NO_CHANGE = A *LockType* argomento di SQL_LOCK_NO_CHANGE è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_LOCK_UNLOCK = A *LockType* argomento di SQL_LOCK_UNLOCK è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_POS_POSITION = un *operazione* argomento di SQL_POSITION è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_POS_UPDATE = un *operazione* argomento di SQL_UPDATE è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_POS_DELETE = un *operazione* argomento di SQL_DELETE è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_POS_REFRESH = un *operazione* argomento di SQL_REFRESH è supportato in una chiamata a **SQLSetPos** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_POSITIONED_UPDATE = un aggiornamento in cui corrente di SQL istruzione è supportata quando il cursore è un cursore dinamico. (Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre questa opzione supportata.)  
  
 SQL_CA1_POSITIONED_DELETE = A eliminare in corrente di SQL istruzione è supportata quando il cursore è un cursore dinamico. (Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre questa opzione supportata.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = un'istruzione SELECT per istruzione UPDATE SQL è supportata quando il cursore è un cursore dinamico. (Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre questa opzione supportata.)  
  
 SQL_CA1_BULK_ADD = un *operazione* argomento di SQL_ADD è supportato in una chiamata a **SQLBulkOperations** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = un *operazione* argomento di SQL_UPDATE_BY_BOOKMARK è supportato in una chiamata a **SQLBulkOperations** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = un *operazione* argomento di SQL_DELETE_BY_BOOKMARK è supportato in una chiamata a **SQLBulkOperations** quando il cursore si trova un cursore dinamico.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = un *operazione* argomento di SQL_FETCH_BY_BOOKMARK è supportato in una chiamata a **SQLBulkOperations** quando il cursore si trova un cursore dinamico.  
  
 Un driver di livello conforme allo standard SQL-92 intermedio in genere restituirà le opzioni SQL_CA1_NEXT SQL_CA1_ABSOLUTE e SQL_CA1_RELATIVE supportato, poiché supporta i cursori scorrevoli tramite l'istruzione SQL FETCH incorporato. Poiché questo non determinare direttamente il supporto SQL sottostante, tuttavia, i cursori scorrevoli potrebbero non essere supportati, anche per un driver conforme allo standard livello intermedio di SQL-92.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore dinamico sono supportati dal driver. La maschera di bit contiene il secondo subset di attributi. per il primo subset, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = sola lettura con cursori dinamici, in cui non sono consentiti aggiornamenti, sono supportata. (L'attributo di istruzione SQL_ATTR_CONCURRENCY può essere SQL_CONCUR_READ_ONLY per un cursore dinamico).  
  
 SQL_CA2_LOCK_CONCURRENCY = un cursore dinamico che utilizza il livello più basso di blocco sufficiente per assicurarsi che sia possibile aggiornare la riga è supportata. (L'attributo di istruzione SQL_ATTR_CONCURRENCY può essere SQL_CONCUR_LOCK per un cursore dinamico). Tali blocchi devono essere consistenti con il livello di isolamento impostato dall'attributo di connessione SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = un cursore dinamico che utilizza la concorrenza ottimistica controllo confronto tra le versioni di riga è supportata. (L'attributo di istruzione SQL_ATTR_CONCURRENCY può essere SQL_CONCUR_ROWVER per un cursore dinamico).  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = un cursore dinamico che utilizza i valori di confronto del controllo della concorrenza ottimistica è supportato. (L'attributo di istruzione SQL_ATTR_CONCURRENCY può essere SQL_CONCUR_VALUES per un cursore dinamico).  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = sono state aggiunte le righe sono visibili in un cursore dinamico; il cursore è possibile scorrere a tali righe. (In cui queste righe vengono aggiunte al cursore è dipendente dal driver).  
  
 SQL_CA2_SENSITIVITY_DELETIONS = eliminati non sono più disponibili in un cursore dinamico, righe e di non lasciare un foro"" nel set di risultati. Dopo il cursore dinamico passa da una riga eliminata, è possibile tornare alla riga.  
  
 SQL_CA2_SENSITIVITY_UPDATES = gli aggiornamenti alle righe sono visibili in un cursore dinamico; Se il cursore dinamico scorre dall'e restituisce una riga aggiornata, i dati restituiti dal cursore sono i dati aggiornati, non i dati originali.  
  
 SQL_CA2_MAX_ROWS_SELECT = SQL_ATTR_MAX_ROWS l'istruzione attributo influisce **selezionare** istruzioni quando il cursore è un cursore dinamico.  
  
 SQL_CA2_MAX_ROWS_INSERT = SQL_ATTR_MAX_ROWS l'istruzione attributo influisce **inserire** istruzioni quando il cursore è un cursore dinamico.  
  
 SQL_CA2_MAX_ROWS_DELETE = SQL_ATTR_MAX_ROWS l'istruzione attributo influisce **eliminare** istruzioni quando il cursore è un cursore dinamico.  
  
 SQL_CA2_MAX_ROWS_UPDATE = SQL_ATTR_MAX_ROWS l'istruzione attributo influisce **aggiornamento** istruzioni quando il cursore è un cursore dinamico.  
  
 SQL_CA2_MAX_ROWS_CATALOG = SQL_ATTR_MAX_ROWS l'istruzione attributo influisce **catalogo** set di risultati quando il cursore è un cursore dinamico.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = SQL_ATTR_MAX_ROWS l'istruzione attributo influisce **selezionare**, **inserire**, **eliminare**, e **aggiornamento** istruzioni e **catalogo** set, di risultati quando il cursore è un cursore dinamico.  
  
 SQL_CA2_CRC_EXACT = l'esatto numero di righe è disponibile nel campo diagnostica SQL_DIAG_CURSOR_ROW_COUNT quando il cursore si trova un cursore dinamico.  
  
 SQL_CA2_CRC_APPROXIMATE = un valore approssimato conteggio delle righe è disponibile nel campo diagnostica SQL_DIAG_CURSOR_ROW_COUNT quando il cursore è un cursore dinamico.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = il driver non garantisce che simulato posizionato aggiornamento o le istruzioni delete influirà solo una riga quando il cursore è un cursore dinamico. è responsabilità dell'applicazione a tale scopo. (Se un'istruzione interessa più di una riga, **SQLExecute** o **SQLExecDirect** restituisce SQLSTATE 01001 [conflitto dell'operazione di cursore].) Per impostare questo comportamento, l'applicazione chiama **SQLSetStmtAttr** con il SQL_ATTR_SIMULATE_CURSOR attributo impostato su SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = driver tenta di garantire che simulati per gli aggiornamenti posizionati o le istruzioni delete influirà solo una riga quando il cursore è un cursore dinamico. Il driver esegue sempre tali istruzioni, anche se che potrebbero influire su più righe, ad esempio quando è presente alcuna chiave univoca. (Se un'istruzione interessa più di una riga, **SQLExecute** o **SQLExecDirect** restituisce SQLSTATE 01001 [conflitto dell'operazione di cursore].) Per impostare questo comportamento, l'applicazione chiama **SQLSetStmtAttr** con il SQL_ATTR_SIMULATE_CURSOR attributo impostato su SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE = il driver garantisce che simulato posizionato aggiornamento o le istruzioni delete influirà solo una riga quando il cursore è un cursore dinamico. Se il driver non può garantire per una determinata istruzione **SQLExecDirect** o **SQLPrepare** restituire SQLSTATE 01001 (conflitto dell'operazione del cursore). Per impostare questo comportamento, l'applicazione chiama **SQLSetStmtAttr** con il SQL_ATTR_SIMULATE_CURSOR attributo impostato su SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 Una stringa di caratteri: "Y" se l'origine dati supporta le espressioni nel **ORDER BY** elenco; "N" in caso contrario.  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 Un valore SQLUSMALLINT che indica il modo in cui un driver a un solo livello considera direttamente i file in un'origine dati:  
  
 SQL_FILE_NOT_SUPPORTED = il driver non è un driver a un solo livello. Ad esempio, un driver ORACLE è un driver a due livelli.  
  
 SQL_FILE_TABLE = un file di driver a un solo livello considera in un'origine dati come tabelle. Ad esempio, un driver Xbase considera ogni file Xbase come una tabella.  
  
 SQL_FILE_CATALOG = i file considera un solo livello driver in un'origine dati come un catalogo. Ad esempio, un driver Microsoft Access considera ogni file di Microsoft Access come un database completo.  
  
 Un'applicazione può utilizzare per determinare come gli utenti la selezione dei dati. Ad esempio, Xbase gli utenti spesso considerare i dati archiviati in file, mentre gli utenti ORACLE e Microsoft Access in genere considerate dei dati archiviati nelle tabelle.  
  
 Quando un utente seleziona un'origine dati Xbase, l'applicazione può visualizzare le finestre **Apri File** la finestra di dialogo comuni; quando l'utente seleziona un'origine dati ORACLE o Microsoft Access, l'applicazione potrebbe visualizzare un oggetto personalizzato  **Selezionare una tabella** la finestra di dialogo.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore forward-only sono supportati dal driver. La maschera di bit contiene il primo subset di attributi. per il subset di secondo, vedere SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_ UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Per una descrizione di queste maschere di bit, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (e sostituire "cursore forward-only" per "cursore dinamico" nelle descrizioni).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore forward-only sono supportati dal driver. La maschera di bit contiene il secondo subset di attributi. per il primo subset, vedere SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Per una descrizione di queste maschere di bit, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (e sostituire "cursore forward-only" per "cursore dinamico" nelle descrizioni).  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle estensioni **SQLGetData**.  
  
 Le maschere di bit seguenti vengono utilizzati con il flag per determinare quali il driver supporta per le estensioni comuni **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** può essere chiamato per qualsiasi colonna non associata, inclusi quelli prima che l'ultima colonna associata. Si noti che le colonne devono essere chiamate in ordine crescente numero di colonna, a meno che non viene restituito anche SQL_GD_ANY_ORDER.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** può essere chiamato per le colonne non associate in qualsiasi ordine. Si noti che **SQLGetData** può essere chiamato solo per le colonne dopo l'ultima colonna associata, a meno che non viene restituito anche SQL_GD_ANY_COLUMN.  
  
 SQL_GD_BLOCK = **SQLGetData** può essere chiamato per una colonna non associata in qualsiasi riga in un blocco (in cui le dimensioni del set di righe sono maggiore di 1) dei dati dopo il posizionamento di tale riga con **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** può essere chiamato per le colonne associate, oltre alle colonne non associate. Un driver non può restituire questo valore, a meno che non restituisce inoltre SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** può essere chiamato per restituire i valori di parametro di output. Per ulteriori informazioni, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** è necessaria per restituire i dati solo da colonne che si verificano dopo l'ultima colonna, associata vengono chiamati in ordine crescente numero di colonna e non sono in una riga in un blocco di righe.  
  
 Se un driver supporta segnalibri (a lunghezza fissa o a lunghezza variabile), deve supportare la chiamata **SQLGetData** nella colonna 0. Questo supporto è richiesto indipendentemente dalla ciò che il driver restituisce per una chiamata a **SQLGetInfo** con il SQL_GETDATA_EXTENSIONS *InfoType*.  
  
 SQL_GROUP_BY (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica la relazione tra le colonne di **GROUP BY** clausola e le colonne non aggregate nell'elenco di selezione:  
  
 SQL_GB_COLLATE = A **COLLATE** clausola può essere specificata alla fine di ogni colonna di raggruppamento. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY** clausole non sono supportate. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = il **GROUP BY** clausola deve contenere tutte le colonne non aggregate nell'elenco di selezione. Non può contenere altre colonne. Ad esempio, **selezionare reparto, MAX(SALARY) dal gruppo dipendenti per reparto**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = il **GROUP BY** clausola deve contenere tutte le colonne non aggregate nell'elenco di selezione. Può contenere colonne che non sono presenti nell'elenco di selezione. Ad esempio, **selezionare reparto, MAX(SALARY) dal gruppo dipendenti per reparto, l'età**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = le colonne di **GROUP BY** clausola e l'elenco di selezione non sono correlati. Il significato delle colonne nongrouped, non aggregati nell'elenco di selezione è dipende dall'origine dati. Ad esempio, **selezionare reparto, stipendio dal gruppo dipendenti per reparto, l'età**. (ODBC 2.0)  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre l'opzione SQL_GB_GROUP_BY_EQUALS_SELECT supportato. Un driver di livello conforme allo standard SQL-92 completo restituirà sempre l'opzione SQL_GB_COLLATE supportato. Se nessuna delle opzioni è supportata la **GROUP BY** clausola non è supportata dall'origine dati.  
  
 SQL_IDENTIFIER_CASE (ODBC 1.0)  
 Un SQLUSMALLINT valore come indicato di seguito:  
  
 SQL_IC_UPPER = identificatori in SQL non sono tra maiuscole e minuscole e vengono archiviati in maiuscolo nel catalogo di sistema.  
  
 SQL_IC_LOWER = identificatori in SQL non sono tra maiuscole e minuscole e vengono archiviati in minuscolo nel catalogo di sistema.  
  
 SQL_IC_SENSITIVE = gli identificatori di SQL tra maiuscole e minuscole e vengono archiviati in maiuscolo e minuscolo nel catalogo di sistema.  
  
 SQL_IC_MIXED = gli identificatori di SQL non sono tra maiuscole e minuscole e vengono archiviati in caratteri maiuscoli e minuscoli nel catalogo di sistema.  
  
 Poiché gli identificatori di SQL-92 sono mai distinzione maiuscole/minuscole, un driver conforme esclusivamente a SQL-92 (qualsiasi livello) non restituisce mai l'opzione SQL_IC_SENSITIVE supportato.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1.0)  
 La stringa di caratteri che viene utilizzata come delimitatore iniziale e finale di un'offerta identificatore nelle istruzioni SQL (delimitato). (Identificatori passati come argomenti alle funzioni ODBC non è necessario essere racchiusi tra virgolette). Se l'origine dati non supporta gli identificatori tra virgolette, viene restituito un valore vuoto.  
  
 Questa stringa di caratteri anche utilizzabile per racchiudere tra virgolette gli argomenti della funzione catalogo quando l'attributo di connessione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE.  
  
 Poiché il carattere di virgoletta identificatore in SQL-92 è il segno di virgolette doppie ("), un driver conforme esclusivamente a SQL-92 restituirà sempre il carattere di virgolette doppie.  
  
 SQL_INDEX_KEYWORDS (ODBC 3.0)  
 Maschera di bit SQLUINTEGER che enumera le parole chiave nell'istruzione CREATE INDEX che sono supportate dal driver:  
  
 SQL_IK_NONE = nessuna delle parole chiave è supportata.  
  
 SQL_IK_ASC = ASC (parola chiave) è supportato.  
  
 SQL_IK_DESC = DESC (parola chiave) è supportato.  
  
 SQL_IK_ALL = tutte le parole chiave sono supportate.  
  
 Per vedere se l'istruzione CREATE INDEX è supportata, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_DLL_INDEX.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle viste INFORMATION_SCHEMA sono supportate dal driver. Le visualizzazioni e il contenuto di INFORMATION_SCHEMA sono definite in SQL-92.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali visualizzazioni sono supportate:  
  
 SQL_ISV_ASSERTIONS = identifica le asserzioni del catalogo che appartengono a un determinato utente. (Livello completo)  
  
 SQL_ISV_CHARACTER_SETS = identifica set di caratteri del catalogo che è possibile accedere a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_CHECK_CONSTRAINTS = identifica il controllo di vincoli che appartengono a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_COLLATIONS = identifica le regole di confronto carattere per il catalogo a cui è possibile accedere a un determinato utente. (Livello completo)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = identifica le colonne per il catalogo che dipendono da domini definiti nel catalogo e di proprietà di un determinato utente. (Livello intermedio)  
  
 SQL_ISV_COLUMN_PRIVILEGES = identifica i privilegi sulle colonne di tabelle permanenti sono disponibili a o concessi da un determinato utente. (Transizione FIPS livello)  
  
 SQL_ISV_COLUMNS = identifica le colonne delle tabelle permanenti che è possibile accedere a un determinato utente. (Transizione FIPS livello)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = simile a CONSTRAINT_TABLE_USAGE-vista, le colonne vengono identificate per i vari vincoli che appartengono a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = identifica le tabelle utilizzate da vincoli (referenziale, univoco, asserzioni e) che appartengono a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = identifica i vincoli di dominio (dei domini nel catalogo) che è possibile accedere a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_DOMAINS = identifica i domini definiti in un catalogo che sono accessibili dall'utente. (Livello intermedio)  
  
 SQL_ISV_KEY_COLUMN_USAGE = identifica le colonne definite nel catalogo sono vincolate come chiavi di un determinato utente. (Livello intermedio)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = identifica i vincoli referenziali che appartengono a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_SCHEMATA = identifica gli schemi di proprietà di un determinato utente. (Livello intermedio)  
  
 SQL_ISV_SQL_LANGUAGES = identifica i livelli di conformità SQL, opzioni e sottolinguaggi supportati dall'implementazione SQL. (Livello intermedio)  
  
 SQL_ISV_TABLE_CONSTRAINTS = identifica i vincoli di tabella che appartengono a un determinato utente. (Livello intermedio)  
  
 SQL_ISV_TABLE_PRIVILEGES = identifica i privilegi sulle tabelle permanenti sono disponibili a o concessi da un determinato utente. (Transizione FIPS livello)  
  
 SQL_ISV_TABLES = identifica le tabelle persistenti definite in un catalogo che è possibile accedere a un determinato utente. (Transizione FIPS livello)  
  
 SQL_ISV_TRANSLATIONS = identifica le traduzioni di carattere per il catalogo a cui è possibile accedere a un determinato utente. (Livello completo)  
  
 SQL_ISV_USAGE_PRIVILEGES = identifica l'utilizzo di privilegi su oggetti di catalogo che sono disponibili o proprietà di un determinato utente. (Transizione FIPS livello)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = identifica le colonne in cui il catalogo viste che appartengono a un determinato utente sono dipendenti. (Livello intermedio)  
  
 SQL_ISV_VIEW_TABLE_USAGE = identifica le tabelle in cui il catalogo viste che appartengono a un determinato utente sono dipendenti. (Livello intermedio)  
  
 SQL_ISV_VIEWS = identifica le tabelle visualizzate definite nel catalogo accessibili a un determinato utente. (Transizione FIPS livello)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 Maschera di bit SQLUINTEGER che indica il supporto per **inserire** istruzioni:  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_INTEGRITY (ODBC 1.0)  
 Una stringa di caratteri: "Y" se l'origine dati supporta la funzionalità di miglioramento integrità; "N" in caso contrario.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore keyset sono supportati dal driver. La maschera di bit contiene il primo subset di attributi. per il subset di secondo, vedere SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Per una descrizione di queste maschere di bit, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (e sostituire "basati su keyset cursor" per "cursore dinamico" nelle descrizioni).  
  
 Un driver di livello conforme allo standard SQL-92 intermedio in genere restituirà le opzioni SQL_CA1_NEXT SQL_CA1_ABSOLUTE e SQL_CA1_RELATIVE supportato, perché il driver supporta i cursori scorrevoli tramite l'istruzione SQL FETCH incorporato. Poiché questo non determinare direttamente il supporto SQL sottostante, tuttavia, i cursori scorrevoli potrebbero non essere supportati, anche per un driver conforme allo standard livello intermedio di SQL-92.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore keyset sono supportati dal driver. La maschera di bit contiene il secondo subset di attributi. per il primo subset, vedere SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Per una descrizione di queste maschere di bit, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (e sostituire "basati su keyset cursor" per "cursore dinamico" nelle descrizioni).  
  
 SQL_KEYWORDS (ODBC 2.0)  
 Una stringa di caratteri che contiene un elenco delimitato da virgole di tutte le parole chiave specifici dell'origine dati. Questo elenco non contiene parole chiave specifiche di ODBC o le parole chiave utilizzate da parte dell'origine dati e ODBC. Questo elenco rappresenta tutte le parole chiave riservate. applicazioni interoperative non utilizzare queste parole nei nomi degli oggetti.  
  
 Per un elenco di parole chiave ODBC, vedere [parole chiave riservate](../../../odbc/reference/appendixes/reserved-keywords.md) in [grammatica SQL di appendice c:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Il **#define** valore SQL_ODBC_KEYWORDS contiene un elenco delimitato da virgole delle parole chiave ODBC.  
  
 Appendice c: la grammatica SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 Una stringa di caratteri: "Y" se l'origine dati supporta un carattere di escape per la percentuale di caratteri (%) e caratteri di sottolineatura (_) di caratteri un **come** predicato e il driver supporta la sintassi ODBC per la definizione di un **come** predicato carattere di escape. "N" in caso contrario.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3.0)  
 Valore SQLUINTEGER che specifica il numero massimo di istruzioni simultanee attive in modalità asincrona in grado di supportare il driver in una determinata connessione. Se non vi è alcun limite specifico o il limite è sconosciuto, questo valore è zero.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 Valore SQLUINTEGER che specifica la lunghezza massima (numero di caratteri esadecimali, escluso il prefisso letterale e il suffisso restituito da **SQLGetTypeInfo**) di un valore letterale binario in un'istruzione SQL. Ad esempio, il file binario 0xFFAA letterale ha una lunghezza pari a 4. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome di catalogo nell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS completo restituirà almeno 128.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 Valore SQLUINTEGER che specifica la lunghezza massima (numero di caratteri, escluso il prefisso letterale e il suffisso restituito da **SQLGetTypeInfo**) di un carattere letterale in un'istruzione SQL. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome di colonna nell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 18. Un driver di livello – conforme a FIPS intermedio restituirà almeno 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di colonne consentite in un **GROUP BY** clausola. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 6. Un driver di livello – conforme a FIPS intermedio restituirà almeno 15.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di colonne consentite in un indice. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di colonne consentite in un **ORDER BY** clausola. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 6. Un driver di livello – conforme a FIPS intermedio restituirà almeno 15.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di colonne consentite in un elenco di selezione. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno pari a 100. Un driver di livello – conforme a FIPS intermedio restituirà almeno 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di colonne consentite in una tabella. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno pari a 100. Un driver di livello – conforme a FIPS intermedio restituirà almeno 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di istruzioni attive in grado di supportare il driver per una connessione. Un'istruzione è definita come attivo se i risultati in sospeso, con il termine "risultati" significato le righe da un **selezionare** operazione o delle righe interessate da un **inserire**, **aggiornamento**, o **Eliminare** operazione (ad esempio, un conteggio delle righe), o se è in uno stato NEED_DATA. Questo valore può riflettere una limitazione imposta dal driver o l'origine dati. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome di cursore nell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 18. Un driver di livello – conforme a FIPS intermedio restituirà almeno 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di connessioni attive in grado di supportare il driver per un ambiente. Questo valore può riflettere una limitazione imposta dal driver o l'origine dati. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 Un SQLUSMALLINT che indica la dimensione massima in caratteri che l'origine dati supporta per i nomi definiti dall'utente.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 18. Un driver di livello – conforme a FIPS intermedio restituirà almeno 128.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 Valore SQLUINTEGER che specifica il numero massimo di byte consentito nei campi combinati di un indice. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome della stored procedure nell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 SQL_MAX_ROW_SIZE (ODBC 2.0)  
 Valore SQLUINTEGER che specifica la lunghezza massima di una singola riga in una tabella. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 2.000. Un driver di livello – conforme a FIPS intermedio restituirà almeno 8.000.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 Una stringa di caratteri: "Y", se le dimensioni massime delle righe restituite per il tipo di informazioni SQL_MAX_ROW_SIZE include la lunghezza di tutte le colonne SQL_LONGVARCHAR e SQL_LONGVARBINARY nella riga. "N" in caso contrario.  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome di schema dell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 18. Un driver di livello – conforme a FIPS intermedio restituirà almeno 128.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 Valore SQLUINTEGER che specifica la lunghezza massima (numero di caratteri, incluso lo spazio vuoto) di un'istruzione SQL. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome di tabella nell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 18. Un driver di livello – conforme a FIPS intermedio restituirà almeno 128.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di tabelle consentito nel **FROM** clausola di un **selezionare** istruzione. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 Un driver di livello – conforme a FIPS voce restituirà almeno 15. Un driver di livello – conforme a FIPS intermedio restituirà almeno 50.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2.0)  
 Valore SQLUSMALLINT che specifica la lunghezza massima di un nome utente nell'origine dati. Se è prevista una lunghezza massima o la lunghezza è sconosciuta, questo valore è impostato su zero.  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 Una stringa di caratteri: "Y" se l'origine dati supporta più set di risultati, "N", in caso contrario.  
  
 Per ulteriori informazioni sui più set di risultati, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1.0)  
 Una stringa di caratteri: "Y" se il driver supporta più di una transazione attiva allo stesso tempo, "N" se solo una transazione può essere attiva in qualsiasi momento.  
  
 Le informazioni restituite per questo tipo di informazioni non è applicabile nel caso di transazioni distribuite.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2.0)  
 Una stringa di caratteri: "Y" se l'origine dati è la lunghezza di un valore di dati long (il tipo di dati è un tipo di dati specifici dell'origine dati di tipo long, SQL_LONGVARCHAR o SQL_LONGVARBINARY) prima di tale valore viene inviato all'origine dati, "N", in caso contrario. Per ulteriori informazioni, vedere [funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) e [funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1.0)  
 Un valore SQLUSMALLINT che specifica se l'origine dati supporta NOT NULL nelle colonne:  
  
 SQL_NNC_NULL = tutte le colonne devono essere nullable.  
  
 SQL_NNC_NON_NULL = colonne non possono essere nullable. (L'origine dati supporta la **non NULL** il vincolo di colonna in **CREATE TABLE** istruzioni.)  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 Un valore SQLUSMALLINT che specifica in cui i valori null sono ordinati in un set di risultati:  
  
 SQL_NC_END = i valori null vengono posizionati alla fine del set di risultati, indipendentemente dal fatto le parole chiave ASC o DESC.  
  
 SQL_NC_HIGH = vengono ordinati i valori null nella parte superiore del set di risultati, a seconda delle parole chiave ASC o DESC.  
  
 SQL_NC_LOW = vengono ordinati i valori null nella parte inferiore del set di risultati, a seconda delle parole chiave ASC o DESC.  
  
 SQL_NC_START = i valori null vengono posizionati all'inizio del set di risultati, indipendentemente dal fatto le parole chiave ASC o DESC.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1.0)  
 Nota: Il tipo di informazioni è stata introdotta in ODBC 1.0; ogni maschera di bit viene etichettato con la versione in cui è stato introdotto.  
  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni scalari numeriche supportate dal driver origine dati associata.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali funzioni numeriche sono supportate:  
  
 (ODBC 1.0) SQL_FN_NUM_ABS SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 SQL _ SQL_FN_NUM_DEGREES (ODBC 2.0) DI (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) (ODBC 1.0) FN_NUM_EXP SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 SQL_FN_ SQL_FN_NUM_RAND (ODBC 1.0) DI (ODBC 2.0) SQL_FN_NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) NUM_ROUND (ODBC 2.0) (ODBC 1.0) SQL_FN_NUM_SIGN SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3.0)  
 Valore SQLUINTEGER che indica il livello di ODBC 3*x* interfaccia compatibile con il driver.  
  
 SQL_OIC_CORE: Dovrà conformarsi il livello minimo di tutti i driver ODBC. Questo livello include gli elementi di interfaccia di base, ad esempio le funzioni di connessione, le funzioni per la preparazione e l'esecuzione di un'istruzione SQL, funzioni dei metadati di set di risultati di base, funzioni di catalogo di base e così via.  
  
 SQL_OIC_LEVEL1: Un livello tra i segnalibri funzionalità a livello di conformità agli standard e i cursori scorrevoli, componenti di base, posizionati degli aggiornamenti e consente di eliminare e così via.  
  
 SQL_OIC_LEVEL2: Un livello include funzionalità a livello di conformità agli standard livello 1, oltre alle funzionalità avanzate, ad esempio i cursori sensibili; aggiornare, eliminare e aggiornare i segnalibri; supporto delle stored procedure; funzioni di catalogo per le chiavi primarie ed esterne; Supporto multi-catalogo. E così via.  
  
 Per ulteriori informazioni, vedere [livelli di conformità interfaccia](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER (ODBC 1.0)  
 Una stringa di caratteri con la versione di a cui è conforme in Gestione Driver ODBC. La versione è nel formato # #. # #. 0000, in cui le prime due cifre indicano la versione principale e le due cifre successive sono la versione secondaria. Questo viene implementato solo in Gestione Driver.  
  
 SQL_OJ_CAPABILITIES (ODBC 2.01)  
 Maschera di bit SQLUINTEGER l'enumerazione dei tipi di outer join, supportati dall'origine dati e i driver. Le maschere di bit seguenti vengono utilizzati per determinare i tipi supportati:  
  
 SQL_OJ_LEFT = Left outer join sono supportati.  
  
 SQL_OJ_RIGHT = Right outer join sono supportati.  
  
 SQL_OJ_FULL = Full outer join sono supportati.  
  
 SQL_OJ_NESTED = Nested outer join sono supportati.  
  
 SQL_OJ_NOT_ORDERED = nome nella clausola ON di outer join non deve essere nello stesso ordine come i nomi di tabella corrispondente nella colonna di **OUTER JOIN** clausola.  
  
 SQL_OJ_INNER = interna tabella (tabella di destra in un left outer join) o la tabella a sinistra in un right outer join può essere utilizzata anche in un inner join. Questa opzione non viene applicata a full outer join, che non dispongono di una tabella interna.  
  
 SQL_OJ_ALL_COMPARISON_OPS = il confronto nella clausola ON può essere uno degli operatori di confronto di ODBC. Se questo bit non è impostato, è possibile utilizzare solo l'operatore di confronto di uguaglianza (=) in outer join.  
  
 Se nessuna di queste opzioni viene restituita come supportate, una clausola outer join non è supportata.  
  
 Per informazioni sul supporto degli operatori di join relazionale in un'istruzione SELECT, come definito da SQL-92, vedere SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2.0)  
 Una stringa di caratteri: "Y" se le colonne di **ORDER BY** clausola deve essere nell'elenco di selezione; in caso contrario, "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3.0)  
 Un SQLUINTEGER durante l'enumerazione delle proprietà del driver relativa alla disponibilità della riga conta durante l'esecuzione di parametri. Presenta i seguenti valori:  
  
 SQL_PARC_BATCH = individuale i conteggi delle righe sono disponibili per ogni set di parametri. Questo è concettualmente equivalente al driver di generazione di un batch di istruzioni SQL, uno per ogni parametro nella matrice. Informazioni dettagliate sull'errore può essere recuperato tramite il campo di descrizione SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH = solo una riga il numero è disponibile, ovvero il conteggio cumulativo delle righe risultante dall'esecuzione dell'istruzione per l'intera matrice di parametri. Questo è concettualmente equivalente al considerando l'istruzione con la matrice di parametri completo come un'unità atomica. Gli errori vengono gestiti come se sono stata eseguita una sola istruzione.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 Un SQLUINTEGER durante l'enumerazione delle proprietà del driver sulla disponibilità del risultato imposta durante l'esecuzione di parametri. Presenta i seguenti valori:  
  
 SQL_PAS_BATCH = è un set di risultati disponibile per ogni set di parametri. Questo è concettualmente equivalente al driver di generazione di un batch di istruzioni SQL, uno per ogni parametro nella matrice.  
  
 SQL_PAS_NO_BATCH = è solo un set di risultati disponibile, che rappresenta il risultato cumulativo set risultante dall'esecuzione dell'istruzione per la matrice completa di parametri. Questo è concettualmente equivalente al considerando l'istruzione con la matrice di parametri completo come un'unità atomica.  
  
 SQL_PAS_NO_SELECT = un driver non consente un'istruzione di generazione di set di risultati deve essere eseguito con una matrice di parametri.  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 Una stringa di caratteri con il nome del fornitore di origine dati per una routine. ad esempio, "procedura di database", "stored procedure", "procedura", "pacchetto" o "query archiviata".  
  
 SQL_PROCEDURES (ODBC 1.0)  
 Una stringa di caratteri: "Y" se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC. "N" in caso contrario.  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 Una maschera di bit SQLINTEGER durante l'enumerazione delle operazioni di supporto in **SQLSetPos**.  
  
 Le maschere di bit seguenti vengono utilizzati con il flag per determinare quali opzioni sono supportate.  
  
 SQL_POS_POSITION (ODBC 2.0) (ODBC 2.0) SQL_POS_REFRESH SQL_POS_UPDATE (ODBC 2.0) (ODBC 2.0) SQL_POS_DELETE SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2.0)  
 Un SQLUSMALLINT valore come indicato di seguito:  
  
 SQL_IC_UPPER = tra virgolette gli identificatori di SQL non sono rilevanti e vengono archiviati in maiuscolo nel catalogo di sistema.  
  
 SQL_IC_LOWER = tra virgolette gli identificatori di SQL non sono tra maiuscole e minuscole e vengono archiviati in minuscolo nel catalogo di sistema.  
  
 SQL_IC_SENSITIVE = tra virgolette gli identificatori di SQL tra maiuscole e minuscole e vengono archiviati in maiuscolo e minuscolo nel catalogo di sistema. (In un database compatibile con SQL-92, gli identificatori tra virgolette sono sempre distinzione maiuscole/minuscole).  
  
 SQL_IC_MIXED = tra virgolette gli identificatori di SQL non sono tra maiuscole e minuscole e vengono archiviati in caratteri maiuscoli e minuscoli nel catalogo di sistema.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre SQL_IC_SENSITIVE.  
  
 SQL_ROW_UPDATES (ODBC 1.0)  
 Una stringa di caratteri: "Y", se un cursore keyset o misto mantiene le versioni di riga o valori per tutte le righe recupero e pertanto possono rilevare gli aggiornamenti che sono stati apportati a una riga da qualsiasi utente dopo l'ultimo recupero della riga. (Si applica solo agli aggiornamenti, non per eliminazioni o inserimenti). Il driver può restituire il flag SQL_ROW_UPDATED allo stato della riga della matrice quando **SQLFetchScroll** viene chiamato. In caso contrario, "N".  
  
 SQL_SCHEMA_TERM (ODBC 1.0)  
 Una stringa di caratteri con il nome del fornitore di origine dati per uno schema. ad esempio, "proprietario", "ID autorizzazione" o "Schema".  
  
 La stringa di caratteri può essere restituita in caso di superiore, inferiore o misto.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre "schema".  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE (ODBC 2.0)  
 Maschera di bit SQLUINTEGER enumerazione le istruzioni in cui è possibile utilizzare schemi:  
  
 SQL_SU_DML_STATEMENTS = gli schemi sono supportati in tutte le istruzioni Data Manipulation Language: **selezionare**, **inserire**, **aggiornamento**, **DELETE**e, se supportato **selezionare per aggiornare** e posizionato aggiornamento e istruzioni delete.  
  
 SQL_SU_PROCEDURE_INVOCATION = gli schemi sono supportati nell'istruzione di chiamata di procedura ODBC.  
  
 SQL_SU_TABLE_DEFINITION = gli schemi sono supportati in tutte le istruzioni di definizione di tabella: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE** , e **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = gli schemi sono supportati in tutte le istruzioni di definizione di indice: **CREATE INDEX** e **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = gli schemi sono supportati in tutte le istruzioni di definizione dei privilegi: **GRANT** e **revocare**.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre le opzioni di SQL_SU_DML_STATEMENTS SQL_SU_TABLE_DEFINITION e SQL_SU_PRIVILEGE_DEFINITION supportato.  
  
 Questo *InfoType* è stata rinominata per ODBC 3.0 da ODBC 2.0 *InfoType* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS ODBC (1.0)  
 Nota: Il tipo di informazioni è stata introdotta in ODBC 1.0; ogni maschera di bit viene etichettato con la versione in cui è stato introdotto.  
  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle opzioni di scorrimento supportate per i cursori scorrevoli.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali opzioni sono supportate:  
  
 SQL_SO_FORWARD_ONLY = il cursore solo scorre verso il rollforward. ODBC (1.0)  
  
 SQL_SO_STATIC = i dati del risultato è statico. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = i salvataggi dei driver e utilizza le chiavi per ogni riga nel set di risultati. ODBC (1.0)  
  
 SQL_SO_DYNAMIC = mantiene il driver le chiavi per ogni riga nel set di righe (la dimensione del keyset è la stessa della dimensione del set di righe). ODBC (1.0)  
  
 SQL_SO_MIXED = mantiene il driver le chiavi per ogni riga nel keyset e la dimensione del keyset è maggiore della dimensione del set di righe. Il cursore è basati su keyset in keyset e dinamici all'esterno di keyset. ODBC (1.0)  
  
 Per informazioni sui cursori scorrevoli, vedere [cursori scorrevoli](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1.0)  
 Una stringa di caratteri che specifica ciò che il driver supporta come carattere di escape che consente di usare il modello corrispondenza metacaratteri sottolineatura (_) e segno di percentuale (%) come caratteri validi in Criteri di ricerca. Questo carattere escape si applica solo a tali argomenti della funzione di catalogo che supportano le stringhe di ricerca. Se questa stringa è vuota, il driver non supporta un carattere di escape del criterio di ricerca.  
  
 Poiché questo tipo di informazioni non indica il supporto generale del carattere di escape di **come** predicato, SQL-92 non includono i requisiti per questa stringa di caratteri.  
  
 Questo *InfoType* è limitato alle funzioni di catalogo. Per una descrizione dell'utilizzo del carattere di escape nelle stringhe di modello di ricerca, vedere [argomenti di modello valore](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME ODBC (1.0)  
 Una stringa di caratteri con il nome di server specifici dell'origine dati effettivi. utile quando viene utilizzato un nome origine dati durante **SQLConnect**, **SQLDriverConnect**, e **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2.0)  
 Una stringa di caratteri che contiene tutti i caratteri speciali (vale a dire tutti i caratteri eccetto alla z, alla Z, 0 a 9 e caratteri di sottolineatura) che possono essere utilizzati in un nome di identificatore, ad esempio un nome di tabella, nome di colonna o il nome dell'indice, l'origine dati. Ad esempio, "#$^". Se un identificatore contiene uno o più di questi caratteri, l'identificatore deve essere un identificatore delimitato.  
  
 SQL_SQL_CONFORMANCE (ODBC 3.0)  
 Valore SQLUINTEGER che indica il livello di SQL-92 supportate dal driver:  
  
 SQL_SC_SQL92_ENTRY = voce livello SQL-92 conformi.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 livello transizione conformo.  
  
 SQL_SC_SQL92_FULL = livello completo SQL-92.  
  
 SQL_SC_ SQL92_INTERMEDIATE = intermedio livello SQL-92 conformi.  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni scalari datetime supportati dal driver e l'origine dati associata, come definito in SQL-92.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali funzioni di data/ora sono supportate:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle regole è supportate per una chiave esterna in un **eliminare** istruzione, come definito in SQL-92.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate dall'origine dati:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Un driver di livello – conforme a FIPS transizione restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle regole è supportate per una chiave esterna in un **aggiornamento** istruzione, come definito in SQL-92.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate dall'origine dati:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Un driver di livello conforme allo standard SQL-92 completo restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di clausole supportate nel **GRANT** istruzione, come definito in SQL-92.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate dall'origine dati:  
  
 (SQL_SG_INSERT_COLUMN (livello intermedio) SQL_SG_INSERT_TABLE (Entry level) SQL_SG_REFERENCES_TABLE (Entry level) SQL_SG_REFERENCES_COLUMN (Entry level) SQL_SG_SELECT_TABLE (Entry level) SQL_SG_UPDATE_COLUMN SQL_SG_DELETE_TABLE (Entry level) Entry level) SQL_SG_UPDATE_TABLE (Entry level) SQL_SG_USAGE_ON_DOMAIN (livello FIPS transizione) SQL_SG_USAGE_ON_CHARACTER_SET (livello FIPS transizione) SQL_SG_USAGE_ON_COLLATION (livello FIPS transizione) SQL_SG_USAGE_ON_TRANSLATION FIPS (FEDERAL Livello di transizione) SQL_SG_WITH_GRANT_OPTION (Entry level)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni scalari valore numerico che sono supportate dal driver e l'origine dati associata, come definito in SQL-92.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali funzioni numeriche sono supportate:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione dei predicati supportati in un **selezionare** istruzione, come definito in SQL-92.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali opzioni sono supportate dall'origine dati:  
  
 SQL_SP_BETWEEN (Entry level) SQL_SP_COMPARISON (Entry level) SQL_SP_EXISTS (Entry level) SQL_SP_IN (Entry level) SQL_SP_ISNOTNULL (Entry level) SQL_SP_ISNULL (Entry level) SQL_SP_LIKE (Entry level) SQL_SP_MATCH_FULL (livello completo) SQL_SP_MATCH_PARTIAL (Livello completo) SQL_SP_MATCH_UNIQUE_FULL (livello completo) SQL_SP_MATCH_UNIQUE_PARTIAL (livello completo) SQL_SP_OVERLAPS (livello FIPS transizione) SQL_SP_QUANTIFIED_COMPARISON (Entry level) SQL_SP_UNIQUE (Entry level)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 Maschera di bit SQLUINTEGER enumerazione gli operatori di join relazionali supportati in un **selezionare** istruzione, come definito in SQL-92.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali opzioni sono supportate dall'origine dati:  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (livello intermedio) SQL_SRJO_CROSS_JOIN (livello completo) SQL_SRJO_EXCEPT_JOIN (livello intermedio) SQL_SRJO_FULL_OUTER_JOIN (livello intermedio) SQL_SRJO_INNER_JOIN (livello FIPS transizione) SQL_SRJO_INTERSECT_JOIN (Livello intermedio) SQL_SRJO_LEFT_OUTER_JOIN (livello FIPS transizione) SQL_SRJO_NATURAL_JOIN (livello FIPS transizione) SQL_SRJO_RIGHT_OUTER_JOIN (livello FIPS transizione) SQL_SRJO_UNION_JOIN (livello completo)  
  
 SQL_SRJO_INNER_JOIN indica il supporto per il **INNER JOIN** sintassi, non per la funzionalità di inner join. Supporto per il **INNER JOIN** sintassi è FIPS transizione, mentre il supporto per la funzionalità di inner join **voce**.  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di clausole supportate nel **revocare** istruzione, come definito in SQL-92, supportato dall'origine dati.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate dall'origine dati:  
  
 SQL_SR_CASCADE (livello FIPS transizione) SQL_SR_DELETE_TABLE (Entry level) SQL_SR_GRANT_OPTION_FOR (livello intermedio) SQL_SR_INSERT_COLUMN (livello intermedio) SQL_SR_INSERT_TABLE (Entry level) SQL_SR_REFERENCES_COLUMN (Entry level) SQL_SR_ REFERENCES_TABLE (Entry level) SQL_SR_RESTRICT (livello FIPS transizione) SQL_SR_SELECT_TABLE (Entry level) SQL_SR_UPDATE_COLUMN (Entry level) SQL_SR_UPDATE_TABLE (Entry level) SQL_SR_USAGE_ON_DOMAIN (livello FIPS transizione) SQL_SR_USAGE_ON_ CHARACTER_SET (livello FIPS transizione) SQL_SR_USAGE_ON_COLLATION (livello FIPS transizione) SQL_SR_USAGE_ON_TRANSLATION (FIPS transizione livello)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 Maschera di bit SQLUINTEGER enumerazione le espressioni di costruttore di valore di riga è supportate in un **selezionare** istruzione, come definito in SQL-92. Le maschere di bit seguenti vengono utilizzati per determinare quali opzioni sono supportate dall'origine dati:  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni scalari di stringa supportate dal driver e l'origine dati associata, come definito in SQL-92.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le funzioni di stringa supportate:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Maschera di bit SQLUINTEGER enumerazione le espressioni valore supportate, come definito in SQL-92.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali opzioni sono supportate dall'origine dati:  
  
 SQL_SVE_CASE (livello intermedio) SQL_SVE_CAST (livello FIPS transizione) SQL_SVE_COALESCE (livello intermedio) SQL_SVE_NULLIF (livello intermedio)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3.0)  
 Maschera di bit SQLUINTEGER enumerazione standard CLI o standard a cui il driver conforme. Le maschere di bit seguenti vengono utilizzati per determinare quali livelli il driver conforme con:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Il driver è conforme a Open gruppo CLI versione 1.  
  
 SQL_SCC_ISO92_CLI: Il driver è conforme a ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore statico che sono supportati dal driver. La maschera di bit contiene il primo subset di attributi. per il subset di secondo, vedere SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Per una descrizione di queste maschere di bit, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (e sostituire "cursore statico" per "cursore dinamico" nelle descrizioni).  
  
 Un driver di livello conforme allo standard SQL-92 intermedio in genere restituirà le opzioni SQL_CA1_NEXT SQL_CA1_ABSOLUTE e SQL_CA1_RELATIVE supportato, perché il driver supporta i cursori scorrevoli tramite l'istruzione SQL FETCH incorporato. Poiché questo non determinare direttamente il supporto SQL sottostante, tuttavia, i cursori scorrevoli potrebbero non essere supportati, anche per un driver conforme allo standard livello intermedio di SQL-92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Maschera di bit SQLUINTEGER che descrive gli attributi di un cursore statico che sono supportati dal driver. La maschera di bit contiene il secondo subset di attributi. per il primo subset, vedere SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali attributi sono supportati:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Per una descrizione di queste maschere di bit, vedere SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (e sostituire "cursore statico" per "cursore dinamico" nelle descrizioni).  
  
 SQL_STRING_FUNCTIONS (ODBC 1.0)  
 Nota: Il tipo di informazioni è stata introdotta in ODBC 1.0; ogni maschera di bit viene etichettato con la versione in cui è stato introdotto.  
  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni scalari stringa supportate dal driver origine dati associata.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le funzioni di stringa supportate:  
  
 (ODBC 1.0) SQL_FN_STR_ASCII SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0) SQL_FN_STR_INSERT (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_ (ODBC 1.0) STR_REPLACE SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0)  
  
 Se un'applicazione può chiamare il **INDIVIDUA** funzione scalare con il *string_exp1*, *string_exp2 e*, e *avviare* argomenti, il driver Restituisce la maschera di bit SQL_FN_STR_LOCATE. Se un'applicazione può chiamare la funzione scalare di individuare solo con il *string_exp1* e *string_exp2 e* argomenti, il driver restituisce la maschera di bit SQL_FN_STR_LOCATE_2. I driver che supportano completamente il **INDIVIDUA** funzioni scalari restituiscono entrambi maschere di bit.  
  
 (Per ulteriori informazioni, vedere [funzioni stringa](../../../odbc/reference/appendixes/string-functions.md) nell'appendice e "funzioni scalari.")  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di predicati che supportano le sottoquery:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 La maschera di bit SQL_SQ_CORRELATED_SUBQUERIES indica che tutti i predicati che supportano le sottoquery supportano le sottoquery correlate.  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre una maschera di bit in cui tutti i bit sono impostati.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle funzioni di sistema scalari supportate dal driver e origine dati associata.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le funzioni di sistema sono supportate:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1.0)  
 Una stringa di caratteri con il nome del fornitore di origine dati per una tabella. ad esempio, "table" o "file".  
  
 Questa stringa di caratteri possibile in caso di superiore, inferiore o misto.  
  
 Un driver di livello conforme allo standard SQL-92 voce verrà sempre restituito "table".  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2.0)  
 Maschera di bit SQLUINTEGER enumerazione supportati dal driver origine dati associata per la funzione scalare TIMESTAMPADD gli intervalli di timestamp.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali intervalli sono supportati:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un driver di livello – conforme a FIPS transizione restituirà sempre una maschera di bit in cui tutti i bit sono impostati.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2.0)  
 Maschera di bit SQLUINTEGER enumerazione supportati dal driver origine dati associata per la funzione scalare TIMESTAMPDIFF gli intervalli di timestamp.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali intervalli sono supportati:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Un driver di livello – conforme a FIPS transizione restituirà sempre una maschera di bit in cui tutti i bit sono impostati.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1.0)  
 Nota: Il tipo di informazioni è stata introdotta in ODBC 1.0; ogni maschera di bit viene etichettato con la versione in cui è stato introdotto.  
  
 Maschera di bit SQLUINTEGER l'enumerazione di scalare funzioni data e ora supportate dal driver e origine dati associata.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare quali funzioni di data e ora sono supportate:  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) (SQL_FN_TD_DAYOFWEEK ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_ SECONDO (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE (ODBC 1.0)  
 Nota: Il tipo di informazioni è stata introdotta in ODBC 1.0; ogni valore restituito viene denominato con la versione in cui è stato introdotto.  
  
 Un valore SQLUSMALLINT che descrive il supporto delle transazioni nell'origine dati o driver:  
  
 SQL_TC_NONE = transazioni non supportate. ODBC (1.0)  
  
 SQL_TC_DML = transazioni possono contenere solo le istruzioni Data Manipulation Language (DML) (**selezionare**, **inserire**, **aggiornamento**, **eliminare** ). Istruzioni di Data Definition Language (DDL) errore in delle cause delle transazioni. ODBC (1.0)  
  
 SQL_TC_DDL_COMMIT = transazioni possono contenere solo le istruzioni DML. Istruzioni DDL (**CREATE TABLE**, **DROP INDEX**e così via) ha rilevato in delle cause delle transazioni la transazione di cui eseguire il commit. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = transazioni possono contenere solo le istruzioni DML. Le istruzioni DDL rilevate in una transazione vengono ignorate. (ODBC 2.0)  
  
 SQL_TC_ALL = transazioni possono contenere istruzioni DDL e le istruzioni DML in qualsiasi ordine. ODBC (1.0)  
  
 (Perché il supporto delle transazioni è obbligatorio in SQL-92, un driver conforme allo standard SQL-92 [qualsiasi livello] non restituisce mai SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1.0)  
 Maschera di bit SQLUINTEGER l'enumerazione dei livelli di isolamento delle transazioni disponibili dall'origine dati o driver.  
  
 Le maschere di bit seguenti vengono utilizzati con il flag per determinare quali opzioni sono supportate:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Per una descrizione di questi livelli di isolamento, vedere la descrizione di SQL_DEFAULT_TXN_ISOLATION.  
  
 Per impostare il livello di isolamento delle transazioni, un'applicazione chiama **SQLSetConnectAttr** per impostare l'attributo SQL_ATTR_TXN_ISOLATION. Per ulteriori informazioni, vedere [funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre SQL_TXN_SERIALIZABLE supportato. Un driver di livello – conforme a FIPS transizione restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_UNION (ODBC 2.0)  
 Maschera di bit SQLUINTEGER enumerazione il supporto per il **unione** clausola:  
  
 SQL_U_UNION = l'origine dati supporta la **unione** clausola.  
  
 SQL_U_UNION_ALL = l'origine dati supporta la **tutti** parola chiave nel **unione** clausola. (**SQLGetInfo** restituisce in questo caso SQL_U_UNION e SQL_U_UNION_ALL.)  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre entrambe le opzioni supportate.  
  
 SQL_USER_NAME (ODBC 1.0)  
 Una stringa di caratteri con il nome utilizzato in un determinato database, che può essere diverso dal nome dell'account di accesso.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3.0)  
 Una stringa di caratteri che indica l'anno di pubblicazione del server con cui la versione di gestione Driver ODBC è completamente conforme alla specifica di Open Group.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Una stringa di caratteri: "Y" se l'utente può eseguire tutte le procedure restituite dal **SQLProcedures**; "N" se vi sono procedure restituito che l'utente non è possibile eseguire.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Una stringa di caratteri: "Y" se è garantito che l'utente **selezionare** privilegi per tutte le tabelle restituite da **SQLTables**; "N" se vi sono tabelle restituito che l'utente non può accedere.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Valore SQLUSMALLINT che specifica il numero massimo di ambienti in grado di supportare il driver. Se non vi è alcun limite specificato o il limite è sconosciuto, questo valore è impostato su zero.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Maschera di bit SQLUINTEGER l'enumerazione di supporto per le funzioni di aggregazione:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Un driver di livello conforme allo standard SQL-92 Entry restituirà sempre tutte queste opzioni come supportati.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **ALTER dominio** istruzione, come definito in SQL-92, supportato dall'origine dati. Un driver conforme a livello di SQL-92 completo restituirà sempre tutte le maschere di bit. Il valore restituito pari a "0" indica che il **ALTER dominio** istruzione non è supportata.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = aggiunta è supportato un vincolo di dominio (livello completo)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter dominio > \<clausola default di set domain > è supportato (livello completo)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<clausola del nome della definizione di vincolo > è supportato per la denominazione dei vincoli di dominio (livello intermedio)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<clausola di vincolo dominio drop > è supportato (livello completo)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter dominio > \<clausola default di rilascio domain > è supportato (livello completo)  
  
 I bit seguenti specificano supportati \<attributi vincolo > Se \<aggiungere vincoli di dominio > è supportato (è impostato il bit SQL_AD_ADD_DOMAIN_CONSTRAINT):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (livello completo) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (livello completo) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (livello completo) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (livello completo)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Maschera di bit SQLUINTEGER durante l'enumerazione delle clausole nel **ALTER TABLE** supportati dall'origine dati.  
  
 Il livello di conformità in SQL-92 o FIPS in corrispondenza del quale deve essere supportata questa funzionalità è racchiusa tra parentesi accanto a ogni maschera di bit.  
  
 Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<aggiungere colonna > clausola è supportata, con funzionalità per specificare regole di confronto colonna (livello completo) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<aggiungere colonna > clausola è supportata, con possibilità di specificare i valori predefiniti delle colonne (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<aggiungere colonna > è supportato (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<aggiungere colonna > clausola è supportata, con funzionalità per specificare i vincoli di colonna (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<Aggiungi vincolo di tabella > clausola è supportata (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<definizione di vincolo nome > è supportato per la denominazione dei vincoli di colonna e tabella (livello intermedio) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<eliminare la colonna > è supportato in serie (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<modificare la colonna > \<clausola default di rilascio colonna > è supportato (livello intermedio) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<eliminare la colonna > è supportato RESTRICT (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<eliminare la colonna > è supportato RESTRICT (livello FIPS transizione) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<modificare la colonna > \<clausola default di set di colonna > è supportato (livello intermedio) (ODBC 3.0)  
  
 Il supporto di specificare i bit seguenti \<attributi vincolo > Se è consentito specificare vincoli di colonna o una tabella (è impostato il bit SQL_AT_ADD_CONSTRAINT):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (livello completo) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (livello completo) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (livello completo) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (livello completo) (ODBC 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 Valore SQLUINTEGER che indica il livello di supporto asincrono nel driver:  
  
 SQL_AM_CONNECTION = connessione è supportata l'esecuzione asincrona di livello. Tutti gli handle di istruzione associati all'handle di connessione sono in modalità asincrona o tutti sono in modalità sincrona. Un handle di istruzione su una connessione non può essere in modalità asincrona, mentre un altro handle di istruzione nella stessa connessione è in modalità sincrona e viceversa.  
  
 SQL_AM_STATEMENT = è supportata l'esecuzione asincrona di livello di istruzione. Alcuni handle di istruzione associati a un handle di connessione possono essere in modalità asincrona, mentre altri handle di istruzione nella stessa connessione sono in modalità sincrona.  
  
 SQL_AM_NONE = asincrono in modalità non è supportata.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Maschera di bit SQLUINTEGER enumerazione il comportamento del driver rispetto alla disponibilità della riga di conteggi. Le maschere di bit seguenti vengono utilizzate insieme al tipo di informazioni:  
  
 SQL_BRC_ROLLED_UP = i conteggi delle righe delle istruzioni INSERT, DELETE o UPDATE consecutive vengono raggruppate in una sola. Se questo bit non è impostato, i conteggi delle righe sono disponibili per ogni istruzione.  
  
 SQL_BRC_PROCEDURES = i conteggi delle righe, se presente, sono disponibili quando un batch viene eseguito in una stored procedure. Se sono disponibili i conteggi delle righe, è possibile eseguire il rollback verso l'alto o singolarmente disponibile, a seconda di bit SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = i conteggi delle righe, se presente, sono disponibili quando un batch viene eseguito chiamando direttamente **SQLExecute** o **SQLExecDirect**. Se sono disponibili i conteggi delle righe, è possibile eseguire il rollback verso l'alto o singolarmente disponibile, a seconda di bit SQL_BRC_ROLLED_UP.  
  
## <a name="example"></a>Esempio  
 **SQLGetInfo** restituisce gli elenchi delle opzioni supportate come maschera di bit SQLUINTEGER in **InfoValuePtr*. La maschera di bit per ogni opzione viene utilizzata con il flag per determinare se l'opzione è supportata.  
  
 Ad esempio, un'applicazione può utilizzare il codice seguente per determinare se la funzione scalare SUBSTRING è supportata dal driver associato alla connessione.  
  
 Per un altro esempio di utilizzo **SQLGetInfo**, vedere [funzione SQLTables](../../../odbc/reference/syntax/sqltables-function.md).  
  
```  
SQLUINTEGER fFuncs;  
  
SQLGetInfo(hdbc,   
           SQL_STRING_FUNCTIONS,  
           (SQLPOINTER)&fFuncs,  
           sizeof(fFuncs),  
           NULL);  
  
// SUBSTRING supported  
if (fFuncs & SQL_FN_STR_SUBSTRING)   
   ;   // do something  
  
// SUBSTRING not supported  
else  
   ;   // do something else  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
 Restituisce l'impostazione di un attributo di connessione  
 [Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Determinare se un driver supporta la funzione  
 [Funzione SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Restituisce l'impostazione di un attributo di istruzione  
 [Funzione SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Restituzione di informazioni sui tipi di dati di un'origine dati  
 [Funzione SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
