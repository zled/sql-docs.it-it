---
title: DBCC CHECKTABLE (Transact-SQL) | Documenti Microsoft
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKTABLE_TSQL
- DBCC_CHECKTABLE_TSQL
- DBCC CHECKTABLE
- CHECKTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], DBCC CHECKTABLE
- page integrity checks [SQL Server]
- consistency [SQL Server], tables
- consistency [SQL Server], indexed views
- DBCC CHECKTABLE statement
- integrity [SQL Server]
- low overhead checks
- table integrity checks [SQL Server]
ms.assetid: 0d6cb620-eb58-4745-8587-4133a1b16994
caps.latest.revision: 89
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: af19e042e9e40bd92352a175394c442431959b0e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-checktable-transact-sql"></a>DBCC CHECKTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Controlla l'integrità di tutte le pagine e strutture che compongono la tabella o vista indicizzata.
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
    
## <a name="syntax"></a>Sintassi    
    
```sql
    
DBCC CHECKTABLE     
(    
    table_name | view_name    
    [ , { NOINDEX | index_id }    
     |, { REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD }     
    ]     
)    
    [ WITH     
        { ALL_ERRORMSGS ]    
          [ , EXTENDED_LOGICAL_CHECKS ]     
          [ , NO_INFOMSGS ]    
          [ , TABLOCK ]     
          [ , ESTIMATEONLY ]     
          [ , { PHYSICAL_ONLY | DATA_PURITY } ]     
          [ , MAXDOP = number_of_processors ]    
        }    
    ]    
```    
    
