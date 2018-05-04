---
title: Sqlcolumnprivileges-funzione | Documenti Microsoft
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
- SQLColumnPrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumnPrivileges
helpviewer_keywords:
- SQLColumnPrivileges function [ODBC]
ms.assetid: ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f13f898beac2336942c0e8b44a0be8ad5037a55
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolumnprivileges-function"></a>SQLColumnPrivileges Function
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLColumnPrivileges** restituisce un elenco di colonne e i privilegi associati per la tabella specificata. Il driver restituisce le informazioni come set di risultati sull'oggetto specificato *StatementHandle*.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLColumnPrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *CatalogName*  
 [Input] Nome del catalogo. Se un driver supporta i nomi per alcuni cataloghi ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica i cataloghi che non dispongono di nomi. *CatalogName* non può contenere un criterio di ricerca di stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *CatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *CatalogName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Input] Lunghezza in caratteri del **CatalogName*.  
  
 *NomeSchema*  
 [Input] Nome dello schema. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispongono di schemi. *NomeSchema* non può contenere un criterio di ricerca di stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *SchemaName* viene considerato come un identificatore. Se è SQL_FALSE, *SchemaName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength2*  
 [Input] Lunghezza in caratteri del **SchemaName*.  
  
 *TableName*  
 [Input] Nome della tabella. Questo argomento non può essere un puntatore null. *TableName* non può contenere un criterio di ricerca di stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *TableName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *TableName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength3*  
 [Input] Lunghezza in caratteri del **TableName*.  
  
 *ColumnName*  
 [Input] Stringa criterio di ricerca per i nomi di colonna.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *ColumnName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *ColumnName* è un argomento di valore modello; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength4*  
 [Input] Lunghezza in caratteri del **ColumnName*.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLColumnPrivileges** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLColumnPrivileges** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti dal Driver Manager. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle,* e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|Il *TableName* argomento è un puntatore null.<br /><br /> L'attributo di istruzione SQL_ATTR_METADATA_ID è stato impostato su SQL_TRUE, il *CatalogName* argomento è un puntatore null e il SQL_CATALOG_NAME *InfoType* restituisce i nomi di catalogo sono supportati.<br /><br /> (DM) a cui è stato impostato su SQL_TRUE, l'attributo di istruzione SQL_ATTR_METADATA_ID e *SchemaName* o *ColumnName* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore di uno degli argomenti nome di lunghezza è minore di 0 ma non uguale a SQL_NTS.|  
|||Il valore di uno degli argomenti nome di lunghezza maggiore del valore di lunghezza massima per il nome corrispondente. (Vedere "Commenti".)|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|È stato specificato un nome di catalogo e del driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato un nome di schema e del driver o l'origine dati non supporta schemi.<br /><br /> Un criterio di ricerca della stringa è stato specificato per il nome della colonna e l'origine dati non supporta i criteri di ricerca per l'argomento.<br /><br /> La combinazione delle impostazioni correnti degli attributi di istruzione SQL_CONCURRENCY e SQL_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 **SQLColumnPrivileges** restituisce i risultati come set di risultati standard, ordinati in base TABLE_CAT TABLE_SCHEM, TABLE_NAME, COLUMN_NAME e privilegi.  
  
> [!NOTE]  
>  **SQLColumnPrivileges** potrebbe non restituire i privilegi per tutte le colonne. Ad esempio, un driver potrebbe non restituire informazioni sui privilegi per pseudo-colonne, ad esempio Oracle ROWID. Le applicazioni possono utilizzare qualsiasi colonna valida, indipendentemente dal fatto se viene restituito da **SQLColumnPrivileges**.  
  
 La lunghezza delle colonne VARCHAR non viene visualizzata nella tabella. le lunghezze effettivi variano a seconda dell'origine dati. Per determinare la lunghezza effettiva delle colonne CATALOG_NAME, SCHEMA_NAME, TABLE_NAME e COLUMN_NAME, un'applicazione può chiamare **SQLGetInfo** con il SQL_MAX_TABLE_NAME_ SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, LEN e SQL_MAX_COLUMN_NAME_LEN opzioni.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Le colonne seguenti sono state rinominate per ODBC 3. *x*. Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3. *x* colonna|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre la colonna 8 (IS_GRANTABLE) dal driver. Un'applicazione deve accedere a colonne specifiche del driver rovescia dalla fine del set di risultati, anziché specificare una posizione ordinale esplicita. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Numero colonna|Tipo di dati|Commenti|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Identificatore del catalogo. NULL se non è applicabile all'origine dati. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di cataloghi.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Identificatore di schema. NULL se non è applicabile all'origine dati. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di schemi.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar non NULL|Identificatore di tabella.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar non NULL|Nome colonna. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|GRANTOR (ODBC 1.0)|5|Varchar|Nome dell'utente che ha concesso il privilegio; NULL se non è applicabile all'origine dati.<br /><br /> Per tutte le righe in cui il valore nella colonna utente autorizzato è il proprietario dell'oggetto, la colonna GRANTOR sarà "_SYSTEM".|  
|UTENTE AUTORIZZATO (ODBC 1.0)|6|Varchar non NULL|Nome dell'utente a cui è stato concesso il privilegio.|  
|PRIVILEGIO (ODBC 1.0)|7|Varchar non NULL|Identifica il privilegio di colonna. Può essere uno dei seguenti (o altri supportati dai dati di origine quando definito dall'implementazione):<br /><br /> Selezionare: L'utente autorizzato è consentito recuperare i dati per la colonna.<br /><br /> Inserisci: L'utente autorizzato è consentito per fornire dati per la colonna in nuove righe inserite nella tabella associata.<br /><br /> AGGIORNAMENTO: L'utente autorizzato è consentito aggiornare i dati nella colonna.<br /><br /> RIFERIMENTI: L'utente autorizzato è consentito fare riferimento alla colonna all'interno di un vincolo (ad esempio, un elemento univoco, referenziale, vincolo check di tabella o).|  
|IS_GRANTABLE (ODBC 1.0)|8|Varchar|Indica se l'utente autorizzato è consentito di concedere il privilegio ad altri utenti. "YES", "NO" o "NULL" se sconosciuto o non applicabile all'origine dati.<br /><br /> Privilegio è la che è possibile concedere o che non è possibile concedere, ma non entrambi. Il set di risultati restituito da **SQLColumnPrivileges** mai conterrà due righe per cui tutte le colonne ad eccezione della colonna IS_GRANTABLE contengono lo stesso valore.|  
  
## <a name="code-example"></a>Esempio di codice  
 Per un esempio di codice di una funzione simile, vedere [funzione SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione delle colonne in una o più tabelle|[Funzione SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di più righe di dati|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Restituzione di privilegi per una o più tabelle|[Funzione SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
|Restituzione di un elenco di tabelle in un'origine dati|[Funzione SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
