---
title: Funzione SQLWriteDSNToIni | Documenti Microsoft
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
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 315ea45ac8f88d482f0b2cf81ed3b9d15b80a7b8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni (funzione)
**Conformità**  
 Introdotta: versione ODBC 1.0  
  
 **Riepilogo**  
 **SQLWriteDSNToIni** aggiunge un'origine dati per le informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDSN*  
 [Input] Nome dell'origine dati da aggiungere.  
  
 *lpszDriver*  
 [Input] Descrizione del driver (in genere il nome del DBMS associato) presentati agli utenti anziché il nome fisico del driver.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLWriteDSNToIni** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_DSN|DSN non valido.|Il *lpszDSN* argomento contiene una stringa che non è valida per un DSN.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszDriver* argomento non valido.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|Il programma di installazione non è stato possibile creare un DSN nel Registro di sistema.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLWriteDSNToIni** aggiunge l'origine dati alla sezione [origini dati ODBC] le informazioni di sistema. Quindi crea una sezione specifica per l'origine dati e aggiunge una singola parola chiave (**Driver**) con il nome della DLL come valore del driver. Se la sezione specifica di origine dati esiste già, **SQLWriteDSNToIni** rimuove la sezione precedente prima di creare una nuova.  
  
 Il chiamante di questa funzione è necessario aggiungere le parole chiave specifiche del driver e i valori per la sezione delle informazioni di sistema specifica all'origine dati.  
  
 Se il nome dell'origine dati è l'impostazione predefinita, **SQLWriteDSNToIni** crea anche la sezione specifica di driver predefinito nelle informazioni di sistema.  
  
 Questa funzione deve essere chiamata solo da una DLL di installazione.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(in DLL di installazione)|  
|Aggiunta, modifica o rimozione di un'origine dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Rimozione di un nome origine dati dalle informazioni di sistema|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
