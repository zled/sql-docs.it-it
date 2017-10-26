---
title: Funzione SQLForeignKeys | Documenti Microsoft
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
- SQLForeignKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLForeignKeys
helpviewer_keywords:
- SQLForeignKeys function [ODBC]
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0d56fd87c4c9612fb520b1a54b9d0c2cab645223
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlforeignkeys-function"></a>Funzione SQLForeignKeys
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLForeignKeys** può restituire:  
  
-   Un elenco di chiavi esterne della tabella specificata (colonne nella tabella specificata che fanno riferimento a chiavi primarie in altre tabelle).  
  
-   Un elenco di chiavi esterne in altre tabelle che fanno riferimento alla chiave primaria nella tabella specificata.  
  
 Il driver restituisce ogni elenco come set di risultati dell'istruzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLForeignKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      PKCatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      PKSchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      PKTableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      FKCatalogName,  
     SQLSMALLINT    NameLength4,  
     SQLCHAR *      FKSchemaName,  
     SQLSMALLINT    NameLength5,  
     SQLCHAR *      FKTableName,  
     SQLSMALLINT    NameLength6);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *PKCatalogName*  
 [Input] Nome del catalogo tabella chiave primaria. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispone di cataloghi. *PKCatalogName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *PKCatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *PKCatalogName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa. Per ulteriori informazioni, vedere [argomenti delle funzioni di catalogo in](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Input] Lunghezza di **PKCatalogName*, in caratteri.  
  
 *PKSchemaName*  
 [Input] Nome dello schema di tabella della chiave primaria. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispongono di schemi. *PKSchemaName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *PKSchemaName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *PKSchemaName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength2*  
 [Input] Lunghezza di **PKSchemaName*, in caratteri.  
  
 *PKTableName*  
 [Input] Nome della tabella chiave primaria. *PKTableName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *PKTableName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *PKTableName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength3*  
 [Input] Lunghezza di **PKTableName*, in caratteri.  
  
 *FKCatalogName*  
 [Input] Nome del catalogo tabella chiave esterna. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispone di cataloghi. *FKCatalogName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *FKCatalogName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *FKCatalogName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength4*  
 [Input] Lunghezza di **FKCatalogName*, in caratteri.  
  
 *FKSchemaName*  
 [Input] Nome dello schema di tabella della chiave esterna. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando vengono recuperati i dati dai diversi DBMS, una stringa vuota ("") indica le tabelle che non dispongono di schemi. *FKSchemaName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *FKSchemaName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *FKSchemaName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength5*  
 [Input] Lunghezza di **FKSchemaName*, in caratteri.  
  
 *FKTableName*  
 [Input] Nome della tabella chiave esterna. *FKTableName* non può contenere un criterio di ricerca della stringa.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, *FKTableName* viene considerato come un identificatore e il relativo case non è significativa. Se è SQL_FALSE, *FKTableName* è un argomento normale; viene considerato letteralmente e il relativo case è significativa.  
  
 *NameLength6*  
 [Input] Lunghezza di **FKTableName*, in caratteri.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLForeignKeys** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLForeignKeys** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto nel *StatementHandle*, e **SQLFetch** o **SQLFetchScroll** fosse stata chiamata. Questo errore viene restituito da Gestione Driver se **SQLFetch** o **SQLFetchScroll** non è stato restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto nel *StatementHandle*, ma **SQLFetch** o **SQLFetchScroll** non è stato chiamato.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*, e quindi è stata chiamata la funzione nuovo di *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|(DM) argomenti *PKTableName* e *FKTableName* sono stati entrambi puntatori null.<br /><br /> L'attributo di istruzione SQL_ATTR_METADATA_ID è stato impostato su SQL_TRUE, il *FKCatalogName* o *PKCatalogName* argomento è un puntatore null e il SQL_CATALOG_NAME *InfoType*restituisce i nomi di catalogo sono supportati.<br /><br /> (DM) a cui è stato impostato su SQL_TRUE, l'attributo di istruzione SQL_ATTR_METADATA_ID e *FKSchemaName*, *PKSchemaName*, *FKTableName*, o *PKTableName * argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando è stata chiamata la funzione SQLForeignKeys.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il * StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore di uno degli argomenti nome di lunghezza è minore di 0 ma non uguale a SQL_NTS.|  
