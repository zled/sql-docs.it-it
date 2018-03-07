---
title: DBCC CHECKDB (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKDB_TSQL
- DBCC_CHECKDB_TSQL
- DBCC CHECKDB
- CHECKDB
dev_langs:
- TSQL
helpviewer_keywords:
- CHECKDB [DBCC statement]
- database objects [SQL Server], checking
- counting pages
- per-index row counts
- per-table row counts
- DBCC CHECKDB statement
- per-table page counts
- allocation checks
- integrity [SQL Server], database objects
- per-index page counts
- counting rows
- table integrity checks [SQL Server]
- row count accuracy [SQL Server]
- negative counts
- checking database objects
- page count accuracy [SQL Server]
ms.assetid: 2c506167-0b69-49f7-9282-241e411910df
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: d2d28362462825c1e39d0a7a41f6a57f810c107e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkdb-transact-sql"></a>DBCC CHECKDB (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Verifica l'integrità logica e fisica di tutti gli oggetti del database specificato eseguendo le operazioni seguenti:    
    
-   Esecuzioni [DBCC CHECKALLOC](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md) nel database.    
-   Esecuzioni [DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md) in ogni tabella e vista nel database.    
-   Esecuzioni [DBCC CHECKCATALOG](../../t-sql/database-console-commands/dbcc-checkcatalog-transact-sql.md) nel database.    
-   Convalida del contenuto di ogni vista indicizzata nel database.    
-   Convalida la coerenza a livello di collegamenti tra file e directory di sistema di metadati e i file di tabella quando si archiviano **varbinary (max)** dati nel file system utilizzando FILESTREAM.    
-   Convalida dei dati di [!INCLUDE[ssSB](../../includes/sssb-md.md)] nel database.    
    
Non è pertanto necessario eseguire i comandi DBCC CHECKALLOC, DBCC CHECKTABLE o DBCC CHECKCATALOG separatamente da DBCC CHECKDB. Per ulteriori informazioni sui controlli eseguiti da questi comandi, vedere la relativa descrizione.    
 
> [!NOTE]
> DBCC CHECKDB è supportato nei database che contengono tabelle ottimizzate per la memoria, ma la convalida viene eseguita solo nelle tabelle basate su disco. Tuttavia, come parte del backup e del ripristino del database, la convalida mediante CHECKSUM viene eseguita per i file nei filegroup ottimizzati per la memoria.    
>     
> Poiché le opzioni di correzione DBCC non sono disponibili per le tabelle ottimizzate per la memoria, è necessario eseguire regolarmente il backup dei database e verificare i backup. Se i problemi di integrità dei dati si verificano in una tabella ottimizzata per la memoria, è necessario eseguire il ripristino dall'ultima copia di backup valida nota.    

![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Sintassi    
    
```    
DBCC CHECKDB     
    [ ( database_name | database_id | 0    
        [ , NOINDEX     
        | , { REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD } ]    
    ) ]    
    [ WITH     
        {    
            [ ALL_ERRORMSGS ]    
            [ , EXTENDED_LOGICAL_CHECKS ]     
            [ , NO_INFOMSGS ]    
            [ , TABLOCK ]    
            [ , ESTIMATEONLY ]    
            [ , { PHYSICAL_ONLY | DATA_PURITY } ]    
            [ , MAXDOP  = number_of_processors ]    
        }    
    ]    
]    
```    
    
## <a name="arguments"></a>Argomenti    
 *database_name* | *database_id* | 0  
 Nome o ID del database per cui eseguire i controlli di integrità. Se questo argomento viene omesso oppure se viene specificato il valore 0, viene utilizzato il database corrente. I nomi dei database devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
    
NOINDEX  
 Specifica che non è necessario eseguire controlli estesi di indici non cluster per le tabelle utente. In questo modo, è possibile ridurre i tempi di esecuzione complessivi. NOINDEX non influisce sulle tabelle di sistema perché i controlli di integrità vengono sempre eseguiti sugli indici delle tabelle di sistema.  
    
REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD  
 Specifica che DBCC CHECKDB corregge gli errori rilevati. Utilizzare le opzioni REPAIR solo come ultima risorsa. Il database specificato deve essere in modalità utente singolo per utilizzare una delle opzioni di correzione seguenti.  
    
REPAIR_ALLOW_DATA_LOSS  
 Tenta di riparare tutti gli errori rilevati. Le operazioni di correzione possono comportare la perdita di dati.  
    
> [!WARNING]
> L'opzione REPAIR_ALLOW_DATA_LOSS è una funzionalità supportata, ma potrebbe non essere sempre l'opzione migliore per portare un database in uno stato fisicamente consistente. Se ha esito positivo, l'opzione REPAIR_ALLOW_DATA_LOSS può comportare una perdita di dati. Infatti, può comportare una perdita maggiore di dati rispetto al ripristino del database dall'ultimo backup valido. 
>
> [!INCLUDE[msCoName](../../includes/msconame-md.md)]consiglia sempre di un utente di ripristino dall'ultimo backup valido come metodo principale per il recupero da errori segnalati da DBCC CHECKDB. L'opzione REPAIR_ALLOW_DATA_LOSS non è un'alternativa del ripristino da un backup valido. È un'opzione di emergenza che è consigliabile usare solo se non è possibile eseguire il ripristino da un backup.    
>     
> Alcuni errori che possono essere corretti solo con l'opzione REPAIR_ALLOW_DATA_LOSS, possono comportare la deallocazione di una riga, una pagina o una serie di pagine per cancellare gli errori. Tutti i dati deallocati non saranno più accessibile né potranno essere recuperati e non sarà possibile determinare il contenuto esatto dei dati deallocati. Pertanto, l'integrità referenziale potrebbe non essere accurata dopo la deallocazione di una riga o una pagina poiché i vincoli di chiave esterna non vengono verificati né mantenuti come parte di questa operazione di ripristino. L'utente deve controllare l'integrità referenziale del database (con DBCC CHECKCONSTRAINTS) dopo aver usato l'opzione REPAIR_ALLOW_DATA_LOSS.    
>     
> Prima di eseguire il ripristino, creare copie fisiche dei file che appartengono a questo database. Ciò include il file di dati primario (mdf), eventuali file di dati secondari (ndf), tutti i file di log delle transazioni (ldf) e altri contenitori che costituiscono il database, compresi cataloghi full-text, cartelle del flusso di file, dati con ottimizzazione per la memoria e così via.    
>     
> Prima di eseguire il ripristino, provare a modificare lo stato del database impostando la modalità di emergenza e a estrarre quante più informazioni possibile dalle tabelle critiche salvando tali dati.    
    
REPAIR_FAST  
 Supporta la sintassi per motivi di compatibilità con le versioni precedenti Non vengono eseguite correzioni.  
    
REPAIR_REBUILD  
 Esegue operazioni di ripristino senza possibilità di perdita dei dati. Sono incluse operazioni di ripristino rapide, ad esempio ripristino di righe mancanti in indici non cluster, e operazioni che richiedono una maggiore quantità di tempo, come la ricompilazione di un indice.  
 Questo argomento non in grado di correggere errori relativi ai dati FILESTREAM.  
    
> [!IMPORTANT] 
> Poiché tutte le operazioni eseguite da DBCC CHECKDB con qualsiasi opzione di ripristino (REPAIR) vengono registrate e possono essere recuperate completamente, [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia sempre di usare CHECKDB con le opzioni di ripristino (REPAIR) in una transazione (eseguire BEGIN TRANSACTION) in modo da consentire all'utente di verificare se accettare o meno i risultati dell'operazione. L'utente potrà quindi eseguire il commit di tutte le operazioni effettuate dall'operazione di ripristino con l'istruzione COMMIT TRANSACTION. Se l'utente non vuole accettare i risultati dell'operazione, potrà eseguire un'istruzione ROLLBACK TRANSACTION per annullare gli effetti delle operazioni di ripristino.    
>     
> Per correggere gli errori, è consigliabile eseguire un ripristino da un backup. Le operazioni di correzione non tengono conto degli eventuali vincoli esistenti per le tabelle o tra le tabelle. Se la tabella specificata è interessata da uno o più vincoli, è consigliabile eseguire DBCC CHECKCONSTRAINTS dopo l'operazione di correzione. Se è necessario utilizzare REPAIR, eseguire DBCC CHECKDB senza opzioni di correzione per individuare il livello di correzione da applicare. Se si utilizza il livello REPAIR_ALLOW_DATA_LOSS, è consigliabile eseguire il backup del database prima di utilizzare DBCC CHECKDB con questa opzione.    
    
ALL_ERRORMSGS  
 Visualizza tutti gli errori segnalati per oggetto. Tutti i messaggi di errore vengono visualizzati per impostazione predefinita. La specifica o l'omissione di questa opzione non ha alcun effetto. I messaggi di errore vengono ordinati per ID di oggetto, ad eccezione dei messaggi generati da [database tempdb](../../relational-databases/databases/tempdb-database.md).     

EXTENDED_LOGICAL_CHECKS  
 Se il livello di compatibilità è 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) o maggiore, esegue controlli di consistenza logica in una vista indicizzata, indici XML e indici spaziali, dove presenti.  
 Per ulteriori informazioni, vedere *esecuzione logico controlli di consistenza sugli indici*nella [osservazioni](#remarks) sezione più avanti in questo argomento.  
    
NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
    
TABLOCK  
 Consente a DBCC CHECKDB di ottenere blocchi invece di utilizzare uno snapshot di database interno, incluso un blocco esclusivo (X) sul database di breve durata. TABLOCK consente l'esecuzione più rapida di DBCC CHECKDB in database con carico di lavoro elevato, ma comporta una diminuzione del livello di concorrenza del database durante l'esecuzione del comando.  
    
> [!IMPORTANT] 
> TABLOCK limita i controlli eseguiti. DBCC CHECKCATALOG non viene eseguito sul database e i dati di [!INCLUDE[ssSB](../../includes/sssb-md.md)] non vengono convalidati.
    
ESTIMATEONLY  
 Visualizza la quantità stimata di spazio di tempdb è necessario eseguire DBCC CHECKDB con tutte le altre opzioni specificate. Il controllo effettivo sul database non viene eseguito.  
    
PHYSICAL_ONLY  
 Limita il controllo di integrità alla struttura fisica della pagina, alle intestazioni dei record e alla consistenza di allocazione del database. Sebbene sia progettato per consentire un controllo a basso overhead della consistenza fisica del database, questo controllo consente inoltre di rilevare le pagine incomplete, gli errori di checksum e i comuni problemi a livello di hardware che possono compromettere i dati di un utente.  
 Un'esecuzione completa di DBCC CHECKDB può richiedere tempi notevolmente più lunghi rispetto alle versioni precedenti, per i seguenti motivi:  
 -   I controlli logici sono più completi.  
 -   Alcune delle strutture sottostanti da controllare sono più complesse.  
 -   Sono stati introdotti molti nuovi controlli per includere le nuove funzionalità.  
 Per questo motivo, l'utilizzo dell'opzione PHYSICAL_ONLY può consentire di ottenere tempi molto più brevi per l'esecuzione di DBCC CHECKDB in database di grandi dimensioni ed è quindi l'opzione consigliata per l'utilizzo frequente nei sistemi di produzione. È consigliabile prevedere periodicamente un'esecuzione completa di DBCC CHECKDB. La frequenza di esecuzione dipende da fattori specifici per i singoli ambienti aziendali e di produzione.    
Questo argment sempre implica NO_INFOMSGS e non è consentito con una delle opzioni di ripristino.  
    
> [!WARNING] 
> Se si specifica PHYSICAL_ONLY, DBCC CHECKDB ignora tutti i controlli dei dati FILESTREAM.
    
DATA_PURITY  
 Consente a DBCC CHECKDB di controllare il database per i valori di colonna che non sono validi o non sono compresi nell'intervallo dei valori consentiti. Ad esempio, DBCC CHECKDB rileva le colonne con valori di data e ora maggiori sono minori dell'intervallo accettabile per il **datetime** tipo di dati, o **decimale** o tipo di dati numerici approssimati colonne con valori di precisione o scala che non sono validi.  
 I controlli di integrità dei valori di colonna sono abilitati per impostazione predefinita e non richiedono l'opzione DATA_PURITY. Per i database aggiornati da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i controlli dei valori di colonna non sono abilitati per impostazione predefinita fino a quando DBCC CHECKDB WITH DATA_PURITY non è stato eseguito senza errori nel database. A questo punto, DBCC CHECKDB controlla l'integrità dei valori di colonna per impostazione predefinita. Per ulteriori informazioni su come l'aggiornamento del database da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può influire su CHECKDB, vedere la sezione Osservazioni di seguito in questo argomento.  
    
> [!WARNING]
> Se si specifica PHYSICAL_ONLY, i controlli di integrità di colonna non vengono eseguiti.
    
 Gli errori di convalida rilevati da questa opzione non possono essere corretti utilizzando le opzioni di correzione DBCC. Per informazioni sulla correzione manuale di questi errori, vedere l'articolo 923247 della Knowledge Base: [risoluzione dell'errore DBCC 2570 in SQL Server 2005 e versioni successive](http://support.microsoft.com/kb/923247).  
    
 MAXDOP  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
    
 Esegue l'override di **massimo grado di parallelismo** opzione di configurazione di **sp_configure** per l'istruzione. Il MAXDOP può superare il valore configurato con sp_configure. Se MAXDOP supera il valore configurato con Resource Governor il [!INCLUDE[ssDEnoversion](../../includes/ssDEnoversion_md.md)] utilizza il valore MAXDOP di Resource Governor, descritto in [ALTER WORKLOAD GROUP](../../t-sql/statements/alter-workload-group-transact-sql.md). Quando si utilizza l'hint per la query MAXDOP sono valide tutte le regole semantiche utilizzate con l'opzione di configurazione max degree of parallelism. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
 
> [!WARNING] 
> Se MAXDOP è impostato su zero, SQL Server sceglie il grado massimo di parallelismo da utilizzare.    

## <a name="remarks"></a>Osservazioni    
DBCC CHECKDB non esamina gli indici disabilitati. Per ulteriori informazioni sugli indici disabilitati, vedere [disabilitazione di indici e vincoli](../../relational-databases/indexes/disable-indexes-and-constraints.md).    

Se un tipo definito dall'utente (UDT) viene contrassegnato come ordinato per byte, è necessario che sia presente un'unica serializzazione di tale tipo. In assenza di una serializzazione consistente dei tipi definiti dall'utente (UDT) ordinati per byte, durante l'esecuzione di DBCC CHECKDB viene generato l'errore 2537. Per ulteriori informazioni, vedere [i requisiti del tipo definito dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-requirements.md).    

Poiché il [database delle risorse](../../relational-databases/databases/resource-database.md) è modificabile solo in modalità utente singolo, il comando non può essere eseguito direttamente su tale DBCC CHECKDB. Tuttavia, quando DBCC CHECKDB viene eseguita su di [database master](../../relational-databases/databases/master-database.md), un secondo CHECKDB viene eseguito internamente anche nel database delle risorse. Di conseguenza, DBCC CHECKDB può restituire risultati aggiuntivi. Il comando restituisce ulteriori set di risultati quando non si imposta alcuna opzione o quando si imposta l'opzione PHYSICAL_ONLY o ESTIMATEONLY.    

A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP2, l'esecuzione di DBCC CHECKDB **non è più** Cancella la cache dei piani per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Prima di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP2, l'esecuzione di DBCC CHECKDB Cancella la cache dei piani. La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un improvviso temporaneo peggioramento delle prestazioni di esecuzione delle query. 
    
## <a name="performing-logical-consistency-checks-on-indexes"></a>Esecuzione di controlli di consistenza logica negli indici    
I controlli di consistenza logica negli indici variano in base al livello di compatibilità del database, come indicato di seguito:
-   Se il livello di compatibilità è 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) o maggiore:    
-   A meno che non venga specificato NOINDEX, tramite DBCC CHECKDB vengono eseguiti controlli di consistenza sia fisica che logica in una singola tabella e in tutti i relativi indici non cluster. Per impostazione predefinita, tuttavia, negli indici XML, negli indici spaziali e nelle viste indicizzate vengono eseguiti solo controlli di consistenza fisica.
-   Se viene specificato WITH EXTENDED_LOGICAL_CHECKS, vengono eseguiti controlli logici in una vista indicizzata, indici XML e indici spaziali, dove presenti. Per impostazione predefinita, i controlli di consistenza fisica vengono eseguiti prima di quelli di consistenza logica. Se viene specificato anche NOINDEX, vengono eseguiti solo i controlli logici.
    
Tramite questi controlli di consistenza logica vengono eseguiti controlli incrociati della tabella degli indici interna dell'oggetto Index con la tabella utente a cui viene fatto riferimento. Per trovare le righe esterne, viene creata una query interna per eseguire un'intersezione completa della tabella interna e della tabella utente. L'esecuzione di questa query può influire notevolmente sulle prestazioni e non è possibile tenere traccia del relativo stato di avanzamento. È pertanto consigliabile specificare WITH EXTENDED_LOGICAL_CHECKS solo se si sospetta la presenza di problemi dell'indice non correlati a danni fisici o se i checksum a livello di pagina sono stati disabilitati e si sospetta la presenza di danni hardware a livello di colonna.
-   Se l'indice è un indice filtrato, tramite DBCC CHECKDB vengono eseguiti controlli di consistenza per verificare che le voci di indice soddisfino il predicato del filtro.
-   Se il livello di compatibilità è 90 o minore, a meno che non venga specificato NOINDEX, tramite DBCC CHECKDB vengono eseguiti controlli di consistenza sia fisica che logica in una singola tabella o vista indicizzata e in tutti i relativi indici non cluster e XML. Gli indici spaziali non sono supportati.  
- A partire da SQL Server 2016, controlli aggiuntivi in colonne calcolate persistenti, le colonne di tipo definito dall'utente e gli indici filtrati non verranno eseguito per impostazione predefinita per evitare le valutazioni di espressione costosa. Questa modifica riduce la durata di CHECKDB su database che contiene tali oggetti. Tuttavia, i controlli di consistenza fisica di questi oggetti viene sempre completata. Solo quando è specificata l'opzione EXTENDED_LOGICAL_CHECKS verranno le valutazioni di espressione eseguite oltre ai controlli di logici è già presenti (vista indicizzata, indici XML e indici spaziali) come parte dell'opzione EXTENDED_LOGICAL_CHECKS.   
    
**Per informazioni sul livello di compatibilità di un database**
-   [Visualizzare o modificare il livello di compatibilità di un database](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)    
    
## <a name="internal-database-snapshot"></a>Snapshot di database interno    
DBCC CHECKDB utilizza uno snapshot interno del database per garantire la consistenza delle transazioni necessaria per l'esecuzione di questi controlli. Ciò consente di evitare problemi di blocco e concorrenza durante l'esecuzione di questi comandi. Per ulteriori informazioni, vedere [visualizzare le dimensioni del File Sparse di uno Snapshot del Database &#40; Transact-SQL &#41; ](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) e la sezione Utilizzo Snapshot Database interno di DBCC in [DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-transact-sql.md). Se non è possibile creare uno snapshot o se viene specificato TABLOCK, DBCC CHECKDB acquisisce blocchi per ottenere la consistenza necessaria. In questo caso, è necessario un blocco esclusivo a livello di database per eseguire i controlli di allocazione, nonché blocchi condivisi a livello di tabella per eseguire i controlli delle tabelle.
DBCC CHECKDB non riesce se viene eseguito in generale, se non è possibile creare uno snapshot interno del database.
Esecuzione di DBCC CHECKDB nel database tempdb non esegue controlli di allocazione o il catalogo e deve acquisire blocchi di tabella condivisi per eseguire controlli di tabella. Questo funzionamento dipende dal fatto che per motivi di prestazioni gli snapshot di database non sono disponibili in tempdb. Ciò significa che non è possibile ottenere la consistenza delle transazioni necessaria.
In Microsoft SQL Server 2012 o una versione precedente di SQL Server, è possibile riscontrare i messaggi di errore quando si esegue il comando DBCC CHECKDB per un database che include i file in un volume formattato ReFS. Per ulteriori informazioni, vedere l'articolo della Knowledge Base 2974455: [il comportamento di DBCC CHECKDB quando il database di SQL Server si trova in un volume ReFS.](https://support.microsoft.com/kb/2974455)    
    
## <a name="checking-and-repairing-filestream-data"></a>Controllo e ripristino dei dati FILESTREAM    
Se FILESTREAM è abilitato per un database e una tabella, è possibile archiviare facoltativamente **varbinary (max)** oggetti binari di grandi dimensioni (BLOB) nel file system. Quando si utilizza DBCC CHECKDB in un database tramite cui vengono archiviati oggetti BLOB nel file system, tramite DBCC viene verificata la consistenza a livello di collegamenti tra il file system e il database.
Ad esempio, se una tabella contiene un **varbinary (max)** colonna che utilizza l'attributo FILESTREAM, DBCC CHECKDB viene verificato che sia presente un mapping uno a uno tra directory del file system e i file e le righe delle tabelle, colonne e colonna valori. DBCC CHECKDB consente di correggere i danneggiamenti se si specifica l'opzione REPAIR_ALLOW_DATA_LOSS. Per ripristinare il danneggiamento di FILESTREAM, DBCC consentirà di eliminare qualsiasi riga della tabella in cui mancano i dati del file system.
    
## <a name="best-practices"></a>Procedure consigliate    
È consigliabile utilizzare l'opzione PHYSICAL_ONLY per l'utilizzo frequente nei sistemi di produzione, poiché consente di ridurre notevolmente i tempi di esecuzione di DBCC CHECKDB su database di grandi dimensioni. È inoltre consigliabile eseguire periodicamente DBCC CHECKDB senza opzioni. La frequenza consigliata di esecuzione varia a seconda delle singole aziende e dei relativi ambienti di produzione.
    
## <a name="checking-objects-in-parallel"></a>Controllo parallelo degli oggetti    
Per impostazione predefinita, DBCC CHECKDB esegue il controllo parallelo degli oggetti. Il grado di parallelismo viene determinato in modo automatico da Query Processor. Il livello massimo di parallelismo viene configurato allo stesso modo delle query parallele. Per limitare il numero massimo di processori disponibili per la verifica DBCC, utilizzare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md). Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). È possibile disabilitare il controllo parallelo tramite il flag di traccia 2528. Per altre informazioni, vedere [Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).
    
> [!NOTE]
> Questa funzionalità non è disponibile in ogni edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere la coerenza parallela nella sezione Gestione RDBMS di [funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).    
    
## <a name="understanding-dbcc-error-messages"></a>Informazioni sui messaggi di errore DBCC    
Dopo il completamento del comando DBCC CHECKDB, nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene scritto un messaggio. Se l'esecuzione del comando DBCC ha esito positivo, il messaggio segnala che il completamento è avvenuto correttamente e indica la durata di esecuzione del comando. Se il comando DBCC viene arrestato prima del completamento del controllo a causa di un errore, il messaggio indica che il comando è stato terminato e specifica un valore di stato e la durata dell'esecuzione del comando. Nella tabella seguente sono elencati e descritti i valori di stato che possono essere inclusi nel messaggio.
    
|State|Description|    
|-----------|-----------------|    
|0|È stato generato l'errore numero 8930. Indica un danneggiamento dei metadati che ha causato l'interruzione del comando DBCC.|    
|1|È stato generato l'errore numero 8967. Si è verificato un errore DBCC interno.|    
|2|Si è verificato un errore durante un ripristino di database in modalità di emergenza.|    
|3|Indica un danneggiamento dei metadati che ha causato l'interruzione del comando DBCC.|    
|4|È stata rilevata una violazione di accesso o asserzione.|    
|5|Si è verificato un errore sconosciuto che ha causato l'interruzione del comando DBCC.|    
    
## <a name="error-reporting"></a>Segnalazione errori    
Un file di dump (`SQLDUMP*nnnn*.txt`) viene creato nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] directory LOG DBCC CHECKDB rileva un errore di danneggiamento. Quando il *sull'utilizzo delle funzionalità* la raccolta dei dati e *segnalazione* funzionalità sono abilitate per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il file verrà inoltrato automaticamente a [!INCLUDE[msCoName](../../includes/msconame-md.md)]. I dati raccolti consentono di migliorare la funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
Il file di dump contiene i risultati dell'esecuzione del comando DBCC CHECKDB e l'output di dati diagnostici supplementari. L'accesso è limitato al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account e i membri del ruolo sysadmin. Per impostazione predefinita, il ruolo sysadmin contiene tutti i membri di Windows `BUILTIN\Administrators` gruppo e il gruppo Administrators locale. Se il processo di raccolta dei dati non ha esito positivo, l'esecuzione del comando DBCC viene completata comunque.
    
