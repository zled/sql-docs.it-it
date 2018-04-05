---
title: Funzione ConfigDSN | Documenti Microsoft
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
- ConfigDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDSN
helpviewer_keywords:
- ConfigDSN [ODBC]
ms.assetid: 01ced74e-c575-4a25-83f5-bd7d918123f8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b82eb128f125415d3dbdb24ffc616dbeccc5e938
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="configdsn-function"></a>Funzione ConfigDSN
**Conformità**  
 Introdotta: versione ODBC 1.0  
  
 **Riepilogo**  
 **ConfigDSN** aggiunge, modifica o Elimina le origini dati dalle informazioni di sistema. Potrebbe richiedere all'utente le informazioni di connessione. Può essere nella DLL del driver o di una DLL di installazione separato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL ConfigDSN(  
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
  
 ODBC_ADD_DSN: Aggiungere una nuova origine dati.  
  
 ODBC_CONFIG_DSN: Configurare (modifica) un'origine dati esistente.  
  
 ODBC_REMOVE_DSN: Rimuovere un'origine dati esistente.  
  
 *lpszDriver*  
 [Input] Descrizione del driver (in genere il nome del DBMS associato) presentati agli utenti anziché il nome fisico del driver.  
  
 *lpszAttributes*  
 [Input] Un elenco di attributi in forma di coppie valore-parola chiave terminazione null. Per ulteriori informazioni, vedere "Commenti".  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **ConfigDSN** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore viene inserito nel buffer di errore del programma di installazione da una chiamata a **SQLPostInstallerError** e può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwndParent* argomento non valido.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Coppie parola chiave-valore non valido|Il *lpszAttributes* argomento contiene un errore di sintassi.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszDriver* argomento non valido. Non è stato possibile trovarlo nel Registro di sistema.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *trattano* argomento non è uno dei seguenti:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*Richiesta* non riuscita|Non è stato possibile eseguire l'operazione richiesta per il *trattano* argomento.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Errore specifico del driver o funzione di conversione|Un errore specifico del driver per cui non è disponibile alcun errore di programma di installazione ODBC definita. Il *SzError* argomento in una chiamata al **SQLPostInstallerError** la funzione deve contenere il messaggio di errore specifico del driver.|  
  
## <a name="comments"></a>Commenti  
 **ConfigDSN** riceve informazioni di connessione dal programma di installazione DLL come un elenco di attributi in forma di coppie valore-parola chiave. Ogni coppia è terminato con un byte null e l'intero elenco è terminata con un byte null. (Ovvero, due byte null contrassegnano la fine dell'elenco.) Racchiudere il segno di uguale nella coppia valore-parola chiave non sono consentiti spazi. **ConfigDSN** può accettare parole chiave che non sono parole chiave valide per **SQLBrowseConnect** e **SQLDriverConnect**. **ConfigDSN** non necessariamente il supporto di tutte le parole chiave sono parole chiave valide per **SQLBrowseConnect** e **SQLDriverConnect**. (**ConfigDSN** non accetta il **DRIVER** (parola chiave).) Parole chiave utilizzate la **ConfigDSN** funzione deve supportare tutte le opzioni necessarie per ricreare l'origine dati tramite la funzionalità di installazione automatica del programma di installazione. Quando gli utilizzi del **ConfigDSN** valori e i valori di stringa di connessione sono uguali, è necessario usare le stesse parole chiave.  
  
 Come in **SQLBrowseConnect** e **SQLDriverConnect**, le parole chiave e i relativi valori non devono contenere il **[] {} (),? \*=! @** caratteri e il valore di **DSN** parola chiave non può essere costituito solo da spazi vuoti. A causa di grammatica del Registro di sistema, i nomi delle origini dati e le parole chiave non può contenere la barra rovesciata (\\) caratteri.  
  
 **ConfigDSN** deve chiamare **SQLValidDSN** per controllare la lunghezza del nome dell'origine dati e per verificare che contenga caratteri non validi vengono inclusi nel nome. Se il nome dell'origine dati è più lungo di SQL_MAX_DSN_LENGTH o include caratteri non validi, **SQLValidDSN** restituisce un errore e **ConfigDSN** restituisce un errore. Inoltre viene verificata la lunghezza del nome dell'origine dati da **SQLWriteDSNToIni**.  
  
 Per configurare un'origine dati che richiede un ID utente, password e nome del database, ad esempio, un'applicazione di installazione potrebbe passare le coppie parola chiave-valore seguente:  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 Per ulteriori informazioni sulle parole chiave, vedere [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) e la documentazione del driver ogni.  
  
 Per visualizzare una finestra di dialogo *hwndParent* non deve essere null.  
  
