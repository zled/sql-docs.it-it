---
title: Funzione SQLBindCol | Documenti Microsoft
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
- SQLBindCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 641b08ab3d3aec59f66dd0405770cf19d4690769
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbindcol-function"></a>Funzione SQLBindCol
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLBindCol** associa i buffer di dati di applicazione per le colonne nel set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLBindCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *ColumnNumber*  
 [Input] Numero del risultato imposta una colonna da associare. Le colonne sono numerate in ordine crescente di colonna a partire da 0, in cui la colonna 0 è la colonna del segnalibro. Se non vengono usati i segnalibri, ovvero, ovvero l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è SQL_UB_OFF, quindi i numeri di colonna iniziano da 1.  
  
 *TargetType*  
 [Input] L'identificatore del tipo di dati C di \* *TargetValuePtr* buffer. Durante il recupero dei dati dall'origine dati con **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, o **SQLSetPos**, driver converte i dati per questo tipo. Quando vengono inviati dati all'origine dati con **SQLBulkOperations** o **SQLSetPos**, il driver converte i dati da questo tipo. Per un elenco di tipi di dati C validi e di identificatori di tipo, vedere il [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) sezione Appendice d: tipo di dati.  
  
 Se il *TargetType* argomento è un tipo di dati di intervallo, la precisione iniziale intervallo predefinita (2) e la precisione dei secondi di intervallo predefinito (6), di cui i campi SQL_DESC_DATETIME_INTERVAL_PRECISION e SQL_DESC_PRECISION di ARD, vengono utilizzati rispettivamente per i dati. Se il *TargetType* argomento SQL_C_NUMERIC, la precisione predefinita (definito dal driver) e predefinito (0), scala come set di campi di SQL_DESC_PRECISION e SQL_DESC_SCALE il ARD, vengono utilizzato per i dati. Se qualsiasi precisione predefinita o la scala non è appropriata, l'applicazione deve impostare in modo esplicito il campo di descrizione appropriato da una chiamata a **SQLSetDescField** o **SQLSetDescRec**.  
  
 È inoltre possibile specificare un tipo di dati C esteso. Per ulteriori informazioni, vedere [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Input/Output posticipata] Puntatore al buffer di dati da associare alla colonna. **SQLFetch** e **SQLFetchScroll** restituire i dati in questo buffer. **SQLBulkOperations** restituisce i dati in questo buffer quando *operazione* è SQL_FETCH_BY_BOOKMARK; recupera dati da questo buffer quando *operazione* è SQL_ADD o SQL_UPDATE_BY_BOOKMARK . **SQLSetPos** restituisce i dati in questo buffer quando *operazione* è SQL_REFRESH; recupera dati da questo buffer quando *operazione* è SQL_UPDATE.  
  
 Se *TargetValuePtr* è un puntatore null, il driver viene disassociato il buffer dei dati per la colonna. Un'applicazione può annullare l'associazione di tutte le colonne chiamando **SQLFreeStmt** con l'opzione SQL_UNBIND. Un'applicazione è possibile separare il buffer dei dati per una colonna ma ancora un buffer di lunghezza/indicatore associato per la colonna, se il *TargetValuePtr* argomento nella chiamata a **SQLBindCol** è un puntatore null, ma il *StrLen_or_IndPtr* argomento è un valore valido.  
  
 *BufferLength*  
 [Input] Lunghezza di **TargetValuePtr* buffer in byte.  
  
 Il driver utilizza *BufferLength* per evitare di scrivere oltre la fine del \* *TargetValuePtr* nel buffer quando vengono restituiti i dati a lunghezza variabile, ad esempio carattere o dati binari. Si noti che il driver viene considerato il carattere di terminazione null al momento della restituzione dei dati di tipo carattere a \* *TargetValuePtr*. **TargetValuePtr* deve pertanto contenere spazio per il carattere di terminazione null o il driver verrà troncare i dati.  
  
 Quando il driver restituisce dati a lunghezza fissa, ad esempio un numero intero o una struttura di data, il driver ignora *BufferLength* e presuppone che il buffer sia sufficientemente grande da contenere i dati. Pertanto, è importante per l'applicazione allocare un buffer sufficiente per i dati a lunghezza fissa o il driver scriverà oltre la fine del buffer.  
  
 **SQLBindCol** restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer) quando *BufferLength* è minore di 0 ma non quando *BufferLength* è 0. Tuttavia, se *TargetType* specifica un tipo di carattere, un'applicazione non è consigliabile impostare *BufferLength* su 0, perché il driver conforme a ISO CLI restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer) in case.  
  
 *StrLen_or_IndPtr*  
 [Input/Output posticipata] Puntatore al buffer di lunghezza/indicatore da associare alla colonna. **SQLFetch** e **SQLFetchScroll** restituiscono un valore di questo buffer. **SQLBulkOperations** recupera un valore da questo buffer quando *operazione* è SQL_ADD, SQL_UPDATE_BY_BOOKMARK o SQL_DELETE_BY_BOOKMARK. **SQLBulkOperations** restituisce un valore in questo buffer quando *operazione* è SQL_FETCH_BY_BOOKMARK. **SQLSetPos** restituisce un valore in questo buffer quando *operazione* SQL_REFRESH; è un valore viene recuperato da questo buffer quando *operazione* è SQL_UPDATE.  
  
 **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, e **SQLSetPos** può restituire i valori seguenti nel buffer di lunghezza/indicatore:  
  
