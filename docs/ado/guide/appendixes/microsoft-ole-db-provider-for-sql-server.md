---
title: Provider Microsoft OLE DB per SQL Server | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], OLE DB provider for SQL Server
- OLE DB provider for SQL Server [ADO]
- SQLOLEDB [ADO]
ms.assetid: 99bc40c4-9181-4ca1-a06f-9a1a914a0b7b
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: a81ac91a4a159d41e711f79f76f79d9f168e23af
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Provider Microsoft OLE DB per una panoramica di SQL Server
Il Provider Microsoft OLE DB per SQL Server, SQLOLEDB, consente di ADO per accedere a Microsoft SQL Server.

## <a name="connection-string-parameters"></a>Parametri di stringa di connessione
 Per connettersi a questo provider, impostare il *Provider* argomento per il [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà:

```
SQLOLEDB
```

 Questo valore può essere impostato o utilizzando il [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=SQLOLEDB;Data Source=serverName;"
Initial Catalog=databaseName;
User ID=MyUserID;Password=MyPassword;"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il Provider OLE DB per SQL Server.|
|**Origine dati** o **Server**|Specifica il nome di un server.|
|**Catalogo iniziale** o **Database**|Specifica il nome di un database nel server.|
|**ID utente** o **uid**|Specifica il nome utente (autenticazione di SQL Server).|
|**Password** o **pwd**|Specifica la password dell'utente (autenticazione di SQL Server).|

> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** o **Integrated Security = SSPI** anziché l'ID utente e password informazioni nella stringa di connessione.

## <a name="provider-specific-connection-parameters"></a>Parametri di connessione specifica del provider
 Il provider supporta vari parametri di connessione specifica del provider oltre a quelli definiti da ADO. Come con le proprietà di connessione ADO, è possono impostare queste proprietà specifiche del provider tramite il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta di un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oppure può essere impostato come parte di **ConnectionString**.

|Parametro|Description|
|---------------|-----------------|
|Trusted_Connection|Indica la modalità di autenticazione utente. Può essere impostata su **Sì** o **n**. Il valore predefinito è **n**. Se questa proprietà è impostata su **Sì**, SQLOLEDB utilizza la modalità di autenticazione di Microsoft Windows NT per autorizzare l'accesso al database di SQL Server specificato dall'utente di **percorso** e [Datasource ](../../../ado/reference/ado-api/datasource-property-ado.md) i valori delle proprietà. Se questa proprietà è impostata su **n**, SQLOLEDB utilizza la modalità mista per autorizzare l'accesso utente al database di SQL Server. L'account di accesso di SQL Server e la password vengono specificati nel **Id utente** e **Password** proprietà.|
|Lingua corrente|Indica un nome di lingua di SQL Server. Identifica la lingua utilizzata per la selezione e la formattazione dei messaggi di sistema. La lingua deve essere installata in SQL Server, apertura in caso contrario, la connessione avrà esito negativo.|
|Indirizzo di rete|Indica l'indirizzo di rete del Server SQL specificato per il **percorso** proprietà.|
|Libreria di rete|Indica il nome della libreria di rete (DLL) utilizzata per comunicare con SQL Server. Il nome non deve include il percorso o l'estensione di file DLL. Il valore predefinito è fornito dalla configurazione di client di SQL Server.|
|Usare Procedure per preparare|Determina se SQL Server crea le stored procedure temporanee quando sono stati preparati i comandi (per il **Prepared** proprietà).|
|Conversione automatica|Indica se i caratteri OEM/ANSI vengono convertiti. Questa proprietà può essere impostata su **True** o **False**. Il valore predefinito è **True**. Se questa proprietà è impostata su **True**, SQLOLEDB esegue la conversione dei caratteri OEM/ANSI se le stringhe di caratteri multibyte vengono recuperate da o inviate a SQL Server. Se questa proprietà è impostata su **False**, SQLOLEDB non esegue la conversione dei caratteri OEM/ANSI in dati di stringa di caratteri multibyte.|
|Packet Size|Indica una dimensione del pacchetto di rete in byte. Il valore della proprietà dimensione pacchetto deve essere compreso tra 512 e 32767. Le dimensioni predefinite del pacchetto di rete SQLOLEDB sono 4096.|
|Application Name|Indica il nome dell'applicazione client.|
|ID workstation|Stringa che identifica la workstation.|

## <a name="command-object-usage"></a>Utilizzo dell'oggetto Command
 SQLOLEDB accetta un amalgama di ODBC, ANSI e specifiche di SQL Server Transact-SQL come sintassi valida. L'istruzione SQL seguente, ad esempio, utilizza una sequenza di escape ODBC SQL per specificare la funzione per i valori stringa LCASE:

```
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 LCASE restituisce una stringa di caratteri, convertendo tutti i caratteri maiuscoli nei rispettivi equivalenti minuscoli. La funzione stringa ANSI SQL LOWER esegue la stessa operazione, pertanto l'istruzione SQL seguente è un ANSI equivalente all'istruzione ODBC presentata in precedenza:

```
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB elabora correttamente entrambe le versioni dell'istruzione quando vengono specificate come testo di un comando.

## <a name="stored-procedures"></a>Stored procedure
 Quando si esegue un Server SQL stored procedure tramite un comando SQLOLEDB, è possibile utilizzare la sequenza di escape ODBC routine chiamata nel testo del comando. SQLOLEDB utilizza quindi il meccanismo di chiamata di procedura remota di SQL Server per ottimizzare l'elaborazione del comando. Ad esempio, l'istruzione ODBC SQL seguente è il testo del comando preferito su un modulo Transact-SQL:

## <a name="odbc-sql"></a>ODBC SQL

```
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>Funzionalità di SQL Server
 Con SQL Server, ADO possa usare XML per **comando** immettere e recuperare i risultati in formato flusso XML anziché in **Recordset** oggetti. Per ulteriori informazioni, vedere [tramite flussi di Input del comando](../../../ado/guide/data/command-streams.md) e [il recupero dei set di risultati in flussi](../../../ado/guide/data/retrieving-resultsets-into-streams.md).

### <a name="accessing-sqlvariant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>Accesso ai dati di tipo sql_variant con MDAC 2.7, MDAC 2.8 o Windows DAC 6.0
 Microsoft SQL Server è un tipo di dati denominato **sql_variant**. Simile a OLE DB **DBTYPE_VARIANT**, **sql_variant** tipo di dati può archiviare i dati di tipi diversi. Tuttavia, esistono alcune differenze principali tra **DBTYPE_VARIANT** e **sql_variant**. ADO gestisce anche i dati archiviati come un **sql_variant** valore in modo diverso rispetto alla modalità di gestione di altri tipi di dati. Nell'elenco seguente vengono descritti i problemi da prendere in considerazione quando si accede di dati di SQL Server archiviati in colonne di tipo **sql_variant**.

-   In MDAC 2.7, MDAC 2.8 e Windows Data Access Components (Windows DAC) 6.0, il Provider OLE DB per SQL Server supporta il **sql_variant** tipo. Non è il Provider OLE DB per ODBC.

-   Il **sql_variant** tipo corrisponde esattamente il **DBTYPE_VARIANT** tipo di dati.  Il **sql_variant** tipo supporta alcuni nuovi sottotipi non è supportati da **DBTYPE_VARIANT,** inclusi **GUID**, **ANSI** (non-UNICODE) le stringhe, e **BIGINT**. Usando i sottotipi diverso da quelli elencati in precedenza funzionerà correttamente.

-   Il **sql_variant** sottotipo **numerico** non corrisponde la **DBTYPE_DECIMAL** dimensioni.

-   Coercizioni dei tipi di dati più comporterà tipi che non corrispondono. Ad esempio, la coercizione di un **sql_variant** con un sottotipo di **GUID** per un **DBTYPE_VARIANT** comporterà un sottotipo di **safearray**(byte) . Conversione di questo tipo di backup per un **sql_variant** comporterà un sottotipo del nuovo **matrice**(byte).

-   **Recordset** campi che contengono **sql_variant** dati possono essere eseguita in modalità remota (il marshalling) o persistente solo se il **sql_variant** contiene sottotipi specifici. Il tentativo di remoto o rendere persistenti i dati con il codice seguente non supportato sottotipi causerà un errore di run-time (conversione non supportata) dal Provider di persistenza (MSPersist) di Microsoft: **VT_VARIANT**, **VT_RECORD**, **VT_ILLEGAL**, **VT_UNKNOWN**, **VT_BSTR**, e **VT_DISPATCH.**

-   Il Provider OLE DB per SQL Server in MDAC 2.7, MDAC 2.8 e 6.0 di applicazione livello dati di Windows ha una proprietà dinamica denominata **consentire Native varianti** , come suggerisce il nome, consentendo agli sviluppatori di accedere il **sql_variant** in il modulo nativo anziché un **DBTYPE_VARIANT**. Se questa proprietà è impostata e un **Recordset** viene aperto con Client Cursor Engine (**adUseClient**), il **Open** chiamata avrà esito negativo. Se questa proprietà è impostata e un **Recordset** viene aperto con i cursori del server (**adUseServer**), il **Open** chiamata avrà esito positivo, ma che accedono a colonne di tipo **sql_variant** genererà un errore.

-   Nelle applicazioni client che utilizzano MDAC 2.5, **sql_variant** dati possono essere utilizzati con le query in Microsoft SQL Server. Tuttavia, i valori del **sql_variant** dati vengono considerati come stringhe. Le applicazioni client devono essere aggiornate a Windows DAC 6.0, MDAC 2.8 o MDAC 2.7.

## <a name="recordset-behavior"></a>Comportamento di recordset
 SQLOLEDB non è possibile utilizzare i cursori di SQL Server per supportare più risultati generati da molti comandi. Se un consumer richiede un recordset che richiedono il supporto di cursore di SQL Server, si verifica un errore se il testo del comando utilizzato genera più di un recordset singolo come risultato.

 Recordset SQLOLEDB scorrevole sono supportati dai cursori di SQL Server. SQL Server impone limitazioni sui cursori sensibili alle modifiche apportate da altri utenti del database. In particolare, non è possibile ordinare le righe in alcuni cursori e il tentativo di creazione di un recordset tramite un comando contenente una clausola SQL ORDER BY può avere esito negativo.

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Il Provider Microsoft OLE DB per SQL Server inserisce numerose proprietà dinamiche nel **proprietà** raccolta di oggetti [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e [ Comando](../../../ado/reference/ado-api/command-object-ado.md) oggetti.

 Le tabelle seguenti sono un incrociato dei nomi ADO e OLE DB per ogni proprietà dinamica. Riferimento di OLE DB Programmer fa riferimento a un nome della proprietà ADO il termine "Descrizione". È possibile trovare ulteriori informazioni su queste proprietà in riferimento OLE DB Programmer. Cercare il nome della proprietà OLE DB nell'indice oppure vedere [appendice c: OLE DB proprietà](http://msdn.microsoft.com/en-us/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Proprietà di connessione dinamica
 Vengono aggiunte le seguenti proprietà per il **proprietà** insieme il **connessione** oggetto.

|Nome della proprietà ADO|Nome della proprietà OLE DB|
|-----------------------|--------------------------|
|Sessioni attive|DBPROP_ACTIVESESSIONS|
|Interruzione asincrona|DBPROP_ASYNCTXNABORT|
|Commit Asynchable|DBPROP_ASYNCTNXCOMMIT|
|Livelli di isolamento autocommit|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Percorso del catalogo|DBPROP_CATALOGLOCATION|
|Termine catalogo|DBPROP_CATALOGTERM|
|Definizione di colonna|DBPROP_COLUMNDEFINITION|
|Timeout di connessione|DBPROP_INIT_TIMEOUT|
|Catalogo corrente|DBPROP_CURRENTCATALOG|
|origine dati|DBPROP_INIT_DATASOURCE|
|Nome origine dati|VALORE DBPROP_DATASOURCENAME|
|Modello di Threading oggetto origine dei dati|DBPROP_DSOTHREADMODEL|
|Nome DBMS|DBPROP_DBMSNAME|
|Versione DBMS|DBPROP_DBMSVER|
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|
|GRUPPO di assistenza|DBPROP_GROUPBY|
|Supporto tabelle eterogenee|DBPROP_HETEROGENEOUSTABLES|
|Identificatore distinzione maiuscole/minuscole|DBPROP_IDENTIFIERCASE|
|Catalogo iniziale|DBPROP_INIT_CATALOG|
|Livelli di isolamento|DBPROP_SUPPORTEDTXNISOLEVELS|
|Memorizzazione di isolamento|DBPROP_SUPPORTEDTXNISORETAIN|
|Locale Identifier|DBPROP_INIT_LCID|
|Dimensione massima dell'indice|DBPROP_MAXINDEXSIZE|
|Dimensioni massime delle righe|DBPROP_MAXROWSIZE|
|Dimensioni massime riga con BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Numero massimo di tabelle in SELECT|DBPROP_MAXTABLESINSELECT|
|Più set di parametri|DBPROP_MULTIPLEPARAMSETS|
|Più risultati|DBPROP_MULTIPLERESULTS|
|Più oggetti di archiviazione|DBPROP_MULTIPLESTORAGEOBJECTS|
|Aggiornamento di più tabelle|DBPROP_MULTITABLEUPDATE|
|Ordine delle regole di confronto NULL|DBPROP_NULLCOLLATION|
|Comportamento di concatenazione NULL|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB versione|DBPROP_PROVIDEROLEDBVER|
|Supporto dell'oggetto OLE|DBPROP_OLEOBJECTS|
|Aprire il supporto di set di righe|DBPROP_OPENROWSETSUPPORT|
|Colonne ORDER BY nell'elenco di selezione|DBPROP_ORDERBYCOLUMNSINSELECT|
|Disponibilità dei parametri di output|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Passare dalle funzioni di accesso di riferimento|DBPROP_BYREFACCESSORS|
|Password|DBPROP_AUTH_PASSWORD|
|Persist Security Info|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
|Tipo di ID persistenti|DBPROP_PERSISTENTIDTYPE|
|Preparare il comportamento di interruzione|DBPROP_PREPAREABORTBEHAVIOR|
|Preparare il comportamento di Commit|DBPROP_PREPARECOMMITBEHAVIOR|
|Termine procedura|DBPROP_PROCEDURETERM|
|Messaggio di richiesta|DBPROP_INIT_PROMPT|
|Nome descrittivo del provider|DBPROP_PROVIDERFRIENDLYNAME|
|Provider Name|DBPROP_PROVIDERFILENAME|
|Versione del provider|DBPROP_PROVIDERVER|
|Origine dati di sola lettura|DBPROP_DATASOURCEREADONLY|
|Conversioni di set di righe nel comando|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|Termine schema|DBPROP_SCHEMATERM|
|Utilizzo dello schema|DBPROP_SCHEMAUSAGE|
|Supporto di SQL|DBPROP_SQLSUPPORT|
|Archiviazione strutturata|DBPROP_STRUCTUREDSTORAGE|
|Supporto delle sottoquery|DBPROP_SUBQUERIES|
|Termine di una tabella|DBPROP_TABLETERM|
|Transazione DDL|DBPROP_SUPPORTEDTXNDDL|
|ID utente|DBPROP_AUTH_USERID|
|Nome utente|DBPROP_USERNAME|
|Handle di finestra|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>Proprietà dinamiche dell'oggetto Recordset
 Vengono aggiunte le seguenti proprietà per il **proprietà** insieme il **Recordset** oggetto.

|Nome della proprietà ADO|Nome della proprietà OLE DB|
|-----------------------|--------------------------|
|Ordine di accesso|DBPROP_ACCESSORDER|
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|
|Supporta|DBPROP_IROWSETLOCATE|
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|
|Timeout del comando|DBPROP_COMMANDTIMEOUT|
|Rinviare colonna|DBPROP_DEFERRED|
|Aggiornamenti degli oggetti di archiviazione di ritardo|DBPROP_DELAYSTORAGEOBJECTS|
|Recuperare le versioni precedenti|DBPROP_CANFETCHBACKWARDS|
|Contengono righe|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Righe immobili|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Valore letterale segnalibri|DBPROP_LITERALBOOKMARKS|
|Identità riga letterale|DBPROP_LITERALIDENTITY|
|Numero massimo di righe aperto|DBPROP_MAXOPENROWS|
|Numero massimo di righe in sospeso|DBPROP_MAXPENDINGROWS|
|Numero massimo di righe|DBPROP_MAXROWS|
|Granularità di notifica|DBPROP_NOTIFICATIONGRANULARITY|
|Fasi di notifica|DBPROP_NOTIFICATIONPHASES|
|Oggetti transazione|DBPROP_TRANSACTEDOBJECT|
|Modifiche di altri utenti visibili|DBPROP_OTHERUPDATEDELETE|
|Inserimenti altrui visibili|DBPROP_OTHERINSERT|
|Proprie modifiche visibili|DBPROP_OWNUPDATEDELETE|
|Inserimenti visibili|DBPROP_OWNINSERT|
|Mantieni in caso di interruzione|DBPROP_ABORTPRESERVE|
|Mantieni in caso di Commit|DBPROP_COMMITPRESERVE|
|Riavvio rapido|DBPROP_QUICKRESTART|
|Eventi rientranti|DBPROP_REENTRANTEVENTS|
|Rimuovere le righe eliminate|DBPROP_REMOVEDELETED|
|Più modifiche del report|DBPROP_REPORTMULTIPLECHANGES|
|Restituisci inserimenti in sospeso|DBPROP_RETURNPENDINGINSERTS|
|Notifica di eliminazione riga|DBPROP_NOTIFYROWDELETE|
|Notifica prima modifica riga|DBPROP_NOTIFYROWFIRSTCHANGE|
|Notifica inserimento riga|DBPROP_NOTIFYROWINSERT|
|Privilegi di riga|DBPROP_ROWRESTRICT|
|Notifica di risincronizzazione di riga|DBPROP_NOTIFYROWRESYNCH|
|Modello di Threading di riga|DBPROP_ROWTHREADMODEL|
|Notifica annullamento Modifica riga|DBPROP_NOTIFYROWUNDOCHANGE|
|Notifica annullamento eliminazione riga|DBPROP_NOTIFYROWUNDODELETE|
|Notifica annullamento inserimento riga|DBPROP_NOTIFYROWUNDOINSERT|
|Notifica di aggiornamento di riga|DBPROP_NOTIFYROWUPDATE|
|Notifica modifica posizione recupero di set di righe|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Notifica il rilascio di set di righe|DBPROP_NOTIFYROWSETRELEASE|
|Scorrere in senso inverso|DBPROP_CANSCROLLBACKWARDS|
|Cursore del server|DBPROP_SERVERCURSOR|
|Ignora segnalibri eliminati|DBPROP_BOOKMARKSKIPPED|
|Identità riga forte|DBPROP_STRONGITDENTITY|
|Righe univoche|DBPROP_UNIQUEROWS|
|Aggiornabile|DBPROP_UPDATABILITY|
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Proprietà dinamiche di comando
 Vengono aggiunte le seguenti proprietà per il **proprietà** insieme il **comando** oggetto.

|Nome della proprietà ADO|Nome della proprietà OLE DB|
|-----------------------|--------------------------|
|Ordine di accesso|DBPROP_ACCESSORDER|
|Percorso di base|SSPROP_STREAM_BASEPATH|
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|
|Supporta|DBPROP_IROWSETLOCATE|
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|
|Tipo di contenuto|SSPROP_STREAM_CONTENTTYPE|
|Recupero automatico di cursore|SSPROP_CURSORAUTOFETCH|
|Rinviare colonna|DBPROP_DEFERRED|
|Posticipa comandi prepare|SSPROP_DEFERPREPARE|
|Aggiornamenti degli oggetti di archiviazione di ritardo|DBPROP_DELAYSTORAGEOBJECTS|
|Recuperare le versioni precedenti|DBPROP_CANFETCHBACKWARDS|
|Contengono righe|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Righe immobili|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch|DBPROP_IRowsetResynch|
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Valore letterale segnalibri|DBPROP_LITERALBOOKMARKS|
|Identità riga letterale|DBPROP_LITERALIDENTITY|
|Modalità di blocco|DBPROP_LOCKMODE|
|Numero massimo di righe aperto|DBPROP_MAXOPENROWS|
|Numero massimo di righe in sospeso|DBPROP_MAXPENDINGROWS|
|Numero massimo di righe|DBPROP_MAXROWS|
|Granularità di notifica|DBPROP_NOTIFICATIONGRANULARITY|
|Fasi di notifica|DBPROP_NOTIFICATIONPHASES|
|Oggetti transazione|DBPROP_TRANSACTEDOBJECT|
|Modifiche di altri utenti visibili|DBPROP_OTHERUPDATEDELETE|
|Inserimenti altrui visibili|DBPROP_OTHERINSERT|
|Proprietà di codifica di output|DBPROP_OUTPUTENCODING|
|Proprietà del flusso di output|DBPROP_OUTPUTSTREAM|
|Proprie modifiche visibili|DBPROP_OWNUPDATEDELETE|
|Inserimenti visibili|DBPROP_OWNINSERT|
|Mantieni in caso di interruzione|DBPROP_ABORTPRESERVE|
|Mantieni in caso di Commit|DBPROP_COMMITPRESERVE|
|Riavvio rapido|DBPROP_QUICKRESTART|
|Eventi rientranti|DBPROP_REENTRANTEVENTS|
|Rimuovere le righe eliminate|DBPROP_REMOVEDELETED|
|Più modifiche del report|DBPROP_REPORTMULTIPLECHANGES|
|Restituisci inserimenti in sospeso|DBPROP_RETURNPENDINGINSERTS|
|Notifica di eliminazione riga|DBPROP_NOTIFYROWDELETE|
|Notifica prima modifica riga|DBPROP_NOTIFYROWFIRSTCHANGE|
|Notifica inserimento riga|DBPROP_NOTIFYROWINSERT|
|Privilegi di riga|DBPROP_ROWRESTRICT|
|Notifica di risincronizzazione di riga|DBPROP_NOTIFYROWRESYNCH|
|Modello di Threading di riga|DBPROP_ROWTHREADMODEL|
|Notifica annullamento Modifica riga|DBPROP_NOTIFYROWUNDOCHANGE|
|Notifica annullamento eliminazione riga|DBPROP_NOTIFYROWUNDODELETE|
|Notifica annullamento inserimento riga|DBPROP_NOTIFYROWUNDOINSERT|
|Notifica di aggiornamento di riga|DBPROP_NOTIFYROWUPDATE|
|Notifica modifica posizione recupero di set di righe|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|
|Notifica il rilascio di set di righe|DBPROP_NOTIFYROWSETRELEASE|
|Scorrere in senso inverso|DBPROP_CANSCROLLBACKWARDS|
|Cursore del server|DBPROP_SERVERCURSOR|
|Dati server all'inserimento|DBPROP_SERVERDATAONINSERT|
|Ignora segnalibri eliminati|DBPROP_BOOKMARKSKIP|
|Identità riga forte|DBPROP_STRONGIDENTITY|
|Aggiornabile|DBPROP_UPDATABILITY|
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|
|Radice XML|SSPROP_STREAM_XMLROOT|
|XSL|SSPROP_STREAM_XSL|

 Per dettagli specifici sull'implementazione e informazioni funzionale il Provider OLE DB Microsoft SQL Server, vedere il [Provider per SQL Server](http://msdn.microsoft.com/en-us/adf1d6c4-5930-444a-9248-ff1979729635).

## <a name="see-also"></a>Vedere anche
 [Proprietà ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [proprietà Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
