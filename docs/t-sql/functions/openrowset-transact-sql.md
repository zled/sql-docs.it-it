---
title: OPENROWSET (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET_TSQL
- OPENROWSET
dev_langs:
- TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENROWSET function
- remote data access [SQL Server], OPENROWSET
- ad hoc distributed queries
- OPENROWSET function, Transact-SQL
- OPENROWSET statement
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: f47eda43-33aa-454d-840a-bb15a031ca17
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 68db78ede26c3e7f8c60ced655d89d0fc9a615ac
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="openrowset-transact-sql"></a>OPENROWSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Include tutte le informazioni di connessione necessarie per l'accesso remoto ai dati da un'origine dati OLE DB. Si tratta di un metodo alternativo per l'accesso alle tabelle di un server collegato e corrisponde a un metodo ad hoc eseguito una sola volta per la connessione e l'accesso ai dati remoti tramite OLE DB. Per ottenere riferimenti più frequenti alle origini dati OLE DB, utilizzare server collegati. Per altre informazioni, vedere [Server collegati &#40;Motore di database&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md). Il `OPENROWSET` funzione può essere fatto riferimento nella clausola FROM di una query come se fosse un nome di tabella. Il `OPENROWSET` funzione inoltre possibile farvi riferimento come tabella di destinazione di un `INSERT`, `UPDATE`, o `DELETE` istruzione, a seconda delle capacità del provider OLE DB. Anche se la query potrebbe restituire più set di risultati, `OPENROWSET` restituisce solo il primo.  
  
 `OPENROWSET`supporta inoltre operazioni bulk tramite un provider BULK predefinito che consente di dati da un file di essere letti e restituiti come un set di righe.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OPENROWSET   
( { 'provider_name' , { 'datasource' ; 'user_id' ; 'password'   
   | 'provider_string' }   
   , {   [ catalog. ] [ schema. ] object   
       | 'query'   
     }   
   | BULK 'data_file' ,   
       { FORMATFILE = 'format_file_path' [ <bulk_options> ]  
       | SINGLE_BLOB | SINGLE_CLOB | SINGLE_NCLOB }  
} )   
  
<bulk_options> ::=  
   [ , CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ , DATASOURCE = 'data_source_name' ]
   [ , ERRORFILE = 'file_name' ]  
   [ , ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ , FIRSTROW = first_row ]   
   [ , LASTROW = last_row ]   
   [ , MAXERRORS = maximum_errors ]   
   [ , ROWS_PER_BATCH = rows_per_batch ]  
   [ , ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) [ UNIQUE ] ]
  
   -- bulk_options related to input file format
   [ , FORMAT = 'CSV' ]
   [ , FIELDQUOTE = 'quote_characters']
   [ , FORMATFILE = 'format_file_path' ]   
```

  
## <a name="arguments"></a>Argomenti  
 '*provider_name*'  
 Stringa di caratteri che rappresenta il nome descrittivo (o PROGID) del provider OLE DB specificato nel Registro di sistema. *provider_name* nessun valore predefinito.  
  
 '*datasource*'  
 Costante stringa che corrisponde a un'origine dati OLE DB specifica. *origine dati* è la proprietà DBPROP_INIT_DATASOURCE da passare all'interfaccia IDBProperties del provider per inizializzare il provider. In genere questa stringa include il nome del file di database, il nome di un server di database o un nome riconosciuto dal provider per individuare il database o i database.  
  
 '*user_id*'  
 Costante stringa che rappresenta il nome utente passato al provider OLE DB specificato. *USER_ID* specifica il contesto di sicurezza per la connessione e viene passato come proprietà DBPROP_AUTH_USERID per l'inizializzazione del provider. *USER_ID* non può essere un nome di account di accesso di Microsoft Windows.  
  
 '*password*'  
 Costante stringa che rappresenta la password utente da passare al provider OLE DB. *password* viene passato come proprietà DBPROP_AUTH_PASSWORD durante l'inizializzazione del provider. *password* non può essere una password di Microsoft Windows.  
  
 '*provider_string*'  
 Stringa di connessione specifica del provider passata come proprietà DBPROP_INIT_PROVIDERSTRING per l'inizializzazione del provider OLE DB. *provider_string* in genere incapsula tutte le informazioni di connessione necessarie per inizializzare il provider. Per un elenco di parole chiave riconosciute dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, vedere [proprietà di inizializzazione e autorizzazione](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 *catalogo*  
 Nome del catalogo o database contenente l'oggetto specificato.  
  
 *schema*  
 Nome dello schema o proprietario dell'oggetto specificato.  
  
 *oggetto*  
 Nome dell'oggetto che identifica in modo univoco l'oggetto da utilizzare.  
  
 '*query*'  
 Costante stringa inviata al provider ed eseguita da questo. L'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non elabora questa query, ma i risultati della query restituiti dal provider (query pass-through). Le query pass-through risultano utili quando vengono utilizzate in provider che non espongono i dati tabulari tramite i nomi di tabella, ma solo attraverso un linguaggio di comando. Query pass-through sono supportate nel server remoto, fino a quando il provider di query supporta l'oggetto comando OLE DB e le relative interfacce obbligatorie. Per ulteriori informazioni, vedere [OLE DB Native Client di SQL Server &#40; &#41; Riferimento](../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md).  
  
 BULK  
 Utilizza il provider BULK per set di righe per OPENROWSET per leggere i dati da un file. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], OPENROWSET è in grado di leggere da un file di dati senza caricare i dati in una tabella di destinazione. Ciò consente di utilizzare OPENROWSET con un'istruzione SELECT semplice.  
  
 Gli argomenti dell'opzione BULK consentono un controllo significativo su dove iniziare e terminare la lettura dei dati, come gestire gli errori e come interpretare i dati. Ad esempio, è possibile specificare che il file di dati venga letto come un set di righe a riga singola e una sola colonna di tipo **varbinary**, **varchar**, o **nvarchar**. Il comportamento predefinito viene illustrato nelle descrizioni degli argomenti seguenti.  
  
 Per informazioni sull'utilizzo dell'opzione BULK, vedere la sezione "Osservazioni" di seguito in questo argomento. Per informazioni sulle autorizzazioni necessarie per l'opzione BULK, vedere la sezione "Autorizzazioni" di seguito in questo argomento.  
  
> [!NOTE]  
>  Quando utilizzata per importare i dati con il modello di recupero con registrazione completa, OPENROWSET (BULK ...) non ottimizza la registrazione.  
  
 Per informazioni sulla preparazione dei dati per l'importazione bulk, vedere [preparazione dei dati per l'esportazione Bulk o importazione &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 '*data_file*'  
 Percorso completo del file di dati i cui dati devono essere copiati nella tabella di destinazione.   
 **Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, il data_file può essere nell'archiviazione BLOB di Azure. Per esempi, vedere [esempi di massa di accesso ai dati nell'archiviazione Blob di Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
  
 \<bulk_options >  
 Specifica uno o più argomenti per l'opzione BULK.  
  
 CODEPAGE = {"ACP" | "OEM" | 'NON ELABORATI' | *code_page*'}  
 Specifica la tabella codici dei dati contenuti nel file di dati. CODEPAGE è rilevante solo se i dati contengono **char**, **varchar**, o **testo** colonne con valori di carattere maggiori di 127 o minori di 32.  
  
> [!NOTE]  
>  È consigliabile specificare un nome di regole di confronto per ogni colonna in un file di formato tranne quando si desidera che l'hanno la priorità sulla specifica pagina regole di confronto o codice all'opzione 65001.  
  
|Valore CODEPAGE|Description|  
|--------------------|-----------------|  
|ACP|Converte le colonne di **char**, **varchar**, o **testo** tipo di dati da ANSI /[!INCLUDE[msCoName](../../includes/msconame-md.md)] codici di Windows (ISO 1252) per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] codici.|  
|OEM (predefinito)|Converte le colonne di **char**, **varchar**, o **testo** il tipo di dati dalla tabella codici OEM di sistema per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] codici.|  
|RAW|Non vengono eseguite conversioni tra tabelle codici. Si tratta dell'opzione più rapida.|  
|*code_page*|Indica la tabella codici di origine in cui vengono codificati i dati di tipo carattere del file di dati, ad esempio 850.<br /><br /> **\*\*Importante \* \***  versioni precedenti a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] non supportano la tabella codici 65001 (codifica UTF-8).|  
  
 ERRORFILE ='*file_name*'  
 Specifica il file utilizzato per raccogliere le righe che contengono errori di formattazione e non possono essere convertite in un set di righe OLE DB. Tali righe vengono copiate nel file degli errori dal file di dati così come sono.  
  
 Il file di errori viene creato all'inizio dell'esecuzione del comando. Se il file esiste già viene generato un errore. Viene inoltre creato un file di controllo con estensione ERROR.txt. Questo file contiene un riferimento a ogni riga nel file degli errori e fornisce informazioni di diagnostica. Dopo la correzione degli errori, i dati possono essere caricati.  
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], `error_file_path` può trovarsi in archiviazione BLOB di Azure. 

'errorfile_data_source_name'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
Un'origine dati esterna denominata che punta al percorso di archiviazione Blob di Azure che conterrà gli errori rilevati durante l'importazione degli errori. L'origine dati esterna deve essere creata usando il `TYPE = BLOB_STORAGE` opzione aggiunto in [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
 FIRSTROW =*first_row*  
 Specifica il numero della prima riga da caricare. Il valore predefinito è 1. Questo valore indica la prima riga nel file di dati specificato. I numeri di riga sono determinati dal conteggio dei caratteri di terminazione. FIRSTROW è in base 1.  
  
 LASTROW =*last_row*  
 Specifica il numero dell'ultima riga da caricare. Il valore predefinito è 0. Questo valore indica l'ultima riga nel file di dati specificato.  
  
 MAXERRORS =*maximum_errors*  
 Specifica il numero massimo di errori di sintassi o righe non conformi, definite nel file di formato, che possono verificarsi prima che OPENROWSET generi un'eccezione. Fino al raggiungimento di MAXERRORS, OPENROWSET ignora ogni riga non conforme, non caricandola, e conteggia la riga non conforme come un errore.  
  
 Il valore predefinito per *maximum_errors* è 10.  
  
> [!NOTE]  
>  MAX_ERRORS non si applica ai vincoli CHECK o alla conversione **money** e **bigint** tipi di dati.  
  
 ROWS_PER_BATCH =*rows_per_batch*  
 Specifica il numero approssimativo di righe di dati nel file di dati. Questo valore deve essere dello stesso ordine del numero effettivo di righe.  
  
 OPENROWSET importa sempre un file di dati come batch singolo. Tuttavia, se si specifica *rows_per_batch* con un valore > 0, query processor utilizza il valore di *rows_per_batch* come hint per allocare risorse nel piano di query.  
  
 Per impostazione predefinita, il valore ROWS_PER_BATCH è sconosciuto. La specifica di ROWS_PER_BATCH = 0 equivale all'omissione di ROWS_PER_BATCH.  
  
 ORDINE ({ *colonna* [ASC | DESC]} [,...  *n*  ] [UNIQUE])  
 Hint facoltativo che specifica il modo in cui vengono ordinati i dati nel file di dati. Per impostazione predefinita, per l'operazione bulk si presume che il file di dati non sia ordinato. Se l'ordine specificato può essere sfruttato da Query Optimizer per generare un piano di query più efficiente, le prestazioni possono migliorare. Di seguito vengono riportati alcuni esempi di situazioni in cui può essere utile specificare l'ordinamento:  
  
-   Inserimento di righe in una tabella con un indice cluster, in cui i dati del set di righe sono ordinati in base alla chiave dell'indice cluster.  
  
-   Unione del set di righe con un'altra tabella, in cui le colonne di ordinamento e di join corrispondono.  
  
-   Aggregazione dei dati del set di righe tramite le colonne dell'ordinamento.  
  
-   Utilizzo del set di righe come tabella di origine nella clausola FROM di una query, in cui le colonne di ordinamento e di join corrispondono.  
  
 UNIQUE specifica che il file di dati non ha voci duplicate.  
  
 Se le righe effettive del file di dati non sono ordinate in base all'ordine specificato o se l'hint UNIQUE viene specificato e sono presenti chiavi duplicate, viene restituito un errore.  
  
 Gli alias di colonna sono richiesti quando si utilizza ORDER. L'elenco di alias di colonna deve fare riferimento alla tabella derivata a cui è possibile accedere tramite la clausola BULK. I nomi di colonna specificati nella clausola ORDER si riferiscono a questo elenco di alias di colonna. Tipi di valori di grandi dimensioni (**varchar (max)**, **nvarchar (max)**, **varbinary (max)**, e **xml**) e i tipi LOB (large object) (**testo**, **ntext**, e **immagine**) non è possibile specificare le colonne.  
  
 SINGLE_BLOB  
 Restituisce il contenuto di *data_file* come un set di righe a riga singola e una sola colonna di tipo **varbinary (max)**.  
  
> [!IMPORTANT]  
>  Per l'importazione di dati XML è consigliabile utilizzare solo l'opzione SINGLE_BLOB anziché SINGLE_CLOB e SINGLE_NCLOB, in quanto solo SINGLE_BLOB supporta tutti i tipi di conversione di codifica di Windows.  
  
 SINGLE_CLOB  
 Leggendo *data_file* come ASCII, restituisce il contenuto come set di righe a riga singola e una sola colonna di tipo **varchar (max)**, utilizzando le regole di confronto del database corrente.  
  
 SINGLE_NCLOB  
 Leggendo *data_file* come UNICODE, restituisce il contenuto come set di righe a riga singola e una sola colonna di tipo **nvarchar (max)**, utilizzando le regole di confronto del database corrente.  

### <a name="input-file-format-options"></a>Opzioni di formato di file di input
  
FORMATO  **=**  'CSV'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Specifica un file di valori separati da virgole conforme il [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

 FORMATFILE ='*format_file_path*'  
 Specifica il percorso completo di un file di formato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta due tipi di file di formato, ovvero XML e non XML.  
  
 Un file di formato è necessario per definire i tipi di colonna nel set di risultati. L'unica eccezione si verifica quando viene specificato SINGLE_CLOB, SINGLE_BLOB o SINGLE_NCLOB. In questo caso, il file di formato non è necessario.  
  
 Per informazioni sui file di formato, vedere [utilizzare un File di formato per l'importazione Bulk dei dati &#40; SQL Server &#41; ](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).  

**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, il format_file_path può essere nell'archiviazione BLOB di Azure. Per esempi, vedere [esempi di massa di accesso ai dati nell'archiviazione Blob di Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).

FIELDQUOTE  **=**  'field_quote'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Specifica un carattere che verrà utilizzato come carattere di virgolette nel file CSV. Se non specificato, il carattere virgoletta (") da utilizzare come carattere di virgolette come definito nel [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

  
## <a name="remarks"></a>Osservazioni  
 `OPENROWSET`può essere utilizzato per accedere ai dati remoti da OLE DB solo quando le origini dati di **DisallowAdhocAccess** opzione del Registro di sistema è impostata esplicitamente su 0 per il provider specificato e Ad Hoc Distributed Queries opzione di configurazione avanzata è abilitata. Quando queste opzioni non vengono impostate, il comportamento predefinito non consente l'accesso ad hoc.  
  
 Quando si accede alle origini dati OLE DB remote, l'identità dell'account di accesso delle connessioni trusted non viene delegata automaticamente dal server in cui il client è connesso al server su cui viene eseguita la query. È necessario configurare la delega dell'autenticazione.  
  
 Se il provider OLE DB supporta più cataloghi e schemi nell'origine dati specificata, è necessario specificare i nomi di catalogo e di schema. I valori del parametro *catalogo* e *schema* può essere omessa quando il provider OLE DB non li supporta. Se il provider supporta solo nomi di schema, un nome in due parti nel formato *schema***.** *oggetto* deve essere specificato. Se il provider supporta solo nomi di catalogo, un nome in tre parti nel formato *catalogo***.** *schema***.** *oggetto* deve essere specificato. È necessario specificare nomi composti da tre parti per le query pass-through che utilizzano il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client. Per ulteriori informazioni, vedere [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 `OPENROWSET`non accetta variabili come argomenti.  
  
 Qualsiasi chiamata a `OPENDATASOURCE`, `OPENQUERY`, o `OPENROWSET` nel `FROM` clausola viene valutata separatamente e in modo indipendente da qualsiasi altra chiamata a queste funzioni utilizzate come destinazione dell'aggiornamento, anche se alle due chiamate vengono forniti argomenti identici. In particolare, le condizioni di filtro o join applicate al risultato di una di tali chiamate non hanno effetto sui risultati dell'altra.  
  
## <a name="using-openrowset-with-the-bulk-option"></a>Utilizzo di OPENROWSET con l'opzione BULK  
 I miglioramenti seguenti apportati a [!INCLUDE[tsql](../../includes/tsql-md.md)] offrono il supporto per la funzione OPENROWSET(BULK…):  
  
-   Una clausola FROM utilizzata con `SELECT` può chiamare `OPENROWSET(BULK...)` anziché un nome di tabella, come con full `SELECT` funzionalità.  
  
     `OPENROWSET`con il `BULK` richiede un nome di correlazione, noto anche come una variabile di intervallo o l'alias, nel `FROM` clausola. È possibile specificare alias di colonne. Se non è specificato un elenco di alias di colonna, il file di formato deve contenere nomi di colonna. Se si specificano gli alias di colonna, i nomi di colonna nel file di formato vengono sostituiti, ad esempio:  
  
     `FROM OPENROWSET(BULK...) AS table_alias`  
  
     `FROM OPENROWSET(BULK...) AS table_alias(column_alias,...n)`  
>    [!IMPORTANT]  
>    Impossibile aggiungere il `AS <table_alias>` comporterà l'errore:    
>    Messaggio 491, livello 16, stato 1, riga 20    
>    Specificare il nome della correlazione per il set di righe con lettura bulk nella clausola FROM.    
  
-   Oggetto `SELECT...FROM OPENROWSET(BULK...)` istruzione esegue query i dati in un file direttamente, senza importare i dati in una tabella. `SELECT…FROM OPENROWSET(BULK...)`le istruzioni possono anche di elencare alias di colonna bulk utilizzando un file di formato per specificare i nomi di colonna e tipi di dati.  
  
-   Utilizzando `OPENROWSET(BULK...)` come una tabella di origine in un `INSERT` o `MERGE` importazioni bulk di istruzione di dati da un file di dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella. Per ulteriori informazioni, vedere [importazione Bulk dei dati per l'utilizzo di BULK INSERT o OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) .  
  
-   Quando il `OPENROWSET BULK` opzione viene utilizzata con un `INSERT` istruzione, la clausola BULK supporta gli hint di tabella. Oltre alle normali hint di tabella, ad esempio `TABLOCK`, `BULK` clausola può accettare gli hint di tabella specializzati seguenti: `IGNORE_CONSTRAINTS` (ignora solo il `CHECK` e `FOREIGN KEY` vincoli), `IGNORE_TRIGGERS`, `KEEPDEFAULTS`, e `KEEPIDENTITY`. Per altre informazioni, vedere [Hint di tabella &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Per informazioni su come usare `INSERT...SELECT * FROM OPENROWSET(BULK...)` istruzioni, vedere [importazione in blocco e l'esportazione di dati &#40; SQL Server &#41; ](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md). Per informazioni sui casi in cui le operazioni di inserimento di righe eseguite durante l'importazione in blocco vengono registrate nel log delle transazioni, vedere [Prerequisiti per la registrazione minima nell'importazione in blocco](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
> [!NOTE]  
>  Quando si utilizza `OPENROWSET`, è importante comprendere come [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestisce la rappresentazione. Per informazioni sulle considerazioni relative alla sicurezza, vedere [importazione Bulk dei dati per l'utilizzo di BULK INSERT o OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="bulk-importing-sqlchar-sqlnchar-or-sqlbinary-data"></a>Importazione bulk di dati SQLCHAR, SQLNCHAR o SQLBINARY  
 OPENROWSET(BULK...) presuppone che, se non è specificata, la lunghezza massima dei dati SQLCHAR, SQLNCHAR o SQLBINARY non supera 8000 byte. Se i dati da importare in un campo di dati LOB contenente qualsiasi **varchar (max)**, **nvarchar (max)**, o **varbinary (max)** gli oggetti che superano 8000 byte, è necessario utilizzare un File di formato XML che definisce la lunghezza massima per il campo dei dati. Per specificare la lunghezza massima, modificare il file di formato dichiarando l'attributo MAX_LENGTH.  
  
> [!NOTE]  
>  Un file di formato generato automaticamente non specifica la lunghezza o la lunghezza massima per un campo di tipo LOB. Tuttavia, è possibile modificare un file di formato e specificare la lunghezza o la lunghezza massima manualmente.  
  
### <a name="bulk-exporting-or-importing-sqlxml-documents"></a>Esportazione o importazione bulk di documenti SQLXML  
 Per l'esportazione o l'importazione bulk di dati SQLXML, utilizzare uno dei tipi di dati seguenti nel file di formato.  
  
|Tipo di dati|Effetto|  
|---------------|------------|  
|SQLCHAR o SQLVARYCHAR|I dati vengono inviati nella tabella codici del client o nella tabella codici implicita delle regole di confronto.|  
|SQLNCHAR o SQLNVARCHAR|I dati vengono inviati in formato Unicode.|  
|SQLBINARY o SQLVARYBIN|I dati vengono inviati senza conversione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 `OPENROWSET`le autorizzazioni sono determinate dalle autorizzazioni del nome utente che viene passato al provider OLE DB. Utilizzare il `BULK` opzione richiede `ADMINISTER BULK OPERATIONS` autorizzazione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-openrowset-with-select-and-the-sql-server-native-client-ole-db-provider"></a>A. Utilizzo di OPENROWSET con SELECT e il provider OLE DB di SQL Server Native Client  
 L'esempio seguente usa il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client per accedere il `HumanResources.Department` tabella il [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database nel server remoto `Seattle1`. (L'utilizzo di SQLNCLI e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reindirizza alla versione più recente del provider OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.) Viene utilizzata un'istruzione `SELECT` per definire il set di righe restituito. La stringa del provider contiene le parole chiave `Server` e `Trusted_Connection`. Queste parole chiave sono riconosciute dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client.  
  
```sql  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-jet"></a>B. Utilizzo del provider Microsoft OLE DB per Jet  
 Nell'esempio seguente viene ottenuto l'accesso alla tabella `Customers` del database `Northwind` di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access tramite il provider [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB per Jet.  
  
> [!NOTE]  
>  Nell'esempio si presuppone che Access sia installato. Per eseguire questo esempio, è necessario installare il database Northwind.  
  
```sql  
SELECT CustomerID, CompanyName  
   FROM OPENROWSET('Microsoft.Jet.OLEDB.4.0',  
      'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';  
      'admin';'',Customers);  
GO  
```  
  
### <a name="c-using-openrowset-and-another-table-in-an-inner-join"></a>C. Utilizzo di OPENROWSET e di un'altra tabella in un INNER JOIN  
 L'esempio seguente seleziona tutti i dati di `Customers` tabella dall'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Northwind` database e dal `Orders` tabella dall'accesso `Northwind` database archiviato nello stesso computer.  
  
> [!NOTE]  
>  Nell'esempio si presuppone che Access sia installato. Per eseguire questo esempio, è necessario installare il database Northwind.  
  
```sql  
USE Northwind  ;  
GO  
SELECT c.*, o.*  
FROM Northwind.dbo.Customers AS c   
   INNER JOIN OPENROWSET('Microsoft.Jet.OLEDB.4.0',   
   'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';'admin';'', Orders)      
   AS o   
   ON c.CustomerID = o.CustomerID ;  
GO  
```  
  
### <a name="d-using-openrowset-to-bulk-insert-file-data-into-a-varbinarymax-column"></a>D. Utilizzo di OPENROWSET per eseguire un inserimento bulk dei dati del file in una colonna varbinary(max).  
 Nell'esempio seguente viene creata una tabella di piccole dimensioni a titolo dimostrativo e vengono quindi inseriti i dati di un file denominato `Text1.txt` archiviato nella directory radice `C:` in una colonna `varbinary(max)`.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTable(FileName nvarchar(60),   
  FileType nvarchar(60), Document varbinary(max));  
GO  
  
INSERT INTO myTable(FileName, FileType, Document)   
   SELECT 'Text1.txt' AS FileName,   
      '.txt' AS FileType,   
      * FROM OPENROWSET(BULK N'C:\Text1.txt', SINGLE_BLOB) AS Document;  
GO  
```  
  
### <a name="e-using-the-openrowset-bulk-provider-with-a-format-file-to-retrieve-rows-from-a-text-file"></a>E. Utilizzo del provider OPENROWSET BULK con un file di formato per recuperare le righe da un file di testo  
 Nell'esempio seguente viene utilizzato un file di formato per recuperare le righe da un file di testo delimitato da tabulazioni, `values.txt` contenente i dati seguenti:  
  
```sql  
1     Data Item 1  
2     Data Item 2  
3     Data Item 3  
```  
  
 Il file di formato, `values.fmt`, descrive le colonne in `values.txt`:  
  
```sql  
9.0  
2  
1  SQLCHAR  0  10 "\t"        1  ID                SQL_Latin1_General_Cp437_BIN  
2  SQLCHAR  0  40 "\r\n"      2  Description        SQL_Latin1_General_Cp437_BIN  
```  
  
 Di seguito è illustrata la query che recupera tali dati:  
  
```sql  
SELECT a.* FROM OPENROWSET( BULK 'c:\test\values.txt',   
   FORMATFILE = 'c:\test\values.fmt') AS a;  
```  
  
### <a name="f-specifying-a-format-file-and-code-page"></a>F. Specificare una pagina di codice e file di formato  
 Nell'esempio seguente viene illustrato come utilizzare entrambi i file di codice pagina Opzioni di formato nello stesso momento.  
  
```sql  
INSERT INTO MyTable SELECT a.* FROM  
OPENROWSET (BULK N'D:\data.csv', FORMATFILE =   
    'D:\format_no_collation.txt', CODEPAGE = '65001') AS a;  
```  
### <a name="g-accessing-data-from-a-csv-file-with-a-format-file"></a>G. L'accesso ai dati da un file CSV con un file di formato  
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
```sql
SELECT *
FROM OPENROWSET(BULK N'D:\XChange\test-csv.csv',
    FORMATFILE = N'D:\XChange\test-csv.fmt', 
    FIRSTROW=2, 
    FORMAT='CSV') AS cars;  
```

### <a name="h-accessing-data-from-a-csv-file-without-a-format-file"></a>H. L'accesso ai dati da un file CSV senza un file di formato

```sql
SELECT * FROM OPENROWSET(
   BULK 'C:\Program Files\Microsoft SQL Server\MSSQL14.CTP1_1\MSSQL\DATA\inv-2017-01-19.csv',
   SINGLE_CLOB) AS DATA;
```

### <a name="i-accessing-data-from-a-file-stored-on-azure-blob-storage"></a>I. Accesso ai dati da un file archiviato in archiviazione Blob di Azure   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
L'esempio seguente usa un'origine dati esterna che punta a un contenitore in un account di archiviazione di Azure e le credenziali con ambito database creato per una firma di accesso condiviso.     

```sql
SELECT * FROM OPENROWSET(
   BULK  'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   SINGLE_CLOB) AS DataFile;
```   
Per completare `OPENROWSET` esempi inclusi la configurazione di credenziali e l'origine dati esterna, vedere [esempi di massa di accesso ai dati nell'archiviazione Blob di Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
 
### <a name="additional-examples"></a>Esempi aggiuntivi  
 Per ulteriori esempi che illustrano l'utilizzo `INSERT...SELECT * FROM OPENROWSET(BULK...)`, vedere gli argomenti seguenti:  
  
-   [Esempi di importazione ed esportazione bulk di documenti XML &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Mantenere i valori Identity durante l'importazione in blocco dei dati &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Mantenere i valori Null o usare i valori predefiniti durante l'importazione in blocco &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Usare un file di formato per l'importazione in blocco dei dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utilizzo del formato carattere per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilizzo di un file di formato per ignorare una colonna di una tabella &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Utilizzo di un file di formato per escludere un campo di dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utilizzo di un file di formato per eseguire il mapping tra le colonne della tabella e i campi del file di dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Informazioni sull'importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [OPENQUERY &#40; Transact-SQL &#41;](../../t-sql/functions/openquery-transact-sql.md)   
 [Funzioni rowset &#40; Transact-SQL &#41;](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_serveroption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
