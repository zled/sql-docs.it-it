---
title: Provider Microsoft OLE DB per ODBC | Documenti Microsoft
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
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 44f3131bff34d35b334495c7c718eb513f5d88bf
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Provider Microsoft OLE DB per ODBC Panoramica
Per un programmatore di ADO o RDS, un mondo ideale sarebbe uno in cui ogni tipo di dati origine espone un'interfaccia OLE DB, in modo che ADO è possibile chiamare direttamente nell'origine dati. Anche se un numero sempre maggiore di fornitori di database siano implementando le interfacce OLE DB, alcune origini dati non sono ancora esposte in questo modo. Tuttavia, è possano accedere la maggior parte dei sistemi DBMS attualmente in uso tramite ODBC.

 Driver ODBC sono disponibili per i principali DBMS in uso oggi, tra cui Microsoft SQL Server, Microsoft Access (motore di database Microsoft Jet) e Microsoft FoxPro, oltre ai prodotti del database non Microsoft, ad esempio Oracle.

 Il Provider ODBC di Microsoft, tuttavia, consente di ADO per connettersi a qualsiasi origine dati ODBC. Il provider è a thread libero e abilitato per Unicode.

 Il provider supporta le transazioni, anche se diversi motori di DBMS offrono diversi tipi di supporto delle transazioni. Ad esempio, Microsoft Access supporta transazioni nidificate fino a cinque livelli.

 Questo è il provider predefinito per ADO e sono supportati tutti i metodi e proprietà ADO dipende dal provider.