## <a name="resolving-errors"></a>Risoluzione degli errori    
Se vengono rilevati errori da DBCC CHECKDB, è consigliabile ripristinare il database dal backup del database invece di eseguire REPAIR con una delle opzioni REPAIR. Se non esistono backup, l'esecuzione di REPAIR corregge gli errori rilevati. L'opzione REPAIR da utilizzare è specificata al termine dell'elenco degli errori rilevati. La correzione di errori con l'opzione REPAIR_ALLOW_DATA_LOSS, tuttavia, potrebbe richiedere l'eliminazione di alcune pagine, con conseguente perdita di dati.    

In determinate circostanze, nel database possono essere inseriti dei valori non validi o non compresi nell'intervallo dei valori consentiti in base al tipo di dati della colonna. DBCC CHECKDB è in grado di rilevare i valori di colonna non validi per tutti i tipi di dati della colonna. Pertanto, l'esecuzione di DBCC CHECKDB con l'opzione DATA_PURITY per i database aggiornati da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può indicare errori di valori di colonna preesistenti. Poiché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di correggere automaticamente questi errori, il valore della colonna deve essere aggiornato manualmente. Se CHECKDB rileva tale errore, CHECKDB restituisce un avviso di errore numero 2570, nonché le informazioni per identificare la riga interessata e correggere manualmente l'errore.    

