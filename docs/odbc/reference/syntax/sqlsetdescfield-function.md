---
title: Funzione SQLSetDescField | Documenti Microsoft
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
- SQLSetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescField
helpviewer_keywords:
- SQLSetDescField function [ODBC]
ms.assetid: 8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee9cd8b485584d863e7eac942a7c81792bb22bd7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetdescfield-function"></a>Funzione SQLSetDescField
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLSetDescField** imposta il valore di un singolo campo di un record del descrittore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLSetDescField(  
     SQLHDESC      DescriptorHandle,  
     SQLSMALLINT   RecNumber,  
     SQLSMALLINT   FieldIdentifier,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    BufferLength);  
```  
  
## <a name="arguments"></a>Argomenti  
 *DescriptorHandle*  
 [Input] Handle di descrittore.  
  
 *RecNumber*  
 [Input] Indica che contiene il campo che l'applicazione tenta di impostare il record del descrittore. Record del descrittore sono numerati da 0, con il numero di record 0 è il record di segnalibro. Il *RecNumber* argomento viene ignorato per i campi di intestazione.  
  
 *FieldIdentifier*  
 [Input] Indica il campo del descrittore il cui valore è necessario impostare. Per ulteriori informazioni, vedere "*FieldIdentifier* argomento" nella sezione "Commenti".  
  
 *ValuePtr*  
 [Input] Puntatore a un buffer contenente le informazioni sul descrittore o un valore intero. Il tipo di dati dipende dal valore di *FieldIdentifier*. Se *ValuePtr* è un valore integer, può essere considerata come 8 byte (SQLLEN), 4 byte (SQLINTEGER) o 2 byte (SQLSMALLINT), in base al valore di *FieldIdentifier* argomento.  
  
 *BufferLength*  
 [Input] Se *FieldIdentifier* è un campo definito ODBC e *ValuePtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere **ValuePtr*. Per i dati di stringa di caratteri, questo argomento deve contenere il numero di byte nella stringa.  
  
 Se *FieldIdentifier* è un campo definito ODBC e *ValuePtr* è un numero intero, *BufferLength* viene ignorato.  
  
 Se *FieldIdentifier* è un campo definito dal driver, l'applicazione indica la natura del campo al Driver Manager impostando il *BufferLength* argomento. *BufferLength* può avere i valori seguenti:  
  
-   Se *ValuePtr* è un puntatore a una stringa di caratteri, quindi *BufferLength* è la lunghezza della stringa o SQL_NTS.  
  
-   Se *ValuePtr* è un puntatore a un buffer binario, quindi viene visualizzato il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *BufferLength*. In questo modo un valore negativo in *BufferLength*.  
  
-   Se *ValuePtr* è un puntatore a un valore diverso da una stringa di caratteri o una stringa binaria, quindi *BufferLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se *ValuePtr* contiene un valore di lunghezza fissa, quindi *BufferLength* è SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT o SQL_IS_USMALLINT, come appropriato.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetDescField** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL_HANDLE_DESC e *gestire* di *DescriptorHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLSetDescField** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Il driver non supportava il valore specificato  *\*ValuePtr* (se *ValuePtr* era un puntatore) o il valore in *ValuePtr* (se *ValuePtr*  è un valore integer), o  *\*ValuePtr* non valido a causa di condizioni di lavoro di implementazione, pertanto il driver sostituito con un valore analogo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07009|Indice del descrittore non valido|Il *FieldIdentifier* argomento è un campo di record, il *RecNumber* argomento è 0 e *DescriptorHandle* argomento cui fa riferimento a un handle IPD.<br /><br /> Il *RecNumber* argomento è minore di 0 e *DescriptorHandle* argomento riferimento a un ARD o un APD.<br /><br /> Il *RecNumber* argomento è maggiore del numero massimo di colonne o parametri in grado di supportare l'origine dati, e *DescriptorHandle* argomento cui fa riferimento a un APD o ARD.<br /><br /> (DM) il *FieldIdentifier* argomento era SQL_DESC_COUNT, e  *\*ValuePtr* argomento è minore di 0.<br /><br /> Il *RecNumber* argomento è uguale a 0 e *DescriptorHandle* argomento cui fa riferimento a un APD allocato in modo implicito. (Questo errore si verifica con un descrittore di applicazione allocato in modo esplicito, perché non è noto se un descrittore allocato in modo esplicito dell'applicazione è un APD ARD fino a fase di esecuzione.)|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22001|Stringa di dati corretto troncato|Il *FieldIdentifier* argomento era SQL_DESC_NAME e *BufferLength* argomento è un valore maggiore di SQL_MAX_IDENTIFIER_LEN.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) il *DescriptorHandle* è stato associato un *StatementHandle* per i quali è stata chiamata una funzione in modo asincrono in esecuzione (non presente) ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* con cui il *DescriptorHandle* è stato associato e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *DescriptorHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLSetDescField** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per uno degli handle di istruzione associati il *DescriptorHandle* e SQL_PARAM_DATA_AVAILABLE restituito. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY016|Non è possibile modificare un descrittore della riga di implementazione|Il *DescriptorHandle* argomento è stato associato a un'implementazione e *FieldIdentifier* argomento non è stata SQL_DESC_ARRAY_STATUS_PTR o SQL_DESC_ROWS_PROCESSED_PTR.|  
|HY021|Informazioni del descrittore incoerenti.|I campi SQL_DESC_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE non formano un tipo SQL ODBC valido o un tipo SQL specifici del driver valido (per IPD, Implementation) o un tipo di dati ODBC C valido (per Apd o ARDs).<br /><br /> Informazioni sul descrittore controllati durante una verifica coerenza non era coerente. (Vedere "Controllo di coerenza" nella **SQLSetDescRec**.)|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM)  *\*ValuePtr* è una stringa di caratteri e *BufferLength* era minore di zero ma non uguale a SQL_NTS.<br /><br /> (DM) il driver non è un'API ODBC 2*x* driver, il descrittore è un ARD, il *ColumnNumber* argomento è stato impostato su 0 e il valore specificato per l'argomento *BufferLength* stato non è uguale a 4.|  
|HY091|Identificatore del campo del descrittore non valido|Il valore specificato per il *FieldIdentifier* argomento non è un campo definito ODBC e non è un valore definito dall'implementazione.<br /><br /> Il *FieldIdentifier* argomento non valido per il *DescriptorHandle* argomento.<br /><br /> Il *FieldIdentifier* argomento è un campo di sola lettura, definite da ODBC.|  
|HY092|Identificatore di attributo/opzione non valida|Il valore in  *\*ValuePtr* non valido per il *FieldIdentifier* argomento.<br /><br /> Il *FieldIdentifier* argomento era SQL_DESC_UNNAMED, e *ValuePtr* stato SQL_NAMED.|  
|HY105|Tipo di parametro non valido|(DM) il valore specificato per il campo SQL_DESC_PARAMETER_TYPE non è valido. (Per ulteriori informazioni, vedere la "*InputOutputType* argomento" sezione **SQLBindParameter**.)|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *DescriptorHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Un'applicazione può chiamare **SQLSetDescField** per impostare qualsiasi campo di descrizione uno alla volta. Una chiamata a **SQLSetDescField** imposta un singolo campo in un singolo descrittore. Questa funzione può essere chiamato per impostare i campi in qualsiasi tipo di descrittore, fornito che il campo può essere impostato. (Vedere la tabella più avanti in questa sezione).  
  
> [!NOTE]  
>  Se una chiamata a **SQLSetDescField** ha esito negativo, il contenuto del record del descrittore identificate le *RecNumber* argomento non sono definiti.  
  
 Altre funzioni possono essere chiamati per impostare più campi di descrizione con una sola chiamata della funzione. Il **SQLSetDescRec** funzione imposta vari campi che interessano il buffer e il tipo di dati associati a una colonna o un parametro (il SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL _ Campi DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR e SQL_DESC_INDICATOR_PTR). **SQLBindCol** oppure **SQLBindParameter** può essere usato per rendere una specifica completa per l'associazione di una colonna o parametro. Queste funzioni impostano un gruppo specifico di campi di descrizione con chiamata una funzione.  
  
 **SQLSetDescField** può essere chiamato per modificare i buffer di associazione tramite l'aggiunta di un offset per i puntatori di associazione (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR). In questo caso, i buffer dell'associazione senza chiamare **SQLBindCol** o **SQLBindParameter**, che consente a un'applicazione modificare SQL_DESC_DATA_PTR senza modificare altri campi, ad esempio SQL_DESC_DATA_ TIPO.  
  
 Se un'applicazione chiama **SQLSetDescField** per impostare un campo diverso da SQL_DESC_COUNT o i campi posticipati SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR o SQL_DESC_INDICATOR_PTR, diventa non associato al record.  
  
 I campi di intestazione di descrizione vengono impostati chiamando **SQLSetDescField** con l'appropriato *FieldIdentifier*. Numero di campi di intestazione è anche gli attributi di istruzione, pertanto può anche essere impostate da una chiamata a **SQLSetStmtAttr**. Questo consente alle applicazioni di impostare un campo di descrizione senza prima di ottenere un handle descrittore. Quando **SQLSetDescField** per impostare un campo di intestazione, viene chiamato il *RecNumber* argomento viene ignorato.  
  
 Oggetto *RecNumber* 0 è utilizzato per impostare i campi di segnalibro.  
  
> [!NOTE]  
>  L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS deve sempre essere impostata prima di chiamare **SQLSetDescField** per impostare i campi di segnalibro. Sebbene non sia obbligatorio, è consigliabile.  
  
## <a name="sequence-of-setting-descriptor-fields"></a>Sequenza dell'impostazione di campi di descrizione  
 Quando si impostano i campi di descrizione chiamando **SQLSetDescField**, l'applicazione deve seguire una sequenza specifica:  
  
1.  L'applicazione è innanzitutto necessario impostare il campo SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE o SQL_DESC_DATETIME_INTERVAL_CODE.  
  
2.  Dopo aver impostato uno di questi campi, l'applicazione può impostare l'attributo di un tipo di dati e il driver imposta i campi degli attributi di tipo di dati per i valori predefiniti appropriati per il tipo di dati. L'impostazione automatica dei campi di tipo attributo assicura che il descrittore sia sempre pronto per l'uso dopo l'applicazione è specificato un tipo di dati. Se l'applicazione imposta in modo esplicito un attributo di tipo di dati, esegue l'override l'attributo predefinito.  
  
3.  Dopo che uno dei campi elencati nel passaggio 1 è stato impostato e sono stati impostati gli attributi di tipo di dati, l'applicazione può impostare SQL_DESC_DATA_PTR. Verrà chiesto di specificare un controllo di coerenza dei campi di descrizione. Se l'applicazione modifica il tipo di dati o gli attributi dopo aver impostato il campo SQL_DESC_DATA_PTR, il driver imposta SQL_DESC_DATA_PTR a un puntatore null, il record di annullamento dell'associazione. In questo modo l'applicazione per completare la procedura in sequenza, prima che il record del descrittore sia utilizzabile.  
  
## <a name="initialization-of-descriptor-fields"></a>Inizializzazione di campi di descrizione  
 Quando viene allocato un descrittore, i campi del descrittore possono essere inizializzati su un valore predefinito, essere inizializzati senza un valore predefinito o essere non definito per il tipo di descrittore. Nelle tabelle seguenti indicano l'inizializzazione di ogni campo per ogni tipo di descrittore, con "D" che indica che il campo viene inizializzato con un valore predefinito e "ND" che indica che il campo viene inizializzato senza un valore predefinito. Se viene visualizzato un numero, il valore predefinito del campo è il numero. Le tabelle indicano anche se un campo è di sola lettura (R) o lettura/scrittura (L/S).  
  
 I campi di un IRD hanno un valore predefinito solo dopo l'istruzione è stato preparato o eseguito e l'implementazione è stato popolato, non quando è stato allocato l'handle di istruzione o di un descrittore. Fino a quando non è stato popolato il IRD, qualsiasi tentativo di accedere a un campo di un IRD restituirà un errore.  
  
 Alcuni campi di descrizione vengono definiti per una o più, ma non tutti i tipi di descrittore (ARDs e IRDs, Apd e IPD, Implementation). Quando un campo non è definito per un tipo di descrittore, non è necessaria per tutte le funzioni che utilizzano tale descrittore.  
  
 I campi che è possibile accedere tramite **SQLGetDescField** necessariamente non possono essere impostate da **SQLSetDescField**. I campi che possono essere impostati da **SQLSetDescField** sono elencati nelle tabelle seguenti.  
  
 L'inizializzazione di campi di intestazione è descritta nella tabella che segue.  
  
|Nome di campo di intestazione|Tipo|L/S|Valore predefinito|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: APD R: R IRD: R IPD: R|ARD: SQL_DESC_ALLOC_AUTO per implicita o SQL_DESC_ALLOC_USER per esplicita<br /><br /> APD: SQL_DESC_ALLOC_AUTO per implicita o SQL_DESC_ALLOC_USER per esplicita<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN|ARD: L/S APD: L/S IRD: inutilizzati IPD: inutilizzati|ARD: APD [1]: [1] IRD: inutilizzati IPD: inutilizzati|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLUSMALLINT *|ARD: L/S APD: IRD L/S: IPD L/S: L/S|ARD: Null ptr APD: Null ptr IRD: Null ptr IPD: Null ptr|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN *|ARD: L/S APD: L/S IRD: inutilizzati IPD: inutilizzati|ARD: Null ptr APD: Null ptr IRD: inutilizzati IPD: inutilizzati|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: L/S APD: L/S IRD: inutilizzati IPD: inutilizzati|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: inutilizzati<br /><br /> IPD: inutilizzati|  
SQL_DESC_COUNT|SQLSMALLINT|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: APD 0: IRD 0: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN *|ARD: APD inutilizzati: IRD inutilizzato: IPD L/S: L/S|ARD: APD inutilizzati: IRD inutilizzato: Null ptr IPD: Null ptr|  
  
 [1] questi campi vengono definiti solo quando il IPD viene popolato automaticamente dal driver. Se non sono definiti. Se un'applicazione tenta di impostare questi campi, SQLSTATE HY091 verrà restituito (identificatore di campo del descrittore non valido).  
  
 L'inizializzazione di campi di record è come illustrato nella tabella seguente.  
  
|Nome del campo di record|Tipo|L/S|Valore predefinito|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: APD inutilizzati: IRD inutilizzato: R IPD: R|ARD: APD inutilizzati: IRD inutilizzato: D IPD: D [1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: SQL_C_ PREDEFINITO APD: SQL_C_ PREDEFINITO IRD: D IPD: ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER|ARD: L/S APD: L/S IRD: inutilizzati IPD: inutilizzati|ARD: Null ptr APD: Null ptr IRD: inutilizzati IPD: [2] non utilizzati|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: R IPD: R|ARD: APD inutilizzati: IRD inutilizzato: D IPD: D [1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN *|ARD: L/S APD: L/S IRD: inutilizzati IPD: inutilizzati|ARD: Null ptr APD: Null ptr IRD: inutilizzati IPD: inutilizzati|  
|SQL_DESC_LABEL|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_LENGTH|SQLULEN|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: R|ARD: APD inutilizzati: IRD inutilizzato: D IPD: D [1]|  
|SQL_DESC_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: R IPD: R|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
SQL_DESC_OCTET_LENGTH|SQLLEN|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN *|ARD: L/S APD: L/S IRD: inutilizzati IPD: inutilizzati|ARD: Null ptr APD: Null ptr IRD: inutilizzati IPD: inutilizzati|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: inutilizzati IPD: L/S|ARD: APD inutilizzati: IRD inutilizzato: inutilizzati IPD: D = SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: inutilizzati<br /><br /> APD: inutilizzati<br /><br /> IRD: R<br /><br /> IPD: R|ARD: inutilizzati<br /><br /> APD: inutilizzati<br /><br /> IRD: ND<br /><br /> IPD: ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_TABLE_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: L/S APD: IRD L/S: R IPD: L/S|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: ND|  
SQL_DESC_TYPE_NAME|SQLCHAR *|ARD: APD inutilizzati: IRD inutilizzato: R IPD: R|ARD: APD inutilizzati: IRD inutilizzato: D IPD: D [1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: R IPD: L/S|ARD: ND APD: IRD ND: D IPD: ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: R IPD: R|ARD: APD inutilizzati: IRD inutilizzato: D IPD: D [1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: APD inutilizzati: IRD inutilizzato: R IPD: inutilizzati|ARD: APD inutilizzati: IRD inutilizzato: D IPD: inutilizzati|  
  
 [1] questi campi vengono definiti solo quando il IPD viene popolato automaticamente dal driver. Se non sono definiti. Se un'applicazione tenta di impostare questi campi, SQLSTATE HY091 verrà restituito (identificatore di campo del descrittore non valido).  
  
 [2] per forzare un controllo di coerenza, è possibile impostare il IPD il campo SQL_DESC_DATA_PTR. In una chiamata successiva a **SQLGetDescField** o **SQLGetDescRec**, il driver non è necessario restituire il valore SQL_DESC_DATA_PTR è stato impostato su.  
  
## <a name="fieldidentifier-argument"></a>Argomento FieldIdentifier  
 Il *FieldIdentifier* argomento indica il campo di descrizione da impostare. Contiene un descrittore di *intestazione descrittore,* costituito da campi intestazione descritti nella sezione successiva, "Campi di intestazione," e zero o più *record del descrittore,* costituita dai campi di record descritto nella sezione dopo la sezione "Campi di intestazione".  
  
## <a name="header-fields"></a>Campi di intestazione  
 Ogni descrittore ha un'intestazione costituito dai seguenti campi:  
  
 **SQL_DESC_ALLOC_TYPE [All]**  
 Questo campo di intestazione SQLSMALLINT di sola lettura consente di specificare se il descrittore allocato automaticamente dal driver o in modo esplicito dall'applicazione. L'applicazione può ottenere, ma non modificare, questo campo. Il campo è impostato su SQL_DESC_ALLOC_AUTO dal driver, se il descrittore allocato automaticamente dal driver. È impostato per SQL_DESC_ALLOC_USER dal driver se il descrittore è stato allocato in modo esplicito dall'applicazione.  
  
 **SQL_DESC_ARRAY_SIZE [descrittori applicazione]**  
 In ARDs, questo campo di intestazione SQLULEN specifica il numero di righe nel set di righe. Il numero di righe restituito da una chiamata a **SQLFetch** o **SQLFetchScroll** o per essere utilizzato da una chiamata a **SQLBulkOperations** o **SQLSetPos** .  
  
 In Apd, questo campo di intestazione SQLULEN specifica il numero di valori per ogni parametro.  
  
 Il valore predefinito di questo campo è 1. Se è maggiore di 1, SQL_DESC_ARRAY_SIZE SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR del APD o ARD puntare alle matrici. La cardinalità di ogni matrice è uguale al valore di questo campo.  
  
 Questo campo nel ARD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_ROW_ARRAY_SIZE. Questo campo in APD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_PARAMSET_SIZE.  
  
 **SQL_DESC_ARRAY_STATUS_PTR [All]**  
 Per ogni tipo di descrittore questo SQLUSMALLINT * punti campo di intestazione in una matrice di valori SQLUSMALLINT. Queste matrici sono denominate come segue: riga di matrice di stato (IRD), la matrice di stato parametri (IPD), riga operazione matrice (ARD) e matrice di parametri operazione (APD).  
  
 Nell'implementazione, questo campo di intestazione punta a una matrice di stato di riga che contiene i valori di stato dopo una chiamata a **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, o **SQLSetPos**. La matrice dispone di molti elementi sono presenti righe nel set di righe. L'applicazione deve allocare una matrice di SQLUSMALLINTs e impostare questo campo in modo che punti alla matrice. Per impostazione predefinita, il campo è impostato su un puntatore null. Il driver popolerà la matrice, a meno che il campo SQL_DESC_ARRAY_STATUS_PTR è impostato su un puntatore null, nel qual caso in cui non vengono generati valori di stato e la matrice non viene popolata.  
  
> [!CAUTION]  
>  Se l'applicazione imposta gli elementi della matrice di stato di riga a cui fa riferimento il campo SQL_DESC_ARRAY_STATUS_PTR di implementazione non è definito il comportamento del driver.  
  
 La matrice viene popolata mediante una chiamata a **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, o **SQLSetPos**. Se la chiamata non restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il contenuto della matrice a cui fa riferimento questo campo è definito. Gli elementi nella matrice possono contenere i seguenti valori:  
  
-   SQL_ROW_SUCCESS: La riga è stata recuperata correttamente e non è stato modificato dopo l'ultimo recupero.  
  
-   SQL_ROW_SUCCESS_WITH_INFO: La riga è stata recuperata correttamente e non è stato modificato dopo l'ultimo recupero. Tuttavia, è stato restituito un avviso sulla riga.  
  
-   SQL_ROW_ERROR: Si è verificato un errore durante il recupero della riga.  
  
-   SQL_ROW_UPDATED: La riga è stata recuperata correttamente ed è stata aggiornata dopo l'ultimo recupero. Se la riga viene recuperata di nuovo, il relativo stato è SQL_ROW_SUCCESS.  
  
-   SQL_ROW_DELETED: La riga è stata eliminata dopo l'ultimo recupero.  
  
-   SQL_ROW_ADDED: La riga inserita da **SQLBulkOperations**. Se la riga viene recuperata di nuovo, il relativo stato è SQL_ROW_SUCCESS.  
  
-   SQL_ROW_NOROW: Il set di righe sovrapposti la fine del set di risultati ed è stata restituita alcuna riga che corrisponde a questo elemento della matrice di stato di riga.  
  
 Questo campo nell'implementazione può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_ROW_STATUS_PTR.  
  
 Il campo SQL_DESC_ARRAY_STATUS_PTR di implementazione è valido solo dopo che è stato restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO. Se il codice restituito non è uno di questi, il percorso a cui puntato SQL_DESC_ROWS_PROCESSED_PTR è definito.  
  
 In IPD, questo campo di intestazione punta a una matrice di parametri stato contenente informazioni sullo stato per ogni set di valori di parametro dopo una chiamata a **SQLExecute** o **SQLExecDirect**. Se la chiamata a **SQLExecute** o **SQLExecDirect** non ha restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il contenuto della matrice a cui fa riferimento questo campo non sono definiti. L'applicazione deve allocare una matrice di SQLUSMALLINTs e impostare questo campo in modo che punti alla matrice. Il driver popolerà la matrice, a meno che il campo SQL_DESC_ARRAY_STATUS_PTR è impostato su un puntatore null, nel qual caso in cui non vengono generati valori di stato e la matrice non viene popolata. Gli elementi nella matrice possono contenere i seguenti valori:  
  
-   SQL_PARAM_SUCCESS: L'istruzione SQL è stata eseguita correttamente per questo set di parametri.  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: L'istruzione SQL è stata eseguita correttamente per questo set di parametri. Tuttavia, le informazioni sull'avviso è disponibile nella struttura di dati di diagnostica.  
  
-   SQL_PARAM_ERROR: Si è verificato un errore durante l'elaborazione di questo set di parametri. Informazioni aggiuntive sull'errore è disponibile nella struttura di dati di diagnostica.  
  
-   SQL_PARAM_UNUSED: Il set di parametri è stato inutilizzato, probabilmente dovuto al fatto che alcuni set di parametri precedente ha causato un errore che ha interrotto l'ulteriore elaborazione o SQL_PARAM_IGNORE è stato impostato per tale set di parametri nella matrice specificata per il SQL_DESC_ARRAY_ Campo STATUS_PTR di APD.  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: Informazioni di diagnostica non sono disponibile. Un esempio è quando il driver considera le matrici di parametri come unità monolitica e quindi non genera questo livello di informazioni sull'errore.  
  
 Questo campo nel IPD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_PARAM_STATUS_PTR.  
  
 In ARD, questo campo di intestazione punta a una matrice di operazione riga di valori che possono essere impostate dall'applicazione per indicare se deve essere ignorato per questa riga **SQLSetPos** operazioni. Gli elementi nella matrice possono contenere i seguenti valori:  
  
-   SQL_ROW_PROCEED: La riga è incluso nell'operazione bulk mediante **SQLSetPos**. (Questa impostazione non garantisce che l'operazione verrà eseguita sulla riga. Se la riga ha lo stato SQL_ROW_ERROR nella matrice di stato di riga IRD, il driver potrebbe non essere in grado di eseguire l'operazione della riga.)  
  
-   SQL_ROW_IGNORE: La riga viene escluso dall'operazione bulk utilizzando **SQLSetPos**.  
  
 Se nessun elemento della matrice è impostato, tutte le righe sono inclusi nell'operazione di blocco. Se il valore nel campo SQL_DESC_ARRAY_STATUS_PTR del ARD è un puntatore null, tutte le righe sono inclusi nell'operazione di blocco; l'interpretazione è la stessa a cui punta il puntatore a una matrice valida e tutti gli elementi della matrice sono stati SQL_ROW_PROCEED. Se un elemento nella matrice è impostato su SQL_ROW_IGNORE, è possibile che il valore nella matrice di stato di riga per riga ignorata non viene modificato.  
  
 Questo campo nel ARD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_ROW_OPERATION_PTR.  
  
 In APD, questo campo di intestazione punta a una matrice di operazione di parametri dei valori che possono essere impostate dall'applicazione per indicare se questo set di parametri deve essere ignorata quando **SQLExecute** o **SQLExecDirect**viene chiamato. Gli elementi nella matrice possono contenere i seguenti valori:  
  
-   SQL_PARAM_PROCEED: In cui è incluso il set di parametri di **SQLExecute** o **SQLExecDirect** chiamare.  
  
-   SQL_PARAM_IGNORE: Il set di parametri è escluso dal **SQLExecute** o **SQLExecDirect** chiamare.  
  
 Se nessun elemento della matrice è impostato, tutti i set di parametri nella matrice vengono utilizzati la **SQLExecute** o **SQLExecDirect** chiamate. Se il valore nel campo SQL_DESC_ARRAY_STATUS_PTR di APD è un puntatore null, vengono utilizzati tutti i set di parametri. l'interpretazione è la stessa a cui punta il puntatore a una matrice valida e tutti gli elementi della matrice sono stati SQL_PARAM_PROCEED.  
  
 Questo campo in APD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_PARAM_OPERATION_PTR.  
  
 **SQL_DESC_BIND_OFFSET_PTR [descrittori applicazione]**  
 Questo SQLLEN * punti di campo di intestazione all'offset dell'associazione. È impostata su un puntatore null per impostazione predefinita. Se questo campo non è un puntatore null, il driver Dereferenzia il puntatore e aggiunge il valore dereferenziato a ognuno dei campi posticipati con un valore non null nel record del descrittore (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR) durante l'associazione a recuperare tempo e utilizza i nuovi valori di puntatore.  
  
 L'offset di associazione viene sempre aggiunto direttamente ai valori nei campi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR. Se l'offset viene modificato in un valore diverso, il nuovo valore risulta ancora aggiunto direttamente al valore di ogni campo di descrizione. Il nuovo offset non viene aggiunto per il valore del campo e per qualsiasi offset precedente.  
  
 Questo campo è un *campo posticipata*: non viene utilizzato al momento è impostata, ma viene utilizzato in un secondo momento dal driver, quando è necessario determinare gli indirizzi per i buffer di dati.  
  
 Questo campo nel ARD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_ROW_BIND_OFFSET_PTR. Questo campo nel ARD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_PARAM_BIND_OFFSET_PTR.  
  
 Per ulteriori informazioni, vedere la descrizione dell'associazione per riga in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) e [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 **SQL_DESC_BIND_TYPE [descrittori applicazione]**  
 Questo campo di intestazione SQLUINTEGER imposta l'orientamento di associazione da utilizzare per le colonne o parametri di associazione.  
  
 In ARDs, questo campo specifica l'orientamento di associazione quando **SQLFetchScroll** o **SQLFetch** viene chiamato nell'handle di istruzione associata.  
  
 Per selezionare l'associazione per colonna per le colonne, questo campo è impostato su SQL_BIND_BY_COLUMN (impostazione predefinita).  
  
 Questo campo nel ARD può essere impostato anche chiamando **SQLSetStmtAttr** con il SQL_ATTR_ROW_BIND_TYPE *attributo*.  
  
 In Apd, questo campo specifica l'orientamento di associazione da utilizzare per i parametri dinamici.  
  
 Per selezionare l'associazione per colonna per i parametri, questo campo è impostato su SQL_BIND_BY_COLUMN (impostazione predefinita).  
  
 Questo campo in APD può essere impostato anche chiamando **SQLSetStmtAttr** con il SQL_ATTR_PARAM_BIND_TYPE *attributo*.  
  
 **SQL_DESC_COUNT [All]**  
 Questo campo di intestazione SQLSMALLINT specifica l'indice in base 1 del record numero più alto che contiene dati. Quando il driver imposta la struttura dei dati per il descrittore, è necessario impostare anche il campo SQL_DESC_COUNT per visualizzare il numero di record è significativo. Quando un'applicazione alloca un'istanza di questa struttura di dati, non dispone di specificare il numero di record per riservare spazio per. Come l'applicazione specifica il contenuto dei record, il driver accetta le necessarie azioni per assicurarsi che l'handle di descrittore fa riferimento a una struttura di dati di dimensioni adeguate.  
  
 SQL_DESC_COUNT non è un conteggio di tutte le colonne di dati associati (se il campo è in un ARD) o di tutti i parametri sono associati (se il campo è in un APD), ma il numero del record del numero più alto. Se il numero più alto di colonna o parametro non è associato, SQL_DESC_COUNT viene modificato il numero di colonna numero più alto successivo o del parametro. Se una colonna o un parametro con un numero che è inferiore al numero della colonna numero più alto viene disassociato (chiamando **SQLBindCol** con il *TargetValuePtr* argomento impostato su un puntatore null o **SQLBindParameter** con il *ParameterValuePtr* argomento impostato su un puntatore null), SQL_DESC_COUNT non viene modificato. Se con un numero maggiore del numero più alto record che contiene i dati sono associati parametri o colonne aggiuntive, il driver aumenta automaticamente il valore nel campo SQL_DESC_COUNT. Se tutte le colonne sono associate chiamando **SQLFreeStmt** con l'opzione SQL_UNBIND, i campi SQL_DESC_COUNT ARD e IRD vengono impostati su 0. Se **SQLFreeStmt** viene chiamato con l'opzione SQL_RESET_PARAMS, i campi SQL_DESC_COUNT in APD e IPD vengono impostati su 0.  
  
 Il valore in SQL_DESC_COUNT può essere impostato in modo esplicito da un'applicazione chiamando **SQLSetDescField**. Se il valore in SQL_DESC_COUNT in modo esplicito è ridotto, tutti i record con un numero maggiore del valore nuovo in SQL_DESC_COUNT vengono rimossi in modo efficace. Se il valore in SQL_DESC_COUNT è impostato esplicitamente su 0 e il campo in un ARD, vengono rilasciati tutti i buffer di dati, ad eccezione di una colonna del segnalibro associato.  
  
 Il numero di record in questo campo di un ARD non include una colonna del segnalibro associato. L'unico modo per separare una colonna del segnalibro è impostare il campo SQL_DESC_DATA_PTR su un puntatore null.  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [descrittori di implementazione]**  
 In un'implementazione, questa SQLULEN \* punti di campo di intestazione in un buffer contenente il numero di righe recuperate dopo una chiamata a **SQLFetch** o **SQLFetchScroll**, o il numero di righe interessate in un'operazione bulk eseguita da una chiamata a **SQLBulkOperations** o **SQLSetPos**, incluse le righe di errore.  
  
 In un IPD, questo SQLUINTEGER * punti di campo di intestazione in un buffer contenente il numero di set di parametri che sono stati elaborati, compresi i set di errore. Se si tratta di un puntatore null, non verrà restituito alcun numero.  
  
 SQL_DESC_ROWS_PROCESSED_PTR è valido solo dopo che ha restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO dopo una chiamata a **SQLFetch** o **SQLFetchScroll** (per un campo IRD) o **SQLExecute** , **SQLExecDirect**, o **SQLParamData** (per un campo IPD). Se la chiamata che viene riempito il buffer a cui fa riferimento questo campo non viene restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il contenuto del buffer non è definito, a meno che non restituisce SQL_NO_DATA, nel qual caso il valore nel buffer è impostato su 0.  
  
 Questo campo nel ARD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_ROWS_FETCHED_PTR. Questo campo in APD può essere impostato anche chiamando **SQLSetStmtAttr** con l'attributo SQL_ATTR_PARAMS_PROCESSED_PTR.  
  
 Il buffer a cui fa riferimento questo campo viene allocato dall'applicazione. È un buffer di output posticipata impostato dal driver. È impostata su un puntatore null per impostazione predefinita.  
  
## <a name="record-fields"></a>I campi di record  
 Ogni descrittore contiene uno o più record costituita dai campi che definiscono i dati della colonna o i parametri dinamici, a seconda del tipo del descrittore. Ogni record è una definizione completa di una singola colonna o parametro.  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]**  
 Questo campo di record SQLINTEGER di sola lettura contiene SQL_TRUE se la colonna è una colonna a incremento automatico o SQL_FALSE se la colonna non è una colonna a incremento automatico. Questo campo è di sola lettura, ma la colonna a incremento automatico sottostante non è necessariamente di sola lettura.  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contiene il nome di colonna di base per colonna del set di risultati. Se non esiste un nome di colonna di base (come nel caso di colonne che sono espressioni), questa variabile contiene una stringa vuota.  
  
 **SQL_DESC_BASE_TABLE_NAME [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contiene il nome della tabella di base per colonna del set di risultati. Se un nome di tabella di base non può essere definito o non è applicabile, questa variabile contiene una stringa vuota.  
  
 **SQL_DESC_CASE_SENSITIVE [descrittori di implementazione]**  
 Questo campo di record SQLINTEGER di sola lettura contiene SQL_TRUE se la colonna o il parametro viene trattato come tra maiuscole e minuscole per le regole di confronto e i confronti o SQL_FALSE se la colonna non viene considerata come tra maiuscole e minuscole per i confronti e regole di confronto o se è non di un tipo di carattere colonna.  
  
 **SQL_DESC_CATALOG_NAME [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contiene il catalogo per la tabella di base che contiene la colonna. Il valore restituito è dipendente dal driver, se la colonna è un'espressione o se la colonna fa parte di una vista. Se l'origine dati non supporta cataloghi o non è possibile determinare il catalogo, questa variabile contiene una stringa vuota.  
  
 **SQL_DESC_CONCISE_TYPE [All]**  
 Questo campo di intestazione SQLSMALLINT specifica il tipo di dati conciso per tutti i tipi di dati, inclusi i tipi di dati datetime e interval.  
  
 I valori nei campi SQL_DESC_CONCISE_TYPE SQL_DESC_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE sono interdipendenti. Ogni volta che uno dei campi è impostata, l'altro deve essere impostato. SQL_DESC_CONCISE_TYPE può essere impostata da una chiamata a **SQLBindCol** o **SQLBindParameter**, o **SQLSetDescField**. SQL_DESC_TYPE può essere impostata da una chiamata a **SQLSetDescField** o **SQLSetDescRec**.  
  
 Se SQL_DESC_CONCISE_TYPE è impostata su un tipo di dati conciso diverso da un tipo di dati di intervallo o datetime, il campo SQL_DESC_TYPE è impostato sullo stesso valore e il campo SQL_DESC_DATETIME_INTERVAL_CODE è impostato su 0.  
  
 Se SQL_DESC_CONCISE_TYPE è impostata per il tipo di dati datetime o intervallo breve, il campo SQL_DESC_TYPE è impostato per il corrispondente tipo verbose (SQL_DATETIME o SQL_INTERVAL) e il campo SQL_DESC_DATETIME_INTERVAL_CODE è impostato per il codice appropriato secondario.  
  
 **SQL_DESC_DATA_PTR [descrittori di applicazioni e nei]**  
 Questo campo di record SQLPOINTER punta a una variabile che conterrà il valore del parametro (per Apd) o il valore della colonna (per ARDs). Questo campo è un *campo posticipata*. Non è utilizzato al momento è impostata, ma il driver viene utilizzato in un secondo momento per recuperare i dati.  
  
 Se non è associata alla colonna specificata per il campo SQL_DESC_DATA_PTR del ARD il *TargetValuePtr* argomento in una chiamata a **SQLBindCol** è un puntatore null o se il campo di SQL_DESC_DATA_PTR il ARD viene impostata da un chiamata a **SQLSetDescField** o **SQLSetDescRec** a un puntatore null. Se il campo SQL_DESC_DATA_PTR è impostato su un puntatore null, i campi non sono interessati.  
  
 Se la chiamata a **SQLFetch** o **SQLFetchScroll** che operazioni di inserimento nel buffer a cui fa riferimento questo campo non ha restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il contenuto del buffer non è definito.  
  
 Ogni volta che il campo SQL_DESC_DATA_PTR del APD, ARD o IPD è impostato, il driver verificherà che il valore nel campo SQL_DESC_TYPE contiene uno dei tipi di dati C ODBC validi o un tipo di dati specifici del driver, e che tutti gli altri campi che interessano i tipi di dati siano coerenti. Che richiede una verifica coerenza è il solo utilizzo del campo SQL_DESC_DATA_PTR un IPD. In particolare, se un'applicazione imposta il campo SQL_DESC_DATA_PTR di un IPD e le chiamate successive **SQLGetDescField** su questo campo, non viene necessariamente restituito il valore di cui era stata impostata. Per ulteriori informazioni, vedere "Verifiche coerenza" nella [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [All]**  
 Questo campo SQLSMALLINT di record contiene il codice secondario per il tipo di dati datetime o intervallo specifico quando il campo SQL_DESC_TYPE è SQL_DATETIME o SQL_INTERVAL. Questo vale per i tipi di dati C e SQL. Il codice costituito il nome del tipo di dati con "CODE" sostituito "Tipo" o "C_TYPE" (per i tipi di data/ora), o "CODE" sostituisce "Intervallo" o "C_INTERVAL" (per i tipi di intervallo).  
  
 Se SQL_DESC_TYPE SQL_DESC_CONCISE_TYPE in un descrittore di applicazione sono impostate su SQL_C_DEFAULT e il descrittore non è associato a un handle di istruzione, il contenuto di SQL_DESC_DATETIME_INTERVAL_CODE è definito.  
  
 Questo campo può essere impostato per i tipi di dati Data/ora elencati nella tabella seguente.  
  
|Tipi DateTime|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|TIPO SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP / SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 Questo campo può essere impostato per i tipi di dati di intervallo elencati nella tabella seguente.  
  
|Tipo di intervallo|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY / SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR / SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE / SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND / SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR / SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
QL_INTERVAL_HOUR_TO_MINUTE / SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND / SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE / SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND / SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH / SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
QL_INTERVAL_SECOND / SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR / SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH / SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 Per ulteriori informazioni sugli intervalli di dati e questo campo, vedere [gli identificatori di tipo di dati e i descrittori](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [All]**  
 Questo campo di record SQLINTEGER contiene l'intervallo di precisione iniziale, se il campo SQL_DESC_TYPE è SQL_INTERVAL. Quando il campo SQL_DESC_DATETIME_INTERVAL_CODE è impostato su un tipo di dati di intervallo, questo campo è impostato per l'intervallo predefinito di precisione iniziale.  
  
 **SQL_DESC_DISPLAY_SIZE [IRDs]**  
 Questo campo di record SQLINTEGER di sola lettura contiene il numero massimo di caratteri necessari per visualizzare i dati dalla colonna.  
  
 **SQL_DESC_FIXED_PREC_SCALE [descrittori di implementazione]**  
 Questo campo di record SQLSMALLINT di sola lettura è impostato su SQL_TRUE se la colonna è una colonna numerica esatta e ha precisione e scala diverso da zero o a SQL_FALSE se la colonna non è una colonna numerica esatto con scala e precisione fisse.  
  
 **SQL_DESC_INDICATOR_PTR [descrittori applicazione]**  
 In ARDs, questo SQLLEN * registrare punti campo alla variabile dell'indicatore. Questa variabile contiene SQL_NULL_DATA se il valore della colonna è un valore NULL. Per Apd, la variabile indicatore è impostata su SQL_NULL_DATA per specificare gli argomenti dinamici NULL. In caso contrario, la variabile è zero (a meno che i valori in SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR sono lo stesso puntatore).  
  
 Se il campo SQL_DESC_INDICATOR_PTR un ARD è un puntatore null, il driver viene impedito di restituzione di informazioni su se la colonna è NULL o non. Se la colonna è NULL e SQL_DESC_INDICATOR_PTR è un puntatore null, SQLSTATE 22002 (variabile indicatore necessaria ma non specificato) viene restituito quando il driver tenta di popolare i buffer dopo una chiamata a **SQLFetch** o  **SQLFetchScroll**. Se la chiamata a **SQLFetch** o **SQLFetchScroll** non ha restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il contenuto del buffer non sono definiti.  
  
 Il campo SQL_DESC_INDICATOR_PTR determina se il campo a cui puntato SQL_DESC_OCTET_LENGTH_PTR è impostato. Se il valore di dati per una colonna è NULL, il driver imposta la variabile indicatore su SQL_NULL_DATA. Il campo a cui puntato SQL_DESC_OCTET_LENGTH_PTR non viene quindi impostato. Se un valore NULL non viene rilevato durante l'operazione di recupero, il buffer a cui puntato SQL_DESC_INDICATOR_PTR è impostato su zero e il buffer a cui puntato SQL_DESC_OCTET_LENGTH_PTR è impostato sulla lunghezza dei dati.  
  
 Se il campo SQL_DESC_INDICATOR_PTR un APD è un puntatore null, l'applicazione non è possibile utilizzare questo record del descrittore per specificare gli argomenti NULL.  
  
 Questo campo è un *campo posticipata*: non viene utilizzato al momento è impostata, ma viene utilizzato in un secondo momento dal driver per indicare l'ammissione di valori null (per ARDs) o per determinare l'ammissione di valori null (per Apd).  
  
 **SQL_DESC_LABEL [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contiene l'etichetta di colonna o il titolo. Se la colonna non dispone di un'etichetta, questa variabile contiene il nome della colonna. Se la colonna è senza nome e senza etichetta, questa variabile contiene una stringa vuota.  
  
 **SQL_DESC_LENGTH [All]**  
 Questo campo di record SQLULEN è la lunghezza massima o effettiva di una stringa di caratteri in caratteri o un tipo di dati binari in byte. È la lunghezza massima per un tipo di dati a lunghezza fissa o la lunghezza effettiva per un tipo di dati a lunghezza variabile. Il valore esclude sempre il carattere di terminazione null che termina la stringa di caratteri. Per i valori il cui tipo è di tipo SQL_TYPE_DATE, SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP o uno dei tipi di dati di intervallo SQL, questo campo ha la lunghezza in caratteri della rappresentazione di stringa di caratteri del valore datetime o intervallo.  
  
 Il valore in questo campo può essere diverso dal valore per "lunghezza" come definito in ODBC 2*x*. Per ulteriori informazioni, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_LITERAL_PREFIX [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contengano uno o più caratteri che il driver riconosce come prefisso per un valore letterale di questo tipo di dati. Questa variabile contiene una stringa vuota per un tipo di dati per cui non è applicabile un prefisso letterale.  
  
 **SQL_DESC_LITERAL_SUFFIX [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contengano uno o più caratteri che il driver riconosce come un suffisso per un valore letterale di questo tipo di dati. Questa variabile contiene una stringa vuota per un tipo di dati per cui un suffisso letterale non è applicabile.  
  
 **SQL_DESC_LOCAL_TYPE_NAME [descrittori di implementazione]**  
 Questo SQLCHAR di sola lettura * campi di record contiene qualsiasi nome localizzato (native language) per il tipo di dati che può essere diverso dal nome del tipo di dati regolare. Se non è presente alcun nome localizzato, viene restituita una stringa vuota. Questo campo è solo per la visualizzazione.  
  
 **SQL_DESC_NAME [descrittori di implementazione]**  
 Questo SQLCHAR * campo del record in un descrittore della riga contiene l'alias di colonna, se applicabile. Se non si applica l'alias di colonna, viene restituito il nome della colonna. In entrambi i casi, il driver imposta il campo SQL_DESC_UNNAMED SQL_NAMED quando imposta il campo SQL_DESC_NAME. Se è presente alcun nome di colonna o un alias di colonna, il driver restituisce una stringa vuota nel campo SQL_DESC_NAME e imposta il campo SQL_DESC_UNNAMED SQL_UNNAMED.  
  
 Un'applicazione può impostare il campo SQL_DESC_NAME di un IPD per un nome di parametro o un alias per specificare i parametri di stored procedure in base al nome. (Per ulteriori informazioni, vedere [Binding Parameters by Name (Named Parameters)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md).) Il campo SQL_DESC_NAME di un IRD è un campo di sola lettura. SQLSTATE HY091 se un'applicazione tenta di impostarla viene restituito (identificatore di campo del descrittore non valido).  
  
 In IPD, Implementation, questo campo è definito se il driver non supporta parametri denominati. Se il driver supporta parametri denominati ed è in grado di descrivere i parametri, in questo campo viene restituito il nome del parametro.  
  
 **SQL_DESC_NULLABLE [descrittori di implementazione]**  
 In IRDs, questo campo di record SQLSMALLINT di sola lettura è SQL_NULLABLE se la colonna può avere valori NULL, SQL_NO_NULLS se la colonna non dispone di valori NULL o SQL_NULLABLE_UNKNOWN se non è noto se la colonna accetta valori NULL. Questo campo riguarda la colonna del set di risultati, non la colonna di base.  
  
 In IPD, Implementation, questo campo è sempre impostato su SQL_NULLABLE poiché i parametri dinamici sono sempre ammette valori null e non possono essere impostati da un'applicazione.  
  
 **SQL_DESC_NUM_PREC_RADIX [All]**  
 Questo campo SQLINTEGER contiene un valore pari a 2 se il tipo di dati nel campo SQL_DESC_TYPE è un tipo di dati numerici approssimati, perché il campo SQL_DESC_PRECISION contiene il numero di bit. Questo campo contiene un valore pari a 10 se il tipo di dati nel campo SQL_DESC_TYPE è un tipo di dati numerici esatti, perché il campo SQL_DESC_PRECISION contiene il numero di cifre decimali. Questo campo è impostato su 0 per tutti i tipi di dati non numerici.  
  
 **SQL_DESC_OCTET_LENGTH [All]**  
 Questo campo di record SQLLEN contiene la lunghezza, espressa in byte, di una stringa di caratteri o un tipo di dati binary. Per i caratteri a lunghezza fissa o tipi binari, questa è la lunghezza effettiva in byte. Per i tipi binari o carattere a lunghezza variabile, questa è la lunghezza massima in byte. Questo valore è sempre esclude spazio per il carattere di terminazione null per i descrittori di implementazione e include sempre spazio per il carattere di terminazione null per i descrittori di applicazione. Per i dati dell'applicazione, questo campo contiene la dimensione del buffer. Per Apd, questo campo viene definito solo per i parametri di output o input/output.  
  
 **SQL_DESC_OCTET_LENGTH_PTR [descrittori applicazione]**  
 Questo SQLLEN * registrare punti campo a una variabile che conterrà la lunghezza totale in byte di un argomento dinamico (per i descrittori di parametri) o di un valore della colonna associata (per i descrittori di riga).  
  
 Per un APD, questo valore viene ignorato per tutti gli argomenti, ad eccezione di stringa di caratteri e binario. Se questo campo punta a SQL_NTS, deve essere l'argomento dinamico con terminazione null. Per indicare che un parametro associato verrà un parametro data-at-execution, un'applicazione imposta questo campo del record appropriato di APD a una variabile che, eseguire ora, conterrà il valore SQL_DATA_AT_EXEC o il risultato della macro SQL_LEN_DATA_AT_EXEC . Se è presente più di un campo di questo tipo, è possibile impostare un valore che identifica in modo univoco il parametro SQL_DESC_DATA_PTR per determinare il parametro è richiesto l'applicazione.  
  
 Se il campo OCTET_LENGTH_PTR di un ARD è un puntatore null, il driver non restituisce informazioni sulla lunghezza della colonna. Se il campo SQL_DESC_OCTET_LENGTH_PTR di un APD è un puntatore null, il driver presuppone che le stringhe di caratteri e i valori binari con terminazione null. (I valori binari non devono essere con terminazione null ma devono avere una lunghezza per evitare il troncamento).  
  
 Se la chiamata a **SQLFetch** o **SQLFetchScroll** che operazioni di inserimento nel buffer a cui fa riferimento questo campo non ha restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il contenuto del buffer non è definito. Questo campo è un *campo posticipata*. Non è utilizzato al momento è impostata, ma è utilizzata in un secondo momento dal driver per determinare o indicare la lunghezza di ottetti di dati.  
  
 **SQL_DESC_PARAMETER_TYPE [nei]**  
 Questo campo SQLSMALLINT di record è impostato su SQL_PARAM_INPUT per un parametro di input, SQL_PARAM_INPUT_OUTPUT per un parametro di input/output, SQL_PARAM_OUTPUT per un parametro di output, SQL_PARAM_INPUT_OUTPUT_STREAM per un parametro di flusso di input/output o SQL _ PARAM_OUTPUT_STREAM per un parametro di output di streaming. È impostata su SQL_PARAM_INPUT per impostazione predefinita.  
  
 Per un IPD, il campo è impostato su SQL_PARAM_INPUT per impostazione predefinita se il IPD non viene popolato automaticamente dal driver (l'attributo di istruzione SQL_ATTR_ENABLE_AUTO_IPD è SQL_FALSE). Un'applicazione deve impostare questo campo nel IPD per i parametri che non sono parametri di input.  
  
 **SQL_DESC_PRECISION [All]**  
 Questo campo SQLSMALLINT di record contiene il numero di cifre per un tipo numerico esatto, il numero di bit nella mantissa (e precisione binaria) per un tipo numerico approssimato o il numero di cifre nel componente di secondi frazionari per la SQL_TYPE_TIME, SQL_TYPE Timestamp, o SQL_INTERVAL_SECOND tipo di dati. Questo campo è definito per tutti gli altri tipi di dati.  
  
 Il valore in questo campo può essere diverso dal valore di "precisione" come definito in ODBC 2*x*. Per ulteriori informazioni, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_ROWVER [descrittori di implementazione]**  
 Questo campo SQLSMALLINTrecord indica se una colonna viene automaticamente modificata dal sistema DBMS quando viene aggiornata una riga (ad esempio, una colonna di tipo "timestamp" in SQL Server). Il valore di questo campo di record è impostato su SQL_TRUE se la colonna è una colonna del controllo delle versioni di riga e SQL_FALSE in caso contrario. L'attributo di colonna è simile alla chiamata **SQLSpecialColumns** con IdentifierType SQL_ROWVER per determinare se una colonna viene aggiornata automaticamente.  
  
 **SQL_DESC_SCALE [All]**  
 Questo campo SQLSMALLINT di record contiene scala definita per i tipi di dati decimali e numerici. Il campo non è definito per tutti gli altri tipi di dati.  
  
 Il valore in questo campo può essere diverso dal valore di "scalabilità", come definito in ODBC 2*x*. Per ulteriori informazioni, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_SCHEMA_NAME [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contiene il nome dello schema della tabella di base che contiene la colonna. Il valore restituito è dipendente dal driver, se la colonna è un'espressione o se la colonna fa parte di una vista. Se l'origine dati non supporta schemi o non è possibile determinare il nome dello schema, questa variabile contiene una stringa vuota.  
  
 **SQL_DESC_SEARCHABLE [IRDs]**  
 Questo campo di record SQLSMALLINT di sola lettura è impostato su uno dei valori seguenti:  
  
-   SQL_PRED_NONE se la colonna non può essere utilizzata in un **dove** clausola. (Questo è identico al valore SQL_UNSEARCHABLE in ODBC 2*x*.)  
  
-   SQL_PRED_CHAR se la colonna può essere utilizzata in un **in** clausola ma solo con il **come** predicato. (Questo è identico al valore SQL_LIKE_ONLY in ODBC 2*x*.)  
  
-   SQL_PRED_BASIC se la colonna può essere utilizzata in un **in** clausola con tutti gli operatori di confronto tranne **come**. (Questo è identico al valore SQL_EXCEPT_LIKE in ODBC 2*x*.)  
  
-   SQL_PRED_SEARCHABLE se la colonna può essere utilizzata in un **dove** clausola con qualsiasi operatore di confronto.  
  
 **SQL_DESC_TABLE_NAME [IRDs]**  
 Questo SQLCHAR di sola lettura * campi di record contiene il nome della tabella di base che contiene questa colonna. Il valore restituito è dipendente dal driver, se la colonna è un'espressione o se la colonna fa parte di una vista.  
  
 **SQL_DESC_TYPE [All]**  
 Questo campo di record SQLSMALLINT specifica il tipo di dati di conciso SQL o C per tutti i tipi di dati tranne i tipi di dati datetime e interval. Per i tipi di dati datetime e interval, questo campo specifica il tipo di dati dettagliati, che è SQL_DATETIME o SQL_INTERVAL.  
  
 Ogni volta che questo campo contiene SQL_DATETIME o SQL_INTERVAL, il campo SQL_DESC_DATETIME_INTERVAL_CODE deve contenere il codice secondario appropriato per il tipo conciso. Per i tipi di dati datetime, SQL_DESC_TYPE contiene SQL_DATETIME e il campo SQL_DESC_DATETIME_INTERVAL_CODE contiene un codice secondario per il tipo di dati datetime specifico. Per i tipi di dati di intervallo, SQL_DESC_TYPE contiene SQL_INTERVAL e il campo SQL_DESC_DATETIME_INTERVAL_CODE contiene un codice secondario per il tipo di dati di intervallo specifico.  
  
 I valori nei campi SQL_DESC_TYPE e SQL_DESC_CONCISE_TYPE sono interdipendenti. Ogni volta che uno dei campi è impostata, l'altro deve essere impostato. SQL_DESC_TYPE può essere impostata da una chiamata a **SQLSetDescField** o **SQLSetDescRec**. SQL_DESC_CONCISE_TYPE può essere impostata da una chiamata a **SQLBindCol** o **SQLBindParameter**, o **SQLSetDescField**.  
  
 Se SQL_DESC_TYPE è impostato su un tipo di dati conciso diverso da un tipo di dati di intervallo o datetime, il campo SQL_DESC_CONCISE_TYPE è impostato sullo stesso valore e il campo SQL_DESC_DATETIME_INTERVAL_CODE è impostato su 0.  
  
 Se SQL_DESC_TYPE è impostato su dettagliato valore datetime o tipo di dati di intervallo (SQL_DATETIME o SQL_INTERVAL) e il campo SQL_DESC_DATETIME_INTERVAL_CODE è impostato per il codice appropriato secondario, il campo tipo SQL_DESC_CONCISE è impostato per il tipo conciso corrispondente. Tentativo di impostare SQL_DESC_TYPE su uno dei tipi di valore datetime o intervallo concisi restituiranno SQLSTATE HY021 (le informazioni del descrittore incoerenti).  
  
 Quando il campo SQL_DESC_TYPE è impostato da una chiamata a **SQLBindCol**, **SQLBindParameter**, o **SQLSetDescField**, i campi seguenti vengono impostati sui valori predefiniti seguenti, come illustrato nella tabella seguente. I valori dei campi rimanenti dello stesso record sono definiti.  
  
|Valore di SQL_DESC_TYPE|Gli altri campi impostati in modo implicito|  
|------------------------------|---------------------------------|  
|SQL_CHAR, SQL_VARCHAR, SQL_C_CHAR SQL_C_VARCHAR|SQL_DESC_LENGTH è impostato su 1. SQL_DESC_PRECISION è impostato su 0.|  
|SQL_DATETIME|Quando SQL_DESC_DATETIME_INTERVAL_CODE è impostato su SQL_CODE_DATE o SQL_CODE_TIME, SQL_DESC_PRECISION è impostato su 0. Quando è impostata su SQL_DESC_TIMESTAMP, SQL_DESC_PRECISION è impostata su 6.|  
|SQL_C_NUMERIC SQL_DECIMAL, SQL_NUMERIC,|SQL_DESC_SCALE è impostato su 0. SQL_DESC_PRECISION è impostato per la precisione del tipo di dati definito dall'implementazione.<br /><br /> Vedere [SQL per c: numerico](../../../odbc/reference/appendixes/sql-to-c-numeric.md) per informazioni su come associare manualmente un valore SQL_C_NUMERIC.|  
|SQL_FLOAT, SQL_C_FLOAT|SQL_DESC_PRECISION è impostato per la precisione predefinita definita dall'implementazione per SQL_FLOAT.|  
|SQL_INTERVAL|Quando SQL_DESC_DATETIME_INTERVAL_CODE è impostata su un tipo di dati di intervallo, SQL_DESC_DATETIME_INTERVAL_PRECISION è impostato su 2 (la precisione iniziale intervallo predefinita). Quando l'intervallo è un componente di secondi, SQL_DESC_PRECISION è impostata su 6 (precisione secondi intervallo predefinito).|  
  
 Quando un'applicazione chiama **SQLSetDescField** per impostare i campi di un descrittore anziché chiamare **SQLSetDescRec**, l'applicazione prima di tutto necessario dichiarare il tipo di dati. In questo caso, gli altri campi indicati nella tabella precedente sono impostati in modo implicito. Se uno dei valori in modo implicito set è accettabile, l'applicazione può quindi chiamare **SQLSetDescField** o **SQLSetDescRec** per impostare in modo esplicito il valore non valido.  
  
 **Descrizione SQL_DESC_TYPE_NAME [descrittori di implementazione]**  
 Questo SQLCHAR di sola lettura * campi di record contiene il nome di tipo dipende dall'origine dati (ad esempio, "CHAR", "VARCHAR" e così via). Se il nome del tipo di dati è sconosciuto, questa variabile contiene una stringa vuota.  
  
 **SQL_DESC_UNNAMED [descrittori di implementazione]**  
 Questo campo di record SQLSMALLINT un descrittore della riga è impostato dal driver per SQL_NAMED o SQL_UNNAMED quando imposta il campo SQL_DESC_NAME. Se il campo SQL_DESC_NAME contiene un alias di colonna o se non si applica l'alias di colonna, il driver imposta il campo SQL_DESC_UNNAMED per SQL_NAMED. Se un'applicazione imposta il campo SQL_DESC_NAME di un IPD per un nome di parametro o un alias, il driver imposta il campo SQL_DESC_UNNAMED del IPD per SQL_NAMED. Se è presente alcun nome di colonna o un alias di colonna, il driver imposta il campo SQL_DESC_UNNAMED SQL_UNNAMED.  
  
 Un'applicazione può impostare il campo SQL_DESC_UNNAMED di un IPD per SQL_UNNAMED. Un driver restituisce SQLSTATE HY091 (identificatore di campo del descrittore non valido) se un'applicazione tenta di impostare il campo SQL_DESC_UNNAMED di un IPD su SQL_NAMED. Il campo SQL_DESC_UNNAMED di un IRD è di sola lettura. SQLSTATE HY091 se un'applicazione tenta di impostarla viene restituito (identificatore di campo del descrittore non valido).  
  
 **SQL_DESC_UNSIGNED [descrittori di implementazione]**  
 Questo campo di record SQLSMALLINT di sola lettura è SQL_TRUE se il tipo di colonna è senza segno o non numerico oppure SQL_FALSE se il tipo di colonna è firmato.  
  
 **SQL_DESC_UPDATABLE [IRDs]**  
 Questo campo di record SQLSMALLINT di sola lettura è impostato su uno dei valori seguenti:  
  
-   SQL_ATTR_READ_ONLY se colonna del set di risultati è di sola lettura.  
  
-   SQL_ATTR_WRITE se colonna del set di risultati è di lettura / scrittura.  
  
-   SQL_ATTR_READWRITE_UNKNOWN se non è noto se colonna del set di risultati è aggiornabile o meno.  
  
 SQL_DESC_UPDATABLE descrive l'aggiornabilità della colonna nel set di risultati, non la colonna nella tabella di base. L'aggiornabilità della colonna nella tabella di base in cui è in questa colonna del set di risultati potrebbe essere diverso rispetto al valore in questo campo. Se una colonna è aggiornabile può basarsi sul tipo di dati, i privilegi di utente e la definizione di se stesso set di risultati. Se non è chiaro se una colonna è aggiornabile, SQL_ATTR_READWRITE_UNKNOWN deve essere restituito.  
  
## <a name="consistency-checks"></a>Verifiche di coerenza  
 Un controllo di coerenza viene eseguito automaticamente dal driver ogni volta che un'applicazione passa un valore per il campo SQL_DESC_DATA_PTR del ARD, APD o IPD. Se uno dei campi è incoerente con gli altri campi, **SQLSetDescField** restituiranno SQLSTATE HY021 (le informazioni del descrittore incoerenti). Per ulteriori informazioni, vedere "Verifica di coerenza" nella [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di una colonna|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Associazione di un parametro|[Funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Recupero di un campo di descrizione|[Funzione SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Recupero di più campi di descrizione|[Funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|L'impostazione di più campi di descrizione|[Funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Riferimento API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)