## <a name="arguments"></a>Argomenti    
 *TABLE_NAME* | *view_name*  
 Tabella o vista indicizzata per cui si desidera eseguire i controlli di integrità. I nomi di tabella o vista devono essere conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
    
 NOINDEX  
 Specifica che non è necessario eseguire controlli estesi di indici non cluster per le tabelle utente. In questo modo, è possibile ridurre i tempi di esecuzione complessivi. NOINDEX non influisce sulle tabelle di sistema perché i controlli di integrità vengono sempre eseguiti su tutti gli indici delle tabelle di sistema.  
    
 *index_id*  
 Numero di identificazione (ID) dell'indice per cui eseguire i controlli di integrità. Se *index_id* viene specificato, DBCC CHECKTABLE esegue controlli di integrità solo su tale indice, con l'indice cluster o heap.  
    
 REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD  
 Specifica che DBCC CHECKTABLE corregge gli errori rilevati. Per utilizzare un'opzione di correzione, è necessario che il database sia in modalità utente singolo.  
    
 REPAIR_ALLOW_DATA_LOSS  
 Tenta di riparare tutti gli errori rilevati. Le operazioni di correzione possono comportare la perdita di dati.  
    
 REPAIR_FAST  
 La sintassi è stata mantenuta solo a scopo di compatibilità con le versioni precedenti. Non vengono eseguite correzioni.  
    
 REPAIR_REBUILD  
 Esegue operazioni di ripristino senza possibilità di perdita dei dati. Sono incluse operazioni di ripristino rapide, ad esempio ripristino di righe mancanti in indici non cluster, e operazioni che richiedono una maggiore quantità di tempo, come la ricompilazione di un indice.  
 Questo argomento non in grado di correggere errori relativi ai dati FILESTREAM.  
    
 > [!NOTE]  
 >  Utilizzare le opzioni REPAIR solo come ultima risorsa. Per correggere gli errori, è consigliabile eseguire un ripristino da un backup. Le operazioni di correzione non tengono conto degli eventuali vincoli esistenti per le tabelle o tra le tabelle. Se la tabella specificata è interessata da uno o più vincoli, è consigliabile eseguire DBCC CHECKCONSTRAINTS dopo l'operazione di correzione. Se è necessario utilizzare REPAIR, eseguire DBCC CHECKTABLE senza opzioni di correzione per individuare il livello di correzione da applicare. Se si prevede di utilizzare il livello REPAIR_ALLOW_DATA_LOSS, è consigliabile eseguire il backup del database prima di utilizzare DBCC CHECKTABLE con questa opzione.  
    
 ALL_ERRORMSGS  
 Visualizza un numero illimitato di errori. Tutti i messaggi di errore vengono visualizzati per impostazione predefinita. La specifica o l'omissione di questa opzione non ha alcun effetto.  
    
 EXTENDED_LOGICAL_CHECKS  
 Se il livello di compatibilità è 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) o maggiore, esegue controlli di consistenza logica in una vista indicizzata, indici XML e indici spaziali, dove presenti.  
 Per ulteriori informazioni, vedere "Esecuzione di controlli di consistenza logica negli indici" nella sezione "Osservazioni" più avanti in questo argomento.  
    
 NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
    
 TABLOCK  
 Impone l'acquisizione di un blocco condiviso a livello di tabella per l'esecuzione di DBCC CHECKTABLE, anziché utilizzare uno snapshot interno del database. TABLOCK consente l'esecuzione più rapida di DBCC CHECKTABLE in una tabella con carico di lavoro elevato, ma comporta una diminuzione del livello di concorrenza della tabella durante l'esecuzione di DBCC CHECKTABLE.  
    
 ESTIMATEONLY  
 Visualizza la quantità stimata di spazio di tempdb necessaria per eseguire DBCC CHECKTABLE con tutte le altre opzioni specificate.  
    
 PHYSICAL_ONLY  
 Limita il controllo di integrità alla struttura fisica della pagina, alle intestazioni dei record e alla struttura fisica degli alberi B. Progettato per consentire un controllo a basso overhead della consistenza fisica della tabella, questo controllo consente inoltre di rilevare le pagine incomplete e i comuni problemi a livello di hardware che possono compromettere i dati. Un'esecuzione completa di DBCC CHECKTABLE può richiedere tempi notevolmente più lunghi rispetto alle versioni precedenti, per i seguenti motivi:  
 -   I controlli logici sono più completi.  
 -   Alcune delle strutture sottostanti da controllare sono più complesse.  
 -   Sono stati introdotti molti nuovi controlli per includere le nuove funzionalità.  
   
 Per questo motivo, l'utilizzo dell'opzione PHYSICAL_ONLY può consentire di ottenere tempi molto più brevi per l'esecuzione di DBCC CHECKTABLE su tabelle di grandi dimensioni ed è quindi l'opzione consigliata per l'esecuzione frequente nei sistemi di produzione. È tuttora consigliabile prevedere periodicamente un'esecuzione completa di DBCC CHECKTABLE. La frequenza di esecuzione dipende da fattori specifici per i singoli ambienti aziendali e di produzione. L'opzione PHYSICAL_ONLY implica sempre l'utilizzo dell'opzione NO_INFOMSGS e non è consentita con le opzioni di correzione.  
    
 > [!NOTE]  
 >  Se si specifica PHYSICAL_ONLY, DBCC CHECKTABLE ignora tutti i controlli dei dati FILESTREAM.  
    
 DATA_PURITY  
 Consente a DBCC CHECKTABLE di controllare la tabella per individuare valori di colonna non validi o non compresi nell'intervallo dei valori consentiti. Ad esempio, DBCC CHECKTABLE rileva le colonne con valori di data e ora maggiori sono minori dell'intervallo accettabile per il **datetime** tipo di dati, o **decimale** o tipo di dati numerici approssimati colonne con valori di precisione o scala che non sono validi.  
 I controlli di integrità dei valori di colonna sono abilitati per impostazione predefinita e non richiedono l'opzione DATA_PURITY. Per i database aggiornati da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile utilizzare DBCC CHECKTABLE WITH DATA_PURITY per individuare e correggere gli errori in una specifica tabella. I controlli dei valori di colonna nella tabella, tuttavia, non vengono abilitati per impostazione predefinita fino a quando DBCC CHECKDB WITH DATA_PURITY non è stato eseguito senza errori nel database. A questo punto, DBCC CHECKDB e DBCC CHECKTABLE controllano l'integrità dei valori di colonna per impostazione predefinita.  
 Gli errori di convalida rilevati da questa opzione non possono essere corretti utilizzando le opzioni di correzione DBCC. Per informazioni sulla correzione manuale di questi errori, vedere l'articolo 923247 della Knowledge Base: [risoluzione dell'errore DBCC 2570 in SQL Server 2005 e versioni successive](http://support.microsoft.com/kb/923247).  
 Se si specifica PHYSICAL_ONLY, i controlli di integrità di colonna non vengono eseguiti.  
    
 MAXDOP  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 SP2 tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
 Esegue l'override di **massimo grado di parallelismo** opzione di configurazione di **sp_configure** per l'istruzione. Il MAXDOP può superare il valore configurato con sp_configure. Se MAXDOP supera il valore configurato con Resource Governor, il motore di Database utilizza il valore MAXDOP di Resource Governor, descritto in ALTER WORKLOAD GROUP (Transact-SQL). Quando si utilizza l'hint per la query MAXDOP sono valide tutte le regole semantiche utilizzate con l'opzione di configurazione max degree of parallelism. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
    
 > [!CAUTION]  
 >  Se MAXDOP è impostato su zero, il server sceglie il grado massimo di parallelismo.  
    
## <a name="remarks"></a>Osservazioni    
    
> [!NOTE]    
>  Per eseguire DBCC CHECKTABLE su ogni tabella nel database, utilizzare [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).    
    
DBCC CHECKTABLE esegue i controlli seguenti per la tabella specificata:
-   Collegamenti corretti per le pagine di dati di indice, all'interno di righe, LOB e di overflow della riga.    
-   Ordinamento corretto degli indici.    
-   Consistenza dei puntatori.    
-   Presenza di dati accettabili in ogni pagina, incluse le colonne calcolate.    
-   Presenza di offset di pagina accettabili.    
-   A ogni riga nella tabella di base corrisponde una riga in ogni indice non cluster e viceversa.    
-   Ogni riga in una tabella o un indice partizionato è inclusa nella partizione corretta.    
-   Collegamento a livello di coerenza tra il file system e una tabella quando si archiviano **varbinary (max)** dati nel file system utilizzando FILESTREAM.    
    
## <a name="performing-logical-consistency-checks-on-indexes"></a>Esecuzione di controlli di consistenza logica negli indici    
I controlli di consistenza logica negli indici variano in base al livello di compatibilità del database, come indicato di seguito:
-   Se il livello di compatibilità è 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) o maggiore:    
    -   A meno che non venga specificato NOINDEX, tramite DBCC CHECKTABLE vengono eseguiti controlli di consistenza sia fisica che logica in una singola tabella e in tutti i relativi indici non cluster. Per impostazione predefinita, tuttavia, negli indici XML, negli indici spaziali e nelle viste indicizzate vengono eseguiti solo controlli di consistenza fisica.    
    -   Se viene specificato WITH EXTENDED_LOGICAL_CHECKS, vengono eseguiti controlli logici in una vista indicizzata, indici XML e indici spaziali, dove presenti. Per impostazione predefinita, i controlli di consistenza fisica vengono eseguiti prima di quelli di consistenza logica. Se viene specificato anche NOINDEX, vengono eseguiti solo i controlli logici.    
         Tramite questi controlli di consistenza logica vengono eseguiti controlli incrociati della tabella degli indici interna dell'oggetto Index con la tabella utente a cui viene fatto riferimento. Per trovare le righe esterne, viene creata una query interna per eseguire un'intersezione completa della tabella interna e della tabella utente. L'esecuzione di questa query può influire notevolmente sulle prestazioni e non è possibile tenere traccia del relativo stato di avanzamento. È pertanto consigliabile specificare WITH EXTENDED_LOGICAL_CHECKS solo se si sospetta la presenza di problemi dell'indice non correlati a danni fisici o se i checksum a livello di pagina sono stati disabilitati e si sospetta la presenza di danni hardware a livello di colonna.    
    -   Se l'indice è un indice filtrato, tramite DBCC CHECKDB vengono eseguiti controlli di consistenza per verificare che le voci di indice soddisfino il predicato del filtro.   
      