È possibile eseguire l'operazione di correzione tramite una transazione utente che consente il rollback delle modifiche apportate. Se si esegue il rollback delle correzioni, il database include ancora errori e deve essere ripristinato da un backup. Dopo il completamento delle correzioni, eseguire il backup del database.
    
## <a name="resolving-errors-in-database-emergency-mode"></a>Risoluzione degli errori in modalità di emergenza per il database    
Quando un database è stata impostata in modalità di emergenza utilizzando il [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) istruzione DBCC CHECKDB può eseguire alcune correzioni speciali nel database se viene specificata l'opzione REPAIR_ALLOW_DATA_LOSS. Grazie a queste correzioni è possibile riportare online database altrimenti irrecuperabili in uno stato consistente dal punto di vista fisico. È consigliabile utilizzarle solo se strettamente necessario e solo se non è possibile ripristinare il database da un backup. Quando il database è impostato in modalità di emergenza, il database è contrassegnato come READ_ONLY, la registrazione è disabilitata e l'accesso è limitato ai membri del ruolo predefinito del server sysadmin.
    
> [!NOTE]
> Non è possibile eseguire il comando DBCC CHECKDB in modalità di emergenza all'interno di una transazione utente, né eseguire il rollback della transazione al termine dell'esecuzione.    
    
