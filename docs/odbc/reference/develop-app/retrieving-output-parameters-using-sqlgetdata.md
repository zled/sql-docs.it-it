---
title: Il recupero dei parametri di Output tramite SQLGetData | Documenti Microsoft
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
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 73a76a7c78a6dc5b9cc1d3128863d7c8a0de2ff4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Il recupero dei parametri di Output tramite SQLGetData
Prima di ODBC 3.8, un'applicazione può recuperare solo i parametri di output di una query con un buffer di output associata. Tuttavia, è difficile allocare un buffer di dimensioni molto grande quando le dimensioni del valore del parametro sono molto grande (ad esempio, un'immagine di grandi dimensioni). ODBC 3.8 introduce un nuovo modo per recuperare i parametri di output in parti. Un'applicazione può chiamare **SQLGetData** con un buffer di piccole dimensioni più volte per recuperare un valore di parametro di grandi dimensioni. È simile al recupero di dati della colonna di grandi dimensioni.  
  
 Per associare un parametro di output o un parametro di input/output devono essere recuperate in parti, chiamare **SQLBindParameter** con il *InputOutputType* argomento impostato su SQL_PARAM_OUTPUT_STREAM o SQL_PARAM_INPUT_OUTPUT _STREAM. Con SQL_PARAM_INPUT_OUTPUT_STREAM, un'applicazione può utilizzare **SQLPutData** per dati di input nel parametro e quindi usare **SQLGetData** per recuperare il parametro di output. I dati di input devono essere nella data-at-execution (DAE) del modulo utilizzando **SQLPutData** anziché l'associazione a un buffer allocato precedentemente.  
  
 Questa funzionalità può essere utilizzata dalle applicazioni ODBC 3.8 o ricompilate ODBC 3. x e le applicazioni ODBC 2. x e queste applicazioni devono disporre di un driver ODBC 3.8 che supporta il recupero dei parametri di output utilizzando **SQLGetData** e il Driver ODBC 3.8 Manager. Per informazioni su come abilitare un'applicazione usare nuove funzionalità ODBC meno recente, vedere [matrice di compatibilità](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Esempio di utilizzo  
 Si consideri ad esempio l'esecuzione di una stored procedure, **{chiamata sp_f(?,?)}** , dove entrambi i parametri vengono associati come SQL_PARAM_OUTPUT_STREAM e la stored procedure non restituisce alcun set di risultati (più avanti in questo argomento sono disponibili uno scenario più complesso):  
  
1.  Per ogni parametro, chiamare **SQLBindParameter** con *InputOutputType* impostato su SQL_PARAM_OUTPUT_STREAM e *ParameterValuePtr* impostato su un token, ad esempio un numero di parametro , un puntatore ai dati o un puntatore a una struttura che l'applicazione viene utilizzato per associare i parametri di input. In questo esempio verrà utilizzato il numero ordinale del parametro come il token.  
  
2.  Eseguire la query con **SQLExecDirect** o **SQLExecute**. Verrà restituito SQL_PARAM_DATA_AVAILABLE, che indica che sono disponibili per il recupero dei parametri di flusso di output.  
  
3.  Chiamare **SQLParamData** per ottenere il parametro che è disponibile per il recupero. **SQLParamData** restituirà SQL_PARAM_DATA_AVAILABLE con il token del primo parametro disponibile, che è impostato in **SQLBindParameter** (passaggio 1). Il token viene restituito nel buffer che il *ValuePtrPtr* punta a.  
  
4.  Chiamare **SQLGetData** con l'argomento *Col*or\_*Param_Num* impostata sul parametro ordinale per recuperare i dati del primo parametro disponibile. Se **SQLGetData** restituisce SQL_SUCCESS_WITH_INFO e SQLState 01004 (dati troncati) e il tipo di lunghezza variabile nel client e server, è più dati da recuperare dal primo parametro disponibile. È possibile continuare a chiamare **SQLGetData** fino a quando non viene restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO con un altro **SQLState**.  
  
5.  Ripetere i passaggi 3 e 4 per recuperare il parametro corrente.  
  
6.  Chiamare **SQLParamData** nuovamente. Se viene restituito un valore diverso da SQL_PARAM_DATA_AVAILABLE, non è non più flussi di dati di parametro per recuperare e il codice restituito sarà il codice restituito dell'istruzione successiva che viene eseguita.  
  