|||Il valore di uno degli argomenti nome di lunghezza maggiore del valore di lunghezza massima per il nome corrispondente. (Vedere "Commenti".)|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|È stato specificato un nome di catalogo e del driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato un nome di schema e del driver o l'origine dati non supporta schemi.|  
|||La combinazione delle impostazioni correnti degli attributi di istruzione SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE non era supportata dall'origine dati o driver.<br /><br /> L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE di istruzione è stato impostato su un tipo di cursore per i quali il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati ha restituito il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Per informazioni sulla modalità di utilizzo le informazioni restituite da questa funzione, vedere [utilizza dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Se \* *PKTableName* contiene un nome di tabella, **SQLForeignKeys** restituisce un set di risultati che contiene la chiave primaria della tabella specificata e tutte le chiavi esterne che fanno riferimento a esso. L'elenco di chiavi esterne in altre tabelle non include chiavi esterne che puntano ai vincoli univoci nella tabella specificata.  
  
 Se \* *FKTableName* contiene un nome di tabella, **SQLForeignKeys** restituisce un set di risultati contenente tutte le chiavi esterne della tabella specificata che fanno riferimento a chiavi primarie in altre tabelle e chiavi primarie nelle tabelle a cui fanno riferimento. L'elenco di chiavi esterne della tabella specificata non contiene chiavi esterne che fanno riferimento a vincoli univoci in altre tabelle.  
  
 Se entrambi \* *PKTableName* e \* *FKTableName* contengono nomi di tabella, **SQLForeignKeys** restituisce le chiavi esterne nella tabella specificata in \* *FKTableName* che fanno riferimento alla chiave primaria della tabella specificata **PKTableName*. Deve essere al massimo una chiave.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, gli argomenti e i dati restituiti delle funzioni di catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLForeignKeys** restituisce i risultati come un set di risultati standard. Se sono richieste le chiavi esterne associate a una chiave primaria, il set di risultati viene ordinato in base FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME e KEY_SEQ. Se sono richieste le chiavi primarie associate a una chiave esterna, il set di risultati viene ordinato in base PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME e KEY_SEQ. Nella tabella seguente elenca le colonne nel set di risultati.  
  
 La lunghezza delle colonne VARCHAR non viene visualizzata nella tabella. le lunghezze effettivi variano a seconda dell'origine dati. Per determinare la lunghezza effettiva del PKTABLE_CAT o FKTABLE_CAT, PKTABLE_SCHEM o FKTABLE_SCHEM, colonne PKTABLE_NAME o FKTABLE_NAME e PKCOLUMN_NAME o FKCOLUMN_NAME, un'applicazione può chiamare **SQLGetInfo** con il SQL_MAX_ Opzioni CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN e SQL_MAX_COLUMN_NAME_LEN.  
  
 Le colonne seguenti sono state rinominate per ODBC 3*. x.* Le modifiche ai nomi di colonna non influiscono sulla compatibilità con le versioni precedenti poiché nelle applicazioni associati dal numero di colonna.  
  