Quando il database è in modalità di emergenza e DBCC CHECKDB viene eseguito con la clausola REPAIR_ALLOW_DATA_LOSS, vengono eseguite le azioni seguenti:
-   DBCC CHECKDB utilizza le pagine contrassegnate come inaccessibili a causa di errori di I/O o checksum come se tali errori non si fossero verificati. Questa azione consente di aumentare le possibilità di recupero dei dati del database.    
-   DBCC CHECKDB tenta di recuperare il database mediante tecniche di recupero standard basate su log.    
-   Se il recupero del database ha esito negativo a causa di un problema di danneggiamento del log delle transazioni, verrà ricostruito il log delle transazioni. Tale ricompilazione può provocare la perdita di consistenza delle transazioni.    
    
> [!WARNING]
> L'opzione REPAIR_ALLOW_DATA_LOSS è una funzionalità supportata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tuttavia, non sempre può rappresentare l'opzione migliore per portare un database in uno stato coerente dal punto di vista fisico. Se ha esito positivo, l'opzione REPAIR_ALLOW_DATA_LOSS può comportare una perdita di dati. Infatti, può comportare una perdita maggiore di dati rispetto al ripristino del database dall'ultimo backup valido. [!INCLUDE[msCoName](../../includes/msconame-md.md)]consiglia sempre di un utente di ripristino dall'ultimo backup valido come metodo principale per il recupero da errori segnalati da DBCC CHECKDB. L'opzione REPAIR_ALLOW_DATA_LOSS è **non** alternativa per il ripristino da un backup valido noto. È un'opzione di emergenza che è consigliabile usare solo se non è possibile eseguire il ripristino da un backup.    
>     
>  Dopo la ricompilazione del log non ci sarà alcuna garanzia ACID completa.    
>     
>  Dopo la ricompilazione del log DBCC CHECKDB verrà eseguito automaticamente segnalando e correggendo i problemi di coerenza fisica.    
>     
>  I vincoli applicati alla coerenza dei dati logici e alla logica di business devono essere convalidati manualmente.    
>     
>  Le dimensioni del log delle transazioni rimarranno quelle predefinite e dovranno essere modificate manualmente impostando le dimensioni recenti.    
    
