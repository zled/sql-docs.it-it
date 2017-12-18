---
title: Database tempdb | Microsoft Docs
ms.custom: 
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
caps.latest.revision: "66"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.openlocfilehash: 6d71dcbda413d604c2c6ac2e4d85a815a4aa3719
ms.sourcegitcommit: ef1fa818beea435f58986af3379853dc28f5efd8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="tempdb-database"></a>Database tempdb
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Il database di sistema **tempdb** è una risorsa globale disponibile per tutti gli utenti connessi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], usata per contenere gli elementi seguenti:  
  
- **Oggetti utente** temporanei creati in modo esplicito, ad esempio tabelle e indici temporanei globali o locali, stored procedure temporanee, variabili di tabella, tabelle restituite in funzioni con valori di tabella o cursori.  
- **Oggetti interni** creati dal [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], tra cui:
  - Tabelle di lavoro in cui archiviare i risultati intermedi di operazioni di spooling e di ordinamento e cursori, nonché in cui archiviare LOB (Large Object) temporanei.
  - File di lavoro per operazioni hash join o hash aggregate.
  - Risultati intermedi dell'ordinamento per operazioni quali la creazione o la ricompilazione di indici (se SORT_IN_TEMPDB è specificato) o per alcune query GROUP BY, ORDER BY o UNION.

  > [!NOTE]
  > Ogni oggetto interno utilizza un minimo di nove pagine: una pagina IAM e un'estensione di otto pagine. Per altre informazioni sulle pagine e sugli extent, vedere [Pagine ed extent](../../relational-databases/pages-and-extents-architecture-guide.md#pages-and-extents).

- **Archivi delle versioni**, raccolte di pagine di dati che contengono le righe di dati usate dalle caratteristiche che supportano il controllo delle versioni delle righe. Vengono utilizzati due archivi delle versioni: uno comune e uno per la compilazione di indici online. Gli archivi delle versioni contengono:
  - Versioni di riga generate dalle transazioni di modifica dei dati in un database in cui viene usato il Read committed tramite isolamento del controllo delle versioni delle righe o transazioni di isolamento dello snapshot.  
  - Versioni di riga generate dalle transazioni di modifica dei dati per le caratteristiche, ad esempio le operazioni sugli indici online, la caratteristica MARS (Multiple Active Result Set) e i trigger AFTER.  
  
In **tempdb** viene registrato un numero minimo di operazioni Consente il rollback delle transazioni. **tempdb** viene ricreato ogni volta che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene avviato in modo che il sistema inizi sempre con una copia pulita del database. Poiché le tabelle e le stored procedure temporanee vengono eliminate automaticamente al momento della disconnessione e poiché al momento della chiusura del sistema non vi sono connessioni attive, nessuna parte del database **tempdb** viene salvata per le sessioni successive di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le operazioni di backup e di ripristino non sono consentite nel database **tempdb**.  
  
## <a name="physical-properties-of-tempdb"></a>Proprietà fisiche di tempdb  
 La tabella seguente elenca i valori iniziali di configurazione dei dati e dei file di log di **tempdb**, basati sulle impostazioni predefinite del database modello. Le dimensioni di questi file possono variare leggermente a seconda dell'edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|File|Nome logico|Nome fisico|Dimensioni iniziali|Aumento di dimensioni del file|  
|----------|------------------|-------------------|------------------|-----------------|  
|Dati primari|tempdev|tempdb.mdf|8 megabyte|Aumento automatico di 64 MB fino a quando il disco risulta pieno|  
|File di dati secondari*|temp#|tempdb_mssql_#.ndf|8 megabyte|Aumento automatico di 64 MB fino a quando il disco risulta pieno|  
|File di log|templog|templog.ldf|8 megabyte|Aumento automatico di 64 megabyte fino a un massimo di 2 terabyte|  
  
 \* Il numero di file dipende dal numero di processori (logici) del computer. In generale, se il numero di processori logici è minore o uguale a 8, usare un numero di file di dati pari al numero dei processori logici. Se il numero di processori logici è maggiore di 8, usare 8 file di dati e, se la contesa persiste, aumentare il numero di file di dati per multipli di 4 fino a quando la contesa si riduce a livelli accettabili o modificare il carico di lavoro o il codice.

