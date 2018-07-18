---
title: Funzione SQLBindParameter | Documenti Microsoft
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
- SQLBindParameter
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBindParameter
helpviewer_keywords:
- SQLBindParameter function [ODBC]
ms.assetid: 38349d4b-be03-46f9-9d6a-e50dd144e225
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e1cdde978780cce1807885334d42d0d89d44130
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlbindparameter-function"></a>Pagina relativa alla funzione SQLBindParameter
**Conformità**  
 Introdotta: versione ODBC 2.0 aderenza: ODBC  
  
 **Riepilogo**  
 **SQLBindParameter** associa un buffer per un marcatore di parametro in un'istruzione SQL. **SQLBindParameter** supporta l'associazione a un tipo di dati Unicode C, anche se il driver sottostante non supporta i dati Unicode.  
  
> [!NOTE]  
>  Questa funzione sostituisce la funzione ODBC 1.0 **SQLSetParam**. Per ulteriori informazioni, vedere "Commenti".  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLBindParameter(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT     InputOutputType,  
      SQLSMALLINT     ValueType,  
      SQLSMALLINT     ParameterType,  
      SQLULEN         ColumnSize,  
      SQLSMALLINT     DecimalDigits,  
      SQLPOINTER      ParameterValuePtr,  
      SQLLEN          BufferLength,  
      SQLLEN *        StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *ParameterNumber*  
 [Input] Numero di parametro, ordinati in sequenza in ordine crescente di parametro, a partire da 1.  
  
 *InputOutputType*  
 [Input] Il tipo del parametro. Per ulteriori informazioni, vedere "*InputOutputType* argomento" in "Commenti".  
  
 *ValueType*  
 [Input] Il tipo di dati C del parametro. Per ulteriori informazioni, vedere "*ValueType* argomento" in "Commenti".  
  
 *ParameterType*  
 [Input] Il tipo di dati SQL del parametro. Per ulteriori informazioni, vedere "*ParameterType* argomento" in "Commenti".  
  
 *ColumnSize*  
 [Input] Le dimensioni della colonna o espressione del marcatore di parametro corrispondente. Per ulteriori informazioni, vedere "*ColumnSize* argomento" in "Commenti".  
  
 Se l'applicazione verrà eseguita in un sistema operativo di Windows a 64 bit, vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
 *DecimalDigits*  
 [Input] Le cifre decimali della colonna o espressione del marcatore di parametro corrispondente. Per ulteriori informazioni sulle dimensioni di colonna, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *ParameterValuePtr*  
 [Input posticipata] Un puntatore a un buffer per i dati del parametro. Per ulteriori informazioni, vedere "*ParameterValuePtr* argomento" in "Commenti".  
  
 *BufferLength*  
 [Input/Output] Lunghezza di *ParameterValuePtr* buffer in byte. Per ulteriori informazioni, vedere "*BufferLength* argomento" in "Commenti".  
  
 Vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione verrà eseguita in un sistema operativo a 64 bit.  
  
 *StrLen_or_IndPtr*  
 [Input posticipata] Un puntatore a un buffer per la lunghezza del parametro. Per ulteriori informazioni, vedere "*StrLen_or_IndPtr* argomento" in "Commenti".  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLBindParameter** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLBindParameter** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Il tipo di dati identificato dal *ValueType* argomento non può essere convertito nel tipo di dati identificato dal *ParameterType* argomento. Si noti che questo errore potrebbe essere restituito da **SQLExecDirect**, **SQLExecute**, o **SQLPutData** in fase di esecuzione, anziché da **SQLBindParameter**.|  
|07009|Indice del descrittore non valido|(DM) il valore specificato per l'argomento *ParameterNumber* è minore di 1.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel **MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY003|Tipo di buffer dell'applicazione non valido|Il valore specificato dall'argomento *ValueType* non è un tipo di dati C valido o SQL_C_DEFAULT.|  
|HY004|Tipo di dati SQL non valido|Il valore specificato per l'argomento *ParameterType* è un identificatore di tipo di dati SQL ODBC valido né un identificatore di tipo dati SQL specifiche del driver supportata dal driver.|  
|HY009|Valore dell'argomento non valido|(DM) l'argomento *ParameterValuePtr* era un puntatore null, l'argomento *StrLen_or_IndPtr* era un puntatore null e l'argomento *InputOutputType* SQL_PARAM_ non è stato OUTPUT.<br /><br /> SQL_PARAM_OUTPUT (DM), in cui l'argomento *ParameterValuePtr* era un puntatore null, il tipo di C è char o binary e il BufferLength (*cbValueMax*) è maggiore di 0.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando **SQLBindParameter** è stato chiamato.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione il *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY021|Informazioni del descrittore incoerenti.|Le informazioni sul descrittore controllati durante una verifica coerenza non era coerente. (Vedere la sezione "Verifiche coerenza" in **SQLSetDescField**.)<br /><br /> Il valore specificato per l'argomento *DecimalDigits* non compreso nell'intervallo dei valori supportati dall'origine dati per una colonna di tipo di dati SQL specificato per il *ParameterType* argomento.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore in *BufferLength* era minore di 0. (Vedere la descrizione del campo SQL_DESC_DATA_PTR **SQLSetDescField**.)|  
|HY104|Valore di precisione o scala non valido|Il valore specificato per l'argomento *ColumnSize* o *DecimalDigits* non compreso nell'intervallo dei valori supportati dall'origine dati per una colonna di tipo di dati SQL specificato per il  *ParameterType* argomento.|  
|HY105|Tipo di parametro non valido|(DM) il valore specificato per l'argomento *InputOutputType* non è valido. (Vedere "Commenti".)|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|L'origine dati o driver non supporta la conversione specificata tramite la combinazione del valore specificato per l'argomento *ValueType* e il valore specifico del driver specificato per l'argomento *ParameterType*.<br /><br /> Il valore specificato per l'argomento *ParameterType* è un identificatore di tipo di dati SQL ODBC valido per la versione di ODBC supportati dal driver, ma non è supportata dall'origine dati o driver.<br /><br /> Il driver supporta solo l'API ODBC 2. *x* e l'argomento *ValueType* è uno dei seguenti:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> tutti i tipi di dati di intervallo C sono elencati nella [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) appendice d: tipo di dati.<br /><br /> Il driver supporta solo versioni ODBC prima 3.50 e l'argomento *ValueType* stato SQL_C_GUID.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Un'applicazione chiama **SQLBindParameter** associare ogni marcatore di parametro in un'istruzione SQL. Associazioni rimangono valide fino a quando l'applicazione chiama **SQLBindParameter** nuovamente, chiama **SQLFreeStmt** con l'opzione SQL_RESET_PARAMS oppure chiamate **SQLSetDescField** per impostare il campo di intestazione SQL_DESC_COUNT di APD su 0.  
  
 Per ulteriori informazioni sui parametri, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md). Per ulteriori informazioni sui tipi di dati di parametro e gli indicatori di parametro, vedere [tipi di dati di parametro](../../../odbc/reference/appendixes/parameter-data-types.md) e [marcatori di parametro](../../../odbc/reference/appendixes/parameter-markers.md) nella grammatica SQL di appendice c:.  
  
## <a name="parameternumber-argument"></a>Argomento ParameterNumber  
 Se *ParameterNumber* nella chiamata a **SQLBindParameter** è maggiore del valore di SQL_DESC_COUNT, **SQLSetDescField** viene chiamato per aumentare il valore di SQL_DESC_ CONTEGGIO su *ParameterNumber*.  
  