Se il comando DBCC CHECKDB viene eseguito correttamente, il database è in uno stato consistente dal punto di vista fisico e lo stato del database viene impostato su ONLINE. È tuttavia possibile che il database contenga una o più inconsistenze delle transazioni. È consigliabile eseguire [DBCC CHECKCONSTRAINTS](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md) per identificare eventuali difetti della logica di business e immediatamente il backup del database.
Se il comando DBCC CHECKDB non riesce, non è possibile correggere il database.
    
## <a name="running-dbcc-checkdb-with-repairallowdataloss-in-replicated-databases"></a>Esecuzione di DBCC CHECKDB con REPAIR_ALLOW_DATA_LOSS nei database replicati    
L'esecuzione del comando DBCC CHECKDB con l'opzione REPAIR_ALLOW_DATA_LOSS può influire sui database utente (database di pubblicazione e di sottoscrizione) e sul database di distribuzione utilizzato dalla replica. Nei database di pubblicazione e di sottoscrizione sono incluse le tabelle pubblicate e le tabelle di metadati della replica. Per questi database è necessario tenere in considerazione i possibili problemi seguenti:
-   Tabelle pubblicate. Le azioni eseguite dal processo CHECKDB per correggere i dati utente danneggiati potrebbero non essere replicate:    
-   La replica di tipo merge utilizza i trigger per tenere traccia delle modifiche apportate alle tabelle pubblicate. Se il processo CHECKDB inserisce, aggiorna o elimina righe, i trigger non vengono attivati e, di conseguenza, le modifiche non vengono replicate.
-   La replica transazionale utilizza il log delle transazioni per tenere traccia delle modifiche apportate alle tabelle pubblicate. L'agente di lettura log sposta quindi tali modifiche nel database di distribuzione. Nonostante siano registrate, alcune correzioni DBCC non possono essere replicate dall'agente di lettura log. Se ad esempio una pagina di dati viene deallocata dal processo CHECKDB, l'agente di lettura log non associa questa condizione a un'istruzione DELETE. Di conseguenza, la modifica non viene replicata.
-   Tabelle di metadati della replica. Le azioni eseguite dal processo CHECKDB per correggere le tabelle di metadati della replica danneggiate richiedono l'eliminazione e la riconfigurazione della replica.    
    
