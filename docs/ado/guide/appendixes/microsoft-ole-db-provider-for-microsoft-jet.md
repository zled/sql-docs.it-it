---
title: Provider Microsoft OLE DB per Microsoft Jet | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet provider for OLE DB [ADO]
- providers [ADO], OLE DB provider for Microsoft Jet
- OLE DB provider for Microsoft Jet [ADO]
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 253de8c53055269efb6a9e15c9d9a5ca940606e8
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Provider Microsoft OLE DB per Microsoft Jet Panoramica
Il Provider OLE DB per Microsoft Jet consente ADO per accedere ai database Microsoft Jet.

## <a name="connection-string-parameters"></a>Parametri di stringa di connessione
 Per connettersi a questo provider, impostare il *Provider* argomento del [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà per le operazioni seguenti:

```
Microsoft.Jet.OLEDB.4.0
```

 Lettura di [Provider](../../../ado/reference/ado-api/provider-property-ado.md) restituirà anche questa stringa.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il Provider OLE DB per Microsoft Jet.|
|**Data Source**|Specifica il percorso e il nome del database (ad esempio, `c:\Northwind.mdb`).|
|**ID utente**|Specifica il nome utente. Se questa parola chiave non è specificata, la stringa "`admin`", viene utilizzato per impostazione predefinita.|
|**Password**|Specifica la password dell'utente. Se questa parola chiave non è specificata, una stringa vuota (""), viene utilizzato per impostazione predefinita.|

> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** o **Integrated Security = SSPI** anziché l'ID utente e password informazioni nella stringa di connessione.

## <a name="provider-specific-connection-parameters"></a>Parametri di connessione specifica del provider
 Il Provider OLE DB per Microsoft Jet supporta varie proprietà dinamiche specifiche del provider oltre a quelli che sono definiti da ADO. Come con tutti gli altri **connessione** parametri, è possibile impostare utilizzando il **proprietà** insieme il **connessione** oggetto o come parte della stringa di connessione.

 Nella tabella seguente sono elencate queste proprietà insieme al nome di proprietà OLE DB corrispondente tra parentesi.

|Parametro|Description|
|---------------|-----------------|
|Quantità di spazio recuperato OLEDB:Compact Jet (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|Indica una stima della quantità di spazio, espressa in byte, che può essere recuperato dalla compressione del database. Questo valore è valido solo dopo aver stabilita una connessione al database.|
|Controllo OLEDB:Connection Jet (DBPROP_JETOLEDB_CONNECTIONCONTROL)|Indica se gli utenti possono connettersi al database.|
|Jet OLEDB: creare il Database di sistema (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)|Indica se è necessario creare un database di sistema quando si crea una nuova origine dati.|
|Jet OLEDB: database la modalità di blocco (DBPROP_JETOLEDB_DATABASELOCKMODE)|Indica la modalità di blocco per il database. Il primo utente ad aprire il database determina la modalità utilizzata, mentre il database è aperto.|
|Jet OLEDB: database Password (DBPROP_JETOLEDB_DATABASEPASSWORD)|Indica la password del database.|
|Jet OLEDB: non copia delle impostazioni locali in Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)|Indica se Jet deve copiare informazioni sulle impostazioni locali quando si compatta un database.|
|Jet OLEDB: crittografare il Database (DBPROP_JETOLEDB_ENCRYPTDATABASE)|Indica se un database compattato deve essere crittografato. Se questa proprietà non è impostata, il database compattato verrà crittografato se il database originale è stato inoltre crittografato.|
|Tipo OLEDB:Engine Jet (DBPROP_JETOLEDB_ENGINE)|Indica il motore di archiviazione utilizzato per accedere all'archivio dati corrente.|
|Jet OLEDB:Exclusive Async ritardo (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|Indica la lunghezza massima di tempo, espresso in millisecondi, che Jet possono ritardare scritture asincrone sul disco quando il database è aperto in modalità esclusiva.<br /><br /> Questa proprietà viene ignorata a meno che non **Jet OLEDB: Flush Transaction Timeout** è impostato su 0.|
|Timeout della transazione Jet OLEDB: Flush (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|Indica la quantità di tempo di attesa prima che i dati archiviati in una cache per la scrittura asincrona vengano effettivamente scritti su disco. Questa impostazione sostituisce i valori per **Jet OLEDB: condiviso ritardo Async** e **Jet OLEDB:Exclusive Async ritardo**.|
|Jet OLEDB: le transazioni di blocco globale (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|Indica se le transazioni di blocco SQL vengono eseguite.|
|Jet OLEDB: Ops globale Bulk parziale (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|Indica la password utilizzata per aprire il database.|
|Jet OLEDB: sincronizzazione di Commit implicito (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|Indica se le modifiche apportate in transazioni implicite interne vengono scritti in modalità sincrona o asincrona.|
|Jet OLEDB:Lock ritardo (DBPROP_JETOLEDB_LOCKDELAY)|Indica il numero di millisecondi di attesa prima del tentativo di acquisire un blocco dopo un precedente tentativo non riuscito.|
|Jet OLEDB:Lock tentativi (DBPROP_JETOLEDB_LOCKRETRY)|Indica quante volte viene ripetuto un tentativo di accedere a una pagina bloccata.|
|Dimensione del Buffer di Jet OLEDB:Max (DBPROP_JETOLEDB_MAXBUFFERSIZE)|Indica la quantità massima di memoria, espressa in kilobyte, Jet consente prima di iniziare a scaricare le modifiche su disco.|
|Jet OLEDB:Max blocchi per ogni File (DBPROP_JETOLEDB_MAXLOCKSPERFILE)|Indica il numero massimo di blocchi che Jet è possibile inserire in un database. Il valore predefinito è 9500.|
|Jet OLEDB: nuova Password del Database (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|Indica la nuova password da impostare per questo database. La vecchia password viene archiviata **Jet OLEDB: database Password**.|
|Timeout del comando di Jet OLEDB (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Indica che il numero di millisecondi prima che una query ODBC remota da Jet scadrà.|
|Jet OLEDB:Page blocchi di blocco di tabella (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Indica il numero di pagine deve essere bloccato all'interno di una transazione prima di Jet tenta di alzare di livello il blocco di un blocco di tabella. Se questo valore è 0, il blocco non viene promossa mai.|
|Timeout OLEDB:Page Jet (DBPROP_JETOLEDB_PAGETIMEOUT)|Indica il numero di millisecondi di che attesa prima di un controllo per verificare se la cache non è aggiornato con il file di database Jet.|
|Jet OLEDB:Recycle Long con valori di pagine (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Indica se Jet in modo aggressivo deve tentare di recuperare le pagine BLOB quando vengono liberati.|
|Percorso OLEDB:Registry Jet (DBPROP_JETOLEDB_REGPATH)|Indica la chiave del Registro di sistema di Windows che contiene i valori per il motore di database Jet.|
|Jet OLEDB:Reset ISAM statistiche (DBPROP_JETOLEDB_RESETISAMSTATS)|Indica se lo schema **Recordset** DBSCHEMA_JETOLEDB_ISAMSTATS deve reimpostare i contatori di prestazioni dopo la restituzione di informazioni sulle prestazioni.|
|Jet OLEDB: condiviso ritardo Async (DBPROP_JETOLEDB_SHAREDASYNCDELAY)|Indica la quantità massima di tempo, espresso in millisecondi, Jet può posticipare le scritture asincrone su disco quando il database è aperto in modalità multiutente.|
|Database di sistema OLEDB Jet (DBPROP_JETOLEDB_SYSDBPATH)|Indica il percorso e il nome per il file di informazioni sul gruppo di lavoro (database di sistema).|
|Modalità di Commit OLEDB:Transaction Jet (DBPROP_JETOLEDB_TXNCOMMITMODE)|Indica se Jet scrive dati su disco in modo sincrono o asincrono quando una transazione viene eseguito il commit.|
|Sincronizzazione di Commit OLEDB:User Jet (DBPROP_JETOLEDB_USERCOMMITSYNC)|Indica se le modifiche apportate nelle transazioni vengono scritte in modalità sincrona o asincrona.|

## <a name="provider-specific-recordset-and-command-properties"></a>Recordset specifico del provider e le proprietà dei comandi
 Il provider Jet supporta anche diverse specifiche del provider **Recordset** e **comando** proprietà. Queste proprietà sono accessibili e impostate tramite il **proprietà** insieme il **Recordset** o **comando** oggetto. Nella tabella sono elencati il nome della proprietà ADO e il relativo nome di proprietà OLE DB corrispondente tra parentesi.

|Nome proprietà|Description|
|-------------------|-----------------|
|Transazioni OLEDB:Bulk Jet (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|Indica se vengono eseguite operazioni bulk SQL. Le operazioni bulk di grandi dimensioni potrebbero non riuscire quando supporta le transazioni, a causa di ritardi di risorse.|
|Il parametro Jet Fat Cursors (DBPROP_JETOLEDB_ENABLEFATCURSOR)|Indica se Jet deve memorizzare nella cache di più righe durante la compilazione di un recordset per origini riga remote.|
|Dimensione della Cache di cursore OLEDB:Fat Jet (DBPROP_JETOLEDB_FATCURSORMAXROWS)|Indica il numero di righe da memorizzare nella cache quando si utilizza la memorizzazione nella cache riga archivio dati remoti. Questo valore viene ignorato a meno che non **Jet Enable Fat Cursors** è True.|
|Jet OLEDB: incoerenti (DBPROP_JETOLEDB_INCONSISTENT)|Indica se i risultati di query consentono aggiornamenti non consistenti.|
|Jet OLEDB: blocco granularità (DBPROP_JETOLEDB_LOCKGRANULARITY)|Indica se una tabella viene aperto con blocco a livello di riga.|
|Istruzione pass-through di Jet OLEDB (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Indica che Jet deve passare il testo SQL in un **comando** oggetto al back-end senza modificata.|
|Jet OLEDB:Partial Bulk Operations (DBPROP_JETOLEDB_BULKPARTIAL)|Indica il comportamento di Jet quando operazioni DML SQL hanno esito negativo.|
|Jet OLEDB:Pass tramite Query Bulk-Op (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)|Indica se le query che non restituiscono un **Recordset** vengono passate all'origine dati senza modifiche.|
|(DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING) di stringa di connessione di Jet OLEDB:Pass tramite Query|Indica la stringa di connessione Jet utilizzata per connettersi a un archivio dati remoto. Questo valore viene ignorato a meno che non **Jet OLEDB pass-through Statement** è True.|
|Jet OLEDB: archiviati Query (DBPROP_JETOLEDB_STOREDQUERY)|Indica se il testo del comando deve essere interpretato come una query archiviata anziché un comando SQL.|
|Jet OLEDB: convalidare le regole nel Set (DBPROP_JETOLEDB_VALIDATEONSET)|Indica se le regole di convalida di Jet vengono valutate quando i dati della colonna sono impostati o quando le modifiche vengono salvate nel database.|

 Per impostazione predefinita, il Provider OLE DB per Microsoft Jet apre database Microsoft Jet in modalità di lettura/scrittura. Per aprire un database in modalità di sola lettura, impostare il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà ADO **connessione** oggetto **adModeRead**.

## <a name="command-object-usage"></a>Utilizzo dell'oggetto Command
 Testo del comando di [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto utilizza il sottolinguaggio SQL di Microsoft Jet. È possibile specificare query che restituiscono righe, query e i nomi di tabella nel testo del comando; Tuttavia, le stored procedure non sono supportate e non devono essere specificate.

## <a name="recordset-behavior"></a>Comportamento di recordset
 Il motore di database Microsoft Jet non supporta i cursori dinamici. Pertanto, il Provider OLE DB per Microsoft Jet non supporta il **adLockDynamic** tipo di cursore. Quando viene richiesto un cursore dinamico, il provider restituisce un cursore keyset e reimposta il [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) proprietà per indicare il tipo di [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) restituito. Inoltre, se un aggiornabile **Recordset** richiesta (**LockType** è **adLockOptimistic**, **adLockBatchOptimistic**, o **adLockPessimistic**) il provider restituisce un cursore keyset e reimposta anche il **CursorType** proprietà.

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Il Provider OLE DB per Microsoft Jet inserisce varie proprietà dinamiche nel **proprietà** raccolta di oggetti [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e [Comando](../../../ado/reference/ado-api/command-object-ado.md) oggetti.

 Le tabelle seguenti sono un incrociato dei nomi ADO e OLE DB per ogni proprietà dinamica. Riferimento di OLE DB Programmer fa riferimento a un nome della proprietà ADO il termine, "Descrizione". È possibile trovare ulteriori informazioni su queste proprietà in riferimento OLE DB Programmer.

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
|Catalogo corrente|DBPROP_CURRENTCATALOG|
|Data Source|DBPROP_INIT_DATASOURCE|
|Nome origine dati|DBPROP_DATASOURCENAME|
|Modello di Threading oggetto origine dei dati|DBPROP_DSOTHREADMODEL|
|Nome DBMS|DBPROP_DBMSNAME|
|Versione DBMS|DBPROP_DBMSVER|
|GRUPPO di assistenza|DBPROP_GROUPBY|
|Supporto tabelle eterogenee|DBPROP_HETEROGENEOUSTABLES|
|Identificatore distinzione maiuscole/minuscole|DBPROP_IDENTIFIERCASE|
|Livelli di isolamento|DBPROP_SUPPORTEDTXNISOLEVELS|
|Memorizzazione di isolamento|DBPROP_SUPPORTEDTXNISORETAIN|
|Locale Identifier|DBPROP_INIT_LCID|
|Dimensione massima dell'indice|DBPROP_MAXINDEXSIZE|
|Dimensioni massime delle righe|DBPROP_MAXROWSIZE|
|Dimensioni massime riga con BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Numero massimo di tabelle in SELECT|DBPROP_MAXTABLESINSELECT|
|Elabora partizione/i|DBPROP_INIT_MODE|
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
|Set di righe solo di Accodamento|DBPROP_APPENDONLY|
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|
|Supporta|DBPROP_IROWSETLOCATE|
|Segnalibri ordinati|DBPROP_ORDEREDBOOKMARKS|
|Memorizzare nella cache colonne posticipate|DBPROP_CACHEDEFERRED|
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|
|Colonna accessibile in scrittura|DBPROP_MAYWRITECOLUMN|
|Rinviare colonna|DBPROP_DEFERRED|
|Aggiornamenti degli oggetti di archiviazione di ritardo|DBPROP_DELAYSTORAGEOBJECTS|
|Recuperare le versioni precedenti|DBPROP_CANFETCHBACKWARDS|
|Contengono righe|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Righe immobili|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Valore letterale segnalibri|DBPROP_LITERALBOOKMARKS|
|Identità riga letterale|DBPROP_LITERALIDENTITY|
|Numero massimo di righe aperto|DBPROP_MAXOPENROWS|
|Numero massimo di righe in sospeso|DBPROP_MAXPENDINGROWS|
|Numero massimo di righe|DBPROP_MAXROWS|
|Utilizzo memoria|DBPROP_MEMORYUSAGE|
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
|Ignora segnalibri eliminati|DBPROP_BOOKMARKSKIPPED|
|Identità riga forte|DBPROP_STRONGITDENTITY|
|Aggiornabile|DBPROP_UPDATABILITY|
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Proprietà dinamiche di comando
 Vengono aggiunte le seguenti proprietà per il **proprietà** insieme il **comando** oggetto.

|Nome della proprietà ADO|Nome della proprietà OLE DB|
|-----------------------|--------------------------|
|Ordine di accesso|DBPROP_ACCESSORDER|
|Set di righe solo di Accodamento|DBPROP_APPENDONLY|
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|
|Supporta|DBPROP_IROWSETLOCATE|
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|
|Rinviare colonna|DBPROP_DEFERRED|
|Aggiornamenti degli oggetti di archiviazione di ritardo|DBPROP_DELAYSTORAGEOBJECTS|
|Recuperare le versioni precedenti|DBPROP_CANFETCHBACKWARDS|
|Contengono righe|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Righe immobili|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
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
|Dati server all'inserimento|DBPROP_SERVERDATAONINSERT|
|Ignora segnalibri eliminati|DBPROP_BOOKMARKSKIP|
|Identità riga forte|DBPROP_STRONGIDENTITY|
|Aggiornabile|DBPROP_UPDATABILITY|
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|

 Per dettagli specifici sull'implementazione e di funzionalità relative al Provider OLE DB per Microsoft Jet, vedere [Provider Jet](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) nella documentazione di OLE DB.
