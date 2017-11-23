---
title: Utilizzo di Connection String Keywords with SQL Server Native Client | Documenti Microsoft
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
caps.latest.revision: "81"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 03cfc5aa4dd24dc595984298710c073061bec0b7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Utilizzo delle parole chiave delle stringhe di connessione con SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In alcune API di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate stringhe di connessione per specificare gli attributi di connessione. Le stringhe di connessione sono elenchi di parole chiave con i relativi valori associati. Ogni parola chiave identifica un particolare attributo di connessione.  
  
> **Nota:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta l'ambiguità nelle stringhe di connessione per mantenere la compatibilità con le versioni precedenti (ad esempio, alcune parole chiave possono essere specificati più di una volta e possono essere consentite parole chiave in conflitto con una risoluzione basata sulla posizione o precedenza). È possibile che nelle versioni successive di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client tale ambiguità non sia più supportata. Quando si modificano le applicazioni, è consigliabile utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per eliminare l'eventuale dipendenza dall'ambiguità delle stringhe di connessione.  
  
 Nelle sezioni seguenti vengono descritte le parole chiave che è possibile specificare con il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e gli oggetti ADO (ActiveX Data Objects) quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client come provider di dati.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Parole chiave di stringa di connessione del Driver ODBC  
 Le applicazioni ODBC utilizzano stringhe di connessione come parametri il [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) e [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) funzioni.  
  
 Le stringhe di connessione utilizzate da ODBC presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ODBC.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|**Addr**|Sinonimo di "Address".|  