7.  Chiamare **SQLMoreResults** per elaborare il set successivo di parametri fino a quando non viene restituito SQL_NO_DATA. **SQLMoreResults** restituirà SQL_NO_DATA in questo esempio, se l'attributo di istruzione SQL_ATTR_PARAMSET_SIZE è stato impostato su 1. In caso contrario, **SQLMoreResults** restituirà SQL_PARAM_DATA_AVAILABLE per indicare che sono disponibili per il set successivo di parametri per recuperare i parametri di flusso di output.  
  
 Il token è simile a un parametro di input DAE, utilizzato nell'argomento *ParameterValuePtr* in **SQLBindParameter** (passaggio 1) può essere un puntatore che punta a una struttura di dati dell'applicazione, che contiene il ordinale del parametro e informazioni specifiche dell'applicazione, se necessario.  
  
 L'ordine del flusso di output restituito o parametri di input/output è specifici del driver e potrebbe non essere sempre uguale a quello specificato nella query.  
  
 Se l'applicazione non chiama **SQLGetData** nel passaggio 4, il valore del parametro viene eliminato. Analogamente, se l'applicazione chiama **SQLParamData** prima di tutto di un parametro di valore è stato letto dal **SQLGetData**, il resto del valore viene ignorato e l'applicazione può elaborare successivo parametro.  
  
 Se l'applicazione chiama **SQLMoreResults** prima di tutto l'output inviato nel flusso di elaborazione dei parametri (**SQLParamData** comunque restituire SQL_PARAM_DATA_AVAILABLE), vengono eliminati tutti i parametri rimanenti. Analogamente, se l'applicazione chiama **SQLMoreResults** prima di tutto di un parametro di valore è stato letto dal **SQLGetData**, il resto del valore e tutti i parametri rimanenti viene rimossi e applicazione possa continuare a elaborare il successivo set di parametri.  
  
 Si noti che un'applicazione può specificare il tipo di dati C sia in **SQLBindParameter** e **SQLGetData**. Specificato con il tipo di dati C **SQLGetData** esegue l'override nel tipo di dati C specificato **SQLBindParameter**, a meno che il tipo di dati C specificato in **SQLGetData** è SQL_APD_TYPE.  
  
 Anche se un parametro di flusso di output è più utile quando il tipo di dati del parametro di output è di tipo BLOB, questa funzionalità può essere utilizzata anche con qualsiasi tipo di dati. Nel driver vengono specificati i tipi di dati supportati per i parametri di flusso di output.  
  
 Se sono presenti parametri SQL_PARAM_INPUT_OUTPUT_STREAM da elaborare, **SQLExecute** o **SQLExecDirect** verrà restituito SQL_NEED_DATA prima. Un'applicazione può chiamare **SQLParamData** e **SQLPutData** per inviare i dati del parametro DAE. Quando vengono elaborati tutti i parametri di input DAE, **SQLParamData** restituisce SQL_PARAM_DATA_AVAILABLE per indicare i parametri di flusso di output sono disponibili.  
  
 Quando vengono trasmessi parametri di output e i parametri di output associata da elaborare, il driver determina l'ordine di elaborazione dei parametri di output. Pertanto, se un parametro di output è associato a un buffer (il **SQLBindParameter** parametro *InputOutputType* è impostato su SQL_PARAM_INPUT_OUTPUT o SQL_PARAM_OUTPUT), il buffer non è possibile popolare finché  **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO. Un'applicazione deve leggere un limite del buffer solo dopo che **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO trasmesso dopo che tutti i parametri di output vengono elaborati.  
  
 L'origine dati può restituire che un avviso e il risultato impostate, in aggiunta al parametro di flusso di output. In generale, gli avvisi e i set di risultati vengono elaborati separatamente da un parametro di flusso di output chiamando **SQLMoreResults**. Gli avvisi di processo e il set prima di elaborare il parametro di output inviati come flusso di risultati.  
  
 Nella tabella seguente vengono descritti diversi scenari di un singolo comando inviato al server e in che modo usare l'applicazione.  
  