## <a name="inputoutputtype-argument"></a>Argomento InputOutputType  
 Il *InputOutputType* argomento specifica il tipo del parametro. Questo argomento imposta il campo SQL_DESC_PARAMETER_TYPE del IPD. Tutti i parametri nelle istruzioni SQL che non chiamano le procedure, ad esempio **inserire** , le istruzioni sono *input * * parametri*. I parametri nelle chiamate di procedura possono essere di input, input/output o i parametri di output. (Un'applicazione chiama **SQLProcedureColumns** per determinare il tipo di un parametro in una chiamata di procedura si presuppone che non è possibile determinare il cui tipo di parametri sono parametri di input.)  
  
 Il *InputOutputType* argomento è uno dei valori seguenti:  
  
-   SQL_PARAM_INPUT. Il parametro contrassegna un parametro in un'istruzione SQL che non chiama una routine, ad esempio un **inserire** istruzione oppure contrassegna un parametro di input in una stored procedure. Ad esempio, i parametri in **inserire i valori in dipendente (?,?,?)**  sono parametri di input, mentre i parametri in **{chiamare AddEmp (?,?,?)}**  possono essere, ma non necessariamente, parametri di input.  
  
     Quando viene eseguita l'istruzione, il driver invia dati per il parametro dell'origine dati. il \* *ParameterValuePtr* buffer deve contenere un valore di input valido, o **StrLen_or_IndPtr* buffer deve contenere il risultato di SQL_LEN_DATA_AT SQL_NULL_DATA o SQL_DATA_AT_EXEC Macro Exec.  
  
     Se un'applicazione non è possibile determinare il tipo di un parametro in una chiamata di routine, imposta *InputOutputType* a SQL_PARAM_INPUT; se l'origine dati restituisce un valore per il parametro, il driver Ignora.  
  
-   SQL_PARAM_INPUT_OUTPUT. Il parametro contrassegna un parametro di input/output in una stored procedure. Ad esempio, il parametro in **{chiamare GetEmpDept(?)}**  è un parametro di input/output che accetta un nome di dipendente e restituisce il nome del reparto del dipendente.  
  
     Quando viene eseguita l'istruzione, il driver invia dati per il parametro dell'origine dati. il \* *ParameterValuePtr* buffer deve contenere un valore di input valido, o \* *StrLen_or_IndPtr* buffer deve contenere il risultato di SQL_NULL_DATA o SQL_DATA_AT_EXEC la macro SQL_LEN_DATA_AT_EXEC. Dopo l'istruzione viene eseguita, il driver restituisce i dati per il parametro all'applicazione. Se l'origine dati non restituisce un valore per un parametro di input/output, il driver imposta il **StrLen_or_IndPtr* buffer su SQL_NULL_DATA.  
  
    > [!NOTE]  
    >  Quando un'applicazione ODBC 1.0 chiama **SQLSetParam** in un driver ODBC 2.0, gestione Driver Converte l'oggetto in una chiamata a **SQLBindParameter** in cui il *InputOutputType* argomento è impostato su SQL_PARAM_INPUT_OUTPUT.  
  
-   SQL_PARAM_OUTPUT. Il parametro contrassegna il valore restituito di una routine o un parametro di output in una routine. in entrambi i casi, questi sono conosciuti come *i parametri di output*. Ad esempio, il parametro in **{? = chiamare GetNextEmpID}** è un parametro di output che restituisce l'ID del dipendente successivo.  
  
     Dopo l'istruzione viene eseguita, il driver restituisce dati per il parametro all'applicazione, a meno che il *ParameterValuePtr* e *StrLen_or_IndPtr* gli argomenti sono entrambi puntatori null, nel qual caso il driver ignora il valore di output. Se l'origine dati non restituisce un valore per un parametro di output, il driver imposta il **StrLen_or_IndPtr* buffer su SQL_NULL_DATA.  
  
-   SQL_PARAM_INPUT_OUTPUT_STREAM. Indica che deve essere trasmesso un parametro di input/output. **SQLGetData** possono leggere i valori di parametro in parti. *BufferLength* è stato ignorato perché la lunghezza del buffer verrà determinata in corrispondenza della chiamata di **SQLGetData**. Il valore di *StrLen_or_IndPtr* buffer deve contenere il risultato della macro SQL_LEN_DATA_AT_EXEC, SQL_DEFAULT_PARAM, SQL_DATA_AT_EXEC o SQL_NULL_DATA. Un parametro deve essere associato come un parametro data-at-execution (DAE) nell'input se che verrà trasmesso dall'output. *ParameterValuePtr* può essere qualsiasi valore di puntatore non null che restituirà **SQLParamData** come definito dall'utente del token il cui valore è stato superato con *ParameterValuePtr* per input sia e output. Per ulteriori informazioni, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_PARAM_OUTPUT_STREAM. Uguale a SQL_PARAM_INPUT_OUTPUT_STREAM, per un parametro di output. **StrLen_or_IndPtr* viene ignorato a livello di input.  
  
 Nella tabella seguente sono elencate diverse combinazioni di *InputOutputType* e **StrLen_or_IndPtr*:  
  
|*InputOutputType*|**StrLen_or_IndPtr*|Risultato|Mettere in ParameterValuePtr|  
|-----------------------|----------------------------|-------------|---------------------------------|  
|SQL_PARAM_INPUT|SQL_LEN_DATA_AT_EXEC (*len*) o SQL_DATA_AT_EXEC|Input in parti|*ParameterValuePtr* può essere qualsiasi valore di puntatore che restituirà **SQLParamData** come definito dall'utente del token il cui valore è stato superato con *ParameterValuePtr*.|  
|SQL_PARAM_INPUT|Non SQL_LEN_DATA_AT_EXEC (*len*) o SQL_DATA_AT_EXEC|Associare buffer di input|*ParameterValuePtr* è l'indirizzo del buffer di input.|  
|SQL_PARAM_OUTPUT|Ignorato nell'input.|Buffer di output associato|*ParameterValuePtr* è l'indirizzo del buffer di output.|  
|SQL_PARAM_OUTPUT_STREAM|Ignorato nell'input.|Flusso di output|*ParameterValuePtr* può essere qualsiasi valore di puntatore, verrà restituito dal **SQLParamData** come definito dall'utente del token il cui valore è stato superato con *ParameterValuePtr*.|  
|SQL_PARAM_INPUT_OUTPUT|SQL_LEN_DATA_AT_EXEC (*len*) o SQL_DATA_AT_EXEC|Input in parti e buffer di output associata|*ParameterValuePtr* è l'indirizzo del buffer di output, verrà restituito anche dal **SQLParamData** come definito dall'utente del token il cui valore è stato superato con *ParameterValuePtr*.|  
|SQL_PARAM_INPUT_OUTPUT|Non SQL_LEN_DATA_AT_EXEC (*len*) o SQL_DATA_AT_EXEC|Associare input buffer e buffer di output associata|*ParameterValuePtr* è l'indirizzo del buffer di input/output condiviso.|  
L_PARAM_INPUT_OUTPUT_STREAM|SQL_LEN_DATA_AT_EXEC (*len*) o SQL_DATA_AT_EXEC|Flusso di output e di input in parti|*ParameterValuePtr* può essere qualsiasi valore di puntatore non null, verrà restituito dal **SQLParamData** come definito dall'utente del token il cui valore è stato superato con *ParameterValuePtr* per input sia e di output.|  
  
> [!NOTE]  
>  Il driver è necessario decidere quali tipi SQL sono consentiti quando un'applicazione viene associato un output o un parametro di input-output come flusso. Gestione driver non genererà un errore per un tipo SQL non valido.  
  
## <a name="valuetype-argument"></a>Argomento ValueType  
 Il *ValueType* argomento specifica il tipo di dati C del parametro. Questo argomento consente di impostare i campi SQL_DESC_TYPE SQL_DESC_CONCISE_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE di APD. Deve essere uno dei valori di [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) sezione Appendice d: tipi di dati.  
  
 Se il *ValueType* argomento è uno dei tipi di dati di intervallo, il campo SQL_DESC_TYPE del *ParameterNumber* record di APD è impostata su SQL_INTERVAL, il campo SQL_DESC_CONCISE_TYPE di APD è impostato su il tipo di dati di intervallo conciso e il campo SQL_DESC_DATETIME_INTERVAL_CODE del *ParameterNumber* record è impostato su un codice secondario per il tipo di dati di intervallo specifico. (Vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).) L'intervallo predefinito iniziali precisione (2) e (6), la precisione in secondi intervallo predefinito di cui i campi SQL_DESC_DATETIME_INTERVAL_PRECISION e SQL_DESC_PRECISION dell'APD, rispettivamente, vengono utilizzati per i dati. Se una precisione predefinita non è appropriata, l'applicazione deve impostare in modo esplicito il campo di descrizione da una chiamata a **SQLSetDescField** o **SQLSetDescRec**.  
  
 Se il *ValueType* argomento è uno dei tipi di dati datetime, il campo SQL_DESC_TYPE del *ParameterNumber* record di APD è impostato su SQL_DATETIME, il campo SQL_DESC_CONCISE_TYPE del *ParameterNumber* record di APD è impostato il tipo di dati datetime conciso C e il campo SQL_DESC_DATETIME_INTERVAL_CODE del *ParameterNumber* record è impostato su un codice secondario per l'oggetto datetime specifico tipo di dati. (Vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Se il *ValueType* argomento è un tipo di dati SQL_C_NUMERIC, la precisione predefinita (che è definito dal driver) e la dimensione predefinita (0), come set di campi di SQL_DESC_PRECISION e SQL_DESC_SCALE APD, vengono utilizzati per i dati. Se la precisione predefinita o la scala non è appropriata, l'applicazione deve impostare in modo esplicito il campo di descrizione da una chiamata a **SQLSetDescField** o **SQLSetDescRec**.  
  
 SQL_C_DEFAULT specifica che il valore del parametro da trasferire dal tipo di dati C predefinito per il tipo di dati SQL specificato con *ParameterType*.  
  
 È inoltre possibile specificare un tipo di dati C esteso. Per ulteriori informazioni, vedere [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 Per ulteriori informazioni, vedere [tipi di dati C predefiniti](../../../odbc/reference/appendixes/default-c-data-types.md), [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md), e [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) appendice d: tipo di dati.  
  
## <a name="parametertype-argument"></a>Argomento ParameterType  
 Deve essere uno dei valori elencati nel [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) sezione dell'appendice d: i tipi di dati, oppure deve essere un valore specifico del driver. Questo argomento imposta i campi SQL_DESC_TYPE SQL_DESC_CONCISE_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE del IPD.  
  
 Se il *ParameterType* argomento è uno degli identificatori di datetime, il campo SQL_DESC_TYPE del IPD è impostato su SQL_DATETIME, il campo SQL_DESC_CONCISE_TYPE del IPD è impostato per il tipo di dati datetime conciso SQL e il SQL_DESC_ Campo DATETIME_INTERVAL_CODE è impostata sul valore del codice secondario datetime appropriato.  
  
 Se *ParameterType* è uno degli identificatori di intervallo, il campo SQL_DESC_TYPE del IPD è impostato su SQL_INTERVAL, il campo SQL_DESC_CONCISE_TYPE del IPD è impostato per il tipo di dati di intervallo SQL conciso e il SQL_DESC_DATETIME_ Campo INTERVAL_CODE del IPD è impostato il codice secondario dell'intervallo di tempo appropriato. Il campo SQL_DESC_DATETIME_INTERVAL_PRECISION del IPD è impostato per la precisione iniziale intervallo e il campo SQL_DESC_PRECISION è impostato per la precisione dei secondi di intervallo, se applicabile. Se il valore predefinito di SQL_DESC_DATETIME_INTERVAL_PRECISION o SQL_DESC_PRECISION non è appropriato, impostare nell'applicazione in modo esplicito, chiamando **SQLSetDescField**. Per ulteriori informazioni su uno di questi campi, vedere [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Se il *ValueType* argomento è un tipo di dati SQL_NUMERIC, la precisione predefinita (che è definito dal driver) e la dimensione predefinita (0), come set di campi di SQL_DESC_PRECISION e SQL_DESC_SCALE IPD, vengono utilizzati per i dati. Se la precisione predefinita o la scala non è appropriata, l'applicazione deve impostare in modo esplicito il campo di descrizione da una chiamata a **SQLSetDescField** o **SQLSetDescRec**.  
  
 Per informazioni sulla modalità di conversione di dati, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) e [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) appendice d: tipo di dati.  
  
## <a name="columnsize-argument"></a>Argomento ColumnSize  
 Il *ColumnSize* argomento specifica la dimensione della colonna o espressione che corrisponde al marcatore di parametro, la lunghezza di tali dati, o entrambi. Questo argomento consente di impostare diversi campi del IPD, a seconda del tipo di dati SQL (il *ParameterType* argomento). Le regole seguenti si applicano a questo mapping:  
  
-   Se *ParameterType* è SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY, o un tipo conciso SQL datetime o intervallo di dati, il campo SQL_DESC_LENGTH del IPD è impostato sul valore di  *ColumnSize*. (Per ulteriori informazioni, vedere il [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) sezione Appendice d: tipo di dati.)  
  
-   Se *ParameterType* è SQL_DECIMAL, SQL_NUMERIC, SQL_FLOAT, SQL_REAL o SQL_DOUBLE, il campo SQL_DESC_PRECISION del IPD è impostato sul valore di *ColumnSize*.  
  
-   Per altri tipi di dati, il *ColumnSize* argomento viene ignorato.  
  
 Per ulteriori informazioni, vedere "Passaggio di valori di parametro" e SQL_DATA_AT_EXEC in "*StrLen_or_IndPtr* argomento."  
  
## <a name="decimaldigits-argument"></a>Argomento DecimalDigits  
 Se *ParameterType* è SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, SQL_INTERVAL_SECOND, SQL_INTERVAL_DAY_TO_SECOND, SQL_INTERVAL_HOUR_TO_SECOND o SQL_INTERVAL_MINUTE_TO_SECOND, il campo SQL_DESC_PRECISION del IPD è impostato per *DecimalDigits*. Se *ParameterType* è SQL_NUMERIC o SQL_DECIMAL, il campo SQL_DESC_SCALE del IPD è impostato su *DecimalDigits*. Per tutti gli altri tipi di dati, il *DecimalDigits* argomento viene ignorato.  
  
## <a name="parametervalueptr-argument"></a>Argomento ParameterValuePtr  
 Il *ParameterValuePtr* argomento punta a un buffer che, quando **SQLExecute** o **SQLExecDirect** viene chiamato, contiene i dati effettivi per il parametro. I dati devono essere nel formato specificato per il *ValueType* argomento. Questo argomento consente di impostare il campo SQL_DESC_DATA_PTR di APD. Un'applicazione può impostare il *ParameterValuePtr* argomento a un puntatore null, purché  *\*StrLen_or_IndPtr* è SQL_NULL_DATA o SQL_DATA_AT_EXEC. (Si applica solo a parametri input o di input/output).  
  
 Se \* *StrLen_or_IndPtr* è il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro) o SQL_DATA_AT_EXEC, *ParameterValuePtr* è un valore di puntatore definiti dall'applicazione associata con il parametro. Viene restituito all'applicazione tramite **SQLParamData**. Ad esempio, *ParameterValuePtr* potrebbe essere un token diverso da zero, ad esempio un numero di parametro, un puntatore ai dati o un puntatore a una struttura che l'applicazione utilizzata per associare i parametri di input. Tuttavia, si noti che se il parametro è un parametro di input/output, *ParameterValuePtr* deve essere un puntatore a un buffer in cui verrà archiviato il valore di output. Se il valore dell'attributo di istruzione SQL_ATTR_PARAMSET_SIZE è maggiore di 1, l'applicazione può utilizzare il valore a cui fa riferimento l'attributo SQL_ATTR_PARAMS_PROCESSED_PTR dell'istruzione con il *ParameterValuePtr* argomento. Ad esempio, *ParameterValuePtr* potrebbe puntare a una matrice di valori e l'applicazione potrebbe utilizzare il valore a cui puntato SQL_ATTR_PARAMS_PROCESSED_PTR per recuperare il valore corretto dalla matrice. Per ulteriori informazioni, vedere "passaggio di valori dei parametri" più avanti in questa sezione.  
  
 Se il *InputOutputType* argomento è SQL_PARAM_INPUT_OUTPUT o SQL_PARAM_OUTPUT, *ParameterValuePtr* punta a un buffer in cui il driver restituisce il valore di output. Se la routine restituisce uno o più set di risultati, il \* *ParameterValuePtr* buffer non è garantito da impostare fino a quando non sono stati elaborati tutti i conteggi o la riga set di risultati. Se il buffer non viene impostato fino a quando non è stata completata l'elaborazione, i parametri di output e i valori restituiti non sono disponibili fino a **SQLMoreResults** restituisce SQL_NO_DATA. La chiamata **SQLCloseCursor** o **SQLFreeStmt** con un'opzione di SQL_CLOSE causerà questi valori verranno ignorati.  
  
 Se è maggiore di 1, il valore dell'attributo di istruzione SQL_ATTR_PARAMSET_SIZE *ParameterValuePtr* punta a una matrice. Una singola istruzione SQL elabora la matrice di valori di input per un parametro di input o input/output completa e restituisce una matrice di valori di output per un input/output o parametro di output.  
  
