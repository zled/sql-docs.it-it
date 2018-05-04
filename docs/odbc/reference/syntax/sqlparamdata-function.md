---
title: Funzione SQLParamData | Documenti Microsoft
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
- SQLParamData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLParamData
helpviewer_keywords:
- SQLParamData function [ODBC]
ms.assetid: 68fe010d-9539-4e5b-a260-c8d32423b1db
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 936a45822c06eb530be077f4a43249579ac42c86
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlparamdata-function"></a>SQLParamData-funzione
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLParamData** viene utilizzata in combinazione con **SQLPutData** per fornire i dati dei parametri in fase di esecuzione di istruzione e con **SQLGetData** per recuperare i dati dei parametri di output inviati come flusso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *ValuePtrPtr*  
 [Output] Puntatore a un buffer in cui si desidera restituire l'indirizzo del *ParameterValuePtr* specificato nel buffer **SQLBindParameter** (per i dati di parametri) o l'indirizzo del *TargetValuePtr* specificato nel buffer **SQLBindCol** (per i dati di colonna), contenuta nel campo del record del descrittore SQL_DESC_DATA_PTR.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE o SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLParamData** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLParamData** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Il valore di dati identificato dal *ValueType* argomento **SQLBindParameter** per non è possibile convertire il parametro associato al tipo di dati identificato dal *ParameterType*argomento **SQLBindParameter**.<br /><br /> Il valore di dati restituito per un parametro di associazione come SQL_PARAM_INPUT_OUTPUT o SQL_PARAM_OUTPUT Impossibile convertire nel tipo di dati identificato dal *ValueType* argomento **SQLBindParameter**.<br /><br /> (Se non è stato possibile convertire i valori dei dati per una o più righe, ma una o più righe sono state restituite correttamente, Microsoft questa funzione restituisce SQL_SUCCESS_WITH_INFO.)|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22026|Lunghezza dei dati non corrispondente.|Il tipo di informazioni SQL_NEED_LONG_DATA_LEN **SQLGetInfo** è "Y" e minore quantità di dati è stato inviato per un parametro long (tipo di dati è stato SQL_LONGVARCHAR, SQL_LONGVARBINARY o un tipo di dati specifici dell'origine dati di tipo long) rispetto a quello indicato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**.<br /><br /> Il tipo di informazioni SQL_NEED_LONG_DATA_LEN **SQLGetInfo** è "Y" e minore quantità di dati è stato inviato per una colonna long (tipo di dati è stato SQL_LONGVARCHAR, SQL_LONGVARBINARY o un tipo di dati specifici dell'origine dati di tipo long) rispetto a quello indicato di buffer di lunghezza corrispondente a una colonna in una riga di dati che è stato aggiunto o aggiornati con **SQLBulkOperations** o aggiornate con **SQLSetPos**.|  
|40001|Errore di serializzazione.|La transazione viene annullata a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento delle istruzioni sconosciuto|Impossibile stabilire la connessione associata durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver non è riuscito ad allocare memoria che è necessario per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*; la funzione è stata chiamata quindi nuovamente su il *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) la chiamata di funzione precedente non è una chiamata a **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, o **SQLSetPos** in cui il codice stato SQL_NEED_DATA oppure la chiamata di funzione precedente è stata una chiamata a **SQLPutData**.<br /><br /> La chiamata di funzione precedente è stata una chiamata a **SQLParamData**.<br /><br /> (DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando il **SQLParamData** funzione è stata chiamata.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.<br /><br /> **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos** è stato chiamato per il *StatementHandle* e restituito SQL_NEED_DATA. **SQLCancel** è stato chiamato prima dei dati è stati inviati per tutti i parametri data-at-execution o più colonne.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver che corrisponde alla *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
 Se **SQLParamData** viene chiamato durante l'invio dei dati per un parametro in un'istruzione SQL, può restituire qualsiasi SQLSTATE che può essere restituite dalla funzione chiamata per eseguire l'istruzione (**SQLExecute** o **SQLExecDirect**). Se viene chiamato durante l'invio di dati per una colonna da aggiornare o aggiungere con **SQLBulkOperations** o che venga aggiornato con **SQLSetPos**, può restituire qualsiasi SQLSTATE che può essere restituiti da  **SQLBulkOperations** o **SQLSetPos**.  
  
## <a name="comments"></a>Commenti  
 **SQLParamData** può essere chiamato per fornire i dati di data-at-execution per due scopi: dati del parametro che verranno utilizzati in una chiamata a **SQLExecute** o **SQLExecDirect**, o dati della colonna che verrà utilizzato quando una riga viene aggiornata o aggiunto mediante una chiamata a **SQLBulkOperations** o aggiornati da una chiamata a **SQLSetPos**. In fase di esecuzione **SQLParamData** restituisce un valore per l'applicazione richiede il driver di un indicatore di dati.  
  
 Quando un'applicazione chiama **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, o **SQLSetPos**, il driver restituisce SQL_NEED_ DATI se necessita di dati data-at-execution. Un'applicazione chiama quindi **SQLParamData** per determinare i dati da inviare. Se il driver richiede dati del parametro, il driver restituisce il  *\*ValuePtrPtr* il valore che l'applicazione inserito nel buffer di set di righe nel buffer di output. L'applicazione può utilizzare questo valore per determinare quali dati di parametro, il driver richiede. Se il driver richiede dati della colonna, il driver restituisce il  *\*ValuePtrPtr* buffer l'indirizzo che la colonna è stata associata in origine, come indicato di seguito:  
  
 *Associare l'indirizzo* + *associazione Offset* + ((*il numero di riga* – 1) x *dimensione dell'elemento*)  
  
 le variabili in cui sono definite come indicato nella tabella seguente.  
  