Se è necessario eseguire il comando DBCC CHECKDB con l'opzione REPAIR_ALLOW_DATA_LOSS su un database utente o di distribuzione:
1.  Mettere in stato di inattività il sistema: arrestare l'attività sul database e su qualsiasi altro database incluso nella topologia di replica, quindi provare a sincronizzare tutti i nodi. Per altre informazioni, vedere [Come mettere una topologia di replica in stato di inattività &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).    
1.  Eseguire DBCC CHECKDB.    
1.  Se il report di DBCC CHECKDB include correzioni relative a tabelle presenti nel database di distribuzione o a tabelle di metadati della replica di un database utente, eliminare e riconfigurare la replica. Per altre informazioni, vedere [Disabilitare la pubblicazione e la distribuzione](../../relational-databases/replication/disable-publishing-and-distribution.md).    
1.  Se il report di DBCC CHECKDB include correzioni relative a tabelle replicate, eseguire la convalida dei dati per determinare la presenza di eventuali differenze tra i dati dei database di pubblicazione e di sottoscrizione.    
    
## <a name="result-sets"></a>Set di risultati    
DBCC CHECKDB restituisce il set di risultati seguente. I valori possono variare, tranne quando vengono specificate le opzioni ESTIMATEONLY, PHYSICAL_ONLY o NO_INFOMSGS:
    
