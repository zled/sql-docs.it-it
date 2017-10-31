---
title: Istruzione ALTER INDEX (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER INDEX
- ALTER_INDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- indexes [SQL Server], reorganizing
- ALTER INDEX statement
- indexes [SQL Server], disabling
- online index operations
- index reorganization [SQL Server]
- ALLOW_ROW_LOCKS option
- ALL keyword
- reorganizing indexes
- constraints [SQL Server], indexes
- row locks [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- locking [SQL Server], indexes
- partitioned indexes [SQL Server], rebuilding
- defragmenting indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- index modifications [SQL Server]
- indexes [SQL Server], modifying
- index options [SQL Server]
- modifying indexes
- index disabling [SQL Server]
- MAXDOP index option, ALTER INDEX statement
- spatial indexes [SQL Server], modifying
- indexes [SQL Server], options
- ALLOW_PAGE_LOCKS option
- page locks [SQL Server]
ms.assetid: b796c829-ef3a-405c-a784-48286d4fb2b9
caps.latest.revision: 222
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: f61b6469e40ba303cbff14db9bde15161b225ca7
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="alter-index-transact-sql"></a>ALTER INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Consente di modificare un indice di tabella o di vista esistente, di tipo relazionale o XML, tramite la disabilitazione, la ricompilazione o la riorganizzazione dell'indice oppure tramite l'impostazione di opzioni per l'indice.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and SQL Database
  
ALTER INDEX { index_name | ALL } ON <object>  
{  
      REBUILD {  
            [ PARTITION = ALL ] [ WITH ( <rebuild_index_option> [ ,...n ] ) ]   
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_index_option> ) [ ,...n ] ]  
      }  
    | DISABLE  
    | REORGANIZE  [ PARTITION = partition_number ] [ WITH ( <reorganize_option>  ) ]  
    | SET ( <set_index_option> [ ,...n ] )   
    | RESUME [WITH (<resumable_index_options>,[…n])]
    | PAUSE
    | ABORT
}  
[ ; ]  
  
<object> ::=   
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_or_view_name  
}  
  
<rebuild_index_option > ::=  
{  
      PAD_INDEX = { ON | OFF }  
    | FILLFACTOR = fillfactor   
    | SORT_IN_TEMPDB = { ON | OFF }  
    | IGNORE_DUP_KEY = { ON | OFF }  
    | STATISTICS_NORECOMPUTE = { ON | OFF }  
    | STATISTICS_INCREMENTAL = { ON | OFF }  
    | ONLINE = {   
          ON [ ( <low_priority_lock_wait> ) ]   
        | OFF } 
    | RESUMABLE = { ON | OFF } 
    | MAX_DURATION = <time> [MINUTES}     
    | ALLOW_ROW_LOCKS = { ON | OFF }  
    | ALLOW_PAGE_LOCKS = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | COMPRESSION_DELAY = {0 | delay [Minutes]}  
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }   
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]  
}  
  
<single_partition_rebuild_index_option> ::=  
{  
      SORT_IN_TEMPDB = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | RESUMABLE = { ON | OFF } 
    | MAX_DURATION = <time> [MINUTES}     
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE} }  
    | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<reorganize_option>::=  
{  
       LOB_COMPACTION = { ON | OFF }  
    |  COMPRESS_ALL_ROW_GROUPS =  { ON | OFF}  
}  
  
<set_index_option>::=  
{  
      ALLOW_ROW_LOCKS = { ON | OFF }  
    | ALLOW_PAGE_LOCKS = { ON | OFF }  
    | IGNORE_DUP_KEY = { ON | OFF }  
    | STATISTICS_NORECOMPUTE = { ON | OFF }  
    | COMPRESSION_DELAY= {0 | delay [Minutes]}  
}  

<resumable_index_option> ::=
 { 
    MAXDOP = max_degree_of_parallelism
    | MAX_DURATION =<time> [MINUTES]
    | <low_priority_lock_wait>  
 }
 
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                          ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )  
}  

```  
  
```  
-- Syntax for SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER INDEX { index_name | ALL }  
    ON   [ schema_name. ] table_name  
{  
      REBUILD {  
            [ PARTITION = ALL [ WITH ( <rebuild_index_option> ) ] ] 
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_index_option> )] ] 
      }  
    | DISABLE  
    | REORGANIZE [ PARTITION = partition_number ]  
}  
[;]  

<rebuild_index_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]   
}

<single_partition_rebuild_index_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
}  
  
