---
title: Funzione SQLDriverConnect | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDriverConnect
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDriverConnect
helpviewer_keywords: SQLDriverConnect function [ODBC]
ms.assetid: e299be1d-5c74-4ede-b6a3-430eb189134f
caps.latest.revision: "50"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6c5eaaa0580d718ecfa3b57c2c4b0aa7da5cda41
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqldriverconnect-function"></a>SQLDriverConnect Function
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLDriverConnect** è un'alternativa a **SQLConnect**. Supporta origini dati che richiedono più informazioni di connessione di tre argomenti in **SQLConnect**, finestre di dialogo per chiedere all'utente per tutte le origini dati che non sono definite nel sistema e informazioni di connessione informazioni.  
  
 **SQLDriverConnect** fornisce gli attributi di connessione seguente:  
  
-   Stabilire una connessione utilizzando una stringa di connessione che contiene il nome dell'origine dati, uno o più ID utente, una o più password e altre informazioni richieste dall'origine dati.  
  
-   Stabilire una connessione tramite una stringa di connessione parziale o nessuna informazione aggiuntiva; In questo caso, gestione Driver e il driver può ogni prompt dei comandi all'utente le informazioni di connessione.  
  
-   Stabilire una connessione a un'origine dati che non è definita nelle informazioni di sistema. Se l'applicazione fornisce una stringa di connessione parziale, il driver può richiedere all'utente le informazioni di connessione.  
  
-   Stabilire una connessione a un'origine dati utilizzando una stringa di connessione costruita dalle informazioni contenute in un file DSN.  
  
 Dopo aver stabilita una connessione, **SQLDriverConnect** restituisce la stringa di connessione completata. L'applicazione è possibile utilizzare questa stringa per le richieste di connessione successivi. Per ulteriori informazioni, vedere [connessione con SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLDriverConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLHWND         WindowHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr,  
     SQLUSMALLINT    DriverCompletion);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *WindowHandle*  
 [Input] Handle di finestra. L'applicazione può passare l'handle della finestra padre, se applicabile, o un puntatore null se l'handle di finestra non è applicabile o **SQLDriverConnect** non presenta alcuna finestra di dialogo.  
  
 *InConnectionString*  
 [Input] Una stringa di connessione completa (vedere la sintassi "Commenti"), una stringa di connessione o una stringa vuota.  
  
 *StringLength1*  
 [Input] Lunghezza di **InConnectionString*, in caratteri, se la stringa è Unicode, o byte se stringa ANSI o DBCS.  
  
 *OutConnectionString*  
 [Output] Puntatore a un buffer per la stringa di connessione completata. Dopo la connessione all'origine dati di destinazione, questo buffer contiene la stringa di connessione completata. Le applicazioni è consigliabile allocare almeno 1024 caratteri per questo buffer.  
  
 Se *OutConnectionString* è NULL, *StringLength2Ptr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntava *OutConnectionString*.  
  
 *BufferLength*  
 [Input] Lunghezza di **OutConnectionString* buffer, in caratteri.  
  
 *StringLength2Ptr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (escluso il carattere di terminazione null) disponibile per restituire \* *OutConnectionString*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength*, completare la stringa di connessione in \* *OutConnectionString* viene troncato a  *BufferLength* meno la lunghezza di un carattere di terminazione null.  
  
 *DriverCompletion*  
 [Input] Flag che indica se il Driver Manager o il driver deve richiedere le informazioni di connessione:  
  
 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED o SQL_DRIVER_NOPROMPT.  
  
 (Per ulteriori informazioni, vedere "Commenti".)  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE o SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLDriverConnect** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *fHandleType*impostato su SQL_HANDLE_DBC e un *hHandle* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLDriverConnect** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *OutConnectionString* non sia abbastanza grande per restituire la stringa intera connessione, pertanto la stringa di connessione è stata troncata. Viene restituita la lunghezza della stringa di connessione non troncato **StringLength2Ptr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S00|Attributo di stringa di connessione non valida|È stata specificata una parola chiave di attributo non valido nella stringa di connessione (*InConnectionString*), ma il driver è stato in grado di connettersi all'origine dati comunque. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Il driver non supportava il valore specificato a cui fa riferimento il *ValuePtr* argomento **SQLSetConnectAttr** e sostituito con un valore analogo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S08|Errore durante il salvataggio di DSN su file|La stringa in  *\*InConnectionString* contenuti un **FILEDSN** (parola chiave), ma il file DSN non è stato salvato. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S09|Parola chiave non valida|(DM) la stringa in  *\*InConnectionString* contenuti un **SAVEFILE** (parola chiave), ma non un **DRIVER** o **FILEDSN** parola chiave. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08001|Impossibile stabilire la connessione client|Il driver non è riuscito a stabilire una connessione con l'origine dati.|  