|Variabile|Description|  
|--------------|-----------------|  
|*Associazione di indirizzi*|L'indirizzo specificato con il *TargetValuePtr* argomento **SQLBindCol**.|  
|*Offset di associazione*|Il valore archiviato in corrispondenza dell'indirizzo specificato con l'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR.|  
|*Numero di riga*|Il numero della riga nel set di righe in base 1. Per operazioni di recupero a riga singola, ovvero l'impostazione predefinita, questo è 1.|  
|*Dimensione dell'elemento*|Il valore dell'attributo di istruzione SQL_ATTR_ROW_BIND_TYPE per i buffer di dati e lunghezza/indicatore.|  
  
 Viene inoltre restituito SQL_NEED_DATA, che è un indicatore per l'applicazione deve chiamare **SQLPutData** per inviare i dati.  
  
 L'applicazione chiama **SQLPutData** come numero di volte necessario per inviare i dati di data-at-execution per la colonna o parametro. Dopo l'invio di tutti i dati per la colonna o parametro, l'applicazione chiama **SQLParamData** nuovamente. Se **SQLParamData** nuovamente restituisce SQL_NEED_DATA, devono essere inviati i dati per un altro parametro o una colonna. Pertanto, l'applicazione chiama **SQLPutData**. Se tutti i dati di data-at-execution è stato inviato per tutti i parametri o colonne, quindi **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, il valore in  *\*ValuePtrPtr* è definito, e può essere eseguita l'istruzione SQL o **SQLBulkOperations** o **SQLSetPos** chiamata può essere elaborata.  
  
 Se **SQLParamData** fornisce i dati di parametro per una ricerca istruzioni update o delete che non influiscono su tutte le righe nell'origine dati, la chiamata a **SQLParamData** restituisce SQL_NO_DATA.  
  
 Per ulteriori informazioni sui dati di parametro come data-at-execution viene passate in fase di esecuzione di istruzione, vedere "Passaggio di valori di parametro" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) e [l'invio di dati Long](../../../odbc/reference/develop-app/sending-long-data.md). Per ulteriori informazioni sui dati di colonna come data-at-execution sono state aggiornate o aggiunti, vedere la sezione "Utilizzo SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Esecuzione delle operazioni Bulk aggiornamenti mediante segnalibri" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), e [dati di tipo Long e SQLSetPos e SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
 **SQLParamData** può essere chiamato per recuperare i parametri di output inviati come flusso. Quando **SQLMoreResults**, **SQLExecute**, **SQLGetData**, o **SQLExecDirect** restituisce SQL_PARAM_DATA_AVAILABLE, chiamare **SQLParamData** per determinare quale parametro ha un valore disponibile. Per ulteriori informazioni su SQL_PARAM_DATA_AVAILABLE e parametri di flusso di output, vedere [il recupero dei parametri di Output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="code-example"></a>Esempio di codice  
 Vedere [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer per un parametro|[Funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Restituzione di informazioni su un parametro in un'istruzione|[Funzione SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|L'invio di dati del parametro in fase di esecuzione|[Funzione SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Recupero di parametri di output tramite SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