## <a name="connection-string-parameters"></a>Parametri di stringa di connessione
 Per connettersi a questo provider, impostare il **Provider =** argomento del [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà:

```
MSDASQL
```

 Lettura di [Provider](../../../ado/reference/ado-api/provider-property-ado.md) restituirà anche questa stringa.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il provider OLE DB per ODBC.|
|**DSN**|Specifica il nome dell'origine dati.|
|**UID**|Specifica il nome utente.|
|**PWD**|Specifica la password dell'utente.|
|**URL**|Specifica l'URL di un file o directory pubblicati in una cartella Web.|

 Poiché si tratta del provider predefinito per ADO, se si omette il **Provider =** parametro dalla stringa di connessione, ADO tenterà di stabilire una connessione al provider.

> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** o **Integrated Security = SSPI** anziché l'ID utente e password informazioni nella stringa di connessione.

 Il provider non supporta parametri di connessione specifici oltre a quelli definiti da ADO. Tuttavia, il provider passerà eventuali parametri di connessione non ADO a Gestione driver ODBC.

 Poiché è possibile omettere il **Provider** parametro, pertanto è possibile comporre una stringa di connessione ADO è identica alla stringa di connessione ODBC per la stessa origine dati. Utilizzare gli stessi nomi di parametro (**DRIVER =**, **DATABASE =**, **DSN =**e così via), i valori e la stessa sintassi è valida per la composizione di una stringa di connessione ODBC. È possibile connettersi con o senza un nome di origine di dati predefiniti (DSN) o FileDSN.

## <a name="syntax-with-a-dsn-or-filedsn"></a>Sintassi con un DSN o FileDSN:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>Sintassi senza un DSN (connessione senza DSN):

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>Osservazioni
 Se si utilizza un **DSN** o **FileDSN**, deve essere definita tramite Amministrazione origine dati ODBC nel Pannello di controllo di Windows. In Microsoft Windows 2000, l'amministratore ODBC si trova in strumenti di amministrazione. Nelle versioni precedenti di Windows, l'icona del ruolo Amministratore ODBC è denominata **ODBC a 32 bit** o semplicemente **ODBC**.

 In alternativa all'impostazione un **DSN**, è possibile specificare il driver ODBC (**DRIVER =**), ad esempio "SQL Server"; il nome del server (**SERVER =**); e il nome del database (**DATABASE =**).

 È inoltre possibile specificare un nome di account utente (**UID =**) e la password per l'account utente (**PWD =**) nei parametri specifici di ODBC o nello standard definiti da ADO *utente* e *password* parametri.

 Sebbene un **DSN** già una definizione specifica un database, è possibile specificare *un* *database* parametro oltre a un **DSN** per la connessione per un database diverso. È buona norma includere sempre *il* *database* parametro quando si utilizza un **DSN**. In questo modo la connessione al database corretto se un altro utente il parametro predefinito del database dall'ultima ricerca di **DSN** definizione.

## <a name="provider-specific-connection-properties"></a>Proprietà di connessione specifica del provider
 Il provider OLE DB per ODBC aggiunge diverse proprietà per il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme il **connessione** oggetto. Nella tabella seguente sono elencate queste proprietà con il nome della proprietà OLE DB corrispondente tra parentesi.

|Nome proprietà|Description|
|-------------------|-----------------|
|Routine accessibili (KAGPROP_ACCESSIBLEPROCEDURES)|Indica se l'utente ha accesso alle stored procedure.|
|Tabelle accessibili (KAGPROP_ACCESSIBLETABLES)|Indica se l'utente dispone dell'autorizzazione per eseguire le istruzioni SELECT sulle tabelle del database.|
|Istruzioni attive (KAGPROP_ACTIVESTATEMENTS)|Indica il numero di handle che può supportare un driver ODBC in una connessione.|
|Nome del driver (KAGPROP_DRIVERNAME)|Indica il nome del file del driver ODBC.|
|Versione del driver ODBC (KAGPROP_DRIVERODBCVER)|Indica la versione di ODBC supportata dal driver.|
|Utilizzo di file (KAGPROP_FILEUSAGE)|Indica il modo in cui il driver considera un file in un'origine dati. come una tabella o come un catalogo.|
|Ad esempio la clausola Escape (KAGPROP_LIKEESCAPECLAUSE)|Indica se il driver supporta la definizione e utilizzo di un carattere di escape per la percentuale di caratteri (%) e il carattere di sottolineatura (_) nel predicato LIKE di una clausola WHERE.|
|Numero massimo di colonne in Group By (KAGPROP_MAXCOLUMNSINGROUPBY)|Indica il numero massimo di colonne che possono essere incluse nella clausola GROUP BY di un'istruzione SELECT.|
|Numero massimo di colonne nell'indice (KAGPROP_MAXCOLUMNSININDEX)|Indica il numero massimo di colonne che possono essere inclusi in un indice.|
|Numero massimo di colonne nella clausola Order By (KAGPROP_MAXCOLUMNSINORDERBY)|Indica il numero massimo di colonne che possono essere incluse nella clausola ORDER BY di un'istruzione SELECT.|
|Numero massimo di colonne nell'istruzione Select (KAGPROP_MAXCOLUMNSINSELECT)|Indica il numero massimo di colonne che possono essere incluse nella parte SELECT di un'istruzione SELECT.|
|Numero massimo di colonne nella tabella (KAGPROP_MAXCOLUMNSINTABLE)|Indica il numero massimo di colonne consentite in una tabella.|
|Funzioni numeriche (KAGPROP_NUMERICFUNCTIONS)|Indica quali funzioni numeriche sono supportate dal driver ODBC. Per un elenco di nomi di funzione e i valori associati utilizzati in questa maschera di bit, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), nella documentazione di ODBC.|
|Funzionalità di outer Join (KAGPROP_OJCAPABILITY)|Indica i tipi di OUTER join è supportata dal provider.|
|Outer join (KAGPROP_OUTERJOINS)|Indica se il provider supporta l'OUTER join.|
|Caratteri speciali (KAGPROP_SPECIALCHARACTERS)|Indica quali caratteri hanno un significato speciale per il driver ODBC.|
|Stored procedure (KAGPROP_PROCEDURES)|Indica se le stored procedure sono disponibili per l'utilizzo con il driver ODBC.|
|Funzioni stringa (KAGPROP_STRINGFUNCTIONS)|Indica le funzioni di stringa supportate dal driver ODBC. Per un elenco di nomi di funzione e i valori associati utilizzati in questa maschera di bit, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), nella documentazione di ODBC.|
|Funzioni di sistema (KAGPROP_SYSTEMFUNCTIONS)|Indica le funzioni di sistema supportate dal driver ODBC. Per un elenco di nomi di funzione e i valori associati utilizzati in questa maschera di bit, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), nella documentazione di ODBC.|
|Funzioni di data e ora (KAGPROP_TIMEDATEFUNCTIONS)|Indica quali funzioni di data e ora sono supportate dal driver ODBC. Per un elenco di nomi di funzione e i valori associati utilizzati in questa maschera di bit, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), nella documentazione di ODBC.|
|Supporto della grammatica SQL (KAGPROP_ODBCSQLCONFORMANCE)|Indica la grammatica SQL che supporta il driver ODBC.|

