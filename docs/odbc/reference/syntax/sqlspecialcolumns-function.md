---
title: Funzione SQLSpecialColumns | Documenti Microsoft
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
- SQLSpecialColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSpecialColumns
helpviewer_keywords:
- SQLSpecialColumns function [ODBC]
ms.assetid: bb2d9f21-bda0-4e50-a8be-f710db660034
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae814d95d376e928e2fafc323dedc14a3a532aa8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlspecialcolumns-function"></a>Funzione SQLSpecialColumns
**Conformità**  
 Versione è stato introdotto: Conformità di 1.0 standard ODBC: Open Group  
  
 **Riepilogo**  
 **SQLSpecialColumns** recupera le informazioni seguenti sulle colonne all'interno di una tabella specificata:  
  
-   Set di colonne ottimale che identifica in modo univoco una riga nella tabella.  
  
-   Colonne che vengono aggiornate automaticamente quando qualsiasi valore nella riga viene aggiornato da una transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLSpecialColumns(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   IdentifierType,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLSMALLINT   Scope,  
     SQLSMALLINT   Nullable);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *IdentifierType*  
 [Input] Tipo di colonna da restituire. Deve essere uno dei valori seguenti:  
  
 SQL_BEST_ROWID: Restituisce la colonna o ottimale set di colonne che, tramite il recupero dei valori di colonna o delle colonne, consente a qualsiasi riga della tabella specificata per essere identificato in modo univoco. Una colonna può essere una pseudo-colonna appositamente per questo scopo (come ROWID Oracle o Ingres TID) o le colonne di un indice univoco per la tabella.  
  
 SQL_ROWVER: Restituisce le colonne della tabella specificata, se presente, che vengono aggiornate automaticamente dall'origine dati quando qualsiasi valore nella riga viene aggiornato da una transazione (come SQLBase ROWID o Sybase TIMESTAMP).  
  
 *CatalogName*  
 [Input] Nome del catalogo per la tabella. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispone di cataloghi. *CatalogName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *CatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *CatalogName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Input] Lunghezza in caratteri del **CatalogName*.  
  
 *NomeSchema*  
 [Input] Nome dello schema per la tabella. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispongono di schemi. *NomeSchema* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *SchemaName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *SchemaName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength2*  
 [Input] Lunghezza in caratteri del **SchemaName*.  
  
 *TableName*  
 [Input] Nome della tabella. Questo argomento non può essere un puntatore null. *TableName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *TableName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *TableName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength3*  
 [Input] Lunghezza in caratteri del **TableName*.  
  
 *Ambito*  
 [Input] Ambito minimo richiesto per ROWID. Il valore restituito rowid possono essere di ambito più vasto. I possibili valori sono i seguenti:  
  
 SQL_SCOPE_CURROW: Il valore rowid è valido solo quando è posizionato in tale riga. Una selezione successiva in mediante rowid potrebbe non restituire una riga se la riga è stata aggiornata o eliminata da un'altra transazione.  
  
 SQL_SCOPE_TRANSACTION: Il valore rowid è valido per la durata della transazione corrente.  
  
 SQL_SCOPE_SESSION: Il valore rowid è valido per la durata della sessione (oltre i limiti delle transazioni).  
  
 *Ammette valori Null*  
 [Input] Determina se restituire le colonne speciali che possono avere un valore NULL. I possibili valori sono i seguenti:  
  
 SQL_NO_NULLS: Escludere le colonne speciali che possono avere valori NULL. Alcuni driver non è in grado di supportare SQL_NO_NULLS e questi driver restituirà un risultato vuoto impostato se SQL_NO_NULLS è stato specificato. Applicazioni devono essere preparate per il case e la richiesta SQL_NO_NULLS solo se è assolutamente necessario.  
  
 SQL_NULLABLE: Restituire colonne speciali, anche se possono avere valori NULL.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSpecialColumns** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLSpecialColumns** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|Il *TableName* argomento è un puntatore null.<br /><br /> L'attributo di istruzione SQL_ATTR_METADATA_ID è stato impostato su SQL_TRUE, il *CatalogName* argomento è un puntatore null e il SQL_CATALOG_NAME *InfoType* restituisce i nomi di catalogo sono supportati.<br /><br /> (DM) a cui è stato impostato su SQL_TRUE, l'attributo di istruzione SQL_ATTR_METADATA_ID e *SchemaName* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione era ancora in esecuzione quando **SQLSpecialColumns** è stato chiamato.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore di uno degli argomenti di lunghezza è minore di 0 ma non uguale a SQL_NTS.<br /><br /> Il valore di uno degli argomenti di lunghezza maggiore del valore di lunghezza massima per il nome corrispondente. La lunghezza massima di ogni nome può essere ottenuta chiamando **SQLGetInfo** con il *InfoType* valori: SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN o SQL_MAX_TABLE_NAME_LEN.|  