- A partire da SQL Server 2016, controlli aggiuntivi in colonne calcolate persistenti, le colonne di tipo definito dall'utente e gli indici filtrati non verranno eseguito per impostazione predefinita per evitare le valutazioni di espressione costosa. Questa modifica riduce la durata di CHECKDB su database che contiene tali oggetti. Tuttavia, i controlli di consistenza fisica di questi oggetti viene sempre completata. Solo quando è specificata l'opzione EXTENDED_LOGICAL_CHECKS verranno le valutazioni di espressione eseguite oltre ai controlli di logici è già presenti (vista indicizzata, indici XML e indici spaziali) come parte dell'opzione EXTENDED_LOGICAL_CHECKS.
-  Se il livello di compatibilità è 90 o minore, a meno che non venga specificato NOINDEX, tramite DBCC CHECKTABLE vengono eseguiti controlli di consistenza sia fisica che logica in una singola tabella o vista indicizzata e in tutti i relativi indici non cluster e XML. Gli indici spaziali non sono supportati.
    
 **Per informazioni sul livello di compatibilità di un database**    
[Visualizzare o modificare il livello di compatibilità di un database](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)    
    
## <a name="internal-database-snapshot"></a>Snapshot di database interno    
DBCC CHECKTABLE utilizza uno snapshot interno del database per garantire la consistenza transazionale necessaria per l'esecuzione di questi controlli. Per ulteriori informazioni, vedere [visualizzare le dimensioni del File Sparse di uno Snapshot del Database &#40; Transact-SQL &#41; ](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) e la sezione "DBCC dell'utilizzo di Snapshot interno del Database" in [DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-transact-sql.md).
Se non è possibile creare uno snapshot o se viene specificato TABLOCK, DBCC CHECKTABLE acquisisce un blocco condiviso a livello di tabella per ottenere la consistenza necessaria.
    
