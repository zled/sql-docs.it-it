---
title: Funzione SQLProcedureColumns | Documenti Microsoft
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
- SQLProcedureColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedureColumns
helpviewer_keywords:
- SQLProcedureColumns function [ODBC]
ms.assetid: 4ca37b28-a6df-465b-8988-d422d37fc025
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db80c3c1fbf8e4d22f09849c95dde4bc4319bedf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprocedurecolumns-function"></a>Funzione SQLProcedureColumns
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLProcedureColumns** restituisce l'elenco dei parametri di input e outpui, nonché le colonne che costituiscono il set di risultati per le procedure specificate. Il driver restituisce le informazioni come set di risultati dell'istruzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLProcedureColumns(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     ProcName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *CatalogName*  
 [Input] Nome del catalogo della routine. Se un driver supporta cataloghi per alcune procedure ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le procedure che non dispone di cataloghi. *CatalogName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *CatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *CatalogName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Input] Lunghezza in caratteri del **CatalogName*.  
  
 *NomeSchema*  
 [Input] Stringa criterio di ricerca per i nomi di schema di stored procedure. Se un driver supporta gli schemi per alcune procedure ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le procedure che non dispongono di schemi.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *SchemaName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *SchemaName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength2*  
 [Input] Lunghezza in caratteri del **SchemaName*.  
  
 *ProcName*  
 [Input] Stringa criterio di ricerca per i nomi delle procedure.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *ProcName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *ProcName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength3*  
 [Input] Lunghezza in caratteri del **ProcName*.  
  
 *Nome colonna*  
 [Input] Stringa criterio di ricerca per i nomi di colonna.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *ColumnName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *ColumnName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength4*  
 [Input] Lunghezza in caratteri del **ColumnName*.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLProcedureColumns** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLProcedureColumns** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti dal Driver Manager. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLError** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|L'attributo di istruzione SQL_ATTR_METADATA_ID è stato impostato su SQL_TRUE, il *CatalogName* argomento è un puntatore null e il SQL_CATALOG_NAME *InfoType* restituisce i nomi di catalogo sono supportati.<br /><br /> (DM) a cui è stato impostato su SQL_TRUE, l'attributo di istruzione SQL_ATTR_METADATA_ID e *SchemaName*, *ProcName*, o *ColumnName* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione aynschronous era ancora in esecuzione quando è stata chiamata la funzione SQLProcedureColumns.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore di uno degli argomenti nome di lunghezza è minore di 0 ma non uguale a SQL_NTS.<br /><br /> Il valore di uno degli argomenti nome di lunghezza supera il valore di lunghezza massima per il catalogo corrispondente, schema, stored procedure o nome di colonna.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|È stato specificato un catalogo di stored procedure e il driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato uno schema di stored procedure e il driver o l'origine dati non supporta schemi.<br /><br /> Un criterio di ricerca della stringa è stato specificato per lo schema di stored procedure, nome della stored procedure o nome di colonna e l'origine dati non supporta i criteri di ricerca per uno o più di questi argomenti.<br /><br /> La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene in genere utilizzata prima dell'esecuzione di istruzione per recuperare informazioni sui parametri di stored procedure e le colonne che costituiscono il set di risultati o i set restituiti dalla procedura, se presente. Per ulteriori informazioni, vedere [procedure](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  **SQLProcedureColumns** potrebbe non restituire tutte le colonne utilizzate da una stored procedure. Ad esempio, un driver potrebbe restituire solo le informazioni sui parametri utilizzati da una stored procedure e non le colonne in un set di risultati che viene generato.  
  
 Il *SchemaName*, *ProcName*, e *ColumnName* argomenti accettano i criteri di ricerca. Per ulteriori informazioni sui pattern di ricerca validi, vedere [argomenti di modello valore](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedureColumns** restituisce i risultati come set di risultati standard, ordinati in base PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME e COLUMN_TYPE. Vengono restituiti i nomi di colonna per ogni procedura nell'ordine seguente: il nome del valore restituito, i nomi di ogni parametro nella chiamata di procedura (in ordine di chiamata) e i nomi di ogni colonna nel set di risultati restituito dalla routine (nell'ordine delle colonne).  
  
 Le applicazioni devono essere associati a colonne specifiche del driver relativo alla fine del set di risultati. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
 Per determinare la lunghezza effettiva delle colonne PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME e COLUMN_NAME, un'applicazione può chiamare **SQLGetInfo** con il SQL_MAX_ SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, PROCEDURE_NAME_LEN e SQL_MAX_COLUMN_NAME_LEN opzioni.  
  
 Le colonne seguenti sono state rinominate per ODBC 3. *x*. Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3. *x* colonna|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|PROCEDURA _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Le colonne seguenti sono stati aggiunti al set di risultati restituito da **SQLProcedureColumns** per ODBC 3.* x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre colonna 19 (IS_NULLABLE) dal driver. Un'applicazione deve accedere a colonne specifiche del driver rovescia dalla fine del set di risultati, anziché specificare una posizione ordinale esplicita. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Numero colonna|Tipo di dati|Commenti|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|Nome del catalogo della procedura. NULL se non è applicabile all'origine dati. Se un driver supporta cataloghi per alcune procedure ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per tutte le procedure che non dispone di cataloghi.|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|Nome dello schema della procedura. NULL se non è applicabile all'origine dati. Se un driver supporta gli schemi per alcune procedure ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per tutte le procedure che non dispongono di schemi.|  