|08002|Nome della connessione in uso|(DM) specificato *ConnectionHandle* fosse già utilizzato per stabilire una connessione a un'origine dati, e la connessione è stata ancora aperta.|  
|08004|Il server ha rifiutato la connessione|L'origine dati ha rifiutato la creazione di una connessione per motivi di tipo definito dall'implementazione.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui è stato effettuato un tentativo di connessione il driver non riuscita prima di **SQLDriverConnect** l'elaborazione di funzione è stata completata.|  
|28000|Specifica di autorizzazione non valido|L'identificatore utente o la stringa di autorizzazione o entrambe, come specificato nella stringa di connessione (*InConnectionString*), violazione delle restrizioni definite dall'origine dati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*szMessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY000|Errore generale: dsn su file non valido|(DM) la stringa in **InConnectionString* contenuti di una parola chiave FILEDSN, ma il nome del file DSN non è stato trovato.|  
|HY000|Errore generale: Impossibile creare il buffer di file|(DM) la stringa in **InConnectionString* contenuti di una parola chiave FILEDSN, ma il file DSN è illeggibile.|  
|HY001|Errore di allocazione della memoria|Impossibile allocare la memoria necessaria per supportare l'esecuzione o il completamento della gestione Driver il **SQLDriverConnect** (funzione).<br /><br /> Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *ConnectionHandle*. La funzione è stata chiamata e prima ha completato l'esecuzione, il [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md) è stato chiamato sul *ConnectionHandle*e quindi la **SQLDriverConnect** funzione è stata chiamata nuovamente sul *ConnectionHandle*.<br /><br /> O, **SQLDriverConnect** funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancelHandle** è stato chiamato sul *ConnectionHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) un'altra funzione di esecuzione asincrona (non **SQLDriverConnect**) è stato chiamato per il *ConnectionHandle* ed era ancora in esecuzione quando il **SQLDriverConnect** funzione è stata chiamata.|  
|HY013|Errore di gestione della memoria|Il **SQLDriverConnect** chiamata di funzione non può essere elaborata perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *StringLength1* sia minore di 0 e non è uguale a SQL_NTS.<br /><br /> (DM) il valore specificato per l'argomento *BufferLength* era minore di 0.|  
|HY092|Identificatore di attributo/opzione non valida|(DM) il *DriverCompletion* argomento è SQL_DRIVER_PROMPT e *WindowHandle* argomento è un puntatore null.|  
|HY110|Completamento del driver non valido|(DM) il valore specificato per l'argomento *DriverCompletion* non è uguale a SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED o SQL_DRIVER_NOPROMPT.<br /><br /> (DM), il pool di connessioni è stato abilitato e il valore specificato per l'argomento *DriverCompletion* non è uguale a SQL_DRIVER_NOPROMPT.|  
|HYC00|Funzionalità facoltativa non implementata.|Il driver non supporta la versione di ODBC comportamento richiesto dall'applicazione.|  
|HYT00|Timeout|Il periodo di timeout di accesso è scaduto prima della connessione all'origine dati completata. Il periodo di timeout viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver corrispondente al nome dell'origine dati specificata non supporta la funzione.|  
|IM002|Origine dati non trovato e driver predefinito non specificato|(DM) nome specificato nella stringa di connessione dell'origine dati (*InConnectionString*) non è stato trovato nelle informazioni di sistema e si è verificato alcun specifica di driver predefinita.<br /><br /> (DM) ODBC dati origine e l'impostazione predefinita le informazioni sul driver non è state trovate nelle informazioni di sistema.|  
|IM003|Impossibile caricare il driver specificato|(DM) il driver elencato nella specifica dell'origine dati nelle informazioni di sistema o specificati dal **DRIVER** parola chiave non è stato trovato o non può essere caricato per altri motivi.|  
|IM004|Driver **SQLAllocHandle** su SQL_HANDLE_ENV non riuscita|(DM) durante **SQLDriverConnect**, gestione Driver denominato il driver **SQLAllocHandle** funzione con un *fHandleType* di impostato su SQL_HANDLE_ENV e il driver ha restituito un errore.|  
|IM005|Driver **SQLAllocHandle** su SQL_HANDLE_DBC non riuscita.|(DM) durante **SQLDriverConnect**, gestione Driver denominato il driver **SQLAllocHandle** funzione con un *fHandleType* di impostato su SQL_HANDLE_DBC e il driver ha restituito un errore.|  
|IM006|Driver **SQLSetConnectAttr** non riuscita|(DM) durante **SQLDriverConnect**, gestione Driver denominato il driver **SQLSetConnectAttr** (funzione) e il driver ha restituito un errore.|  
|IM007|Nessuna origine dati o il driver specificato. finestra di dialogo non consentito|Nessun nome origine dati o il driver specificato nella stringa di connessione e *DriverCompletion* è SQL_DRIVER_NOPROMPT.|  
|IM008|Finestra di dialogo non riuscita|Il driver ha tentato di visualizzare la finestra di dialogo account di accesso e non è riuscita.<br /><br /> *WindowHandle* era un puntatore null, e *DriverCompletion* SQL_DRIVER_NO_PROMPT non è stato.|  
|IM009|Impossibile caricare la DLL di conversione|Il driver non è riuscito a caricare la DLL che è stata specificata per l'origine dati o per la connessione di traduzione.|  
|IM010|Nome dell'origine dati troppo lungo|(DM) il valore dell'attributo per la parola chiave DSN è stato più SQL_MAX_DSN_LENGTH caratteri.|  
|IM011|Nome del driver troppo lungo|Valore di attributo (DM) per il **DRIVER** parola chiave ha una lunghezza di 255 caratteri.|  
|IM012|Errore di sintassi della parola chiave DRIVER|Coppia di valore della parola chiave (DM) per il **DRIVER** (parola chiave) contiene un errore di sintassi.<br /><br /> (DM) la stringa in  *\*InConnectionString* contenuti un **FILEDSN** (parola chiave), ma il file DSN non conteneva un **DRIVER** parola chiave o un  **DSN** (parola chiave).|  
|IM014|Il DSN specificato contiene una mancata corrispondenza di architettura tra l'applicazione e il Driver|Applicazione a 32 bit (DM) utilizza un DSN la connessione a un driver a 64 bit. o viceversa.|  
|IM015|SQLDriverConnect del driver su SQL_HANDLE_DBC_INFO_HANDLE non riuscita|Se un driver restituisce SQL_ERROR, gestione Driver restituirà SQL_ERROR all'applicazione e la connessione avrà esito negativo.<br /><br /> Per ulteriori informazioni su SQL_HANDLE_DBC_INFO_TOKEN, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
|S1118|Driver non supporta la notifica asincrona|Quando il driver non supporta la notifica asincrona, è possibile impostare SQL_ATTR_ASYNC_DBC_EVENT o SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="comments"></a>Commenti  
 Una stringa di connessione presenta la sintassi seguente:  
  
 *stringa di connessione* :: = *stringa vuota*[;] &#124; *attributo*[;] &#124; *attributo*; *stringa di connessione*  
  
 *stringa vuota* :: =*attributo* :: = *parola chiave di attributo*=*attributo-valore* &#124; DRIVER = [{}]*attributo-valore*[}]  
  
 *parola chiave di attributo* :: = DSN &#124; UID &#124; PWD &#124; *-definiti-attributo-parola chiave driver*  
  
 *valore dell'attributo* :: = *stringa di caratteri*  
  
 *definiti-attributo-parola chiave driver* :: = *identificatore*  
  
 dove *stringa di caratteri* contiene zero o più caratteri; *identificatore* contiene uno o più caratteri; *parola chiave di attributo* non è tra maiuscole e minuscole; *attributo-valore* potrebbe essere tra maiuscole e minuscole; e il valore della **DSN** (parola chiave) non è costituito esclusivamente spazi vuoti.  
  
 A causa di connessione stringa e l'inizializzazione file grammatica, parole chiave e l'attributo valori che contengono i caratteri **[] {} (),? \*=! @** non racchiusi tra parentesi graffe. Il valore di **DSN** parola chiave non può essere costituito solo da spazi vuoti e non deve contenere spazi vuoti iniziali. A causa di grammatica delle informazioni di sistema, i nomi delle origini dati e le parole chiave non può contenere la barra rovesciata (\\) caratteri.  
  
 Le applicazioni non è necessario aggiungere le parentesi graffe per il valore dell'attributo dopo il **DRIVER** (parola chiave), a meno che l'attributo contiene un punto e virgola (;), nel qual caso sono necessarie le parentesi graffe. Se il valore dell'attributo che il driver riceve include parentesi graffe, il driver non necessario rimuoverli ma dovrebbero far parte della stringa di connessione restituito.  
  
 Un valore di stringa di connessione o DSN tra parentesi graffe ({}) contenente i caratteri **[] {} (),? \*=! @** passati invariati al driver. Tuttavia, quando si utilizza questi caratteri in una parola chiave, gestione Driver restituisce un errore quando si lavora con i DSN su file, ma passa la stringa di connessione per il driver per le stringhe di connessione normale. Evitare di usare parentesi graffe incorporate in un valore della parola chiave.  
  
 La stringa di connessione può includere qualsiasi numero di parole chiave definito dal driver. Poiché il **DRIVER** parola chiave non utilizza informazioni dalle informazioni di sistema, il driver deve definire sufficiente parole chiave in modo da potersi connettere a un'origine dati utilizzando solo le informazioni nella stringa di connessione. (Per ulteriori informazioni, vedere "Driver linee guida," più avanti in questa sezione). Il driver definisce le parole chiave sono necessarie per connettersi all'origine dati.  
  
 Nella tabella seguente vengono descritti i valori dell'attributo di **DSN**, **FILEDSN**, **DRIVER**, **UID**, **PWD**, e **SAVEFILE** parole chiave.  
  