> [!NOTE]    
> Se si esegue DBCC CHECKTABLE in tempdb, è necessario acquisire un blocco condiviso. Questo funzionamento dipende dal fatto che per motivi di prestazioni gli snapshot di database non sono disponibili in tempdb. Ciò significa che non è possibile ottenere la consistenza delle transazioni necessaria.    
    
## <a name="checking-and-repairing-filestream-data"></a>Controllo e ripristino dei dati FILESTREAM    
Se FILESTREAM è abilitato per un database e una tabella, è possibile archiviare facoltativamente **varbinary (max)** oggetti binari di grandi dimensioni (BLOB) nel file system. Quando si utilizza DBCC CHECKTABLE in una tabella tramite cui vengono archiviati oggetti BLOB nel file system, tramite DBCC viene verificata la consistenza a livello di collegamenti tra il file system e il database.
Ad esempio, se una tabella contiene un **varbinary (max)** colonna che utilizza l'attributo FILESTREAM, DBCC CHECKTABLE viene verificato che sia presente un mapping uno a uno tra directory del file system e i file e le righe delle tabelle, colonne e colonna valori. DBCC CHECKTABLE consente di correggere i danneggiamenti se si specifica l'opzione REPAIR_ALLOW_DATA_LOSS. Per correggere i danneggiamenti relativi a FILESTREAM, DBCC elimina qualsiasi riga di tabella in cui non sono presenti dati del file system e qualsiasi directory e file sui quali non è stato eseguito il mapping a una riga, una colonna o un valore di colonna della tabella.
    
## <a name="checking-objects-in-parallel"></a>Controllo parallelo degli oggetti    
Per impostazione predefinita, DBCC CHECKTABLE esegue un controllo parallelo degli oggetti. Il grado di parallelismo viene determinato in modo automatico da Query Processor. Il grado di parallelismo massimo viene configurato esattamente come per le query parallele. Per limitare il numero massimo di processori disponibili per la verifica DBCC, utilizzare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md). Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).
È possibile disabilitare il controllo parallelo tramite il flag di traccia 2528. Per altre informazioni, vedere [Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).
    
> [!NOTE]    
>  Durante un'operazione DBCC CHECKTABLE i byte archiviati in una colonna con tipo definito dall'utente ordinato per byte devono essere uguali alla serializzazione calcolata del valore con tipo definito dall'utente. Se questa condizione non si verifica, la routine DBCC CHECKTABLE restituirà un errore di consistenza.    
    
## <a name="understanding-dbcc-error-messages"></a>Informazioni sui messaggi di errore DBCC    
Dopo il completamento del comando DBCC CHECKTABLE, nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene scritto un messaggio. Se il comando DBCC viene eseguito correttamente, il messaggio indica il completamento corretto e la durata dell'esecuzione del comando. Se il comando DBCC viene arrestato prima del completamento del controllo a causa di un errore, il messaggio indica che il comando è stato terminato e specifica un valore di stato e la durata dell'esecuzione del comando. Nella tabella seguente sono elencati e descritti i valori di stato che possono essere inclusi nel messaggio.
    
|State|Description|    
|-----------|-----------------|    
|0|È stato generato l'errore numero 8930. Indica che il comando DBCC è stato terminato a causa di un danneggiamento dei metadati.|    
|1|È stato generato l'errore numero 8967. Si è verificato un errore DBCC interno.|    
|2|Si è verificato un errore durante un ripristino di database in modalità di emergenza.|    
|3|Indica che il comando DBCC è stato terminato a causa di un danneggiamento dei metadati.|    
|4|È stata rilevata una violazione di accesso o asserzione.|    
|5|Si è verificato un errore sconosciuto che ha causato l'interruzione del comando DBCC.|    
    