## <a name="provider-specific-recordset-and-command-properties"></a>Recordset specifico del provider e le proprietà dei comandi
 Il provider OLE DB per ODBC aggiunge diverse proprietà per il **proprietà** insieme il **Recordset** e **comando** oggetti. Nella tabella seguente sono elencate queste proprietà con il nome della proprietà OLE DB corrispondente tra parentesi.

|Nome proprietà|Description|
|-------------------|-----------------|
|Aggiornamenti/eliminazioni o inserimenti (KAGPROP_QUERYBASEDUPDATES) basati su query|Indica se è possano eseguire gli aggiornamenti, eliminazioni e inserimenti tramite query SQL.|
|Tipo di concorrenza ODBC (KAGPROP_CONCURRENCY)|Indica il metodo utilizzato per ridurre i potenziali problemi causati da due utenti che tentano di accedere contemporaneamente agli stessi dati dall'origine dati.|
|Accesso facilitato BLOB su cursore Forward-Only (KAGPROP_BLOBSONFOCURSOR)|Indica se BLOB **campi** accessibili quando si utilizza un cursore forward-only.|
|Includere SQL_FLOAT, SQL_DOUBLE e SQL_REAL in clausole QBU WHERE (KAGPROP_INCLUDENONEXACT)|Indica se i valori SQL_FLOAT, SQL_DOUBLE e SQL_REAL possono essere incluso in una clausola WHERE QBU.|
|Posizione sull'ultima riga dopo l'inserimento (KAGPROP_POSITIONONNEWROW)|Indica che, dopo aver inserito un nuovo record in una tabella, può essere l'ultima riga nella tabella la riga corrente.|
|IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)|Indica se il **IRowsetChange** interfaccia fornisce il supporto di informazioni estese.|
|Tipo di cursore ODBC (KAGPROP_CURSOR)|Indica il tipo di cursore utilizzato per il **Recordset**.|
|Generare un set di righe che è possibile effettuare il marshalling (KAGPROP_MARSHALLABLE)|Indica che il driver ODBC genera un oggetto recordset che è possibile effettuare il marshalling|

## <a name="command-text"></a>Testo comando
 L'utilizzo di [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto dipende in gran parte dall'origine dati e il tipo di query o istruzione di comando verranno accettate.

 ODBC fornisce una sintassi specifica per la chiamata di stored procedure. Per il [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà di un **comando** oggetto, il *CommandText* argomento per il **Execute** metodo su un [ Connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto, o *origine* argomento per il **aprire** metodo su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, passa una stringa con questa sintassi:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , … ]] ) ] }"
