---
title: Funzione SQLGetTypeInfo | Documenti Microsoft
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
apiname: SQLGetTypeInfo
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetTypeInfo
helpviewer_keywords: SQLGetTypeInfo function [ODBC]
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
caps.latest.revision: "21"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 508b89f5ff60b5cf64a03d167bf1ad4476edb734
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgettypeinfo-function"></a>Funzione SQLGetTypeInfo
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLGetTypeInfo** restituisce informazioni sui tipi di dati supportati dall'origine dati. Il driver restituisce le informazioni sotto forma di un set di risultati SQL. I tipi di dati devono essere utilizzati nelle istruzioni Data Definition Language (DDL).  
  
> [!IMPORTANT]  
>  Le applicazioni devono utilizzare i nomi dei tipi restituiti nella colonna TYPE_NAME del **SQLGetTypeInfo** set di risultati in **ALTER TABLE** e **CREATE TABLE** istruzioni. **SQLGetTypeInfo** può restituire più righe con lo stesso valore nella colonna DATA_TYPE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione per il set di risultati.  
  
 *Tipo di dati*  
 [Input] Il tipo di dati SQL. Deve essere uno dei valori di [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) sezione dell'appendice d: i tipi di dati o un tipo di dati specifici del driver SQL. SQL_ALL_TYPES specifica che devono essere restituite informazioni su tutti i tipi di dati.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetTypeInfo** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLGetTypeInfo** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Un attributo di istruzione specificata non è valido a causa di condizioni di lavoro di implementazione, in modo temporaneamente con cui sostituire un valore analogo. (Chiamare **SQLGetStmtAttr** per determinare il valore di sostituzione temporaneamente.) Il valore di sostituzione è valido per il *StatementHandle* fino a quando il cursore è chiuso. Gli attributi di istruzione che può essere modificato: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT e SQL_ATTR_SIMULATE_CURSOR. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle,* e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> È stato aperto in un set di risultati di *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY004|Tipo di dati SQL non valido|Il valore specificato per l'argomento *DataType* è un identificatore di tipo di dati SQL ODBC valido né un identificatore di tipo di dati specifici del driver supportata dal driver.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*, quindi è stata chiamata la funzione e, prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> È stata chiamata la funzione e, prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLGetTypeInfo** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver corrispondente il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **SQLGetTypeInfo** restituisce i risultati come set di risultati standard, ordinati in base a DATA_TYPE e quindi al precisione il tipo di dati esegue il mapping al tipo di dati SQL ODBC corrispondente. Tipi di dati definiti dall'origine dati hanno la precedenza su tipi di dati definito dall'utente. Di conseguenza, l'ordinamento non è necessariamente coerenza, ma può essere generalizzato come DATA_TYPE prima, seguito da TYPE_NAME, entrambi crescente. Ad esempio, si supponga che tipi di dati INTEGER e contatore, contatore, in cui è a incremento automatico, è definita da un'origine dati e che un tipo di dati definito dall'utente WHOLENUM sia stato definito. Questi verrebbe restituito nell'ordine di numero intero, WHOLENUM e contatore, perché esegue il mapping da vicino ai dati SQL ODBC WHOLENUM tipo SQL_INTEGER, mentre il tipo di dati a incremento automatico, anche se supportato dall'origine dati, non è associato strettamente a un tipo di dati SQL ODBC. Per informazioni sulla modalità di utilizzo queste informazioni, vedere [istruzioni DDL](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Se il *DataType* argomento specifica un tipo di dati che è valido per la versione di ODBC supportati dal driver, ma non è supportata dal driver, quindi verrà restituito un set di risultati vuoto.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Le colonne seguenti sono state rinominate per ODBC 3. *x*. Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3. *x* colonna|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Le colonne seguenti sono stati aggiunti al set di risultati restituito da **SQLGetTypeInfo** per ODBC 3. *x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre colonna 19 (INTERVAL_PRECISION) dal driver. Un'applicazione deve accedere a colonne specifiche del driver rovescia dalla fine del set di risultati, anziché specificare una posizione ordinale esplicita. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** potrebbe non restituire tutti i tipi di dati. Ad esempio, un driver potrebbe non restituire i tipi di dati definito dall'utente. Le applicazioni possono utilizzare qualsiasi tipo di dati valido, indipendentemente dal fatto se viene restituito da **SQLGetTypeInfo**. I tipi di dati restituiti da **SQLGetTypeInfo** sono quelli supportati dall'origine dati. Essi devono essere utilizzati nelle istruzioni Data Definition Language (DDL). I driver possono restituire dati di set di risultati utilizzando tipi di dati diversi dai tipi restituiti dalla **SQLGetTypeInfo**. Nella creazione di set di risultati per una funzione di catalogo, il driver potrebbe utilizzare un tipo di dati che non è supportato dall'origine dati.  
  
