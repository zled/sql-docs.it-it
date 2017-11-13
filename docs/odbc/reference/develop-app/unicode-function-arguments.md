---
title: Gli argomenti della funzione Unicode | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff461881ea10c904ceefd1c51a364984ca10971b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="unicode-function-arguments"></a>Argomenti della funzione Unicode
La gestione Driver ODBC 3.5 (o versioni successive) supporta sia ANSI e Unicode versioni di tutte le funzioni che accettano puntatori alle stringhe di caratteri o SQLPOINTER nei relativi argomenti. Le funzioni Unicode vengono implementate come funzioni (con il suffisso *W*), non come macro. Le funzioni ANSI (che può essere chiamato con o senza un suffisso di *A*) sono identiche per le funzioni API ODBC corrente.  
  
## <a name="remarks"></a>Osservazioni  
 Le funzioni Unicode che restituiscono sempre o richiedere stringhe o gli argomenti di lunghezza vengono passate come numero di caratteri. Per le funzioni che restituiscono informazioni sulla lunghezza dei dati di server, sono descritte le dimensioni di visualizzazione e la precisione in numero di caratteri. Quando una lunghezza (dimensioni di trasferimento dei dati) potrebbe fare riferimento ai dati stringa o non di tipo stringa, la lunghezza è descritto in lunghezze ottetto. Ad esempio, **SQLGetInfoW** richiederà comunque la lunghezza come numero di byte, ma **SQLExecDirectW** utilizzerà conteggio di caratteri.  
  
 Numero di caratteri si intende il numero di byte (in ottetti) per le funzioni ANSI e il numero di WCHAR (parole a 16 bit) per le funzioni UNICODE. In particolare, una sequenza di caratteri a byte doppio (DBCS) o una sequenza di caratteri multibyte (MBCS) possa essere composti da più byte. Una sequenza di caratteri UTF-16 Unicode può essere costituita da più WCHAR.  
  
 Di seguito è riportato un elenco di funzioni API ODBC che supportano versioni sia Unicode (W) e ANSI (A):  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagField**|  
|**SQLColAttribute**|**SQLGetDiagRec**|  
|**SQLColAttributes**|**SQLGetInfo**|  
|**SQLColumnPrivileges**|**SQLGetStmtAttr**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**Funzione SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**Funzione SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
  
 Di seguito è riportato un elenco di funzioni il programma di installazione ODBC e funzione di conversione ODBC che supportano versioni sia Unicode (W) e ANSI (A):  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**Funzione SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**Funzione SQLInstallDriver**||  
  
> [!NOTE]  
>  Funzioni obsolete sono di supporto di mapping Unicode-to-ANSI poiché ODBC 3*x* gestione Driver supporta la ricompilazione di ODBC 2. *x* applicazioni con UNICODE **#define**.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Applicazioni Unicode](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Driver di Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Mapping di funzione in Gestione Driver](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)

