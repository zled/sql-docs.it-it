---
title: Funzione SQLCreateDataSource | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLCreateDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCreateDataSource
helpviewer_keywords:
- SQLCreateDataSource function [ODBC]
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87a5383d5580c9c6ca706e13e1fd3171713511bf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcreatedatasource-function"></a>Funzione SQLCreateDataSource
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **SQLCreateDataSource** Visualizza una finestra di dialogo in cui l'utente può aggiungere un'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HWND*  
 [Input] Handle della finestra padre.  
  
 *lpszDS*  
 [Input] Nome dell'origine dati. *lpszDS* può essere un puntatore null o una stringa vuota.  
  
## <a name="returns"></a>Valori di codice restituiti  
 **SQLCreateDataSource** restituisce TRUE se l'origine dati viene creato. In caso contrario, restituisce FALSE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLCreateDataSource** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwnd* argomento non valido o NULL.|  
|ODBC_ERROR_INVALID_DSN|DSN non valido.|Il *lpszDS* argomento contiene una stringa che non è valida per un DSN.|  
|ODBC_ERROR_REQUEST_FAILED|*Richiesta* non riuscita|La chiamata a **ConfigDSN** con l'opzione ODBC_ADD_DSN non riuscito.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Non è stato possibile caricare la libreria dell'installazione del driver o funzione di conversione|Impossibile caricare la libreria dell'installazione di driver.|  
|ODBC_ERROR_USER_CANCELED|Operazione annullata dall'utente|Creazione di una nuova origine dati annullata dall'utente.|  
|ODBC_ERROR_CREATE_DSN_FAILED|Impossibile creare il DSN richiesto|Impossibile connettersi al database. la chiamata a **SQLDriverConnect** per un DSN su File non ha restituito una connessione riuscita.<br /><br /> Impossibile scrivere nel file.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 Se *hwnd* è null, **SQLCreateDataSource** restituisce FALSE. In caso contrario, viene visualizzato il **Crea nuova origine dati** la finestra di dialogo con una pagina della procedura guidata per la scelta del tipo di origine dati per impostare, come illustrato nella figura seguente.  
  
 ![Creare la finestra di dialogo Nuova origine dati: Selezione tipo di](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 L'opzione predefinita è **origine dati File**. Quando è stata selezionata un'origine dati e **Avanti** si fa clic, viene visualizzata la pagina seguente della procedura guidata che contiene un elenco di driver installati.  
  
 ![Creare la finestra di dialogo Nuova origine dati: selezione del driver](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 Se **Annulla** si fa clic, la finestra di dialogo verrà visualizzata la e **SQLCreateDataSource** restituisce FALSE con il codice di errore di ODBC_ERROR_USER_CANCELED. Se il valore di **origine dati utente** o **origine dati di sistema** è stata selezionata l'opzione, il **avanzate** pulsante non è disponibile.  
  
 Quando il **Avanti** fa clic sul pulsante, si verificherà una delle operazioni seguenti, a seconda del tipo di dati è stata selezionata l'origine:  
  
-   Se **origine dati File** è stata selezionata, una pagina della procedura guidata viene visualizzata all'utente di immettere un nome di file.  
  
-   Se il valore **origine dati utente** o **origine dati di sistema** è stata selezionata, la visualizzazione del tipo di origine dati e i driver di una pagina della procedura guidata viene visualizzata per la revisione e quando **fine** è si fa clic, l'origine dati è impostata.  
  
 Se **avanzate** si fa clic da pagina della procedura guidata Crea nuova origine dati, viene visualizzata una pagina della procedura guidata per l'utente di immettere informazioni specifiche del driver. Nella casella di testo della finestra di dialogo, digitare il driver e parole chiave separate da restituisce, come illustrato nella figura seguente.  
  
 ![Finestra di dialogo Impostazioni per la creazione di File DSN anticipo](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 Parole chiave specifiche del driver aggiuntive sono disponibili nella descrizione di **SQLDriverConnect**. Tutti tranne **DSN** sono consentiti.  
  
 Il valore predefinito per il **verificare la connessione** opzione è impostata su TRUE. Questa impostazione si applica questa pagina della procedura guidata è attivata o meno. Se **OK** si fa clic, la stringa specificata nella casella di testo e **verificare la connessione** vengono memorizzati nella cache il valore di opzione. (Se il **Chiudi** pulsante o **Annulla** viene fatto clic su qualsiasi appena immesso informazioni specifiche del driver si interrompe perché la stringa specificata nella casella di testo e **verificare la connessione** valore dell'opzione non vengono memorizzati nella cache.)  
  
 Se **origine dati File** è stata selezionata nella prima pagina della procedura guidata, quindi dopo aver selezionato un driver e i valori di parola chiave immessa nella pagina avanzate della procedura guidata, l'utente viene richiesto di immettere un nome di file. Fare clic su **Sfoglia** per cercare un nome file, nel qual caso la directory predefinita nel **Sfoglia** casella specificata da una combinazione del percorso specificato da CommonFileDir in HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Windows\CurrentVersion e "ODBC\DataSources". (Se CommonFileDir era "C:\Program Files\Common Files", la directory predefinita sarà "C:\Programmi\Microsoft c:\Programmi\Common Files\ODBC\Data Sources".)  
  
 Quando è stato immesso un nome di file e **Avanti** si fa clic, il file di nome immesso viene verificato la validità in base alle regole standard di denominazione dei file del sistema operativo. Se il nome del file non è valido, un messaggio di errore indica all'utente che sia stato immesso un nome di file non valido. Dopo che l'utente riconosce la finestra di messaggio, viene restituito lo stato attivo per la pagina della procedura guidata in cui è stato immesso il nome del file. Se il nome del file è valido, una pagina della procedura guidata che mostra le coppie parola chiave-valore selezionata viene visualizzata per la revisione, come illustrato nella figura seguente.  
  
 ![Creare la finestra di dialogo Nuova origine dati: esaminare](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 Se **fine** si fa clic e **origine dati File** è stato selezionato come tipo di origine dati e se il **verificare questa connessione** opzione è impostata su TRUE,  **SQLDriverConnect** viene chiamato con il **SAVEFILE** e **DRIVER** parole chiave. Il *DriverCompletion* argomento è impostato su SQL_DRIVER_COMPLETE. Il nome del file per il **SAVEFILE** (parola chiave) è il nome immesso o selezionato e il nome del driver per il **DRIVER** (parola chiave) è il nome che è stato scelto. Se una stringa di connessione specifici del driver è stata specificata nella pagina avanzate della procedura guidata, tale stringa viene aggiunto dopo il **DRIVER** (parola chiave).  
  
 Se **SQLDriverConnect** restituisce SQL_SUCCESS, gestione Driver ha creato il DSN su File. **SQLCreateDataSource** restituisce TRUE. Se **SQLDriverConnect** non restituisce SQL_SUCCESS, un messaggio di avviso casella indica che non è stato possibile stabilire una connessione all'origine dati. Un DSN con informazioni di connessione minima può comunque essere creato. Questa finestra di messaggio consente all'utente di annullare o continuare con la creazione di DSN su File.  
  
 Se l'utente sceglie di continuare a creare il DSN, questo processo continua come se il **verificare questa connessione** opzione fosse impostata su FALSE. Se l'utente sceglie di annullare, viene restituito FALSE per **SQLCreateDataSource** con un codice di errore di ODBC_ERROR_CREATE_DSN_FAILED.  
  
 Se **origine dati File** è stato selezionato come tipo di origine dati e **verificare questa connessione** opzione è FALSE, viene creato un DSN su File con il **DRIVER** (parola chiave) e specificato dall'utente stringa di connessione (se presente) dalla pagina avanzate della procedura guidata. Se la creazione di file ha esito positivo, viene restituito TRUE per **SQLCreateDataSource**. Se la creazione di file non ha esito positivo, un messaggio di errore indica all'utente con qualsiasi errore restituito dal sistema operativo. Viene restituito FALSE per **SQLCreateDataSource** con un codice di errore di ODBC_ERROR_CREATE_DSN_FAILED. Per ulteriori informazioni sulle origini dati di file, vedere [connessione utilizzando le origini dati](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), oppure vedere [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Se **utente** o **origine dati di sistema** è stato selezionato come tipo di origine dati, **ConfigDSN** nel programma di installazione driver libreria viene chiamata con il ODBC_ADD_DSN  *trattano*. Per ulteriori informazioni, vedere [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Gestione delle origini dati|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|