```

 Ogni **?** fa riferimento a un oggetto di [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme. Il primo **?** riferimenti **parametri**(0), alla successiva **?** riferimenti **parametri**(1), e così via.

 I parametri di riferimento sono facoltativi e dipendono dalla struttura della stored procedure. Se si desidera chiamare una stored procedure che non definisce alcun parametro, la stringa avrà un aspetto simile al seguente:

```
"{ call procedure }"
```

 Se si dispongono di due parametri di query, la stringa sarà simile alla seguente:

```
"{ call procedure ( ?, ? ) }"
```

 Se la stored procedure restituirà un valore, il valore restituito viene considerato come un altro parametro. Se non si dispone di alcun parametro di query, ma è un valore restituito, la stringa sarà simile alla seguente:

```
"{ ? = call procedure }"
```

 Infine, se si dispone di un valore restituito e due parametri di query, la stringa sarà simile alla seguente:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Comportamento di recordset
 Le tabelle seguenti elencano i metodi standard di ADO e le proprietà disponibili in un **Recordset** oggetto aperto con questo provider.

 Per informazioni dettagliate sui **Recordset** comportamento per la configurazione di provider, eseguire il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo ed enumerare il **proprietà** insieme del **Recordset** per determinare se sono presenti proprietà dinamiche specifiche del provider.

 Disponibilità di ADO standard **Recordset** proprietà:

|Proprietà|ForwardOnly|Dynamic|Keyset|Statico|
|--------------|-----------------|-------------|------------|------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|non disponibile|non disponibile|lettura/scrittura|lettura/scrittura|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|non disponibile|non disponibile|lettura/scrittura|lettura/scrittura|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Sola lettura|Sola lettura|Sola lettura|Sola lettura|
|[Segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md)|non disponibile|non disponibile|lettura/scrittura|lettura/scrittura|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|Sola lettura|Sola lettura|Sola lettura|Sola lettura|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[Tipo di blocco](../../../ado/reference/ado-api/locktype-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|lettura/scrittura|non disponibile|Sola lettura|Sola lettura|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|lettura/scrittura|non disponibile|Sola lettura|Sola lettura|
|[Origine](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lettura/scrittura|lettura/scrittura|lettura/scrittura|lettura/scrittura|
|[State](../../../ado/reference/ado-api/state-property-ado.md)|Sola lettura|Sola lettura|Sola lettura|Sola lettura|
|[Stato](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Sola lettura|Sola lettura|Sola lettura|Sola lettura|

 Il [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) e [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) proprietà sono di sola scrittura quando ADO viene utilizzato con la versione 1.0 del Provider Microsoft OLE DB per ODBC.

 Disponibilità di ADO standard **Recordset** metodi:

|Metodo|ForwardOnly|Dynamic|Keyset|Statico|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Sì|Sì|Sì|Sì|
|[Annulla](../../../ado/reference/ado-api/cancel-method-ado.md)|Sì|Sì|Sì|Sì|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Sì|Sì|Sì|Sì|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Sì|Sì|Sì|Sì|
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|no|no|Sì|Sì|
|[Chiudi](../../../ado/reference/ado-api/close-method-ado.md)|Sì|Sì|Sì|Sì|
|[Elimina](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Sì|Sì|Sì|Sì|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Sì|Sì|Sì|Sì|
|[Sposta](../../../ado/reference/ado-api/move-method-ado.md)|Sì|Sì|Sì|Sì|
|[Metodo MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|Sì|Sì|Sì|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|no|Sì|Sì|Sì|
|[Metodo MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|Sì|Sì|Sì|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|no|Sì|Sì|Sì|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|Sì|Sì|Sì|Sì|
|[Aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Sì|Sì|Sì|Sì|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Sì|Sì|Sì|Sì|
|[Risincronizzazione](../../../ado/reference/ado-api/resync-method.md)|no|no|Sì|Sì|
|[Supporta](../../../ado/reference/ado-api/supports-method.md)|Sì|Sì|Sì|Sì|
|[Update](../../../ado/reference/ado-api/update-method.md)|Sì|Sì|Sì|Sì|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Sì|Sì|Sì|Sì|

 * Non supportato per il database di Microsoft Access.

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Il Provider Microsoft OLE DB per ODBC inserisce varie proprietà dinamiche nel **proprietà** raccolta di oggetti [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e [Comando](../../../ado/reference/ado-api/command-object-ado.md) oggetti.

 Le tabelle seguenti sono un incrociato dei nomi ADO e OLE DB per ogni proprietà dinamica. Riferimento di OLE DB Programmer fa riferimento a un nome della proprietà ADO il termine, "Descrizione". È possibile trovare ulteriori informazioni su queste proprietà in riferimento OLE DB Programmer. Cercare il nome della proprietà OLE DB nell'indice oppure vedere [appendice c: OLE DB proprietà](http://msdn.microsoft.com/en-us/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Proprietà di connessione dinamica
 Le proprietà seguenti vengono aggiunti per il **connessione** dell'oggetto **proprietà** insieme.

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
|Percorso|DBPROP_INIT_LOCATION|
|Dimensione massima dell'indice|DBPROP_MAXINDEXSIZE|
|Dimensioni massime delle righe|DBPROP_MAXROWSIZE|
|Dimensioni massime riga con BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Numero massimo di tabelle in SELECT|DBPROP_MAXTABLESINSELECT|
|Mode|DBPROP_INIT_MODE|
|Più set di parametri|DBPROP_MULTIPLEPARAMSETS|
|Più risultati|DBPROP_MULTIPLERESULTS|
|Più oggetti di archiviazione|DBPROP_MULTIPLESTORAGEOBJECTS|
|Aggiornamento di più tabelle|DBPROP_MULTITABLEUPDATE|
|Ordine delle regole di confronto NULL|DBPROP_NULLCOLLATION|
|Comportamento di concatenazione NULL|DBPROP_CONCATNULLBEHAVIOR|
|Servizi OLE DB|DBPROP_INIT_OLEDBSERVICES|
|OLE DB versione|DBPROP_PROVIDEROLEDBVER|
|Supporto dell'oggetto OLE|DBPROP_OLEOBJECTS|
|Aprire il supporto di set di righe|DBPROP_OPENROWSETSUPPORT|
|Colonne ORDER BY nell'elenco di selezione|DBPROP_ORDERBYCOLUMNSINSELECT|
|Disponibilità dei parametri di output|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Password|DBPROP_AUTH_PASSWORD|
|Passare dalle funzioni di accesso di riferimento|DBPROP_BYREFACCESSORS|
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
 Le proprietà seguenti vengono aggiunti per il **Recordset** dell'oggetto **proprietà** insieme.

|Nome della proprietà ADO|Nome della proprietà OLE DB|
|-----------------------|--------------------------|
|Ordine di accesso|DBPROP_ACCESSORDER|
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|
|Supporta|DBPROP_IROWSETLOCATE|
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Righe univoche|DBPROP_UNIQUEROWS|
|Aggiornabile|DBPROP_UPDATABILITY|
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Proprietà dinamiche di comando
 Le proprietà seguenti vengono aggiunti per il **comando** dell'oggetto **proprietà** insieme.

|Nome della proprietà ADO|Nome della proprietà OLE DB|
|-----------------------|--------------------------|
|Ordine di accesso|DBPROP_ACCESSORDER|
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|
|Supporta|DBPROP_IROWSETLOCATE|
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Ignora segnalibri eliminati|DBPROP_BOOKMARKSKIP|
|Identità riga forte|DBPROP_STRONGIDENTITY|
|Aggiornabile|DBPROP_UPDATABILITY|
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|

 Per informazioni dettagliate e sull'implementazione funzionale informazioni sui Provider Microsoft OLE DB per ODBC, vedere il [riferimento per programmatori OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) o visitare il sito Data Access and Storage Developer Center Web su MSDN.

## <a name="see-also"></a>Vedere anche
 [Comando oggetto (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) [oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md) [proprietà ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [eseguire Metodo (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md) [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) [la raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md) [insieme di proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Proprietà provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [supporta (metodo)](../../../ado/reference/ado-api/supports-method.md)