|HY097|Tipo di colonna non compreso nell'intervallo|(DM) non valido *IdentifierType* valore specificato.|  
|HY098|Tipo di ambito non compreso nell'intervallo|(DM) non valido *ambito* valore specificato.|  
|HY099|Tipo che ammette valori null non compreso nell'intervallo|(DM) non valido *Nullable* valore specificato.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|È stato specificato un catalogo e del driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato uno schema e del driver o l'origine dati non supporta schemi.<br /><br /> La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima origine dati ha restituito il set di risultati richiesti. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Quando il *IdentifierType* argomento è SQL_BEST_ROWID, **SQLSpecialColumns** restituisce le colonne che identificano in modo univoco ogni riga della tabella. Queste colonne possono sempre essere utilizzate un *elenco select* o **dove** clausola. **SQLColumns**, che viene utilizzata per restituire un'ampia gamma di informazioni sulle colonne di una tabella, non necessariamente restituire le colonne che identificano in modo univoco ogni riga o le colonne che vengono aggiornate automaticamente quando qualsiasi valore nella riga viene aggiornata da un transazione. Ad esempio, **SQLColumns** potrebbe non restituire il valore ROWID pseudo-colonna Oracle. Questo è il motivo **SQLSpecialColumns** viene utilizzata per restituire le colonne. Per ulteriori informazioni, vedere [utilizza dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Se non sono presenti colonne che identificano in modo univoco ogni riga della tabella, **SQLSpecialColumns** restituisce un set di righe e senza righe, una chiamata successiva a **SQLFetch** o **SQLFetchScroll**l'istruzione restituisce SQL_NO_DATA.  
  
 Se il *IdentifierType*, *ambito*, o *Nullable* argomenti specificano caratteristiche che non sono supportate dall'origine dati, **SQLSpecialColumns ** restituisce un set di risultati vuoto.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, il *CatalogName*, *SchemaName*, e *TableName* argomenti vengono trattati come identificatori, in modo non può essere impostato su un puntatore null in determinate situazioni. (Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).)  
  
 **SQLSpecialColumns** restituisce i risultati come set di risultati standard, ordinate dall'ambito.  
  
 Le colonne seguenti sono state rinominate per ODBC 3*x*. Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3*x* colonna|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 Per determinare la lunghezza effettiva della colonna COLUMN_NAME, un'applicazione può chiamare **SQLGetInfo** con l'opzione SQL_MAX_COLUMN_NAME_LEN.  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre la colonna 8 (PSEUDO_COLUMN) dal driver. Un'applicazione deve accedere a colonne specifiche del driver rovescia dalla fine del set di risultati, anziché specificare una posizione ordinale esplicita. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Numero colonna|Tipo di dati|Commenti|  
