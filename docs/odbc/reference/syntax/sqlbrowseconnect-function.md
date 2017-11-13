---
title: Funzione SQLBrowseConnect | Documenti Microsoft
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
- SQLBrowseConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBrowseConnect
helpviewer_keywords:
- SQLBrowseConnect function [ODBC]
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9f8117cc5238576f840cdb98f5ffaded38aed0d6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbrowseconnect-function"></a>Funzione SQLBrowseConnect
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: ODBC  
  
 **Riepilogo**  
 **SQLBrowseConnect** supporta un metodo iterativo di individuazione e l'enumerazione di attributi e valori di attributo necessari per connettersi a un'origine dati. Ogni chiamata a **SQLBrowseConnect** restituisce livelli successivi di attributi e valori di attributo. Quando tutti i livelli sono stati enumerati, una connessione all'origine dati viene completata e viene restituita una stringa di connessione completa da **SQLBrowseConnect**. Codice restituito SQL_SUCCESS o SQL_SUCCESS_WITH_INFO indica che sono state specificate tutte le informazioni di connessione e l'applicazione viene stabilita una connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLBrowseConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *InConnectionString*  
 [Input] Passare la stringa di connessione richiesta (vedere "*InConnectionString* argomento" in "Commenti").  
  
 *StringLength1*  
 [Input] Lunghezza di **InConnectionString* in caratteri.  
  
 *OutConnectionString*  
 [Output] Puntatore a un buffer di caratteri in cui si desidera restituire la stringa di connessione di risultati di ricerca (vedere "*OutConnectionString* argomento" in "Commenti").  
  
 Se *OutConnectionString* è NULL, *StringLength2Ptr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntava *OutConnectionString*.  
  
 *BufferLength*  
 [Input] La lunghezza in caratteri, del **OutConnectionString* buffer.  
  
 *StringLength2Ptr*  
 [Output] Il numero totale di caratteri (ad eccezione di terminazione null) disponibili per restituire \* *OutConnectionString*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength*, la stringa di connessione in \* *OutConnectionString* viene troncato a  *BufferLength* meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_ERROR, SQL_INVALID_HANDLE o SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLBrowseConnect** restituisce SQL_NEED_DATA, associato a un valore SQLSTATE, SQL_SUCCESS_WITH_INFO o SQL_ERROR possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* impostato su SQL_HANDLE_STMT e *Handle di ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE comunemente restituiti da **SQLBrowseConnect** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|Il buffer \* *OutConnectionString* non sia abbastanza grande per restituire la stringa di connessione del risultato Sfoglia intero, pertanto la stringa è stata troncata. Il buffer **StringLength2Ptr* contiene la lunghezza della stringa di connessione di risultato non troncato Sfoglia. (Funzione restituisce SQL_NEED_DATA).|  