|Parola chiave|Descrizione con valore attributo|  
|-------------|---------------------------------|  
|**DSN**|Nome di un'origine dati, come restituito da **SQLDataSources** o la finestra di dialogo delle origini dei dati di **SQLDriverConnect**.|  
|**FILEDSN**|Nome di un file DSN da cui verrà generata una stringa di connessione per l'origine dati. Queste origini dati vengono chiamate origini dati dei file.|  
|**DRIVER**|Descrizione del driver restituito dal **SQLDrivers** (funzione). Ad esempio, Rdb o SQL Server.|  
|**UID**|Un ID utente.|  
|**PWD**|La password corrispondente per l'ID utente o una stringa vuota se non esiste alcuna password per l'ID utente (PWD =;).|  
|**SAVEFILE**|Il nome di file di un file DSN in cui i valori di attributo di parole chiave utilizzate per effettuare la connessione ha esito positivo in caso contrario, devono essere salvati.|  
  
 Per informazioni su come un'applicazione sceglie un'origine dati o i driver, vedere [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Se le parole chiave vengono ripetute nella stringa di connessione, il driver utilizza il valore associato alla prima occorrenza della parola chiave. Se il **DSN** e **DRIVER** parole chiave sono inclusi nella stessa stringa di connessione, gestione Driver e il driver utilizza la parola chiave che viene visualizzata per prima.  
  
 Il **FILEDSN** e **DSN** parole chiave si escludono a vicenda: viene utilizzata la parola chiave che viene visualizzata per prima e quella visualizzata secondo viene ignorato. Il **FILEDSN** e **DRIVER** parole chiave, d'altra parte, non si escludono a vicenda. Se qualsiasi parola chiave viene visualizzata in una stringa di connessione con **FILEDSN**, viene utilizzato il valore dell'attributo della parola chiave nella stringa di connessione anziché il valore dell'attributo della stessa parola chiave nel file DSN.  
  
 Se il **FILEDSN** parola chiave viene utilizzata, le parole chiave specificate in un file DSN vengono utilizzate per creare una stringa di connessione. (Per ulteriori informazioni, vedere "Origini dati su File," più avanti in questa sezione). Il **UID** (parola chiave) è facoltativo; un file DSN può essere creato solo con il **DRIVER** (parola chiave). Il **PWD** parola chiave non viene archiviato in un file DSN. La directory predefinita per il salvataggio e caricamento di un file DSN sarà una combinazione del percorso specificato da **CommonFileDir** hkey_local_machine\software\microsoft\. Windows\CurrentVersion e "ODBC\DataSources". (Se CommonFileDir "C:\Program Files\Common Files", la directory predefinita sarebbe "C:\Programmi\Microsoft c:\Programmi\Common Files\ODBC\Data Sources".)  
  
> [!NOTE]  
>  Un file DSN può essere modificato chiamando direttamente il [SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md) e [SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md) funzioni nel programma di installazione DLL.  
  
 Se il **SAVEFILE** (parola chiave) viene utilizzato, i valori di attributo di parole chiave utilizzate per effettuare la connessione ha esito positivo in caso contrario, verranno salvati come un file DSN con il nome del valore dell'attributo di **SAVEFILE** parola chiave. Il **SAVEFILE** parola chiave deve essere utilizzata in combinazione con il **DRIVER** (parola chiave), il **FILEDSN** (parola chiave), o entrambi, o la funzione restituisce SQL_SUCCESS_WITH_INFO con SQLSTATE 01S09 (parola chiave non valida). Il **SAVEFILE** (parola chiave) deve precedere il **DRIVER** parola chiave nella stringa di connessione oppure i risultati saranno non definiti.  
  
## <a name="driver-manager-guidelines"></a>Linee guida di Gestione driver  
 Gestione Driver costruisce una stringa di connessione per passare al driver nel *InConnectionString* argomento del driver **SQLDriverConnect** (funzione). Gestione Driver non modifica il *InConnectionString* argomento passato dall'applicazione.  
  
 L'azione di gestione Driver è in base al valore del *DriverCompletion* argomento:  
  
-   SQL_DRIVER_PROMPT: Se la stringa di connessione non contiene il **DRIVER**, **DSN**, o **FILEDSN** (parola chiave), gestione Driver consente di visualizzare la finestra di dialogo di origini dati. Costruisce una stringa di connessione dal nome di origine di dati restituito dalla finestra di dialogo e parole chiave passati dall'applicazione. Se il nome di origine di dati restituito dalla finestra di dialogo è vuoto, gestione Driver specifica la coppia valore-parola chiave DSN = predefinito. (Questa finestra di dialogo verrà visualizzato un'origine dati con il nome "Default").  
  
