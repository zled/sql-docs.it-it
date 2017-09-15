---
title: Funzione SQLPutData | Documenti Microsoft
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
- SQLPutData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPutData
helpviewer_keywords:
- SQLPutData function [ODBC]
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fac078be865e13dc2a216c8c0610d15be0b2e373
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlputdata-function"></a>SQLPutData Function
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLPutData** consente a un'applicazione inviare i dati per un parametro o una colonna per il driver in fase di esecuzione di istruzione. Questa funzione può essere utilizzata per inviare i caratteri o valori di dati binari in parti di una colonna con un tipo di dati specifici dell'origine dati, carattere o binario (ad esempio, i parametri di tipo SQL_LONGVARBINARY o SQL_LONGVARCHAR). **SQLPutData** supporta l'associazione a un tipo di dati Unicode C, anche se il driver sottostante non supporta i dati Unicode.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 [Input] Handle di istruzione.  
  
 *DataPtr*  
 [Input] Puntatore a un buffer contenente i dati effettivi per il parametro o una colonna. I dati devono essere del tipo di dati C specificato nella *ValueType* argomento di **SQLBindParameter** (per i dati di parametri) o *TargetType* argomento di ** SQLBindCol** (per i dati di colonna).  
  
 *StrLen_or_Ind*  
 [Input] Lunghezza di \* *DataPtr*. Specifica la quantità di dati inviati in una chiamata a **SQLPutData**. La quantità di dati può variare a ogni chiamata per un determinato parametro o una colonna. *StrLen_or_Ind* viene ignorato a meno che non soddisfa una delle condizioni seguenti:  
  
-   *StrLen_or_Ind* è SQL_NTS, SQL_NULL_DATA o SQL_DEFAULT_PARAM.  
  
-   Tipo di dati C specificato **SQLBindParameter** o **SQLBindCol** è SQL_C_CHAR o SQL_C_BINARY.  
  
-   Il tipo di dati C è SQL_C_DEFAULT, e il tipo di dati C predefinito per il tipo di dati SQL specificato è SQL_C_CHAR o SQL_C_BINARY.  
  
 Per tutti gli altri tipi di dati C, se *StrLen_or_Ind* non SQL_NULL_DATA o SQL_DEFAULT_PARAM, il driver presuppone che le dimensioni del \* *DataPtr* buffer è la dimensione del tipo di dati C specificato con *ValueType* o *TargetType* e invia l'intero valore dei dati. Per ulteriori informazioni, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) appendice d: tipo di dati.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLPutData** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_STMT e *gestire* di *StatementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLPutData** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Stringa o dati binari restituiti per un parametro di output ha restituito il troncamento di un carattere non vuoto o dati binari non NULL. Se si trattasse di un valore stringa, è stato troncato a destra. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|07006|Violazione dell'attributo del tipo di dati|Il valore di dati identificato dal *ValueType* argomento **SQLBindParameter** per non è possibile convertire il parametro associato al tipo di dati identificato dal *ParameterType*argomento **SQLBindParameter**.|  