|01S00|Attributo di stringa di connessione non valida|È stata specificata una parola chiave di attributo non valido nella stringa di connessione richiesta Sfoglia (*InConnectionString*). (Funzione restituisce SQL_NEED_DATA).<br /><br /> Una parola chiave di attributo è stata specificata nella stringa di connessione richiesta Sfoglia (*InConnectionString*) che non si applicano a livello di connessione corrente. (Funzione restituisce SQL_NEED_DATA).|  
|01S02|È stato modificato|Il driver non supportava il valore specificato per il *ValuePtr* argomento **SQLSetConnectAttr** e sostituito con un valore analogo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08001|Impossibile stabilire la connessione client|Il driver non è riuscito a stabilire una connessione con l'origine dati.|  
|08002|Nome della connessione in uso|(DM), la connessione specificata è già stata utilizzata per stabilire una connessione a un'origine dati e la connessione era aperta.|  
|08004|Il server ha rifiutato la connessione|L'origine dati ha rifiutato la creazione di una connessione per motivi di tipo definito dall'implementazione.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui è stato effettuato un tentativo di connessione il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|28000|Specifica di autorizzazione non valido|L'identificatore utente o la stringa di autorizzazione o entrambe, come specificato in Sfoglia richiesta una stringa di connessione (*InConnectionString*), violazione delle restrizioni definite dall'origine dati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Impossibile allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione (DM) il Driver Manager.<br /><br /> Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operazione annullata|Un'operazione asincrona è stata annullata chiamando [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md). Quindi, la funzione originale è stata chiamata nuovamente sul *ConnectionHandle*.<br /><br /> Un'operazione è stata annullata chiamando **SQLCancelHandle** sul *ConnectionHandle* da un thread diverso in un'applicazione multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *ConnectionHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *StringLength1* sia minore di 0 e non è uguale a SQL_NTS.<br /><br /> (DM) il valore specificato per l'argomento *BufferLength* era minore di 0.|  
|HY114|Driver non supporta l'esecuzione di funzione asincrona livello di connessione|(DM) l'applicazione è abilitata l'operazione asincrona nell'handle di connessione prima di effettuare la connessione. Tuttavia, il driver non supporta l'operazione asincrona su handle di connessione.|  
|HYT00|Timeout|Il periodo di timeout di accesso è scaduto prima della connessione all'origine dati completata. Il periodo di timeout viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver corrispondente al nome dell'origine dati specificata non supporta la funzione.|  
|IM002|Origine dati non trovato e driver predefinito non specificato|(DM) specificato nella stringa di connessione richiesta Sfoglia nome dell'origine dati (*InConnectionString*) non è stato trovato nelle informazioni di sistema e non era presente una specifica del driver predefinito.<br /><br /> (DM) ODBC dati origine e l'impostazione predefinita le informazioni sul driver non è state trovate nelle informazioni di sistema.|  
|IM003|Impossibile caricare il driver specificato|(DM) il driver elencato nella specifica dell'origine dati nelle informazioni di sistema o specificati dal **DRIVER** parola chiave non è stato trovato o non può essere caricato per altri motivi.|  
|IM004|Driver **SQLAllocHandle** su _ENV SQL_HANDLE non riuscita|(DM) durante **SQLBrowseConnect**, gestione Driver denominato il driver **SQLAllocHandle** funzione con un *HandleType* di impostato su SQL_HANDLE_ENV e il driver ha restituito un errore.|  
|IM005|Driver **SQLAllocHandle** su SQL_HANDLE_DBC non riuscita|(DM) durante **SQLBrowseConnect**, gestione Driver denominato il driver **SQLAllocHandle** funzione con un *HandleType* di impostato su SQL_HANDLE_DBC e il driver ha restituito un errore.|  
|IM006|Driver **SQLSetConnectAttr** non riuscita|(DM) durante **SQLBrowseConnect**, gestione Driver denominato il driver **SQLSetConnectAttr** (funzione) e il driver ha restituito un errore.|  
|IM009|Impossibile caricare la DLL di conversione|Il driver non è riuscito a caricare la DLL che è stata specificata per l'origine dati o per la connessione di traduzione.|  
|IM010|Nome dell'origine dati troppo lungo|(DM) il valore dell'attributo per la parola chiave DSN è stato più SQL_MAX_DSN_LENGTH caratteri.|  
|IM011|Nome del driver troppo lungo|(DM) il valore dell'attributo per la parola chiave DRIVER è stato più di 255 caratteri.|  
|IM012|Errore di sintassi della parola chiave DRIVER|(DM) la coppia valore-parola chiave per la parola chiave DRIVER è contenuto un errore di sintassi.|  
|IM014|Il DSN specificato contiene una mancata corrispondenza di architettura tra l'applicazione e il Driver|Applicazione a 32 bit (DM) utilizza un DSN la connessione a un driver a 64 bit. o viceversa.|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
|S1118|Driver non supporta la notifica asincrona|Quando il driver non supporta la notifica asincrona, è possibile impostare SQL_ATTR_ASYNC_DBC_EVENT o SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="inconnectionstring-argument"></a>Argomento InConnectionString  
 Una stringa di connessione richiesta Sfoglia presenta la sintassi seguente:  
  
 *stringa di connessione* :: = *attributo*[;] &#124; *attributo*; *connessione stringattribute* :: = *parola chiave di attributo*=*attributo-valore* &#124; DRIVER = [{}]*attributo-valore [*}]*parola chiave di attributo* :: = DSN &#124; UID &#124; PWD &#124; *driver--valore dell'attributo definito-keywordattribute* :: = *carattere-stringdriver-definiti-attributo-parola chiave* :: = *identificatore*  
  
 dove *stringa di caratteri* contiene zero o più caratteri; *identificatore* contiene uno o più caratteri; *parola chiave di attributo* non è tra maiuscole e minuscole; *attributo-valore* potrebbe essere tra maiuscole e minuscole; e il valore della **DSN** (parola chiave) non è costituito esclusivamente spazi vuoti. A causa di connessione stringa e l'inizializzazione file grammatica, parole chiave e l'attributo valori che contengono i caratteri **[] {} (),? \*=! @** deve essere evitato. A causa di grammatica nelle informazioni di sistema, i nomi delle origini dati e le parole chiave non può contenere la barra rovesciata (\\) caratteri. Per un database ODBC 2. *x* driver, è necessario racchiudere il valore dell'attributo per la parola chiave DRIVER tra parentesi graffe.  
  
 Se le parole chiave vengono ripetute nella stringa di connessione richiesta Sfoglia, il driver utilizza il valore associato alla prima occorrenza della parola chiave. Se il **DSN** e **DRIVER** parole chiave sono inclusi nella stessa stringa di connessione richiesta Sfoglia, il gestore dei Driver e il driver utilizza la parola chiave che viene visualizzata per prima.  
  
 Per informazioni su come un'applicazione sceglie un'origine dati o i driver, vedere [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
## <a name="outconnectionstring-argument"></a>Argomento OutConnectionString  
 La stringa di connessione di risultati di ricerca è un elenco di attributi di connessione. Un attributo di connessione è costituito da una parola chiave di attributo e un valore di attributo corrispondente. La stringa di connessione del risultato Sfoglia presenta la sintassi seguente:  
  
 *stringa di connessione* :: = *attributo*[;] &#124; *attributo*; *connessione stringattribute* :: = [\*]*parola chiave di attributo = attributo-valueattribute-parola chiave* :: = *parola chiave di attributo ODBC* &#124; *driver-defined-attribute-keywordODBC-attribute-keyword* = {UID &#124; PWD} [:*identificatore localizzata*]*-definiti-attributo-parola chiave driver* :: = *identificatore*[:*localizzata-identificatore*]*attributo-valore* :: = {*elenco di valori di attributo*} &#124;? (Le parentesi graffe sono valori letterali, vengono restituiti dal driver). *elenco di valori di attributo* :: = *stringa di caratteri* [:*stringa di caratteri localizzati*] &#124; *stringa di caratteri* [:*stringa di caratteri localizzati*], *elenco di valori di attributo*  
  
 dove *stringa di caratteri* e *stringa di caratteri localizzati* avere zero o più caratteri; *identificatore* e *identificatore localizzata* dispone di uno o più caratteri; *parola chiave di attributo* non è tra maiuscole e minuscole; e *attributo-valore* potrebbe essere tra maiuscole e minuscole. A causa di connessione file grammatica, parole chiave, gli identificatori localizzati, stringa e l'inizializzazione e i valori che contengono i caratteri di attributo **[] {} (),? \*=! @** deve essere evitato. A causa di grammatica nelle informazioni di sistema, i nomi delle origini dati e le parole chiave non può contenere la barra rovesciata (\\) caratteri.  
  
 La sintassi della stringa di connessione risultato Sfoglia viene utilizzato secondo le regole semantiche seguenti:  
  
-   Se un asterisco (\*) precede un *parola chiave di attributo*, *attributo* è facoltativo e può essere omesso nella chiamata successiva a **SQLBrowseConnect**.  
  
-   Le parole chiave di attributo **UID** e **PWD** hanno lo stesso significato, come definito in **SQLDriverConnect**.  
  
-   Oggetto *-definiti-attributo-parola chiave driver* i nomi del tipo di attributo per cui può essere specificato un valore di attributo. Ad esempio, potrebbe essere **SERVER**, **DATABASE**, **HOST**, o **DBMS**.  
  
-   *Parole chiave di attributo ODBC* e *driver--attributo-parole chiave definite dal* include una versione localizzata o intuitiva della parola chiave. Questo potrebbe essere utilizzato da applicazioni come un'etichetta in una finestra di dialogo. Tuttavia, **UID**, **PWD**, o *identificatore* autonoma deve essere utilizzato quando si passa una stringa di richiesta di ricerca per il driver.  
  
-   Il {*elenco di valori di attributo*} è un'enumerazione dei valori effettivi valido per il corrispondente *parola chiave di attributo*. Si noti che le parentesi graffe ({}) non indicano un elenco di scelte; vengono restituiti dal driver. Ad esempio, potrebbe essere un elenco di nomi di server o un elenco di nomi di database.  
  
-   Se il *attributo-valore* è un singolo punto interrogativo (?), un singolo valore corrisponde alla *parola chiave di attributo*. Ad esempio UID = JohnS; PWD = pieno.  
  
-   Ogni chiamata a **SQLBrowseConnect** restituisce solo le informazioni necessarie per soddisfare il livello successivo del processo di connessione. Il driver associa informazioni sullo stato dell'handle di connessione in modo che il contesto può essere determinato sempre per ogni chiamata.  
  
## <a name="using-sqlbrowseconnect"></a>Utilizzando SQLBrowseConnect  
 **SQLBrowseConnect** richiede una connessione allocata. Gestione Driver viene caricato il driver che è stato specificato o che corrisponde al nome dell'origine dati specificato nella stringa di connessione richiesta iniziale Sfoglia; Per informazioni su quando ciò si verifica, vedere la sezione "Osservazioni" in [funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Il driver può stabilire una connessione con l'origine dati durante il processo di esplorazione. Se **SQLBrowseConnect** restituisce SQL_ERROR, in attesa di connessioni vengono terminate e viene restituita la connessione a uno stato non è connesso.  
  
> [!NOTE]  
>  **SQLBrowseConnect** non supporta il pool di connessioni. Se **SQLBrowseConnect** viene chiamato quando il pool di connessioni è abilitato, SQLSTATE HY000 (errore generale) verrà restituiti.  
  
 Quando **SQLBrowseConnect** viene chiamato per la prima volta in una connessione, deve contenere la stringa di connessione richiesta Sfoglia il **DSN** parola chiave o **DRIVER** (parola chiave). Se la stringa di connessione richiesta Sfoglia contiene il **DSN** (parola chiave), gestione Driver individua una specifica origine dati corrispondente nelle informazioni di sistema:  
  
-   Se il Driver Manager rileva specifica dell'origine dati corrispondente, viene caricato il driver associato DLL. il driver può recuperare informazioni sull'origine dati dalle informazioni di sistema.  
  
-   Se Gestione Driver non è possibile trovare specifica dell'origine dati corrispondente, individua specifica dell'origine dati predefinito e carica il driver associato DLL. il driver può recuperare informazioni sull'origine dati predefinito dalle informazioni di sistema. "DEFAULT" viene passato al driver per il DSN.  
  
-   Se Gestione Driver non è possibile trovare specifica dell'origine dati corrispondente e non esiste alcuna specifica di origine dati predefinita, viene restituito SQL_ERROR con SQLSTATE IM002 (origine dati non trovato e driver predefinito non specificato).  
  
 Se la stringa di connessione richiesta Sfoglia contiene il **DRIVER** (parola chiave), gestione Driver viene caricato il driver specificato; non tenta di individuare un'origine dati nelle informazioni di sistema. Poiché il **DRIVER** parola chiave non utilizza informazioni dalle informazioni di sistema, il driver deve definire sufficiente parole chiave in modo da potersi connettere a un'origine dati utilizzando solo le informazioni nelle stringhe di connessione richiesta Sfoglia.  
  
 In ogni chiamata a **SQLBrowseConnect**, l'applicazione specifica i valori di attributo di connessione nella stringa di connessione richiesta Sfoglia. Il driver restituisce livelli successivi di attributi e valori di attributo nella stringa di connessione risultato Sfoglia; fino a quando sono presenti attributi di connessione che non sono ancora stati enumerati nella stringa di connessione richiesta Sfoglia restituisce SQL_NEED_DATA. L'applicazione utilizza il contenuto della stringa di connessione del risultato Sfoglia per compilare la stringa di connessione richiesta Sfoglia per la chiamata successiva a **SQLBrowseConnect**. Tutti gli attributi obbligatori (quelle non preceduto da un asterisco nel *OutConnectionString* argomento) deve essere incluso nella chiamata successiva a **SQLBrowseConnect**. Si noti che l'applicazione non è possibile usare il contenuto delle stringhe di connessione risultato ricerca precedente quando si compila la stringa di connessione richiesta Sfoglia corrente; non è possibile quindi specificare valori diversi per gli attributi impostati nei livelli precedenti.  
  
 Quando tutti i livelli di connessione e i relativi attributi associati sono stati enumerati, il driver restituisce SQL_SUCCESS, la connessione all'origine dati è stata completata e viene restituita una stringa di connessione completa per l'applicazione. La stringa di connessione è consigliabile utilizzare, in combinazione con **SQLDriverConnect**, con l'opzione SQL_DRIVER_NOPROMPT per stabilire un'altra connessione. La stringa di connessione completa non può essere utilizzata in un'altra chiamata a **SQLBrowseConnect**, tuttavia, se **SQLBrowseConnect** venisse chiamata nuovamente, l'intera sequenza di chiamate, è possibile ripetere.  
  
 **SQLBrowseConnect** anche restituisce SQL_NEED_DATA se sono presenti errori non irreversibili, recuperabili durante il processo di ricerca; ad esempio, una password non valida o una parola chiave di attributo fornita dall'applicazione. Quando viene restituito SQL_NEED_DATA e la stringa di connessione del risultato Sfoglia rimane invariata, si è verificato un errore e l'applicazione può chiamare **SQLGetDiagRec** per restituire il valore SQLSTATE per gli errori in fase di esplorazione. In tal modo l'applicazione per correggere l'attributo e continuare la ricerca.  
  
 Un'applicazione può terminare il processo di ricerca in qualsiasi momento chiamando **SQLDisconnect**. Il driver terminerà tutte le connessioni in sospeso e restituire la connessione a uno stato non è connesso.  
  
 Se sono abilitate le operazioni asincrone nell'handle di connessione, **SQLBrowseConnect** potrebbe restituire anche SQL_STILL_EXECUTING. Quando viene restituito SQL_NEED_DATA, un'applicazione deve utilizzare **SQLDisconnect** per annullare il processo di ricerca. Se **SQLBrowseConnect** restituisce SQL_STILL_EXECUTING, un'applicazione devono utilizzare **SQLCancelHandle** per annullare l'operazione in corso. La chiamata **SQLCancelHandle** dopo la funzione restituisce SQL_NEED_DATA non ha alcun effetto.  
  
 Per ulteriori informazioni, vedere [connessione con SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md).  
  
 Se un driver supporta **SQLBrowseConnect**, la sezione della parola chiave driver nelle informazioni di sistema per il driver deve contenere il **ConnectFunctions** parola chiave con il terzo carattere impostata su "Y".  
  
## <a name="code-example"></a>Esempio di codice  
  
> [!NOTE]  
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare `Trusted_Connection=yes` anziché informazioni utente ID e password nella stringa di connessione.  
  
 Nell'esempio seguente, un'applicazione chiama **SQLBrowseConnect** ripetutamente. Ogni volta che **SQLBrowseConnect** restituisce SQL_NEED_DATA, passa informazioni sui dati necessari in \* *OutConnectionString*. I passaggi di applicazione *OutConnectionString* alla relativa routine **GetUserInput** (non illustrato). **GetUserInput** analizza le informazioni, compila e visualizza una finestra di dialogo e restituisce le informazioni immesse dall'utente in \* *InConnectionString*. L'applicazione passa le informazioni dell'utente per il driver nella chiamata successiva a **SQLBrowseConnect**. Dopo l'applicazione ha fornito tutte le informazioni necessarie per il driver per la connessione all'origine dati, **SQLBrowseConnect** restituisce SQL_SUCCESS e l'applicazione continua.  
  
 Per un esempio più dettagliato di connessione a un driver di SQL Server tramite la chiamata **SQLBrowseConnect**, vedere [esempio esplorazione di SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md).  
  
 Per connettersi ai dati di vendita di origine, ad esempio, potrebbero verificarsi le seguenti azioni. In primo luogo, l'applicazione passa la stringa seguente per **SQLBrowseConnect**:  
  
```  
"DSN=Sales"  
```  
  
 Gestione Driver carica il driver associato all'origine dati delle vendite. Chiama quindi il driver **SQLBrowseConnect** funzione con gli stessi argomenti ricevuto dall'applicazione. Il driver restituisce la stringa seguente in **OutConnectionString*:  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 L'applicazione passa la stringa per il relativo **GetUserInput** routine, che compila una finestra di dialogo che chiede all'utente di selezionare il server verde, rosso o blu e immettere un ID utente e una password. Il routine passa nuovamente le informazioni seguenti specificato dall'utente \* *InConnectionString*, che l'applicazione passa al **SQLBrowseConnect**:  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **SQLBrowseConnect** utilizza queste informazioni per connettersi al server rosso come Smith, con la password pieno e quindi restituisce la stringa seguente in **OutConnectionString*:  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 L'applicazione passa la stringa per il relativo **GetUserInput** routine, che crea una finestra di dialogo che chiede all'utente di selezionare un database. Il empdata Seleziona utente e l'applicazione chiama **SQLBrowseConnect** un'ultima volta con questa stringa:  
  
```  
"DATABASE=SalesOrders"  
```  
  
 Questo è l'informazione finale che il driver deve connettersi all'origine dati. **SQLBrowseConnect** restituisce SQL_SUCCESS, e **OutConnectionString* contiene la stringa di connessione completata:  
  
```  
// SQLBrowseConnect_Function.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define BRWS_LEN 100  
SQLHENV henv;  
SQLHDBC hdbc;  
SQLHSTMT hstmt;  
SQLRETURN retcode;  
SQLCHAR szConnStrIn[BRWS_LEN], szConnStrOut[BRWS_LEN];  
SQLSMALLINT cbConnStrOut;  
  
void GetUserInput(SQLCHAR * szConnStrOut, SQLCHAR * szConnStrIn) {}  
  
int main() {  
   // Allocate the environment handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);        
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
      // Set the version environment attribute.  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
         // Allocate the connection handle.  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            // Call SQLBrowseConnect until it returns a value other than SQL_NEED_DATA   
            // (pass data source name the first time).  If SQL_NEED_DATA is returned, call GetUserInput   
            // (not shown) to build a dialog from the values in szConnStrOut.  The user-supplied values   
            // are returned in szConnStrIn, which is passed in the next call to SQLBrowseConnect.  
  
            strcpy_s((char*)szConnStrIn, _countof(szConnStrIn), "DSN=Sales");  
            do {  
               retcode = SQLBrowseConnect(hdbc, szConnStrIn, SQL_NTS,  
                  szConnStrOut, BRWS_LEN, &cbConnStrOut);  
               if (retcode == SQL_NEED_DATA)  
                  GetUserInput(szConnStrOut, szConnStrIn);  
            } while (retcode == SQL_NEED_DATA);  
  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
               // Allocate the statement handle.  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                  // Process data after successful connection  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               SQLDisconnect(hdbc);  
            }  
         }  
         SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      }  
   }  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocare un handle di connessione|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Connessione a un'origine dati|[Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Disconnessione da un'origine dati|[Funzione SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Connessione a un'origine dati tramite una connessione stringa o una finestra di dialogo|[Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Restituzione di attributi e le descrizioni di driver|[Funzione SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Liberare un handle di connessione|[Funzione SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

