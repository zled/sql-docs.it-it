---
title: Informazioni di ODBC a 64 bit | Documenti Microsoft
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
ms.assetid: ed9851ce-44ee-4c8e-b626-1d0b52da30fe
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77449f6077adbad3eabf9ca928b2ce19b47c79b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-64-bit-information"></a>Informazioni di ODBC a 64 bit
A partire da Windows Server 2003, Microsoft sono supportati i sistemi operativi le librerie ODBC a 64 bit. Le intestazioni ODBC e librerie fornite con il SDK di MDAC 2.7 contengono le modifiche per consentire ai programmatori di scrivere facilmente il codice per nuove piattaforme a 64 bit. Assicurando che il codice vengono utilizzati i tipi ODBC definiti elencati di seguito, è possibile compilare il codice sorgente stesso sia per le piattaforme a 64 bit e a 32 bit basati sul **Win64** o **WIN32** macro.  
  
 Esistono diversi punti da tenere presenti durante la programmazione per un processore a 64 bit:  
  
-   Anche se le dimensioni di un puntatore sono modificato da 4 byte a 8 byte, numeri interi e Long sono comunque valori a 4 byte. I tipi di **INT64** e **UINT64** sono stati definiti per i valori integer a 8 byte. I nuovi tipi ODBC **SQLLEN** e **SQLULEN** sono definiti nel file di intestazione ODBC come **INT64** e **UINT64** quando **Win64**  è stato definito.  
  
-   Molte funzioni ODBC vengono dichiarate come accettare un parametro di tipo puntatore. In ODBC a 32 bit, i parametri definiti come puntatori sono stati utilizzati per passare un valore intero o un puntatore a un buffer, a seconda del contesto della chiamata. Questo stato, naturalmente, possibile che i puntatori e i numeri interi ha le stesse dimensioni. In Windows a 64 bit, questo non avviene.  
  
-   Alcune funzioni ODBC che sono state definite in precedenza con **SQLINTEGER** e **SQLUINTEGER** parametri sono stati modificati in cui è opportuno utilizzare il nuovo **SQLLEN** e  **SQLULEN** typedef. Queste modifiche sono elencate nella sezione successiva, modifiche alle dichiarazioni di funzione.  
  
-   Alcuni dei campi di descrizione che possono essere impostati tramite le varie **SQLSet** e **SQLGet** funzioni sono state modificate per adattare i valori di a 64 bit, mentre altri sono valori comunque a 32 bit. Assicurarsi di utilizzare la variabile con dimensione appropriata quando l'impostazione e recupero di questi campi. Specifiche del descrittore di quali campi sono stati modificati sono elencate sotto modifiche alle dichiarazioni di funzione.  
  
## <a name="function-declaration-changes"></a>Modifiche alle dichiarazioni di funzione  
 Le firme di funzione seguenti sono stati modificati per la programmazione a 64 bit. Gli elementi in grassetto sono parametri specifici che sono diversi.  
  
