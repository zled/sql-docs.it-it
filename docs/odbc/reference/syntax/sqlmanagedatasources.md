---
title: SQLManageDataSources | Documenti Microsoft
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
- SQLManageDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLManageDataSources
helpviewer_keywords:
- SQLManageDataSources [ODBC]
ms.assetid: ac6d186f-b394-406c-94c4-c6331d1ca468
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8785fef25830aa3987470a8007e115da1cc73a42
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **SQLManageDataSources** Visualizza una finestra di dialogo con cui gli utenti possono configurare, aggiungere ed eliminare origini dati nelle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HWND*  
 [Input] Handle della finestra padre.  
  
## <a name="returns"></a>Valori di codice restituiti  
 **SQLManageDataSources** restituisce FALSE se *hwnd* non è un handle di finestra valido. In caso contrario, restituisce TRUE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLManageDataSources** restituisce FALSE, un oggetto associato * \*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i * \*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_REQUEST_FAILED|*Richiesta* non riuscita|La chiamata a **ConfigDSN** non riuscita.|  
|ODBC_ERROR_INVALID__HWND|Handle di finestra non valido.|Il *hwnd* argomento non valido o NULL.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="managing-data-sources"></a>Gestione delle origini dati  
 **SQLManageDataSources** vengono inizialmente visualizzate sia la **Amministrazione origine dati ODBC** la finestra di dialogo, come illustrato nella figura seguente.  
  
 ![La finestra di dialogo Amministratore origine dati ODBC](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 Nella finestra di dialogo consente di visualizzare le origini dati elencate nelle informazioni di sistema in tre schede: **DSN utente**, **DSN di sistema**, e **DSN su File**. Se l'utente fa doppio clic su un'origine dati o seleziona un'origine dati e sceglie **configura**, **SQLManageDataSources** chiamate **ConfigDSN** nel programma di installazione DLL con il ODBC_CONFIG_ Opzione DSN.  
  
 Se l'utente fa clic **Aggiungi**, **SQLManageDataSources** consente di visualizzare il **Crea nuova origine dati** finestra di dialogo, illustrata nella figura seguente.  
  
 ![Creare la finestra di dialogo Nuova origine dati](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 Nella finestra di dialogo Visualizza un elenco di driver installati. Se l'utente fa doppio clic su un driver o seleziona un driver e fa clic su **OK**, **SQLManageDataSources** chiamate **ConfigDSN** nel programma di installazione DLL e passa l'opzione ODBC_ADD_DSN.  
  
 Se l'utente seleziona un'origine dati e sceglie **rimuovere**, **SQLManageDataSources** chiede se si desidera eliminare l'origine dati. Se l'utente fa clic **Sì**, **SQLManageDataSources** chiamate **ConfigDSN** nella DLL di installazione con l'opzione ODBC_REMOVE_DSN.  
  
 Il **Crea nuova origine dati** viene utilizzata la finestra di dialogo per aggiungere o eliminare un'origine dati utente, un'origine dati di sistema o un'origine dati file.  
  
## <a name="user-dsns"></a>DSN utente  
 I DSN creati per utenti singoli verranno chiamati DSN utente, per distinguerli dai DSN di sistema. I DSN utente vengono registrati come indicato di seguito le informazioni di sistema:  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>DSN di sistema  
 Il **Crea nuova origine dati** finestra di dialogo consente di aggiungere un'origine dati di sistema nel computer locale o eliminare uno o per impostare la configurazione per un'origine dati di sistema.  
  
 Un'origine dati configurato con un nome di origine dati (DSN) di sistema può essere utilizzata da più di un utente nello stesso computer. E può essere utilizzato anche da un servizio a livello di sistema, che può accedere all'origine dati anche se nessun utente è connesso al computer.  
  
 Un DSN di sistema viene registrato nella voce HKEY_LOCAL_MACHINE nelle informazioni di sistema anziché nella voce HKEY_CURRENT_USER. Non è associato a un utente che esegue l'accesso con il proprio nome utente e una password, ma può essere utilizzato da qualsiasi utente del computer o da un servizio automatico a livello di sistema. Il DSN di sistema è, tuttavia, associato a un computer. Non supporta la funzionalità di utilizzo remoto DSN tra computer. DSN di sistema vengono registrati come indicato di seguito le informazioni di sistema:  
  
 HKEY_LOCAL_MACHINE SOFTWARE ODBC ODBC  
  
## <a name="file-dsns"></a>DSN file  
 Un'origine dati file non dispone di un nome dell'origine dati, come non a un'origine dati macchina e non è registrato a un utente o computer. Le informazioni di connessione per l'origine dati sono contenute in un file DSN che può essere copiato in qualsiasi computer. Un'origine dati file può essere condivisibile, nel qual caso il file DSN si trova in una rete e possa essere utilizzata contemporaneamente da più utenti della rete purché l'utente abbia il driver appropriato installato. Un'origine dati file può anche essere condivisibile, nel qual caso può essere utilizzato solo in un singolo computer.  
  
 Per ulteriori informazioni sulle origini dati di file, vedere [connessione utilizzando le origini dati](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), oppure vedere [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="managing-drivers"></a>La gestione dei driver  
 Se l'utente fa clic il **driver** nella scheda il **Amministrazione origine dati ODBC** nella finestra di dialogo **SQLManageDataSources** Visualizza un elenco di driver ODBC installati nel sistema, Oltre a informazioni sui driver di. La data visualizzata è la data di creazione del driver, come illustrato nella figura seguente.  
  
 ![Scheda Amministrazione origine dati ODBC driver](../../../odbc/reference/syntax/media/ch23g.gif "ch23g")  
  
## <a name="tracing-options"></a>Opzioni di traccia  
 Se l'utente fa clic il **traccia** nella scheda il **Amministrazione origine dati ODBC** nella finestra di dialogo **SQLManageDataSources** Visualizza le opzioni di traccia, come illustrato nell'esempio seguente Figura.  
  
 ![Scheda Tracing Amministrazione origine dati ODBC](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h")  
  
 Se l'utente fa clic **Avvia ora traccia** e quindi fa clic su **OK**, **SQLManageDataSources** abilita la traccia manualmente per tutte le applicazioni in esecuzione nel computer.  
  
 Se l'utente specifica il nome di un file di traccia nel **percorso file di Log** casella di testo e quindi fa clic su **OK**, **SQLManageDataSources** imposta il **TraceFile** (parola chiave) nella sezione [ODBC] le informazioni di sistema per il nome specificato.  
  
> [!IMPORTANT]  
>  Supporto per Visual Studio Analyzer è stata rimossa a partire da Windows 8 (solo incluso Visual Studio Analyzer in versioni precedenti di Visual Studio). Per un'alternativa meccanismo di risoluzione dei problemi, utilizzare la traccia dell'offerta.  
  
 Se l'utente fa clic **avviare Visual Studio Analyzer** e quindi fa clic su **OK**, Visual Studio Analyzer è abilitata. Rimane abilitata fino **arrestare Visual Studio Analyzer** si fa clic.  
  
 Per ulteriori informazioni sulla traccia, vedere [traccia](../../../odbc/reference/develop-app/tracing.md). Per ulteriori informazioni sul **traccia** e **TraceFile** parole chiave, vedere [sottochiave ODBC](../../../odbc/reference/install/odbc-subkey.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Creazione di origini dati|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|