-   SQL_DRIVER_COMPLETE o SQL_DRIVER_COMPLETE_REQUIRED: se la stringa di connessione specificata dall'applicazione include il **DSN** (parola chiave), gestione Driver consente di copiare la stringa di connessione specificata dall'applicazione. In caso contrario, accetta le stesse azioni a quanto accade quando *DriverCompletion* è SQL_DRIVER_PROMPT.  
  
-   SQL_DRIVER_NOPROMPT: The Driver Manager consente di copiare la stringa di connessione specificata dall'applicazione.  
  
 Se la stringa di connessione specificata dall'applicazione contiene la **DRIVER** (parola chiave), gestione Driver consente di copiare la stringa di connessione specificata dall'applicazione.  
  
 Utilizzando la stringa di connessione che è costruito, Driver Manager determina i driver da utilizzare, si connette a tale driver e passa la stringa di connessione che è costruito al driver. Per ulteriori informazioni sull'interazione di gestione Driver e il driver, vedere la sezione "Osservazioni" in [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Se la stringa di connessione non contiene il **DRIVER** (parola chiave), Driver Manager determina i driver da utilizzare come indicato di seguito:  
  
1.  Se la stringa di connessione contiene la **DSN** (parola chiave), Driver Manager recupera il driver associato all'origine dati dalle informazioni di sistema.  
  