|Nome colonna|colonna<br /><br /> number|Tipo di dati|Commenti|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|Varchar non NULL|Nome del tipo di dati dipende dall'origine dati. ad esempio, "Char ()", "Varchar ()", "MONEY", "LONG VARBINARY" o "CHAR () FOR BIT DATA". Le applicazioni devono utilizzare il nome specificato nel **CREATE TABLE** e **ALTER TABLE** istruzioni.|  
|DATA_TYPE (ODBC 2.0)|2|Smallint non NULL|Tipo di dati SQL. Può trattarsi di un tipo di dati SQL ODBC o un tipo di dati specifici del driver SQL. Per i tipi di dati datetime o intervallo, questa colonna restituisce il tipo di dati conciso (ad esempio SQL_TYPE_TIME o SQL_INTERVAL_YEAR_TO_MONTH). Per un elenco dei tipi di dati ODBC SQL validi, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) appendice d: tipo di dati. Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.|  
|COLUMN_SIZE (ODBC 2.0)|3|Valore intero|La dimensione massima delle colonne supportati dal server per questo tipo di dati. Per i dati numerici, è la massima precisione. Per i dati stringa, si tratta della lunghezza in caratteri. Per i tipi di dati datetime, si tratta della lunghezza in caratteri della rappresentazione di stringa (presupponendo la precisione massima consentita del componente delle frazioni di secondo). Viene restituito NULL per i tipi di dati in dimensioni di colonna non sono applicabile. Per i tipi di dati di intervallo, questo è il numero di caratteri nella rappresentazione di caratteri dell'intervallo di valori letterale (come definito in base all'intervallo iniziali precisione; vedere [lunghezza del tipo di dati intervallo](../../../odbc/reference/appendixes/interval-data-type-length.md) appendice d: tipo di dati).<br /><br /> Per ulteriori informazioni sulle dimensioni di colonna, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|:: SQLGETTYPEINFO (ODBC 2.0)|4|Varchar|Carattere o caratteri utilizzati come prefisso un valore letterale; ad esempio, una virgoletta singola (') per i tipi di dati carattere o 0x per tipi di dati binari. Viene restituito NULL per i tipi di dati in cui non è applicabile un prefisso letterale.|  
|SQL_VARCHAR (ODBC 2.0)|5|Varchar|Carattere o caratteri utilizzati per terminare un valore letterale; ad esempio, una virgoletta singola (') per i tipi di dati carattere. Viene restituito NULL per i tipi di dati in cui un suffisso letterale non è applicabile.|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|Un elenco di parole chiave, separati da virgole, corrispondente a ciascun parametro quando si utilizza il nome che viene restituito nel campo TYPE_NAME, l'applicazione può specificare tra parentesi. Le parole chiave nell'elenco possono essere uno dei seguenti: lunghezza, precisione o scala. Vengono visualizzate nell'ordine che la sintassi richiede che vengano utilizzati. Ad esempio, si sarebbe CREATE_PARAMS per decimale "precisione, scala"; CREATE_PARAMS per VARCHAR daranno "lunghezza". Viene restituito NULL se non sono presenti parametri per la definizione di tipo di dati. ad esempio INTEGER.<br /><br /> Il driver fornisce il testo CREATE_PARAMS nella lingua del paese/area geografica in cui viene utilizzato.|  
|NULLABLE (ODBC 2.0)|7|Smallint non NULL|Se il tipo di dati accetta un valore NULL:<br /><br /> SQL_NO_NULLS se il tipo di dati non accetta valori NULL.<br /><br /> SQL_NULLABLE se il tipo di dati ammette valori NULL.<br /><br /> SQL_NULLABLE_UNKNOWN se non è noto se la colonna accetta valori NULL.|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint non NULL|Indica se un tipo di dati carattere è distinzione tra maiuscole e le regole di confronto e i confronti:<br /><br /> SQL_TRUE se il tipo di dati è un tipo di dati character e tra maiuscole e minuscole.<br /><br /> SQL_FALSE se il tipo di dati non è un tipo di dati carattere o non è tra maiuscole e minuscole.|  
|ESEGUIRE RICERCHE (ODBC 2.0)|9|Smallint non NULL|Utilizzo del tipo di dati in un **dove** clausola:<br /><br /> SQL_PRED_NONE se la colonna non può essere utilizzata in un **dove** clausola. (Questo è identico al valore SQL_UNSEARCHABLE in ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR se la colonna può essere utilizzata in un **in** clausola, ma solo con il **come** predicato. (Questo è identico al valore SQL_LIKE_ONLY in ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC se la colonna può essere utilizzata in un **in** clausola con tutti gli operatori di confronto tranne **come** (confronto, il confronto quantificato, **BETWEEN**,  **DISTINCT**, **IN**, **corrispondenza**, e **UNIQUE**). (Questo è identico al valore SQL_ALL_EXCEPT_LIKE in ODBC 2. *x*.)<br /><br /> SQL_SEARCHABLE se la colonna può essere utilizzata in un **dove** clausola con qualsiasi operatore di confronto.|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|Indica se il tipo di dati è senza segno:<br /><br /> SQL_TRUE se il tipo di dati è senza segno.<br /><br /> SQL_FALSE se il tipo di dati è firmato.<br /><br /> Se l'attributo non è applicabile al tipo di dati o il tipo di dati non è numerico, viene restituito NULL.|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint non NULL|Se il tipo di dati è disponibili predefinite precisione e scala (che sono specifici dell'origine dati), ad esempio un tipo di dati money fisse:<br /><br /> SQL_TRUE se disponga di predefiniti scala e precisione fisse.<br /><br /> Precisione e scala fisse SQL_FALSE se non sono predefinite.|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|Se il tipo di dati viene incrementato automaticamente:<br /><br /> SQL_TRUE se il tipo di dati viene incrementato automaticamente.<br /><br /> SQL_FALSE se il tipo di dati non viene incrementato automaticamente.<br /><br /> Se l'attributo non è applicabile al tipo di dati o il tipo di dati non è numerico, viene restituito NULL.<br /><br /> Un'applicazione può inserire valori in una colonna con questo attributo, ma in genere non è possibile aggiornare i valori nella colonna.<br /><br /> Quando un'operazione di inserimento viene effettuata in una colonna a incremento automatico, viene inserito un valore univoco nella colonna al momento dell'inserimento. L'incremento non è definito, ma è specifici dell'origine dati. Un'applicazione non deve presupporre che una colonna a incremento automatico inizia da qualsiasi punto specifico o l'incremento di un particolare valore.|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|Versione localizzata del nome del tipo di dati dipende dall'origine dati. Se il nome localizzato non è supportato dall'origine dati, viene restituito NULL. Questo nome è destinato alla visualizzazione solo, ad esempio le finestre di dialogo.|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|Scala minima del tipo di dati nell'origine dati. Se a un tipo di dati è associata una scala fissa, le colonne MINIMUM_SCALE e MAXIMUM_SCALE contengono entrambe lo stesso valore. Ad esempio, una colonna SQL_TYPE_TIMESTAMP potrebbe disporre di una scala fissa per i secondi frazionari. Se la scala non è applicabile, viene restituito NULL. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|Scala massima del tipo di dati nell'origine dati. Se la scala non è applicabile, viene restituito NULL. Se la scala massima non viene definita separatamente nell'origine dati, ma viene invece definita come la precisione massima, questa colonna contiene lo stesso valore di colonna COLUMN_SIZE. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|SQL_DATA_TYPE (ODBC 3.0)|16|Smallint non NULL|Il valore del tipo di dati SQL come viene visualizzato nel campo SQL_DESC_TYPE del descrittore. Questa colonna corrisponde alla colonna DATA_TYPE, tranne i tipi di dati di intervallo e datetime.<br /><br /> Per i tipi di dati datetime e di intervallo, il campo SQL_DATA_TYPE nel set di risultati restituirà SQL_INTERVAL o SQL_DATETIME e il campo SQL_DATETIME_SUB restituirà il codice secondario per il tipo di dati di intervallo o data/ora specifico. (Vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|Quando il valore di SQL_DATA_TYPE è SQL_DATETIME o SQL_INTERVAL, questa colonna contiene il codice secondario datetime o intervallo. Per i tipi di dati diverso da datetime e interval, questo campo è NULL.<br /><br /> Per i tipi di dati datetime o di intervallo, il campo SQL_DATA_TYPE nel set di risultati restituirà SQL_INTERVAL o SQL_DATETIME e il campo SQL_DATETIME_SUB restituirà il codice secondario per il tipo di dati di intervallo o data/ora specifico. (Vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Valore intero|Se il tipo di dati è un tipo numerico approssimato, questa colonna contiene il valore 2 per indicare che COLUMN_SIZE specifica un numero di bit. Per i tipi numerici esatti, questa colonna contiene il valore 10 per indicare che COLUMN_SIZE specifica un numero di cifre decimali. Negli altri casi la colonna è NULL.|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|Se il tipo di dati è un tipo di dati di intervallo, questa colonna contiene il valore di precisione iniziale intervallo. (Vedere [precisione del tipo di dati di intervallo](../../../odbc/reference/appendixes/interval-data-type-precision.md) appendice d: tipo di dati.) Negli altri casi la colonna è NULL.|  
  
 Informazioni sugli attributi è possibile applicare ai tipi di dati o a colonne specifiche in un set di risultati. **SQLGetTypeInfo** restituisce informazioni sugli attributi associati a tipi di dati. **SQLColAttribute** restituisce informazioni sugli attributi associati alle colonne in un set di risultati.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su una colonna in un set di risultati|[Funzione SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Restituzione di informazioni su un'origine dati o il driver|[Funzione SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