|-----------------|-------------------|---------------|--------------|  
|AMBITO (ODBC 1.0)|1|Smallint|Ambito effettivo ROWID. Contiene uno dei valori seguenti:<br /><br /> SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION<br /><br /> Viene restituito NULL quando *IdentifierType* è SQL_ROWVER. Per una descrizione di ogni valore, vedere la descrizione di *ambito* in "Sintassi" più indietro in questa sezione.|  
|COLUMN_NAME (ODBC 1.0)|2|Varchar non NULL|Nome colonna. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|DATA_TYPE (ODBC 1.0)|3|Smallint non NULL|Tipo di dati SQL. Può trattarsi di un tipo di dati SQL ODBC o un tipo di dati specifici del driver SQL. Per un elenco dei tipi di dati ODBC SQL validi, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md). Per informazioni sui tipi di dati specifici del driver SQL, vedere la documentazione del driver.|  
|TYPE_NAME (ODBC 1.0)|4|Varchar non NULL|Nome del tipo di dati dipende dall'origine dati; ad esempio, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" o "CHAR () FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|5|Valore intero|Le dimensioni della colonna nell'origine dati. Per ulteriori informazioni sulle dimensioni della colonna, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|BUFFER_LENGTH (ODBC 1.0)|6|Valore intero|La lunghezza in byte di dati trasferiti in un **SQLGetData** o **SQLFetch** operazione se si specifica SQL_C_DEFAULT. Per dati numerici, questa dimensione può essere diversa rispetto alle dimensioni dei dati archiviati nell'origine dati. Questo valore è lo stesso come colonna COLUMN_SIZE per dati carattere o binario. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|DECIMAL_DIGITS (ODBC 1.0)|7|Smallint|Le cifre decimali della colonna nell'origine dati. Viene restituito NULL per i tipi di dati in cui non sono applicabili cifre decimali. Per ulteriori informazioni sulle cifre decimali, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|PSEUDO_COLUMN (ODBC 2.0)|8|Smallint|Indica se la colonna è una pseudo-colonna, ad esempio Oracle ROWID:<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO **Nota:** per garantire la massima interoperabilità, Pseudocolonne non devono essere delimitate con l'identificatore di virgolette restituito da **SQLGetInfo**.|  
  
 Dopo l'applicazione recupera i valori per SQL_BEST_ROWID, l'applicazione può utilizzare questi valori per selezionare nuovamente tale riga all'interno dell'ambito definito. Il **selezionare** istruzione restituzione senza righe o una riga è garantita.  
  
 Se un'applicazione seleziona una riga in base alla colonna rowid o colonne e la riga non è disponibile, l'applicazione può presupporre che la riga è stata eliminata o che sono state modificate le colonne rowid. Non è vero il contrario: anche se non è stato modificato il valore rowid, le altre colonne nella riga sia stato modificato.  
  
 Colonne restituite per il tipo di colonna SQL_BEST_ROWID sono utili per le applicazioni che è necessario scorrere in avanti e indietro all'interno di un set di risultati per recuperare i dati più recenti da un set di righe. Le colonne ROWID sicuramente non cambia mentre è posizionato in tale riga.  
  
 Le colonne ROWID possono rimanere valide anche se il cursore non è posizionato sulla riga; l'applicazione può determinare l'ambito di colonne nel set di risultati.  
  
 Colonne restituite per il tipo di colonna SQL_ROWVER sono utili per applicazioni che richiedono la possibilità di controllare se tutte le colonne di una determinata riga sono state aggiornate, mentre la riga è stata saranno mediante rowid. Ad esempio, dopo si riseleziona una riga mediante rowid, l'applicazione può confrontare i valori nelle colonne SQL_ROWVER per recuperare solo quelli precedenti. Se il valore in una colonna SQL_ROWVER è diverso dal valore precedente, l'applicazione può avvertire l'utente che la visualizzazione dati sono stati modificati.  
  
## <a name="code-example"></a>Esempio di codice  
 Per un esempio di codice di una funzione simile, vedere [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione delle colonne in una o più tabelle|[Funzione SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|La restituzione di colonne di una chiave primaria|[Funzione SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