> [!NOTE]
> Il valore predefinito per il numero di file di dati si basa sulle linee guida generali in [KB 2154845](http://support.microsoft.com/kb/2154845/).  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Spostamento dei dati e dei file di log di tempdb  
 Per spostare i file di log e i dati **tempdb** , vedere [Spostare i database di sistema](../../relational-databases/databases/move-system-databases.md).  
  
### <a name="database-options"></a>Opzioni di database  
 Nella tabella seguente sono elencati i valori predefiniti delle singole opzioni di database di **tempdb** e viene indicato se l'opzione è modificabile. Per visualizzare le impostazioni correnti di queste opzioni, usare la vista del catalogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
|Opzione di database|Valore predefinito|Modificabile|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Sì|  
|ANSI_NULL_DEFAULT|OFF|Sì|  
|ANSI_NULLS|OFF|Sì|  
|ANSI_PADDING|OFF|Sì|  
|ANSI_WARNINGS|OFF|Sì|  
|ARITHABORT|OFF|Sì|  
|AUTO_CLOSE|OFF|No|  
|AUTO_CREATE_STATISTICS|ON|Sì|  
|AUTO_SHRINK|OFF|No|  
|AUTO_UPDATE_STATISTICS|ON|Sì|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Sì|  
|CHANGE_TRACKING|OFF|No|  
|CONCAT_NULL_YIELDS_NULL|OFF|Sì|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Sì|  
|CURSOR_DEFAULT|GLOBAL|Sì|  
|Opzioni relative alla disponibilità del database|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|No<br /><br /> No<br /><br /> No|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Sì|  
|DB_CHAINING|ON|No|  
|ENCRYPTION|OFF|No|  
|MIXED_PAGE_ALLOCATION|OFF|No|  
|NUMERIC_ROUNDABORT|OFF|Sì|  
|PAGE_VERIFY|CHECKSUM per nuove installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NONE per aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Sì|  
|PARAMETERIZATION|SIMPLE|Sì|  
|QUOTED_IDENTIFIER|OFF|Sì|  
|READ_COMMITTED_SNAPSHOT|OFF|No|  
|RECOVERY|SIMPLE|No|  
|RECURSIVE_TRIGGERS|OFF|Sì|  
|Opzioni relative a Service Broker|ENABLE_BROKER|Sì|  
|TRUSTWORTHY|OFF|No|  
  
 Per una descrizione di queste opzioni di database, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="restrictions"></a>Restrizioni  
 Di seguito sono riportate le operazioni che non è possibile eseguire sul database **tempdb** :  
  
- Aggiunta di filegroup.  
- Backup o ripristino del database.  
- Modifica delle regole di confronto. Le regole di confronto predefinite corrispondono a quelle del server.  
- Modifica del proprietario del database. **tempdb** è di proprietà di **sa**.  
- Creazione di uno snapshot del database.  
- Eliminazione del database.  
- Eliminazione dell'utente **guest** dal database.  
- Abilitazione dell'acquisizione dei dati delle modifiche.  
- Partecipazione al mirroring del database.  
- Rimozione del filegroup primario, del file di dati primario o del file di log.  
- Ridenominazione del filegroup primario o del database.  
- Esecuzione di DBCC CHECKALLOC.  
- Esecuzione di DBCC CHECKCATALOG.  
- Impostazione del database su OFFLINE.  
- Impostazione del database o del filegroup primario su READ_ONLY.  
  
## <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente può creare oggetti temporanei in tempdb. Gli utenti possono accedere solo ai propri oggetti, a meno che non ottengano ulteriori autorizzazioni. È possibile revocare l'autorizzazione per la connessione a tempdb per impedire a un utente di utilizzarlo, tuttavia questa operazione non è consigliabile poiché in alcune operazioni di routine è richiesto l'utilizzo di tempdb.  

## <a name="optimizing-tempdb-performance"></a>Ottimizzazione delle prestazioni di tempdb
 Le dimensioni e la posizione fisica del database tempdb possono influire sulle prestazioni di un sistema. Se, ad esempio, le dimensioni definite per tempdb sono eccessivamente ridotte, il carico di elaborazione del sistema può essere in parte dovuto alla necessità di aumentare automaticamente le dimensioni di tempdb fino a raggiungere quelle necessarie per supportare il carico di lavoro a ogni riavvio dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

 Se possibile, usare l'[inizializzazione immediata dei file di database](../../relational-databases/databases/database-instant-file-initialization.md) per migliorare le prestazioni delle operazioni di aumento delle dimensioni.
 
 Preallocare lo spazio per tutti i file di tempdb impostando le relative dimensioni su un valore adeguato per il carico di lavoro tipico nell'ambiente. In questo modo il database tempdb non si espanderà con una frequenza eccessiva e le prestazioni non subiranno alterazioni. È opportuno impostare il database tempdb per l'aumento automatico delle dimensioni. Questa funzionalità deve tuttavia essere usata per aumentare lo spazio su disco per le eccezioni non pianificate. 

 All'interno di ogni [filegroup](../../relational-databases/databases/database-files-and-filegroups.md#filegroups) i file di dati devono avere le stesse dimensioni, perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa un algoritmo di riempimento proporzionale che favorisce le allocazioni all'interno di file con maggiore spazio disponibile. La suddivisione di tempdb in più file di dati di dimensioni uguali garantisce un livello elevato di efficienza parallela nelle operazioni che usano tempdb. 
 
 Impostare un valore di aumento delle dimensioni del file tale da evitare aumenti troppo ridotti delle dimensioni dei file del database tempdb. Se l'aumento delle dimensioni dei file è troppo ridotto in confronto alla quantità di dati scritti nel database tempdb, quest'ultimo potrebbe espandersi costantemente. Questo comportamento ha un impatto negativo sulle prestazioni.
 
 Per controllare i parametri di dimensione e crescita correnti di tempdb, usare la query seguente:
 ```t-sql
 SELECT name AS FileName, 
    size*1.0/128 AS FileSizeinMB,
    CASE max_size 
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
        ELSE 'Log file will grow to a maximum size of 2 TB.'
    END,
    growth AS 'GrowthValue',
    'GrowthIncrement' = 
        CASE
            WHEN growth = 0 THEN 'Size is fixed and will not grow.'
            WHEN growth > 0 AND is_percent_growth = 0 
                THEN 'Growth value is in 8-KB pages.'
            ELSE 'Growth value is a percentage.'
        END
FROM tempdb.sys.database_files;
GO
```
 
 Posizionare il database tempdb in un sottosistema I/O veloce. In presenza di molti dischi collegati direttamente, utilizzare lo striping del disco. File singoli o gruppi di file di dati di tempdb non devono necessariamente trovasi in dischi o spindle diversi, a meno che non si verifichino anche colli di bottiglia di I/O.
 
 Posizionare il database tempdb in dischi diversi da quelli utilizzati dai database utente.

## <a name="performance-improvements-in-tempdb"></a>Miglioramenti delle prestazioni in tempdb  
 A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], le prestazioni di **tempdb** vengono ulteriormente ottimizzate nei modi seguenti:  
  