|Colonna ODBC 2.0|ODBC 3*x* colonna|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 Nella tabella seguente elenca le colonne nel set di risultati. È possibile definire le colonne aggiuntive oltre colonna 14 (note) dal driver. Un'applicazione deve accedere a colonne specifiche del driver contando dalla fine del gruppo di risultati anziché specificare una posizione ordinale esplicita verso il basso. Per ulteriori informazioni, vedere [dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Numero colonna|Tipo di dati|Commenti|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|Nome del catalogo tabella chiave primaria; NULL se non è applicabile all'origine dati. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di cataloghi.|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|Nome dello schema di tabella della chiave primaria; NULL se non è applicabile all'origine dati. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di schemi.|  
|PKTABLE_NAME (ODBC 1.0)|3|Varchar non NULL|Nome della tabella chiave primaria.|  
|PKCOLUMN_NAME (ODBC 1.0)|4|Varchar non NULL|Nome della colonna chiave primaria. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|Nome del catalogo tabella chiave esterna; NULL se non è applicabile all'origine dati. Se un driver supporta cataloghi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di cataloghi.|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|Nome dello schema di tabella della chiave esterna. NULL se non è applicabile all'origine dati. Se un driver supporta gli schemi per alcune tabelle ma non per altri utenti, ad esempio quando il driver recupera i dati dai diversi DBMS, restituisce una stringa vuota ("") per le tabelle che non dispone di schemi.|  
|FKTABLE_NAME (ODBC 1.0)|7|Varchar non NULL|Nome della tabella chiave esterna.|  
|FKCOLUMN_NAME (ODBC 1.0)|8|Varchar non NULL|Nome della colonna chiave esterna. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|KEY_SEQ (ODBC 1.0)|9|Smallint non NULL|Numero di sequenza di colonne nella chiave (a partire da 1).|  
|UPDATE_RULE (ODBC 1.0)|10|Smallint|Azione da applicare alla chiave esterna durante l'operazione SQL è **aggiornamento**. Può avere uno dei valori seguenti. (La tabella di riferimento è la tabella che contiene la chiave primaria, la tabella di riferimento è la tabella che contiene la chiave esterna).<br /><br /> SQL_CASCADE: Quando la chiave primaria della tabella di riferimento viene aggiornata, viene aggiornata anche la chiave esterna della tabella di riferimento.<br /><br /> SQL_NO_ACTION: Se un aggiornamento della chiave primaria della tabella di riferimento causerebbe "riferimenti inesatti" nella tabella di riferimento (ovvero, le righe nella tabella di riferimento non avrebbero corrispondenti nella tabella di riferimento), l'aggiornamento viene rifiutato. Se un aggiornamento della chiave esterna della tabella di riferimento introdurrebbe un valore che non esiste come valore della chiave primaria della tabella di riferimento, l'aggiornamento è stato rifiutato. (Questa azione è lo stesso come azione SQL_RESTRICT in ODBC 2*x*.)<br /><br /> SQL_SET_NULL: Quando una o più righe nella tabella di riferimento vengono aggiornate in modo che uno o più componenti della chiave primaria vengono modificati, i componenti della chiave esterna nella tabella di riferimento che corrispondono ai componenti modificati della chiave primaria sono impostati su NULL in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> SQL_SET_DEFAULT: Quando una o più righe nella tabella di riferimento vengono aggiornate in modo che uno o più componenti della chiave primaria vengono modificati, i componenti della chiave esterna nella tabella di riferimento che corrispondono ai componenti modificati della chiave primaria sono impostare i valori predefiniti applicabili in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> NULL se non è applicabile all'origine dati.|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|Azione da applicare alla chiave esterna durante l'operazione SQL è **eliminare**. Può avere uno dei valori seguenti. (La tabella di riferimento è la tabella che contiene la chiave primaria, la tabella di riferimento è la tabella che contiene la chiave esterna).<br /><br /> SQL_CASCADE: Quando viene eliminata una riga nella tabella di riferimento, vengono eliminate anche tutte le righe corrispondenti nelle tabelle di riferimento.<br /><br /> SQL_NO_ACTION: Se un'operazione di eliminazione di una riga nella tabella di riferimento causerebbe "riferimenti inesatti" nella tabella di riferimento (ovvero, le righe nella tabella di riferimento non avrebbero corrispondenti nella tabella di riferimento), l'aggiornamento viene rifiutato. (Questa azione è lo stesso come azione SQL_RESTRICT in ODBC 2*x*.)<br /><br /> SQL_SET_NULL: Quando una o più righe nella tabella di riferimento vengono eliminate, ogni componente della chiave esterna della tabella di riferimento viene impostato su NULL in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> SQL_SET_DEFAULT: Quando una o più righe nella tabella di riferimento vengono eliminate, ogni componente della chiave esterna della tabella di riferimento viene impostato sul valore predefinito applicabile in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> NULL se non è applicabile all'origine dati.|  
|FK_NAME (ODBC 2.0)|12|Varchar|Nome della chiave esterna. NULL se non è applicabile all'origine dati.|  
|PK_NAME (ODBC 2.0)|13|Varchar|Nome della chiave primaria. NULL se non è applicabile all'origine dati.|  
|DEFERRABILITY (ODBC 3.0)|14|Smallint|SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Esempio di codice  
 Come illustrato nella tabella seguente, in questo esempio utilizza tre tabelle, denominate ORDERS, le righe e i clienti.  
  
