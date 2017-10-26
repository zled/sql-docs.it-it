---
title: Funzione SQLTables | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLTables
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTables
helpviewer_keywords:
- SQLTables function [ODBC]
ms.assetid: 60d5068a-7d7c-447c-acc6-f3f2cf73440c
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd6e505ee08d7162ef820c7c7c75195b3616e585
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqltables-function"></a>Funzione SQLTables
**Conformità**  
 Versione è stato introdotto: Conformità di 1.0 standard ODBC: Open Group  
  
 **Riepilogo**  
 **SQLTables** restituisce l'elenco di nomi di tabella, catalogo o schema e tipi di tabella, archiviati in un'origine dati specifica. Il driver restituisce le informazioni come set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLTables(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      TableType,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione per recuperata i risultati.  
  
 *CatalogName*  
 [Input] Nome del catalogo. Il *CatalogName* argomento accetta i criteri di ricerca se l'attributo di ambiente SQL_ODBC_VERSION SQL_OV_ODBC3; non accetta modelli di ricerca se SQL_OV_ODBC2 è impostata. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando un driver recupera i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispone di cataloghi.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *CatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *CatalogName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Input] Lunghezza in caratteri del **CatalogName*.  
  
 *NomeSchema*  
 [Input] Stringa criterio di ricerca per i nomi degli schemi. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispongono di schemi.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *SchemaName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *SchemaName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength2*  
 [Input] Lunghezza in caratteri del **SchemaName*.  
  
 *TableName*  
 [Input] Criterio di ricerca per i nomi delle tabelle di stringhe.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *TableName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *TableName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength3*  
 [Input] Lunghezza in caratteri del **TableName*.  
  
 *TableType*  
 [Input] Elenco dei tipi di tabella per trovare la corrispondenza.  
  
 Si noti che l'attributo di istruzione SQL_ATTR_METADATA_ID non ha alcun effetto durante il *TableType* argomento. *TableType* è un argomento di elenco di valore, indipendentemente dall'impostazione di SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 [Input] Lunghezza in caratteri del **TableType*.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLTables** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLTables** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|L'attributo di istruzione SQL_ATTR_METADATA_ID è stato impostato su SQL_TRUE, il *CatalogName* argomento è un puntatore null e il SQL_CATALOG_NAME *InfoType* restituisce i nomi di catalogo sono supportati.<br /><br /> (DM) a cui è stato impostato su SQL_TRUE, l'attributo di istruzione SQL_ATTR_METADATA_ID e *SchemaName* o *TableName* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando è stato chiamato SQLTables.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore di uno degli argomenti di lunghezza è minore di 0 ma non uguale a SQL_NTS.<br /><br /> Il valore di uno degli argomenti nome di lunghezza maggiore del valore di lunghezza massima per il nome corrispondente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|È stato specificato un catalogo e del driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato uno schema e del driver o l'origine dati non supporta schemi.<br /><br /> Un criterio di ricerca della stringa è stato specificato per il nome del catalogo, schema della tabella o il nome di tabella e l'origine dati non supporta i criteri di ricerca per uno o più di questi argomenti.<br /><br /> La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima origine dati ha restituito il set di risultati richiesti. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **SQLTables** Elenca tutte le tabelle nell'intervallo richiesto. Un utente può o che non disponga delle autorizzazioni SELECT per una di queste tabelle. Per controllare l'accesso facilitato, un'applicazione è possibile:  
  
-   Chiamare **SQLGetInfo** e controllare il tipo di informazioni SQL_ACCESSIBLE_TABLES.  
  
-   Chiamare **SQLTablePrivileges** per controllare i privilegi per ogni tabella.  
  
 In caso contrario, l'applicazione deve essere in grado di gestire una situazione in cui l'utente seleziona una tabella per cui **selezionare** non vengono concessi privilegi.  
  
 Il *SchemaName* e *TableName* argomenti accettano i criteri di ricerca. Il *CatalogName* argomento accetta i criteri di ricerca se l'attributo di ambiente SQL_ODBC_VERSION SQL_OV_ODBC3; non accetta modelli di ricerca se SQL_OV_ODBC2 è impostata. Se è impostato SQL_OV_ODBC3, un'applicazione ODBC 3*. x* driver richiederà di caratteri che con caratteri jolly di *CatalogName* argomento usare caratteri di escape per essere considerate letteralmente. Per ulteriori informazioni sui pattern di ricerca validi, vedere [argomenti di modello valore](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Per supportare l'enumerazione dei cataloghi, schemi e tipi di tabella, la semantica di speciale seguente venga definita per il *CatalogName*, *SchemaName*, *TableName*e * TableType* gli argomenti di **SQLTables**:  
  
-   Se *CatalogName* è SQL_ALL_CATALOGS e *SchemaName* e *TableName* sono stringhe vuote, il set di risultati contiene un elenco dei cataloghi validi per l'origine dati. (Tutte le colonne ad eccezione della colonna TABLE_CAT contengono valori null).  
  
-   Se *SchemaName* è SQL_ALL_SCHEMAS e *CatalogName* e *TableName* sono stringhe vuote, il set di risultati contiene un elenco di schemi validi per l'origine dati. (Tutte le colonne ad eccezione della colonna TABLE_SCHEM contengono valori null).  
  
-   Se *TableType* è SQL_ALL_TABLE_TYPES e *CatalogName*, *SchemaName*, e *TableName* sono stringhe vuote, il set di risultati contiene un elenco dei tipi di tabella valido per l'origine dati. (Tutte le colonne ad eccezione della colonna TABLE_TYPE contengono valori null).  
  
 Se *TableType* non è una stringa vuota, deve contenere un elenco di valori delimitati da virgole per i tipi di interesse, ogni valore possono essere racchiusi tra virgolette singole (') o non racchiusi tra virgolette, ad esempio 'TABLE', 'Visualizza' o tabella, visualizzare. Un'applicazione deve specificare sempre il tipo di tabella in maiuscole. il driver deve convertire il tipo di tabella in qualsiasi caso è necessario per l'origine dati. Se l'origine dati non supporta un tipo di tabella specificata, **SQLTables** non restituirà alcun risultato per quel tipo.  
  
 **SQLTables** restituisce i risultati come set di risultati standard, ordinati in TABLE_TYPE, TABLE_CAT, TABLE_SCHEM e TABLE_NAME. Per informazioni sulla modalità di utilizzo queste informazioni, vedere [utilizza dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Per determinare la lunghezza effettiva delle colonne di TABLE_NAME TABLE_CAT e TABLE_SCHEM, un'applicazione può chiamare **SQLGetInfo** con le informazioni SQL_MAX_CATALOG_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN e SQL_MAX_TABLE_NAME_LEN tipi.  
  
 Le colonne seguenti sono state rinominate per ODBC 3*x*. Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3*x* colonna|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre colonna 5 (note) dal driver. Un'applicazione deve accedere a colonne specifiche del driver contando dalla fine del gruppo di risultati anziché specificare una posizione ordinale esplicita verso il basso. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Numero colonna|Tipo di dati|Commenti|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nome di catalogo. NULL se non è applicabile all'origine dati. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di cataloghi.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nome dello schema. NULL se non è applicabile all'origine dati. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di schemi.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|Nome della tabella.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Nome tipo di tabella. uno dei seguenti: "TABLE", "VIEW", "Tabella di sistema", "Temporanee globali", "TEMPORANEO locale", "ALIAS", "SINONIMO" o un nome di tipo specifici dell'origine dati.<br /><br /> Il significato di "ALIAS" e "SINONIMO" è specifici del driver.|  
|SEZIONE OSSERVAZIONI (ODBC 1.0)|5|Varchar|Descrizione della tabella.|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente non libera l'handle e delle connessioni. Vedere [SQLFreeHandle-funzione](../../../odbc/reference/syntax/sqlfreehandle-function.md) e [SQLFreeStmt-funzione](../../../odbc/reference/syntax/sqlfreestmt-function.md) per esempi di codice liberare l'handle e istruzioni.  
  
```  
// SQLTables.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
// simple helper functions  
int MySQLSuccess(SQLRETURN rc) {  
   return (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO);  
}  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printCatalog(const struct DataBinding* catalogResult) {  
   if (catalogResult[0].StrLen_or_Ind != SQL_NULL_DATA)   
      printf("Catalog Name = %s\n", (char *)catalogResult[0].TargetValuePtr);  
}  
  
// remember to disconnect and free memory, and free statements and handles  
int main() {  
   int bufferSize = 1024, i, numCols = 5;  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   wchar_t* dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   wchar_t* userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR*)"Driver={SQL Server}", SQL_NTS, (SQLCHAR*)connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
  
   bufferSize = 1024;  
  
   // allocate memory for the binding  
   // free this memory when done  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // setup the binding (can be used even if the statement is closed by closeStatementHandle)  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   // all catalogs query  
   printf( "A list of names of all catalogs\n" );  
   retCode = SQLTables( hstmt, (SQLCHAR*)SQL_ALL_CATALOGS, SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS );  
   for ( retCode = SQLFetch(hstmt) ;  MySQLSuccess(retCode) ; retCode = SQLFetch(hstmt) )  
      printCatalog( catalogResult );  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di privilegi per una o più colonne|[Funzione SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Restituzione delle colonne in una o più tabelle|[Funzione SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Restituzione delle statistiche delle tabelle e indici|[Funzione SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Restituzione di privilegi per una o più tabelle|[Funzione SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

