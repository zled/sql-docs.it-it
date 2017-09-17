---
title: Funzione SQLConfigDriver | Documenti Microsoft
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
- SQLConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDriver
helpviewer_keywords:
- SQLConfigDriver function [ODBC]
ms.assetid: 4f681961-ac9f-4d88-b065-5258ba112642
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9dd30a466fefda6f8b100fdd9595e9ab65e4d85f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.5  
  
 **Riepilogo**  
 **SQLConfigDriver** carica la DLL di installazione del driver appropriato e chiama il **ConfigDriver** (funzione).  
  
 La funzionalità di **SQLConfigDriver** accessibili anche con [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLConfigDriver(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszArgs,  
     LPSTR    lpszMsg,  
     WORD     cbMsgMax,  
     WORD *   pcbMsgOut);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hwndParent*  
 [Input] Handle della finestra padre. Se l'handle è null, la funzione non verrà visualizzata alcuna finestra di dialogo.  
  
 *trattano*  
 [Input] Tipo di richiesta. *trattano* deve contenere uno dei valori seguenti:  
  
 ODBC_CONFIG_DRIVER: Cambia il pool di connessioni timeout utilizzato dal driver.  
  
 ODBC_INSTALL_DRIVER: Installa un nuovo driver.  
  
 ODBC_REMOVE_DRIVER: Rimuove un driver esistente.  
  
 Questa opzione può anche essere specifici del driver, nel qual caso il *trattano* per la prima opzione è necessario iniziare da ODBC_CONFIG_DRIVER_MAX + 1. Il *trattano* per qualsiasi altra opzione deve inoltre iniziare da un valore maggiore di ODBC_CONFIG_DRIVER_MAX + 1.  
  
 *lpszDriver*  
 [Input] Il nome del driver registrato nelle informazioni di sistema.  
  
 *lpszArgs*  
 [Input] Una stringa con terminazione null che contiene gli argomenti per una specifica del driver *trattano*.  
  
 *lpszMsg*  
 [Output] Una stringa con terminazione null che contiene un messaggio di output dal programma di installazione di driver.  
  
 *cbMsgMax*  
 [Input] Lunghezza di *lpszMsg.*  
  
 *pcbMsgOut*  
 [Output] Numero totale di byte disponibili per restituire *lpszMsg*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbMsgMax*, il messaggio di output in *lpszMsg* viene troncato a *cbMsgMax* meno la terminazione null carattere. Il *pcbMsgOut* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLConfigDriver** restituisce FALSE, un oggetto associato * \*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i * \*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *lpszMsg* argomento non valido.|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwndParent* argomento non valido.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *trattano* argomento non è uno dei seguenti:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Il *trattano* argomento è un'opzione di specifica di driver che è minore o uguale a ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszDriver* argomento non valido. Non è stato possibile trovarlo nel Registro di sistema.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Coppie parola chiave-valore non valido|Il *lpszArgs* argomento contiene un errore di sintassi.|  
|ODBC_ERROR_REQUEST_FAILED|*Richiesta* non riuscita|Il programma di installazione non è in grado di eseguire l'operazione richiesta dal *trattano* argomento. La chiamata a **ConfigDriver** non riuscita.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Non è stato possibile caricare la libreria dell'installazione del driver o funzione di conversione|Impossibile caricare la libreria dell'installazione di driver.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLConfigDriver** consente a un'applicazione di chiamare un driver **ConfigDriver** routine senza dover conoscere il nome e caricare la DLL di installazione specifici del driver. Un programma di installazione chiama questa funzione dopo l'installazione di driver che DLL è stato installato. Il programma chiamante deve tenere presente che questa funzione potrebbe non essere disponibile per tutti i driver. In tal caso, il programma chiamante deve continuare senza errori.  
  
## <a name="driver-specific-options"></a>Opzioni specifiche del driver  
 Un'applicazione può richiedere funzionalità specifiche del driver esposte dal driver tramite il *trattano* argomento. Il *trattano* per la prima opzione verrà ODBC_CONFIG_DRIVER_MAX + 1, e le opzioni aggiuntive verranno incrementate di 1 da quel valore. Eventuali argomenti richiesti dal driver per tale funzione deve essere fornita in una stringa con terminazione null passati nel *lpszArgs* argomento. I driver di tale funzionalità è necessario mantenere una tabella delle opzioni specifiche del driver. Le opzioni devono essere completamente documentate nella documentazione del driver. Gli autori di applicazioni che utilizzano opzioni specifiche del driver devono essere consapevoli che questo utilizzo effettuerà l'applicazione meno interoperativa.  
  
## <a name="setting-connection-pooling-timeout"></a>L'impostazione di Timeout pool di connessioni  
 Quando si imposta la configurazione del driver, è possono impostare le proprietà di timeout pool di connessioni. **SQLConfigDriver** viene chiamato con un *trattano* di ODBC_CONFIG_DRIVER e *lpszArgs* impostato su **CPTimeout**. **CPTimeout** determina il periodo di tempo in cui una connessione può rimanere nel pool di connessioni senza essere utilizzati. Quando il timeout scade, la connessione viene chiusa e rimossa dal pool. Il timeout predefinito è 60 secondi.  
  
 Quando **SQLConfigDriver** viene chiamato con *trattano* impostata su ODBC_INSTALL_DRIVER o ODBC_REMOVE_DRIVER, gestione Driver carica la DLL di installazione del driver appropriato e chiama il ** ConfigDriver** (funzione). Quando **SQLConfigDriver** viene chiamato con un *trattano* di ODBC_CONFIG_DRIVER, tutta l'elaborazione viene eseguita nel programma di installazione ODBC, in modo che la DLL di installazione di driver non deve essere caricata.  
  
## <a name="messages"></a>Messaggi  
 Una routine di installazione di driver può inviare un messaggio di testo a un'applicazione come stringhe con terminazione null nel *lpszMsg* buffer. Il messaggio verrà troncato a *cbMsgMax* meno il carattere di terminazione null dal **ConfigDriver** funzione se è maggiore o uguale a *cbMsgMax* caratteri.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un driver|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(in DLL di installazione)|  
|Rimuovendo l'origine dati predefinito|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|