|PROCEDURE_NAME (ODBC 2.0)|3|Varchar non NULL|Nome della procedura. Per una procedura che non dispone di un nome, viene restituita una stringa vuota.|  
|COLUMN_NAME (ODBC 2.0)|4|Varchar non NULL|Nome colonna della procedura. Il driver restituisce una stringa vuota per una colonna di procedure che non dispone di un nome.|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint non NULL|Definisce la colonna di stored procedure come parametro o una colonna del set di risultati:<br /><br /> SQL_PARAM_TYPE_UNKNOWN: Colonna della procedura è un parametro il cui tipo è sconosciuto. ODBC (1.0)<br /><br /> SQL_PARAM_INPUT: La colonna di stored procedure è un parametro di input. ODBC (1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT: La colonna di stored procedure è un parametro di input/output. ODBC (1.0)<br /><br /> SQL_PARAM_OUTPUT: La colonna di stored procedure è un parametro di output. (ODBC 2.0)<br /><br /> SQL_RETURN_VALUE: La colonna di stored procedure è il valore restituito della procedura. (ODBC 2.0)<br /><br /> SQL_RESULT_COL: La colonna di stored procedure è una colonna del set di risultati. ODBC (1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint non NULL|Tipo di dati SQL. Può trattarsi di un tipo di dati SQL ODBC o un tipo di dati specifici del driver SQL. Per i tipi di dati datetime e interval, questa colonna restituisce i tipi di dati conciso (ad esempio, SQL_TYPE_TIME o SQL_INTERVAL_YEAR_TO_MONTH). Per un elenco dei tipi di dati ODBC SQL validi, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) appendice d: tipo di dati. Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.|  
|TYPE_NAME (ODBC 2.0)|7|Varchar non NULL|Nome del tipo di dati dipende dall'origine dati; ad esempio, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" o "CHAR () FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 2.0)|8|Valore intero|Le dimensioni di colonna della colonna della procedura nell'origine dati. Viene restituito NULL per i tipi di dati in dimensioni di colonna non sono applicabile. Per ulteriori informazioni sulle precisione, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|BUFFER_LENGTH (ODBC 2.0)|9|Valore intero|La lunghezza in byte di dati trasferiti in un **SQLGetData** o **SQLFetch** operazione se si specifica SQL_C_DEFAULT. Per dati numerici, questa dimensione può essere diversa rispetto alle dimensioni dei dati archiviati nell'origine dati. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md), nell'appendice d: i tipi di dati.|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|Le cifre decimali della colonna della procedura nell'origine dati. Viene restituito NULL per i tipi di dati in cui non sono applicabile cifre decimali. Per ulteriori informazioni sulle cifre decimali, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md), nell'appendice d: i tipi di dati.|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|Per i tipi di dati numerici, 10 o 2.<br /><br /> Se è 10, i valori COLUMN_SIZE e DECIMAL_DIGITS assegnare il numero di cifre consentito per la colonna. Ad esempio, una colonna DECIMAL(12,5) restituirebbe un NUM_PREC_RADIX di 10, un valore di COLUMN_SIZE 12 e un DECIMAL_DIGITS 5; una colonna di tipo FLOAT può restituire un NUM_PREC_RADIX di 10, un valore di COLUMN_SIZE 15 e DECIMAL_DIGITS NULL.<br /><br /> Se è 2, i valori COLUMN_SIZE e DECIMAL_DIGITS assegnare il numero di bit consentite nella colonna. Ad esempio, una colonna di tipo FLOAT potrebbe restituire un NUM_PREC_RADIX 2, un valore di COLUMN_SIZE di 53 e DECIMAL_DIGITS NULL.<br /><br /> Viene restituito NULL per i tipi di dati in cui non è applicabile NUM_PREC_RADIX.|  
|NULLABLE (ODBC 2.0)|12|Smallint non NULL|Se la colonna di stored procedure accetta un valore NULL:<br /><br /> SQL_NO_NULLS: La colonna di routine non accetta valori NULL.<br /><br /> SQL_NULLABLE: Colonna della procedura accetta valori NULL.<br /><br /> SQL_NULLABLE_UNKNOWN: Non è noto se la colonna procedura accetta valori NULL.|  
|SEZIONE OSSERVAZIONI (ODBC 2.0)|13|Varchar|Descrizione della colonna della procedura.|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|Valore predefinito della colonna.<br /><br /> Se è stato specificato NULL come valore predefinito, questa colonna è la parola NULL, non è racchiuso tra virgolette. Se il valore predefinito non può essere rappresentato senza troncamento, questa colonna contiene troncati, con nessuna inclusione tra virgolette singole. Se è stato specificato alcun valore predefinito, questa colonna è NULL.<br /><br /> Il valore di COLUMN_DEF può essere utilizzato per la generazione di una nuova definizione di colonna, tranne quando contiene il valore troncati.|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint non NULL|Il valore del tipo di dati SQL come viene visualizzato nel campo SQL_DESC_TYPE del descrittore. Questa colonna corrisponde alla colonna DATA_TYPE, tranne i tipi di dati datetime e interval.<br /><br /> Per i tipi di dati datetime e interval, il campo SQL_DATA_TYPE nel set di risultati restituirà SQL_INTERVAL o SQL_DATETIME e il campo SQL_DATETIME_SUB restituirà il codice secondario per il tipo di dati di intervallo o data/ora specifico. (Vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|Il codice di sottotipo per i tipi di dati datetime e interval. Per gli altri tipi di dati in questa colonna viene restituito NULL.|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Valore intero|La lunghezza massima in byte di un carattere o dati binari di colonna di tipo. Per gli tutti gli altri tipi di dati, il valore di questa colonna è NULL.|  
|ORDINAL_POSITION (ODBC 3.0)|18|Integer non NULL|Per i parametri inpui e outpui, la posizione ordinale del parametro nella definizione della routine (parametro in ordine crescente in, a partire da 1). Per un valore restituito (se presente), viene restituito 0. Per le colonne di set di risultati, imposta la posizione ordinale della colonna nel risultato, con la prima colonna nel corso di set di risultati numero 1. Se sono presenti più set di risultati, vengono restituite le posizioni ordinali di colonna in modo specifico del driver.|  
|IS_NULLABLE (ODBC 3.0)|19|Varchar|"NO" se la colonna non ammette valori null.<br /><br /> "YES" se la colonna può includere valori null.<br /><br /> Quando non è noto se i valori Null sono supportati, in questa colonna viene restituita una stringa di lunghezza zero.<br /><br /> Per determinare il supporto di valori Null vengono seguite le regole ISO. Un DBMS conforme a ISO SQL non può restituire una stringa vuota.<br /><br /> Il valore restituito per questa colonna è diverso dal valore restituito per la colonna NULLABLE. (Vedere la descrizione della colonna che ammette valori null).|  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [chiamate di procedura](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Restituzione di un elenco di procedure in un'origine dati|[Funzione SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
