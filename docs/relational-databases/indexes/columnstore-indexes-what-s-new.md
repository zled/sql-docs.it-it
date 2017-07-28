---
title: "Indici columnstore - Novità | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe5ea05-5b19-45a4-9b7a-8ae5ca367897
caps.latest.revision: 28
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 47b0c3fc8aba635dcfd573536b770f13a40956fa
ms.openlocfilehash: 0a63e3e5641ce513e0d3c30705ac8a7523cbc053
ms.contentlocale: it-it
ms.lasthandoff: 06/29/2017

---
# <a name="columnstore-indexes---what39s-new"></a>Indici columnstore - Novità
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Riepilogo delle funzionalità columnstore disponibili per ogni versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e per le versioni più recenti del database SQL di Azure Premium Edition, Azure SQL Data Warehouse e Parallel Data Warehouse.  

 >[!NOTE]
 > Per il database SQL di Azure gli indici columnstore sono disponibili solo nella Premium Edition.
 
## <a name="feature-summary-for-product-releases"></a>Riepilogo delle funzionalità per le versioni dei prodotti  
 Questa tabella riepiloga le funzionalità principali per gli indici columnstore e i prodotti in cui sono disponibili.  

  
|Funzionalità indice columnstore|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]|  
|-------------------------------|---------------------------|---------------------------|---------------------------|--------------------------------------------|-------------------------|---|  
|Esecuzione batch per le query multithreading|sì|sì|sì|sì|sì|sì| 
|Esecuzione batch per le query a thread singolo|||sì|sì|sì|sì|  
|Opzione relativa alla compressione dell'archivio||sì|sì|sì|sì|sì|  
|Isolamento dello snapshot e dello snapshot Read Committed|||sì|sì|sì|sì| 
|Specificare l'indice columnstore durante la creazione di una tabella|||sì|sì|sì|sì|  
|AlwaysOn supporta gli indici columnstore|sì|sì|sì|sì|sì|sì| 
|Le repliche secondarie leggibili AlwaysOn supportano l'indice columnstore non cluster di sola lettura|sì|sì|sì|sì|sì|sì|  
|Le repliche secondarie leggibili AlwaysOn supportano gli indici columnstore aggiornabili|||sì|sì|||  
|Indice columnstore non cluster di sola lettura su heap o albero B|sì|sì|sì*|sì*|sì*|sì*|  
|Indice columnstore non cluster aggiornabile su heap o albero B|||sì|sì|sì|sì|  
|Indici albero b aggiuntivi consentiti su un heap o albero b che dispone di un indice columnstore non cluster|sì|sì|sì|sì|sì|sì|  
|Indice columnstore cluster aggiornabile||sì|sì|sì|sì|sì|  
|Indice albero b su un indice columnstore cluster|||sì|sì|sì|sì|  
|Indice columnstore su una tabella con ottimizzazione per la memoria|||sì|sì|sì|sì|  
|La definizione degli indici columnstore non cluster supporta l'uso di una condizione filtrata|||sì|sì|sì|sì|  
|Opzione relativa al ritardo di compressione per gli indici columnstore in CREATE TABLE e ALTER TABLE|||sì|sì|sì|sì|
|L'indice columnstore può avere una colonna calcolata non persistente.||||sì|||   
  
 *Per creare un indice columnstore non cluster leggibile, archiviare l'indice in un filegroup di sola lettura.  

## [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 
 [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] aggiunge queste nuove funzionalità.

### <a name="functional"></a>Funzionale
- [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] supporta le colonne calcolate non persistenti in indici columnstore cluster. Le colonne persistenti non sono supportate negli indici columnstore cluster. Non è possibile creare un indice non cluster in un indice columnstore che contiene una colonna calcolata. 

## [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] aggiunge miglioramenti importanti per aumentare le prestazioni e la flessibilità degli indici columnstore. In questo modo è possibile migliorare gli scenari di data warehouse e abilitare l'analisi operativa in tempo reale.  
  
### <a name="functional"></a>Funzionale  
  
-   Una tabella rowstore può avere un solo indice columnstore non cluster aggiornabile. In precedenza, l'indice columnstore non cluster era di sola lettura.  
  