```
 DBCC results for 'model'.    
    
 Service Broker Msg 9675, Level 10, State 1: Message Types analyzed: 13.    
    
 Service Broker Msg 9676, Level 10, State 1: Service Contracts analyzed: 5.    
    
 Service Broker Msg 9667, Level 10, State 1: Services analyzed: 3.    
    
 Service Broker Msg 9668, Level 10, State 1: Service Queues analyzed: 3.    
    
 Service Broker Msg 9669, Level 10, State 1: Conversation Endpoints analyzed: 0.    
    
 Service Broker Msg 9674, Level 10, State 1: Conversation Groups analyzed: 0.    
    
 Service Broker Msg 9670, Level 10, State 1: Remote Service Bindings analyzed: 0.    
    
 DBCC results for 'sys.sysrowsetcolumns'.    
    
 There are 630 rows in 7 pages for object 'sys.sysrowsetcolumns'.    
    
 DBCC results for 'sys.sysrowsets'.    
    
 There are 97 rows in 1 pages for object 'sys.sysrowsets'.    
    
 DBCC results for 'sysallocunits'.    
    
 There are 195 rows in 3 pages for object 'sysallocunits'.    
    
 There are 0 rows in 0 pages for object "sys.sysasymkeys".    
    
 DBCC results for 'sys.syssqlguides'.    
    
 There are 0 rows in 0 pages for object "sys.syssqlguides".    
    
 DBCC results for 'sys.queue_messages_1977058079'.    
    
 There are 0 rows in 0 pages for object "sys.queue_messages_1977058079".    
    
 DBCC results for 'sys.queue_messages_2009058193'.    
    
 There are 0 rows in 0 pages for object "sys.queue_messages_2009058193".    
    
 DBCC results for 'sys.queue_messages_2041058307'.    
    
 There are 0 rows in 0 pages for object "sys.queue_messages_2041058307".    
    
 CHECKDB found 0 allocation errors and 0 consistency errors in database 'model'.    
    
 DBCC execution completed. If DBCC printed error messages, contact your system administrator.    
```

