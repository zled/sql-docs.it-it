---
title: Funzione SQLConfigDataSource | Documenti Microsoft
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
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1d1fddaf67cfbdb8f8c8df7e66b86a681ca2e23d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdatasource-function"></a>Funzione SQLConfigDataSource
**Conformità**  
 Introdotta: versione ODBC 1.0  
  
 **Riepilogo**  
 **SQLConfigDataSource** aggiunge, modifica o Elimina le origini dati.  
  
 La funzionalità di **SQLConfigDataSource** accessibili anche con [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hwndParent*  
 [Input] Handle della finestra padre. Se l'handle è null, la funzione non verrà visualizzata alcuna finestra di dialogo.  
  
 *trattano*  
 [Input] Tipo di richiesta. Il *trattano* argomento deve essere uno dei valori seguenti:  
  
 ODBC_ADD_DSN: Aggiungere una nuova origine dati utente.  
  
 ODBC_CONFIG_DSN: Configurare (modifica) un'origine dati utente esistente.  
  
 ODBC_REMOVE_DSN: Rimuovere un'origine dati utente esistente.  
  
 ODBC_ADD_SYS_DSN: Aggiungere una nuova origine dati di sistema.  
  
 ODBC_CONFIG_SYS_DSN: Modificare un'origine dati di sistema esistente.  
  
 ODBC_REMOVE_SYS_DSN: Rimuovere un'origine dati di sistema esistente.  
  
 ODBC_REMOVE_DEFAULT_DSN: Rimuovere una sezione specifica origine dati predefinito dalle informazioni di sistema. (Rimuove inoltre la sezione specifica di driver predefinito dalla voce di Odbcinst.ini nelle informazioni di sistema. Questo *trattano* esegue la stessa funzione deprecata **SQLRemoveDefaultDataSource** (funzione).) Quando si specifica questa opzione, tutti gli altri parametri nella chiamata a **SQLConfigDataSource** devono essere valori null; se non sono NULL, essi verranno ignorati.  
  
 *lpszDriver*  
 [Input] Descrizione del driver (in genere il nome del DBMS associato) presentati agli utenti anziché il nome fisico del driver.  
  
 *lpszAttributes*  
 [Input] Un elenco di attributi in forma di coppie valore-parola chiave terminazione null. Per ulteriori informazioni, vedere [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore. Se non esiste alcuna voce nelle informazioni di sistema quando questa funzione viene chiamata, la funzione restituisce FALSE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLConfigDataSource** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwndParent* argomento non valido o NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *trattano* argomento non è uno dei seguenti:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszDriver* argomento non valido. Non è stato possibile trovarlo nel Registro di sistema.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Coppie parola chiave-valore non valido|Il *lpszAttributes* argomento contiene un errore di sintassi.|  
|ODBC_ERROR_REQUEST_FAILED|*Richiesta* non riuscita|Il programma di installazione non è in grado di eseguire l'operazione richiesta dal *trattano* argomento. La chiamata a **ConfigDSN** non riuscita.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Non è stato possibile caricare la libreria dell'installazione del driver o funzione di conversione|Impossibile caricare la libreria dell'installazione di driver.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLConfigDataSource** utilizza il valore di *lpszDriver* per leggere il percorso completo della DLL di installazione per il driver dalle informazioni di sistema. Carica la DLL e chiama **ConfigDSN** con gli stessi argomenti passati al metodo.  
  
 **SQLConfigDataSource** restituisce FALSE se non è in grado di trovare o caricare la DLL di installazione o se l'utente annulla la finestra di dialogo. In caso contrario, restituisce lo stato ricevuto da **ConfigDSN**.  
  
 **SQLConfigDataSource** esegue il mapping il DSN di sistema *trattano*s per il DSN utente *trattano*s (ODBC_ADD_SYS_DSN per ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN e ODBC_REMOVE_SYS _DSN a ODBC_REMOVE_DSN). La distinzione tra utente e DSN di sistema, **SQLConfigDataSource** imposta il programma di installazione in modalità di configurazione in base alla tabella seguente. Prima della restituzione, **SQLConfigDataSource** BOTHDSN Reimposta modalità di configurazione. **ConfigDSN** (implementata dai driver) deve chiamare **SQLWriteDSNToIni** e **SQLWritePrivateProfileString** per supportare un DSN di sistema. Per ulteriori informazioni, vedere [funzione ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*trattano*|Modalità di configurazione|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in DLL di installazione)|  
|Rimozione di un nome origine dati dalle informazioni di sistema|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Aggiunta di un nome di origine dati per le informazioni di sistema|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