## <a name="bufferlength-argument"></a>Argomento BufferLength  
 Per i caratteri e i dati binari C, il *BufferLength* argomento specifica la lunghezza del \* *ParameterValuePtr* buffer (se è un elemento singolo) o la lunghezza di un elemento di \* *ParameterValuePtr* matrice (se il valore dell'attributo di istruzione SQL_ATTR_PARAMSET_SIZE è maggiore di 1). Questo argomento consente di impostare il campo del record SQL_DESC_OCTET_LENGTH di APD. Se l'applicazione specifica di più valori, *BufferLength* viene utilizzato per determinare la posizione dei valori di **ParameterValuePtr* matrice, input e output. Per i parametri di input/output e outpui, viene utilizzata per determinare se troncare i caratteri e binari C dati nell'output:  
  
-   Per i dati di tipo carattere C, se il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength*, i dati in \* *ParameterValuePtr* viene troncato a  *BufferLength* meno la lunghezza di un carattere di terminazione null ed è con terminazione null dal driver.  
  
-   Per i dati binari di C, se il numero di byte disponibili da restituire è maggiore di *BufferLength*, i dati in \* *ParameterValuePtr* viene troncato a *BufferLength*byte.  
  
 Per tutti gli altri tipi di dati C, il *BufferLength* argomento viene ignorato. La lunghezza del \* *ParameterValuePtr* buffer (se è un elemento singolo) o la lunghezza di un elemento di \* *ParameterValuePtr* matrice (se l'applicazione chiama  **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_PARAMSET_SIZE per specificare più valori per ogni parametro) si presuppone che sia la lunghezza del tipo di dati C.  
  
 Per flusso di output o i parametri di input/output trasmessi, il *BufferLength* verrà ignorato perché la lunghezza del buffer è stata specificata **SQLGetData**.  
  
> [!NOTE]  
>  Quando un'applicazione ODBC 1.0 chiama **SQLSetParam** in un'applicazione ODBC 3. *x* driver, Driver Manager Converte l'oggetto in una chiamata a **SQLBindParameter** in cui il *BufferLength* argomento è sempre SQL_SETPARAM_VALUE_MAX. Poiché gestione Driver restituisce un errore se un'applicazione ODBC 3. *x* applicazione imposta *BufferLength* a SQL_SETPARAM_VALUE_MAX, un'applicazione ODBC 3. *x* driver può utilizzare per determinare quando viene chiamato da un'applicazione ODBC 1.0.  
  
> [!NOTE]  
>  In **SQLSetParam**, il modo in cui un'applicazione specifica la lunghezza del **ParameterValuePtr* memorizzare nel buffer in modo che il driver può restituire carattere o dati binari e il modo in cui un'applicazione invia un Matrice di caratteri o valori di parametro binario per il driver, driver-definiti.  
  
## <a name="strlenorindptr-argument"></a>Argomento StrLen_or_IndPtr  
 Il *StrLen_or_IndPtr* argomento punta a un buffer che, quando **SQLExecute** o **SQLExecDirect** viene chiamato, contiene uno dei seguenti. (Questo argomento consente di impostare i campi di record SQL_DESC_OCTET_LENGTH_PTR e SQL_DESC_INDICATOR_PTR dei puntatori di parametro dell'applicazione.)  
  
-   La lunghezza del valore del parametro archiviato in **ParameterValuePtr*. Questo viene ignorato, ad eccezione di dati carattere o binario C.  
  
-   SQL_NTS. Il valore del parametro è una stringa con terminazione null.  
  
-   SQL_NULL_DATA. Il valore del parametro è NULL.  
  
-   SQL_DEFAULT_PARAM. Una stored procedure consiste nell'utilizzare il valore predefinito di un parametro, anziché un valore recuperato dall'applicazione. Questo valore è valido solo in una routine denominata nella sintassi canonica ODBC, quindi solo se il *InputOutputType* argomento è SQL_PARAM_INPUT o SQL_PARAM_INPUT_OUTPUT SQL_PARAM_INPUT_OUTPUT_STREAM. Quando \* *StrLen_or_IndPtr* è SQL_DEFAULT_PARAM, il *ValueType*, *ParameterType*, *ColumnSize*,  *DecimalDigits*, *BufferLength*, e *ParameterValuePtr* argomenti vengono ignorati per i parametri di input e vengono utilizzati solo per definire il valore del parametro di output per l'input / i parametri di output.  
  
-   Il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro). Verranno inviati con i dati per il parametro **SQLPutData**. Se il *ParameterType* argomento SQL_LONGVARBINARY, SQL_LONGVARCHAR o long, tipo di dati specifici dell'origine dati e il driver restituisce "Y" per il tipo di informazioni SQL_NEED_LONG_DATA_LEN in **SQLGetInfo**, *lunghezza* è il numero di byte di dati da inviare per il parametro; in caso contrario, *lunghezza* deve essere un valore non negativo e viene ignorato. Per ulteriori informazioni, vedere "Passaggio di valori di parametro," più avanti in questa sezione.  
  
     Ad esempio, per specificare che 10.000 byte di dati verranno inviati con **SQLPutData** in una o più chiamate per un parametro SQL_LONGVARCHAR, un'applicazione imposta **StrLen_or_IndPtr* su SQL_LEN_DATA_AT_EXEC ( 10000).  
  
-   SQL_DATA_AT_EXEC. Verranno inviati con i dati per il parametro **SQLPutData**. Questo valore viene utilizzato dalle applicazioni ODBC 1.0 chiamano ODBC 3. *x* driver. Per ulteriori informazioni, vedere "Passaggio di valori di parametro," più avanti in questa sezione.  
  
 Se *StrLen_or_IndPtr* è un puntatore null, il driver presuppone che tutti i valori di parametro di input sono non NULL e che i dati character e binary sono con terminazione null. Se *InputOutputType* è SQL_PARAM_OUTPUT o SQL_PARAM_OUTPUT_STREAM e *ParameterValuePtr* e *StrLen_or_IndPtr* sono entrambi puntatori null, Elimina il driver il valore di output.  
  
> [!NOTE]  
>  Gli sviluppatori di applicazioni sono assolutamente sconsigliati dall'impostazione di un puntatore null per *StrLen_or_IndPtr* quando il tipo di dati del parametro è SQL_C_BINARY. Per assicurarsi che un driver non in modo imprevisto troncare i dati SQL_C_BINARY, *StrLen_or_IndPtr* deve contenere un puntatore a un valore di lunghezza valida.  
  
 Se il *InputOutputType* argomento è SQL_PARAM_INPUT_OUTPUT, SQL_PARAM_OUTPUT, SQL_PARAM_INPUT_OUTPUT_STREAM o SQL_PARAM_OUTPUT_STREAM, *StrLen_or_IndPtr* punta a un buffer in cui il il driver restituisce SQL_NULL_DATA, il numero di byte disponibili per restituire \* *ParameterValuePtr* (escluso il byte di terminazione null di dati di tipo carattere), o SQL_NO_TOTAL (se il numero di byte disponibili return non può essere determinato). Se la routine restituisce uno o più set di risultati, il **StrLen_or_IndPtr* buffer non è garantito da impostare fino a quando non sono stati recuperati tutti i risultati.  
  
 Se è maggiore di 1, il valore dell'attributo di istruzione SQL_ATTR_PARAMSET_SIZE *StrLen_or_IndPtr* punta a una matrice di valori SQLLEN. Questi può essere uno dei valori elencati in precedenza in questa sezione e vengono elaborati con una singola istruzione SQL.  
  
## <a name="passing-parameter-values"></a>Passaggio di valori di parametro  
 Un'applicazione è possibile passare il valore per un parametro sia nel \* *ParameterValuePtr* buffer o con uno o più chiamate a **SQLPutData**. Parametri i cui dati vengono passati con **SQLPutData** sono note come *data-at-execution* parametri. Questi sono in genere utilizzati per inviare i dati per i parametri SQL_LONGVARBINARY e SQL_LONGVARCHAR e può essere combinati con altri parametri.  
  
 Per passare i valori dei parametri, un'applicazione esegue la sequenza di passaggi seguente:  
  
1.  Chiamate **SQLBindParameter** per ogni parametro associare i buffer per il valore del parametro (*ParameterValuePtr* argomento) e lunghezza/indicatore (*StrLen_or_IndPtr* argomento). Per i parametri data-at-execution, *ParameterValuePtr* è un valore di puntatore definiti dall'applicazione, ad esempio un numero di parametro o un puntatore ai dati. Il valore verrà restituito in un secondo momento e può essere utilizzato per identificare il parametro.  
  
2.  Inserisce i valori per i parametri di input e di input/output nel \* *ParameterValuePtr* e **StrLen_or_IndPtr* buffer:  
  
    -   Per i parametri normali, viene visualizzato il valore del parametro nel \* *ParameterValuePtr* buffer e la lunghezza di tale valore nel **StrLen_or_IndPtr* buffer. Per ulteriori informazioni, vedere [impostazione valori di parametro](../../../odbc/reference/develop-app/setting-parameter-values.md).  
  
    -   Per i parametri data-at-execution, l'applicazione inserisce il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro) (quando si chiama un driver ODBC 2.0) nei **StrLen_or_IndPtr* buffer.  
  
3.  Chiamate **SQLExecute** o **SQLExecDirect** per eseguire l'istruzione SQL.  
  
    -   Se non sono presenti parametri data-at-execution, il processo è stato completato.  
  
    -   Se sono presenti parametri data-at-execution, la funzione restituisce SQL_NEED_DATA.  
  
4.  Chiamate **SQLParamData** per recuperare il valore definito dall'applicazione specificato nel *ParameterValuePtr* argomento di **SQLBindParameter** per la prima parametro data-at-execution da elaborare. **SQLParamData** restituisce SQL_NEED_DATA.  
  
    > [!NOTE]  
    >  Anche se i parametri data-at-execution sono simili a colonne data-at-execution, il valore restituito da **SQLParamData** è diverso per ognuno. I parametri data-at-execution sono parametri in un'istruzione SQL per il quale i dati verranno inviati con **SQLPutData** quando viene eseguita l'istruzione con **SQLExecDirect** o **SQLExecute**. Sono associate con **SQLBindParameter**. Il valore restituito da **SQLParamData** è un valore di puntatore passato a **SQLBindParameter** nel *ParameterValuePtr* argomento. Le colonne data-at-execution sono colonne in un set di righe per cui i dati verranno inviati con **SQLPutData** quando una riga viene aggiornata o aggiunti con **SQLBulkOperations** o aggiornate con **SQLSetPos**. Sono associate con **SQLBindCol**. Il valore restituito da **SQLParamData** è l'indirizzo della riga di **TargetValuePtr* buffer (impostata da una chiamata a **SQLBindCol**) che viene elaborato.  
  
5.  Chiamate **SQLPutData** uno o più volte per inviare i dati per il parametro. Più di una chiamata è necessaria se il valore dei dati è maggiore di \* *ParameterValuePtr* specificato nel buffer **SQLPutData**; più chiamate al metodo **SQLPutData**per lo stesso parametro sono consentiti solo durante l'invio di dati di tipo carattere C a una colonna con un tipo di carattere, binary o dati specifici dell'origine dati o per l'invio di dati C binari a una colonna con un carattere, binario, o tipo di dati specifici dell'origine dati.  
  
6.  Chiamate **SQLParamData** per segnalare che tutti i dati è stato inviato per il parametro.  
  
    -   Se sono presenti più parametri data-at-execution, **SQLParamData** restituisce SQL_NEED_DATA e il valore definito dall'applicazione per il parametro data-at-execution successivo da elaborare. L'applicazione si ripete i passaggi 4 e 5.  
  
    -   Se sono presenti parametri data-at-execution non sono più presenti, il processo è stato completato. Se l'istruzione è stata eseguita correttamente, **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO; se l'esecuzione non riuscita, viene restituito SQL_ERROR. A questo punto, **SQLParamData** può restituire qualsiasi SQLSTATE che può essere restituite dalla funzione che viene utilizzata per eseguire l'istruzione (**SQLExecDirect** o **SQLExecute**).  
  
         Sono disponibili in valori di output per i parametri di input/output o di output di \* *ParameterValuePtr* e **StrLen_or_IndPtr* memorizza nel buffer dopo l'applicazione recupera tutti i set di risultati generato dall'istruzione.  
  
 La chiamata **SQLExecute** o **SQLExecDirect** inserisce l'istruzione in uno stato SQL_NEED_DATA. A questo punto, l'applicazione può chiamare solo **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**, o **SQLPutData** con l'istruzione o *handle di connessione* associate all'istruzione. Se chiama qualsiasi altra funzione con l'istruzione o la connessione associata all'istruzione, la funzione restituisce SQLSTATE HY010 (funzione di errore nella sequenza). Lascia l'istruzione di SQL_NEED_DATA stato quando **SQLParamData** o **SQLPutData** restituisce un errore, **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, o l'istruzione viene annullata.  
  
 Se l'applicazione chiama **SQLCancel** mentre il driver deve comunque i dati per i parametri data-at-execution, il driver Annulla l'esecuzione dell'istruzione; l'applicazione può quindi chiamare **SQLExecute** o  **SQLExecDirect** nuovamente.  
  
## <a name="retrieving-streamed-output-parameters"></a>Il recupero dei parametri di flusso di Output  
 Quando un'applicazione imposta *InputOutputType* SQL_PARAM_INPUT_OUTPUT_STREAM o SQL_PARAM_OUTPUT_STREAM, il valore del parametro di output deve essere recuperato da una o più chiamate a **SQLGetData**. Quando il driver ha un valore di parametro di flusso di output da restituire all'applicazione, verrà restituito SQL_PARAM_DATA_AVAILABLE in risposta a una chiamata alle funzioni seguenti: **SQLMoreResults**, **SQLExecute**, e **SQLExecDirect**. Un'applicazione chiama **SQLParamData** per determinare quale valore del parametro è disponibile.  
  
 Per ulteriori informazioni su SQL_PARAM_DATA_AVAILABLE e parametri di flusso di output, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-arrays-of-parameters"></a>Utilizzo delle matrici di parametri  
 Quando un'applicazione prepara un'istruzione con marcatori di parametro e passa una matrice di parametri, esistono due modi diversi, che questo può essere eseguito. Il driver si basano sulle funzionalità di elaborazione di matrice di back-end, in cui i case l'intera istruzione con la matrice di parametri viene trattato come un'unità atomica è. Oracle è un esempio di un'origine dati che supporta la funzionalità di elaborazione di matrice. È possibile implementare questa funzionalità per il driver per un batch di istruzioni SQL, un'istruzione SQL per ogni set di parametri nella matrice di parametri, generare ed eseguire il batch. Le matrici di parametri non possono essere utilizzate con un **WHERE CURRENT OF di aggiornamento** istruzione.  
  
 Quando viene elaborata una matrice di parametri, i conteggi di set o la riga di risultati singolo (uno per ogni set di parametri) possono essere disponibili o conteggi o righe di set di risultati possono essere eseguiti in un unico. Opzione di SQL_PARAM_ARRAY_ROW_COUNTS **SQLGetInfo** indica se sono disponibili per ogni set di parametri (SQL_PARC_BATCH) i conteggi delle righe o conteggio solo una riga è disponibile (SQL_PARC_NO_BATCH).  
  
 Opzione di SQL_PARAM_ARRAY_SELECTS **SQLGetInfo** indica se un set di risultati è disponibile per ogni set di parametri (SQL_PAS_BATCH) o solo un set di risultati è disponibile (SQL_PAS_NO_BATCH). Se il driver non consente un'istruzione di creazione di set di risultati deve essere eseguito con una matrice di parametri, SQL_PARAM_ARRAY_SELECTS restituisce SQL_PAS_NO_SELECT.  
  
 Per ulteriori informazioni, vedere [funzione SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 Per supportare le matrici di parametri, l'attributo di istruzione SQL_ATTR_PARAMSET_SIZE è impostato per specificare il numero di valori per ogni parametro. Se il campo è maggiore di 1, i campi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR di APD devono puntare a matrici. La cardinalità di ogni matrice è uguale al valore di SQL_ATTR_PARAMSET_SIZE.  
  
 Il campo SQL_DESC_ROWS_PROCESSED_PTR di APD punta a un buffer che contiene il numero di set di parametri che sono stati elaborati, compresi i set di errore. Durante l'elaborazione di ogni set di parametri, il driver archivia un nuovo valore nel buffer. Se si tratta di un puntatore null, non verrà restituito alcun numero. Quando si utilizzano matrici di parametri, il valore a cui fa riferimento il campo SQL_DESC_ROWS_PROCESSED_PTR di APD viene popolato anche se viene restituito SQL_ERROR dalla funzione di impostazione. Se viene restituito SQL_NEED_DATA, il valore a cui fa riferimento il campo SQL_DESC_ROWS_PROCESSED_PTR di APD è impostato per il set di parametri che viene elaborato.  
  
 Cosa accade quando è associata una matrice di parametri e un **WHERE CURRENT OF di aggiornamento** viene eseguita l'istruzione è definito dal driver.  
  
## <a name="column-wise-parameter-binding"></a>L'associazione di parametri  
 Nell'associazione per colonna, l'applicazione associa il parametro separato e matrici di lunghezza/indicatore a ogni parametro.  
  
 Per utilizzare l'associazione per colonna, l'applicazione imposta innanzitutto l'attributo di istruzione SQL_ATTR_PARAM_BIND_TYPE su SQL_PARAM_BIND_BY_COLUMN. (Questo è il valore predefinito). Per ogni colonna da associare, l'applicazione esegue i passaggi seguenti:  
  
1.  Alloca una matrice di buffer di parametri.  
  
2.  Alloca una matrice di buffer di lunghezza/indicatore.  
  
    > [!NOTE]  
    >  Se l'applicazione scrive direttamente descrittori quando viene utilizzata l'associazione per colonna, è possono utilizzare matrici separate per i dati di lunghezza e indicatore.  
  
3.  Chiamate **SQLBindParameter** con gli argomenti seguenti:  
  
    -   *ValueType* è il tipo C di un singolo elemento nella matrice di buffer del parametro.  
  
    -   *ParameterType* è il tipo SQL del parametro.  
  
    -   *ParameterValuePtr* è l'indirizzo della matrice di buffer del parametro.  
  
    -   *BufferLength* è la dimensione di un singolo elemento nella matrice di buffer del parametro. Il *BufferLength* argomento viene ignorato quando i dati sono dati a lunghezza fissa.  
  
    -   *StrLen_or_IndPtr* è l'indirizzo della matrice di lunghezza/indicatore.  
  
 Per ulteriori informazioni sull'uso di queste informazioni, vedere la sezione "ParameterValuePtr argomento" in "Commenti", più avanti in questa sezione. Per ulteriori informazioni sulle associazioni di parametri, vedere [matrici di parametri di associazione](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="row-wise-parameter-binding"></a>L'associazione dei parametri  
 Nell'associazione per riga, l'applicazione definisce una struttura che contiene i parametri e lunghezza/indicatore buffer per ogni parametro deve essere associata.  
  
 Per utilizzare l'associazione per riga, l'applicazione esegue i passaggi seguenti:  
  
1.  Definisce una struttura per contenere un singolo set di parametri (inclusi i buffer di parametro sia di lunghezza/indicatore) e alloca una matrice di strutture.  
  
    > [!NOTE]  
    >  Se l'applicazione scrive direttamente descrittori quando viene utilizzata l'associazione per riga, è possono utilizzare campi separati per i dati di lunghezza e indicatore.  
  
2.  Imposta l'attributo di istruzione SQL_ATTR_PARAM_BIND_TYPE sulla dimensione della struttura che contiene un singolo set di parametri o alle dimensioni di un'istanza di un buffer in cui verranno associati ai parametri. La lunghezza deve includere lo spazio per tutti i parametri associati ed eventuale riempimento della struttura o del buffer, per assicurarsi che quando l'indirizzo di un parametro associato viene incrementato con la lunghezza specificata, il risultato punterà all'inizio del parametro stesso di riga successiva. Quando si utilizza il *sizeof* operatore in ANSI C, questo comportamento è garantito.  
  
3.  Chiamate **SQLBindParameter** con gli argomenti seguenti per ogni parametro di associazione:  
  
    -   *ValueType* è il tipo del membro di buffer di parametro da associare alla colonna.  
  
    -   *ParameterType* è il tipo SQL del parametro.  
  
    -   *ParameterValuePtr* è l'indirizzo del membro buffer parametro nel primo elemento della matrice.  
  
    -   *BufferLength* è la dimensione del membro di buffer del parametro.  
  
    -   *StrLen_or_IndPtr* è l'indirizzo del membro lunghezza/indicatore da associare.  
  
 Per ulteriori informazioni sull'uso di queste informazioni, vedere "*ParameterValuePtr* argomento," più avanti in questa sezione. Per ulteriori informazioni sull'associazione per riga di parametri, vedere il [matrici di parametri di associazione](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="error-information"></a>Informazioni sull'errore  
 Se un driver non implementa le matrici di parametri come batch (l'opzione SQL_PARAM_ARRAY_ROW_COUNTS è uguale a SQL_PARC_NO_BATCH), situazioni di errore vengono gestiti come se sono stata eseguita una sola istruzione. Se il driver implementa le matrici di parametri come batch, un'applicazione può utilizzare il campo di intestazione SQL_DESC_ARRAY_STATUS_PTR del IPD per determinare quale parametro di un'istruzione SQL o ha causato il parametro in una matrice di parametri  **SQLExecDirect** o **SQLExecute** per restituire un errore. Questo campo contiene informazioni sullo stato per ogni riga di valori di parametro. Se il campo indica che si è verificato un errore, campi della struttura di dati di diagnostica verranno indicato il numero di riga e di parametro del parametro che non è riuscita. Nel campo di intestazione SQL_DESC_ARRAY_SIZE in APD, che può essere impostata dall'attributo di istruzione SQL_ATTR_PARAMSET_SIZE verrà definito il numero di elementi nella matrice.  
  
> [!NOTE]  
>  Il campo di intestazione SQL_DESC_ARRAY_STATUS_PTR in APD viene utilizzato per ignorare i parametri. Per ulteriori informazioni su come ignorare i parametri, vedere la sezione successiva, "Verrà ignorato un Set di parametri".  
  
 Quando **SQLExecute** o **SQLExecDirect** restituisce SQL_ERROR, gli elementi nella matrice a cui fa riferimento il campo SQL_DESC_ARRAY_STATUS_PTR il IPD conterrà SQL _ SQL_PARAM_ERROR, SQL_PARAM_SUCCESS, PARAM_SUCCESS_WITH_INFO SQL_PARAM_UNUSED o SQL_PARAM_DIAG_UNAVAILABLE.  
  
 Per ogni elemento nella matrice, la struttura di dati di diagnostica contiene uno o più record di stato. Il campo SQL_DIAG_ROW_NUMBER della struttura indica il numero di riga dei valori di parametro che ha causato l'errore. Se è possibile determinare il parametro specifico in una riga di parametri che ha causato l'errore, il numero di parametro verrà immesso nel campo SQL_DIAG_COLUMN_NUMBER.  
  
 SQL_PARAM_UNUSED viene immesso quando un parametro non è stato usato perché si è verificato un errore in un parametro precedente che forzato **SQLExecute** o **SQLExecDirect** da interrompere. Ad esempio, se sono presenti 50 parametri e un errore durante l'esecuzione il set di parametri che ha causato fortieth **SQLExecute** o **SQLExecDirect** per interrompere, quindi SQL_PARAM_UNUSED viene immesso nel Matrice di stato per i parametri 41 e 50.  
  
 SQL_PARAM_DIAG_UNAVAILABLE viene immesso quando il driver considera le matrici di parametri come unità monolitica, in modo non genera questo livello di singolo parametro di informazioni sull'errore.  
  
 Alcuni errori nell'elaborazione di un singolo set di parametri di causano l'elaborazione dei set di parametri successivi nella matrice da arrestare. Altri errori non influenzano l'elaborazione dei parametri successivi. Quali errori arresterà l'elaborazione è definito dal driver. Se l'elaborazione non è stata arrestata, vengono elaborati tutti i parametri nella matrice, a causa dell'errore viene restituito SQL_SUCCESS_WITH_INFO e il buffer definito da SQL_ATTR_PARAMS_PROCESSED_PTR viene impostato per il numero totale di set di parametri elaborati (come definito per il Attributo di istruzione SQL_ATTR_PARAMSET_SIZE), che include il set di errore.  
  
> [!CAUTION]  
>  Comportamento ODBC quando si verifica un errore nell'elaborazione di una matrice di parametri è diverso in ODBC 3. *x* rispetto a ODBC 2. *x*. In ODBC 2. *x*, la funzione ha restituito SQL_ERROR e l'elaborazione non siano più. Il buffer a cui punta il *pirow* argomento di **SQLParamOptions** contiene il numero di riga di errore. In ODBC 3. *x*, la funzione restituisce SQL_SUCCESS_WITH_INFO e l'elaborazione può essere arrestato o continuare. Se continua, il buffer specificato da SQL_ATTR_PARAMS_PROCESSED_PTR imposterà il valore di tutti i parametri elaborati, incluse quelle che hanno restituito un errore. Questa modifica nel comportamento può causare problemi per le applicazioni esistenti.  
  
 Quando **SQLExecute** o **SQLExecDirect** restituisce prima di completare l'elaborazione di tutti i set di parametri in una matrice di parametri, ad esempio quando viene restituito SQL_ERROR o SQL_NEED_DATA, contiene la matrice di stato stati per i parametri che sono state già elaborati. Il percorso a cui fa riferimento il campo SQL_DESC_ROWS_PROCESSED_PTR il IPD contiene il numero di riga nella matrice del parametro che ha causato il codice di errore SQL_ERROR o SQL_NEED_DATA. Quando una matrice di parametri viene inviata a un'istruzione SELECT, la disponibilità di matrice di valori di stato è definito dal driver; che potrebbero essere disponibili dopo l'istruzione è stata eseguita o come risultato set vengono recuperati.  
  
## <a name="ignoring-a-set-of-parameters"></a>Ignorare un Set di parametri  
 Il campo SQL_DESC_ARRAY_STATUS_PTR di APD (come impostato per il tipo di istruzione sql_attr_param_status_ptr) può essere utilizzato per indicare che un set di parametri associati in un'istruzione SQL deve essere ignorato. Per indirizzare il driver per ignorare uno o più set di parametri durante l'esecuzione, un'applicazione deve eseguire la procedura seguente:  
  
1.  Chiamare **SQLSetDescField** per impostare il campo di intestazione SQL_DESC_ARRAY_STATUS_PTR di APD in modo che punti a una matrice di valori SQLUSMALLINT contengono informazioni sullo stato. Questo campo può essere impostato anche chiamando **SQLSetStmtAttr** con un *attributo* di SQL_ATTR_PARAM_OPERATION_PTR, che consente a un'applicazione impostare il campo senza ottenere un handle descrittore.  
  
2.  Impostare ogni elemento della matrice di cui è definita dal campo SQL_DESC_ARRAY_STATUS_PTR di APD su uno dei due valori:  
  
    -   SQL_PARAM_IGNORE, a indicare che la riga viene escluso dall'esecuzione dell'istruzione.  
  
    -   SQL_PARAM_PROCEED, per indicare che la riga viene inclusa nell'esecuzione dell'istruzione.  
  
3.  Chiamare **SQLExecDirect** o **SQLExecute** per eseguire l'istruzione preparata.  
  
 Le regole seguenti si applicano alla matrice definita dal campo SQL_DESC_ARRAY_STATUS_PTR di APD:  
  
-   Il puntatore è impostato su null per impostazione predefinita.  
  
-   Se il puntatore è null, vengono utilizzati tutti i set di parametri, come se tutti gli elementi sono stati impostati su SQL_ROW_PROCEED.  
  
-   L'impostazione di un elemento a SQL_PARAM_PROCEED non garantisce che l'operazione utilizzerà quel particolare set di parametri.  
  
-   SQL_PARAM_PROCEED è definito come 0 nel file di intestazione.  
  
 Un'applicazione può impostare il SQL_DESC_ARRAY_STATUS_PTR campo in APD in modo che punti allo stesso array a cui fa riferimento in base al campo SQL_DESC_ARRAY_STATUS_PTR nell'implementazione. Ciò è utile quando i parametri di associazione ai dati di riga. Parametri possono quindi essere ignorati in base allo stato della riga di dati. Oltre a SQL_PARAM_IGNORE, i seguenti codici di causano un parametro in un'istruzione SQL verrà ignorato: SQL_ROW_DELETED, SQL_ROW_UPDATED e SQL_ROW_ERROR. Oltre a SQL_PARAM_PROCEED, i codici seguenti determinano un'istruzione SQL continuare: SQL_ROW_SUCCESS SQL_ROW_SUCCESS_WITH_INFO e SQL_ROW_ADDED.  
  
## <a name="rebinding-parameters"></a>Associazione di parametri  
 Un'applicazione può eseguire una delle due operazioni per modificare un'associazione:  
  
-   Chiamare **SQLBindParameter** per specificare una nuova associazione per una colonna che è già associata. Il driver sovrascrive l'associazione precedente con quello nuovo.  
  
-   Specificare un offset da aggiungere all'indirizzo del buffer che è stato specificato tramite la chiamata di associazione di **SQLBindParameter**. Per ulteriori informazioni, vedere la sezione successiva, "Riassociazione con offset".  
  
## <a name="rebinding-with-offsets"></a>Riassociazione con offset  
 Riassociazione dei parametri è particolarmente utile quando un'applicazione dispone di un'installazione di area del buffer che può contenere un numero di parametri ma una chiamata a **SQLExecDirect** o **SQLExecute** utilizza solo alcuni dei parametri. Lo spazio rimanente nell'area del buffer è utilizzabile per il successivo set di parametri modificando il binding esistente da un offset.  
  
 Il campo di intestazione SQL_DESC_BIND_OFFSET_PTR in APD punta all'offset dell'associazione. Se il campo è non null, il driver Dereferenzia il puntatore e, se nessuno dei valori nei campi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR è un puntatore null, aggiunge il valore dereferenziato a tali campi nel descrittore di record in fase di esecuzione. Quando vengono eseguite le istruzioni SQL, vengono utilizzati i nuovi valori di puntatore. L'offset rimane valido dopo la riassociazione. Poiché SQL_DESC_BIND_OFFSET_PTR è un puntatore all'offset anziché l'offset stesso, un'applicazione cambiare l'offset direttamente, senza dover chiamare [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) o [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md) per modificare il campo di descrizione. Il puntatore è impostato su null per impostazione predefinita. Il campo SQL_DESC_BIND_OFFSET_PTR del ARD può essere impostato da una chiamata a [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) o da una chiamata a [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)con un *fAttribute* di SQL_ATTR_PARAM_BIND_ OFFSET_PTR.  
  
 L'offset di associazione viene sempre aggiunto direttamente ai valori nei campi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR. Se l'offset viene modificato in un valore diverso, il nuovo valore risulta ancora aggiunto direttamente al valore di ogni campo di descrizione. Il nuovo offset non viene aggiunta alla somma di qualsiasi offset precedenti e il valore del campo.  
  
## <a name="descriptors"></a>Descrittori  
 Modalità di associazione di un parametro è determinato dai campi del Apd e IPD, Implementation. Gli argomenti in **SQLBindParameter** vengono utilizzati per impostare i campi di descrizione. I campi possono essere impostati anche il **SQLSetDescField** funzioni, anche se **SQLBindParameter** è più efficiente l'utilizzo in quanto l'applicazione non è necessario ottenere un handle di descrittore per chiamare **SQLBindParameter**.  
  
> [!CAUTION]  
>  La chiamata **SQLBindParameter** per un'istruzione può influire sulle altre istruzioni. Questo errore si verifica quando il ARD associate all'istruzione viene allocato in modo esplicito ed è inoltre associata con altre istruzioni. Poiché **SQLBindParameter** modifica i campi di APD, le modifiche si applicano a tutte le istruzioni a cui è associato questo descrittore. In caso contrario il comportamento richiesto, l'applicazione deve annullare l'associazione di questo descrittore da altre istruzioni prima di chiamare **SQLBindParameter**.  
  
 Concettualmente, **SQLBindParameter** esegue i passaggi seguenti in sequenza:  
  
1.  Chiamate [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) per ottenere l'handle APD.  
  
2.  Chiamate [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) per ottenere campo SQL_DESC_COUNT del APD e se il valore della *ColumnNumber* argomento supera il valore di SQL_DESC_COUNT, chiamate **SQLSetDescField**per aumentare il valore di SQL_DESC_COUNT a *ColumnNumber*.  
  
3.  Chiamate [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) più volte per assegnare valori ai campi di APD seguenti:  
  
    -   Imposta il valore di SQL_DESC_TYPE e SQL_DESC_CONCISE_TYPE *ValueType*, ad eccezione del fatto che se *ValueType* è uno degli identificatori di un sottotipo di datetime o intervallo concisi, imposta SQL_DESC_TYPE su SQL _ DATETIME o SQL_INTERVAL, rispettivamente, imposta SQL_DESC_CONCISE_TYPE all'identificatore di conciso e SQL_DESC_DATETIME_INTERVAL_CODE al corrispondente valore datetime o codice secondario dell'intervallo.  
  
    -   Imposta sul valore del campo SQL_DESC_OCTET_LENGTH *BufferLength*.  
  
    -   Imposta il campo SQL_DESC_DATA_PTR al valore di *ParameterValue*.  
  
    -   Imposta sul valore del campo SQL_DESC_OCTET_LENGTH_PTR *StrLen_or_Ind*.  
  
    -   Imposta il campo SQL_DESC_INDICATOR_PTR anche il valore *StrLen_or_Ind*.  
  
     Il *StrLen_or_Ind* parametro specifica le informazioni sugli indicatori sia la lunghezza del valore del parametro.  
  
4.  Chiamate [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) per ottenere l'handle IPD.  
  
5.  Chiamate [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) per ottenere SQL_DESC_COUNT campo del IPD e se il valore della *ColumnNumber* argomento supera il valore di SQL_DESC_COUNT, chiamate **SQLSetDescField**per aumentare il valore di SQL_DESC_COUNT a *ColumnNumber*.  
  
6.  Chiamate [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) più volte per assegnare valori ai campi seguenti del IPD:  
  
    -   Imposta il valore di SQL_DESC_TYPE e SQL_DESC_CONCISE_TYPE *ParameterType*, ad eccezione del fatto che se *ParameterType* è uno degli identificatori di un sottotipo di datetime o intervallo concisi, imposta SQL_DESC_TYPE SQL_DATETIME o SQL_INTERVAL, rispettivamente, imposta SQL_DESC_CONCISE_TYPE per l'identificatore conciso e SQL_DESC_DATETIME_INTERVAL_CODE su valore datetime corrispondente o codice secondario dell'intervallo.  
  
    -   Imposta uno o più, SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION e SQL_DESC_LENGTH come appropriato per *ParameterType*.  
  
    -   Imposta il valore di SQL_DESC_SCALE *DecimalDigits*.  
  
 Se la chiamata a **SQLBindParameter** ha esito negativo, il contenuto dei campi di descrizione che sarebbe impostato in APD sono definiti e il campo SQL_DESC_COUNT di APD viene modificato. Inoltre, non sono definiti i campi SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE e SQL_DESC_TYPE del record appropriato di IPD e il campo SQL_DESC_COUNT del IPD rimane immutato.  
  
## <a name="conversion-of-calls-to-and-from-sqlsetparam"></a>Conversione di chiamate da e verso SQLSetParam  
 Quando un'applicazione ODBC 1.0 chiama **SQLSetParam** in un'applicazione ODBC 3. *x* driver ODBC 3. *x* gestione Driver esegue il mapping di chiamata, come illustrato nella tabella seguente.  
  
|Chiamare dall'applicazione ODBC 1.0|Chiamata eseguita per ODBC 3. *x* driver|  
|----------------------------------|-------------------------------|  
|SQLSetParam (StatementHandle, ParameterNumber, ValueType, ParameterType, LengthPrecision, ParameterScale, ParameterValuePtr, StrLen_or_IndPtr);|SQLBindParameter (StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, *ColumnSize*, *DecimalDigits*, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX,      StrLen_or_IndPtr);|  
  
## <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione prepara un'istruzione SQL per inserire dati nella tabella ORDERS. Per ogni parametro nell'istruzione, l'applicazione chiama **SQLBindParameter** per specificare il tipo di dati ODBC C e il tipo di dati SQL del parametro e per associare un buffer a ogni parametro. Per ogni riga di dati, l'applicazione assegna i valori dei dati per ogni parametro e chiama **SQLExecute** per eseguire l'istruzione.  
  
 L'esempio seguente si presuppone la presenza di un'origine dati ODBC nel computer denominato Northwind che è associato al database Northwind.  
  
 Per ulteriori esempi di codice, vedere [funzione SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [funzione SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md), [funzione SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), e [funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```  
// SQLBindParameter_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define EMPLOYEE_ID_LEN 10  
  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLSMALLINT sCustID;  
  
SQLCHAR szEmployeeID[EMPLOYEE_ID_LEN];  
SQL_DATE_STRUCT dsOrderDate;  
SQLINTEGER cbCustID = 0, cbOrderDate = 0, cbEmployeeID = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, EMPLOYEE_ID_LEN, 0, szEmployeeID, 0, &cbEmployeeID);  
   retcode = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sCustID, 0, &cbCustID);  
   retcode = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TIMESTAMP, sizeof(dsOrderDate), 0, &dsOrderDate, 0, &cbOrderDate);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"INSERT INTO Orders(CustomerID, EmployeeID, OrderDate) VALUES (?, ?, ?)", SQL_NTS);  
  
   strcpy_s((char*)szEmployeeID, _countof(szEmployeeID), "BERGS");  
   sCustID = 5;  
   dsOrderDate.year = 2006;  
   dsOrderDate.month = 3;  
   dsOrderDate.day = 17;  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione esegue una stored procedure SQL Server utilizzando un parametro denominato.  
  
```  
// SQLBindParameter_Function_2.cpp  
// compile with: ODBC32.lib  
// sample assumes the following stored procedure:  
// use northwind  
// DROP PROCEDURE SQLBindParameter  
// GO  
//   
// CREATE PROCEDURE SQLBindParameter @quote int  
// AS  
// delete from orders where OrderID >= @quote  
// GO  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
SQLHDESC hIpd = NULL;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLCHAR szQuote[50] = "100084";  
SQLINTEGER cbValue = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"{call SQLBindParameter(?)}", SQL_NTS);  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 50, 0, szQuote, 0, &cbValue);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
   retcode = SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituzione di informazioni su un parametro in un'istruzione|[Funzione SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Il buffer di parametri nell'istruzione di rilascio|[Funzione SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Restituzione del numero di parametri dell'istruzione|[Funzione SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|Restituisce il parametro successivo per l'invio di dati|[Funzione SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Specifica di più valori di parametro|[Funzione SQLParamOptions](../../../odbc/reference/syntax/sqlparamoptions-function.md)|  
|L'invio di dati del parametro in fase di esecuzione|[Funzione SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Recupero di parametri di output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
