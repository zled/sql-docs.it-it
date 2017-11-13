---
title: Funzione SQLSetConfigMode | Documenti Microsoft
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
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8919f758c486e6569b9620fcaa7bcf76f4dac0f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLSetConfigMode** imposta la modalità di configurazione che indica la posizione nelle informazioni di sistema la voce Odbc.ini Elenco valori DSN.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Argomenti  
 *wConfigMode*  
 [Input] La modalità di configurazione del programma di installazione (vedere "Commenti"). Il valore in *wConfigMode* può essere:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetConfigMode** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Sequenza di parametri non validi|Il *wConfigMode* argomento non conteneva ODBC_USER_DSN, ODBC_SYSTEM_DSN o ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene utilizzata per impostare in cui la voce di ODBC elenco valori DSN è nelle informazioni di sistema. Se *wConfigMode* ODBC_USER_DSN, il DSN è un DSN utente e la funzione legge dalla voce di ODBC in HKEY_CURRENT_USER. Se è ODBC_SYSTEM_DSN, il DSN è un DSN di sistema e la funzione legge dalla voce di ODBC in HKEY_LOCAL_MACHINE. Se è ODBC_BOTH_DSN, viene eseguito un tentativo di HKEY_CURRENT_USER e in caso contrario, viene utilizzato HKEY_LOCAL_MACHINE.  
  
 Questa funzione non influisce sulla **SQLCreateDataSource** e **SQLDriverConnect**. La modalità di configurazione deve essere impostata durante la lettura dal Registro di sistema chiamando un driver **SQLGetPrivateProfileString** o scrive nel Registro di sistema chiamando **SQLWritePrivateProfileString**. Le chiamate a **SQLGetPrivateProfileString** e **SQLWritePrivateProfileString** per sapere quale parte del Registro di sistema su cui operare, usare la modalità di configurazione.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** deve essere chiamato solo quando necessario; se la modalità è impostata in modo non corretto, il programma di installazione di ODBC potrebbero non funzionare correttamente.  
  
 **SQLSetConfigMode** apporta una modifica diretta del Registro di sistema della modalità di configurazione. Si tratta di oltre il processo di modifica la modalità di configurazione da una chiamata a **SQLConfigDataSource**. Una chiamata a **SQLConfigDataSource** imposta la modalità di configurazione per distinguere i DSN di sistema e utente quando si modifica un DSN. Prima della restituzione, **SQLConfigDataSource** BOTHDSN Reimposta la modalità di configurazione.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Creazione di un'origine dati|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Connessione a un'origine dati tramite una connessione stringa o una finestra di dialogo|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Recuperare la modalità di configurazione|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|