- Le tabelle temporanee e le variabili di tabella vengono memorizzate nella cache. La memorizzazione nella cache consente di eseguire molto rapidamente le operazioni di eliminazione e creazione degli oggetti temporanei e di ridurre i problemi di contesa nell'allocazione delle pagine.  
- Il protocollo di latch delle pagine di allocazione è stato migliorato. In questo modo è possibile ridurre il numero di latch di aggiornamento (UP) usati.  
- L'overhead di registrazione per il database **tempdb** è stato ridotto. In questo modo si riduce l'utilizzo di banda per operazioni di I/O su disco nel file di log di **tempdb** .  
- Durante l'installazione di una nuova istanza vengono aggiunti più file di dati di tempdb. Questa attività può essere eseguita con un nuovo controllo input dell'interfaccia utente nella sezione **Configurazione del motore di database** e con un parametro della riga di comando /SQLTEMPDBFILECOUNT. Per impostazione predefinita, il programma di installazione aggiunge un numero di file di dati tempdb pari al numero di processori logici oppure a 8, a seconda di quale sia il valore inferiore.  
- Se ci sono più file di dati **tempdb** , le dimensioni di tutti i file aumenteranno contemporaneamente e della stessa quantità in base alle impostazioni specificate. Il flag di traccia 1117 non è più richiesto.  
- Tutte le allocazioni in **tempdb** usano extent uniformi. Il [flag di traccia 1118](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) non è più necessario.  
- Per il filegroup primario, la proprietà AUTOGROW_ALL_FILES è attivata e non può essere modificata. 