|Scenario|Valore restituito da SQLExecute o SQLExecDirect|Cosa fare successivamente|  
|--------------|---------------------------------------------------|---------------------|  
|I dati includono solo parametri di flusso di output|SQL_PARAM_DATA_AVAILABLE|Utilizzare **SQLParamData** e **SQLGetData** per recuperare i parametri di flusso di output.|  
|Dati includono un set di risultati e i parametri di output di streaming|SQL_SUCCESS|Recuperare il set di risultati con **SQLBindCol** e **SQLGetData**.<br /><br /> Chiamare **SQLMoreResults** per avviare l'elaborazione dei parametri di flusso di output. Deve restituire SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilizzare **SQLParamData** e **SQLGetData** per recuperare i parametri di flusso di output.|  
|Dati includono un messaggio di avviso e i parametri di output di streaming|SQL_SUCCESS_WITH_INFO|Utilizzare **SQLGetDiagRec** e **SQLGetDiagField** per elaborare i messaggi di avviso.<br /><br /> Chiamare **SQLMoreResults** per avviare l'elaborazione dei parametri di flusso di output. Deve restituire SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilizzare **SQLParamData** e **SQLGetData** per recuperare i parametri di flusso di output.|  
|I dati includono un messaggio di avviso, set di risultati e i parametri di output di streaming|SQL_SUCCESS_WITH_INFO|Utilizzare **SQLGetDiagRec** e **SQLGetDiagField** per elaborare i messaggi di avviso. Chiamare quindi **SQLMoreResults** per avviare l'elaborazione dei risultati impostato.<br /><br /> Recuperare un set di risultati con **SQLBindCol** e **SQLGetData**.<br /><br /> Chiamare **SQLMoreResults** per avviare l'elaborazione dei parametri di flusso di output. **SQLMoreResults** deve restituire SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilizzare **SQLParamData** e **SQLGetData** per recuperare i parametri di flusso di output.|  
|Parametro di query con parametri di input DAE, ad esempio, un flusso input/output (DAE)|NEED_DATA SQL|Chiamare **SQLParamData** e **SQLPutData** DAE di inviare i dati di parametro di input.<br /><br /> Dopo l'elaborazione di tutti i parametri di input DAE, **SQLParamData** può restituire qualsiasi codice che **SQLExecute** e **SQLExecDirect** può restituire. I case in questa tabella possono essere applicati.<br /><br /> Se il codice restituito è SQL_PARAM_DATA_AVAILABLE, sono disponibili parametri di flusso di output. Un'applicazione deve chiamare **SQLParamData** nuovamente di recuperare il token per il parametro di flusso di output, come descritto nella prima riga della tabella.<br /><br /> Se il codice restituito è SQL_SUCCESS, è un set di risultati per l'elaborazione o l'elaborazione è stata completata.<br /><br /> Se il codice restituito SQL_SUCCESS_WITH_INFO, sono disponibili per elaborare i messaggi di avviso.|  
  
 Dopo aver **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** restituisce SQL_PARAM_DATA_AVAILABLE, un errore nella sequenza funzione determinerà se un'applicazione chiama una funzione che non è presente nell'elenco seguente:  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions**  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr** / **SQLGetDescField** / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (con handle di istruzione)  
  
-   **SQLFreeStmt** (con l'opzione = SQL_CLOSE, SQL_DROP o SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (con HandleType = impostato su SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Le applicazioni possono ancora utilizzare **SQLSetDescField** o **SQLSetDescRec** per impostare le informazioni di associazione. Mapping di campo non verranno modificate. Tuttavia, i campi all'interno di descrittore potrebbero restituire nuovi valori. Ad esempio, SQL_DESC_PARAMETER_TYPE potrebbe restituire SQL_PARAM_INPUT_OUTPUT_STREAM o SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Scenario di utilizzo: Recupera un'immagine in parti da un Set di risultati  
 **SQLGetData** può essere usato per ottenere i dati in parti quando una stored procedure restituisce un set di risultati che contiene una riga di metadati su un'immagine e l'immagine viene restituito in un parametro di output di grandi dimensioni.  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Scenario di utilizzo: Inviare e ricevere un oggetto di grandi dimensioni come un parametro di Input/Output flusso  
 **SQLGetData** può essere utilizzato per ottenere e inviare i dati in parti quando una stored procedure passa un oggetto di grandi dimensioni come parametro di input/output, il valore da e verso il database di flusso. Non è necessario archiviare tutti i dati in memoria.  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri delle istruzioni](../../../odbc/reference/develop-app/statement-parameters.md)
