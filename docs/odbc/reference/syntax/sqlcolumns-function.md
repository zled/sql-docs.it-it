---
title: Funzione SQLColumns | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9686336403da750a01610518d37ff60dcc2df80d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolumns-function"></a>Funzione SQLColumns
**Conformità**  
 Versione è stato introdotto: Conformità di 1.0 standard ODBC: Open Group  
  
 **Riepilogo**  
 **SQLColumns** restituisce l'elenco di nomi di colonna nelle tabelle specificate. Il driver restituisce queste informazioni come set di risultati sull'oggetto specificato *StatementHandle*.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLColumns(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      ColumnName,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *CatalogName*  
 [Input] Nome del catalogo. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispone di cataloghi. *CatalogName* non può contenere un criterio di ricerca di stringa.  
  
> [!NOTE]  
>  Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *CatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *CatalogName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Input] Lunghezza in caratteri del **CatalogName*.  
  
 *NomeSchema*  
 [Input] Stringa criterio di ricerca per i nomi degli schemi. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispongono di schemi.  
  
> [!NOTE]  
>  Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *SchemaName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *SchemaName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength2*  
 [Input] Lunghezza in caratteri del **SchemaName*.  
  
 *TableName*  
 [Input] Criterio di ricerca per i nomi delle tabelle di stringhe.  
  
> [!NOTE]  
>  Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *TableName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *TableName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength3*  
 [Input] Lunghezza in caratteri del **TableName*.  
  
 *ColumnName*  
 [Input] Stringa criterio di ricerca per i nomi di colonna.  
  
> [!NOTE]  
>  Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *ColumnName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *ColumnName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength4*  
 [Input] Lunghezza in caratteri del **ColumnName*.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLColumns** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLColumns** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle* ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|L'attributo di istruzione SQL_ATTR_METADATA_ID è stato impostato su SQL_TRUE, il *CatalogName* argomento è un puntatore null e il SQL_CATALOG_NAME *InfoType* restituisce i nomi di catalogo sono supportati.<br /><br /> (DM) a cui è stato impostato su SQL_TRUE, l'attributo di istruzione SQL_ATTR_METADATA_ID e *SchemaName*, *TableName*, o *ColumnName* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLColumns** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore di uno degli argomenti nome di lunghezza è minore di 0 ma non uguale a SQL_NTS.|  