2.  Se la stringa di connessione non contiene il **DSN** parola chiave o l'origine dati non viene trovato, il Driver Manager recupera il driver associato all'origine dati predefinito dalle informazioni di sistema. (Per ulteriori informazioni, vedere [predefinito sottochiave](../../../odbc/reference/install/default-subkey.md).) Gestione Driver cambia il valore di **DSN** parola chiave nella stringa di connessione per "DEFAULT".  
  
3.  Se il **DSN** parola chiave nella stringa di connessione è impostata su "DEFAULT", il Driver Manager recupera il driver associato all'origine dati predefinito dalle informazioni di sistema.  
  
4.  Se non è possibile trovare l'origine dati e l'origine dati predefinita non viene trovato, gestione Driver restituisce SQL_ERROR con SQLSTATE IM002 (origine dati non trovato e driver predefinito non specificato).  
  
## <a name="file-data-sources"></a>Origini dati dei file  
 Se la stringa di connessione specificato dall'applicazione nella chiamata a **SQLDriverConnect** contiene il **FILEDSN** (parola chiave) e questa parola chiave non viene sostituito da una di **DSN**o **DRIVER** (parola chiave), quindi Gestione Driver crea una stringa di connessione utilizzando le informazioni nel file DSN e *InConnectionString* argomento. Gestione Driver procede nel modo seguente:  
  
