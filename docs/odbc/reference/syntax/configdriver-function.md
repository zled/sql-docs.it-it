---
title: Funzione ConfigDriver | Documenti Microsoft
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
- ConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDriver
helpviewer_keywords:
- ConfigDriver [ODBC]
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f83ed87bcf3dd764e6907e889bd09d844685dd7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="configdriver-function"></a>ConfigDriver (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.5  
  
 **Riepilogo**  
 **ConfigDriver** consente a un programma di installazione per eseguire l'installazione e disinstallazione funzioni senza il programma di chiamare **ConfigDSN**. Questa funzione eseguirà funzioni specifiche del driver, ad esempio la creazione di informazioni di sistema specifiche del driver e conversioni di DSN durante l'installazione, nonché pulizia delle modifiche del sistema di informazioni durante la disinstallazione. Questa funzione viene esposta la DLL di installazione del driver o di una DLL di installazione separato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL ConfigDriver(  
      HWND    hwndParent,  
      WORD    fRequest,  
      LPCSTR  lpszDriver,  
      LPCSTR  lpszArgs,  
      LPSTR   lpszMsg,  
      WORD    cbMsgMax,  
      WORD *  pcbMsgOut);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hwndParent*  
 [Input] Handle della finestra padre. Se l'handle è null, la funzione non verrà visualizzata alcuna finestra di dialogo.  
  
 *trattano*  
 [Input] Tipo di richiesta. Il *trattano* argomento deve essere uno dei valori seguenti:  
  
 ODBC_INSTALL_DRIVER: Installare un nuovo driver.  
  
 ODBC_REMOVE_DRIVER: Rimuovere un driver.  
  
 Questa opzione può anche essere specifici del driver, nel qual caso il *trattano* argomento per la prima opzione è necessario iniziare da ODBC_CONFIG_DRIVER_MAX + 1. Il *trattano* argomento per qualsiasi altra opzione deve inoltre iniziare da un valore maggiore di ODBC_CONFIG_DRIVER_MAX + 1.  
  
 *lpszDriver*  
 [Input] Il nome del driver registrati nella chiave Odbcinst.ini delle informazioni di sistema.  
  
 *lpszArgs*  
 [Input] Una stringa con terminazione null contenente gli argomenti per una specifica del driver *trattano*.  
  
 *lpszMsg*  
 [Output] Stringa con terminazione null contenente un messaggio di output dal programma di installazione di driver.  
  
 *cbMsgMax*  
 [Input] Lunghezza di *lpszMsg*.  
  
 *pcbMsgOut*  
 [Output] Numero totale di byte disponibili per restituire *lpszMsg*.  
  
 Se il numero di byte disponibili da restituire è maggiore o uguale a *cbMsgMax*, il messaggio di output in *lpszMsg* viene troncato a *cbMsgMax* meno la terminazione null carattere. Il *pcbMsgOut* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **ConfigDriver** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore viene inserito nel buffer di errore del programma di installazione da una chiamata a **SQLPostInstallerError** e può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwndParent* argomento non valido.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *trattano* argomento non è uno dei seguenti:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> L'opzione specifici del driver è inferiore o uguale a ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszDriver* argomento non valido. Non è stato possibile trovarlo nel Registro di sistema.|  
|ODBC_ERROR_REQUEST_FAILED|*Richiesta* non riuscita|Non è stato possibile eseguire l'operazione richiesta per il *trattano* argomento.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Errore specifico del driver o funzione di conversione|Un errore specifico del driver per cui non è disponibile alcun errore di programma di installazione ODBC definita. Il *SzError* argomento in una chiamata al **SQLPostInstallerError** la funzione deve contenere il messaggio di errore specifico del driver.|  
  
## <a name="comments"></a>Commenti  
  
### <a name="driver-specific-options"></a>Opzioni specifiche del driver  
 Un'applicazione può richiedere funzionalità specifiche del driver esposte dal driver tramite il *trattano* argomento. Il *trattano* per la prima opzione verrà ODBC_CONFIG_DRIVER_MAX più 1, e le opzioni aggiuntive verranno incrementate di 1 da quel valore. Eventuali argomenti richiesti dal driver per tale funzione deve essere fornita in una stringa con terminazione null passati nel *lpszArgs* argomento. I driver di tale funzionalità è necessario mantenere una tabella delle opzioni specifiche del driver. Le opzioni devono essere completamente documentate nella documentazione del driver. Gli autori di applicazioni che utilizzano opzioni specifiche del driver devono essere consapevoli che in questo modo l'applicazione meno interoperativa.  
  
### <a name="messages"></a>Messaggi  
 Una routine di installazione di driver può inviare un messaggio di testo a un'applicazione sotto forma di stringa con terminazione null nel *lpszMsg* buffer. Il messaggio verrà troncato a *cbMsgMax* meno il carattere di terminazione null dal **ConfigDriver** funzione se è maggiore o uguale a *cbMsgMax* caratteri.
