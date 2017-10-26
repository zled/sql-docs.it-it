---
title: Funzione SQLInstallDriverEx | Documenti Microsoft
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
- SQLInstallDriverEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverEx
helpviewer_keywords:
- SQLInstallDriverEx function [ODBC]
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2eda9fe4e6a5f300f83512f669ad5206f89effe6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLInstallDriverEx** aggiunge informazioni sul driver per la voce Odbcinst.ini nelle informazioni di sistema e incrementa il driver *UsageCount* di 1. Tuttavia, se una versione del driver esiste già ma il *UsageCount* valore per il driver non esiste, il nuovo *UsageCount* è impostato su 2.  
  
 Questa funzione non copiare effettivamente i file. È responsabilità del programma chiamante per copiare i file del driver nella directory di destinazione in modo corretto.  
  
 La funzionalità di **SQLInstallDriverEx** accessibili anche con [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLInstallDriverEx(  
     LPCSTR    lpszDriver,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDriver*  
 [Input] Descrizione del driver (in genere il nome del DBMS associato) presentata agli utenti anziché il nome fisico del driver. Il *lpszDriver* argomento deve contenere un elenco di terminazione null di coppie valore-parola chiave che descrivono il driver. Per ulteriori informazioni sulle coppie parola chiave / valore, vedere [sottochiavi specifica del Driver](../../../odbc/reference/install/driver-specification-subkeys.md). Per ulteriori informazioni sulla stringa di terminazione null, vedere [funzione ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
 *lpszPathIn*  
 [Input] Percorso completo della directory di destinazione dell'installazione o un puntatore null. Se *lpszPathIn* è un puntatore null, il driver verranno installati nella directory di sistema.  
  
 *lpszPathOut*  
 [Output] Percorso della directory di destinazione in cui deve essere installato il driver. Se il driver non è stato precedentemente installato, *lpszPathOut* deve essere identico *lpszPathIn*. Se il driver è stato installato in precedenza, *lpszPathOut* è il percorso dell'installazione precedente.  
  
 *cbPathOutMax*  
 [Input] Lunghezza di *lpszPathOut*.  
  
 *pcbPathOut*  
 [Output] Numero totale di byte (escluso il carattere di terminazione null) disponibile per restituire *lpszPathOut*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbPathOutMax*, il percorso di output in *lpszPathOut* viene troncato a *cbPathOutMax* meno il carattere di terminazione null. Il *pcbPathOut* argomento può essere un puntatore null.  
  
 *trattano*  
 [Input] Tipo di richiesta. Il *trattano* argomento deve essere uno dei valori seguenti:  
  
 ODBC_INSTALL_INQUIRY: Richiedere informazioni su dove può essere installato un driver.  
  
 ODBC_INSTALL_COMPLETE: Completare la richiesta di installazione.  
  
 *lpdwUsageCount*  
 [Output] Il conteggio di utilizzo del driver dopo la chiamata a questa funzione.  
  
 Applicazioni non devono impostare il conteggio di utilizzo. ODBC manterrà il conteggio.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLInstallDriverEx** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *lpszPathOut* argomento non è sufficientemente grande da contenere il percorso di output. Il buffer contiene il percorso troncato.<br /><br /> Il *cbPathOutMax* argomento è 0, e *trattano* stato ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *trattano* argomento non è uno dei seguenti:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Coppie parola chiave-valore non valido|Il *lpszDriver* argomento contiene un errore di sintassi.|  
|ODBC_ERROR_INVALID_PATH|Percorso di installazione non valido.|Il *lpszPathIn* argomento contiene un percorso non valido.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Non è stato possibile caricare la libreria dell'installazione del driver o funzione di conversione|Impossibile caricare la libreria dell'installazione di driver.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Sequenza di parametri non validi|Il *lpszDriver* argomento non contiene un elenco di coppie valore-parola chiave.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossibile incrementare o decrementare il conteggio di utilizzo del componente|Il programma di installazione non riuscita incrementare il conteggio di utilizzo del driver.|  
  
## <a name="comments"></a>Commenti  
 Il *lpszDriver* argomento è un elenco di attributi in forma di coppie valore-parola chiave. Ogni coppia è terminato con un byte null e l'intero elenco è terminata con un byte null. (Ovvero, due byte null contrassegnano la fine dell'elenco.) Il formato di questo elenco è come segue:  
  
 *driver desc*  **\\** 0Driver**=***driver-DLL-filename*  **\\** 0 [installazione**=***installazione-DLL-filename***\\**0]  
  
 [*driver-attr-keyword1***=***value1***\\**0] [*driver-attr-keyword2*   **=**  *value2***\\**0]...  **\\** 0  
  
 dove \0 è un byte null e *driver-attr-keywordn* qualsiasi parola chiave attributo driver. Le parole chiave devono essere visualizzati nell'ordine specificato. Ad esempio, si supponga che un driver per i file di testo formattato dispone di driver separato e file DLL di installazione e può utilizzare un file con estensione txt e CSV. Il *lpszDriver* argomento per questo driver potrebbe essere come segue:  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 Si supponga che un driver per SQL Server non dispone di una DLL di installazione separato e non dispone delle parole chiave attributo del driver. Il *lpszDriver* argomento per questo driver potrebbe essere come segue:  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 Dopo aver **SQLInstallDriverEx** recupera informazioni sul driver dal *lpszDriver* argomento, la descrizione del driver viene aggiunto alla sezione [ODBC Driver] della voce di Odbcinst.ini nel sistema informazioni. Quindi crea una sezione con la descrizione del driver e aggiunge i percorsi completi della DLL del driver e le DLL di installazione. Infine, restituisce il percorso della directory di destinazione dell'installazione, ma non copia i file di driver a esso. Il programma chiamante deve effettivamente copiare i file dei driver nella directory di destinazione.  
  
 **SQLInstallDriverEx** incrementa il conteggio di utilizzo del componente per il driver installato 1. Se esiste già una versione del driver, ma il conteggio di utilizzo del componente per il driver non esiste, il nuovo valore di conteggio dell'utilizzo di componente è impostato su 2.  
  
 Il programma di installazione dell'applicazione è responsabile per copiare fisicamente il file del driver e il conteggio di utilizzo di file di gestione. Se il file del driver non è stato precedentemente installato, il programma di installazione dell'applicazione deve copiare il file nel *lpszPathIn* percorso e creare il conteggio di utilizzo di file. Se il file è stato installato in precedenza, il programma di installazione semplicemente incrementa il conteggio di utilizzo di file e restituisce il percorso dell'installazione precedente nel *lpszPathOut* argomento.  
  
> [!NOTE]  
>  Per ulteriori informazioni sui conteggi dell'utilizzo di componenti e i conteggi dell'utilizzo di file, vedere [il conteggio di utilizzo](../../../odbc/reference/install/usage-counting.md).  
  
 Se una versione precedente del file del driver è stata installata in precedenza dall'applicazione, il driver deve essere disinstallato e reinstallato, in modo che il conteggio di utilizzo componente driver è valido. **SQLConfigDriver** (con un *trattano* di ODBC_REMOVE_DRIVER) deve essere anzitutto chiamata e quindi **SQLRemoveDriver** deve essere chiamato per diminuire il conteggio di utilizzo del componente. **SQLInstallDriverEx** deve quindi essere chiamato per reinstallare il driver, si incrementa il conteggio di utilizzo del componente. Il programma di installazione dell'applicazione è necessario sostituire il vecchio file con il nuovo file. Il conteggio di utilizzo del file rimarrà invariato e qualsiasi altra applicazione che è utilizzato il file della versione precedente utilizzeranno la versione più recente.  
  
> [!NOTE]  
>  Se il driver è stato installato precedentemente e **SQLInstallDriverEx** viene chiamato per installare il driver in una directory diversa, la funzione restituirà TRUE, ma *lpszPathOut* includerà la directory in cui il driver è stato già installato. Non includerà la directory immessa nella *lpszDriver* argomento.  
  
 La lunghezza del percorso in *lpszPathOut* in **SQLInstallDriverEx** consente per un processo di installazione in due fasi, in modo da un'applicazione è possibile determinare quali *cbPathOutMax* , è possibile la chiamata **SQLInstallDriverEx** con un *trattano* della modalità ODBC_INSTALL_INQUIRY. Verrà restituito il numero totale di byte disponibili nel *pcbPathOut* buffer. **SQLInstallDriverEx** può quindi essere chiamato con un *trattano* di ODBC_INSTALL_COMPLETE e *cbPathOutMax* argomento impostato sul valore di *pcbPathOut*buffer più il carattere di terminazione null.  
  
 Se si sceglie di non utilizzare il modello a due fasi per **SQLInstallDriverEx**, è necessario impostare *cbPathOutMax*, che definisce le dimensioni dello spazio di archiviazione per il percorso della directory di destinazione, per il valore MAX_PATH, come definito in STDLIB. h, per impedire il troncamento.  
  
 Quando *trattano* è ODBC_INSTALL_COMPLETE, **SQLInstallDriverEx** non *lpszPathOut* su NULL (o *cbPathOutMax* da 0). Se *trattano* è ODBC_INSTALL_COMPLETE, viene restituito FALSE quando il numero di byte disponibili da restituire è maggiore o uguale a *cbPathOutMax*, con il risultato che il troncamento si verifica.  
  
 Dopo aver **SQLInstallDriverEx** è stato chiamato e il programma di installazione dell'applicazione è copiato il file del driver (se necessario), il programma di installazione di driver in cui è necessario chiamare DLL **SQLConfigDriver** per impostare la configurazione per il driver.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Installazione di Gestione driver|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|