1.  Controlla se il nome del file del file DSN è valido. Se non viene restituito SQL_ERROR con SQLSTATE IM014 (nome non valido del DSN su file). Se il nome del file è una stringa vuota ("") e SQL_DRIVER_NOPROMPT, non è specificato, il **File Apri** viene visualizzata la finestra di dialogo. Se il nome del file contiene un percorso valido, ma nessun nome file o un nome di file non valido e non si specifica SQL_DRIVER_NOPROMPT, il **File Apri** viene visualizzata la finestra di dialogo con la directory corrente impostata su quello specificato nel nome del file. Se il nome del file è una stringa vuota ("") o il nome del file contiene un percorso valido, ma nessun nome file o un nome di file non valido, si specifica SQL_DRIVER_NOPROMPT, quindi viene restituito SQL_ERROR con SQLSTATE IM014 (nome non valido del DSN su file).  
  
2.  Legge tutte le parole chiave nella sezione [ODBC] del file DSN. Se il **DRIVER** (parola chiave) non è presente, restituisce SQL_ERROR con SQLSTATE IM012 (errore di sintassi della parola chiave Driver,), ad eccezione in cui il file DSN è condivisibile e pertanto contiene solo il **DSN** (parola chiave).  
  
     Se l'origine dati file condivisibile, gestione Driver legge il valore del **DSN** (parola chiave) e si connette come necessarie per l'origine dati di sistema o dell'utente a cui fa riferimento l'origine dati file condivisibile. Non vengono eseguiti i passaggi da 3 a 5.  
  
3.  Costruisce una stringa di connessione per il driver. La stringa di connessione del driver è l'unione di parole chiave specificate nel file DSN e quelle specificate nella stringa di connessione dell'applicazione originale. Regole per la costruzione della stringa di connessione del driver in cui si sovrappongono parole chiave sono le seguenti:  
  
    -   Se il **DRIVER** parola chiave esiste nella stringa di connessione di applicazione e i driver specificati da di **DRIVER** parole chiave non sono gli stessi nel file di DSN e la stringa di connessione dell'applicazione, il le informazioni sul driver nel file DSN viene ignorate e le informazioni del driver nella stringa di connessione dell'applicazione vengono utilizzate. Se il driver specificato per il **DRIVER** (parola chiave) sono gli stessi nel file di DSN e la stringa di connessione dell'applicazione, quindi in cui tutte le parole chiave si sovrappongono, quelli specificati nella stringa di connessione dell'applicazione hanno la precedenza rispetto a quelli specificato nel file DSN.  
  
    -   Nella nuova stringa di connessione, il **FILEDSN** (parola chiave) è stato eliminato.  
  
4.  Carica il driver esaminando la voce del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST.. INI\\< nome Driver\>\Driver. in \<Nome Driver > specificato da di **DRIVER** (parola chiave).  
  
5.  Passa il driver la nuova stringa di connessione.  
  
 Per esempi di file DSN, vedere [connessione utilizzando le origini dati](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md).  
  
## <a name="savefile-keyword"></a>Parola chiave SAVEFILE  
 Se la stringa di connessione specificata dall'applicazione contiene la **SAVEFILE** (parola chiave), quindi Gestione Driver Salva la stringa di connessione in un file DSN. Gestione Driver procede nel modo seguente:  
  
1.  Verifica se il nome del file del file DSN è incluso come valore dell'attributo di **SAVEFILE** (parola chiave) è valido. Se non viene restituito SQL_ERROR con SQLSTATE IM014 (nome non valido del DSN su file). La validità del nome file è determinata dalle regole di denominazione standard del sistema. Se il nome del file è una stringa vuota ("") e *DriverCompletion* argomento non è SQL_DRIVER_NOPROMPT, quindi il nome del file è valido. Se il nome del file esiste già, quindi se *DriverCompletion* è SQL_DRIVER_NOPROMPT, il file viene sovrascritto. Se *DriverCompletion* è SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE o SQL_DRIVER_COMPLETE_REQUIRED, una finestra di dialogo richiede all'utente di specificare se il file deve essere sovrascritto. Se non viene immesso il **salvataggio File** viene visualizzata la finestra di dialogo.  
  
