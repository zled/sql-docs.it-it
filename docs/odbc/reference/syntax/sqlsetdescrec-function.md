---
title: Funzione SQLSetDescRec | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c817bad04757820b7c8ee83905fbc0fad08b4e26
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetdescrec-function"></a>Funzione SQLSetDescRec
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 Il **SQLSetDescRec** funzione imposta più campi di descrizione che interessano il tipo di dati e buffer a una colonna o parametro dati associati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLSetDescRec(  
      SQLHDESC      DescriptorHandle,  
      SQLSMALLINT   RecNumber,  
      SQLSMALLINT   Type,  
      SQLSMALLINT   SubType,  
      SQLLEN        Length,  
      SQLSMALLINT   Precision,  
      SQLSMALLINT   Scale,  
      SQLPOINTER    DataPtr,  
      SQLLEN *      StringLengthPtr,  
      SQLLEN *      IndicatorPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *DescriptorHandle*  
 [Input] Handle di descrittore. Non deve essere un handle IRD.  
  
 *RecNumber*  
 [Input] Indica se il descrittore record che contiene i campi da impostare. Record del descrittore sono numerati da 0, con il numero di record 0 è il record di segnalibro. Questo argomento deve essere uguale o maggiore di 0. Se *RecNumber* è maggiore del valore di SQL_DESC_COUNT, SQL_DESC_COUNTis stato impostato il valore di *RecNumber*.  
  
 *Tipo*  
 [Input] Il valore su cui impostare il campo SQL_DESC_TYPE per il record del descrittore.  
  
 *Sottotipo*  
 [Input] Per i record il cui tipo è SQL_DATETIME o SQL_INTERVAL, questo è il valore su cui impostare il campo SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *Lunghezza*  
 [Input] Il valore su cui impostare il campo SQL_DESC_OCTET_LENGTH per il record del descrittore.  
  
 *Precisione*  
 [Input] Il valore su cui impostare il campo SQL_DESC_PRECISION per il record del descrittore.  
  
 *Scala*  
 [Input] Il valore su cui impostare il campo SQL_DESC_SCALE per il record del descrittore.  
  
 *DataPtr*  
 [Posticipata di Input o Output] Il valore su cui impostare il campo SQL_DESC_DATA_PTR per il record del descrittore. *DataPtr* può essere impostata su un puntatore null.  
  
 Il *DataPtr* argomento può essere impostato su un puntatore null per impostare il campo SQL_DESC_DATA_PTR su un puntatore null. Se l'handle di *DescriptorHandle* argomento è associato a un ARD, questo viene disassociata la colonna.  
  
 *StringLengthPtr*  
 [Posticipata di Input o Output] Il valore su cui impostare il campo SQL_DESC_OCTET_LENGTH_PTR per il record del descrittore. *StringLengthPtr* può essere impostata su un puntatore null per impostare il campo SQL_DESC_OCTET_LENGTH_PTR su un puntatore null.  
  
 *IndicatorPtr*  
 [Posticipata di Input o Output] Il valore su cui impostare il campo SQL_DESC_INDICATOR_PTR per il record del descrittore. *IndicatorPtr* può essere impostata su un puntatore null per impostare il campo SQL_DESC_INDICATOR_PTR su un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetDescRec** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_DESC e *gestire* di *DescriptorHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLSetDescRec** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07009|Indice del descrittore non valido|Il *RecNumber* argomento è stato impostato su 0 e *DescriptorHandle* cui fa riferimento a un handle IPD.<br /><br /> Il *RecNumber* argomento è minore di 0.<br /><br /> Il *RecNumber* argomento è maggiore del numero massimo di colonne o parametri in grado di supportare l'origine dati, e *DescriptorHandle* argomento è un APD, IPD o ARD.<br /><br /> Il *RecNumber* argomento è uguale a 0 e *DescriptorHandle* argomento cui fa riferimento a un APD allocato in modo implicito. (Questo errore si verifica con un descrittore allocato in modo esplicito dell'applicazione perché non è noto un descrittore allocato in modo esplicito dell'applicazione, sia un APD ARD fino alla fase di esecuzione.)|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY010|Errore nella sequenza (funzione)|(DM) il *DescriptorHandle* è stato associato un *StatementHandle* per i quali è stata chiamata una funzione in modo asincrono in esecuzione (non presente) ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il  *StatementHandle* con cui il *DescriptorHandle* è stato associato e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima che sono stati inviati dati per tutti i parametri data-at-execution o colonne.<br /><br /> (DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *DescriptorHandle*. Questa funzione aynchronous era ancora in esecuzione quando il **SQLSetDescRec** funzione è stata chiamata.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per uno degli handle di istruzione associati il *DescriptorHandle* e SQL_PARAM_DATA_AVAILABLE restituito. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY016|Non è possibile modificare un descrittore della riga di implementazione|Il *DescriptorHandle* argomento è stato associato un IRD.|  
|HY021|Informazioni del descrittore incoerenti.|Il *tipo* campo o qualsiasi altro campo associato al campo SQL_DESC_TYPE nel descrittore di, non è coerente o non valido.<br /><br /> Informazioni sul descrittore controllati durante una verifica coerenza non era coerente. (Vedere "Controlli di consistenza," più avanti in questa sezione).|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il driver non è un'API ODBC 2*x* driver, il descrittore è un ARD, il *ColumnNumber* argomento è stato impostato su 0 e il valore specificato per l'argomento *BufferLength* stato non è uguale a 4.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *DescriptorHandle* non supporta la funzione.|  
  
## <a name="comments"></a>Commenti  
 Un'applicazione può chiamare **SQLSetDescRec** per impostare i campi seguenti per una singola colonna o parametro:  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (per i record il cui tipo è SQL_DATETIME o SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Se una chiamata a **SQLSetDescRec** ha esito negativo, il contenuto del record del descrittore identificate le *RecNumber* argomento non sono definiti.  
  
 Quando si associa una colonna o parametro, **SQLSetDescRec** consente di modificare più campi che interessano l'associazione senza chiamare **SQLBindCol** o **SQLBindParameter** o effettuare più chiamate al **SQLSetDescField**. **SQLSetDescRec** impostare campi su un descrittore non è attualmente associato a un'istruzione. Si noti che **SQLBindParameter** imposta più campi **SQLSetDescRec**, impostare campi su un APD sia un IPD in un'unica chiamata e non richiede un handle descrittore.  
  
> [!NOTE]  
>  L'attributo di istruzione SQL_ATTR_USE_BOOKMARKS deve sempre essere impostata prima di chiamare **SQLSetDescRec** con un *RecNumber* argomento pari a 0 per impostare i campi di segnalibro. Sebbene non sia obbligatorio, è consigliabile.  
  
## <a name="consistency-checks"></a>Verifiche di coerenza  
 Un controllo di coerenza viene eseguito automaticamente dal driver ogni volta che un'applicazione imposta il campo SQL_DESC_DATA_PTR del APD, ARD o IPD. Se uno dei campi è incoerente con gli altri campi, **SQLSetDescRec** restituiranno SQLSTATE HY021 (le informazioni del descrittore incoerenti).  
  
 Ogni volta che un'applicazione imposta il campo SQL_DESC_DATA_PTR del APD, ARD o IPD, il driver verificherà che il valore del campo SQL_DESC_TYPE e i valori applicabili a quel campo SQL_DESC_TYPE siano validi e coerenti. Questo controllo è sempre eseguiti quando **SQLBindParameter** o **SQLBindCol** viene chiamato o quando **SQLSetDescRec** viene chiamato per un APD, ARD o IPD. Questo controllo di coerenza include i controlli seguenti in campi di descrizione:  
  
-   Il campo SQL_DESC_TYPE deve essere valido ODBC C o tipi SQL o un tipo SQL specifici del driver. Il campo SQL_DESC_CONCISE_TYPE deve essere uno dei tipi di dati ODBC C o SQL validi o un tipo SQL o C specifici del driver, inclusi i tipi di data/ora e intervallo concisi.  
  
-   Se il campo di record SQL_DESC_TYPE è SQL_DATETIME o SQL_INTERVAL, il campo SQL_DESC_DATETIME_INTERVAL_CODE deve essere uno dei codici di intervallo o datetime valido. (Vedere la descrizione del campo SQL_DESC_DATETIME_INTERVAL_CODE [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Se il campo SQL_DESC_TYPE indica un tipo numerico, vengono verificati i campi SQL_DESC_PRECISION e SQL_DESC_SCALE sia valido.  
  
-   Se il campo SQL_DESC_CONCISE_TYPE è un tipo di dati di ora o timestamp, un intervallo di tipo con un componente di secondi, o uno dei tipi di dati di intervallo con un componente di ora, il campo SQL_DESC_PRECISION viene verificato da una precisione in secondi valido.  
  
-   Se il SQL_DESC_CONCISE_TYPE è un tipo di dati di intervallo, il campo SQL_DESC_DATETIME_INTERVAL_PRECISION viene verificato che sia un valore di precisione iniziale intervallo valido.  
  
 Il campo SQL_DESC_DATA_PTR di un IPD non è in genere impostato; Tuttavia, un'applicazione può farlo per forzare un controllo di coerenza dei campi IPD. Impossibile eseguire una verifica coerenza su un'implementazione. Il valore impostato per il campo SQL_DESC_DATA_PTR del IPD non vengono effettivamente archiviato e non è possibile recuperare da una chiamata a **SQLGetDescField** o **SQLGetDescRec**; l'impostazione viene eseguita solo per forzare il verifica della coerenza.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di una colonna|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Associazione di un parametro|[Funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Recupero di un campo di descrizione singolo|[Funzione SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Recupero di più campi di descrizione|[Funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|L'impostazione di campi di descrizione singolo|[Funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
