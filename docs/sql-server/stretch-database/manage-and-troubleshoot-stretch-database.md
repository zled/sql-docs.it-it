---
title: "Gestione e risoluzione dei problemi di Estensione database | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Estensione database, gestione"
  - "Estensione database, risoluzione dei problemi"
  - "gestione di Estensione database"
  - "risoluzione dei problemi di Estensione database"
ms.assetid: 6334db3e-9297-44df-8d53-211187a95520
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# Gestione e risoluzione dei problemi di Estensione database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per gestire e risolvere i problemi di Estensione database, usare gli strumenti e i metodi descritti in questo argomento.  
## Gestire i dati locali  
  
###  <a name="LocalInfo"></a> Ottenere informazioni su tabelle e database locali abilitati per Estensione database  
 Aprire le viste del catalogo **sys.databases** e **sys.tables** per visualizzare informazioni sulle tabelle e i database di SQL Server abilitati per l'estensione. Per altre informazioni, vedere [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md).  
 
 Per visualizzare la quantità di spazio usata da una tabella abilitata per l'estensione in SQL Server, eseguire questa istruzione.
 
 ```tsql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'LOCAL_ONLY';
GO
 ```
   
## Gestire la migrazione dei dati  
  
### Verificare la funzione di filtro applicata a una tabella  
 Aprire la vista del catalogo **sys.remote_data_archive_tables** e verificare il valore della colonna **filter_predicate** per trovare la funzione usata dall'estensione database per selezionare le righe per la migrazione. Se il valore è null, l'intera tabella è idonea per la migrazione. Per altre informazioni, vedere [sys.remote_data_archive_tables &#40;Transact-SQL&#41;](../Topic/sys.remote_data_archive_tables%20\(Transact-SQL\).md) e [Selezionare le righe di cui eseguire la migrazione tramite una funzione di filtro](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).  
  
###  <a name="Migration"></a> Controllare lo stato della migrazione dei dati  
 Selezionare **Attività | Estendi | Monitoraggio** per un database in SQL Server Management Studio per monitorare la migrazione dei dati in Monitoraggio dell'estensione database. Per altre informazioni, vedere [Monitor and troubleshoot data migration &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) (Monitorare e risolvere i problemi relativi alla migrazione dei dati &#40;Estensione database&#41;).  
  
 In alternativa, aprire la DMV **sys.dm_db_rda_migration_status** per visualizzare il numero di batch e righe di dati di cui è stata eseguita la migrazione.  
  
###  <a name="Firewall"></a> Risolvere i problemi relativi alla migrazione dei dati  
 Per consigli sulla risoluzione dei problemi, vedere [Monitor and troubleshoot data migration &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) (Monitorare e risolvere i problemi relativi alla migrazione dei dati &#40;Estensione database&#41;).  
  
## Gestire i dati remoti  
  
###  <a name="RemoteInfo"></a> Ottenere informazioni su tabelle e database remoti usati da Estensione database  
 Aprire le viste del catalogo **sys.remote_data_archive_databases** e **sys.remote_data_archive_tables** per visualizzare informazioni sulle tabelle e i database remoti in cui sono memorizzati i dati migrati. Per altre informazioni, vedere [sys.remote_data_archive_databases &#40;Transact-SQL&#41;](../Topic/sys.remote_data_archive_databases%20\(Transact-SQL\).md) e [sys.remote_data_archive_tables &#40;Transact-SQL&#41;](../Topic/sys.remote_data_archive_tables%20\(Transact-SQL\).md).  
 
Per visualizzare la quantità di spazio usata da una tabella abilitata per l'estensione in Azure, eseguire questa istruzione.
 
 ```tsql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'REMOTE_ONLY';
GO
 ```

### Eliminare i dati migrati  
Per eliminare i dati di cui è già stata eseguita la migrazione in Azure, seguire i passaggi descritti in [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md).  
  
## Gestire lo schema di una tabella

### Non modificare lo schema di una tabella remota  
 Non modificare lo schema di una tabella remota di Azure associata a una tabella di SQL Server configurata per Estensione database. In particolare, non modificare il nome o il tipo di dati di una colonna. La funzionalità Estensione database formula varie ipotesi relative allo schema della tabella remota in relazione allo schema della tabella di SQL Server. Se si modifica lo schema remoto, Estensione database smetterà di funzionare per la tabella modificata.  

### Riconciliare le colonne della tabella  
Se sono state accidentalmente eliminate colonne dalla tabella remota, eseguire **sp_rda_reconcile_columns** per aggiungere colonne alla tabella remota presenti nella tabella di SQL Server abilitata per l'estensione, ma non nella tabella remota. Per altre informazioni, vedere [sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md).  
  
  > [!IMPORTANT] Quando **sp_rda_reconcile_columns** crea nuovamente le colonne accidentalmente eliminate dalla tabella remota, non ripristina i dati che erano presenti nelle colonne eliminate.
  
**sp_rda_reconcile_columns** non elimina le colonne della tabella remota presenti nella tabella remota, ma non nella tabella di SQL Server abilitata per l'estensione. Se sono presenti colonne nella tabella remota di Azure che non esistono più nella tabella di SQL Server abilitata per l'estensione, queste colonne aggiuntive non impediscono il normale funzionamento dell'estensione database. È possibile rimuovere le colonne aggiuntive manualmente.  
 
## Gestire prestazioni e costi  
  
### Risolvere i problemi relativi alle prestazioni delle query  
  L'esecuzione di query che includono tabelle abilitate per Estensione database in genere è più lenta rispetto a quanto avveniva prima dell'abilitazione delle tabelle per Estensione database. Se le prestazioni delle query peggiorano notevolmente, esaminare i possibili problemi seguenti.  
  
-   Il server di Azure si trova in un'area geografica diversa rispetto all'istanza di SQL Server? Configurare il server di Azure in modo che si trovi nella stessa area geografica dell'istanza di SQL Server per ridurre la latenza di rete.  
  
-   Le condizioni della rete possono essere peggiorate. Per informazioni su problemi o interruzioni recenti, contattare l'amministratore di rete.  
  
### Aumentare il livello di prestazioni di Azure per le operazioni a elevato utilizzo di risorse, quali l'indicizzazione  
 Quando si compila, si ricompila o si riorganizza un indice in una tabella di grandi dimensioni configurata per l'estensione database e si prevede di eseguire molte query sui dati migrati in Azure in questa fase, è opportuno aumentare il livello di prestazioni del database remoto di Azure corrispondente per la durata dell'operazione. Per informazioni sui livelli di prestazioni e i relativi prezzi, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### Non è possibile sospendere il servizio di Estensione database di SQL Server in Azure  
 Assicurarsi di selezionare il livello di prestazioni e il piano tariffario corretti. Se si aumenta il livello di prestazioni temporaneamente per un'operazione che usa un numero elevato di risorse, ripristinare il livello precedente al termine dell'operazione. Per informazioni sui livelli di prestazioni e i relativi prezzi, vedere [Prezzi di Estensione database di SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
   
 ## Modificare l'ambito delle query  
 Le query sulle tabelle abilitate per l'estensione restituiscono dati locali e remoti per impostazione predefinita. È possibile modificare l'ambito delle query per tutte le query di tutti gli utenti oppure per una singola query di un amministratore.  
   
 ### Modificare l'ambito delle query per tutte le query di tutti gli utenti  
 Per modificare l'ambito di tutte le query di tutti gli utenti, eseguire la stored procedure **sys.sp_rda_set_query_mode**. È possibile ridurre l'ambito per eseguire query solo sui dati locali, disabilitare tutte le query o ripristinare l'impostazione predefinita. Per altre informazioni, vedere [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md).  
   
 ### <a name="queryHints"></a>Modificare l'ambito delle query per una singola query di un amministratore  
 Per modificare l'ambito di una singola query di un membro del ruolo db_owner, aggiungere l'hint per la query **WITH (REMOTE_DATA_ARCHIVE_OVERRIDE = *valore* ) * * all'istruzione SELECT. L'hint per la query REMOTE_DATA_ARCHIVE_OVERRIDE può avere i valori seguenti.  
 -   **LOCAL_ONLY**. Eseguire query solo sui dati locali.  
   
 -   **REMOTE_ONLY**. Eseguire query solo sui dati remoti.  
   
 -   **STAGE_ONLY**. Eseguire query solo sui dati della tabella in cui l'estensione database inserisce temporaneamente righe idonee per la migrazione e conserva le righe migrate per il periodo specificato dopo la migrazione. Questo hint per la query è l'unico modo per eseguire query sulla tabella di gestione temporanea.  
  
Ad esempio, la query seguente restituisce solo risultati locali.  
  
 ```tsql  
USE <Stretch-enabled database name>;
GO
SELECT * FROM <Stretch_enabled table name> WITH (REMOTE_DATA_ARCHIVE_OVERRIDE = LOCAL_ONLY) WHERE ... ;
GO
```  
   
 ## <a name="adminHints"></a>Eseguire aggiornamenti ed eliminazioni amministrativi  
 Per impostazione predefinita non è possibile eseguire operazioni UPDATE o DELETE sulle righe idonee per la migrazione o già migrate in una tabella abilitata per l'estensione. Se è necessario risolvere un problema, un membro del ruolo db_owner può eseguire un'operazione UPDATE o DELETE aggiungendo l'hint per la query **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = ** )** all'istruzione. L'hint per la query REMOTE_DATA_ARCHIVE_OVERRIDE può avere i valori seguenti.  
 -   **LOCAL_ONLY**. Aggiornare o eliminare solo i dati locali.  
   
 -   **REMOTE_ONLY**. Aggiornare o eliminare solo i dati remoti.  
   
 -   **STAGE_ONLY**. Aggiornare o eliminare solo i dati della tabella in cui l'estensione database inserisce temporaneamente righe idonee per la migrazione e conserva le righe migrate per il periodo specificato dopo la migrazione.  
  
## Vedere anche  
 [Monitorare e risolvere i problemi relativi alla migrazione dei dati &#40;Estensione database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)   
[Backup di database abilitati per l'estensione (Estensione database)](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
[Ripristino di database abilitati per l'estensione (Estensione database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
  