-   La lunghezza dei dati da restituire  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 L'applicazione è possibile inserire i valori seguenti nel buffer di lunghezza/indicatore per l'utilizzo con **SQLBulkOperations** o **SQLSetPos**:  
  
-   La lunghezza dei dati inviati  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   Il risultato della macro SQL_LEN_DATA_AT_EXEC  
  
-   SQL_COLUMN_IGNORE  
  
 Se il buffer di indicatore e il buffer di lunghezza buffer separato, il buffer di indicatore può restituire solo SQL_NULL_DATA, mentre il buffer di lunghezza può restituire tutti gli altri valori.  
  
 Per ulteriori informazioni, vedere [funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md), [funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), e [tramite valori di lunghezza/indicatore](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Se *StrLen_or_IndPtr* viene utilizzato un valore di puntatore, alcuna lunghezza o indicatore null. Si tratta di un errore durante il recupero di dati e i dati è NULL.  
  
 Vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione verrà eseguita in un sistema operativo a 64 bit.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLBindCol** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLBindCol** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|(DM) il *ColumnNumber* argomento è 0 e *TargetType* argomento non è stata SQL_C_BOOKMARK o SQL_C_VARBOOKMARK.|  
|07009|Indice del descrittore non valido|Il valore specificato per l'argomento *ColumnNumber* superato il numero massimo di colonne nel set di risultati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY003|Tipo di buffer dell'applicazione non valido|L'argomento *TargetType* è un tipo di dati valido né SQL_C_DEFAULT.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando **SQLBindCol** è stato chiamato.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *BufferLength* era minore di 0.<br /><br /> (DM) il driver non è un'API ODBC 2. *x* driver, il *ColumnNumber* argomento è stato impostato su 0 e il valore specificato per l'argomento *BufferLength* non è uguale a 4.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta la conversione specificata dalla combinazione del *TargetType* argomento e il tipo di dati specifici del driver SQL della colonna corrispondente.<br /><br /> L'argomento *ColumnNumber* era 0 e il driver non supporta i segnalibri.<br /><br /> Il driver supporta solo l'API ODBC 2. *x* e l'argomento *TargetType* è uno dei seguenti:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> uno dei tipi di dati di intervallo C sono elencati nella [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) appendice d: tipo di dati.<br /><br /> Il driver supporta solo versioni ODBC prima 3.50 e l'argomento *TargetType* stato SQL_C_GUID.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 **SQLBindCol** viene utilizzato per associare, o *associare,* le colonne nel risultato impostate per i buffer di dati e buffer di lunghezza/indicatore nell'applicazione. Quando l'applicazione chiama **SQLFetch**, **SQLFetchScroll**, o **SQLSetPos** per recuperare dati, il driver restituisce i dati per le colonne associate nel buffer specificato; per altre informazioni, vedere [SQLFetch-funzione](../../../odbc/reference/syntax/sqlfetch-function.md). Quando l'applicazione chiama **SQLBulkOperations** per aggiornare o inserire una riga o **SQLSetPos** per aggiornare una riga, il driver recupera i dati per le colonne associate dai buffer di specificata; per ulteriori informazioni , vedere [funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) o [funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md). Per ulteriori informazioni sull'associazione, vedere [il recupero dei risultati (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 Si noti che le colonne non debbano essere associato a recuperare i dati da essi. Un'applicazione può anche chiamare **SQLGetData** per recuperare dati dalle colonne. Sebbene sia possibile associare alcune colonne in una riga e una chiamata **SQLGetData** per altri utenti, si tratta soggetti ad alcune restrizioni. Per ulteriori informazioni, vedere [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>Associazione, separazione e riassociazione di colonne  
 Una colonna può essere associata, non associata o riassociata in qualunque momento, anche dopo la data è stata recuperata dal set di risultati. La nuova associazione diventa effettiva la volta successiva che viene chiamata una funzione che utilizza le associazioni. Ad esempio, si supponga che un'applicazione associa le colonne in un set di risultati e chiama **SQLFetch**. Il driver restituisce i dati nel buffer associati. Si supponga ora che l'oggetto applicazione associa le colonne da un diverso set di buffer. Il driver non inserire i dati per la riga recuperata solo nei buffer appena associato. In alternativa, è in attesa finché **SQLFetch** viene chiamato nuovamente e quindi inserisce i dati per la riga successiva nel buffer appena associato.  
  
> [!NOTE]  
>  L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS deve sempre essere impostato prima di associare a una colonna 0. Non è obbligatorio ma è fortemente consigliato.  
  
## <a name="binding-columns"></a>Associazione delle colonne  
 Per associare una colonna, un'applicazione chiama **SQLBindCol** e passa il numero di colonna, tipo, indirizzo e lunghezza di un buffer di dati e l'indirizzo di un buffer di lunghezza/indicatore. Per informazioni sull'utilizzo di questi indirizzi, vedere "Buffer indirizzi" più avanti in questa sezione. Per ulteriori informazioni sulle colonne di associazione, vedere [SQLBindCol utilizzando](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 L'uso di questi buffer è posticipata; ovvero, l'applicazione associa in **SQLBindCol** ma il driver si accede da altre funzioni, vale a dire **SQLBulkOperations**, **SQLFetch**,  **SQLFetchScroll**, o **SQLSetPos**. È responsabilità dell'applicazione per assicurarsi che i puntatori specificato **SQLBindCol** rimangono valide fino a quando l'associazione rimane attiva. Se l'applicazione consente questi puntatori non sia più valido, ad esempio, libera un buffer, e quindi chiama una funzione che prevede che siano validi, le conseguenze sono indefinite. Per ulteriori informazioni, vedere [buffer posticipata](../../../odbc/reference/develop-app/deferred-buffers.md).  
  
 L'associazione rimane effettiva fino a quando viene sostituito con una nuova associazione, la colonna non è associata o l'istruzione viene liberata.  
  
## <a name="unbinding-columns"></a>Separazione di colonne  
 Per disassociare una singola colonna, un'applicazione chiama **SQLBindCol** con *ColumnNumber* impostato sul numero di colonna e *TargetValuePtr* impostato su un puntatore null. Se *ColumnNumber* fa riferimento a una colonna non associata, **SQLBindCol** ancora restituisce SQL_SUCCESS.  
  
 Per disassociare tutte le colonne, un'applicazione chiama **SQLFreeStmt** con *fOption* impostato su SQL_UNBIND. Può essere eseguita anche impostando il campo SQL_DESC_COUNT di ARD a zero.  
  
## <a name="rebinding-columns"></a>Riassociazione delle colonne  
 Un'applicazione può eseguire una delle due operazioni per modificare un'associazione:  
  
-   Chiamare **SQLBindCol** per specificare una nuova associazione per una colonna che è già associata. Il driver sovrascrive l'associazione precedente con quello nuovo.  
  
-   Specificare un offset da aggiungere all'indirizzo del buffer che è stato specificato tramite la chiamata di associazione di **SQLBindCol**. Per ulteriori informazioni, vedere la sezione successiva, "Associazione offset".  
  
## <a name="binding-offsets"></a>Offset di associazione  
 Un offset di associazione è un valore che viene aggiunto agli indirizzi dei buffer di dati e lunghezza/indicatore (come specificato nella *TargetValuePtr* e *StrLen_or_IndPtr* argomento) prima che essi vengono dereferenziati. Quando vengono utilizzati gli offset, le associazioni sono "modello" di disposizione buffer dell'applicazione e l'applicazione può passare "modello" a diverse aree di memoria modificando l'offset. Poiché lo stesso offset viene aggiunto a ogni indirizzo in ogni associazione, gli offset relativi tra i buffer per colonne diverse devono corrispondere all'interno di ogni set di buffer. Questo è sempre vero quando viene utilizzata l'associazione per riga l'applicazione deve attentamente il layout dei buffer per il valore è true quando viene utilizzata l'associazione per colonna.  
  
 Usando un offset di associazione è fondamentalmente lo stesso effetto la riassociazione della colonna chiamando **SQLBindCol**. La differenza è che una nuova chiamata a **SQLBindCol** specifica nuovi indirizzi per il buffer dei dati e buffer di lunghezza/indicatore, mentre l'utilizzo di un offset di associazione non modifica gli indirizzi ma aggiunge solo un offset a essi. L'applicazione può specificare un offset di nuovo ogni volta che desidera, e questo offset viene sempre aggiunta agli indirizzi di origine associati. In particolare, se l'offset è impostato su 0 o se l'attributo di istruzione è impostata su un puntatore null, il driver utilizza gli indirizzi di origine associati.  
  
 Per specificare un offset di associazione, l'applicazione imposta l'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR all'indirizzo di un buffer SQLINTEGER. Prima che l'applicazione chiama una funzione che utilizza le associazioni, inserisce un offset in byte di questo buffer. Per determinare l'indirizzo del buffer da utilizzare, il driver aggiunge l'offset per l'indirizzo nell'associazione. La somma dell'indirizzo e l'offset deve essere un indirizzo valido, ma l'indirizzo a cui viene aggiunta l'offset non deve essere valido. Per ulteriori informazioni sull'utilizzo di offset di associazione, vedere "Buffer indirizzi" più avanti in questa sezione.  
  
## <a name="binding-arrays"></a>Associazione di matrici  
 Se le dimensioni del set di righe (il valore dell'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE) sono maggiore di 1, l'applicazione associa le matrici di buffer anziché singolo buffer. Per ulteriori informazioni, vedere [cursori a blocchi](../../../odbc/reference/develop-app/block-cursors.md).  
  
 L'applicazione può associare le matrici in due modi:  
  
-   Associare una matrice per ogni colonna. Ciò è detto *associazione per colonna* perché ogni struttura di dati (matrice) contiene dati per una singola colonna.  
  
-   Definire una struttura per contenere i dati per una riga intera e associare una matrice di strutture. Ciò è detto *l'associazione per riga* perché ogni struttura di dati contiene i dati per una singola riga.  
  
 Ogni matrice di buffer deve avere almeno il numero di elementi come le dimensioni del set di righe.  
  
> [!NOTE]  
>  Un'applicazione deve verificare che l'allineamento è valido. Per ulteriori informazioni sulle considerazioni relative all'allineamento, vedere [allineamento](../../../odbc/reference/develop-app/alignment.md).  
  
## <a name="column-wise-binding"></a>L'associazione per colonna  
 Nell'associazione per colonna, l'applicazione associa dati separata e matrici di lunghezza/indicatore a ogni colonna.  
  
 Per utilizzare l'associazione per colonna, l'applicazione imposta innanzitutto l'attributo di istruzione SQL_ATTR_ROW_BIND_TYPE su SQL_BIND_BY_COLUMN. (Questo è il valore predefinito). Per ogni colonna da associare, l'applicazione esegue i passaggi seguenti:  
  
1.  Alloca una matrice di buffer di dati.  
  
2.  Alloca una matrice di buffer di lunghezza/indicatore.  
  
    > [!NOTE]  
    >  Se l'applicazione scrive direttamente descrittori quando viene utilizzata l'associazione per colonna, è possono utilizzare matrici separate per i dati di lunghezza e indicatore.  
  
3.  Chiamate **SQLBindCol** con gli argomenti seguenti:  
  
    -   *TargetType* è il tipo di un singolo elemento nella matrice di buffer di dati.  
  
    -   *TargetValuePtr* è l'indirizzo della matrice di buffer di dati.  
  
    -   *BufferLength* è la dimensione di un singolo elemento nella matrice di buffer di dati. Il *BufferLength* argomento viene ignorato quando i dati sono dati a lunghezza fissa.  
  
    -   *StrLen_or_IndPtr* è l'indirizzo della matrice di lunghezza/indicatore.  
  
 Per ulteriori informazioni sull'uso di queste informazioni, vedere "Buffer indirizzi" più avanti in questa sezione. Per ulteriori informazioni sull'associazione per colonna, vedere [l'associazione](../../../odbc/reference/develop-app/column-wise-binding.md).  
  
## <a name="row-wise-binding"></a>L'associazione per riga  
 Nell'associazione per riga, l'applicazione definisce una struttura che contiene i dati e lunghezza/indicatore buffer per ogni colonna deve essere associata.  
  
 Per utilizzare l'associazione per riga, l'applicazione esegue i passaggi seguenti:  
  
1.  Definisce una struttura per contenere una singola riga di dati (inclusi i buffer di dati e lunghezza/indicatore) e alloca una matrice di strutture.  
  
    > [!NOTE]  
    >  Se l'applicazione scrive direttamente descrittori quando viene utilizzata l'associazione per riga, è possono utilizzare campi separati per i dati di lunghezza e indicatore.  
  
2.  Imposta l'attributo di istruzione SQL_ATTR_ROW_BIND_TYPE sulla dimensione della struttura che contiene una singola riga di dati o le dimensioni di un'istanza di un buffer in cui le colonne di risultati verranno associate. La lunghezza deve includere lo spazio per tutte le colonne associate ed eventuale riempimento della struttura o del buffer, per assicurarsi che quando l'indirizzo di una colonna associata viene incrementato con la lunghezza specificata, il risultato punterà all'inizio della stessa colonna nella riga successiva. Quando si utilizza il *sizeof* operatore in ANSI C, questo comportamento è garantito.  
  
3.  Chiamate **SQLBindCol** con gli argomenti seguenti per ogni colonna deve essere associata:  
  
    -   *TargetType* è il tipo del membro di buffer di dati da associare alla colonna.  
  
    -   *TargetValuePtr* è l'indirizzo del membro di buffer dei dati nel primo elemento della matrice.  
  
    -   *BufferLength* è la dimensione del membro di buffer di dati.  
  
    -   *StrLen_or_IndPtr* è l'indirizzo del membro di lunghezza/indicatore da associare.  
  
 Per ulteriori informazioni sull'uso di queste informazioni, vedere "Buffer indirizzi" più avanti in questa sezione. Per ulteriori informazioni sull'associazione per colonna, vedere [associazione per riga](../../../odbc/reference/develop-app/row-wise-binding.md).  
  
## <a name="buffer-addresses"></a>Indirizzi di buffer  
 Il *buffer indirizzo* è l'indirizzo effettivo del buffer di dati o di lunghezza/indicatore. Il driver calcola l'indirizzo del buffer solo prima di scrivere nei buffer (ad esempio durante la fase di recupero). Viene calcolato dalla formula seguente, che usa gli indirizzi specificati nella *TargetValuePtr* e *StrLen_or_IndPtr* argomenti, l'offset di associazione e il numero di riga:  
  
 *Associare l'indirizzo* + *associazione Offset* + ((*il numero di riga* – 1) x *dimensione dell'elemento*)  
  
 le variabili della formula in cui sono definite come descritto nella tabella seguente.  
  
|Variabile|Description|  
|--------------|-----------------|  
|*Associare l'indirizzo*|Per i buffer di dati, l'indirizzo specificato con il *TargetValuePtr* argomento **SQLBindCol**.<br /><br /> Per i buffer di lunghezza/indicatore, l'indirizzo specificato con il *StrLen_or_IndPtr* argomento **SQLBindCol**. Per ulteriori informazioni, vedere "Commenti aggiuntivi" nella sezione "Descrittori e SQLBindCol".<br /><br /> Se l'indirizzo di binding è 0, viene restituito alcun valore di dati, anche se l'indirizzo calcolato mediante la formula precedente è diverso da zero.|  
|*Offset di associazione*|Se si utilizza l'associazione per riga, il valore archiviato in corrispondenza dell'indirizzo specificato con l'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR.<br /><br /> Se viene utilizzata l'associazione per colonna o se il valore dell'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR è un puntatore null, *associazione Offset* è 0.|  
|*Numero di riga*|Il numero della riga nel set di righe in base 1. Per operazioni di recupero a riga singola, ovvero l'impostazione predefinita, questo è 1.|  
|*Dimensione dell'elemento*|Le dimensioni di un elemento nella matrice associato.<br /><br /> Se viene utilizzata l'associazione per colonna, si tratta **sizeof(SQLINTEGER)** per i buffer di lunghezza/indicatore. Per i buffer di dati, è il valore di *BufferLength* argomento in **SQLBindCol** se il tipo di dati è di lunghezza variabile e la dimensione del tipo di dati se il tipo di dati è a lunghezza fissa.<br /><br /> Se viene utilizzata l'associazione per riga, questo è il valore dell'attributo di istruzione SQL_ATTR_ROW_BIND_TYPE per i buffer di dati e lunghezza/indicatore.|  
  
## <a name="descriptors-and-sqlbindcol"></a>Descrittori e SQLBindCol  
 Le sezioni seguenti descrivono come **SQLBindCol** interagisce con descrittori.  
  
> [!CAUTION]  
>  La chiamata **SQLBindCol** per un'istruzione può influire sulle altre istruzioni. Questo errore si verifica quando il ARD associate all'istruzione viene allocato in modo esplicito ed è inoltre associata con altre istruzioni. Poiché **SQLBindCol** modifica il descrittore, le modifiche si applicano a tutte le istruzioni a cui è associato questo descrittore. In caso contrario il comportamento richiesto, l'applicazione deve annullare l'associazione di questo descrittore da altre istruzioni prima di chiamare **SQLBindCol**.  
  
## <a name="argument-mappings"></a>Mapping di argomento  
 Concettualmente, **SQLBindCol** esegue i passaggi seguenti in sequenza:  
  
1.  Chiamate **SQLGetStmtAttr** per ottenere l'handle ARD.  
  
2.  Chiamate **SQLGetDescField** per ottenere campo SQL_DESC_COUNT del descrittore e, se il valore di *ColumnNumber* argomento supera il valore di SQL_DESC_COUNT, chiamate **SQLSetDescField**  per aumentare il valore di SQL_DESC_COUNT a *ColumnNumber*.  
  
3.  Chiamate **SQLSetDescField** più volte per assegnare valori ai campi del ARD seguenti:  
  
    -   Imposta il valore di SQL_DESC_TYPE e SQL_DESC_CONCISE_TYPE *TargetType*, ad eccezione del fatto che se *TargetType* è uno degli identificatori di un sottotipo di datetime o intervallo concisi, imposta SQL_DESC_TYPE su SQL _ Valore DATETIME o SQL_INTERVAL, rispettivamente. Imposta l'identificatore conciso; SQL_DESC_CONCISE_TYPE e i set SQL_DESC_DATETIME_INTERVAL_CODE per il valore datetime corrispondente o di un codice secondario dell'intervallo.  
  
    -   Imposta una o più delle SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE e SQL_DESC_DATETIME_INTERVAL_PRECISION, come appropriato per *TargetType*.  
  
    -   Imposta sul valore del campo SQL_DESC_OCTET_LENGTH *BufferLength*.  
  
    -   Imposta il campo SQL_DESC_DATA_PTR al valore di *valore di destinazione*.  
  
    -   Imposta sul valore del campo SQL_DESC_INDICATOR_PTR *StrLen_or_Ind*. (Vedere il paragrafo seguente).  
  
    -   Imposta sul valore del campo SQL_DESC_OCTET_LENGTH_PTR *StrLen_or_Ind*. (Vedere il paragrafo seguente).  
  
 La variabile che il *StrLen_or_Ind* argomento intende viene utilizzata per informazioni sulla lunghezza sia l'indicatore. Se un'operazione di recupero rileva un valore null per la colonna, SQL_NULL_DATA archivia nella variabile; Archivia in caso contrario, la lunghezza dei dati nella variabile. Passando un puntatore null come *StrLen_or_Ind* mantiene l'operazione di recupero di restituire la lunghezza dei dati, ma rende l'operazione di recupero non riesce se rileva un valore null e non è possibile restituire SQL_NULL_DATA.  
  
 Se la chiamata a **SQLBindCol** ha esito negativo, il contenuto dei campi di descrizione che sarebbero impostate nel ARD sono definiti e il valore del campo SQL_DESC_COUNT il ARD rimane invariato.  
  
## <a name="implicit-resetting-of-count-field"></a>Reimpostazione implicita del campo del conteggio  
 **SQLBindCol** imposta il valore di SQL_DESC_COUNT il *ColumnNumber* argomento solo quando si potrebbe aumentare il valore di SQL_DESC_COUNT. Se il valore di *TargetValuePtr* argomento è un puntatore null e il valore della *ColumnNumber* argomento è uguale a SQL_DESC_COUNT (vale a dire quando disassociare il più elevato colonna associata), quindi SQL_DESC_ CONTEGGIO è impostato per il numero della colonna associata rimanente più alto.  
  
## <a name="cautions-regarding-sqldefault"></a>Precauzioni relative SQL_DEFAULT  
 Per recuperare correttamente i dati della colonna, l'applicazione deve determinare correttamente la lunghezza e il punto iniziale dei dati nel buffer dell'applicazione. Quando l'applicazione specifica esplicita *TargetType*, rilevare facilmente convinzioni erronee dell'applicazione. Tuttavia, quando l'applicazione specifica un *TargetType* di SQL_DEFAULT, **SQLBindCol** applicabile a una colonna di un tipo di dati diverse da quella desiderata dall'applicazione, da modifiche per il i metadati o applicando il codice in un'altra colonna. In questo caso, l'applicazione potrebbe non determinano l'inizio o la lunghezza dei dati della colonna di recupero. Questo può causare errori di dati non segnalati o violazioni di memoria.  
  
## <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione esegue un **selezionare** istruzione sulla tabella Customers per restituire un set di risultati del cliente, ID, nomi e numeri di telefono, ordinati per nome. Chiama quindi **SQLBindCol** per associare le colonne di dati ai buffer locale. Infine, l'applicazione recupera ciascuna riga di dati con **SQLFetch** e stampa nome, ID e il numero di telefono di ogni cliente.  
  
 Per ulteriori esempi di codice, vedere [funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [funzione SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), [funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md), e [funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 20  
  
void show_error() {  
   printf("error\n");  
}  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];  
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {   
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
                  // Bind columns 1, 2, and 3  
                  retcode = SQLBindCol(hstmt, 1, SQL_C_CHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (i ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                        wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                     else  
                        break;  
                  }  
               }  
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLCancel(hstmt);  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 Vedere anche [programma di esempio ODBC](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituzione di informazioni su una colonna in un set di risultati|[Funzione SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Recupero di un blocco di dati o di scorrimento di un risultato impostato|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Recupero di più righe di dati|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Il buffer delle colonne nell'istruzione di rilascio|[Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Il recupero o parte di una colonna di dati|[Funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Restituzione del numero di risultati le colonne del set|[Funzione SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