|||Il valore di uno degli argomenti nome di lunghezza supera il valore di lunghezza massima per il catalogo corrispondente o il nome. La lunghezza massima di ogni catalogo o il nome può essere ottenuta chiamando **SQLGetInfo** con il *InfoType* valori. (Vedere "Commenti".)|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|È stato specificato un nome di catalogo e del driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato un nome di schema e del driver o l'origine dati non supporta schemi.<br /><br /> Un criterio di ricerca della stringa è stato specificato per il nome dello schema, un nome della tabella o un nome di colonna e l'origine dati non supporta i criteri di ricerca per uno o più di questi argomenti.<br /><br /> La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene in genere utilizzata prima dell'esecuzione di istruzione per recuperare informazioni sulle colonne per una o più tabelle dal catalogo dell'origine dati. **SQLColumns** può essere utilizzato per recuperare i dati per tutti i tipi di elementi restituiti dalla **SQLTables**. Oltre alle tabelle di base, questo può includere (ma non è limitato a) viste, sinonimi, tabelle di sistema e così via. Al contrario, le funzioni **SQLColAttribute** e **SQLDescribeCol** vengono descritte le colonne in un set di risultati e la funzione **SQLNumResultCols** restituisce il numero di colonne in un set di risultati. Per ulteriori informazioni, vedere [utilizza dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** restituisce i risultati come set di risultati standard, ordinati in base TABLE_CAT, TABLE_SCHEM, TABLE_NAME e ORDINAL_POSITION.  
  
> [!NOTE]  
>  Quando un'applicazione funziona con un'API ODBC 2. *x* driver, non esiste una colonna ORDINAL_POSITION viene restituita nel set di risultati. Di conseguenza, quando si lavora con ODBC 2. *x* driver, l'ordine delle colonne nell'elenco di colonne restituito da **SQLColumns** non viene necessariamente lo stesso ordine delle colonne restituito quando l'applicazione esegue un'istruzione SELECT su tutti colonne della tabella.  
  
> [!NOTE]  
>  **SQLColumns** potrebbe non restituire tutte le colonne. Ad esempio, un driver potrebbe non restituire informazioni sulle colonne pseudo, ad esempio Oracle ROWID. Le applicazioni possono utilizzare qualsiasi colonna valida, se viene restituito da **SQLColumns**.  
>   
>  Alcune colonne che possono essere restituiti da **SQLStatistics** non vengono restituiti da **SQLColumns**. Ad esempio, **SQLColumns** non restituisce le colonne in un indice creato in un'espressione o un filtro, ad esempio stipendio + vantaggi o DEPT = 0012.  
  
 La lunghezza delle colonne VARCHAR non viene visualizzata nella tabella. le lunghezze effettivi variano a seconda dell'origine dati. Per determinare la lunghezza effettiva delle colonne TABLE_CAT, TABLE_SCHEM, TABLE_NAME e COLUMN_NAME, un'applicazione può chiamare **SQLGetInfo** con SQL_MAX_CATALOG_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, e le opzioni di SQL_MAX_COLUMN_NAME_LEN.  
  
 Le colonne seguenti sono state rinominate per ODBC 3. *x*. Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3. *x* colonna|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Le colonne seguenti sono stati aggiunti al set di risultati restituito da **SQLColumns** per ODBC 3. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre colonna 18 (IS_NULLABLE) dal driver. Un'applicazione deve accedere a colonne specifiche del driver contando dalla fine del gruppo di risultati anziché specificare una posizione ordinale esplicita verso il basso. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Colonna<br /><br /> number|Tipo di dati|Commenti|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Nome di catalogo. NULL se non è applicabile all'origine dati. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di cataloghi.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Nome dello schema. NULL se non è applicabile all'origine dati. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di schemi.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar non NULL|Nome della tabella.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar non NULL|Nome colonna. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|DATA_TYPE (ODBC 1.0)|5|Smallint non NULL|Tipo di dati SQL. Può trattarsi di un tipo di dati SQL ODBC o un tipo di dati specifici del driver SQL. Per i tipi di dati datetime e interval, questa colonna restituisce il tipo di dati conciso (ad esempio SQL_TYPE_DATE o SQL_INTERVAL_YEAR_TO_MONTH, anziché il tipo di dati nonconcise, ad esempio SQL_DATETIME o SQL_INTERVAL). Per un elenco dei tipi di dati ODBC SQL validi, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) appendice d: tipo di dati. Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.<br /><br /> I tipi di dati restituiti per ODBC 3. *x* e ODBC 2. *x* applicazioni potrebbero essere diverse. Per ulteriori informazioni, vedere [compatibilità e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|TYPE_NAME (ODBC 1.0)|6|Varchar non NULL|Nome del tipo di dati dipende dall'origine dati; ad esempio, "CHAR", "VARCHAR", "MONEY", "LONG VARBINAR" o "CHAR () FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|7|Integer|Se DATA_TYPE è SQL_CHAR o SQL_VARCHAR, questa colonna contiene la lunghezza massima in caratteri della colonna. Per i tipi di dati datetime, questo è il numero totale di caratteri necessari per visualizzare il valore quando viene convertito in caratteri. Per i tipi di dati numerici, questo è il numero totale di cifre o il numero totale di bit consentite nella colonna, in base alla colonna NUM_PREC_RADIX. Per i tipi di dati di intervallo, questo è il numero di caratteri nella rappresentazione di caratteri dell'intervallo di valori letterale (come definito nell'intervallo di precisione iniziale, vedere [lunghezza del tipo di dati intervallo](../../../odbc/reference/appendixes/interval-data-type-length.md) appendice d: tipo di dati). Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|BUFFER_LENGTH (ODBC 1.0)|8|Integer|La lunghezza in byte dei dati trasferiti durante un'operazione SQLGetData, SQLFetch o SQLFetchScroll se si specifica SQL_C_DEFAULT. Per i dati numerici, queste dimensioni potrebbero differire dalle dimensioni dei dati archiviati nell'origine dati. Questo valore potrebbe essere diverso dalla colonna COLUMN_SIZE per dati di tipo carattere. Per ulteriori informazioni sulla lunghezza, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|Numero totale di cifre a destra del separatore decimale. Per SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP, questa colonna contiene il numero di cifre nel componente di secondi frazionari. Per altri tipi di dati, si tratta di cifre decimali della colonna nell'origine dati. Per i tipi di dati di intervallo che contengono un componente di ora, questa colonna contiene il numero di cifre a destra del separatore decimale (secondi frazionari). Per i tipi di dati di intervallo che non contengono un componente della fase, questa colonna è 0. Per ulteriori informazioni su cifre decimali, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati. Viene restituito NULL per i tipi di dati in cui non è applicabile DECIMAL_DIGITS.|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|Per i tipi di dati numerici, 10 o 2. Se è 10, i valori COLUMN_SIZE e DECIMAL_DIGITS fornire il numero di cifre consentito per la colonna. Ad esempio, una colonna DECIMAL(12,5) restituirebbe un NUM_PREC_RADIX di 10, un valore di COLUMN_SIZE 12 e un DECIMAL_DIGITS 5; una colonna di tipo FLOAT può restituire un NUM_PREC_RADIX di 10, un valore di COLUMN_SIZE 15 e DECIMAL_DIGITS NULL.<br /><br /> Se è 2, i valori COLUMN_SIZE e DECIMAL_DIGITS fornire il numero di bit consentite nella colonna. Ad esempio, una colonna di tipo FLOAT potrebbe restituire una radice pari a 2, un valore di COLUMN_SIZE di 53 e DECIMAL_DIGITS NULL.<br /><br /> Viene restituito NULL per i tipi di dati in cui non è applicabile NUM_PREC_RADIX.|  
|NULLABLE (ODBC 1.0)|11|Smallint non NULL|SQL_NO_NULLS se la colonna non può includere valori NULL.<br /><br /> SQL_NULLABLE se la colonna accetta valori NULL.<br /><br /> SQL_NULLABLE_UNKNOWN se non è noto se la colonna accetta valori NULL.<br /><br /> Il valore restituito per questa colonna è diverso dal valore restituito per la colonna IS_NULLABLE. La colonna ammette valori null indica con certezza che una colonna può accettare valori null, ma non è possibile specificare con certezza che una colonna non accetta valori null. La colonna IS_NULLABLE indica con certezza che una colonna non può accettare valori null, ma non è possibile specificare con certezza che una colonna accetta valori null.|  
|SEZIONE OSSERVAZIONI (ODBC 1.0)|12|Varchar|Descrizione della colonna.|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|Valore predefinito della colonna. Il valore di questa colonna deve essere interpretato come una stringa, se sia racchiuso tra virgolette.<br /><br /> Se è stato specificato NULL come valore predefinito, questa colonna è la parola NULL, non è racchiuso tra virgolette. Se il valore predefinito non può essere rappresentato senza troncamento, questa colonna contiene troncati, senza che li racchiude tra virgolette singole. Se è stato specificato alcun valore predefinito, questa colonna è NULL.<br /><br /> Il valore di COLUMN_DEF può essere utilizzato per la generazione di una nuova definizione di colonna, tranne quando contiene il valore troncati.|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint non NULL|Tipo di dati SQL, così come viene visualizzato nel campo SQL_DESC_TYPE nell'implementazione. Può trattarsi di un tipo di dati SQL ODBC o un tipo di dati specifici del driver SQL. Questa colonna corrisponde alla colonna DATA_TYPE, tranne i tipi di dati datetime e interval. Questa colonna restituisce il tipo di dati nonconcise (ad esempio SQL_DATETIME o SQL_INTERVAL), anziché conciso tipo di dati (ad esempio SQL_TYPE_DATE o SQL_INTERVAL_YEAR_TO_MONTH) per datetime e i tipi di dati di intervallo. Se questa colonna restituisce SQL_DATETIME o SQL_INTERVAL, è possibile determinare il tipo di dati specifico dalla colonna SQL_DATETIME_SUB. Per un elenco dei tipi di dati ODBC SQL validi, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) appendice d: tipo di dati. Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.<br /><br /> I tipi di dati restituiti per ODBC 3. *x* e ODBC 2. *x* applicazioni potrebbero essere diverse. Per ulteriori informazioni, vedere [compatibilità e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Il codice di sottotipo per i tipi di dati datetime e interval. Per gli altri tipi di dati in questa colonna viene restituito NULL. Per ulteriori informazioni su data/ora e intervallo di codici secondari, vedere "SQL_DESC_DATETIME_INTERVAL_CODE" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Integer|La lunghezza massima in byte di un carattere o dati binari di colonna di tipo. Per gli tutti gli altri tipi di dati, il valore di questa colonna è NULL.|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer non NULL|Posizione ordinale della colonna nella tabella. La prima colonna nella tabella è pari al numerica 1.|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|"NO" se la colonna non ammette valori null.<br /><br /> "YES" se la colonna può includere valori null.<br /><br /> Quando non è noto se i valori Null sono supportati, in questa colonna viene restituita una stringa di lunghezza zero.<br /><br /> Per determinare il supporto di valori Null vengono seguite le regole ISO. Un DBMS conforme a ISO SQL non può restituire una stringa vuota.<br /><br /> Il valore restituito per questa colonna è diverso dal valore restituito per la colonna ammette valori null. (Vedere la descrizione della colonna che ammette valori null).|  
  
## <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione dichiara i buffer per il set di risultati restituito da **SQLColumns**. Chiama **SQLColumns** per restituire un set di risultati che descrivono ogni colonna della tabella EMPLOYEE. Chiama quindi **SQLBindCol** per associare le colonne nel set di risultati come buffer. Infine, l'applicazione recupera ciascuna riga di dati con **SQLFetch** e lo elabora.  
  
```  
// SQLColumns_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
// Declare buffers for result set data  
SQLCHAR szSchema[STR_LEN];  
SQLCHAR szCatalog[STR_LEN];  
SQLCHAR szColumnName[STR_LEN];  
SQLCHAR szTableName[STR_LEN];  
SQLCHAR szTypeName[STR_LEN];  
SQLCHAR szRemarks[REM_LEN];  
SQLCHAR szColumnDefault[STR_LEN];  
SQLCHAR szIsNullable[STR_LEN];  
  
SQLINTEGER ColumnSize;  
SQLINTEGER BufferLength;  
SQLINTEGER CharOctetLength;  
SQLINTEGER OrdinalPosition;  
  
SQLSMALLINT DataType;  
SQLSMALLINT DecimalDigits;  
SQLSMALLINT NumPrecRadix;  
SQLSMALLINT Nullable;  
SQLSMALLINT SQLDataType;  
SQLSMALLINT DatetimeSubtypeCode;  
  
SQLHSTMT hstmt = NULL;  
  
// Declare buffers for bytes available to return  
SQLINTEGER cbCatalog;  
SQLINTEGER cbSchema;  
SQLINTEGER cbTableName;  
SQLINTEGER cbColumnName;  
SQLINTEGER cbDataType;  
SQLINTEGER cbTypeName;  
SQLINTEGER cbColumnSize;  
SQLLEN cbBufferLength;  
SQLINTEGER cbDecimalDigits;  
SQLINTEGER cbNumPrecRadix;  
SQLINTEGER cbNullable;  
SQLINTEGER cbRemarks;  
SQLINTEGER cbColumnDefault;  
SQLINTEGER cbSQLDataType;  
SQLINTEGER cbDatetimeSubtypeCode;  
SQLINTEGER cbCharOctetLength;  
SQLINTEGER cbOrdinalPosition;  
SQLINTEGER cbIsNullable;  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);  
  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      // Bind columns in result set to buffers  
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);  
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);  
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);  
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);  
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &DataType, 0, &cbDataType);  
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);  
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);  
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);  
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);  
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);  
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable, 0, &cbNullable);  
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &cbRemarks);  
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &cbColumnDefault);  
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);  
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode, 0, &cbDatetimeSubtypeCode);  
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &CharOctetLength, 0, &cbCharOctetLength);  
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);  
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &cbIsNullable);  
  
      while (SQL_SUCCESS == retcode) {  
         retcode = SQLFetch(hstmt);  
         /*  
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // show_error();  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // Process fetched data  
         else  
            break;  
        */  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di privilegi per una o più colonne|[Funzione SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di più righe di dati|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Restituzione di colonne che identificano in modo univoco una riga o le colonne aggiornate automaticamente da una transazione|[Funzione SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Restituzione delle statistiche delle tabelle e indici|[Funzione SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Restituzione di un elenco di tabelle in un'origine dati|[Funzione SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
|Restituzione di privilegi per una o più tabelle|[Funzione SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