```    
## <a name="arguments"></a>Argomenti  
 *index_name*  
 Nome dell'indice. I nomi di indice devono essere univoci all'interno di una tabella o di una vista, ma non all'interno di un database. I nomi di indice devono rispettare le regole di [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 ALL  
 Specifica tutti gli indici associati alla tabella o alla vista indipendentemente dal tipo di indice. Se viene specificata la parola chiave ALL e uno o più indici si trovano in un filegroup offline o di sola lettura oppure se l'operazione specificata non è consentita per uno o più tipi di indice, l'istruzione ha esito negativo. Nella tabella seguente vengono elencati le operazioni sugli indici e i tipi di indice non supportati.  
  
|Utilizzando la parola chiave ALL con questa operazione|Indici non supportati (l'istruzione ha esito negativo se la tabella include uno o più di questi indici)|  
|----------------------------------------|----------------------------------------|  
|REBUILD WITH ONLINE = ON|Indice XML<br /><br /> Indice spaziale<br /><br /> Indice ColumnStore: **si applica a:** (a partire da SQL Server 2012) di SQL Server e Database SQL di Azure.|  
|REBUILD PARTITION = *numero_partizione*|Indice non partizionato, indice XML, indice spaziale o indice disabilitato|  
|REORGANIZE|Indici con ALLOW_PAGE_LOCKS impostato su OFF|  
|RIORGANIZZA partizione = *numero_partizione*|Indice non partizionato, indice XML, indice spaziale o indice disabilitato|  
|IGNORE_DUP_KEY = ON|Indice XML<br /><br /> Indice spaziale<br /><br /> Indice ColumnStore: **si applica a:** (a partire da SQL Server 2012) di SQL Server e Database SQL di Azure.|  
|ONLINE = ON|Indice XML<br /><br /> Indice spaziale<br /><br /> Indice ColumnStore: **si applica a:** (a partire da SQL Server 2012) di SQL Server e Database SQL di Azure.|
| PUÒ ESSERE RIPRISTINATO = ON  | Gli indici può essere ripristinati non è supportati con **tutti** (parola chiave). <br /><br /> **Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica) |   
  
> [!WARNING]
>  Per ulteriori informazioni sulle operazioni sugli indici che è possibile eseguire online, vedere [linee guida per operazioni sugli indici Online](../../relational-databases/indexes/guidelines-for-online-index-operations.md).

 Se viene specificato ALL con PARTITION = *numero_partizione*, tutti gli indici devono essere allineati. il che significa che devono essere partizionati in base a funzioni di partizione equivalenti. Utilizzo di ALL con PARTITION comporta tutte le partizioni dell'indice con lo stesso *numero_partizione* da ricompilare o riorganizzare. Per ulteriori informazioni sugli indici partizionati, vedere [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 *database_name*  
 Nome del database.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella o la vista.  
  
 *table_or_view_name*  
 Nome della tabella o della vista associata all'indice. Per visualizzare un report degli indici in un oggetto, utilizzare il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo.  
  
 Database SQL supporta il formato di nome di tre parti database_name. table_or_view_name, dove [schema_name] quando nome_database è il database corrente oppure nome_database è tempdb e table_or_view_name inizia con #.  
  
 RICOMPILARE [WITH **(**\<rebuild_index_option > [ **,**... *n*]**)** ]  
 Specifica che l'indice verrà ricompilato con le stesse colonne, lo stesso tipo di indice, lo stesso attributo di univocità e lo stesso tipo di ordinamento. Questa clausola equivale a [DBCC DBREINDEX](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md). REBUILD abilita un indice disabilitato. La ricompilazione di un indice cluster non comporta la ricompilazione degli indici non cluster associati, a meno che non venga specificata la parola chiave ALL. Se non vengono specificate le opzioni di indice, l'indice esistente opzione valori archiviati in [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vengono applicate. Per qualsiasi opzione di indice il cui valore non verrà memorizzato in **Sys. Indexes**, si applica il valore predefinito indicato nella definizione dell'argomento dell'opzione.  
  
 Se viene specificata la parola chiave ALL e la tabella sottostante è un heap, l'operazione di ricompilazione non ha effetto sulla tabella. Vengono ricompilati tutti gli indici non cluster associati alla tabella.  
  
 L'operazione di ricompilazione può essere sottoposta a una registrazione minima se viene utilizzato il modello di recupero del database con registrazione minima o con registrazione minima delle operazioni bulk.  
  
> [!NOTE]
>  Quando si ricompila un indice XML primario, la tabella utente sottostante non è disponibile per tutta la durata dell'operazione sull'indice.  
  
**Si applica a**: (a partire da SQL Server 2012) di SQL Server e Database SQL di Azure.
  
 Per gli indici columnstore, l'operazione di ricompilazione:  
  
1.  Non utilizzare il tipo di ordinamento.  
  
2.  Acquisisce un blocco esclusivo sulla tabella o partizione durante la ricompilazione.  I dati sono "offline" e non disponibili durante la ricompilazione, anche quando si usa NOLOCK, RCSI o SI.  
  
3.  Ricomprime tutti i dati nel columnstore. Durante la ricompilazione esistono due copie dell'indice columnstore. Al termine della ricompilazione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elimina l'indice columnstore originale.  
  
 Per ulteriori informazioni sulla ricompilazione di indici columnstore, vedere [la deframmentazione di indici Columnstore:](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
PARTITION  

**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
 Specifica che verrà ricompilata o riorganizzata solo una partizione di un indice. PARTIZIONE non può essere specificata se *index_name* non è un indice partizionato.  
  
 PARTITION = ALL consente di ricompilare tutte le partizioni.  
  
> [!WARNING]
>  La creazione e la ricompilazione di indici non allineati per una tabella con oltre 1.000 partizioni sono possibili, ma non supportate. Questo tipo di operazioni può causare riduzioni delle prestazioni e un eccessivo consumo della memoria. Quando il numero di partizioni supera 1.000, si consiglia di utilizzare solo indici allineati.  
  
 *numero_partizione*  
   
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.
  
 Numero di partizioni di un indice partizionato da ricompilare o riorganizzare. *numero_partizione* è un'espressione costante che può fare riferimento a variabili. incluse variabili o funzioni con tipo definito dall'utente (UDT) e funzioni definite dall'utente, ma non a istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. *numero_partizione* deve esistere o l'istruzione non riesce.  
  
 CON **(**\<single_partition_rebuild_index_option >**)**  
   
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
 L'opzione SORT_IN_TEMPDB, MAXDOP e DATA_COMPRESSION sono riportate le opzioni che possono essere specificate quando si ricompila una singola partizione (PARTITION =  *n* ). Gli indici XML non possono essere specificati in un'operazione di ricompilazione di una singola partizione.  
  
 DISABLE  
 Contrassegna l'indice come disabilitato e non disponibile per l'utilizzo nel [!INCLUDE[ssDE](../../includes/ssde-md.md)]. È possibile disabilitare qualsiasi indice. La definizione di un indice disabilitato rimane nel catalogo di sistema senza i dati dell'indice sottostante. La disabilitazione di un indice cluster impedisce all'utente di accedere ai dati della tabella sottostante. Per abilitare un indice, utilizzare ALTER INDEX REBUILD oppure CREATE INDEX WITH DROP_EXISTING. Per ulteriori informazioni, vedere [disabilitazione di indici e vincoli](../../relational-databases/indexes/disable-indexes-and-constraints.md) e [Enable Indexes and Constraints](../../relational-databases/indexes/enable-indexes-and-constraints.md).  
  
 RIORGANIZZARE un indice rowstore  
 Per gli indici rowstore, REORGANIZE specifica per riorganizzare il livello foglia dell'indice.  L'operazione di RIORGANIZZAZIONE è:  
  
-   Sempre eseguita online. Ciò significa che i blocchi di tabella a lungo termine non vengono mantenuti attivi e le query o gli aggiornamenti inerenti la tabella sottostante possono continuare durante la transazione ALTER INDEX REORGANIZE.  
  
-   Non è consentita per un indice disabilitato  
  
-   Non è consentita quando ALLOW_PAGE_LOCKS è impostata su OFF  
  
-   Non eseguito il rollback viene eseguito all'interno di una transazione e viene eseguito il rollback della transazione.  
  
REORGANIZE CON **(** LOB_COMPACTION = { **ON** | OFF} **)**  
 Si applica agli indici rowstore.  
  
LOB_COMPACTION = ON  
  
-   Specifica per comprimere tutte le pagine che contengono dati di questi tipi di dati LOB (large object): image, text, ntext, varchar (max), nvarchar (max), varbinary (max) e xml. Compattazione di questi dati, è possibile ridurre le dimensioni dei dati su disco.  
  
-   Per un indice cluster, questo compatta tutte le colonne LOB contenute nella tabella.  
  
-   Per un indice non cluster, questo compatta tutte le colonne LOB che sono colonne non chiave (incluse) nell'indice.  
  
-   RIORGANIZZA tutto esegue LOB_COMPACTION tutti gli indici. Per ogni indice, si compatta tutte le colonne LOB nell'indice cluster, la tabella sottostante o le colonne incluse in un indice non cluster.  
  
LOB_COMPACTION = OFF  
  
-   Le pagine contenenti dati LOB non vengono compattate.  
  
-   OFF non ha alcun effetto su un heap.  
  
RIORGANIZZARE un indice columnstore  
RIORGANIZZAZIONE viene eseguita online.  
  
Per gli indici columnstore, REORGANIZE comprime ogni rowgroup delta chiuso come un gruppo di righe compresso nel columnstore.  
  
-   REORGANIZE non è necessario per spostare i rowgroup delta chiusi in rowgroup compressi. Il processo tuple-mover (TM) in background viene attivato periodicamente per comprimere il rowgroup delta chiuso. Quando è consigliabile usare REORGANIZE tuple-mover è in ritardo. RIORGANIZZAZIONE di gruppi di righe è possibile comprimere in modo più aggressivo.  
  
-   Per comprimere tutti i rowgroup aperto e chiuso, vedere l'opzione REORGANIZE con (COMPRESS_ALL_ROW_GROUPS) in questa sezione.  
  
Per gli indici columnstore in SQL Server (a partire da 2016) e il Database SQL, REORGANIZE esegue le seguenti ottimizzazioni aggiuntive deframmentazione in linea:  
  
-   Rimuove fisicamente le righe da un gruppo di righe quando più di 10% delle righe sono stati eliminati in modo logico. I byte eliminati vengono recuperati sui supporti fisici. Ad esempio, se un gruppo di righe compresso di 1 milione di righe è 100K righe eliminate, SQL Server verrà rimuovere le righe eliminate e ricomprimere il rowgroup con righe k 900. Salva nello spazio di archiviazione rimuovendo le righe eliminate.  
  
-   Consente di combinare uno o più rowgroup compressi per aumentare le righe per rowgroup, il numero massimo di 1,024,576 righe. Ad esempio, se si importano 5 batch di 102.400 righe si otterrà 5 rowgroup compressi. Se si esegue REORGANIZE, questi gruppi di righe verrà viene uniti in rowgroup compressi 1 di 512,000 righe dimensioni. Si presuppone che si sono verificati alcun dizionario dimensioni o limitazioni della memoria.  
  
-   Gruppi di righe in cui più di 10% delle righe è stato in modo logico eliminato, SQL Server tenterà di combinare questo gruppo di righe con uno o più gruppi di righe.    Ad esempio, 1 rowgroup viene compresso con 500.000 righe e 21 rowgroup viene compresso con il numero massimo di 1.048.576 righe.  Rowgroup 21 è 60% delle righe eliminate in modo da lasciare 409,830 righe. Ottimizza per la combinazione di questi due gruppi di righe per comprimere un gruppo di righe nuove 909,830 righe con SQL Server.  
  
RIORGANIZZA MANTENENDO (COMPRESS_ALL_ROW_GROUPS = {ON | **OFF** })  
 In SQL Server (a partire da 2016) e il Database SQL, il COMPRESS_ALL_ROW_GROUPS fornisce un modo per forzare il rowgroup OPEN o CLOSED nel columnstore. Con questa opzione, non è necessario ricompilare l'indice columnstore per svuotare i rowgroup delta.  Questo, combinato con le altre remove e merge deframmentazione funzionalità rende non più necessario ricompilare l'indice nella maggior parte dei casi.    
-   ON impone a tutti i rowgroup in columnstore, indipendentemente dalle dimensioni e lo stato (chiusi o aperti).  
  
-   OFF impone a tutti i rowgroup CLOSED nel columnstore.  
  
IMPOSTARE **(** \<set_index opzione > [ **,**... *n*] **)**  
 Specifica alcune opzioni per l'indice senza ricompilare né riorganizzare l'indice. La parola chiave SET non può essere specificata per un indice disabilitato.  
  
PAD_INDEX = { ON | OFF }  
   
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
 Specifica il riempimento dell'indice. Il valore predefinito è OFF.  
  
 ON  
 La percentuale di spazio disponibile specificata in FILLFACTOR viene applicata alle pagine di livello intermedio dell'indice. Se l'opzione FILLFACTOR non viene specificato nello stesso momento PAD_INDEX è impostata su ON, il riempimento del fattore di valore archiviato nella [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) viene utilizzato.  
  
 DISATTIVARE o *fillfactor* non è specificato  
 Le pagine di livello intermedio vengono riempite poco al di sotto della capacità massima. Lo spazio residuo è sufficiente per almeno una riga della dimensione massima supportata dall'indice, in base al set di chiavi nelle pagine intermedie.  
  
 Per altre informazioni, vedere [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
Fattore di riempimento = *fattore di riempimento*  
 
 **Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.
  
 Specifica una percentuale indicante il livello di riempimento del livello foglia di ogni pagina di indice applicato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o la modifica dell'indice. *fattore di riempimento* deve essere un valore intero compreso tra 1 e 100. Il valore predefinito è 0. I valori 0 e 100 relativi al fattore di riempimento sono equivalenti.  
  
 Un'impostazione esplicita dell'opzione FILLFACTOR viene applicata solo in fase di creazione o ricompilazione dell'indice. La percentuale specificata di spazio vuoto delle pagine non viene mantenuta in modo dinamico da [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Per altre informazioni, vedere [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
 Per visualizzare l'impostazione del fattore di riempimento, utilizzare **Sys. Indexes**.  
  
> [!IMPORTANT]
>  La creazione o la modifica di un indice cluster con un valore FILLFACTOR influisce sulla quantità di spazio di archiviazione occupata dai dati, perché i dati vengono ridistribuiti dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione dell'indice cluster.  
  
 L'OPZIONE SORT_IN_TEMPDB = {ON | **OFF** }  
 

**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
 Specifica se archiviare i risultati dell'ordinamento in **tempdb**. Il valore predefinito è OFF.  
  
 ON  
 I risultati intermedi dell'ordinamento utilizzati per compilare l'indice vengono archiviati **tempdb**. Se **tempdb** è in un diverso set di dischi rispetto al database utente, questo potrebbe ridurre il tempo necessario per creare un indice. La quantità di spazio su disco utilizzata durante la compilazione dell'indice sarà tuttavia maggiore.  
  
 OFF  
 I risultati intermedi dell'ordinamento vengono archiviati nello stesso database dell'indice.  
  
 Se non è necessario eseguire un'operazione di ordinamento oppure se l'ordinamento può essere eseguito in memoria, l'opzione SORT_IN_TEMPDB viene ignorata.  
  
 Per ulteriori informazioni, vedere [opzione SORT_IN_TEMPDB per indici](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md).  
  
 IGNORE_DUP_KEY  **=**  {ON | OFF}  
 Specifica l'errore restituito quando un'operazione di inserimento tenta di inserire valori di chiave duplicati in un indice univoco. L'opzione IGNORE_DUP_KEY viene applicata solo alle operazioni di inserimento eseguite dopo la creazione o la ricompilazione dell'indice. Il valore predefinito è OFF.  
  
 ON  
 Viene visualizzato un messaggio di avviso quando i valori di chiave duplicati vengono inseriti in un indice univoco. Avranno esito negativo solo le righe che violano il vincolo di unicità.  
  
 OFF  
 Viene visualizzato un messaggio di errore quando i valori di chiave duplicati vengono inseriti in un indice univoco. Viene eseguito il rollback dell'intera operazione INSERT.  
  
 Impossibile impostare IGNORE_DUP_KEY su ON per gli indici creati in una vista, gli indici non univoci, gli indici XML, gli indici spaziali e indici filtrati.  
  
 Per visualizzare IGNORE_DUP_KEY, utilizzare [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Per quanto riguarda la sintassi compatibile con le versioni precedenti, WITH IGNORE_DUP_KEY equivale a WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | OFF}  
 Specifica se le statistiche di distribuzione vengono ricalcolate. Il valore predefinito è OFF.  
  
 ON  
 Le statistiche non aggiornate non vengono ricalcolate automaticamente.  
  
 OFF  
 Abilita l'aggiornamento automatico delle statistiche.  
  
 Per ripristinare l'aggiornamento automatico delle statistiche, impostare l'opzione STATISTICS_NORECOMPUTE su OFF oppure eseguire UPDATE STATISTICS senza la clausola NORECOMPUTE.  
  
> [!IMPORTANT]
>  La disabilitazione del ricalcolo automatico delle statistiche di distribuzione può compromettere la selezione di piani di esecuzione ottimali per le query riguardanti la tabella in Query Optimizer.  
  
 STATISTICS_INCREMENTAL = {ON | **OFF** }  
 Quando **ON**, le statistiche create sono di tipo per le statistiche della partizione. Quando **OFF**, l'albero delle statistiche viene eliminato e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ricalcola le statistiche. Il valore predefinito è **OFF**.  
  
 Se le statistiche per partizione non sono supportate, l'opzione viene ignorata e viene generato un avviso. Le statistiche incrementali non sono supportate per i seguenti tipi di statistiche:  
  
-   Statistiche create con indici che non hanno il partizionamento allineato con la tabella di base.  
  
-   Statistiche create per i database secondari leggibili Always On.  
  
-   Statistiche create per i database di sola lettura.  
  
-   Statistiche create per gli indici filtrati.  
  
-   Statistiche create per le viste.  
  
-   Statistiche create per le tabelle interne.  
  
-   Statistiche create con indici spaziali o indici XML.  
  
 
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.  
  
 ONLINE  **=**  {ON | **OFF** } \<come si applica a rebuild_index_option >  
 Specifica se le tabelle sottostanti e gli indici associati sono disponibili per le query e la modifica dei dati durante l'operazione sugli indici. Il valore predefinito è OFF.  
  
 Per un indice XML o spaziale, è supportata solo l'opzione ONLINE = OFF e se ONLINE è impostata su ON viene generato un errore.  
  
> [!NOTE]
>  Le operazioni sugli indici online sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ON  
 I blocchi di tabella a lungo termine non vengono mantenuti per la durata dell'operazione sugli indici. Durante la fase principale dell'operazione viene mantenuto solo un blocco preventivo condiviso (IS, Intent Shared) sulla tabella di origine. In questo modo, le query o gli aggiornamenti relativi alla tabella e agli indici sottostanti possono continuare. All'inizio dell'operazione viene mantenuto brevemente un blocco condiviso (S) sull'oggetto di origine. Al termine dell'operazione, se è in corso la creazione di un indice non cluster, viene mantenuto un blocco S sull'origine per un periodo di tempo molto breve. Se è in corso la creazione o l'eliminazione online di un indice cluster o la ricompilazione di un indice cluster o non cluster, viene acquisito un blocco di modifica dello schema (SCH-M). L'opzione ONLINE non può essere impostata su ON quando viene creato un indice per una tabella temporanea locale.  
  
 OFF  
 I blocchi di tabella vengono applicati per la durata dell'operazione sugli indici. Un'operazione sull'indice offline che crea, ricompila o elimina un indice cluster, spaziale o XML oppure che ricompila o elimina un indice non cluster, acquisisce un blocco di modifica dello schema (SCH-M) sulla tabella. Il blocco impedisce agli utenti di accedere alla tabella sottostante per la durata dell'operazione. Un'operazione sugli indici offline che crea un indice non cluster acquisisce un blocco condiviso (S) sulla tabella. Tale blocco impedisce l'aggiornamento della tabella sottostante ma consente operazioni di lettura, ad esempio l'esecuzione di istruzioni SELECT.  
  
 Per ulteriori informazioni, vedere [come funzionano le operazioni di indice Online](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
 È possibile ricompilare online tutti gli indici, inclusi quelli di tabelle temporanee globali, ad eccezione dei seguenti:  
  
-   Indici XML  
  
-   Indici di tabelle temporanee locali  
  
-   Un subset di un indice partizionato (è possibile ricompilare online un intero indice partizionato).  

-  Database SQL precedenti alla versione 12 e SQL Server precedenti a SQL Server 2012, non consentono il `ONLINE` opzione per la compilazione di indice cluster o ricompilare operazioni quando la tabella di base contiene **varchar (max)** o **varbinary (max)**  colonne.

PUÒ ESSERE RIPRISTINATO  **=**  {ON | **OFF**}

**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)  

 Specifica se un'operazione sull'indice online è ripristinabile.

 INDICE, l'operazione è ripristinabile.

 Operazione non è ripristinabile OFF indice.

MAX_DURATION  **=**  *ora* [**minuti**] utilizzato con **può essere RIPRISTINATO = ON** (richiede **ONLINE = ON**).
 
**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)  

Indica il tempo (valore intero specificato in minuti) che un ripristinabili online operazione di indice viene eseguita prima di essere stato sospeso. 

ALLOW_ROW_LOCKS  **=**  { **ON** | OFF}  
 
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
 Specifica se sono consentiti blocchi di riga. Il valore predefinito è ON.  
  
 ON  
 I blocchi di riga sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi di riga.  
  
 OFF  
 I blocchi di riga non vengono utilizzati.  
  
ALLOW_PAGE_LOCKS  **=**  { **ON** | OFF}  
  
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.
  
 Specifica se sono consentiti blocchi a livello di pagina. Il valore predefinito è ON.  
  
 ON  
 I blocchi a livello di pagina sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi a livello di pagina.  
  
 OFF  
 I blocchi a livello di pagina non vengono utilizzati.  
  
> [!NOTE]
>  Quando l'opzione ALLOW_PAGE_LOCKS è impostata su OFF, non è possibile eseguire operazioni di riorganizzazione degli indici.  
  
 MAXDOP  **=**  max_degree_of_parallelism  
 
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
 Esegue l'override di **massimo grado di parallelismo** opzione di configurazione per la durata dell'operazione sull'indice. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilizzare MAXDOP per limitare il numero di processori utilizzati durante l'esecuzione di un piano parallelo. Il valore massimo è 64 processori.  
  
> [!IMPORTANT]
>  Sebbene l'opzione MAXDOP sia supportata a livello di sintassi per tutti gli indici XML, per un indice XML primario o spaziale ALTER INDEX utilizza attualmente solo un processore singolo.  
  
 *max_degree_of_parallelism* può essere:  
  
 1  
 Disattiva la generazione di piani paralleli.  
  
 \>1  
 Limita il numero massimo di processori utilizzati in un'operazione parallela sull'indice in base al numero specificato.  
  
 0 (predefinito)  
 Utilizza il numero effettivo di processori o un numero inferiore in base al carico di lavoro corrente del sistema.  
  
 Per altre informazioni, vedere [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]
>  Le operazioni parallele sugli indici sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 COMPRESSION_DELAY  **=**  { **0** |*durata [minuti]* }  
 Questa funzionalità è disponibile a partire da SQL Server 2016  
  
 Per una tabella basata su disco, ritardo specifica il numero minimo di minuti che un rowgroup delta in stato di chiusura deve rimanere in rowgroup delta prima di SQL Server può ridurre in rowgroup compressi. Poiché le tabelle basate su disco non tenere traccia delle insert e update volte su singole righe, SQL Server si applica il ritardo in rowgroup delta nello stato CLOSED.  
Il valore predefinito è 0 minuti.  
  
 Il valore predefinito è 0 minuti.  
  
 Per indicazioni su quando usare COMPRESSION_DELAY, vedere gli indici Columnstore per Analitica operativa in tempo reale.  
  
 DATA_COMPRESSION  
 Specifica l'opzione di compressione dei dati per l'indice, il numero di partizione o l'intervallo di partizioni specificato. Sono disponibili le opzioni seguenti:  
  
 Nessuno  
 L'indice o le partizioni specificate non vengono compressi. Non si applica agli indici columnstore.  
  
 ROW  
 L'indice o le partizioni specificate vengono compressi utilizzando la compressione di riga. Non si applica agli indici columnstore.  
  
 PAGE  
 L'indice o le partizioni specificate vengono compressi utilizzando la compressione di pagina. Non si applica agli indici columnstore.  
  
 COLUMNSTORE  
   
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.
  
 Si applica solo agli indici columnstore, inclusi gli indici columnstore cluster e quelli non cluster. COLUMNSTORE specifica di decomprimere l'indice o le partizioni specificate compresse con l'opzione COLUMNSTORE_ARCHIVE. Quando i dati vengono ripristinati, continueranno a essere compressi con la compressione columnstore utilizzata per tutti gli indici columnstore.  
  
 COLUMNSTORE_ARCHIVE  
  
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.
  
 Si applica solo agli indici columnstore, inclusi gli indici columnstore cluster e quelli non cluster. COLUMNSTORE_ARCHIVE comprimerà ulteriormente la partizione specificata a una dimensione inferiore. Può essere utilizzata per l'archiviazione o in altre situazioni in cui sono richieste dimensioni di archiviazione inferiori ed è possibile concedere più tempo per l'archiviazione e il recupero.  
  
 Per ulteriori informazioni sulla compressione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
 PARTIZIONI **(** { \<partition_number_expression > | \<intervallo >} [**,**... n] **)**  
    
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure. 
  
 Specifica le partizioni alle quali si applica l'impostazione DATA_COMPRESSION. Se l'indice non è partizionato, l'argomento ON PARTITIONS genererà un errore. Se la clausola ON PARTITIONS non viene fornita, l'opzione DATA_COMPRESSION si applica a tutte le partizioni di un indice partizionato.  
  
 \<partition_number_expression > possono essere specificati nei modi seguenti:  
  
-   Fornire il numero di una partizione, ad esempio ON PARTITIONS (2).  
  
-   Fornire i numeri di partizione per più partizioni singole separati da virgole, ad esempio ON PARTITIONS (1, 5).  
  
-   Fornire sia intervalli, sia singole partizioni, ad esempio ON PARTITIONS (2, 4, 6 TO 8).  
  
 \<intervallo > possono essere specificati come numeri di partizione separati dalla parola TO, ad esempio: ON PARTITIONS (6 TO 8).  
  
 Per impostare tipi diversi di compressione dei dati per partizioni diverse, specificare più volte l'opzione DATA_COMPRESSION, ad esempio:  
  
```tsql  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
);  
```  
  
 ONLINE  **=**  {ON | **OFF** } \<come si applica a single_partition_rebuild_index_option >  
 Specifica se un indice o una partizione dell'indice di una tabella sottostante può essere ricompilata online o offline. Se **RICOMPILARE** viene eseguita online (**ON**) i dati in questa tabella sono disponibili per query e modifica dei dati durante l'operazione sull'indice.  Il valore predefinito è **OFF**.  
  
 ON  
 I blocchi di tabella a lungo termine non vengono mantenuti per la durata dell'operazione sugli indici. Durante la fase principale dell'operazione viene mantenuto solo un blocco preventivo condiviso (IS, Intent Shared) sulla tabella di origine. All'inizio della ricompilazione dell'indice e un blocco Sch-M nella tabella alla fine della ricompilazione dell'indice online, è necessario un blocco S sulla tabella. Sebbene entrambi i blocchi siano blocchi di metadati brevi, soprattutto il blocco Sch-M deve attendere il completamento di tutte le transazioni bloccanti. Durante il tempo di attesa il blocco Sch-M impedisce tutte le altre transazioni in attesa dietro il blocco stesso per l'accesso alla stessa tabella.  
  
> [!NOTE]
>  Ricompilazione dell'indice online è possibile impostare il *low_priority_lock_wait* opzioni descritte più avanti in questa sezione.  
  
 OFF  
 I blocchi di tabella vengono applicati per la durata dell'operazione sugli indici. Il blocco impedisce agli utenti di accedere alla tabella sottostante per la durata dell'operazione.  
  
 WAIT_AT_LOW_PRIORITY utilizzato con **ONLINE = ON** solo.  
 
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.
  
 Per una ricompilazione di indice online è necessario attendere il blocco delle operazioni su questa tabella. **WAIT_AT_LOW_PRIORITY** indica che l'operazione di ricompilazione indice online rimarrà in attesa dei blocchi con priorità bassa, consentendo alle altre operazioni di continuare mentre è in attesa che l'operazione di compilazione indice online. L'omissione di **WAIT AT LOW PRIORITY** equivale all'opzione `WAIT_AT_LOW_PRIORITY (MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`. Per ulteriori informazioni, vedere [WAIT_AT_LOW_PRIORITY](alter-index-transact-sql.md). 
  
 MAX_DURATION = *ora* [**minuti**]  
  
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.
  
 Il tempo (valore intero specificato in minuti) di attesa con priorità bassa dei blocchi di ricompilazione di indice online durante l'esecuzione del comando DDL. Se l'operazione è bloccata per la **MAX_DURATION** tempo, uno del **ABORT_AFTER_WAIT** azioni verranno eseguite. **MAX_DURATION** ora è sempre espresso in minuti e la parola **minuti** può essere omesso.  
 
 ABORT_AFTER_WAIT = [**NONE** | **SELF** | **BLOCCHI** }]  
   
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.
  
 Nessuno  
 Continuare ad attendere il blocco con priorità normale (regolare).  
  
 SELF  
 Esce dall'operazione DDL di ricompilazione dell'indice online attualmente in esecuzione senza eseguire alcuna azione.  
  
 BLOCKERS  
 Termina tutte le transazioni utente che bloccano l'operazione DDL di ricompilazione dell'indice online in modo da poter continuare l'operazione. Il **BLOCCHI** opzione richiede l'account di accesso **l'autorizzazione ALTER ANY CONNECTION** autorizzazione.  
 
 RESUME 
 
**Si applica a**: a partire da SQL Server 2017 (funzionalità è in anteprima pubblica)

Ripresa di un'operazione sull'indice che è stata sospesa manualmente o a causa di un errore.

MAX_DURATION utilizzato con **può essere RIPRISTINATO = ON**

 
**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)

Il tempo (valore intero specificato in minuti) viene eseguita l'operazione sull'indice online può essere ripristinato dopo viene ripresa. Dopo la scadenza, l'operazione può essere ripristinato è sospeso se è ancora in esecuzione.

WAIT_AT_LOW_PRIORITY utilizzato con **può essere RIPRISTINATO = ON** e **ONLINE = ON**.  
  
**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)
  
 Ripresa di una ricompilazione dell'indice online dopo una pausa deve rimanere in attesa per le operazioni di blocco in questa tabella. **WAIT_AT_LOW_PRIORITY** indica che l'operazione di ricompilazione indice online rimarrà in attesa dei blocchi con priorità bassa, consentendo alle altre operazioni di continuare mentre è in attesa che l'operazione di compilazione indice online. L'omissione di **WAIT AT LOW PRIORITY** equivale all'opzione `WAIT_AT_LOW_PRIORITY (MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`. Per ulteriori informazioni, vedere [WAIT_AT_LOW_PRIORITY](alter-index-transact-sql.md). 


SOSPENDI
 
**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)
  
Sospendere un'operazione di ricompilazione indice online può essere ripristinato.

INTERRUZIONE

**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)   

Interrompere un'operazione di indice in esecuzione o sospesa che è stata dichiarata come ripristinabile. È necessario eseguire in modo esplicito un **ABORT** operazione di ricompilazione di comando per terminare un indice può essere ripristinato. Errore o la sospensione di un'operazione di indice può essere ripristinato non termina l'esecuzione. lascia invece l'operazione in uno stato di sospensione indefinito.
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione ALTER INDEX non può essere utilizzata per ripartizionare un indice o spostarlo in un filegroup diverso né per modificare la definizione dell'indice, ad esempio per aggiungere o eliminare colonne oppure per modificarne l'ordine. Per eseguire queste operazioni, utilizzare CREATE INDEX con la clausola DROP_EXISTING.  
  
 Quando un'opzione non viene specificata in modo esplicito, viene applicata l'impostazione corrente. Se, ad esempio, non viene specificata un'impostazione per FILLFACTOR nella clausola REBUILD, verrà utilizzato il valore del fattore di riempimento archiviato nel catalogo di sistema durante il processo di ricompilazione. Per visualizzare le impostazioni correnti delle opzioni di indice, utilizzare [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
> [!NOTE]
>  I valori di ONLINE, MAXDOP e SORT_IN_TEMPDB non vengono archiviati nel catalogo di sistema. Se non viene specificato un valore nell'istruzione dell'indice, viene utilizzato il valore predefinito dell'opzione.
  
 Nei computer multiprocessore l'istruzione ALTER INDEX REBUILD utilizza automaticamente più processori per eseguire le operazioni di analisi e ordinamento associate alla modifica dell'indice, in modo identico ad altre query. Quando si esegue ALTER INDEX REORGANIZE, con o senza LOB_COMPACTION, il **massimo grado di parallelismo** valore è un'operazione a thread singolo. Per altre informazioni, vedere [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
 Non è possibile riorganizzare o ricompilare indici contenuti in un filegroup offline o di sola lettura. Quando viene specificata la parola chiave ALL e uno o più indici si trovano in un filegroup offline o di sola lettura, l'istruzione ha esito negativo.  
  
## <a name="rebuilding-indexes"></a>Ricompilazione di indici  
 La ricompilazione di un indice consiste nell'eliminazione e nella ricreazione dell'indice. Questa operazione consente di rimuovere la frammentazione, rendere disponibile spazio su disco grazie alla compattazione delle pagine in base all'impostazione del fattore di riempimento esistente o specificata e riordinare le righe dell'indice in pagine contigue. Quando viene specificata la parola chiave ALL, tutti gli indici della tabella vengono eliminati e ricompilati in una singola transazione. Non è necessario eliminare in anticipo i vincoli FOREIGN KEY. Quando vengono ricompilati indici con un numero di extent pari o superiore a 128, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] posticipa le effettive deallocazioni delle pagine e i blocchi associati fino al termine del commit della transazione.  
  
 La ricompilazione o la riorganizzazione degli indici di dimensioni ridotte spesso non riduce la frammentazione. Le pagine di indici di dimensioni ridotte vengono talvolta archiviate in extent misti. Poiché gli extent misti possono essere condivisi al massimo da otto oggetti, la frammentazione in un indice di dimensioni ridotte potrebbe non ridursi dopo la riorganizzazione o la ricompilazione dell'indice.  
  
 A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le statistiche non vengono create analizzando tutte le righe nella tabella quando viene creato o ricompilato un indice partizionato. Query Optimizer utilizza invece l'algoritmo di campionamento predefinito per generare statistiche. Per ottenere statistiche sugli indici partizionati analizzando tutte le righe nella tabella, utilizzare CREATE STATISTICS o UPDATE STATISTICS con la clausola FULLSCAN.  
  
 Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è talvolta possibile ricompilare un indice non cluster per risolvere le incoerenze causate da errori hardware. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e nelle versioni successive, è ancora possibile correggere tali incoerenze tra l'indice e l'indice cluster tramite la ricompilazione di un indice non cluster offline. Non è possibile, tuttavia, correggere le incoerenze di indici non cluster tramite la ricompilazione dell'indice online, in quanto il meccanismo di ricompilazione online utilizza l'indice non cluster esistente come base per la ricompilazione e di conseguenza l'incoerenza persiste. La ricompilazione dell'indice offline può talvolta forzare l'analisi dell'indice cluster (o dell'heap) rimuovendo pertanto l'incoerenza. Per garantire una ricompilazione dall'indice cluster, eliminare e ricreare l'indice non cluster. Come nelle versioni precedenti, il metodo consigliato per il recupero in seguito all'individuazione di incoerenze consiste nel ripristino da backup dei dati interessati. È tuttavia possibile correggere le incoerenze dell'indice tramite la ricompilazione offline dell'indice non cluster. Per altre informazioni, vedere [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).  
  
 Per ricompilare un indice columnstore cluster, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
1.  Acquisisce un blocco esclusivo sulla tabella o partizione durante la ricompilazione. I dati sono "offline" e non disponibili durante la ricompilazione.  
  
2.  Deframmenta il columnstore eliminando fisicamente le righe eliminate in modo logico dalla tabella; i byte eliminati vengono recuperati sui supporti fisici.  
  
3.  Legge tutti i dati dell'indice columnstore originale, incluso il deltastore. Combina i dati in nuovi rowgroup e comprime i rowgroup nel columnstore.  
  
4.  Richiede spazio sul supporto fisico per archiviare due copie dell'indice columnstore durante la ricompilazione. Al termine della ricompilazione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elimina l'indice columnstore cluster originale.  
  
## <a name="reorganizing-indexes"></a>Riorganizzazione di indici  
 La riorganizzazione di un indice richiede una quantità minima di risorse di sistema. Questa operazione deframmenta il livello foglia di indici cluster e non cluster di tabelle e viste tramite il riordinamento fisico delle pagine al livello foglia in base all'ordine logico, da sinistra verso destra, dei nodi foglia. La riorganizzazione consente inoltre di compattare le pagine di indice in base al valore del fattore di riempimento esistente. Per visualizzare l'impostazione del fattore di riempimento, utilizzare [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Quando viene specificata la parola chiave ALL, vengono riorganizzati gli indici relazionali, sia cluster sia non cluster, e gli indici XML della tabella. La parola chiave ALL prevede alcune restrizioni. Per informazioni, vedere la relativa definizione nella sezione Argomenti.  
  
 Per altre informazioni, vedere [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
## <a name="disabling-indexes"></a>Disabilitazione di indici  
 La disabilitazione di un indice impedisce agli utenti di accedere all'indice e, nel caso di indici cluster, ai dati della tabella sottostante. La definizione dell'indice rimane archiviata nel catalogo di sistema. La disabilitazione di un indice non cluster o di un indice cluster di una vista elimina fisicamente i dati dell'indice. La disabilitazione di un indice cluster impedisce l'accesso ai dati, i quali tuttavia rimangono archiviati in forma non gestita nell'albero B fino all'eliminazione o alla ricompilazione dell'indice. Per visualizzare lo stato di un indice abilitato o disabilitato, eseguire una query di **is_disabled** colonna il **Sys. Indexes** vista del catalogo.  
  
 Se una tabella è inclusa in una pubblicazione per la replica transazionale, non è possibile disabilitare gli indici associati a colonne chiave primaria. Questi indici sono necessari per la replica. Per disabilitare un indice, è innanzitutto necessario eliminare la tabella dalla pubblicazione. Per altre informazioni, vedere [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
 Per abilitare l'indice, utilizzare l'istruzione ALTER INDEX REBUILD oppure CREATE INDEX WITH DROP_EXISTING. Quando l'opzione ONLINE è impostata su ON, non è possibile ricompilare un indice cluster disabilitato. Per altre informazioni, vedere [Disabilitazione di indici e vincoli](../../relational-databases/indexes/disable-indexes-and-constraints.md).  
  
## <a name="setting-options"></a>Impostazione delle opzioni  
 È possibile impostare le opzioni ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, IGNORE_DUP_KEY e STATISTICS_NORECOMPUTE per un indice specificato senza ricompilare o riorganizzare l'indice. I valori modificati vengono applicati immediatamente all'indice. Per visualizzare queste impostazioni, utilizzare **Sys. Indexes**. Per altre informazioni vedere [Impostare le opzioni di indice](../../relational-databases/indexes/set-index-options.md).  
  
### <a name="row-and-page-locks-options"></a>Opzioni per blocchi di riga e di pagina  
 Se ALLOW_ROW_LOCKS = ON e ALLOW_PAGE_LOCK = ON, sono consentiti blocchi di riga, di pagina e di tabella per l'accesso all'indice. [!INCLUDE[ssDE](../../includes/ssde-md.md)] sceglie il blocco appropriato e può eseguire un'escalation del blocco da un blocco di riga o di pagina a un blocco di tabella.  
  
 Se ALLOW_ROW_LOCKS = OFF e ALLOW_PAGE_LOCK = OFF, sono consentiti solo blocchi a livello di tabella per l'accesso all'indice.  
  
 Se si specifica la parola chiave ALL durante l'impostazione di opzioni per blocchi di riga o di pagina, le impostazioni vengono applicate a tutti gli indici. Se la tabella sottostante è un heap, le impostazioni vengono applicate nei modi seguenti:  
  
|||  
|-|-|  
|ALLOW_ROW_LOCKS = ON o OFF|Viene applicata all'heap e a tutti gli indici non cluster associati.|  
|ALLOW_PAGE_LOCKS = ON|Viene applicata all'heap e a tutti gli indici non cluster associati.|  
|ALLOW_PAGE_LOCKS = OFF|Viene applicata agli indici non cluster. Ciò significa che negli indici non cluster non è consentito alcun blocco a livello di pagina. Nell'heap non sono consentiti solo i blocchi condivisi (S), di aggiornamento (U) ed esclusivi (X) per la pagina. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] può comunque acquisire un blocco preventivo a livello di pagina (IS, IU o IX) per scopi interni.|  
  
## <a name="online-index-operations"></a>Operazioni sugli indici online  
 Quando si ricompila un indice e l'opzione ONLINE è impostata su ON, gli oggetti sottostanti, ovvero le tabelle e gli indici associati, risultano disponibili per query e operazioni di modifica dei dati. È inoltre possibile ricompilare online una parte di indice che risiede in una singola partizione. I blocchi di tabella esclusivi vengono mantenuti attivi per un periodo di tempo molto limitato durante il processo di modifica.  
  
 La riorganizzazione di un indice viene sempre eseguita online. Questo processo non mantiene attivi i blocchi a lungo termine e non blocca pertanto le query o gli aggiornamenti in corso.  
  
 In una stessa tabella o partizione di tabella è possibile eseguire in modo simultaneo solo le operazioni sugli indici online seguenti:  
  
-   Creazione di più indici non cluster.  
  
-   Riorganizzazione di indici diversi della stessa tabella.  
  
-   Riorganizzazione di indici diversi durante la ricompilazione di indici non sovrapposti della stessa tabella.  
  
 Qualsiasi altra operazione sugli indici online eseguita nello stesso istante avrà esito negativo. Non è ad esempio possibile ricompilare due o più indici della stessa tabella simultaneamente né creare un nuovo indice durante la ricompilazione di un indice esistente nella stessa tabella.  

### <a name="resumable-index-operations"></a>Operazioni sugli indici può essere ripristinato

**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)

RICOSTRUZIONE di un indice ONLINE viene specificato come ripristinabili utilizzando il può essere RIPRISTINATO = opzione. 
-  L'opzione può essere RIPRISTINATO non è persistente nei metadati per un determinato indice e si applica solo alla durata di un'istruzione DDL corrente. Pertanto, il può essere RIPRISTINATO = ON clausola deve essere specificata in modo esplicito affinché funzioni.

-  Tenere presente due diverse opzioni MAX_DURATION. Uno è correlato a low_priority_lock_wait e l'altro è correlato a può essere RIPRISTINATO = opzione.
   -  Opzione MAX_DURATION è supportata per può essere RIPRISTINATO = opzione o **low_priority_lock_wait** argomento opzione. 
   MAX_DURATION per l'opzione può essere RIPRISTINATO specifica l'intervallo di tempo per un indice da ricompilare. Dopo questa fase viene utilizzata la ricompilazione dell'indice è sospesa o completa l'esecuzione. Utente decide quando una ricompilazione per un indice in pausa può essere ripreso. Il **tempo** in minuti per MAX_DURATION deve essere maggiore di 0 minuti e minore o uguale una settimana (7 x 24 x 60 = 10080 minuti). Con un intervallo lungo per un'operazione di indice possono influire sulle prestazioni DML su una tabella specifica, nonché la capacità del disco del database poiché entrambi gli indici di quello di origine e quello appena creato richiede spazio su disco, è necessario aggiornare durante le operazioni DML. Se l'opzione MAX_DURATION viene omessa, l'operazione sull'indice continuerà fino al completamento o fino a quando non si verifica un errore. 
-   Il \<low_priority_lock_wait > argomento consente di decidere come procedere l'operazione sull'indice durante l'attesa sul blocco SCH-M.
 
-  Eseguire nuovamente l'istruzione ALTER INDEX REBUILD originale con gli stessi parametri riprende un'operazione di ricompilazione indice sospesa. È inoltre possibile riprendere un'operazione di ricompilazione indice sospeso tramite l'istruzione ALTER INDEX riprendere.
-  L'opzione SORT_IN_TEMPDB = ON opzione non è supportata per l'indice può essere ripristinato 
-  Il comando DDL con può essere RIPRISTINATO = ON non può essere eseguita all'interno di una transazione esplicita (può far parte di begin tran... blocco di commit).
-  Solo le operazioni sugli indici che sono in pausa sono ripristinabili.
-   Quando si riprende un'operazione sull'indice che è stata sospesa, è possibile modificare il valore MAXDOP per un nuovo valore.  Se MAXDOP non viene specificato quando si riprende un'operazione sull'indice che è stato sospeso, viene eseguita l'ultimo valore MAXDOP. Se l'opzione MAXDOP non è specificato in qualsiasi per l'operazione di ricompilazione dell'indice, verrà usato il valore predefinito.
- Per sospendere immediatamente l'operazione sull'indice, è possibile arrestare il comando in corso (Ctrl-C) o è possibile eseguire il comando ALTER INDEX sospendere o il comando KILL *session_id* comando. Quando viene sospeso il comando può essere ripreso utilizzando l'opzione RESUME.
-  Il comando di interruzione termina la sessione che ospitati la ricompilazione dell'indice originale e interrompe l'operazione di indice  
-  Non sono necessarie per la ricompilazione dell'indice può essere ripristinato, ad eccezione di alcun risorse aggiuntive
   -    Spazio aggiuntivo necessario per mantenere l'indice viene compilato, incluso il tempo in cui è in pausa l'indice
   -    Uno stato DDL impedendo di apportare eventuali modifiche DDL
-  La pulizia fantasma verrà eseguito durante la fase di sospensione di indice, ma viene messa in pausa durante l'esecuzione di indice   
La seguente funzionalità è disabilitata per operazioni di ricompilazione dell'indice può essere ripristinato
   -    Ricompilazione di un indice disabilitato non è supportata con può essere RIPRISTINATO = ON
   -    Comando ALTER INDEX REBUILD ALL
   -    La ricostruzione dell'indice utilizzando ALTER TABLE  
   -    Comando DDL con "RESUMEABLE = ON" non può essere eseguita all'interno di una transazione esplicita (può far parte di begin tran... blocco di commit)
   -    Ricompilare un indice che è calcolato colonne TIMESTAMP come colonne chiave.
-   Nel caso in cui la tabella di base contiene colonne LOB ripristinabili cluster ricompilazione dell'indice richiede un blocco Sch-M all'inizio di questa operazione
   -    L'opzione SORT_IN_TEMPDB = ON opzione non è supportata per l'indice può essere ripristinato 

> [!NOTE]
> Finché non viene completata, viene sospeso o non riesce, viene eseguito il comando DDL. Nel caso in cui il comando mette in pausa, verrà generato un errore che indica che l'operazione è stata sospesa e che non ha completato la creazione dell'indice. Per ottenere ulteriori informazioni sullo stato corrente dell'indice da [sys.index_resumable_operations](../../relational-databases/system-catalog-views/sys-index-resumable-operations.md). Come prima in caso di errore errore verrà generato anche. 

  
 Per altre informazioni, vedere [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md).  
  
 ### <a name="waitatlowpriority-with-online-index-operations"></a>WAIT_AT_LOW_PRIORITY con operazioni sugli indici online  
  
 Per eseguire l'istruzione DDL per una ricompilazione dell'indice online, è necessario completare tutte le transazioni bloccanti attive in esecuzione in una specifica tabella. Quando la ricompilazione dell'indice online viene eseguita, blocca tutte le nuove transazioni pronte per l'esecuzione in questa tabella. Sebbene la durata del blocco della ricompilazione dell'indice online sia molto breve, l'attesa del completamento di tutte le transazioni aperte in una tabella specificata e il blocco dell'avvio di nuove transazioni potrebbero influire in modo significativo sulla velocità effettiva, provocando un rallentamento o un timeout del carico di lavoro e limitando notevolmente l'accesso alla tabella sottostante. Il **WAIT_AT_LOW_PRIORITY** opzione consente agli amministratori di gestire i blocchi di blocco S e Sch-M necessari per un indice online viene ricompilato e consente di selezionare una delle opzioni di 3. In tutti i casi di 3, se durante il tempo di attesa ( `(MAX_DURATION = n [minutes])` ), non sono presenti attività di blocco, la ricompilazione dell'indice online viene eseguita immediatamente senza attendere e l'istruzione DDL è stata completata.  
  
## <a name="spatial-index-restrictions"></a>Restrizioni relative agli indici spaziali  
 Quando si ricompila un indice spaziale, la tabella utente sottostante non è disponibile per tutta la durata dell'operazione sull'indice, in quanto l'indice spaziale acquisisce un blocco di schema.  
  
 Il vincolo PRIMARY KEY nella tabella utente non può essere modificato se in una colonna di tale tabella è definito un indice spaziale. Per modificare il vincolo PRIMARY KEY, eliminare innanzitutto ogni indice spaziale dalla tabella. Dopo avere modificato il vincolo PRIMARY KEY, è possibile ricreare ognuno degli indici spaziali.  
  
 In un'operazione di ricompilazione di una singola partizione, non è possibile specificare indici spaziali. È tuttavia possibile specificare indici spaziali in una ricompilazione di partizioni completa.  
  
 Per modificare opzioni specifiche di un indice spaziale, ad esempio BOUNDING_BOX o GRID, è possibile utilizzare un'istruzione CREATE SPATIAL INDEX che specifica DROP_EXISTING = ON oppure eliminare l'indice spaziale e crearne un nuovo. Per un esempio vedere [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-spatial-index-transact-sql.md).  
  
## <a name="data-compression"></a>Compressione dei dati  
 Per altre informazioni sulla compressione dei dati, vedere [Compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
 Per valutare come la compressione di pagina e riga modifica influirà su una tabella, un indice o una partizione, utilizzare il [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) stored procedure.  
  
 Agli indici partizionati vengono applicate le restrizioni seguenti:  
  
-   Quando si utilizza `ALTER INDEX ALL ...`, non è possibile modificare l'impostazione di compressione di una singola partizione se la tabella include indici non allineati.  
  
-   L'istruzione ALTER INDEX \<indice >... REBUILD PARTITION... consente di ricompilare la partizione specificata dell'indice.  
  
-   L'istruzione ALTER INDEX \<indice >... REBUILD WITH ... consente di ricompilare tutte le partizioni dell'indice.  
  
## <a name="statistics"></a>Statistiche  
 Quando si esegue **ALTER INDEX ALL...** in una tabella, vengono aggiornate solo le statistiche associate agli indici. Le statistiche automatiche o manuali create sulla tabella, anziché su un indice, non vengono aggiornate.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire l'istruzione ALTER INDEX, è necessario disporre almeno dell'autorizzazione ALTER per la tabella o la vista.  
  
## <a name="version-notes"></a>Note sulla versione  
  
-   Database SQL non utilizza le opzioni di filegroup e filestream.  
  
-   Gli indici ColumnStore non sono disponibili prima di SQL Server 2012. 

-  Operazioni sugli indici può essere ripristinato sono disponibili a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica) |   
  
## <a name="basic-syntax-example"></a>Esempio di sintassi di base:   
  
```tsql 
ALTER INDEX index1 ON table1 REBUILD;  
  
ALTER INDEX ALL ON table1 REBUILD;  
  
ALTER INDEX ALL ON dbo.table1 REBUILD;  
```

## <a name="examples-columnstore-indexes"></a>Esempi: Gli indici Columnstore  
 Questi esempi si applicano agli indici columnstore.  
  
### <a name="a-reorganize-demo"></a>A. RIORGANIZZA demo  
 Questo esempio viene illustrato come il comando ALTER INDEX REORGANIZE.  Crea una tabella che dispone di più gruppi di righe e quindi viene illustrata la modalità REORGANIZE unisce i rowgroup.  
  
```  
-- Create a database   
CREATE DATABASE [ columnstore ];  
GO  
  
-- Create a rowstore staging table  
CREATE TABLE [ staging ] (  
     AccountKey              int NOT NULL,  
     AccountDescription      nvarchar (50),  
     AccountType             nvarchar(50),  
     AccountCodeAlternateKey     int  
     )  
  
-- Insert 10 million rows into the staging table.   
DECLARE @loop int  
DECLARE @AccountDescription varchar(50)  
DECLARE @AccountKey int  
DECLARE @AccountType varchar(50)  
DECLARE @AccountCode int  
  
SELECT @loop = 0  
BEGIN TRAN  
    WHILE (@loop < 300000)   
      BEGIN  
        SELECT @AccountKey = CAST (RAND()*10000000 as int);  
        SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
        SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
        SELECT @AccountCode =  CAST (RAND()*10000000 as int);  
  
        INSERT INTO  staging VALUES (@AccountKey, @AccountDescription, @AccountType, @AccountCode);  
  
        SELECT @loop = @loop + 1;  
    END  
COMMIT  
  
-- Create a table for the clustered columnstore index  
  
CREATE TABLE cci_target (  
     AccountKey              int NOT NULL,  
     AccountDescription      nvarchar (50),  
     AccountType             nvarchar(50),  
     AccountCodeAlternateKey int  
     )  
  
-- Convert the table to a clustered columnstore index named inxcci_cci_target;  
```tsql
CREATE CLUSTERED COLUMNSTORE INDEX idxcci_cci_target ON cci_target;  
```  
  
 Utilizzare l'opzione TABLOCK per inserire righe in parallelo. A partire da SQL Server 2016, l'operazione INSERT INTO può eseguire in parallelo quando TABLOCK.  
  
```tsql  
INSERT INTO cci_target WITH (TABLOCK) 
SELECT TOP 300000 * FROM staging;  
```  
  
 Eseguire questo comando per visualizzare i rowgroup delta aperto. Il numero di rowgroup dipende dal grado di parallelismo.  
  
```tsql  
SELECT *   
FROM sys.dm_db_column_store_row_group_physical_stats   
WHERE object_id  = object_id('cci_target');  
```  
  
 Eseguire questo comando per forzare tutti i rowgroup OPEN e CLOSED nel columnstore.  
  
```tsql  
ALTER INDEX idxcci_cci_target ON cci_target REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
 Eseguire nuovamente il comando per visualizzare più piccoli gruppi di righe vengono unite in un rowgroup compressi.  
  
```tsql  
ALTER INDEX idxcci_cci_target ON cci_target REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
### <a name="b-compress-closed-delta-rowgroups-into-the-columnstore"></a>B. Comprimere il rowgroup delta chiusi nel columnstore  
 Questo esempio viene utilizzata la RIORGANIZZAZIONE opzione comprime ogni rowgroup delta chiuso nel columnstore come un gruppo di righe compresso.   Non è necessaria, ma è utile quando il motore di tuple non sta comprimendo sufficientemente rapido dei rowgroup chiuso.  
  
```tsql  
-- Uses AdventureWorksDW  
-- REORGANIZE all partitions  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE;  
  
-- REORGANIZE a specific partition  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE PARTITION = 0;  
```  
  
### <a name="c-compress-all-open-and-closed-delta-rowgroups-into-the-columnstore"></a>C. Comprimere tutti i rowgroup delta aperto e chiuso nel columnstore  
 Non si applica a: SQL Server 2012 e 2014  
  
 A partire da SQL Server 2016, è possibile eseguire REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON) per comprimere ogni rowgroup delta aperto e chiuso in columnstore come un gruppo di righe compresso.    Questo Svuota il deltastore e forza tutte le righe per ottenere compressi nel columnstore. Ciò risulta utile in particolare dopo l'esecuzione di molte operazioni di inserimento poiché queste operazioni archiviano le righe di uno o più deltastore.  
  
 REORGANIZE combina rowgroup per riempire i rowgroup fino a un numero massimo di righe \<= 1,024,576. Pertanto, quando si comprime tutti i rowgroup aperto e chiuso non alla fine si con un numero elevato di rowgroup compressi che hanno solo poche righe in esse contenuti. Si desidera rowgroup come complete possibile in modo da ridurre la dimensione compressa e migliorare le prestazioni delle query.  
  
```tsql  
-- Uses AdventureWorksDW2016  
-- Move all OPEN and CLOSED delta rowgroups into the columnstore.  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
-- For a specific partition, move all OPEN AND CLOSED delta rowgroups into the columnstore  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE PARTITION = 0 WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
### <a name="d-defragment-a-columnstore-index-online"></a>D. Deframmentare un indice columnstore online  
 Non si applica a: SQL Server 2012 e 2014.  
  
 A partire da SQL Server 2016, REORGANIZE comprimere più rowgroup nel columnstore. Esegue inoltre la deframmentazione in linea. In primo luogo, riduce le dimensioni dell'archivio colonne rimuovendo le righe eliminate dopo aver eliminato più di 10% delle righe in un gruppo di righe.  Quindi, combina rowgroup per formare gruppi di righe più grande che è necessario il numero massimo di 1,024,576 righe per rowgroup.  Tutti i gruppi di righe che sono stati modificati nuovamente compresse.  
  
> [!NOTE]
>  A partire da SQL Server 2016, la ricompilazione di un indice columnstore non è più necessaria nella maggior parte dei casi perché REORGANIZE fisicamente rimuove le righe eliminate e unisce i gruppi di righe. L'opzione COMPRESS_ALL_ROW_GROUPS forza tutti i rowgroup delta OPEN o CLOSED nel columnstore che in precedenza poteva essere eseguito solo con una ricompilazione.   RIORGANIZZAZIONE è online e si verifica in background in modo che le query possono continuare quando viene eseguita l'operazione.  
  
```tsql  
-- Uses AdventureWorks  
-- Defragment by physically removing rows that have been logically deleted from the table, and merging rowgroups.  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE;  
```  
  
### <a name="e-rebuild-a-clustered-columnstore-index-offline"></a>E. Ricompilare un indice columnstore cluster non in linea  
 Si applica a: SQL Server 2012, SQL Server 2014  
  
 A partire da SQL Server 2016 e in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], è consigliabile utilizzare ALTER INDEX REORGANIZE anziché l'istruzione ALTER INDEX REBUILD.  
  
> [!NOTE]
>  In SQL Server 2012 e 2014, RIORGANIZZAZIONE viene utilizzato solo per comprimere il rowgroup CLOSED nel columnstore. L'unico modo per eseguire operazioni di deframmentazione in linea e per forzare tutti i rowgroup in columnstore consiste nella ricompilazione dell'indice.  
  
 In questo esempio viene illustrato come ricompilare un indice columnstore cluster e forzare tutti i rowgroup in columnstore. Il primo passaggio consiste nel preparare una tabella FactInternetSales2 con un indice columnstore cluster e nell'inserimento di dati dalle prime quattro colonne.  
  
```tsql  
-- Uses AdventureWorksDW  
  
CREATE TABLE dbo.FactInternetSales2 (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
  
CREATE CLUSTERED COLUMNSTORE INDEX cci_FactInternetSales2  
ON dbo.FactInternetSales2;  
  
INSERT INTO dbo.FactInternetSales2  
SELECT ProductKey, OrderDateKey, DueDateKey, ShipDateKey  
FROM dbo.FactInternetSales;  
  
SELECT * FROM sys.column_store_row_groups;  
```  
  
 I risultati mostrano che è presente un rowgroup OPEN, ovvero [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rimarrà in attesa di più righe da aggiungere prima della chiusura del rowgroup e sposta i dati columnstore. Questa istruzione successiva si ricompila l'indice columnstore cluster, che impone a tutte le righe nel columnstore.  
  
```tsql  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REBUILD;  
SELECT * FROM sys.column_store_row_groups;  
```  
  
 I risultati dell'istruzione SELECT mostrano che il rowgroup è COMPRESSED, il che significa che i segmenti di colonna del rowgroup vengono compressi e archiviati nel columnstore.  
  
### <a name="f-rebuild-a-partition-of-a-clustered-columnstore-index-offline"></a>F. Ricompilare una partizione di un indice columnstore cluster non in linea  
 Utilizzare questa opzione per: SQL Server 2012, SQL Server 2014  
  
 Per ricompilare una partizione di un indice columnstore cluster di grandi dimensioni, utilizzare ALTER INDEX REBUILD con l'opzione di partizione. Questo esempio viene ricompilato partizione 12. A partire da SQL Server 2016, è consigliabile sostituire RICOMPILAZIONE con REORGANIZE.  
  
```tsql  
ALTER INDEX cci_fact3   
ON fact3  
REBUILD PARTITION = 12;  
```  
  
### <a name="g-change-a-clustered-columstore-index-to-use-archival-compression"></a>G. Modificare un indice cluster per utilizzare la compressione dell'archivio  
 Non si applica a: SQL Server 2012  
  
 È possibile scegliere di ridurre le dimensioni di un indice columnstore cluster ulteriormente tramite l'opzione di compressione dati COLUMNSTORE_ARCHIVE. Si tratta di una pratica per i dati meno recenti che si desidera mantenere nell'archiviazione più economica. È consigliabile solo utilizzando questo sui dati che non si accede spesso poiché decomprimere è più lenta con la compressione COLUMNSTORE normale.  
  
 Nell'esempio seguente viene ricompilato un indice columnstore cluster per l'utilizzo della compressione dell'archivio e viene illustrato come rimuovere tale compressione. Il risultato finale consisterà nell'utilizzo della sola compressione columnstore.  
  
```tsql  
--Prepare the example by creating a table with a clustered columnstore index.  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL  
);  
  
CREATE CLUSTERED INDEX cci_SimpleTable ON SimpleTable (ProductKey);  
  
CREATE CLUSTERED COLUMNSTORE INDEX cci_SimpleTable  
ON SimpleTable  
WITH (DROP_EXISTING = ON);  
  
--Compress the table further by using archival compression.  
ALTER INDEX cci_SimpleTable ON SimpleTable  
REBUILD  
WITH (DATA_COMPRESSION = COLUMNSTORE_ARCHIVE);  
  
--Remove the archive compression and only use columnstore compression.  
ALTER INDEX cci_SimpleTable ON SimpleTable  
REBUILD  
WITH (DATA_COMPRESSION = COLUMNSTORE);  
GO  
```  
  
## <a name="examples-rowstore-indexes"></a>Esempi: Gli indici Rowstore  
  
### <a name="a-rebuilding-an-index"></a>A. Ricompilazione di un indice  
 Nell'esempio seguente viene ricompilato un singolo indice della tabella `Employee` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql  
ALTER INDEX PK_Employee_EmployeeID ON HumanResources.Employee REBUILD;  
```  
  
### <a name="b-rebuilding-all-indexes-on-a-table-and-specifying-options"></a>B. Ricompilazione di tutti gli indici di una tabella e impostazione di opzioni  
 Nell'esempio seguente viene specificata la parola chiave `ALL`. In questo modo vengono ricompilati tutti gli indici associati alla tabella Production.Product nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Vengono inoltre specificate tre opzioni.  
  
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
```tsql  
ALTER INDEX ALL ON Production.Product  
REBUILD WITH (FILLFACTOR = 80, SORT_IN_TEMPDB = ON, STATISTICS_NORECOMPUTE = ON);  
```  
  
 Nell'esempio seguente viene aggiunta l'opzione ONLINE, inclusa l'opzione di blocco con priorità bassa, e viene aggiunta l'opzione di compressione di riga.  
  
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.  
  
```tsql  
ALTER INDEX ALL ON Production.Product  
REBUILD WITH   
(  
    FILLFACTOR = 80,   
    SORT_IN_TEMPDB = ON,  
    STATISTICS_NORECOMPUTE = ON,  
    ONLINE = ON ( WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 4 MINUTES, ABORT_AFTER_WAIT = BLOCKERS ) ),   
    DATA_COMPRESSION = ROW  
);  
```  
  
### <a name="c-reorganizing-an-index-with-lob-compaction"></a>C. Ricompilazione di un indice con la compattazione di dati LOB  
 Nell'esempio seguente viene riorganizzato un singolo indice cluster nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Poiché l'indice contiene un tipo di dati LOB al livello foglia, l'istruzione compatta inoltre tutte le pagine contenenti dati LOB. Si noti che non è necessario specificare l'opzione WITH (LOB_COMPACTION) perché il valore predefinito è ON.  
  
```tsql  
ALTER INDEX PK_ProductPhoto_ProductPhotoID ON Production.ProductPhoto REORGANIZE WITH (LOB_COMPACTION);  
```  
  
### <a name="d-setting-options-on-an-index"></a>D. Impostazione di opzioni per un indice  
 Nell'esempio seguente vengono impostate diverse opzioni per l'indice `AK_SalesOrderHeader_SalesOrderNumber` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
**Si applica a**: (a partire da SQL Server 2008) di SQL Server e Database SQL di Azure.  
  
```tsql  
ALTER INDEX AK_SalesOrderHeader_SalesOrderNumber ON  
    Sales.SalesOrderHeader  
SET (  
    STATISTICS_NORECOMPUTE = ON,  
    IGNORE_DUP_KEY = ON,  
    ALLOW_PAGE_LOCKS = ON  
    ) ;  
GO
```  
  
### <a name="e-disabling-an-index"></a>E. Disabilitazione di un indice  
 Nell'esempio seguente viene disabilitato un indice non cluster della tabella `Employee` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql  
ALTER INDEX IX_Employee_ManagerID ON HumanResources.Employee DISABLE;
```  
  
### <a name="f-disabling-constraints"></a>F. Disabilitazione dei vincoli  
 Nell'esempio seguente viene disabilitato un vincolo PRIMARY KEY disabilitando l'indice di chiave primaria nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database. Il vincolo FOREIGN KEY della tabella sottostante viene disabilitato automaticamente e viene visualizzato un messaggio di avviso.  
  
```tsql  
ALTER INDEX PK_Department_DepartmentID ON HumanResources.Department DISABLE;  
```  
  
 Nel set di risultati viene restituito il messaggio di avviso seguente.  
  
 ```tsql  
 Warning: Foreign key 'FK_EmployeeDepartmentHistory_Department_DepartmentID'  
 on table 'EmployeeDepartmentHistory' referencing table 'Department'  
 was disabled as a result of disabling the index 'PK_Department_DepartmentID'.
 ```  
  
### <a name="g-enabling-constraints"></a>G. Abilitazione di vincoli  
 Nell'esempio seguente vengono abilitati i vincoli PRIMARY KEY e FOREIGN KEY disabilitati nell'esempio F.  
  
 Il vincolo PRIMARY KEY viene abilitato tramite la ricompilazione dell'indice PRIMARY KEY.  
  
```tsql  
ALTER INDEX PK_Department_DepartmentID ON HumanResources.Department REBUILD;  
```  
  
 Viene quindi abilitato il vincolo FOREIGN KEY.  
  
```tsql  
ALTER TABLE HumanResources.EmployeeDepartmentHistory  
CHECK CONSTRAINT FK_EmployeeDepartmentHistory_Department_DepartmentID;  
GO  
```  
  
### <a name="h-rebuilding-a-partitioned-index"></a>H. Ricompilazione di un indice partizionato  
 Nell'esempio seguente viene ricompilata una singola partizione, con numero `5`, dell'indice partizionato `IX_TransactionHistory_TransactionDate` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La partizione 5 viene ricompilata online e il tempo di attesa di 10 minuti per il blocco con priorità bassa viene applicato separatamente a ogni blocco acquisito dall'operazione di ricompilazione dell'indice. Se durante questo periodo di tempo non è possibile ottenere il blocco per completare la ricompilazione dell'indice, l'istruzione dell'operazione di ricompilazione viene interrotta.  
  
**Si applica a**: (a partire da SQL Server 2014) di SQL Server e Database SQL di Azure.  
  
```tsql  
-- Verify the partitioned indexes.  
SELECT *  
FROM sys.dm_db_index_physical_stats (DB_ID(),OBJECT_ID(N'Production.TransactionHistory'), NULL , NULL, NULL);  
GO  
--Rebuild only partition 5.  
ALTER INDEX IX_TransactionHistory_TransactionDate  
ON Production.TransactionHistory  
REBUILD Partition = 5   
   WITH (ONLINE = ON (WAIT_AT_LOW_PRIORITY (MAX_DURATION = 10 minutes, ABORT_AFTER_WAIT = SELF)));  
GO  
```  
  
### <a name="i-changing-the-compression-setting-of-an-index"></a>I. Modifica dell'impostazione di compressione di un indice  
 Nell'esempio seguente viene ricompilato un indice in una tabella rowstore non partizionata.  
  
```tsql
ALTER INDEX IX_INDEX1   
ON T1  
REBUILD   
WITH (DATA_COMPRESSION = PAGE);  
GO  
```  
  
 Per esempi sulla compressione dei dati aggiuntivi, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
 
### <a name="j-online-resumable-index-rebuild"></a>J. Ricompilazione dell'indice può essere ripristinato online

**Si applica a**: a partire da 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica)    

 Negli esempi seguenti viene illustrato come utilizzare la ricostruzione dell'indice può essere ripristinato in linea. 

1. Eseguire una ricompilazione dell'indice online come operazione può essere ripristinato con MAXDOP = 1.

   ```tsql
   ALTER INDEX test_idx on test_table REBUILD WITH (ONLINE=ON, MAXDOP=1, RESUMABLE=ON) ;
   ```

2. Eseguire lo stesso comando nuovamente (vedere sopra) dopo un'operazione di indice è stata sospesa, riprende automaticamente l'operazione di ricompilazione dell'indice.

3. Eseguire una ricompilazione dell'indice online come operazione può essere ripristinato con MAX_DURATION è impostata su 240 minuti.

   ```tsql
   ALTER INDEX test_idx on test_table REBUILD WITH (ONLINE=ON, RESUMABLE=ON, MAX_DURATION=240) ; 
   ```
4. Sospendere una ricompilazione dell'indice online in esecuzione può essere ripristinato.

   ```tsql
   ALTER INDEX test_idx on test_table PAUSE ;
   ```   
5. Riprendere una ricompilazione dell'indice online per la ricompilazione di un indice che è stata eseguita come operazione può essere ripristinato specificando un nuovo valore per MAXDOP è impostato su 4.

   ```tsql
   ALTER INDEX test_idx on test_table RESUME WITH (MAXDOP=4) ;
   ```
6. Ripresa di un'operazione di ricompilazione indice online per una ricompilazione dell'indice online che è stata eseguita come ripristinabile. Impostare MAXDOP su 2, il tempo di esecuzione per l'indice in esecuzione come resmumable e 240 minuti e in caso di un indice viene bloccato in attesa di blocco 10 minuti e dopo che tutti i blocchi di terminare. 

   ```tsql
      ALTER INDEX test_idx on test_table  
         RESUME WITH (MAXDOP=2, MAX_DURATION= 240 MINUTES, 
         WAIT_AT_LOW_PRIORITY (MAX_DURATION=10, ABORT_AFTER_WAIT=BLOCKERS)) ;
   ```      
7. Interrompere l'operazione di ricompilazione dell'indice può essere ripristinato che è in esecuzione o sospesa.

   ```tsql
   ALTER INDEX test_idx on test_table ABORT ;
   ``` 
  
## <a name="see-also"></a>Vedere anche  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE SPATIAL INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CREATE XML INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-index-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [Disabilitazione di indici e vincoli](../../relational-databases/indexes/disable-indexes-and-constraints.md)   
 [Indici XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [Eseguire operazioni sugli indici Online](../../relational-databases/indexes/perform-index-operations-online.md)   
 [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  