2.  Se il driver restituisce SQL_SUCCESS e il nome del file non è una stringa vuota, il Driver Manager scrive le informazioni di connessione restituite nel *OutConnectionString* argomento nel file specificato con il formato specificato la sezione "Stringhe di connessione" più indietro in questa sezione.  
  
3.  Se il driver restituisce SQL_SUCCESS e il nome di file non è una stringa vuota (""), quindi Gestione Driver chiama il **salvataggio File** la finestra di dialogo comune con il *hwnd* specificato e scrive le informazioni di connessione restituito in *OutConnectionString* al file specificato nella finestra di dialogo comuni-Salva File con il formato specificato nella sezione "Stringhe di connessione" più indietro in questa sezione.  
  
4.  Se il driver restituisce SQL_SUCCESS, restituisce il *OutConnectionString* argomento che contiene la stringa di connessione all'applicazione.  
  
5.  Se il driver restituisce SQL_SUCCESS_WITH_INFO o SQL_ERROR, Driver Manager restituisce il valore SQLSTATE per l'applicazione.  
  
## <a name="driver-guidelines"></a>Linee guida di driver  
 Il driver controlla se la stringa di connessione passata da Gestione Driver contiene la **DSN** o **DRIVER** (parola chiave). Se la stringa di connessione contiene la **DRIVER** (parola chiave), il driver non è possibile recuperare le informazioni sull'origine dati dalle informazioni di sistema. Se la stringa di connessione contiene la **DSN** parola chiave o non contiene il **DSN** o **DRIVER** (parola chiave), il driver può recuperare informazioni sull'origine dati dalle informazioni di sistema come indicato di seguito:  
  
1.  Se la stringa di connessione contiene la **DSN** (parola chiave), il driver recupera le informazioni per l'origine dati specificata.  
  
2.  Se la stringa di connessione non contiene il **DSN** (parola chiave), l'origine dati specificata non viene trovato, o **DSN** parola chiave è impostata su "DEFAULT", il driver recupera le informazioni per l'origine dati predefinita .  
  
 Il driver utilizza le informazioni a cui che viene recuperato dalle informazioni di sistema per aumentare le informazioni passate nella stringa di connessione. Se le informazioni nelle informazioni di sistema duplica le informazioni nella stringa di connessione, il driver utilizza le informazioni nella stringa di connessione.  
  
 In base al valore di *DriverCompletion*, il driver richiede l'immissione di informazioni di connessione, ad esempio l'ID utente e password e si connette all'origine dati:  
  
-   SQL_DRIVER_PROMPT: Il driver consente di visualizzare una finestra di dialogo, utilizzando i valori dalle informazioni di sistema e di stringa di connessione (se presenti) come valori iniziali. Quando l'utente chiude la finestra di dialogo, il driver si connette all'origine dati. Costruisce una stringa di connessione dal valore della **DSN** o **DRIVER** parola chiave in \* *InConnectionString* e le informazioni restituite dal la finestra di dialogo. Inserisce la stringa di connessione nel **OutConnectionString* buffer.  
  
-   SQL_DRIVER_COMPLETE o SQL_DRIVER_COMPLETE_REQUIRED: se la stringa di connessione contiene informazioni sufficienti e le informazioni sono corrette, il driver si connette all'origine dati e le copie \* *InConnectionString*a \* *OutConnectionString*. Se tutte le informazioni mancanti o non corrette, il driver ha le stesse azioni a quanto accade quando *DriverCompletion* è SQL_DRIVER_PROMPT, tranne che se *DriverCompletion* è SQL_DRIVER_COMPLETE_ OBBLIGATORIO, il driver disattiva i controlli per tutte le informazioni non necessarie per connettersi all'origine dati.  
  