DBCC CHECKDB restituisce il set di risultati (messaggio) seguente quando viene specificato NO_INFOMSGS:
    
```
 The command(s) completed successfully.
 ```
 
DBCC CHECKDB restituisce il set di risultati seguente quando viene specificato PHYSICAL_ONLY:
    
```
 DBCC results for 'model'.    
    
 CHECKDB found 0 allocation errors and 0 consistency errors in database 'master'.  
    
 DBCC execution completed. If DBCC printed error messages, contact your system administrator.
 ```
 
DBCC CHECKDB restituisce il set di risultati seguente quando viene specificato ESTIMATEONLY.
    
```
 Estimated TEMPDB space needed for CHECKALLOC (KB)    
    
 -------------------------------------------------  
    
 13   
    
 (1 row(s) affected)   
    
 Estimated TEMPDB space needed for CHECKTABLES (KB)    
    
 --------------------------------------------------    
    
 57 
    
 (1 row(s) affected)  
    
 DBCC execution completed. If DBCC printed error messages, contact your system administrator.
```
    
## <a name="permissions"></a>Autorizzazioni    
È richiesta l'appartenenza del ruolo predefinito del server sysadmin o db_owner del database.
    
## <a name="examples"></a>Esempi    
    
### <a name="a-checking-both-the-current-and-another-database"></a>A. Controllo del database corrente e di un altro database    
Nell'esempio seguente viene eseguito `DBCC CHECKDB` per il database corrente e per il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
    
```sql    
-- Check the current database.    
DBCC CHECKDB;    
GO    
-- Check the AdventureWorks2012 database without nonclustered indexes.    
DBCC CHECKDB (AdventureWorks2012, NOINDEX);    
GO    
```    
    
### <a name="b-checking-the-current-database-suppressing-informational-messages"></a>B. Controllo del database corrente, con la disattivazione dei messaggi informativi    
Nell'esempio seguente viene verificato il database corrente e vengono soppressi tutti i messaggi informativi.
    
```sql    
DBCC CHECKDB WITH NO_INFOMSGS;    
GO    
```    
    
## <a name="see-also"></a>Vedere anche    
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Visualizzare le dimensioni del file sparse di uno snapshot del database &#40;Transact-SQL&#41;](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)  
[sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)  
[System Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  

