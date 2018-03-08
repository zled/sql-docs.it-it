---
title: Funzione SQLGetDiagField | Documenti Microsoft
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
apiname: SQLGetDiagField
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetDiagField
helpviewer_keywords: SQLGetDiagField function [ODBC]
ms.assetid: 1dbc4398-97a8-4585-bb77-1f7ea75e24c4
caps.latest.revision: "26"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c202841d54e01758312c4e8388a78e583de9058c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetdiagfield-function"></a>Funzione SQLGetDiagField
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLGetDiagField** restituisce il valore corrente di un campo di un record della struttura di dati di diagnostica (associata a un handle specificato) che contiene informazioni sull'errore, avviso e stato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLGetDiagField(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     DiagIdentifier,  
     SQLPOINTER      DiagInfoPtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HandleType*  
 [Input] Un identificatore di tipo di handle che descrive il tipo di handle per cui è richiesto diagnostica. I possibili valori sono i seguenti:  
  
-   IMPOSTATO SU SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   IMPOSTATO SU SQL_HANDLE_ENV  
  
-   IMPOSTATO SU SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN è utilizzato solo da Gestione Driver e driver. Applicazioni non devono utilizzare questo tipo di handle. Per ulteriori informazioni su SQL_HANDLE_DBC_INFO_TOKEN, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Input] Un handle per la struttura di dati di diagnostica, del tipo indicato dalla *HandleType*. Se *HandleType* è impostato su SQL_HANDLE_ENV, *gestire* può essere condivisa o un handle di ambiente non condiviso.  
  
 *RecNumber*  
 [Input] Indica se il record di stato da cui l'applicazione cerca di informazioni. Record di stato vengono numerati da 1. Se il *DiagIdentifier* argomento indica qualsiasi campo dell'intestazione di diagnostica, *RecNumber* viene ignorato. In caso contrario, deve essere maggiore di 0.  
  
 *DiagIdentifier*  
 [Input] Indica il campo della diagnostica il cui valore è da restituire. Per ulteriori informazioni, vedere la "*DiagIdentifier* argomento" sezione "Commenti".  
  
 *DiagInfoPtr*  
 [Output] Puntatore a un buffer in cui si desidera restituire le informazioni di diagnostica. Il tipo di dati dipende dal valore di *DiagIdentifier*. Se *DiagInfoPtr* è di tipo integer, le applicazioni devono utilizzare un buffer di SQLULEN e inizializzare il valore su 0 prima di chiamare questa funzione, come alcuni driver può solo scrivere l'inferiore a 32 bit o a 16 bit di un buffer e lasciare l'ordine più elevato bit invariato.  
  
 Se *DiagInfoPtr* è NULL, *StringLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntato  *DiagInfoPtr*.  
  
 *BufferLength*  
 [Input] Se *DiagIdentifier* è una diagnostica definite da ODBC e *DiagInfoPtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere \* *DiagInfoPtr* . Se *DiagIdentifier* è un campo definito ODBC e \* *DiagInfoPtr* è un numero intero, *BufferLength* viene ignorato. Se il valore in  *\*DiagInfoPtr* è una stringa Unicode (quando si chiama **SQLGetDiagFieldW**), il *BufferLength* argomento deve essere un numero pari.  
  
 Se *DiagIdentifier* è un campo definito dal driver, l'applicazione indica la natura del campo al Driver Manager impostando il *BufferLength* argomento. *BufferLength* può avere i valori seguenti:  
  
-   Se *DiagInfoPtr* è un puntatore a una stringa di caratteri *BufferLength* è la lunghezza della stringa o SQL_NTS.  
  
-   Se *DiagInfoPtr* è un puntatore a un buffer binario, le posizioni dell'applicazione il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *BufferLength*. In questo modo un valore negativo in *BufferLength*.  
  