## <a name="capacity-planning-for-tempdb"></a>Pianificazione delle capacità per tempdb
 La determinazione delle dimensioni appropriate per tempdb in un ambiente di produzione dipende da molti fattori. Come descritto più indietro in questo argomento, tali fattori includono il carico di lavoro esistente e le caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzate. È consigliabile analizzare il carico di lavoro esistente eseguendo le attività seguenti in un ambiente di test di SQL Server:
- Attivare l'aumento automatico delle dimensioni di tempdb.
- Eseguire singole query o file di traccia del carico di lavoro e monitorare l'uso dello spazio da parte di tempdb.
- Eseguire operazioni di manutenzione degli indici, ad esempio la ricompilazione degli indici stessi, e monitorare lo spazio occupato da tempdb. 
- Impiegare i valori di uso dello spazio ottenuti con i passaggi precedenti per prevedere l'utilizzo totale da parte del carico di lavoro. Regolare poi tali valori in funzione delle attività simultanee previste e quindi impostare di conseguenza le dimensioni di tempdb.

## <a name="how-to-monitor-tempdb-use"></a>Come monitorare l'uso di tempdb
  L'esaurimento dello spazio disponibile in tempdb può provocare interruzioni significative nell'ambiente di produzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e può impedire alle applicazioni in esecuzione di completare le operazioni in corso. Per effettuare il monitoraggio dello spazio su disco usato dai file di tempdb, è possibile usare la vista a gestione dinamica (DMV, Dynamic Management View) [sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md):
  
 ```t-sql
 -- Determining the Amount of Free Space in tempdb
 SELECT SUM(unallocated_extent_page_count) AS [free pages], 
  (SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount Space Used by the Version Store
 SELECT SUM(version_store_reserved_page_count) AS [version store pages used],
  (SUM(version_store_reserved_page_count)*1.0/128) AS [version store space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount of Space Used by Internal Objects
 SELECT SUM(internal_object_reserved_page_count) AS [internal object pages used],
  (SUM(internal_object_reserved_page_count)*1.0/128) AS [internal object space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount of Space Used by User Objects
 SELECT SUM(user_object_reserved_page_count) AS [user object pages used],
  (SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
  
  Per effettuare il monitoraggio dell'allocazione delle pagine o dell'attività di deallocazione in tempdb a livello di sessione o di attività, poi, è possibile usare le DMV [sys.dm_db_session_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md) e [sys.dm_db_task_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md). Queste viste consentono di identificare le query, le tabelle temporanee o le variabili di tabella che usano una grande quantità di spazio su disco in tempdb. Sono anche disponibili diversi contatori che consentono di monitorare lo spazio libero disponibile in tempdb e le risorse che stanno usando tempdb. Per ulteriori informazioni, vedere la sezione successiva.

 ```t-sql
 -- Obtaining the space consumed by internal objects in all currently running tasks in each session
 SELECT session_id, 
  SUM(internal_objects_alloc_page_count) AS task_internal_objects_alloc_page_count,
  SUM(internal_objects_dealloc_page_count) AS task_internal_objects_dealloc_page_count 
 FROM sys.dm_db_task_space_usage 
 GROUP BY session_id;
 ```
 
 ```t-sql
 -- Obtaining the space consumed by internal objects in the current session for both running and completed tasks
 SELECT R2.session_id,
  R1.internal_objects_alloc_page_count 
  + SUM(R2.internal_objects_alloc_page_count) AS session_internal_objects_alloc_page_count,
  R1.internal_objects_dealloc_page_count 
  + SUM(R2.internal_objects_dealloc_page_count) AS session_internal_objects_dealloc_page_count
 FROM sys.dm_db_session_space_usage AS R1 
 INNER JOIN sys.dm_db_task_space_usage AS R2 ON R1.session_id = R2.session_id
 GROUP BY R2.session_id, R1.internal_objects_alloc_page_count, 
  R1.internal_objects_dealloc_page_count;;
 ```

## <a name="related-content"></a>Contenuto correlato  
 [Opzione SORT_IN_TEMPDB per gli indici](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
 [Database di sistema.](../../relational-databases/databases/system-databases.md)  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
 [Spostare file del database](../../relational-databases/databases/move-database-files.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di tempdb in SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81216)  
 [Risoluzione dei problemi relativi allo spazio su disco insufficiente in tempdb](http://msdn.microsoft.com/library/ms176029.aspx) 