```  
SQLBindCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,  
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, SQLLEN BufferLength,   SQLLEN * StrLen_or_Ind);  
  
SQLBindParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,  
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType,   
   SQLULEN ColumnSize, SQLSMALLINT DecimalDigits,   
   SQLPOINTER ParameterValuePtr, SQLLEN *StrLen_or_Ind);  
  
SQLBindParameter (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT InputOutputType, SQLSMALLINT ValueType,   
   SQLSMALLINT ParameterType, SQLULEN ColumnSize, SQLSMALLINT DecimalDigits,   
   SQLPOINTER ParameterValuePtr, SQLLEN BufferLength, SQLLEN *StrLen_or_IndPtr);  
  
SQLColAttribute (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,  
    SQLUSMALLINT FieldIdentifier, SQLPOINTER CharacterAttributePtr,   
   SQLSMALLINT BufferLength, SQLSMALLINT * StringLengthPtr,   
   SQLLEN* NumericAttributePtr)  
  
SQLColAttributes (SQLHSTMT hstmt, SQLUSMALLINT icol,   
   SQLUSMALLINT fDescType, SQLPOINTER rgbDesc,   
   SQLSMALLINT cbDescMax, SQLSMALLINT *pcbDesc, SQLLEN * pfDesc);  
  
SQLDescribeCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,   
   SQLCHAR *ColumnName, SQLSMALLINT BufferLength,   
   SQLSMALLINT *NameLengthPtr, SQLSMALLINT *DataTypePtr, SQLULEN *ColumnSizePtr,   
   SQLSMALLINT *DecimalDigitsPtr, SQLSMALLINT *NullablePtr);  
  
SQLDescribeParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT *DataTypePtr, SQLULEN *ParameterSizePtr, SQLSMALLINT *DecimalDigitsPtr,   
   SQLSMALLINT *NullablePtr);  
  
SQLExtendedFetch(SQLHSTMT StatementHandle, SQLUSMALLINT FetchOrientation, SQLLEN FetchOffset,   
   SQLULEN * RowCountPtr, SQLUSMALLINT * RowStatusArray);  
  
SQLFetchScroll (SQLHSTMT StatementHandle, SQLSMALLINT FetchOrientation,   
   SQLLEN FetchOffset);  
  
SQLGetData (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,   
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, SQLLEN BufferLength,    SQLLEN *StrLen_or_Ind);  
  
SQLGetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber,   
   SQLCHAR *Name, SQLSMALLINT BufferLength,   
   SQLSMALLINT *StringLengthPtr, SQLSMALLINT *TypePtr,   
   SQLSMALLINT *SubTypePtr, SQLLEN *LengthPtr,   
   SQLSMALLINT *PrecisionPtr, SQLSMALLINT *ScalePtr,   
   SQLSMALLINT *NullablePtr);  
  
SQLParamOptions(SQLHSTMT hstmt, SQLULEN crow, SQLULEN * pirow);  
  
SQLPutData (SQLHSTMT StatementHandle, SQLPOINTER DataPtr,   
   SQLLEN StrLen_or_Ind);  
  
SQLRowCount (SQLHSTMT StatementHandle, SQLLEN* RowCountPtr);  
  
SQLSetConnectOption(SQLHDBC ConnectHandle, SQLUSMALLINT Option,   
   SQLULEN Value);  
  
SQLSetPos (SQLHSTMT StatementHandle, SQLSETPOSIROW RowNumber, SQLUSMALLINT Operation,  
   SQLUSMALLINT LockType);  
  
SQLSetParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType,   
   SQLULEN LengthPrecision, SQLSMALLINT ParameterScale,   
   SQLPOINTER ParameterValue, SQLLEN *StrLen_or_Ind);  
  
SQLSetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber,   
   SQLSMALLINT Type, SQLSMALLINT SubType, SQLLEN Length,   
   SQLSMALLINT Precision, SQLSMALLINT Scale, SQLPOINTER DataPtr,   
   SQLLEN *StringLengthPtr, SQLLEN *IndicatorPtr);  
  
SQLSetScrollOptions (SQLHSTMT hstmt, SQLUSMALLINT fConcurrency,   
   SQLLEN crowKeyset, SQLUSMALLINT crowRowset);  
  
SQLSetStmtOption (SQLHSTMT StatementHandle, SQLUSMALLINT Option,   
   SQLULEN Value);  
```  
  
## <a name="changes-in-sql-data-types"></a>Modifiche nei tipi di dati SQL  
 I quattro tipi SQL seguenti sono ancora supportati in 32 bit di sola lettura. non sono definiti per i compilatori a 64 bit. Questi tipi non vengono più utilizzati per qualsiasi parametro di MDAC 2.7; l'utilizzo di questi tipi causa errori del compilatore su piattaforme a 64 bit.  
  
```  
#ifdef WIN32   
typedef SQLULEN SQLROWCOUNT;   
typedef SQLULEN SQLROWSETSIZE;   
typedef SQLULEN SQLTRANSID;   
typedef SQLLEN SQLROWOFFSET;   
#endif  
```  
  
 La definizione di SQLSETPOSIROW è state modificate per i compilatori a 32 bit sia a 64 bit:  
  
```  
#ifdef _WIN64   
typedef UINT64 SQLSETPOSIROW;   
#else   
#define SQLSETPOSIROW SQLUSMALLINT   
#endif  
```  
  
 Le definizioni di SQLLEN e SQLULEN sono stati modificati per i compilatori a 64 bit:  
  
```  
#ifdef _WIN64   
typedef INT64 SQLLEN;   
typedef UINT64 SQLULEN;   
#else   
#define SQLLEN SQLINTEGER   
#define SQLULEN SQLUINTEGER   
#endif  
```  
  
 Anche se SQL_C_BOOKMARK è deprecato in ODBC 3.0, per i compilatori a 64 bit su 2.0 client, questo valore è stato modificato:  
  