-   Se *DiagInfoPtr* è un puntatore a un valore diverso da una stringa di caratteri o stringa binaria, *BufferLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se  *\*DiagInfoPtr* contiene un tipo di dati a lunghezza fissa, *BufferLength* è SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT o SQL_IS_USMALLINT, come appropriato.  
  
 *StringLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di byte (escluso il numero di byte necessari per il carattere di terminazione null) disponibile per restituire \* *DiagInfoPtr*, dati di tipo carattere. Se il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength*, il testo in \* *DiagInfoPtr* viene troncato a *BufferLength* meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE o SQL_NO_DATA.  
  
## <a name="diagnostics"></a>Diagnostica  
 **SQLGetDiagField** non registra record di diagnostica per se stesso. Usa i seguenti valori restituiti per segnalare il risultato della propria esecuzione:  
  
-   SQL_SUCCESS: La funzione ha restituito correttamente le informazioni di diagnostica.  
  
-   SQL_SUCCESS_WITH_INFO: \* *DiagInfoPtr* è troppo piccolo per contenere i campi di diagnostica richiesti. Di conseguenza, i dati nel campo di diagnostica è stati troncati. Per determinare che si è verificato un troncamento, l'applicazione deve confrontare *BufferLength* sul numero effettivo di byte disponibili, che viene scritto **StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE: L'handle indicato da *HandleType* e *gestire* non è un handle valido.  
  
-   SQL_ERROR: Uno dei seguenti si è verificato:  
  
    -   *Il DiagIdentifier* argomento non è uno dei valori validi.  
  
    -   *Il DiagIdentifier* argomento è stato SQL_DIAG_CURSOR_ROW_COUNT, SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE o SQL_DIAG_ROW_COUNT, ma *gestire* non è un handle di istruzione. (Gestione Driver restituisce questa diagnostica.)  
  
    -   *Il RecNumber* argomento è negativo o 0 quando *DiagIdentifier* indicato un campo da un record di diagnostica. *RecNumber* viene ignorato per i campi di intestazione.  
  
    -   Il valore richiesto è una stringa di caratteri e *BufferLength* è minore di zero.  
  
    -   Quando si utilizza la notifica asincrona, l'operazione asincrona dell'handle non è completo.  
  
-   SQL_NO_DATA: *RecNumber* è maggiore del numero di record di diagnostica esistenti per l'handle specificato nel *gestire.* La funzione restituisce SQL_NO_DATA per qualsiasi positivo *RecNumber* se non sono presenti record di diagnostica per *gestire*.  
  
## <a name="comments"></a>Commenti  
 Un'applicazione chiama in genere **SQLGetDiagField** a completare una delle tre obiettivi:  
  
1.  Per ottenere le informazioni sull'avviso o errore specifico, quando una chiamata di funzione ha restituito SQL_ERROR o SQL_SUCCESS_WITH_INFO (o SQL_NEED_DATA per il **SQLBrowseConnect** funzione).  
  
2.  Per determinare il numero di righe nell'origine dati che sono stati interessati quando sono state eseguite operazioni update, delete o insert con una chiamata a **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, o **SQLSetPos** (dal campo di intestazione SQL_DIAG_ROW_COUNT), o per determinare il numero di righe presenti nel cursore aperto corrente, se il driver può fornire queste informazioni (dal Campo di intestazione SQL_DIAG_CURSOR_ROW_COUNT).  
  