## <a name="adding-a-data-source"></a>Aggiunta di un'origine dati  
 Se viene passato un nome origine dati al **ConfigDSN** in *lpszAttributes*, **ConfigDSN** verifica che il nome sia valido. Se il nome dell'origine dati corrisponde a un nome origine dati esistente e *hwndParent* è null, **ConfigDSN** sovrascrive il nome esistente. Se corrisponde a un nome esistente e *hwndParent* non è null, **ConfigDSN** chiesto di sovrascrivere il nome esistente.  
  
 Se *lpszAttributes* contiene informazioni sufficienti per connettersi a un'origine dati, **ConfigDSN** possibile aggiungere l'origine dati o visualizzare una finestra di dialogo con cui l'utente può modificare le informazioni di connessione. Se *lpszAttributes* non contiene informazioni sufficienti per connettersi a un'origine dati, **ConfigDSN** necessario determinare le informazioni necessarie; se *hwndParent* non è null, Visualizza una finestra di dialogo per recuperare le informazioni da parte dell'utente.  
  
 Se **ConfigDSN** Visualizza una finestra di dialogo, è necessario visualizzare le informazioni di connessione passate nel *lpszAttributes*. In particolare, se è stato passato un nome origine dati, **ConfigDSN** consente di visualizzare il nome, ma non consente all'utente di modificarlo. **ConfigDSN** può fornire i valori predefiniti per le informazioni di connessione non passato nel *lpszAttributes*.  
  
 Se **ConfigDSN** non è possibile ottenere informazioni di connessione completa per un'origine dati, restituisce FALSE.  
  
 Se **ConfigDSN** possibile ottenere informazioni di connessione completa per un'origine dati, viene chiamato **SQLWriteDSNToIni** nel programma di installazione DLL per aggiungere la nuova specifica origine dati ODBC (i file del Registro di sistema). **SQLWriteDSNToIni** aggiunge il nome dell'origine dati alla sezione [origini dati ODBC], la sezione specifica di origine dati crea e aggiunge il **DRIVER** (parola chiave) con la descrizione del driver come relativo valore. **ConfigDSN** chiamate **SQLWritePrivateProfileString** nel programma di installazione DLL per aggiungere eventuali altre parole chiave e i valori utilizzati dal driver.  
  
## <a name="modifying-a-data-source"></a>Modifica di un'origine dati  
 Per modificare un'origine dati, un nome origine dati deve essere passato a **ConfigDSN** in *lpszAttributes*. **ConfigDSN** verifica che il nome dell'origine dati sia in ODBC (i file del Registro di sistema).  
  
 Se *hwndParent* è null, **ConfigDSN** utilizza le informazioni contenute in *lpszAttributes* per modificare le informazioni nel file Odbc.ini (o del Registro di sistema). Se *hwndParent* non è null, **ConfigDSN** Visualizza una finestra di dialogo con le informazioni contenute in *lpszAttributes*; per informazioni non in *lpszAttributes* , Usa informazioni dalle informazioni di sistema. L'utente può modificare le informazioni prima di **ConfigDSN** archivia le informazioni di sistema.  
  
 Se è stato modificato il nome dell'origine dati, **ConfigDSN** chiama innanzitutto **SQLRemoveDSNFromIni** nel programma di installazione DLL per rimuovere i dati esistenti di origine specifica dal file Odbc.ini (o del Registro di sistema). Segue quindi i passaggi nella sezione precedente per aggiungere la nuova specifica origine dati. Se il nome dell'origine dati non è stato modificato, **ConfigDSN** chiamate **SQLWritePrivateProfileString** nel programma di installazione DLL per apportare altre modifiche. **ConfigDSN** non può eliminare o modificare il valore della **Driver** (parola chiave).  
  
## <a name="deleting-a-data-source"></a>Eliminazione di un'origine dati  
 Per eliminare un'origine dati, un nome origine dati deve essere passato a **ConfigDSN** in *lpszAttributes*. **ConfigDSN** verifica che il nome dell'origine dati sia in ODBC (i file del Registro di sistema). Chiama quindi **SQLRemoveDSNFromIni** nel programma di installazione DLL per rimuovere l'origine dati.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Ottiene un valore dal file Odbc.ini o il Registro di sistema|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|Rimuovendo l'origine dati predefinito|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Rimozione di un nome origine dati da ODBC (o del Registro di sistema)|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Aggiunta di un nome di origine dati ODBC (o del Registro di sistema)|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Scrive un valore per il file Odbc.ini o il Registro di sistema|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