## <a name="error-reporting"></a>Segnalazione errori    
Un file di minidump (denominato SQLDUMP*nnnn*. txt) viene creato nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] directory LOG DBCC CHECKTABLE rileva un errore di danneggiamento. Se le funzionalità di segnalazione degli errori e di raccolta di dati relativi all'utilizzo delle funzionalità sono abilitate per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il file verrà inoltrato automaticamente a [!INCLUDE[msCoName](../../includes/msconame-md.md)]. I dati raccolti consentono di migliorare la funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
Il file di dump contiene i risultati dell'esecuzione del comando DBCC CHECKTABLE e l'output di dati diagnostici supplementari. Il file dispone di elenchi di controllo di accesso discrezionale (DACL) limitati. L'accesso è limitato al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account e i membri del ruolo sysadmin. Per impostazione predefinita, il ruolo sysadmin contiene tutti i membri del gruppo BUILTIN\Administrators di Windows e il gruppo Administrators locale. Se il processo di raccolta dei dati non ha esito positivo, l'esecuzione del comando DBCC viene completata comunque.
    
## <a name="resolving-errors"></a>Risoluzione degli errori    
 Se vengono segnalati errori dopo l'esecuzione di DBCC CHECKTABLE, è consigliabile eseguire il ripristino del database dal backup, anziché eseguire REPAIR con una delle opzioni REPAIR. Se non è disponibile un backup, l'esecuzione di REPAIR può consentire la correzione degli errori segnalati. L'opzione REPAIR da utilizzare viene indicata alla fine dell'elenco degli errori segnalati. Si noti, tuttavia, che la correzione di errori con l'opzione REPAIR_ALLOW_DATA_LOSS potrebbe richiedere l'eliminazione di alcune pagine, con conseguente perdita di dati.    
È possibile eseguire l'operazione di correzione tramite una transazione utente che consente il rollback delle modifiche apportate. Se si esegue il rollback delle correzioni, il database include ancora errori e deve essere ripristinato da un backup. Dopo il completamento di tutte le correzioni, eseguire il backup del database.
    
## <a name="result-sets"></a>Set di risultati    
DBCC CHECKTABLE restituisce il set dei risultati seguente. Viene restituito lo stesso set di risultati se si specifica solo il nome della tabella o qualsiasi opzione.
    
```sql
DBCC results for 'HumanResources.Employee'.    
There are 288 rows in 13 pages for object 'Employee'.    
DBCC execution completed. If DBCC printed error messages, contact your system administrator.    
```    
    
Se si specifica l'opzione ESTIMATEONLY, DBCC CHECKTABLE restituisce il set di risultati seguente:
    
```sql
Estimated TEMPDB space needed for CHECKTABLES (KB)     
--------------------------------------------------     
21    
(1 row(s) affected)    
DBCC execution completed. If DBCC printed error messages, contact your system administrator.    
```    
    
## <a name="permissions"></a>Permissions    
Utente proprietario della tabella oppure essere un membro del ruolo server sysadmin, ruolo predefinito db_owner del database o il ruolo predefinito del database db_ddladmin.    
    
## <a name="examples"></a>Esempi    
    
### <a name="a-checking-a-specific-table"></a>A. Controllo di una tabella specifica    
L'esempio seguente controlla l'integrità di pagina dei dati di `HumanResources.Employee` tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.
    
```sql    
DBCC CHECKTABLE ('HumanResources.Employee');    
GO    
```    
    
### <a name="b-performing-a-low-overhead-check-of-the-table"></a>B. Esecuzione di un controllo della tabella a basso overhead    
 Nell'esempio seguente esegue un controllo a basso overhead del `Employee` tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.    
    
```sql    
DBCC CHECKTABLE ('HumanResources.Employee') WITH PHYSICAL_ONLY;    
GO    
```    
    
### <a name="c-checking-a-specific-index"></a>C. Controllo di un indice specifico    
 Nell'esempio seguente viene eseguito il controllo di un indice specifico, recuperato tramite l'accesso a `sys.indexes`.    
    
```sql    
DECLARE @indid int;    
SET @indid = (SELECT index_id     
              FROM sys.indexes    
              WHERE object_id = OBJECT_ID('Production.Product')    
                    AND name = 'AK_Product_Name');    
DBCC CHECKTABLE ('Production.Product',@indid);    
```    
    
## <a name="see-also"></a>Vedere anche    
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)    
    
  