-   La definizione degli indici columnstore non cluster supporta l'uso di una condizione filtrata. Per ridurre al minimo l'impatto sulle prestazioni conseguente all'aggiunta di un indice columnstore in una tabella OLTP, usare una condizione filtrata per creare un indice columnstore non cluster solo sui dati usati meno di frequente del carico di lavoro operativo. 
  
-   Una tabella in memoria può avere un solo indice columnstore. È possibile crearlo durante la creazione della tabella o aggiungerlo in un secondo momento con [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md). In precedenza, solo una tabella basata su disco poteva avere un indice columnstore.  
  
-   Un indice columnstore cluster può avere uno o più indici rowstore non cluster. In precedenza, l'indice columnstore non supportava gli indici non cluster. SQL Server gestisce automaticamente gli indici non cluster per le operazioni DML.  
  
-   Supporto per le chiavi primarie ed esterne usando un indice albero b per imporre questi vincoli su un indice columnstore cluster.  
  
-   Gli indici columnstore hanno un'opzione relativa al ritardo di compressione che riduce al minimo l'impatto che il carico di lavoro transazionale ha sull'analisi operativa in tempo reale.  Questa opzione consente di modificare frequentemente le righe per stabilizzarle prima di comprimerle nel columnstore. Per informazioni dettagliate, vedere [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md) (Creare un indice columnstore &#40;Transact-SQL&#41) e [Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
### <a name="performance-for-database-compatibility-level-120-or-130"></a>Prestazioni per il livello di compatibilità del database 120 o 130  
  
-   Gli indici columnstore supportano il livello di isolamento dello snapshot Read Committed e l'isolamento dello snapshot. Questo consente le query di analisi coerente transazionale senza alcun blocco.  
  
-   Columnstore supporta la deframmentazione degli indici rimuovendo le righe eliminate senza necessità di ricompilare l'indice in modo esplicito. L'istruzione ALTER INDEX … REORGANIZE rimuove le righe eliminate, in base a un criterio definito internamente, dal columnstore come operazione online  
  
-   Gli indici columnstore sono accessibili su una replica secondaria leggibile AlwaysOn. È possibile migliorare le prestazioni per l'analisi operativa ripartendo le query di analisi su una replica secondaria AlwaysOn.  
  
-   Per migliorare le prestazioni, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] calcola le funzioni di aggregazione MIN, MAX, SUM, COUNT, AVG durante le scansioni di tabella quando il tipo di dati usa non più di 8 byte e non è di tipo stringa. La distribuzione dell'aggregazione è supportata con o senza clausola GROUP BY sia per gli indici columnstore cluster sia per quelli non cluster.  
  
-   La distribuzione del predicato consente di velocizzare le query che confrontano le stringhe di tipo [v]char o n[v]char. Questo si applica ai comuni operatori di confronto e include operatori come LIKE che usano i filtri bitmap. Inoltre, funziona con tutte le regole di confronto supportate da SQL Server.  
  
### <a name="performance-for-database-compatibility-level-130"></a>Prestazioni per il livello di compatibilità del database 130  
  
-   Nuovo supporto dell'esecuzione in modalità batch per le query che usano uno di questi operatori:  
  
    -   SORT  
  
    -   Funzioni di aggregazione con più funzioni distinte. Alcuni esempi: COUNT/COUNT, AVG/SUM, CHECKSUM_AGG, STDEV/STDEVP.  
  
    -   Funzioni di aggregazione delle finestre: COUNT, COUNT_BIG, SUM, AVG, MIN, MAX e CLR.  
  
    -   Funzioni di aggregazione delle finestre definite dall'utente: CHECKSUM_AGG, STDEV, STDEVP, VAR, VARP e GROUPING.  
  
    -   Funzioni analitiche di aggregazione delle finestre: LAG< LEAD, FIRST_VALUE, LAST_VALUE, PERCENTILE_CONT, PERCENTILE_DISC, CUME_DIST e PERCENT_RANK.  
  
-   Le query a thread singolo in esecuzione in MAXDOP 1 o con un piano di query seriale vengono eseguite in modalità batch. Le query multithreading venivano eseguite in modalità batch solo in precedenza.  
  