3.  Per determinare quale funzione che è stata eseguita da una chiamata a **SQLExecDirect** o **SQLExecute** (rispetto ai campi di intestazione SQL_DIAG_DYNAMIC_FUNCTION e SQL_DIAG_DYNAMIC_FUNCTION_CODE).  
  
 Una funzione ODBC può registrare zero o più record di diagnostica ogni volta che viene chiamato, in modo un'applicazione può chiamare **SQLGetDiagField** dopo ogni chiamata di funzione ODBC. Non sussiste alcun limite al numero di record di diagnostica che possono essere archiviati in qualsiasi momento. **SQLGetDiagField** recupera solo le informazioni di diagnostica più di recente associate alla struttura di dati di diagnostica specificata nel *gestire* argomento. Se l'applicazione chiama una funzione ODBC diverso da **SQLGetDiagField** o **SQLGetDiagRec**, le informazioni di diagnostica da una chiamata precedente con lo stesso handle vengono perse.  
  
 Un'applicazione è possibile analizzare tutti i record di diagnostica incrementando *RecNumber*, purché **SQLGetDiagField** restituisce SQL_SUCCESS. Il numero di record di stato è indicato nel campo di intestazione SQL_DIAG_NUMBER. Le chiamate a **SQLGetDiagField** siano distruttive ai campi di intestazione e il record. L'applicazione può chiamare **SQLGetDiagField** più tardi per recuperare un campo da un record, come una funzione diversa da funzioni di diagnostica non è stata chiamata nel frattempo, che potrebbe registrare record sullo stesso handle.  
  
 Un'applicazione può chiamare **SQLGetDiagField** per restituire i campi di diagnostica in qualsiasi momento, ad eccezione di SQL_DIAG_CURSOR_ROW_COUNT o SQL_DIAG_ROW_COUNT, che restituirà SQL_ERROR se *gestire* non è un handle di istruzione. Se gli altri campi di diagnostica non sono definito, la chiamata a **SQLGetDiagField** restituisce SQL_SUCCESS (fornita da altri diagnostica non viene rilevata) e viene restituito un valore non definito per il campo.  
  
 Per ulteriori informazioni, vedere [utilizzando SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) e [implementazione SQLGetDiagRec e SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Chiama un'API diverso da quello che viene eseguita in modo asincrono genererà HY010 "Errore nella sequenza Function". Tuttavia, il record di errore non è possibile recuperare prima che venga completata l'operazione asincrona.  
  
## <a name="handletype-argument"></a>Argomento HandleType  
 Ogni tipo di handle può avere le informazioni di diagnostica associate. Il *HandleType* argomento indica il tipo di handle di *gestire*.  
  
 Alcuni campi di intestazione e record non possono essere restituiti per l'ambiente, connessione, l'istruzione e descrittore di handle. Tali handle per il quale non è applicabile un campo sono indicati nelle sezioni "Campi di intestazione" e "Record" seguente.  
  
 Se *HandleType* è impostato su SQL_HANDLE_ENV, *gestire* può essere un handle di ambiente condiviso o annullata.  
  
 Nessun campo di diagnostica specifici del driver intestazione deve essere associato a un handle di ambiente.  
  
 I campi di intestazione solo diagnostica definiti per un handle di descrittore sono SQL_DIAG_NUMBER e SQL_DIAG_RETURNCODE.  
  
## <a name="diagidentifier-argument"></a>Argomento DiagIdentifier  
 Questo argomento indica l'identificatore del campo richiesto dalla struttura di dati di diagnostica. Se *RecNumber* è maggiore o uguale a 1, i dati nel campo descrivono le informazioni di diagnostica restituite da una funzione. Se *RecNumber* è 0, il campo è contenuto nell'intestazione della struttura di dati di diagnostica e di conseguenza contiene dati relativi alla chiamata di funzione che ha restituito informazioni di diagnostica, non per le informazioni specifiche.  
  
 I driver è possono definire intestazione specifico del driver e i campi di record nella struttura di dati di diagnostica.  
  
 Un'applicazione ODBC 3*x* applicazione che utilizza un ODBC 2*x* driver sarà in grado di chiamare **SQLGetDiagField** solo con un *DiagIdentifier* argomento di SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME o SQL_DIAG_SQLSTATE. Tutti gli altri campi di diagnostica restituirà SQL_ERROR.  
  
## <a name="header-fields"></a>Campi di intestazione  
 I campi di intestazione elencati nella tabella seguente possono essere inclusi nel *DiagIdentifier* argomento.  
  
|DiagIdentifier|Tipo restituito|Valori di codice restituiti|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|Questo campo contiene il numero di righe nel cursore. La semantica varia il **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 e SQL_STATIC_CURSOR_ATTRIBUTES2, che indicano che i tipi di informazioni conteggio delle righe è disponibili per ogni tipo di cursore (nei bit SQL_CA2_CRC_EXACT e SQL_CA2_CRC_APPROXIMATE).<br /><br /> Il contenuto di questo campo è definito solo per gli handle di istruzione e solo dopo che **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato. La chiamata **SQLGetDiagField** con un *DiagIdentifier* di SQL_DIAG_CURSOR_ROW_COUNT in diverso da un'istruzione handle restituirà SQL_ERROR.|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR *|Si tratta di una stringa che descrive l'istruzione SQL eseguita la funzione sottostante. (Per valori specifici, vedere "Valori dei campi, funzione dinamica" più avanti in questa sezione). Il contenuto di questo campo è definito solo per gli handle di istruzione e solo dopo una chiamata a **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults**. La chiamata **SQLGetDiagField** con un *DiagIdentifier* di SQL_DIAG_DYNAMIC_FUNCTION in diverso da un'istruzione handle restituirà SQL_ERROR. Il valore di questo campo non è definito prima della chiamata a **SQLExecute** o **SQLExecDirect**.|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|Si tratta di un codice numerico che descrive l'istruzione SQL eseguita dalla funzione sottostante. (Vedere "Valori del dinamica funzione campi," più avanti in questa sezione per valore specifico.) Il contenuto di questo campo è definito solo per gli handle di istruzione e solo dopo una chiamata a **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults**. La chiamata **SQLGetDiagField** con un *DiagIdentifier* di SQL_DIAG_DYNAMIC_FUNCTION_CODE in diverso da un'istruzione handle restituirà SQL_ERROR. Il valore di questo campo non è definito prima della chiamata a **SQLExecute** o **SQLExecDirect**.|  
|SQL_DIAG_NUMBER|SQLINTEGER|Il numero di record di stato che sono disponibili per l'handle specificato.|  
|SQL_DIAG_RETURNCODE|SQLRETURN|Restituisce il codice restituito dalla funzione. Per un elenco dei codici restituiti, vedere [codici restituiti](../../../odbc/reference/develop-app/return-codes-odbc.md). Il driver non è necessario implementare SQL_DIAG_RETURNCODE; viene sempre implementato da Gestione Driver. Se nessuna funzione è ancora stata chiamata sul *gestire*, viene restituito SQL_SUCCESS per SQL_DIAG_RETURNCODE.|  
|SQL_DIAG_ROW_COUNT|SQLLEN|Il numero di righe interessate da un'istruzione insert, delete o update eseguite da **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos**. È definito dal driver dopo un *specifica del cursore* è stata eseguita. Il contenuto di questo campo è definito solo per gli handle di istruzione. La chiamata **SQLGetDiagField** con un *DiagIdentifier* di SQL_DIAG_ROW_COUNT in diverso da un'istruzione handle restituirà SQL_ERROR. I dati in questo campo viene inoltre restituiti nel *RowCountPtr* argomento di **SQLRowCount**. I dati in questo campo viene reimpostati dopo ogni chiamata di funzione nondiagnostic, mentre il numero di righe restituito da **SQLRowCount** viene mantenuta finché l'istruzione viene impostato lo stato preparato o allocato.|  
  
## <a name="record-fields"></a>I campi di record  
 I campi di record elencati nella tabella seguente possono essere inclusi nel *DiagIdentifier* argomento.  
  
|DiagIdentifier|Tipo restituito|Valori di codice restituiti|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR *|Stringa che indica il documento che definisce la parte relativa alla classe del valore SQLSTATE di questo record. Il valore è "ISO 9075" per tutti SQLSTATE definiti da Open Group e interfaccia di chiamata a livello ISO. Per SQLSTATE ODBC specifiche (tutte quelle la cui classe SQLSTATE è "IM"), il valore è "ODBC 3.0".|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|Se il campo SQL_DIAG_ROW_NUMBER è un numero di riga valida in un set di righe o di un set di parametri, questo campo contiene il valore che rappresenta il numero di colonna nel set di risultati o il numero di parametro nel set di parametri. Set di risultati colonna i numeri iniziano sempre da 1. Se questo record di stato relativo a una colonna del segnalibro, il campo può essere zero. Numeri di parametro iniziano da 1. È impostata sul valore SQL_NO_COLUMN_NUMBER se il record di stato non è associato a un numero di colonna o parametro. Se il driver non è possibile determinare il numero di colonna o parametro associato a questo record, il valore SQL_COLUMN_NUMBER_UNKNOWN questo campo.<br /><br /> Il contenuto di questo campo è definito solo per gli handle di istruzione.|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR *|Stringa che indica il nome della connessione di cui si riferisce al record di diagnostica. Questo campo è definito dal driver. Per le strutture di dati di diagnostica associate all'handle di ambiente e per la diagnostica che non sono correlati a qualsiasi connessione, questo campo è una stringa di lunghezza zero.|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR *|Un messaggio informativo in errore o dell'avviso. Questo campo è formattato come descritto in [messaggi diagnostici](../../../odbc/reference/develop-app/diagnostic-messages.md). È prevista una lunghezza massima per il testo del messaggio di diagnostica.|  
|SQL_DIAG_NATIVE|SQLINTEGER|Un codice di errore nativo specifici dell'origine dati/driver. Se è presente alcun codice di errore nativo, il driver restituisce 0.|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|Questo campo contiene il numero di riga nel set di righe o il numero di parametro nel set di parametri, a cui è associato il record di stato. Numeri di riga e parametro iniziano con 1. Questo campo è il valore SQL_NO_ROW_NUMBER se questo record di stato non è associato a un numero di riga o parametro. Se il driver non è possibile determinare il numero di riga o parametro associato a questo record, il valore SQL_ROW_NUMBER_UNKNOWN questo campo.<br /><br /> Il contenuto di questo campo è definito solo per gli handle di istruzione.|  
|SQL_DIAG_SERVER_NAME|SQLCHAR *|Stringa che indica il nome del server cui si riferisce al record di diagnostica. È identico al valore restituito per una chiamata a **SQLGetInfo** con l'opzione SQL_DATA_SOURCE_NAME. Per le strutture di dati di diagnostica associate all'handle di ambiente e per la diagnostica che non sono correlati a qualsiasi server, questo campo è una stringa di lunghezza zero.|  
|SQL_DIAG_SQLSTATE|SQLCHAR *|Un codice diagnostica SQLSTATE di cinque caratteri. Per ulteriori informazioni, vedere [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md).|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR *|Una stringa con lo stesso formato e i valori validi come SQL_DIAG_CLASS_ORIGIN, che identifica la parte di definizione della parte del codice SQLSTATE sottoclasse. Gli SQLSTATE ODBC specifici per il quale viene restituito "ODBC 3.0" di seguito:<br /><br /> 01S00, 01S01, 01S02, 01S06, 01S07, 07S01, 08S01, 21S01, 21S02, 25S01, 25S02, 25S03, 42S01, 42S02, 42S11, 42S12, 42S21, 42S22, HY095, HY097, HY098, HY099, HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007 IM008, IM010, IM011, IM012.|  
  
## <a name="values-of-the-dynamic-function-fields"></a>Valori dei campi di funzione dinamica  
 Nella tabella seguente vengono descritti i valori di SQL_DIAG_DYNAMIC_FUNCTION e SQL_DIAG_DYNAMIC_FUNCTION_CODE che si applicano a ogni tipo di istruzione SQL eseguita da una chiamata a **SQLExecute** o **SQLExecDirect**. Il driver è possibile aggiungere valori definito dal driver a quelli elencati.  
  
|Istruzione SQL<br /><br /> Esecuzione|Valore di<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|Valore di<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*ALTER-dominio-istruzione*|"ALTER DOMINIO"|SQL_DIAG_ALTER_DOMAIN|  
|*ALTER-tabella-istruzione*|"ALTER TABLE"|SQL_DIAG_ALTER_TABLE|  
|*definizione di asserzione*|"CREAZIONE DI ASSERZIONE"|SQL_DIAG_CREATE_ASSERTION|  
|*definizione di set di caratteri*|"CREAZIONE DI SET DI CARATTERI"|SQL_DIAG_CREATE_CHARACTER_SET|  
|*definizione di regole di confronto*|"CREAZIONE DI REGOLE DI CONFRONTO"|SQL_DIAG_CREATE_COLLATION|  
|*creare-index-istruzione*|"CREAZIONE DELL'INDICE"|SQL_DIAG_CREATE_INDEX|  
|*creare-tabella-istruzione*|"CREAZIONE DI TABELLA"|SQL_DIAG_CREATE_TABLE|  
|*creare-view-istruzione*|"CREAZIONE DI VISUALIZZAZIONE"|SQL_DIAG_CREATE_VIEW|  
|*Specifica di cursore.*|"SELECT DEL CURSORE"|SQL_DIAG_SELECT_CURSOR|  
|*posizionato Delete-istruzione*|"CURSORE DINAMICA DI ELIMINAZIONE"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*la ricerca Delete-istruzione*|"DELETE WHERE"|SQL_DIAG_DELETE_WHERE|  
n-definizione *|"CREAZIONE DI DOMINIO"|SQL_DIAG_CREATE_DOMAIN|  
|*istruzione di asserzione di rilascio*|"ASSERZIONE DI RILASCIO"|SQL_DIAG_DROP_ASSERTION|  
|*DROP-carattere-set-istruzione INSERT.*|"IL SET DI CARATTERI DI RILASCIO"|SQL_DIAG_DROP_CHARACTER_SET|  
|*DROP-regole di confronto-istruzione*|"RIEPILOGO DELLE REGOLE DI CONFRONTO"|SQL_DIAG_DROP_COLLATION|  
|*DROP-dominio-istruzione*|"DOMINIO DI RILASCIO"|SQL_DIAG_DROP_DOMAIN|  
|*DROP index-istruzione*|"DROP INDEX"|SQL_DIAG_DROP_INDEX|  
|*DROP-schema-istruzione*|"DROP SCHEMA"|SQL_DIAG_DROP_SCHEMA|  
|*DROP-tabella-istruzione*|"DROP TABLE"|SQL_DIAG_DROP_TABLE|  
|*DROP-traduzione-istruzione*|"CONVERSIONE DI RILASCIO"|SQL_DIAG_DROP_TRANSLATION|  
|*DROP-view-istruzione*|"DROP VIEW"|SQL_DIAG_DROP_VIEW|  
-istruzione *|"GRANT"|SQL_DIAG_GRANT|  
|*Insert-istruzione*|"INSERT"|SQL_DIAG_INSERT|  
|*Estensione di stored procedure ODBC*|"CHIAMATA DI|CHIAMATA DI SQL_DIAG_|  
|*REVOKE-istruzione*|"REVOKE"|SQL_DIAG_REVOKE|  
|*definizione dello schema*|"CREAZIONE DI SCHEMA"|SQL_DIAG_CREATE_SCHEMA|  
|*definizione di traduzione*|"CREAZIONE DI TRADUZIONE"|SQL_DIAG_CREATE_TRANSLATION|  
|*posizionato Update-istruzione*|"AGGIORNAMENTO DINAMICO DI CURSOR"|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*la ricerca Update-istruzione*|"AGGIORNAMENTO WHERE"|SQL_DIAG_UPDATE_WHERE|  
|Unknown|*stringa vuota*|SQL_DIAG_UNKNOWN_STATEMENT|  
  
## <a name="sequence-of-status-records"></a>Sequenza di record di stato  
 Record di stato vengono posizionati in una sequenza in base a numero di riga e il tipo della diagnostica. Gestione Driver determina l'ordine finale in cui restituire i record di stato che viene generata. Il driver determina l'ordine in cui restituire i record di stato che genera finale.  
  
 Se i record di diagnostica vengono registrati da Gestione Driver sia il driver, Driver Manager è responsabile ordinandoli.  
  
 Se sono presenti due o più record di stato, la sequenza dei record viene determinata innanzitutto dal numero di riga. Le regole seguenti si applicano a definire la sequenza di record di diagnostica a riga:  
  
-   Record non corrispondenti a qualsiasi riga verranno visualizzati davanti record corrispondenti a una determinata riga, perché SQL_NO_ROW_NUMBER è definito per essere -1.  
  
-   I record per cui il numero di riga è sconosciuto visualizzato davanti a tutti gli altri record, perché SQL_ROW_NUMBER_UNKNOWN viene definito come – 2.  
  
-   Per tutti i record relativi a colonne specifiche, i record vengono ordinati dal valore nel campo SQL_DIAG_ROW_NUMBER. Vengono elencati tutti gli errori e avvisi della prima riga interessata, e quindi tutti gli errori e avvisi del successivo di righe interessate e così via.  
  
> [!NOTE]  
>  ODBC 3*x* gestione Driver non sono ordinati i record di stato nella coda di diagnostica se SQLSTATE 01S01 (errore nella riga) restituito da un'API ODBC 2*x* driver o se SQLSTATE 01S01 (riga) che viene restituito da un database ODBC 3*x* driver quando **SQLExtendedFetch** viene chiamato o **SQLSetPos** viene chiamato su un cursore posizionato con **SQLExtendedFetch.** .  
  
 All'interno di ogni riga o per tutti i record che non corrispondono a una riga o per i quali il numero di riga è sconosciuto, o per tutti i record con un numero di riga uguale a SQL_NO_ROW_NUMBER, il primo record elencati è determinato mediante un set di regole di ordinamento. Dopo il primo record, l'ordine dei record che interessano una riga è definito. Un'applicazione non può presumere che gli errori precedono avvisi dopo il primo record. Le applicazioni è consigliabile analizzare la struttura di dati di diagnostica completa per ottenere informazioni complete su una chiamata a una funzione.  
  
 Le regole seguenti vengono utilizzate per determinare il primo record all'interno di una riga. Il record con il valore più alto è il primo record. L'origine di un record (gestione Driver, driver, gateway e così via) non viene considerato quando i record di rango.  
  
-   **Errori** record di stato che descrivono gli errori sono il valore più alto. Per ordinare gli errori, vengono applicate le regole seguenti:  
  
    -   I record che indicano un errore di transazione o di un errore di transazione possibili outrank tutti gli altri record.  
  
    -   Se due o più record di descrivere la stessa condizione di errore, definiti dalla specifica CLI di gruppo aprire (classi 03 tramite HZ) SQLSTATE outrank SQLSTATE ODBC e driver definiti.  
  
-   **I valori dei dati non definito dall'implementazione** record di stato che descrivono i valori dei dati non definito dal driver (classe 02) è il secondo valore più alto.  
  
-   **Avvisi** record di stato che descrivono gli avvisi (classe 01) hanno la priorità più bassa. Se due o più record descrivono la stessa condizione di avviso, quindi avviso SQLSTATE definiti dalla specifica CLI di gruppo aprire outrank SQLSTATE definite da ODBC e definito dal driver.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Recupero di più campi di una struttura di dati di diagnostica|[Funzione SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