-   SQL_DRIVER_NOPROMPT: Se la stringa di connessione contiene informazioni sufficienti, il driver si connette all'origine dati e le copie \* *InConnectionString* a \* *OutConnectionString*. In caso contrario, il driver restituisce SQL_ERROR per **SQLDriverConnect**.  
  
 Per la connessione riuscita all'origine dati, il driver imposta inoltre \* *StringLength2Ptr* alla lunghezza della stringa di connessione di output che è possibile restituire in **OutConnectionString*.  
  
 Se l'utente annulla una finestra di dialogo presentata da Gestione Driver o il driver, **SQLDriverConnect** restituisce SQL_NO_DATA.  
  
 Per informazioni sull'interazione tra gestione Driver e il driver durante il processo di connessione, vedere [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Se un driver supporta **SQLDriverConnect**, la sezione della parola chiave driver delle informazioni di sistema per il driver deve contenere il **ConnectFunctions** parola chiave con il secondo carattere impostata su "Y".  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>La connessione quando il pool di connessioni è abilitato.  
 Il pool di connessioni consente a un'applicazione di riutilizzare una connessione che è già stata creata. Quando **SQLDriverConnect** viene chiamato, i tentativi di gestione Driver per stabilire la connessione utilizzando una connessione che fa parte di un pool di connessioni in un ambiente che è stato designato per il pool di connessioni. Per ulteriori informazioni sui pool di connessioni, vedere [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Un'applicazione può impostare SQL_ATTR_RESET_CONNECTION prima di chiamare SQLDisconnect su una connessione in cui il pool è attivato. Per ulteriori informazioni, vedere [funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Le restrizioni seguenti si applicano quando un'applicazione chiama **SQLDriverConnect** per connettersi a una connessione in pool:  
  
-   Nessun pool di elaborazione viene eseguita quando il **SAVEFILE** (parola chiave) viene specificato nella stringa di connessione.  
  
-   Se il pool di connessioni è abilitato, **SQLDriverConnect** può essere chiamato solo con un *DriverCompletion* argomento di SQL_DRIVER_NOPROMPT; se **SQLDriverConnect** viene chiamato con qualsiasi altro *DriverCompletion*, HY110 SQLSTATE verrà restituito (completamento driver non valido).  
  
## <a name="connection-attributes"></a>Attributi di connessione  
 L'attributo di connessione SQL_ATTR_LOGIN_TIMEOUT, impostata utilizzando **SQLSetConnectAttr**, definisce il numero di secondi di attesa per una richiesta di accesso completare con una connessione dal driver prima di restituire l'applicazione. Se l'utente verrà richiesto di completare la stringa di connessione, un periodo di attesa per ogni richiesta di accesso inizia quando il driver viene avviato il processo di connessione.  
  
 Il driver viene aperta la connessione in modalità di accesso SQL_MODE_READ_WRITE per impostazione predefinita. Per impostare la modalità di accesso su SQL_MODE_READ_ONLY, l'applicazione deve chiamare **SQLSetConnectAttr** con l'attributo SQL_ATTR_ACCESS_MODE prima di chiamare **SQLDriverConnect**.  
  
 Se una libreria di traduzione predefinita è specificata nelle informazioni di sistema per l'origine dati, il driver viene caricato. Una libreria di conversione diverse può essere caricata chiamando **SQLSetConnectAttr** con l'attributo SQL_ATTR_TRANSLATE_LIB. Un'opzione di conversione può essere specificata tramite la chiamata **SQLSetConnectAttr** con l'opzione SQL_ATTR_TRANSLATE_OPTION.  
  
 Per ulteriori informazioni, vedere [connessione con SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
```  
// SQLDriverConnect_ref.cpp  
// compile with: odbc32.lib user32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR OutConnStr[255];  
   SQLSMALLINT OutConnStrLen;  
  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            retcode = SQLDriverConnect( // SQL_NULL_HDBC  
               hdbc,   
               desktopHandle,   
               (SQLCHAR*)"driver=SQL Server",   
               _countof("driver=SQL Server"),  
               OutConnStr,  
               255,   
               &OutConnStrLen,  
               SQL_DRIVER_PROMPT );  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {                 
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 Vedere anche [programma di esempio ODBC](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Individuazione e l'enumerazione dei valori necessari per connettersi a un'origine dati|[Funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connessione a un'origine dati|[Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Disconnessione da un'origine dati|[Funzione SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Restituzione di attributi e le descrizioni di driver|[Funzione SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Liberare un handle|[Funzione SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
