---
title: Funzione SQLColAttribute | Documenti Microsoft
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
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5afbe6bbea4e1c50e3b16742bf5d0fa1b3c16a9d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolattribute-function"></a>Funzione SQLColAttribute
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLColAttribute** restituisce informazioni sul descrittore per una colonna in un set di risultati. Informazioni del descrittore viene restituite come una stringa di caratteri, un dipendente dal descrittore di valore o un valore intero.  
  
> [!NOTE]  
>  Per ulteriori informazioni su quali il Driver Manager esegue il mapping di questa funzione per quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2. *x* driver, vedere [Mapping di funzioni di sostituzione per la compatibilità con le versioni precedenti di applicazioni](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *ColumnNumber*  
 [Input] Il numero del record di IRD da cui è possibile recuperare il valore del campo. Questo argomento corrisponde al numero di colonna di dati del risultato, ordinati in sequenza in ordine crescente di colonna, a partire da 1. Le colonne possono essere descritte in qualsiasi ordine.  
  
 Colonna 0 può essere specificato in questo argomento, ma tutti i valori tranne SQL_DESC_TYPE e SQL_DESC_OCTET_LENGTH restituirà valori non definiti.  
  
 *FieldIdentifier*  
 [Input] L'handle di descrittore. Questo handle definisce il campo di implementazione deve eseguire una query (ad esempio, SQL_COLUMN_TABLE_NAME).  
  
 *CharacterAttributePtr*  
 [Output] Puntatore a un buffer in cui restituire il valore di *FieldIdentifier* campo il *ColumnNumber* riga di implementazione, se il campo è una stringa di caratteri. In caso contrario, il campo non viene utilizzato.  
  
 Se *CharacterAttributePtr* è NULL, *StringLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntava *CharacterAttributePtr*.  
  
 *BufferLength*  
 [Input] Se *FieldIdentifier* è un campo definito ODBC e *CharacterAttributePtr* punta a una stringa di caratteri o binario buffer, la lunghezza di questo argomento deve essere \*  *CharacterAttributePtr*. Se *FieldIdentifier* è un campo definito ODBC e \* *CharacterAttribute*Ptr è un numero intero, questo campo viene ignorato. Se il  *\*CharacterAttributePtr* è una stringa Unicode (quando si chiama **SQLColAttributeW**), il *BufferLength* argomento deve essere un numero pari. Se *FieldIdentifier* è un campo definito dal driver, l'applicazione indica la natura del campo al Driver Manager impostando il *BufferLength* argomento. *BufferLength* può avere i valori seguenti:  
  
-   Se *CharacterAttributePtr* è un puntatore a un puntatore, *BufferLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se *CharacterAttributePtr* è un puntatore a una stringa di caratteri di *BufferLength* è la lunghezza del buffer.  
  
-   Se *CharacterAttributePtr* è un puntatore a un buffer binario, le posizioni dell'applicazione il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *BufferLength*. In questo modo un valore negativo in *BufferLength*.  
  
-   Se *CharacterAttributePtr* è un puntatore a un tipo di dati a lunghezza fissa, *BufferLength* deve essere uno dei seguenti: SQL_IS_INTEGER, SQL_IS_UNINTEGER, SQL_SMALLINT o SQLUSMALLINT.  
  
 *StringLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di byte (escluso il byte di terminazione null per i dati di tipo carattere) disponibile per restituire **CharacterAttributePtr*.  
  
 Per i dati di tipo carattere, se il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength*, le informazioni sul descrittore in \* *CharacterAttributePtr* viene troncato a  *BufferLength* meno la lunghezza di un carattere di terminazione null ed è con terminazione null dal driver.  
  
 Per tutti gli altri tipi di dati, il valore di *BufferLength* viene ignorato e il driver presuppone che le dimensioni di **CharacterAttributePtr* è a 32 bit.  
  
 *NumericAttributePtr*  
 [Output] Puntatore a un buffer di integer in cui restituire il valore di *FieldIdentifier* campo il *ColumnNumber* riga di implementazione, se il campo è un tipo di descrittore numerico, ad esempio SQL_DESC_COLUMN_LENGTH. In caso contrario, il campo non viene utilizzato. Si noti che alcuni driver possono scrivere solo inferiore 32 bit o a 16 bit di un buffer e lasciare il bit di ordine superiore invariata. Pertanto, le applicazioni devono inizializzare il valore su 0 prima di chiamare questa funzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLColAttribute** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType*impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLColAttribute** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *CharacterAttributePtr* non sia abbastanza grande per restituire il valore di stringa intera, pertanto il valore stringa è stato troncato. Viene restituita la lunghezza del valore di stringa non troncato **StringLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07005|Istruzione preparata non un *specifica di cursore.*|L'istruzione associata la *StatementHandle* non ha restituito un set di risultati e *FieldIdentifier* SQL_DESC_COUNT non è stato. Si sono verificati non le colonne per descrivere.|  
|07009|Indice del descrittore non valido|(DM) il valore specificato per *ColumnNumber* sia uguale a 0 e l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è SQL_UB_OFF.<br /><br /> Il valore specificato per l'argomento *ColumnNumber* è maggiore del numero di colonne nel set di risultati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagField** dai dati di diagnostica struttura descrive l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione aynchronous era ancora in esecuzione quando è stato chiamato SQLColAttribute.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata prima di chiamare la funzione **SQLPrepare**, **SQLExecDirect**, o una funzione di catalogo per il *StatementHandle*.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM)  *\*CharacterAttributePtr* è una stringa di caratteri e *BufferLength* è minore di 0 ma non è uguale a SQL_NTS.|  
|HY091|Identificatore del campo del descrittore non valido|Il valore specificato per l'argomento *FieldIdentifier* non è uno dei valori definiti e non è un valore definito dall'implementazione.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Driver non valido|Il valore specificato per l'argomento *FieldIdentifier* non è supportato dal driver.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
 Quando viene chiamato dopo **SQLPrepare** e prima **SQLExecute**, **SQLColAttribute** può restituire qualsiasi SQLSTATE che può essere restituiti da **SQLPrepare**o **SQLExecute**, a seconda di quando l'origine dati restituisce l'istruzione SQL associata la *StatementHandle*.  
  
 Per motivi di prestazioni, un'applicazione non deve chiamare **SQLColAttribute** prima di eseguire un'istruzione.  
  
## <a name="comments"></a>Commenti  
 Per informazioni sull'utilizzano tra applicazioni e le informazioni restituite da **SQLColAttribute**, vedere [metadati dei Set di risultati](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLColAttribute** restituisce informazioni sia in \* *NumericAttributePtr* o nella \* *CharacterAttributePtr*. Vengono restituite informazioni di integer in \* *NumericAttributePtr* come valore SQLLEN; vengono restituiti tutti gli altri formati di informazioni in \* *CharacterAttributePtr*. Quando vengono restituite informazioni \* *NumericAttributePtr*, il driver ignora *CharacterAttributePtr*, *BufferLength*, e  *StringLengthPtr*. Quando vengono restituite informazioni \* *CharacterAttributePtr*, il driver ignora *NumericAttributePtr*.  
  
 **SQLColAttribute** restituisce valori di campi di descrizione di implementazione. La funzione viene chiamata con un handle di istruzione anziché un handle descrittore. I valori restituiti da **SQLColAttribute** per il *FieldIdentifier* valori elencati più avanti in questa sezione possono anche essere recuperati chiamando **SQLGetDescField** con il handle IRD appropriato.  
  
 Il descrittore attualmente definito campi, la versione di ODBC in cui sono state introdotte e gli argomenti in cui vengono restituite informazioni per essi vengono visualizzati in un secondo momento in questa sezione; più tipi di descrittore possono essere definiti dai driver per sfruttare i vantaggi di origini dati diverse.  
  
 Un database ODBC 3. *x* driver deve restituire un valore per ognuno dei campi di descrizione. Se un campo di descrizione non viene applicata a un'origine dati o i driver e se non diversamente specificato, il driver restituisce 0 in \* *StringLengthPtr* o una stringa vuota in **CharacterAttributePtr*.  
  
## <a name="backward-compatibility"></a>Compatibilità con le versioni precedenti  
 ODBC 3. *x* funzione **SQLColAttribute** sostituisce deprecate ODBC 2. *x* funzione **SQLColAttributes**. Quando il mapping di **SQLColAttributes** a **SQLColAttribute** (quando un ODBC 2. *x* applicazione funziona con un'applicazione ODBC 3. *x* driver), o mapping **SQLColAttribute** a **SQLColAttributes** (quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2. *x* driver), gestione Driver sia passa il valore di *FieldIdentifier* tramite, ne esegue il mapping a un nuovo valore, o restituisce un errore, come indicato di seguito:  
  
> [!NOTE]  
>  Il prefisso utilizzato *FieldIdentifier* valori in ODBC 3. *x* è stato modificato da tali utilizzati in ODBC 2. *x*. Il prefisso è "SQL_DESC"; il prefisso precedente era "SQL_COLUMN".  
  
-   Se il **#define** valore ODBC 2. *x* *FieldIdentifier* è lo stesso come il **#define** valore ODBC 3. *x* *FieldIdentifier*, viene passato attraverso il valore nella chiamata di funzione.  
  
-   Il **#define** valori di ODBC 2. *x* *FieldIdentifiers* SQL_COLUMN_LENGTH, SQL_COLUMN_PRECISION e SQL_COLUMN_SCALE sono diversi dal **#define** valori di ODBC 3. *x* *FieldIdentifiers* SQL_DESC_SCALE o SQL_DESC_PRECISION e SQL_DESC_LENGTH. Un database ODBC 2. *x* driver solo deve supportare l'API ODBC 2. *x* valori. Un database ODBC 3. *x* driver deve supportare sia "SQL_COLUMN" e "SQL_DESC" valori per questi tre *FieldIdentifiers*. Questi valori sono diversi perché precisione, scala e lunghezza vengono definite in modo diverso in ODBC 3. *x* rispetto alle API ODBC 2. *x*. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
-   Se il **#define** valore ODBC 2. *x* *FieldIdentifier* è diverso dal **#define** valore ODBC 3. *x* *FieldIdentifier*, come avviene con il numero, nome, e viene eseguito il mapping di valori NULLABLE, il valore nella chiamata di funzione per il valore corrispondente. Ad esempio, viene eseguito il mapping SQL_COLUMN_COUNT a SQL_DESC_COUNT, e viene eseguito il mapping di SQL_DESC_COUNT a SQL_COLUMN_COUNT, a seconda della direzione del mapping.  
  
-   Se *FieldIdentifier* è un nuovo valore in ODBC 3. *x*, per cui si è verificato alcun valore corrispondente in ODBC 2. *x*, non vengono mappato quando un'applicazione ODBC 3. *x* applicazione viene utilizzato in una chiamata a **SQLColAttribute** in un'API ODBC 2. *x* driver e la chiamata restituirà HY091 SQLSTATE (identificatore di campo del descrittore non valido).  
  
 Nella tabella seguente sono elencati i tipi di descrittore restituiti da **SQLColAttribute**. Il tipo per *NumericAttributePtr* valori **SQLLEN \*** .  
  
|*FieldIdentifier*|Informazioni<br /><br /> restituito in|Description|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE se la colonna è una colonna a incremento automatico.<br /><br /> SQL_FALSE se la colonna non è una colonna a incremento automatico o non è numerica.<br /><br /> Questo campo è valido per solo colonne di tipo di dati numerici. Un'applicazione può inserire valori in una riga contenente una colonna autoincrement, ma in genere non è possibile aggiornare i valori nella colonna.<br /><br /> Quando un'operazione di inserimento viene effettuata in una colonna autoincrement, viene inserito un valore univoco nella colonna al momento dell'inserimento. L'incremento non è definito, ma è specifici dell'origine dati. Un'applicazione non deve presupporre che una colonna autoincrement inizia da qualsiasi punto specifico o l'incremento di un particolare valore.|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|Il nome di colonna di base per il risultato della colonna del set. Se non esiste un nome di colonna di base (come nel caso di colonne che sono espressioni), questa variabile contiene una stringa vuota.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_BASE_COLUMN_NAME di implementazione, che è un campo di sola lettura.|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Il nome della tabella di base che contiene la colonna. Se il nome della tabella di base non può essere definito o non è applicabile, questa variabile contiene una stringa vuota.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_BASE_TABLE_NAME di implementazione, che è un campo di sola lettura.|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE se la colonna viene considerata come tra maiuscole e minuscole per le regole di confronto e confronti.<br /><br /> SQL_FALSE se la colonna non viene considerata come tra maiuscole e minuscole per le regole di confronto e confronti o carattere.|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|Il catalogo della tabella che contiene la colonna. Il valore restituito è definito dall'implementazione se la colonna è un'espressione o se la colonna fa parte di una vista. Se l'origine dati non supporta cataloghi o non è possibile determinare il nome del catalogo, viene restituita una stringa vuota. Questo campo di record VARCHAR non è limitato a 128 caratteri.|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*NumericAttributePtr*|Il tipo di dati conciso.<br /><br /> Per i tipi di dati datetime e interval, questo campo restituisce il tipo di dati conciso; ad esempio, SQL_TYPE_TIME o SQL_INTERVAL_YEAR. (Per ulteriori informazioni, vedere [gli identificatori di tipo di dati e i descrittori](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) appendice d: tipo di dati.)<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_CONCISE_TYPE di implementazione.|  
|SQL_DESC_COUNT (ODBC 1.0)|*NumericAttributePtr*|Il numero di colonne disponibili nel set di risultati. Restituisce 0 se non sono presenti colonne nel set di risultati. Il valore di *ColumnNumber* argomento viene ignorato.<br /><br /> Queste informazioni vengono restituite dal campo di intestazione SQL_DESC_COUNT di implementazione.|  
|COLONNE SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*NumericAttributePtr*|Numero massimo di caratteri necessari per visualizzare i dati dalla colonna. Per ulteriori informazioni sulle dimensioni di visualizzazione, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni visualizzare](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE se la colonna ha una scala e precisione fisse diverso da zero che sono specifici dell'origine dati.<br /><br /> SQL_FALSE se la colonna non ha una scala e precisione fisse diverso da zero che sono specifici dell'origine dati.|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|L'etichetta di colonna o il titolo. Ad esempio, una colonna denominata delle EmpName potrebbe essere contrassegnata come nome di dipendente o potrebbe essere denominata con un alias.<br /><br /> Se una colonna non dispone di un'etichetta, viene restituito il nome della colonna. Se la colonna è senza etichetta e senza nome, viene restituita una stringa vuota.|  
|SQL_DESC_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Un valore numerico che è la lunghezza massima o effettivo di un carattere string o binary di dati digitare. È la lunghezza massima per un tipo di dati a lunghezza fissa o la lunghezza in caratteri effettivi per un tipo di dati a lunghezza variabile. Il valore è sempre esclude il byte di terminazione null che termina la stringa di caratteri.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_LENGTH di implementazione.<br /><br /> Per ulteriori informazioni sulla lunghezza, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|Questo campo di record varchar (128) contiene uno o più caratteri che il driver riconosce come prefisso per un valore letterale di questo tipo di dati. Questo campo contiene una stringa vuota per un tipo di dati per cui non è applicabile un prefisso letterale. Per ulteriori informazioni, vedere [letterale prefissi e suffissi](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|Questo campo di record varchar (128) contiene uno o più caratteri che il driver riconosce come un suffisso per un valore letterale di questo tipo di dati. Questo campo contiene una stringa vuota per un tipo di dati per cui un suffisso letterale non è applicabile. Per ulteriori informazioni, vedere [letterale prefissi e suffissi](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Questo campo di record varchar (128) contiene qualsiasi nome localizzato (native language) per il tipo di dati che può essere diverso dal nome del tipo di dati regolare. Se non è presente alcun nome localizzato, viene restituita una stringa vuota. Questo campo è solo per la visualizzazione. Il set di caratteri della stringa dipende dalla lingua e in genere è il set di caratteri predefinito del server.|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|L'alias di colonna, se applicabile. Se non si applica l'alias di colonna, viene restituito il nome della colonna. In entrambi i casi, SQL_DESC_UNNAMED è impostato su SQL_NAMED. Se è presente alcun nome di colonna o un alias di colonna, viene restituita una stringa vuota e SQL_DESC_UNNAMED è impostato su SQL_UNNAMED.<br /><br /> Queste informazioni vengono restituite dal campo SQL_DESC_NAME record di implementazione.|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*NumericAttributePtr*|SQL _ ammette valori null se la colonna può avere valori NULL. SQL_NO_NULLS se la colonna non dispone di valori NULL. o SQL_NULLABLE_UNKNOWN se non è noto se la colonna accetta valori NULL.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_NULLABLE di implementazione.|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*NumericAttributePtr*|Se il tipo di dati nel campo SQL_DESC_TYPE è un tipo di dati numerici approssimati, questo campo SQLINTEGER contiene un valore pari a 2 perché il campo SQL_DESC_PRECISION contiene il numero di bit. Se il tipo di dati nel campo SQL_DESC_TYPE è un tipo di dati numerici esatti, questo campo contiene un valore pari a 10, perché il campo SQL_DESC_PRECISION contiene il numero di cifre decimali. Questo campo è impostato su 0 per tutti i tipi di dati non numerici.|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*NumericAttributePtr*|La lunghezza, espressa in byte, di un tipo di dati character string o binary. Per i caratteri a lunghezza fissa o tipi binari, questa è la lunghezza effettiva in byte. Per i tipi binari o carattere a lunghezza variabile, questa è la lunghezza massima in byte. Questo valore non include il carattere di terminazione null.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_OCTET_LENGTH di implementazione.<br /><br /> Per ulteriori informazioni sulla lunghezza, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.|  
|SQL_DESC_PRECISION (ODBC 3.0)|*NumericAttributePtr*|Un valore numerico che, per un tipo di dati numerici, indica la precisione applicabile. Per i dati di tipi SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, e tutti i tipi di dati di intervallo che rappresentano un intervallo di tempo, il relativo valore è la precisione del componente di secondi frazionari applicabile.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_PRECISION di implementazione.|  
|SQL_DESC_SCALE (ODBC 3.0)|*NumericAttributePtr*|Un valore numerico che rappresenta la scala applicabile per un tipo di dati numerici. Per i tipi di dati DECIMAL e NUMERIC, si tratta alla scala definita. Non è definita per tutti gli altri tipi di dati.<br /><br /> Queste informazioni vengono restituite dal campo del record di scala di implementazione.|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|Lo schema della tabella che contiene la colonna. Il valore restituito è definito dall'implementazione se la colonna è un'espressione o se la colonna fa parte di una vista. Se l'origine dati non supporta schemi o non è possibile determinare il nome dello schema, viene restituita una stringa vuota. Questo campo di record VARCHAR non è limitato a 128 caratteri.|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*NumericAttributePtr*|SQL_PRED_NONE se la colonna non può essere utilizzata in una clausola WHERE. (Questo è identico al valore SQL_UNSEARCHABLE in ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR se la colonna può essere utilizzata in una clausola WHERE, ma solo con il predicato LIKE. (Questo è identico al valore SQL_LIKE_ONLY in ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC se la colonna può essere utilizzata in una clausola WHERE con tutti gli operatori di confronto, ad eccezione di tipo. (Questo è identico al valore SQL_EXCEPT_LIKE in ODBC 2. *x*.)<br /><br /> SQL_PRED_SEARCHABLE se la colonna può essere utilizzata in una clausola WHERE con qualsiasi operatore di confronto.<br /><br /> Colonne di tipo SQL_LONGVARCHAR e SQL_LONGVARBINARY in genere restituito SQL_PRED_CHAR.|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|Nome della tabella che contiene la colonna. Il valore restituito è definito dall'implementazione se la colonna è un'espressione o se la colonna fa parte di una vista.<br /><br /> Se non è possibile determinare il nome della tabella, viene restituita una stringa vuota.|  
|SQL_DESC_TYPE (ODBC 3.0)|*NumericAttributePtr*|Un valore numerico che specifica il tipo di dati SQL.<br /><br /> Quando *ColumnNumber* è uguale a 0, viene restituito SQL_BINARY per i segnalibri a lunghezza variabile e SQL_INTEGER viene restituito per i segnalibri di lunghezza fissa.<br /><br /> Per i tipi di dati datetime e interval, questo campo restituisce il tipo di dati dettagliati: SQL_DATETIME o SQL_INTERVAL. (Per ulteriori informazioni, vedere [gli identificatori di tipo di dati e i descrittori](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) appendice d: tipo di dati.<br /><br /> Queste informazioni vengono restituite dal campo SQL_DESC_TYPE record di implementazione. **Nota:** funzionamento rispetto a ODBC 2. *x* driver, in alternativa, usare SQL_DESC_CONCISE_TYPE.|  
|DESCRIZIONE SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|Nome del tipo di dati dipende dall'origine dati; ad esempio, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" o "CHAR () FOR BIT DATA".<br /><br /> Se il tipo è sconosciuto, viene restituita una stringa vuota.|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*NumericAttributePtr*|SQL_NAMED o SQL_UNNAMED. Se il campo SQL_DESC_NAME di implementazione contiene un alias di colonna o un nome di colonna, viene restituito SQL_NAMED. Se è presente alcun nome di colonna o un alias di colonna, viene restituito SQL_UNNAMED.<br /><br /> Queste informazioni vengono restituite dal campo del record SQL_DESC_UNNAMED di implementazione.|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE se la colonna è senza segno (o non numerico).<br /><br /> SQL_FALSE se la colonna è firmata.|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*NumericAttributePtr*|Colonna verrà indicata i valori per le costanti definite:<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE descrive l'aggiornabilità della colonna nel set di risultati, non la colonna nella tabella di base. L'aggiornabilità della colonna di base su cui si basa la colonna del set di risultati potrebbe essere diverso dal valore in questo campo. Se una colonna è aggiornabile può basarsi sul tipo di dati, i privilegi di utente e la definizione di se stesso set di risultati. Se non è chiaro se una colonna è aggiornabile, SQL_ATTR_READWRITE_UNKNOWN deve essere restituito.|  
  
 **SQLColAttribute** è un'alternativa a extensible **SQLDescribeCol**. **SQLDescribeCol** restituisce un set fisso di informazioni del descrittore di base in SQL ANSI-89. **SQLColAttribute** consente l'accesso per il set più completo di informazioni sul descrittore disponibili in SQL ANSI-92 e DBMS estensioni del fornitore.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su una colonna in un set di risultati|[Funzione SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di più righe di dati|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente non libera l'handle e delle connessioni. Vedere [SQLFreeHandle-funzione](../../../odbc/reference/syntax/sqlfreehandle-function.md), [programma di esempio ODBC](../../../odbc/reference/sample-odbc-program.md), e [SQLFreeStmt-funzione](../../../odbc/reference/syntax/sqlfreestmt-function.md) per esempi di codice liberare l'handle e istruzioni.  
  
```  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;  
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   retCode = SQLNumResultCols(hstmt, &numColumn);  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Programma di esempio ODBC](../../../odbc/reference/sample-odbc-program.md)
