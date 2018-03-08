---
title: Funzione SQLConnect | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLConnect
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLConnect
helpviewer_keywords: SQLConnect function [ODBC]
ms.assetid: 59075e46-a0ca-47bf-972a-367b08bb518d
caps.latest.revision: "37"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9f2c2d3e8b60d0a73d1beba4f68148cd956431b4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlconnect-function"></a>Funzione SQLConnect
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLConnect** stabilisce le connessioni a un driver e un'origine dati. Archiviazione di tutte le informazioni sulla connessione all'origine dati, inclusi lo stato, lo stato della transazione e informazioni sull'errore fa riferimento l'handle di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLConnect(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      ServerName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      UserName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      Authentication,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ConnectionHandle*  
 [Input] Handle di connessione.  
  
 *ServerName*  
 [Input] Nome dell'origine dati. I dati potrebbero trovarsi nello stesso computer del programma, o in un altro computer in un punto qualsiasi in una rete. Per informazioni su come un'applicazione sceglie un'origine dati, vedere [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Input] Lunghezza di **ServerName* in caratteri.  
  
 *UserName*  
 [Input] Identificatore dell'utente.  
  
 *NameLength2*  
 [Input] Lunghezza di **UserName* in caratteri.  
  
 *Autenticazione*  
 [Input] Stringa di autenticazione (in genere la password).  
  
 *NameLength3*  
 [Input] Lunghezza di **autenticazione* in caratteri.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE o SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLConnect** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_DBC e *gestire* di *ConnectionHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLConnect** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Il driver non supportava il valore specificato per il *ValuePtr* argomento **SQLSetConnectAttr** e sostituito con un valore analogo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|08001|Impossibile stabilire la connessione client|Il driver non è riuscito a stabilire una connessione con l'origine dati.|  
|08002|Nome della connessione in uso|(DM) specificato *ConnectionHandle* fosse già utilizzato per stabilire una connessione a un'origine dati e la connessione è ancora aperta o l'utente è stato esplorazione di una connessione.|  
|08004|Il server ha rifiutato la connessione|L'origine dati ha rifiutato la creazione di una connessione per motivi di tipo definito dall'implementazione.|  
|08S01|Errore del collegamento di comunicazione|Collegamento di comunicazione tra il driver e l'origine dati a cui è stato effettuato un tentativo di connessione il driver non è stato possibile prima dell'elaborazione della funzione è stata completata.|  
|28000|Specifica di autorizzazione non valido|Il valore specificato per l'argomento *UserName* o il valore specificato per l'argomento *autenticazione* viola le restrizioni definite dall'origine dati.|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Impossibile allocare la memoria che è necessario per supportare l'esecuzione o il completamento della funzione (DM) il Driver Manager.|  
|HY008|Operazione annullata|L'elaborazione asincrona è stata abilitata per il *ConnectionHandle*. Il **SQLConnect** funzione è stata chiamata e prima ha completato l'esecuzione, [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md) è stato chiamato sul *ConnectionHandle*e quindi la **SQLConnect** funzione è stata chiamata nuovamente sul *ConnectionHandle*.<br /><br /> O, **SQLConnect** funzione è stata chiamata e prima ha completato l'esecuzione, **SQLCancelHandle** è stato chiamato sul *ConnectionHandle* da un thread diverso in un applicazioni multithread.|  
|HY010|Errore nella sequenza (funzione)|(DM) a cui è stata chiamata per una funzione in modo asincrono in esecuzione (non è presente uno) di *ConnectionHandle* ed era ancora in esecuzione quando questa funzione è stata chiamata.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *NameLength1*, *NameLength2*, o *NameLength3* è minore di 0 ma non è uguale a SQL_NTS.<br /><br /> (DM) il valore specificato per l'argomento *NameLength1* supera la lunghezza massima per un nome origine dati.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima della connessione all'origine dati completata. Il periodo di timeout viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HY114|Driver non supporta l'esecuzione di funzione asincrona livello di connessione|(DM) l'applicazione è abilitata l'operazione asincrona nell'handle di connessione prima di effettuare la connessione. Tuttavia, il driver non supporta le operazioni asincrone nell'handle di connessione.|  
|HYT01|Timeout di connessione scaduto|Il periodo di timeout di connessione scaduto prima che l'origine dati ha risposto alla richiesta. Il periodo di timeout di connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Driver non supporta questa funzione|(DM) il driver specificato dal nome dell'origine dati non supporta la funzione.|  
|IM002|Origine dati non trovato e driver predefinito non specificato|(DM) specificato nell'argomento di nome dell'origine dati *ServerName* non è stato trovato nelle informazioni di sistema e non era presente una specifica del driver predefinito.|  
|IM003|Il driver specificato potrebbe non essere connesso a|(DM), il driver elencato nei dati specifica le informazioni di sistema di origine non è stato trovato o potrebbe non essere connesso a per altri motivi.|  
|IM004|SQLAllocHandle del driver su SQL_HANDLE_ENV non riuscita|(DM) durante **SQLConnect**, gestione Driver denominato il driver **SQLAllocHandle** funzione con un *HandleType* di impostato su SQL_HANDLE_ENV e il driver ha restituito un errore.|  
|IM005|SQLAllocHandle del driver su SQL_HANDLE_DBC non riuscita|(DM) durante **SQLConnect**, gestione Driver denominato il driver **SQLAllocHandle** funzione con un *HandleType* di impostato su SQL_HANDLE_DBC e il driver ha restituito un errore.|  
|IM006|Errore di SQLSetConnectAttr del driver|Durante la **SQLConnect**, gestione Driver denominato il driver **SQLSetConnectAttr** (funzione) e il driver ha restituito un errore. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|IM009|Impossibile connettersi a una DLL di conversione|Il driver non è riuscito a connettersi alla traduzione DLL che è stato specificato per l'origine dati.|  
|IM010|Nome dell'origine dati troppo lungo|(DM)  *\*ServerName* più lungo di caratteri SQL_MAX_DSN_LENGTH.|  
|IM014|Il DSN specificato contiene una mancata corrispondenza di architettura tra l'applicazione e il Driver|Applicazione a 32 bit (DM) utilizza un DSN la connessione a un driver a 64 bit. o viceversa.|  
|IM015|SQLConnect del driver su SQL_HANDLE_DBC_INFO_HANDLE non riuscita|Se un driver restituisce SQL_ERROR, gestione Driver restituirà SQL_ERROR all'applicazione e la connessione avrà esito negativo.<br /><br /> Per ulteriori informazioni su SQL_HANDLE_DBC_INFO_TOKEN, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Polling è disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente dell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, **SQLCompleteAsync** deve essere chiamato per l'handle per eseguire la post-elaborazione e completare l'operazione.|  
|S1118|Driver non supporta la notifica asincrona|Quando il driver non supporta la notifica asincrona, è possibile impostare SQL_ATTR_ASYNC_DBC_EVENT o SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="comments"></a>Commenti  
 Per informazioni sui motivi per cui un'applicazione utilizza **SQLConnect**, vedere [connessione con SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md).  
  
 Gestione Driver non è connesso a un driver fino a quando l'applicazione chiama una funzione (**SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**) per la connessione per il driver. Fino a quel punto, gestione Driver funziona con i proprio handle e gestisce informazioni di connessione. Quando l'applicazione chiama una funzione di connessione, gestione Driver controlla se un driver è attualmente connesso per l'oggetto specificato *ConnectionHandle*:  
  
-   Se un driver non è connesso a, gestione Driver si connette al driver e le chiamate **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV, **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC, **SQLSetConnectAttr** (se l'applicazione qualsiasi connessione gli attributi specificati) e la funzione di connessione nel driver. Gestione Driver restituisce SQLSTATE IM006 (patente **SQLSetConnectOption** non riuscita) e SQL_SUCCESS_WITH_INFO per la funzione di connessione se il driver ha restituito un errore per **SQLSetConnectAttr**. Per ulteriori informazioni, vedere [la connessione a un'origine dati o il Driver](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md).  
  
-   Se il driver specificato è già connesso a on il *ConnectionHandle*, gestione Driver chiama la funzione di connessione nel driver. In questo caso, il driver deve assicurarsi che gli attributi di tutte le connessioni per il *ConnectionHandle* mantenere le impostazioni correnti.  
  
-   Se è connesso un altro driver, Driver Manager chiama **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_DBC, e quindi, se un driver non è connesso a in tale ambiente, chiama **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_ENV nel driver connessi e quindi si disconnette tale driver. Quindi, viene eseguita quando un driver non è connesso alle stesse operazioni.  
  
 Quindi, il driver esegue l'allocazione di handle e inizializzato.  
  
 Quando l'applicazione chiama **SQLDisconnect**, le chiamate di gestione Driver **SQLDisconnect** nel driver. Tuttavia, non si disconnette il driver. In questo modo il driver in memoria per le applicazioni che ripetutamente connettersi e disconnettersi da un'origine dati. Quando l'applicazione chiama **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_DBC, gestione Driver chiama **SQLFreeHandle** con un *HandleType*  impostato su SQL_HANDLE_DBC e quindi **SQLFreeHandle** con un *HandleType* impostato su SQL_HANDLE_ENV nel driver e quindi si disconnette il driver.  
  
 Un'applicazione ODBC è possibile stabilire più connessioni.  
  
## <a name="driver-manager-guidelines"></a>Linee guida di Gestione driver  
 Il contenuto di **ServerName* influiscono sulla gestione Driver un driver interazione e per stabilire una connessione a un'origine dati.  
  
-   Se \* *ServerName* contiene un nome di origine dati valido, gestione Driver individua specifica dell'origine dati corrispondente nelle informazioni di sistema e si connette al driver associato. Gestione Driver passa ogni **SQLConnect** argomento per il driver.  
  
-   Se non viene trovato il nome dell'origine dati o *ServerName* è un puntatore null, gestione Driver individua specifica dell'origine dati predefinito e si connette al driver associato. Gestione Driver passa al driver di *UserName* e *autenticazione* argomenti senza modificarli e "DEFAULT" per il *ServerName* argomento.  
  
-   Se il *ServerName* argomento è "DEFAULT", gestione Driver individua specifica dell'origine dati predefinito e si connette al driver associato. Gestione Driver passa ogni **SQLConnect** argomento per il driver.  
  
-   Se non viene trovato il nome dell'origine dati o *ServerName* è un puntatore null e il valore predefinito specifica origine dati non esiste, gestione Driver restituisce SQL_ERROR con SQLSTATE IM002 (nome origine dati non trovato e alcun valore predefinito driver specificato).  
  
 Dopo che è connesso a da Gestione Driver, un driver può individuare la specifica origine dati corrispondente nelle informazioni di sistema e utilizzare informazioni specifiche del driver dalla specifica per completare un set di informazioni di connessione necessarie.  
  
 Se una libreria di traduzione predefinita è specificata nelle informazioni di sistema per l'origine dati, il driver si connette a esso. Può essere connesso a una libreria di conversione diverse in chiamando **SQLSetConnectAttr** con l'attributo SQL_ATTR_TRANSLATE_LIB. Un'opzione di conversione può essere specificata tramite la chiamata **SQLSetConnectAttr** con l'attributo SQL_ATTR_TRANSLATE_OPTION.  
  
 Se un driver supporta **SQLConnect**, la sezione della parola chiave driver delle informazioni di sistema per il driver deve contenere il **ConnectFunctions** (parola chiave) con il primo carattere è impostato su "Y".  
  
### <a name="connection-pooling"></a>Pool di connessioni  
 Il pool di connessioni consente a un'applicazione di riutilizzare una connessione che è già stata creata. Quando il pool di connessioni è abilitato e **SQLConnect** viene chiamato, gestione Driver tenta di stabilire la connessione utilizzando una connessione che fa parte di un pool di connessioni in un ambiente che è stato designato per il pool di connessioni. Questo ambiente è un ambiente condiviso utilizzato da tutte le applicazioni che utilizzano le connessioni nel pool.  
  
 Il pool di connessioni viene attivato prima che l'ambiente viene allocato chiamando **SQLSetEnvAttr** impostata SQL_ATTR_CONNECTION_POOLING su SQL_CP_ONE_PER_DRIVER (che specifica un massimo di un pool per ogni driver) o SQL_CP_ONE_PER_HENV (che specifica un massimo di un pool per ogni ambiente). **SQLSetEnvAttr** in questo caso, viene chiamato con *EnvironmentHandle* impostato su null, che rende l'attributo di un attributo a livello di processo. Se SQL_ATTR_CONNECTION_POOLING è impostata su SQL_CP_OFF, il pool di connessioni è disabilitato.  
  
 Dopo aver abilitato il pool di connessioni, **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV viene chiamata per allocare un ambiente. L'ambiente allocato da questa chiamata è un ambiente condiviso, poiché il pool di connessioni è stato abilitato. Tuttavia, l'ambiente che verrà usato viene determinata solo **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC viene chiamato.  
  
 **SQLAllocHandle** con un *HandleType* chiamata impostato su SQL_HANDLE_DBC per allocare una connessione. Gestione Driver tenta di trovare un ambiente condiviso esistente che corrisponde agli attributi di ambiente impostati dall'applicazione. Se l'ambiente non esiste, ne viene creata come implicita *ambiente condiviso*. Se viene trovato un ambiente condiviso corrispondente, viene restituito l'handle di ambiente per l'applicazione e il conteggio dei riferimenti viene incrementato.  
  
 Tuttavia, la connessione da utilizzare viene determinata solo **SQLConnect** viene chiamato. A questo punto, gestione Driver tenta di trovare una connessione esistente nel pool di connessioni che corrisponde ai criteri richiesti dall'applicazione. Tali criteri includono le opzioni di connessione richieste nella chiamata a **SQLConnect** (i valori del *ServerName*, *UserName*, e  *Autenticazione* parole chiave) e gli attributi di connessione impostata poiché **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC è stato chiamato. Gestione Driver controlla i criteri contro gli attributi nel pool di connessioni e parole chiave di connessione corrispondenti. Se viene trovata una corrispondenza, viene utilizzata la connessione nel pool. Se viene trovata alcuna corrispondenza, viene creata una nuova connessione.  
  
 Se l'attributo di ambiente SQL_ATTR_CP_MATCH è impostato su SQL_CP_STRICT_MATCH, la corrispondenza deve essere esatta per una connessione in pool da utilizzare. Se l'attributo di ambiente SQL_ATTR_CP_MATCH è impostato su SQL_CP_RELAXED_MATCH, opzioni di connessione nella chiamata a **SQLConnect** devono corrispondenza ma non tutti gli attributi di connessione deve corrispondere.  
  
 Le seguenti regole vengono applicate quando un attributo di connessione, l'impostazione applicazione prima di **SQLConnect** viene chiamato, non corrisponde all'attributo di connessione della connessione nel pool di:  
  
-   Se l'attributo di connessione deve essere impostata prima che venga effettuata la connessione:  
  
     Se SQL_ATTR_CP_MATCH SQL_CP_STRICT_MATCH, SQL_ATTR_PACKET_SIZE nella connessione in pool deve essere identico all'attributo impostato dall'applicazione. Se SQL_CP_RELAXED_MATCH, i valori di SQL_ATTR_PACKET_SIZE può essere diverso.  
  
     Il valore di SQL_ATTR_LOGIN_VALUE non influenza la corrispondenza.  
  
-   Se l'attributo di connessione può essere impostato prima o dopo aver effettuata la connessione:  
  
     Se l'attributo di connessione non è stato impostato dall'applicazione ma è stato impostato per la connessione nel pool e vi è un'impostazione predefinita, l'attributo di connessione nella connessione in pool è impostata sul valore predefinito e viene dichiarata una corrispondenza. Se è presente alcun valore predefinito, la connessione in pool non viene considerata una corrispondenza.  
  
     Se l'attributo di connessione è stato impostato dall'applicazione ma non è stato impostato per la connessione in pool, l'attributo di connessione nel pool viene modificato in tale set dall'applicazione e viene dichiarata una corrispondenza.  
  
     Se l'attributo di connessione è stato impostato dall'applicazione e anche impostato per la connessione nel pool, ma i valori sono diversi, viene utilizzato il valore dell'attributo di connessione dell'applicazione e viene dichiarata una corrispondenza.  
  
-   Se i valori degli attributi di connessione specifici del driver non sono identici e SQL_ATTR_CP_MATCH è impostato su SQL_CP_STRICT_MATCH, non verrà usata la connessione nel pool.  
  
 Quando l'applicazione chiama **SQLDisconnect** per disconnettersi, la connessione, viene restituita al pool di connessioni ed è disponibile per il riutilizzo.  
  
### <a name="optimizing-connection-pooling-performance"></a>Ottimizzazione delle prestazioni del pool di connessioni  
 Quando sono coinvolte le transazioni distribuite, è possibile ottimizzare le prestazioni del pool utilizzando **SQL_DTC_TRANSITION_COST**, ovvero una maschera di bit SQLUINTEGER. Le transizioni definite sono transizioni dell'attributo SQL_ATTR_ENLIST_IN_DTC dal valore 0 a diverso da zero, connessione e viceversa. Si tratta di una connessione da non integrate in una transazione distribuita integrata in una transazione distribuita e viceversa. A seconda di come il driver ha implementato integrazione (l'impostazione connessione dell'attributo SQL_ATTR_ENLIST_IN_DTC), queste transizioni potrebbero essere conveniente e pertanto devono essere evitate per prestazioni ottimali.  
  
 Il valore restituito dal driver contiene qualsiasi combinazione dei bit seguenti:  
  
-   **SQL_DTC_ENLIST_EXPENSIVE**, quando è impostata, implica lo zero transizione diverso da zero è molto più costoso di una transizione da diverso da zero a un altro valore diverso da zero (integrazione di una connessione integrata in precedenza la transazione successiva).  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE**, quando è impostata, implica diverso da zero per zero la transizione è molto più costoso rispetto all'utilizzo di una connessione il cui attributo SQL_ATTR_ENLIST_IN_DTC è già impostata su zero.  
  
 È delle prestazioni rispetto a compromesso di utilizzo della connessione. Se un driver indica che uno o più di queste transizioni sono costosi, pool di connessioni di Gestione driver risponde a questo mantenendo più connessioni nel pool. Alcune delle connessioni nel pool sono preferiti per l'utilizzo non transazionale e alcuni sono preferiti per l'utilizzo di transazione. Tuttavia, se il driver indica che queste transizioni non siano onerosi, meno connessioni utilizzabile, forse alternando tra non transazionale e di utilizzare transazionale.  
  
 I driver che non supportano SQL_ATTR_ENLIST_IN_DTC non è necessario supportare SQL_DTC_TRANSITION_COST. Per i driver che supportano SQL_ATTR_ENLIST_IN_DTC ma non SQL_DTC_TRANSITION_COST, si presuppone che le transizioni non sono costose, come se il driver restituisce 0 (Nessun set di bit) per questo valore.  
  
 Anche se SQL_DTC_TRANSITION_COST è stata introdotta in ODBC 3.5, un'API ODBC 2. *x* driver può anche supportarla perché Gestione driver richiederà a queste informazioni indipendentemente dalla versione del driver.  
  
### <a name="code-example"></a>Esempio di codice  
 Nell'esempio seguente, un'applicazione alloca connessione e dell'ambiente handle. Quindi si connette all'origine dati degli ordini di vendita con l'utente ID JohnS e la password pieno ed elabora i dati. Quando ha terminato l'elaborazione dei dati, disconnette dall'origine dati e consente di liberare l'handle.  
  
```  
// SQLConnect_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR * OutConnStr = (SQLCHAR * )malloc(255);  
   SQLSMALLINT * OutConnStrLen = (SQLSMALLINT *)malloc(255);  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLCHAR*) "NorthWind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
  
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
  
### <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Individuazione e l'enumerazione dei valori necessari per connettersi a un'origine dati|[Funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Disconnessione da un'origine dati|[Funzione SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Connessione a un'origine dati tramite una connessione stringa o una finestra di dialogo|[Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Restituisce l'impostazione di un attributo di connessione|[Funzione SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