```  
#ifdef _WIN64   
#define SQL_C_BOOKMARK SQL_C_UBIGINT   
#else   
#define SQL_C_BOOKMARK SQL_C_ULONG   
#endif  
```  
  
 Il tipo di SEGNALIBRO è definito in modo diverso nelle intestazioni del più recente:  
  
```  
typedef SQLULEN BOOKMARK;  
```  
  
## <a name="values-returned-from-odbc-api-calls-through-pointers"></a>Valori restituiti dalle chiamate API ODBC tramite puntatori  
 Le chiamate di funzioni ODBC seguenti accettano come parametro di input è un puntatore a un buffer in cui i dati vengono restituiti dal driver. Il contesto e il significato dei dati restituiti è determinato da altri parametri di input per le funzioni. In alcuni casi, questi metodi possono ora restituire valori a 64 bit (integer a 8 byte) anziché i valori tipici integer (4 byte) a 32 bit. Questi casi sono i seguenti:  
  
 **SQLColAttribute**  
  
 Quando il *FieldIdentifier* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **NumericAttribute*:  
  
 SQL_DESC_AUTO_UNIQUE_VALUE  
  
 SQL_DESC_CASE_SENSITIVE  
  
 SQL_DESC_CONCISE_TYPE  
  
 SQL_DESC_COUNT  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_FIXED_PREC_SCALE  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_NULLABLE  
  
 SQL_DESC_NUM_PREC_RADIX  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_SEARCHABLE  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_UNSIGNED  
  
 SQL_DESC_UPDATABLE  
  
 **SQLColAttributes**  
  
 Quando il *fDescType* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **pfDesc*:  
  
 SQL_COLUMN_COUNT  
  
 SQL_COLUMN_DISPLAY_SIZE  
  
 SQL_COLUMN_LENGTH  
  
 SQL_DESC_AUTO_UNIQUE_VALUE  
  
 SQL_DESC_CASE_SENSITIVE  
  
 SQL_DESC_CONCISE_TYPE  
  
 SQL_DESC_FIXED_PREC_SCALE  
  
 SQL_DESC_SEARCHABLE  
  
 SQL_DESC_UNSIGNED  
  
 SQL_DESC_UPDATABLE  
  
 **SQLGetConnectAttr**  
  
 Quando il *attributo* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in *valore*:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetConnectOption**  
  
 Quando il *attributo* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in *valore*:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetDescField**  
  
 Quando il *FieldIdentifier* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **ValuePtr*:  
  
 SQL_DESC_ARRAY_SIZE  
  
 SQL_DESC_ARRAY_STATUS_PTR  
  
 SQL_DESC_BIND_OFFSET_PTR  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_ROWS_PROCESSED_PTR  
  
 **SQLGetDiagField**  
  
 Quando il *DiagIdentifier* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **DiagInfoPtr*:  
  
 SQL_DIAG_CURSOR_ROW_COUNT  
  
 SQL_DIAG_ROW_COUNT  
  
 SQL_DIAG_ROW_NUMBER  
  
 **SQLGetInfo**  
  
 Quando il *InfoType* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **InfoValuePtr*:  
  
 SQL_DRIVER_HDBC  
  
 SQL_DRIVER_HENV  
  
 SQL_DRIVER_HLIB  
  
 Quando *InfoType* è uno dei seguenti 2 valori **InfoValuePtr* 64 bit su sia di input e output:  
  
 SQL_DRIVER_HDESC  
  
 SQL_DRIVER_HSTMT  
  
 **SQLGetStmtAttr**  
  
 Quando il *attributo* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **ValuePtr*:  
  
 SQL_ATTR_APP_PARAM_DESC  
  
 SQL_ATTR_APP_ROW_DESC  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_CONCURRENCY  
  
 SQL_ATTR_CURSOR_SCROLLABLE  
  
 SQL_ATTR_CURSOR_SENSITIVITY  
  
 SQL_ATTR_CURSOR_TYPE  
  
 SQL_ATTR_ENABLE_AUTO_IPD  
  
 SQL_ATTR_FETCH_BOOKMARK_PTR  
  
 SQL_ATTR_ROWS_FETCHED_PTR  
  
 SQL_ATTR_IMP_PARAM_DESC  
  
 SQL_ATTR_IMP_ROW_DESC  
  
 SQL_ATTR_KEYSET_SIZE  
  
 SQL_ATTR_MAX_LENGTH  
  
 SQL_ATTR_MAX_ROWS  
  
 SQL_ATTR_METADATA_ID  
  
 SQL_ATTR_NOSCAN  
  
 SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
 SQL_ATTR_PARAM_BIND_TYPE  
  
 SQL_ATTR_PARAM_OPERATION_PTR  
  
 SQL_ATTR_PARAM_STATUS_PTR  
  
 SQL_ATTR_PARAMS_PROCESSED_PTR  
  
 SQL_ATTR_PARAMSET_SIZE  
  
 SQL_ATTR_QUERY_TIMEOUT  
  
 SQL_ATTR_RETRIEVE_DATA  
  
 SQL_ATTR_ROW_ARRAY_SIZE  
  
 SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
 SQL_ATTR_ROW_NUMBER  
  
 SQL_ATTR_ROW_OPERATION_PTR  
  
 VENGONO IMPOSTATI SQL_ATTR_ROW_STATUS_PTR  
  
 SQL_ATTR_SIMULATE_CURSOR  
  
 SQL_ATTR_USE_BOOKMARKS  
  
 **SQLGetStmtOption**  
  
 Quando il *opzione* parametro dispone di uno dei valori seguenti, viene restituito un valore a 64 bit in **valore*:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE  
  
 **Funzione SQLSetConnectAttr**  
  
 Quando il *attributo* parametro dispone di uno dei valori seguenti, viene passato un valore a 64 bit *valore*:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetConnectOption**  
  
 Quando il *attributo* parametro dispone di uno dei valori seguenti, viene passato un valore a 64 bit *valore*:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetDescField**  
  
 Quando il *FieldIdentifier* parametro dispone di uno dei valori seguenti, viene passato un valore a 64 bit **ValuePtr*:  
  
 SQL_DESC_ARRAY_SIZE  
  
 SQL_DESC_ARRAY_STATUS_PTR  
  
 SQL_DESC_BIND_OFFSET_PTR  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_ROWS_PROCESSED_PTR  
  
 **Funzione SQLSetStmtAttr**  
  
 Quando il *attributo* parametro dispone di uno dei valori seguenti, viene passato un valore a 64 bit **ValuePtr*:  
  
 SQL_ATTR_APP_PARAM_DESC  
  
 SQL_ATTR_APP_ROW_DESC  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_CONCURRENCY  
  
 SQL_ATTR_CURSOR_SCROLLABLE  
  
 SQL_ATTR_CURSOR_SENSITIVITY  
  
 SQL_ATTR_CURSOR_TYPE  
  
 SQL_ATTR_ENABLE_AUTO_IPD  
  
 SQL_ATTR_FETCH_BOOKMARK_PTR  
  
 SQL_ATTR_IMP_PARAM_DESC  
  
 SQL_ATTR_IMP_ROW_DESC  
  
 SQL_ATTR_KEYSET_SIZE  
  
 SQL_ATTR_MAX_LENGTH  
  
 SQL_ATTR_MAX_ROWS  
  
 SQL_ATTR_METADATA_ID  
  
 SQL_ATTR_NOSCAN  
  
 SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
 SQL_ATTR_PARAM_BIND_TYPE  
  
 SQL_ATTR_PARAM_OPERATION_PTR  
  
 SQL_ATTR_PARAM_STATUS_PTR  
  
 SQL_ATTR_PARAMS_PROCESSED_PTR  
  
 SQL_ATTR_PARAMSET_SIZE  
  
 SQL_ATTR_QUERY_TIMEOUT  
  
 SQL_ATTR_RETRIEVE_DATA  
  
 SQL_ATTR_ROW_ARRAY_SIZE  
  
 SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
 SQL_ATTR_ROW_NUMBER  
  
 SQL_ATTR_ROW_OPERATION_PTR  
  
 VENGONO IMPOSTATI SQL_ATTR_ROW_STATUS_PTR  
  
 SQL_ATTR_ROWS_FETCHED_PTR  
  
 SQL_ATTR_SIMULATE_CURSOR  
  
 SQL_ATTR_USE_BOOKMARKS  
  
 **SQLSetStmtOption**  
  
 Quando il *opzione* parametro dispone di uno dei valori seguenti, viene passato un valore a 64 bit **valore*:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a ODBC](../../odbc/reference/introduction-to-odbc.md)