-   Le query delle tabelle con ottimizzazione per la memoria possono avere piani paralleli in modalità SQL InterOp durante l'accesso dei dati nell'indice rowstore o columnstore.  
  
### <a name="supportability"></a>Facilità di supporto  
 Queste viste di sistema sono una novità per columnstore:  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  
  
-   [sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)  
  
-   [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
-   [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)  
  
 Queste DMV basate su OLTP in memoria contengono aggiornamenti per columnstore:  
  
-   [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)  
  
-   [sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)  
  
-   [sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)  
  
### <a name="limitations"></a>Limitazioni  
  
-   MERGE è disabilitato quando viene definito un indice albero b su un indice columnstore cluster.  
  
-   Per le tabelle in memoria, un indice columnstore deve includere tutte le colonne; l'indice columnstore non può avere una condizione di filtrata.  
  
-   Per le tabelle in memoria, le query sugli indici columnstore vengono eseguite solo in modalità InterOP e non in modalità nativa in memoria. È supportata l'esecuzione parallela.  
  
## <a name="sql-server-2014"></a>SQL Server 2014  
 SQL Server 2014 ha introdotto l'indice dell'archivio columnstore cluster come formato di archiviazione primario. Questo ha consentito caricamenti regolari, nonché operazioni di aggiornamento, eliminazione e inserimento.  
  
-   La tabella può usare un indice columnstore cluster come archiviazione tabella primaria. Nella tabella non è consentito nessun altro indice, ma l'indice columnstore cluster è aggiornabile, pertanto è possibile eseguire caricamenti regolari e apportare modifiche alle singole righe.  
  
-   L'indice columnstore non cluster continua ad avere la stessa funzionalità in SQL Server 2012, ad eccezione degli operatori aggiuntivi che ora possono essere eseguiti in modalità batch. Al momento è aggiornabile solo tramite ricompilazione e usando un cambio di partizione. L'indice columnstore non cluster è supportato solo nelle tabelle basate su disco e non in quelle in memoria.  
  
-   L'indice columnstore cluster e non cluster ha un'opzione relativa alla compressione dell'archivio che comprime ulteriormente i dati. L'opzione di archiviazione è utile per ridurre le dimensioni dei dati in memoria e su disco, ma comporta un rallentamento delle prestazioni delle query. Funziona anche per i dati a cui si accede raramente.  
  
-   L'indice columnstore cluster e quello non cluster funzionano in modo molto simile: usano lo stesso formato di archiviazione a colonne, lo stesso motore di elaborazione delle query e lo stesso insieme di viste di gestione dinamica. La differenza risiede nei tipi di indice primario e secondario e nel fatto che l'indice columnstore non cluster è di sola lettura.  
  
-   Questi operatori vengono eseguiti in modalità batch per le query multithreading: SCAN, FILTER, PROJECT, JOIN, GROUP BY e UNION ALL.  
  
## <a name="sql-server-2012"></a>SQL Server 2012  
 SQL Server 2012 ha introdotto l'indice columnstore non cluster come un altro tipo di indice nelle tabelle rowstore e l'elaborazione batch per le query sui dati columnstore.  
  
-   Una tabella rowstore può avere un solo indice columnstore non cluster.  
  
-   L'indice columnstore è di sola lettura. Dopo aver creato l'indice columnstore, non è possibile aggiornare la tabella tramite operazioni di inserimento, eliminazione e aggiornamento: per eseguire queste operazioni è necessario eliminare l'indice, aggiornare la tabella e ricompilare l'indice columnstore. È possibile caricare dati aggiuntivi nella tabella usando un cambio di partizione. Il vantaggio del cambio di partizione è che consente di caricare dati senza eliminare e ricompilare l'indice columnstore.  
  
-   L'indice columnstore richiede sempre memoria aggiuntiva, in genere un ulteriore 10% per rowstore, poiché archivia una copia dei dati.  
  
-   L'elaborazione batch consente di raddoppiare o migliorare le prestazioni delle query, ma è disponibile solo per l'esecuzione di query parallele.  
  
## <a name="see-also"></a>Vedere anche  
 Guida agli indici columnstore   
 Caricamento dati di indici columnstore   
 [Prestazioni delle query per gli indici columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 Indici columnstore per il data warehousing   
 [Deframmentazione degli indici columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  