|**Indirizzo**|Indirizzo di rete del server che esegue un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Indirizzo** è in genere il nome di rete del server, ma può corrispondere ad altri nomi, ad esempio una pipe, un indirizzo IP o un indirizzo di porta e i socket TCP/IP.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Il valore di **indirizzo** ha la precedenza sul valore passato a **Server** nelle stringhe di connessione ODBC quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Si noti inoltre che `Address=;` si connetterà al server specificato nella **Server** (parola chiave), mentre `Address= ;, Address=.;`, `Address=localhost;`, e `Address=(local);` verrà stabilita una connessione al server locale.<br /><br /> La sintassi completa per la **indirizzo** (parola chiave) è il seguente:<br /><br /> [*protocollo***:**]*indirizzo*[**,***porta &#124; \pipe\pipename*]<br /><br /> *protocol* può essere **tcp** (TCP/IP), **lpc** (memoria condivisa) o **np** (named pipe). Per ulteriori informazioni sui protocolli, vedere [configurazione di protocolli Client](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Se non si specifica *protocollo* né la **rete** viene specificata una parola chiave, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene utilizzato l'ordine dei protocolli specificato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *porta* è la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.|  
|**AnsiNPW**|Se l'opzione è impostata su "yes", nel driver vengono utilizzati i comportamenti definiti da ANSI per la gestione dei confronti NULL, del riempimento dei dati di tipo carattere, degli avvisi e della concatenazione NULL. Se impostata su "no", i comportamenti definiti da ANSI non vengono esposti. Per ulteriori informazioni sui comportamenti ANSI NPW, vedere [gli effetti delle opzioni ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**APP**|Nome dell'applicazione che chiama [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) (facoltativo). Se specificato, questo valore viene archiviato nel **master.dbo** colonna **program_name** e viene restituito da [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) e [nome_app](../../../t-sql/functions/app-name-transact-sql.md) funzioni.|  
|**ApplicationIntent**|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**. Il valore predefinito è **ReadWrite**.  Esempio:<br /><br /> `ApplicationIntent=ReadOnly`<br /><br /> Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto del Client nativo per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client supporta per il ripristino di emergenza a disponibilità elevata](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|Nome del file primario di un database collegabile. Includere il percorso completo e utilizzare la sequenza di escape dei caratteri \ se si utilizza una variabile di tipo stringa di caratteri C:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Questo database viene collegato e diventa il database predefinito per la connessione. Per utilizzare **AttachDBFileName** è inoltre necessario specificare il nome del database in uno di [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) parametro del DATABASE o l'attributo di connessione SQL_COPT_CURRENT_CATALOG. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**AutoTranslate**|Se impostata su "yes", le stringhe di caratteri ANSI inviate tra il client e il server vengono convertite in Unicode per ridurre al minimo i problemi di corrispondenza dei caratteri estesi tra le tabelle codici sul client e sul server.<br /><br /> Dati SQL_C_CHAR del client inviati a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**, **varchar**, o **testo** colonna, parametro o variabile è convertita da caratteri a Unicode utilizzando client tabella codici ANSI (ACP), quindi vengono convertita da Unicode a caratteri utilizzando la tabella codici ANSI del server.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**char**, **varchar**, o **testo** dati inviati a una variabile SQL_C_CHAR del client sono convertiti da caratteri in Unicode utilizzando l'ACP del server, quindi vengono convertiti da Unicode a caratteri utilizzando l'ACP del client.<br /><br /> Queste conversioni vengono eseguite sul client dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e richiedono che sul client sia disponibile la stessa tabella codici ANSI (ACP) utilizzata sul server.<br /><br /> Queste impostazioni non influiscono sulle conversioni eseguite per i trasferimenti seguenti:<br /><br /> \*Dati client SQL_C_WCHAR Unicode inviati a **char**, **varchar**, o **testo** sul server.<br /><br /> \***char**, **varchar**, o **testo** dati server inviati a una variabile SQL_C_WCHAR Unicode sul client.<br /><br /> \*Dati client SQL_C_CHAR ANSI inviati in formato Unicode **nchar**, **nvarchar**, o **ntext** sul server.<br /><br /> \*Unicode **nchar**, **nvarchar**, o **ntext** dati server inviati a una variabile SQL_C_CHAR ANSI sul client.<br /><br /> Se impostata su "no", la conversione dei caratteri non viene eseguita.<br /><br /> Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native Client non converte i dati SQL_C_CHAR carattere ANSI del client inviati a **char**, **varchar**, o **testo** variabili, parametri o colonne nel server. Viene eseguita alcuna conversione **char**, **varchar**, o **testo** dati inviati dal server alle variabili SQL_C_CHAR sul client.<br /><br /> Se il client e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzano ACP differenti, i caratteri estesi potrebbero essere interpretati in modo errato.|  
|**Database**|Nome del database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] predefinito per la connessione. Se **Database** viene omesso, viene utilizzato il database predefinito per l'account di accesso. Il database predefinito dell'origine dati ODBC esegue l'override del database predefinito specificato per l'accesso. Il database deve essere un database esistente, a meno che non **AttachDBFileName** viene anche specificato. Se **AttachDBFileName** viene anche specificato punti al file primario è collegato e specificato il nome del database specificato da **Database**.|  
|**Driver**|Nome del driver restituito da [SQLDrivers](../../../relational-databases/native-client-odbc-api/sqldrivers.md). Il valore della parola chiave per il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client è "{SQL Server Native Client 11.0}". Il **Server** parola chiave è obbligatoria se **Driver** specificato e **DriverCompletion** è impostato su SQL_DRIVER_NOPROMPT.<br /><br /> Per ulteriori informazioni sui nomi di driver, vedere [utilizzando i file di libreria e l'intestazione di SQL Server Native Client](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md).|  
|**DSN**|Nome di un'origine dati di sistema o di un utente ODBC esistente. Questa parola chiave override dei valori che potrebbero essere specificati nel **Server**, **rete**, e **indirizzo** parole chiave.|  
|**Crittografare**|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**Fallback**|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**Failover_Partner**|Nome del server partner di failover da utilizzare se non è possibile stabilire una connessione al server primario.|  
|**FailoverPartnerSPN**|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal driver.|  
|**FileDSN**|Nome di un'origine dati dei file ODBC esistente.|  
|**Lingua**|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (facoltativo). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]può memorizzare messaggi per più lingue in **sysmessages**. Se la connessione a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con più lingue, **Language** specifica il set di messaggi utilizzato per la connessione.|  
|**MARS_Connection**|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "yes" e "no". Il valore predefinito è "no".|  
|**MultiSubnetFailover**|Specificare sempre **multiSubnetFailover = Yes** quando ci si connette al listener del gruppo di disponibilità di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gruppo di disponibilità o un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza Cluster di Failover. **multiSubnetFailover = Yes** configura [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per fornire un rilevamento più veloce e una connessione al server attualmente attivo. I valori possibili sono **Sì** e **No**. Il valore predefinito è **n**. Esempio:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto del Client nativo per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client supporta per il ripristino di emergenza a disponibilità elevata](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**NET**|Sinonimo di "Network".|  
|**Rete**|I valori validi sono **dbnmpntw** (named pipe) e **dbmssocn** (TCP/IP).<br /><br /> È possibile specificare sia un valore per il **rete** (parola chiave) e un protocollo di prefisso nel **Server** (parola chiave).|  
|**PWD**|Password per l'account di accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificato nel parametro UID. **PWD** non è necessario specificare se l'account di accesso dispone di una password NULL o quando si utilizza l'autenticazione di Windows (`Trusted_Connection = yes`).|  
|**QueryLog_On**|Se impostata su "yes", la registrazione dei dati di query con esecuzione prolungata viene abilitata per la connessione. Se impostata su "no", i dati di query con esecuzione prolungata non vengono registrati.|  
|**QueryLogFile**|Nome e percorso completo di un file da utilizzare per registrare dati nelle query con esecuzione prolungata.|  
|**QueryLogTime**|Stringa di cifre che specifica la soglia (in millisecondi) per la registrazione delle query con esecuzione prolungata. Tutte le query che non ottengono una risposta nell'intervallo di tempo specificato vengono scritte nel file di log delle query con esecuzione prolungata.|  
|**QuotedId**|Se impostata su "yes", QUOTED_IDENTIFIERS viene impostata su ON per la connessione e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono utilizzate le regole ISO relative all'uso delle virgolette nelle istruzioni SQL. Se impostata su no, QUOTED_IDENTIFIERS viene impostata su OFF per la connessione. In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono quindi seguite le regole [!INCLUDE[tsql](../../../includes/tsql-md.md)] legacy relative all'utilizzo delle virgolette nelle istruzioni SQL. Per ulteriori informazioni, vedere [gli effetti delle opzioni ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**Internazionali**|Se impostata su "yes", nel driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate le impostazioni client per la conversione dei dati di valuta, data e ora in dati di tipo carattere. La conversione viene eseguita in una sola direzione. Il driver non riconosce i formati standard non ODBC per le stringhe di data o i valori di valuta all'interno, ad esempio, di un parametro utilizzato in un'istruzione INSERT o UPDATE. Se impostata su "no", nel driver vengono utilizzate le stringhe standard ODBC per rappresentare i dati di valuta, data e ora convertiti in dati di tipo carattere.|  
|**SaveFile**|Nome di un file di origine dati ODBC nel quale vengono salvati gli attributi della connessione corrente se la connessione riesce.|  
|**Server**|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore deve corrispondere al nome di un server in rete, a un indirizzo IP o al nome di un alias di Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Il **indirizzo** (parola chiave) esegue l'override di **Server** (parola chiave).<br /><br /> È possibile connettersi all'istanza predefinita nel server locale specificando uno dei valori seguenti:<br /><br /> **Server =;**<br /><br /> **Server =.;**<br /><br /> **Local;**<br /><br /> **Local;**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(LocalDB)\\**  *instancename* **;**<br /><br /> Per ulteriori informazioni sul supporto del database locale, vedere [SQL Server Native Client supporta per LocalDB](../../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md).<br /><br /> Per specificare un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], aggiungere  **\\**  *InstanceName*.<br /><br /> Se non viene specificato un server, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La sintassi completa per la **Server** (parola chiave) è il seguente:<br /><br /> **Server =**[*protocollo***:**]*Server*[**,***porta*]<br /><br /> *protocol* può essere **tcp** (TCP/IP), **lpc** (memoria condivisa) o **np** (named pipe).<br /><br /> Nell'esempio seguente si illustra come specificare una named pipe:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Questa riga specifica un protocollo Named Pipes, una named pipe nel computer locale (`\\.\pipe`), il nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) e il nome predefinito della named pipe (`sql/query`).<br /><br /> Se non si specifica un *protocollo* né la **rete** viene specificata una parola chiave, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene utilizzato l'ordine dei protocolli specificato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *porta* è la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.<br /><br /> Gli spazi vengono ignorati all'inizio del valore passato a **Server** nelle stringhe di connessione ODBC quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**ServerSPN**|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal driver.|  
|**StatsLog_On**|Se impostata su "yes", abilita l'acquisizione dei dati relativi alle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Se impostata su "no", i dati relativi alle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non sono disponibili nella connessione.|  
|**StatsLogFile**|Nome e percorso completo di un file utilizzato per registrare le statistiche sulle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**Trusted_Connection**|Se impostata su "yes", indica al driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare la Modalità di autenticazione di Windows per la convalida dell'accesso. In caso contrario, indica al driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare un nome utente e una password di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la convalida dell'accesso e richiede la specifica delle parole chiave UID e PWD.|  
|**TrustServerCertificate**|Se usato con **Encrypt**, consente la crittografia mediante un certificato server autofirmato.|  
|**UID**|Account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valido. Quando si utilizza l'autenticazione di Windows non è necessario specificare l'UID.|  
|**UseProcForPrepare**|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**WSID**|ID della workstation. In genere, si tratta del nome di rete del computer nel quale risiede l'applicazione (facoltativo). Se specificato, questo valore viene archiviato nel **master.dbo** colonna **hostname** e viene restituito da [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) e [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) (funzione).|  
  
> **Nota:** internazionali conversione impostazioni si applicano a valuta, numerico, data e tipi di dati ora. L'impostazione di conversione è applicabile solo alla conversione di output ed è visibile solo quando i valori di valuta, data, ora o numerici vengono convertiti in stringhe di caratteri.  
  
 Nel driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate le impostazioni locali del Registro di sistema per l'utente corrente. Il driver non rispetta le impostazioni locali del thread corrente se l'applicazione le imposta dopo la connessione, ad esempio, la chiamata **SetThreadLocale**.  
  
 La modifica del comportamento internazionale di un'origine dati può generare un errore nell'applicazione. Un'applicazione che analizza le stringhe relative alla data e ne prevede la visualizzazione in base a quanto definito da ODBC, potrebbe essere influenzata negativamente dalla modifica di questo valore.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per il provider OLE DB  
 Quando si utilizzano le applicazioni OLE DB, è possibile inizializzare gli oggetti origine dati in due modi diversi:  
  
-   **IDBInitialize:: Initialize**  
  
-   **IDataInitialize:: GetDatasource**  
  
 Nel primo caso è possibile utilizzare una stringa del provider per inizializzare le proprietà di connessione impostando la proprietà DBPROP_INIT_PROVIDERSTRING nel set di proprietà DBPROPSET_DBINIT. Nel secondo caso, una stringa di inizializzazione può essere passata a **IDataInitialize:: GetDatasource** metodo per inizializzare le proprietà di connessione. Entrambi i metodi inizializzano le stesse proprietà di connessione OLE DB, sebbene con set di parole chiave differenti. Il set di parole chiave utilizzate dal **IDataInitialize:: GetDatasource** è al minimo la descrizione delle proprietà all'interno del gruppo di proprietà di inizializzazione.  
  
 Per qualsiasi impostazione di stringa del provider con una proprietà OLE DB corrispondente impostata su un valore predefinito o impostata in modo esplicito su un valore, tramite il valore della proprietà OLE DB verrà eseguito l'override dell'impostazione nella stringa del provider.  
  
 Per le proprietà booleane impostate nelle stringhe del provider mediante i valori DBPROP_INIT_PROVIDERSTRING vengono utilizzati i valori "yes" e "no". Le proprietà booleane impostate nelle stringhe di inizializzazione utilizzando **IDataInitialize:: GetDatasource** vengono impostate utilizzando i valori "true" e "false".  
  
 Applicazioni che usano **IDataInitialize:: GetDatasource** inoltre possibile utilizzare le parole chiave utilizzate dal **IDBInitialize:: Initialize** ma solo per le proprietà che non contengono un valore predefinito. Se un'applicazione utilizza sia il **IDataInitialize:: GetDatasource** (parola chiave) e **IDBInitialize:: Initialize** parola chiave nella stringa di inizializzazione, il **IDataInitialize:: GetDatasource** viene utilizzata l'impostazione della parola chiave. È consigliabile che le applicazioni non utilizzano **IDBInitialize:: Initialize** parole chiave in **IDataInitialize: GetDatasource** stringhe di connessione, perché questo comportamento potrebbe non essere supportato nelle versioni successive.  
  
> [!NOTE]  
>  Una stringa di connessione passata a **IDataInitialize:: GetDatasource** viene convertita in proprietà e applicata tramite **IDBProperties:: SetProperties**. Se Servizi componenti ha rilevato la descrizione della proprietà in **IDBProperties:: GetPropertyInfo**, questa proprietà verrà applicata come autonoma. In caso contrario, verrà applicata mediante la proprietà DBPROP_PROVIDERSTRING. Ad esempio, se si specifica una stringa di connessione **origine dati = server1; Server = server2**, **origine dati** verrà impostato come proprietà, ma **Server** entra in una stringa del provider.  
  
 Se si indicano più istanze per la stessa proprietà specifica del provider, verrà utilizzato il primo valore della prima proprietà.  
  
 Stringhe di connessione utilizzate nelle applicazioni OLE DB utilizzando DBPROP_INIT_PROVIDERSTRING con **IDBInitialize:: Initialize** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con DBPROP_INIT_PROVIDERSTRING.  
  
|Parola chiave|Proprietà di inizializzazione|Description|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Sinonimo di "Address".|  
|**Indirizzo**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi valida di indirizzo, vedere la descrizione del **indirizzo** parola chiave ODBC, più avanti in questo argomento.|  
|**APP**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto del Client nativo per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client supporta per il ripristino di emergenza a disponibilità elevata](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave Database della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "yes" e "no".|  
|**Database**|DBPROP_INIT_CATALOG|Nome del database.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|**Crittografare**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Lingua**|SSPROPT_INIT_CURRENTLANGUAGE|Lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**NET**|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|**Rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|**Dimensioni del pacchetto**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "yes" e "no" come valori. Se impostata su "no", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|**PWD**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi valida di indirizzo, vedere la descrizione del **Server** parola chiave ODBC, in questo argomento.|  
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Se impostata su "yes", indica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare la Modalità di autenticazione di Windows per la convalida dell'accesso. In caso contrario, indica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare un nome utente e una password di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la convalida dell'accesso e richiede la specifica delle parole chiave UID e PWD.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "yes" e "no" come valori. Il valore predefinito è "no", il quale indica che il certificato server verrà convalidato.|  
|**UID**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**WSID**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 Stringhe di connessione utilizzate nelle applicazioni OLE DB utilizzando **IDataInitialize:: GetDatasource** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilizzo delle proprietà deve essere conforme alla sintassi consentita nel relativo ambito.  Ad esempio, **WSID** utilizzate le parentesi graffe (**{}**) virgolette e **nome applicazione** vengono utilizzate (**'**) o doppie (**"**) virgolette. Solo per le proprietà delle stringhe è possibile utilizzare le virgolette. Se si tenta di utilizzare le virgolette con una proprietà Integer o enumerata, verrà generato un errore che indica che la stringa di connessione non è conforme alla specifica OLE DB.  
  
 È consigliabile racchiudere i valori di attributo tra virgolette semplici o doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. Se raddoppiato, il carattere virgoletta può essere visualizzato anche per i valori.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Se una stringa di connessione include più di una delle proprietà elencate nella tabella seguente, verrà utilizzato il valore dell'ultima proprietà.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con **IDataInitialize:: GetDatasource**:  
  
|Parola chiave|Proprietà di inizializzazione|Description|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**Finalità dell'applicazione**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto del Client nativo per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client supporta per il ripristino di emergenza a disponibilità elevata](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Lingua corrente**|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Data Source**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi valida di indirizzo, vedere la descrizione del **Server** parola chiave ODBC, più avanti in questo argomento.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Partner di failover**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**Partner di failover SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Catalogo iniziale**|DBPROP_INIT_CATALOG|Nome del database.|  
|**Nome File iniziale**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Sicurezza integrata**|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|**Connessione MARS**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|**Indirizzo di rete**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi valida di indirizzo, vedere la descrizione del **indirizzo** parola chiave ODBC, più avanti in questo argomento.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**Password**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|**Provider**||Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, deve essere "SQLNCLI11".|  
|**SPN server**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|**ID utente**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID workstation**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** nella stringa di connessione, la proprietà "Vecchia Password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà di stringa del provider.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per gli oggetti ADO (ActiveX Data Objects)  
 Applicazioni ADO impostano la **ConnectionString** proprietà di **ADODBConnection** oggetti o fornire una stringa di connessione come parametro per il **aprire** metodo **ADODBConnection** oggetti.  
  
 Applicazioni ADO possono inoltre utilizzare le parole chiave utilizzate da OLE DB **IDBInitialize:: Initialize** (metodo), ma solo per le proprietà che non contengono un valore predefinito. Se un'applicazione utilizza entrambe le parole chiave ADO e **IDBInitialize:: Initialize** parole chiave nella stringa di inizializzazione, l'impostazione della parola chiave ADO verranno utilizzate. Nelle applicazioni è consigliabile utilizzare solo le parole chiave delle stringhe di connessione ADO.  
  
 Le stringhe di connessione utilizzate da ADO presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra virgolette doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. I valori attributo non possono contenere virgolette doppie.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ADO:  
  
|Parola chiave|Proprietà di inizializzazione|Description|  
|-------------|-----------------------------|-----------------|  
|**Finalità dell'applicazione**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto del Client nativo per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client supporta per il ripristino di emergenza a disponibilità elevata](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Application Name**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Lingua corrente**|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Data Source**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi valida di indirizzo, vedere la descrizione del **Server** parola chiave ODBC, in questo argomento.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati che verrà utilizzata. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|**Partner di failover**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**Partner di failover SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Catalogo iniziale**|DBPROP_INIT_CATALOG|Nome del database.|  
|**Nome File iniziale**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Sicurezza integrata**|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|**Connessione MARS**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|**Indirizzo di rete**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi valida di indirizzo, vedere la descrizione del **indirizzo** parola chiave ODBC, in questo argomento.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**Password**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate.|  
|**Provider**||Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, deve essere "SQLNCLI11".|  
|**SPN server**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|**ID utente**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID workstation**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** nella stringa di connessione, la proprietà "Vecchia Password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà di stringa del provider.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