|ORDERS|RIGHE|CLIENTI|  
|------------|-----------|---------------|  
|ORDERID|ORDERID|CUSTID|  
|CUSTID|RIGHE|NAME|  
|OPENDATE|PARTID|INDIRIZZO|  
|VENDITORE|QUANTITÀ|TELEFONO|  
|STATUS|||  
  
 Nella tabella ORDERS, CUSTID identifica il cliente a cui è ancora stata effettuata la vendita. È una chiave esterna che fa riferimento a CUSTID nella tabella CUSTOMERS.  
  
 Nella tabella, le righe ORDERID identifica l'ordine di vendita a cui è associato l'elemento di riga. È una chiave esterna che fa riferimento a ORDERID nella tabella ORDERS.  
  
 Questo esempio viene chiamato **SQLPrimaryKeys** per ottenere la chiave primaria della tabella ORDERS. Il set di risultati disporrà di una riga. le colonne significative sono visualizzate nella tabella seguente.  
  
|TABLE_NAME|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|ORDERID|1|  
  
 Infine, viene chiamato **SQLForeignKeys** per ottenere le chiavi esterne in altre tabelle che fanno riferimento alla chiave primaria della tabella ORDERS. Il set di risultati disporrà di una riga. le colonne significative sono visualizzate nella tabella seguente.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|RIGHE|CUSTID|1|  
  
 Infine, viene chiamato **SQLForeignKeys** per ottenere le chiavi esterne della tabella ordini che fanno riferimento a chiavi primarie delle altre tabelle. Il set di risultati disporrà di una riga. le colonne significative sono visualizzate nella tabella seguente.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|CLIENTI|CUSTID|ORDERS|CUSTID|1|  
  
```  
#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1  
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1  
  
LPSTR   szTable;              /* Table to display */  
  
UCHAR szPkTable[TAB_LEN];   /* Primary key table name */  
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */  
UCHAR szPkCol[COL_LEN];     /* Primary key column */  
UCHAR szFkCol[COL_LEN];     /* Foreign key column */  
  
SQLHSTMT      hstmt;  
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;  
SQLSMALLINT   iKeySeq;  
SQLRETURN     retcode;  
  
// Bind the columns that describe the primary and foreign keys.  
// Ignore the table schema, name, and catalog for this example.  
  
SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &cbPkTable);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &cbPkCol);  
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &iKeySeq, TAB_LEN, &cbKeySeq);  
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &cbFkTable);  
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &cbFkCol);  
  
strcpy_s(szTable, sizeof(szTable), "ORDERS");  
  
/* Get the names of the columns in the primary key. */  
  
retcode = SQLPrimaryKeys(hstmt,  
         NULL, 0,             /* Catalog name */  
         NULL, 0,             /* Schema name */  
         szTable, SQL_NTS);   /* Table name */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {  
  
   /* Fetch and display the result set. This will be a list of the */  
   /* columns in the primary key of the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,  
      iKeySeq);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys that refer to ORDERS primary key.*/   
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,            /* Primary catalog */  
         NULL, 0,            /* Primary schema */  
         szTable, SQL_NTS,   /* Primary table */  
         NULL, 0,            /* Foreign catalog */  
         NULL, 0,            /* Foreign schema */  
         NULL, 0);           /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* foreign keys in other tables that refer to the ORDERS */  
/* primary key. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s ) <-- %-s ( %-s )\n", szPkTable,  
               szPkCol, szFkTable, szFkCol);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys in the ORDERS table. */  
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,             /* Primary catalog */  
         NULL, 0,             /* Primary schema */  
         NULL, 0,             /* Primary table */  
         NULL, 0,             /* Foreign catalog */  
         NULL, 0,             /* Foreign schema */  
         szTable, SQL_NTS);   /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* primary keys in other tables that are referred to by foreign */  
/* keys in the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s )--> %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);  
}  
  
/* Free the hstmt. */  
SQLFreeStmt(hstmt, SQL_DROP);  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Recupero di una singola riga o un blocco di dati in una direzione forward-only|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|La restituzione di colonne di una chiave primaria|[Funzione SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Restituzione delle statistiche delle tabelle e indici|[Funzione SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