|07S01|Utilizzo non valido del parametro predefinito|Impostare un valore di parametro con **SQLBindParameter**stato SQL_DEFAULT_PARAM e il parametro corrispondente non è un valore predefinito.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui era connesso il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|22001|Stringa di dati, troncamento a destra|Il troncamento di byte, non vuoto (carattere) o non null caratteri (binari) ha restituito l'assegnazione di un carattere o un valore binario a una colonna.<br /><br /> Il tipo di informazioni SQL_NEED_LONG_DATA_LEN **SQLGetInfo** è "Y", e altri dati è stati inviati per un parametro long (tipo di dati è stato SQL_LONGVARCHAR, SQL_LONGVARBINARY o un tipo di dati specifici dell'origine dati di tipo long) rispetto a quello indicato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**.<br /><br /> Il tipo di informazioni SQL_NEED_LONG_DATA_LEN **SQLGetInfo** è "Y" e altri dati è stati inviati per una colonna long (tipo di dati è stato SQL_LONGVARCHAR, SQL_LONGVARBINARY o un tipo di dati specifici dell'origine dati di tipo long) rispetto a quello indicato di buffer di lunghezza corrispondente a una colonna in una riga di dati che è stato aggiunto o aggiornati con **SQLBulkOperations** o aggiornate con **SQLSetPos**.|  
|22003|Valore numerico non compreso nell'intervallo|I dati inviati per un parametro numerico associato o colonna ha causato la parte intera (in contrapposizione frazionari) del numero da troncare quando assegnato alla colonna di tabella associati.<br /><br /> Restituisce un valore numerico (come valore numerico o stringa) per uno o più parametri di input/output o di output avrebbe causato la parte intera (in contrapposizione frazionari) del numero da troncare.|  
|22007|Formato di datetime non valido|I dati inviati per un parametro o una colonna che è stato associato a una data, ora o struttura di timestamp sono, rispettivamente, una data non valida, il tempo o timestamp.<br /><br /> Un parametro di input/output o di output è stato associato a una data, ora o struttura di timestamp C, e un valore nel parametro restituito è, rispettivamente, una data non valida, il tempo o timestamp. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|22008|Overflow del campo DateTime|Un'espressione datetime calcolata per un input/output o parametro di output ha restituito una data, ora o struttura di timestamp C che non è valido.|  
|22012|Divisione per zero|Un'espressione aritmetica calcolato per un input/output o un parametro di output ha comportato la divisione per zero.|  
|22015|Overflow del campo intervallo|I dati inviati per una colonna numerica o intervallo esatto o parametro in un tipo di dati di intervallo SQL ha causato una perdita di cifre significative.<br /><br /> Dati è stati inviati per una colonna di intervallo o un parametro con più di un campo, è stati convertiti in un tipo di dati numerici e non avevano alcuna rappresentazione nel tipo di dati numerico.<br /><br /> I dati inviati per la colonna o dati del parametro è stati assegnati a un intervallo di tipo SQL, e non vi è alcuna rappresentazione del valore di tipo C nell'intervallo di tipo SQL.<br /><br /> I dati inviati per un parametro a un tipo di intervallo C numerico esatto o colonna di intervallo C ha causato una perdita di cifre significative.<br /><br /> I dati inviati per la colonna o dati del parametro è stati assegnati a una struttura di intervallo C, ed è non stata alcuna rappresentazione dei dati nella struttura di dati di intervallo.|  
|22018|Valore di carattere non valido per la specifica del cast|Il tipo C è stato un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo SQL della colonna è un tipo di dati character; il valore della colonna o parametro non ha un valore letterale valido del tipo C associato.<br /><br /> Il tipo SQL è un numerico esatto o approssimativo, un valore datetime o un tipo di dati di intervallo. il tipo C è SQL_C_CHAR; il valore della colonna o parametro non ha un valore letterale valido del tipo SQL associato.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *StatementHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle*. Quindi la funzione è stata chiamata nuovamente sul *StatementHandle*.<br /><br /> La funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato sul *StatementHandle* da un thread diverso in un applicazioni multithread.|  
|HY009|Utilizzo non valido del puntatore null|(DM) l'argomento *DataPtr* era un puntatore null e l'argomento *StrLen_or_Ind* non è 0, SQL_DEFAULT_PARAM o SQL_NULL_DATA.|  
|HY010|Errore nella sequenza (funzione)|(DM) la chiamata di funzione precedente non è una chiamata a **SQLPutData** o **SQLParamData**.<br /><br /> (DM) a cui è stata chiamata per l'handle di connessione associata a una funzione in modo asincrono in esecuzione il *StatementHandle*. Questa funzione asincrona era ancora in esecuzione quando è stata chiamata la funzione SQLPutData.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.<br /><br /> (DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *StatementHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY019|Dati non carattere e non binari inviati in blocchi|**SQLPutData** è stato chiamato più di una volta per un parametro o una colonna, e non è stato utilizzato per inviare dati di tipo carattere C a una colonna con un tipo di carattere, binary o dati specifici dell'origine dati o per inviare i dati binari C a una colonna con un carattere , binario o il tipo di dati specifici dell'origine dati.|  
|HY020|Tentativo di concatenare un valore null|**SQLPutData** è stato chiamato più volte dopo la chiamata che ha restituito SQL_NEED_DATA in una di tali chiamate, il *StrLen_or_Ind* argomento contenuti SQL_NULL_DATA o SQL_DEFAULT_PARAM.|  
|HY090|Lunghezza di stringa o di buffer non valida|L'argomento *DataPtr* non è un puntatore null e l'argomento *StrLen_or_Ind* è minore di 0 ma non è uguale a SQL_NTS o SQL_NULL_DATA.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|Il driver (DM) associato il *StatementHandle* non supporta la funzione.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
 Se **SQLPutData** viene chiamato durante l'invio dei dati per un parametro in un'istruzione SQL, può restituire qualsiasi SQLSTATE che può essere restituite dalla funzione chiamata per eseguire l'istruzione (**SQLExecute** o **SQLExecDirect**). Se viene chiamato durante l'invio di dati per una colonna da aggiornare o aggiungere con **SQLBulkOperations** o che venga aggiornato con **SQLSetPos**, può restituire qualsiasi SQLSTATE che può essere restituiti da ** SQLBulkOperations** o **SQLSetPos**.  
  
## <a name="comments"></a>Commenti  
 **SQLPutData** può essere chiamato per fornire i dati di data-at-execution per due funzioni: dati del parametro da utilizzare in una chiamata a **SQLExecute** o **SQLExecDirect**, o i dati della colonna da utilizzare quando una riga è aggiornare o aggiungere da una chiamata a **SQLBulkOperations** o viene aggiornato da una chiamata a **SQLSetPos**.  
  
 Quando un'applicazione chiama **SQLParamData** a determinare quali dati devono inviare, il driver restituisce un indicatore che l'applicazione può utilizzare per determinare quali dati di parametro per inviare o in cui sono presenti dati della colonna. Viene inoltre restituito SQL_NEED_DATA, che è un indicatore per l'applicazione deve chiamare **SQLPutData** per inviare i dati. Nel *DataPtr* argomento **SQLPutData**, l'applicazione passa un puntatore al buffer contenente i dati effettivi per il parametro o una colonna.  
  
 Quando il driver restituisce SQL_SUCCESS per **SQLPutData**, l'applicazione chiama **SQLParamData** nuovamente. **SQLParamData** restituisce SQL_NEED_DATA se più i dati devono essere inviati, nel qual caso l'applicazione chiama **SQLPutData** nuovamente. Restituisce SQL_SUCCESS se tutti i dati di data-at-execution è stato inviato. L'applicazione chiama quindi **SQLParamData** nuovamente. Se il driver restituisce SQL_NEED_DATA e un altro indicatore in * \*ValuePtrPtr*, è necessario che i dati per un altro parametro o una colonna e **SQLPutData** viene chiamata nuovamente. Se il driver restituisce SQL_SUCCESS, quindi tutti i data-at-execution dati sono stati inviati e può essere eseguita l'istruzione SQL o **SQLBulkOperations** o **SQLSetPos** chiamata può essere elaborata.  
  
 Per ulteriori informazioni sui dati di parametro come data-at-execution viene passate in fase di esecuzione di istruzione, vedere "Passaggio di valori di parametro" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) e [l'invio di dati Long](../../../odbc/reference/develop-app/sending-long-data.md). Per ulteriori informazioni su dati di colonna come data-at-execution sono state aggiornate o aggiunti, vedere la sezione "Utilizzo SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Esecuzione delle operazioni Bulk aggiornamenti mediante segnalibri" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), e [Dati di tipo long e SQLSetPos e SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Un'applicazione può utilizzare **SQLPutData** per inviare dati in parti solo quando l'invio di dati di tipo carattere C a una colonna con un tipo di carattere, binary o dati specifici dell'origine dati o l'invio di dati C binari a una colonna con un carattere, binario, o tipo di dati specifici dell'origine. Se **SQLPutData** viene chiamato più volte in altre condizioni, restituisce SQL_ERROR e SQLSTATE HY019 (dati Non carattere e non binari inviati in blocchi).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente si presuppone un nome dell'origine dati denominato Test. Il database associato deve disporre di una tabella che è possibile creare, come indicato di seguito:  
  
```  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```  
// SQLPutData.cpp  
// compile with: odbc32.lib user32.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define TEXTSIZE  12000  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // SQLBindParameter variables.  
   SQLLEN cbTextSize, lbytes;  
  
   // SQLParamData variable.  
   PTR pParmID;  
  
   // SQLPutData variables.  
   UCHAR  Data[] =   
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyz";  
  
   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set parameters based on total data to send.  
   lbytes = (SDWORD)TEXTSIZE;  
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);  
  
   // Bind the parameter marker.  
   retcode = SQLBindParameter (hstmt1,           // hstmt  
                               1,                // ipar  
                               SQL_PARAM_INPUT,  // fParamType  
                               SQL_C_CHAR,       // fCType  
                               SQL_LONGVARCHAR,  // FSqlType  
                               lbytes,           // cbColDef  
                               0,                // ibScale  
                               (VOID *)1,        // rgbValue  
                               0,                // cbValueMax  
                               &cbTextSize);     // pcbValue  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.  
   retcode =   
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_NEED_DATA) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Check to see if NEED_DATA; if yes, use SQLPutData.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if (retcode == SQL_NEED_DATA) {  
      while (lbytes > cbBatch) {  
         SQLPutData(hstmt1, Data, cbBatch);  
         lbytes -= cbBatch;  
      }  
      // Put final batch.  
      retcode = SQLPutData(hstmt1, Data, lbytes);   
   }  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Make final SQLParamData call.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("Final SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clean up.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer per un parametro|[Funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|L'elaborazione di istruzione di annullamento|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Esecuzione di un'istruzione SQL|[Funzione SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|L'esecuzione di un'istruzione SQL preparata|[Funzione SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Restituisce il parametro successivo per l'invio di dati|[Funzione SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
