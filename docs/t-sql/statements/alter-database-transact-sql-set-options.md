---
title: MODIFICARE le opzioni SET di DATABASE (Transact-SQL) | Documenti Microsoft
description: Informazioni su come impostare le opzioni di database, ad esempio la crittografia, ottimizzazione automatica, archivio query in un SQL Server e Database SQL di Azure
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- online database state [SQL Server]
- database options [SQL Server]
- emergency database state [SQL Server]
- databases [SQL Server], options
- read-only databases
- recovery models [SQL Server], switching
- ALTER DATABASE statement, SET options
- offline database state [SQL Server]
- snapshot isolation framework option
- checksums [SQL Server]
- automatic tuning
- SQL plan regression correction
ms.assetid: f76fbd84-df59-4404-806b-8ecb4497c9cc
caps.latest.revision: "159"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b460ca1e3f662ea59c0b7bcd4b1fc0e0e059e236
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-database-set-options-transact-sql"></a>Opzioni ALTER DATABASE SET (Transact-SQL) 
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  In questo argomento è inclusa la sintassi di ALTER DATABASE correlata all'impostazione delle opzioni di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni sulla sintassi di ALTER DATABASE, vedere gli argomenti seguenti.  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  

-   [ALTER DATABASE &#40; Database SQL di Azure &#41;](alter-database-azure-sql-database.md) 

-   [ALTER DATABASE &#40; Azure SQL Data Warehouse &#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)  
  
-   [ALTER DATABASE &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)  
  
Mirroring del database, [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], i livelli di compatibilità `SET` opzioni ma che sono descritte in argomenti separati a causa della lunghezza. Per ulteriori informazioni, vedere [Mirroring del Database di ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md), [ALTER DATABASE SET HADR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-hadr.md), e [modificare a livello di compatibilità del DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
> [!NOTE]  
>  Molte opzioni di set di database possono essere configurate per la sessione corrente tramite [istruzioni SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md) e spesso vengono configurate dalle applicazioni quando si connettono. Livello di sessione Imposta opzioni eseguono l'override di **ALTER DATABASE SET** valori. Le opzioni di database descritte di seguito sono valori che possono essere impostati per le sessioni mediante le quali non vengono forniti in modo esplicito altri valori di opzioni SET.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER DATABASE { database_name  | CURRENT }  
SET   
{  
    <optionspec> [ ,...n ] [ WITH <termination> ]   
}  
  
<optionspec> ::=   
{  
    <auto_option>   
  | <automatic_tuning_option>   
  | <change_tracking_option>   
  | <containment_option>   
  | <cursor_option>   
  | <database_mirroring_option>  
  | <date_correlation_optimization_option>  
  | <db_encryption_option>  
  | <db_state_option>  
  | <db_update_option>   
  | <db_user_access_option>   
  | <delayed_durability_option>  
  | <external_access_option>  
  | FILESTREAM ( <FILESTREAM_option> )  
  | <HADR_options>  
  | <mixed_page_allocation_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <recovery_option>  
  | <remote_data_archive_option>  
  | <service_broker_option>  
  | <snapshot_option>  
  | <sql_option>   
  | <target_recovery_time_option>   
  | <termination>  
}  
  
<auto_option> ::=   
{  
    AUTO_CLOSE { ON | OFF }   
  | AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }   
  | AUTO_SHRINK { ON | OFF }   
  | AUTO_UPDATE_STATISTICS { ON | OFF }   
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}  
  
<automatic_tuning_option> ::=  
{  
  AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = { ON | OFF } )
}  

<change_tracking_option> ::=  
{  
  CHANGE_TRACKING   
   {   
       = OFF  
     | = ON [ ( <change_tracking_option_list > [,...n] ) ]   
     | ( <change_tracking_option_list> [,...n] )  
   }  
}  
  
   <change_tracking_option_list> ::=  
   {  
       AUTO_CLEANUP = { ON | OFF }   
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }  
   }  
  
<containment_option> ::=   
   CONTAINMENT = { NONE | PARTIAL }  
  
<cursor_option> ::=   
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }   
  | CURSOR_DEFAULT { LOCAL | GLOBAL }   
}  
  
<database_mirroring_option>  
  ALTER DATABASE Database Mirroring  
  
<date_correlation_optimization_option> ::=  
    DATE_CORRELATION_OPTIMIZATION { ON | OFF }  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
  
<db_state_option> ::=  
    { ONLINE | OFFLINE | EMERGENCY }  
  
<db_update_option> ::=  
    { READ_ONLY | READ_WRITE }  
  
<db_user_access_option> ::=  
    { SINGLE_USER | RESTRICTED_USER | MULTI_USER }  
  
<delayed_durability_option> ::=  
    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<external_access_option> ::=  
{  
    DB_CHAINING { ON | OFF }  
  | TRUSTWORTHY { ON | OFF }  
  | DEFAULT_FULLTEXT_LANGUAGE = { <lcid> | <language name> | <language alias> }  
  | DEFAULT_LANGUAGE = { <lcid> | <language name> | <language alias> }  
  | NESTED_TRIGGERS = { OFF | ON }  
  | TRANSFORM_NOISE_WORDS = { OFF | ON }  
  | TWO_DIGIT_YEAR_CUTOFF = { 1753, ..., 2049, ..., 9999 }  
}  
<FILESTREAM_option> ::=  
{  
    NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL   
  | DIRECTORY_NAME = <directory_name>  
}  
<HADR_options> ::=  
    ALTER DATABASE SET HADR  
  
<mixed_page_allocation_option> ::=  
    MIXED_PAGE_ALLOCATION { OFF | ON }  
  
<parameterization_option> ::=  
    PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
    QUERY_STORE   
    {  
          = OFF   
        | = ON [ ( <query_store_option_list> [,...n] ) ]  
        | ( < query_store_option_list> [,...n] )  
        | CLEAR [ ALL ]  
    }  
}   
  
<query_store_option_list> ::=  
{  
      OPERATION_MODE = { READ_WRITE | READ_ONLY }   
    | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )  
    | DATA_FLUSH_INTERVAL_SECONDS = number   
    | MAX_STORAGE_SIZE_MB = number   
    | INTERVAL_LENGTH_MINUTES = number   
    | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
    | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
    | MAX_PLANS_PER_QUERY = number
    | WAIT_STATS_CAPTURE_MODE = [ ON | OFF ]
}  
  
<recovery_option> ::=   
{  
    RECOVERY { FULL | BULK_LOGGED | SIMPLE }   
  | TORN_PAGE_DETECTION { ON | OFF }  
  | PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }  
}  
  
<remote_data_archive_option> ::=  
{  
    REMOTE_DATA_ARCHIVE =  
    {  
        ON ( SERVER = <server_name> ,   
                  {   CREDENTIAL = <db_scoped_credential_name>  
                     | FEDERATED_SERVICE_ACCOUNT =  ON | OFF   
                  }  
               )  
      | OFF  
    }  
}  
  
<service_broker_option> ::=  
{  
    ENABLE_BROKER  
  | DISABLE_BROKER  
  | NEW_BROKER  
  | ERROR_BROKER_CONVERSATIONS  
  | HONOR_BROKER_PRIORITY { ON | OFF}  
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = {ON | OFF }  
}  
<sql_option> ::=   
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 90 | 100 | 110 | 120}  
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<target_recovery_time_option> ::=  
    TARGET_RECOVERY_TIME = target_recovery_time { SECONDS | MINUTES }  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database da modificare.  
  
 CURRENT  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 `CURRENT`esegue l'azione nel database corrente. `CURRENT`non è supportata per tutte le opzioni in tutti i contesti. Se `CURRENT` ha esito negativo, fornire il nome del database.  
  
 **\<auto_option >:: =**  
  
 Consente di controllare le opzioni automatiche.  
  
 AUTO_CLOSE { ON | OFF }  
 ON  
 Il database viene chiuso normalmente e le relative risorse vengono rilasciate dopo la disconnessione dell'ultimo utente.  
  
 Il database viene riaperto automaticamente quando un utente tenta di usarlo nuovamente, Ad esempio, generando un `USE database_name` istruzione. Se il database viene chiuso normalmente quando l'opzione AUTO_CLOSE è impostata su ON, non verrà riaperto finché un utente non tenta di usarlo al successivo riavvio di [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 OFF  
 Il database rimane aperto dopo la disconnessione dell'ultimo utente.  
  
 L'opzione AUTO_CLOSE è utile per i database desktop perché consente di gestire i file di database come normali file. I file possono essere spostati, copiati per creare backup o anche inviati tramite posta elettronica ad altri utenti. Il processo AUTO_CLOSE è asincrono. Operazioni ripetute di apertura e chiusura del database non comportano una riduzione delle prestazioni.  
  
> [!NOTE]  
>  L'opzione AUTO_CLOSE non è disponibile in un Database indipendente o in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_auto_close_on nella vista del catalogo sys.databases oppure la proprietà IsAutoClose della funzione DATABASEPROPERTYEX.  
  
> [!NOTE]  
>  Se l'opzione AUTO_CLOSE è impostata su ON, alcune colonne nella vista del catalogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e della funzione DATABASEPROPERTYEX restituiranno NULL perché il database non è disponibile per il recupero dei dati. Per risolvere questo problema, eseguire un'istruzione USE per aprire il database.  
  
> [!NOTE]  
>  Per il mirroring del database è necessario che AUTO_CLOSE sia OFF.  
  
 Quando il database è impostato su AUTOCLOSE = ON, un'operazione che avvia una chiusura automatica del database comporta la cancellazione della cache dei piani per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 e versioni successive il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni di manutenzione o riconfigurazione del database". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.  
  
 AUTO_CREATE_STATISTICS { ON | OFF }  
 ON  
 In Query Optimizer vengono create statistiche per colonne singole nei predicati di query, se necessario, per migliorare i piani di query e le prestazioni di esecuzione delle query. Queste statistiche sulle singole colonne vengono create quando le query vengono compilate in Query Optimizer. Tali statistiche vengono create solo sulle colonne che ancora non sono le prime colonne di un oggetto statistiche esistente.  
  
 Il valore predefinito è ON. È consigliabile usare l'impostazione predefinita per la maggior parte dei database.  
  
 OFF  
 In Query Optimizer non vengono create statistiche per le singole colonne nei predicati di query durante la compilazione delle query. L'impostazione di questa opzione su OFF può determinare piani di query e prestazioni di esecuzione delle query non ottimali.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_auto_create_stats_on nella vista del catalogo sys.databases oppure la proprietà IsAutoCreateStatistics della funzione DATABASEPROPERTYEX.  
  
 Per ulteriori informazioni, vedere la sezione "Utilizzo opzioni delle statistiche a livello di Database" in [statistiche](../../relational-databases/statistics/statistics.md).  
  
 INCREMENTAL = ON | OFF  
 Quando AUTO_CREATE_STATISTICS è ON e INCREMENTAL è impostata su ON, le statistiche create automaticamente vengono create come incrementali ogni volta che le statistiche incrementali sono supportate. Il valore predefinito è OFF. Per altre informazioni, vedere [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md).  
  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 AUTO_SHRINK { ON | OFF }  
 ON  
 I file di database vengono compattati periodicamente, se necessario.  
  
 È possibile compattare automaticamente sia i file di dati sia i file di log. AUTO_SHRINK consente di ridurre le dimensioni del log delle transazioni solo se per il database è impostato il modello di recupero con registrazione minima oppure se viene eseguito il backup del log. Se questa opzione è impostata su OFF, i file di database non vengono compattati automaticamente durante i controlli periodici per la presenza di spazio inutilizzato.  
  
 Con l'opzione AUTO_SHRINK i file vengono compattati quando più del 25% dello spazio del file risulta inutilizzato. Il file viene compattato fino a quando la percentuale di spazio inutilizzato nel file è pari al 25% oppure fino a quando il file raggiunge dimensioni pari a quelle di creazione, a seconda di quale tra questi due è il valore maggiore.  
  
 Non è possibile compattare un database di sola lettura.  
  
 OFF  
 I file di database non vengono compattati automaticamente durante i controlli periodici per la presenza di spazio inutilizzato.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_auto_shrink_on nella vista del catalogo sys.databases oppure la proprietà IsAutoShrink della funzione DATABASEPROPERTYEX.  
  
> [!NOTE]  
>  L'opzione AUTO_SHRINK non è disponibile in un database indipendente.  
  
 AUTO_UPDATE_STATISTICS { ON | OFF }  
 ON  
 Specifica che le statistiche vengono aggiornate in Query Optimizer se vengono usate da una query e quando possono non essere aggiornate. Le statistiche diventano obsolete in seguito a operazioni di inserimento, aggiornamento, eliminazione o unione che modificano la distribuzione dei dati nella tabella o nella vista indicizzata. Query Optimizer determina che le statistiche potrebbero non essere aggiornate contando il numero di modifiche apportate ai dati dopo l'ultimo aggiornamento delle statistiche e confrontando il numero di modifiche con una soglia basata sul numero di righe nella tabella o nella vista indicizzata.  
  
 Query Optimizer controlla la presenza di statistiche non aggiornate prima di compilare una query e prima di eseguire un piano di query memorizzato nella cache. Prima di compilare una query, Query Optimizer usano le colonne, le tabelle e le viste indicizzate nel predicato di query per identificare le eventuali statistiche non aggiornate. Prima di eseguire un piano di query memorizzato nella cache, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] verifica che tale piano faccia riferimento alle statistiche aggiornate.  
  
 L'opzione AUTO_UPDATE_STATISTICS_ASYNC si applica alle statistiche create per indici, colonne singole nei predicati di query e statistiche create con l'istruzione CREATE STATISTICS. Questa opzione si applica anche alle statistiche filtrate.  
  
 Il valore predefinito è ON. È consigliabile usare l'impostazione predefinita per la maggior parte dei database.  
  
 Usare l'opzione AUTO_UPDATE_STATISTICS_ASYNC per specificare se le statistiche vengono aggiornate in modo sincrono o asincrono.  
  
 OFF  
 Specifica che Query Optimizer non aggiorna le statistiche quando vengono usate da una query e quando potrebbero essere obsolete. L'impostazione di questa opzione su OFF può determinare piani di query e prestazioni di esecuzione delle query non ottimali.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_auto_update_stats_on nella vista del catalogo sys.databases oppure la proprietà IsAutoUpdateStatistics della funzione DATABASEPROPERTYEX.  
  
 Per ulteriori informazioni, vedere la sezione "Utilizzo opzioni delle statistiche a livello di Database" in [statistiche](../../relational-databases/statistics/statistics.md).  
  
 AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
 ON  
 Specifica che gli aggiornamenti delle statistiche per l'opzione AUTO_UPDATE_STATISTICS sono asincroni. Query Optimizer non attende il completamento degli aggiornamenti delle statistiche per compilare le query.  
  
 L'impostazione di questa opzione su ON non produce alcun effetto, a meno che AUTO_UPDATE_STATISTICS non sia impostata su ON.  
  
 Per impostazione predefinita, l'opzione AUTO_UPDATE_STATISTICS_ASYNC è impostata su OFF. Query Optimizer aggiorna pertanto le statistiche in modo sincrono.  
  
 OFF  
 Specifica che gli aggiornamenti delle statistiche per l'opzione AUTO_UPDATE_STATISTICS sono sincroni. Query Optimizer attende il completamento degli aggiornamenti delle statistiche per compilare le query.  
  
 L'impostazione di questa opzione su OFF non produce alcun effetto, a meno che AUTO_UPDATE_STATISTICS non sia impostata su ON.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_auto_update_stats_async_on nella vista del catalogo sys.databases.  
  
 Per ulteriori informazioni su quando usare gli aggiornamenti sincroni o asincroni delle statistiche, vedere la sezione "Utilizzo opzioni delle statistiche a livello di Database" in [statistiche](../../relational-databases/statistics/statistics.md).  
  
 **\<automatic_tuning_option >:: =**  
 **Si applica a**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].  

 Abilita o disabilita `FORCE_LAST_GOOD_PLAN` [ottimizzazione automatica](../../relational-databases/automatic-tuning/automatic-tuning.md) opzione.  
  
 FORCE_LAST_GOOD_PLAN = {ON | OFF}  
 ON  
 Il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] impone automaticamente l'ultimo piano buona noto presenti il [!INCLUDE[tsql_md](../../includes/tsql_md.md)] in nuovo piano SQL provoca regressioni delle prestazioni di query. Il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] continui consente di monitorare le prestazioni delle query del [!INCLUDE[tsql_md](../../includes/tsql_md.md)] query con il piano forzato. Se sono disponibili i miglioramenti delle prestazioni, la [!INCLUDE[ssde_md](../../includes/ssde_md.md)] verrà continuare a usare ultimo piano valido noto. Se non vengono rilevati i miglioramenti delle prestazioni, la [!INCLUDE[ssde_md](../../includes/ssde_md.md)] produrrà un nuovo piano SQL. L'istruzione avrà esito negativo se l'archivio Query non è abilitata o se non è incluso nella *lettura-scrittura* modalità.   

 OFF  
 Il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] segnala potenziali regressioni delle prestazioni di query causate da modifiche del piano SQL in [sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) visualizzazione. Tuttavia, questi suggerimenti non vengono applicati automaticamente. Utente possa monitorare active indicazioni e identificato risolvere i problemi di applicando [!INCLUDE[tsql_md](../../includes/tsql_md.md)] script che vengono visualizzati nella vista. Si tratta del valore predefinito.

 **\<change_tracking_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Controlla le opzioni di rilevamento delle modifiche. È possibile abilitare il rilevamento delle modifiche, impostare le opzioni, modificare le opzioni e disabilitare il rilevamento delle modifiche. Per alcuni esempi, vedere la sezione Esempi più avanti in questo argomento.  
  
 ON  
 Abilita il rilevamento delle modifiche per il database. Quando si abilita il rilevamento delle modifiche, è possibile impostare anche le opzioni AUTO CLEANUP e CHANGE RETENTION.  
  
 AUTO_CLEANUP = { ON | OFF }  
 ON  
 Le informazioni sul rilevamento delle modifiche vengono rimosse automaticamente una volta trascorso il periodo di memorizzazione specificato.  
  
 OFF  
 I dati relativi al rilevamento delle modifiche non vengono rimossi dal database.  
  
 CHANGE_RETENTION =*retention_period* {giorni | ORE | MINUTI}  
 Specifica il periodo minimo di conservazione delle informazioni sul rilevamento delle modifiche nel database. I dati vengono rimossi solo quando il valore di AUTO_CLEANUP è ON.  
  
 *retention_period* è un numero intero che specifica il componente numerico del periodo di memorizzazione.  
  
 L'impostazione predefinita è 2 giorni. Il periodo di memorizzazione minimo è 1 minuto. Il tipo di memorizzazione predefinito è giorni.  
  
 OFF  
 Disabilita il rilevamento delle modifiche per il database. Per poter disabilitare il rilevamento delle modifiche per il database, è necessario innanzitutto disabilitarlo per tutte le tabelle.  
  
 **\<containment_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Consente di controllare le opzioni di indipendenza del database.  
  
 INDIPENDENZA = {NESSUNO | PARZIALE}  
 Nessuno  
 Il database non è un database indipendente.  
  
 PARTIAL  
 Il database è un database indipendente. L'impostazione dell'indipendenza del database su PARTIAL restituisce un errore se per il database è abilitato Change Data Capture, la replica o il rilevamento delle modifiche. Il controllo degli errori viene arrestato dopo un errore. Per altre informazioni sui database indipendenti, vedere [Contained Databases](../../relational-databases/databases/contained-databases.md).  
  
> [!NOTE]  
>  Contenuto non può essere configurata [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]. Contenuto non è definita in modo esplicito, ma [!INCLUDE[ssSDS](../../includes/sssds-md.md)] consente agli utenti di database indipendente le funzionalità, ad esempio contenute.  
  
 **\<cursor_option >:: =**  
  
 Consente di controllare le opzioni del cursore.  
  
 CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
 ON  
 Tutti i cursori aperti al momento dell'esecuzione del commit o del rollback di una transazione vengono chiusi.  
  
 OFF  
 I cursori rimangono aperti quando viene eseguito il commit di una transazione. Quando si esegue il rollback di una transazione vengono chiusi tutti i cursori, ad eccezione di quelli definiti come INSENSITIVE o STATIC.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per CURSOR_CLOSE_ON_COMMIT. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta CURSOR_CLOSE_ON_COMMIT su OFF per la sessione quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [SET CURSOR_CLOSE_ON_COMMIT &#40;Transact-SQL&#41;](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_cursor_close_on_commit_on nella vista del catalogo sys.databases oppure la proprietà IsCloseCursorsOnCommitEnabled della funzione DATABASEPROPERTYEX.  
  
 CURSOR_DEFAULT { LOCAL | GLOBAL }  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Determina se l'ambito del cursore è LOCAL o GLOBAL.  
  
 LOCAL  
 Se si specifica LOCAL e se un cursore non viene definito come GLOBAL al momento della creazione, l'ambito del cursore è locale rispetto al batch, alla stored procedure o al trigger in cui è stato creato. Il nome del cursore è valido solo in questo ambito. È possibile fare riferimento al cursore tramite variabili di cursore locali nel batch, nella stored procedure o nel trigger oppure tramite un parametro OUTPUT di stored procedure. Il cursore viene deallocato in modo implicito al termine dell'esecuzione del batch, della stored procedure o del trigger, a meno che non sia stato passato a un parametro OUTPUT. In questo caso, il cursore viene deallocato quando l'ultima variabile che vi fa riferimento viene deallocata o non è più compresa nell'ambito.  
  
 GLOBAL  
 Se si specifica GLOBAL e se un cursore non viene definito come LOCAL al momento della creazione, l'ambito del cursore è globale rispetto alla connessione. È possibile fare riferimento al nome del cursore in qualsiasi stored procedure o batch eseguiti tramite la connessione.  
  
 Il cursore viene deallocato in modo implicito soltanto al momento della disconnessione. Per ulteriori informazioni, vedere [DECLARE CURSOR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-cursor-transact-sql.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_local_cursor_default nella vista del catalogo sys.databases oppure la proprietà IsLocalCursorsDefault della funzione DATABASEPROPERTYEX.  
  
 **\<DATABASE_MIRRORING >**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Per descrizioni di argomento, vedere [Mirroring del Database di ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md).  
  
 **\<date_correlation_optimization_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Controlla l'opzione date_correlation_optimization.  
  
 DATE_CORRELATION_OPTIMIZATION { ON | OFF }  
 ON  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mantiene statistiche di correlazione tra due tabelle nel database che sono collegate da un vincolo FOREIGN KEY e contenenti **datetime** colonne.  
  
 OFF  
 Non vengono mantenute statistiche di correlazione.  
  
 Per impostare DATE_CORRELATION_OPTIMIZATION su ON, è necessario che non siano presenti connessioni attive al database, ad eccezione della connessione che esegue l'istruzione ALTER DATABASE. Successivamente, sono supportate più connessioni.  
  
 Per determinare l'impostazione corrente di questa opzione, è possibile esaminare la colonna is_date_correlation_on nella vista del catalogo sys.databases.  
  
 **\<db_encryption_option >:: =**  
  
 Controlla lo stato della crittografia del database.  
  
 ENCRYPTION {ON | OFF}  
 Imposta il database per l'utilizzo della crittografia (ON) o no (OFF). Per ulteriori informazioni sulla crittografia del database, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), e [Transparent Data Encryption con il Database SQL di Azure](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).  
  
 Quando la crittografia è abilitata a livello di database, tutti i filegroup vengono crittografati. Qualsiasi filegroup nuovo eredita la proprietà di crittografia. Se tutti i filegroup nel database sono impostati su **READ ONLY**, l'operazione di crittografia del database avrà esito negativo.  
  
 È possibile visualizzare lo stato della crittografia del database utilizzando il [Sys.dm database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) vista a gestione dinamica.  
  
 **\<db_state_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Controlla lo stato del database.  
  
 OFFLINE  
 Il database viene chiuso normalmente e contrassegnato come offline. Non è possibile modificare il database mentre è offline.  
  
 ONLINE  
 Il database è aperto e disponibile per l'utilizzo.  
  
 EMERGENCY  
 Il database è contrassegnato come READ_ONLY, la registrazione è disabilitata e l'accesso è limitato ai soli membri del ruolo predefinito del server sysadmin. L'opzione EMERGENCY viene usata principalmente per attività di risoluzione dei problemi. Ad esempio, è possibile impostare lo stato EMERGENCY per un database contrassegnato come sospetto a causa di un file di log danneggiato. In questo modo, l'amministratore di sistema potrà accedere in sola lettura al database. Solo i membri del ruolo predefinito del server sysadmin possono impostare lo stato EMERGENCY per un database.  
  
> [!NOTE]  
>  **Autorizzazioni:** autorizzazione ALTER DATABASE per il database di interesse è necessaria per modificare un database allo stato offline o emergency. Per modificare lo stato di un database da offline a online è necessaria l'autorizzazione ALTER ANY DATABASE a livello di server.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare le colonne state e state_desc il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo o la proprietà Status del [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) (funzione). Per altre informazioni, vedere [Stati del database](../../relational-databases/databases/database-states.md).  
  
 Un database contrassegnato come RESTORING non può essere impostato su OFFLINE, ONLINE o EMERGENCY. Lo stato RESTORING può essere impostato durante un'operazione di ripristino attiva o quando un'operazione di ripristino di un database o di un file di log ha esito negativo a causa di un file di backup danneggiato.  
  
 **\<db_update_option >:: =**  
  
 Indica se sono consentiti aggiornamenti nel database.  
  
 READ_ONLY  
 Gli utenti possono leggere i dati dal database, ma non modificarli.  
  
> [!NOTE]  
>  Per migliorare le prestazioni di esecuzione delle query, aggiornare le statistiche prima di impostare un database su READ_ONLY. Se dopo che un database viene impostato su READ_ONLY sono necessarie statistiche aggiuntive, nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] verranno create statistiche in tempdb. Per ulteriori informazioni sulle statistiche per un database di sola lettura, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
 READ_WRITE  
 Il database è disponibile per operazioni di lettura e scrittura.  
  
 Per modificare questo stato, è necessario disporre dell'accesso esclusivo al database. Per altre informazioni, vedere la clausola SINGLE_USER.  
  
> [!NOTE]  
>  Nei database federati di [!INCLUDE[ssSDS](../../includes/sssds-md.md)], SET { READ_ONLY | READ_WRITE } è disabilitato.  
  
 **\<db_user_access_option >:: =**  
  
 Controlla l'accesso degli utenti al database.  
  
 SINGLE_USER  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Specifica che l'accesso al database è consentito a un solo utente alla volta. Se si specifica SINGLE_USER e sono presenti altri utenti connessi al database, l'istruzione ALTER DATABASE verrà bloccata fino a quando tutti gli utenti non si disconnettono dal database specificato. Per eseguire l'override di questo comportamento, vedere WITH \<terminazione > clausola.  
  
 Il database rimane in modalità SINGLE_USER anche se l'utente che ha impostato l'opzione si disconnette. A questo punto, un altro utente (ma solo uno) potrà connettersi al database.  
  
 Prima di impostare il database in modalità SINGLE_USER, verificare che l'opzione AUTO_UPDATE_STATISTICS_ASYNC sia impostata su OFF. Se l'opzione è impostata su ON, il thread in background usato per aggiornare le statistiche stabilisce una connessione con il database che non sarà quindi accessibile in modalità utente singolo. Per visualizzare lo stato di questa opzione, eseguire una query sulla colonna is_auto_update_stats_async_on nella [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo. Se l'opzione è impostata su ON, effettuare le operazioni seguenti:  
  
1.  Impostare AUTO_UPDATE_STATISTICS_ASYNC su OFF.  
  
2.  Controllare per i processi attivi asincrono delle statistiche eseguendo una query di [Sys.dm exec_background_job_queue](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md) vista a gestione dinamica.  
  
 Se sono presenti processi attivi, consentire i processi completare o Terminarli manualmente usando [KILL STATS JOB](../../t-sql/language-elements/kill-stats-job-transact-sql.md).  
  
RESTRICTED_USER  
 RESTRICTED_USER consente la connessione al database solo ai membri del ruolo predefinito del database db_owner e ai membri dei ruoli predefiniti del server dbcreator e sysadmin, senza tuttavia imporre un limite al numero di connessioni. Tutte le connessioni al database vengono interrotte entro l'intervallo di tempo specificato nella clausola di interruzione dell'istruzione ALTER DATABASE. Dopo l'impostazione dello stato RESTRICTED_USER per il database, qualsiasi tentativo di connessione da parte di utenti non qualificati viene rifiutato.  
  
MULTI_USER  
 Consente la connessione al database a tutti gli utenti che dispongono di autorizzazioni appropriate.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna user_access nella vista del catalogo sys.databases oppure la proprietà UserAccess della funzione DATABASEPROPERTYEX.  
  
 **\<delayed_durability_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Determina se le transazioni sottoposte a commit sono completamente durevoli o durevoli posticipate.  
  
 DISABLED  
 Tutte le transazioni in cui viene usato SET DISABLED sono completamente durevoli. Tutte le opzioni di durabilità impostate in un blocco atomico o in un'istruzione COMMIT vengono ignorate.  
  
 ALLOWED  
 Tutte le transazioni in cui viene usato SET ALLOWED sono completamente durevoli o durevoli posticipate, a seconda del set di opzioni di durabilità nel blocco atomico o nell'istruzione COMMIT.  
  
 FORCED  
 Tutte le transazioni in cui viene usato SET FORCED sono durevoli posticipate. Tutte le opzioni di durabilità impostate in un blocco atomico o in un'istruzione COMMIT vengono ignorate.  
  
 **\<external_access_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Determina se è consentito l'accesso al database da parte di risorse esterne, ad esempio oggetti di un altro database.  
  
 DB_CHAINING { ON | OFF }  
 ON  
 Il database può essere l'origine o la destinazione di una catena di proprietà tra database.  
  
 OFF  
 Il database non può partecipare al concatenamento della proprietà tra database.  
  
> [!IMPORTANT]  
>  Questa impostazione viene riconosciuta dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando l'opzione del server cross db ownership chaining è impostata su 0 (OFF). Quando cross db ownership chaining è 1 (ON), tutti i database utente possono partecipare ai concatenamenti della proprietà tra database, a prescindere dal valore di questa opzione. Questa opzione viene impostata tramite [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 Per impostare questa opzione, è necessaria l'autorizzazione CONTROL SERVER nel database.  
  
 Non è possibile impostare l'opzione DB_CHAINING per i database di sistema master, model e tempdb.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_db_chaining_on nella vista del catalogo sys.databases.  
  
 TRUSTWORTHY { ON | OFF }  
 ON  
 I moduli di database, ad esempio stored procedure o funzioni definite dall'utente, che usano un contesto di rappresentazione, possono accedere a risorse esterne al database.  
  
 OFF  
 I moduli di database in un contesto di rappresentazione non possono accedere a risorse esterne al database.  
  
 L'opzione TRUSTWORTHY viene impostata su OFF ogni volta che il database viene collegato.  
  
 Per impostazione predefinita, in tutti i database di sistema, a eccezione del database msdb, TRUSTWORTHY è impostata su OFF. Per i database model e tempdb questo valore non può essere modificato. È consigliabile evitare di impostare l'opzione TRUSTWORTHY su ON per il database master.  
  
 Per impostare questa opzione, è necessaria l'autorizzazione CONTROL SERVER nel database.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_trustworthy_on nella vista del catalogo sys.databases.  
  
 DEFAULT_FULLTEXT_LANGUAGE  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Consente di specificare il valore della lingua predefinita per le colonne con indicizzazione full-text.  
  
> [!IMPORTANT]  
>  Questa opzione è consentita solo quando l'opzione CONTAINMENT è stata impostata su PARTIAL. Se l'opzione CONTAINMENT è impostata su NONE, si verificheranno errori.  
  
 DEFAULT_LANGUAGE  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica la lingua predefinita per tutti i nuovi account di accesso creati. È possibile specificare la lingua indicando l'ID locale (LCID), il nome della lingua o l'alias di lingua. Per un elenco di nomi di lingua accettabili e alias, vedere [Sys. syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md). Questa opzione è consentita solo quando l'opzione CONTAINMENT è stata impostata su PARTIAL. Se l'opzione CONTAINMENT è impostata su NONE, si verificheranno errori.  
  
 NESTED_TRIGGERS  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica se un trigger AFTER supporta la propagazione, ovvero un'azione che avvia un altro trigger, che a sua volta ne avvia un altro e così via. Questa opzione è consentita solo quando l'opzione CONTAINMENT è stata impostata su PARTIAL. Se l'opzione CONTAINMENT è impostata su NONE, si verificheranno errori.  
  
 TRANSFORM_NOISE_WORDS  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Consente di eliminare un messaggio di errore visualizzato nel caso in cui parole non significative impediscono l'esecuzione di un'operazione booleana in una query full-text. Questa opzione è consentita solo quando l'opzione CONTAINMENT è stata impostata su PARTIAL. Se l'opzione CONTAINMENT è impostata su NONE, si verificheranno errori.  
  
 TWO_DIGIT_YEAR_CUTOFF  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica un numero intero compreso tra 1753 e 9999 che rappresenta l'anno di cambio data per l'interpretazione degli anni a due cifre come anni a quattro cifre. Questa opzione è consentita solo quando l'opzione CONTAINMENT è stata impostata su PARTIAL. Se l'opzione CONTAINMENT è impostata su NONE, si verificheranno errori.  
  
 **\<FILESTREAM_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Consente di controllare le impostazioni per le tabelle FileTable.  
  
 NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
 OFF  
 L'accesso non transazionale ai dati delle tabelle FileTable è disabilitato.  
  
 READ_ONLY  
 I dati FILESTREAM nelle tabelle FileTable in questo database possono essere letti da processi non transazionali.  
  
 FULL  
 L'accesso non transazionale completo a dati FILESTREAM in tabelle FileTable è abilitato.  
  
 DIRECTORY_NAME =  *\<directory_name >*  
 Nome di directory compatibile con Windows. Il nome deve essere univoco in tutti i nomi di directory a livello di database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il confronto di univocità non supporta la distinzione tra maiuscole e minuscole, indipendentemente dalle impostazioni delle regole di confronto. È necessario impostare questa opzione prima di creare una tabella FileTable nel database.  
  
 **\<HADR_options >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Vedere [ALTER DATABASE SET HADR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-hadr.md).  
  
 **\<mixed_page_allocation_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)). Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 MIXED_PAGE_ALLOCATION {OFF | ON} controlli se il database può creare pagine iniziali utilizzando un extent misto per le prime otto pagine di indice o una tabella.  
  
 OFF  
 Il database crea sempre pagine iniziali di extent uniformi. Si tratta del valore predefinito.  
  
 ON  
 Il database è possibile creare pagine iniziali di extent misti.  
  
 Questa impostazione è impostata su ON per tutti i database di sistema. **tempdb** è il solo sistema database che supporta OFF.  
  
 **\<PARAMETERIZATION_option >:: =**  
  
 Consente di controllare l'opzione di parametrizzazione.  
  
 PARAMETERIZATION { SIMPLE | FORCED }  
 SIMPLE  
 Le query vengono parametrizzate in base al comportamento predefinito del database.  
  
 FORCED  
 Con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita la parametrizzazione di tutte le query nel database.  
  
 Per determinare l'impostazione corrente di questa opzione, è possibile esaminare la colonna is_parameterization_forced nella vista del catalogo sys.databases.  
  
 **\<query_store_options >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 ON | OFF | CLEAR [ ALL ]  
 Verifica se l'archivio di query è abilitato nel database e controlla la rimozione del contenuto dell'archivio di query.  
  
ON  
 Abilita l'archivio query.  
  
OFF  
 Disabilita l'archivio query.  Si tratta del valore predefinito.   
  
CLEAR  
 Rimuovere il contenuto dell'archivio query.  
  
OPERATION_MODE  
 Descrive la modalità di funzionamento dell'archivio di query. I valori validi sono READ_ONLY e READ_WRITE. In modalità READ_WRITE l'archivio query raccoglie e mantiene le informazioni di statistiche sull'esecuzione di runtime e piani di query. In modalità READ_ONLY le informazioni possono essere lette dall'archivio di query, ma non vengono aggiunte nuove informazioni. Se lo spazio massimo allocato dell'archivio di query viene esaurito, la modalità di funzionamento dell'archivio di query passa a READ_ONLY.  
  
 CLEANUP_POLICY  
 Descrive i criteri di conservazione dati dell'archivio di query. STALE_QUERY_THRESHOLD_DAYS determina il numero di giorni per cui vengono mantenute le informazioni per una query in archivio query. STALE_QUERY_THRESHOLD_DAYS è di tipo **bigint**.  
  
 DATA_FLUSH_INTERVAL_SECONDS  
 Determina la frequenza con cui i dati scritti nell'archivio query vengono mantenuti su disco. Per ottimizzare le prestazioni, i dati raccolti dall'archivio di query vengono scritti in modo asincrono sul disco. La frequenza con cui si verifica questo trasferimento asincrono viene configurata tramite l'argomento DATA_FLUSH_INTERVAL_SECONDS. DATA_FLUSH_INTERVAL_SECONDS è di tipo **bigint**.  
  
 MAX_STORAGE_SIZE_MB  
 Determina lo spazio allocato per l'archivio di query. MAX_STORAGE_SIZE_MB è di tipo **bigint**.  
  
 INTERVAL_LENGTH_MINUTES  
 Determina l'intervallo di tempo in cui vengono aggregati i dati delle statistiche di esecuzione di runtime nell'archivio di query. Per ottimizzare l'utilizzo dello spazio, le statistiche di esecuzione di runtime nell'archivio di statistiche di runtime vengono aggregate in un intervallo di tempo fisso. L'intervallo di tempo predefinito viene configurato tramite l'argomento INTERVAL_LENGTH_MINUTES. INTERVAL_LENGTH_MINUTES è di tipo **bigint**.  
  
 SIZE_BASED_CLEANUP_MODE  
 Controlla se i pulizia verrà attivata automaticamente quando la quantità totale di dati sta per raggiungere le dimensioni massime:  
  
 OFF  
 Pulizia basati sulle dimensioni non verrà attivata automaticamente. 
  
 AUTO  
 Viene attivata automaticamente pulizia in base alla dimensione su disco raggiunge il 90% delle **max_storage_size_mb**. Pulizia basati sulle dimensioni consente di rimuovere innanzitutto le query meno recenti e meno costose. Si ferma in corrispondenza di circa l'80% di **max_storage_size_mb**.  Questo è il valore di configurazione predefinito.  
  
 SIZE_BASED_CLEANUP_MODE è di tipo **nvarchar**.  
  
 QUERY_CAPTURE_MODE  
 Definisce la modalità di acquisizione query attualmente attiva:  
  
 Tutte le tutte le query vengono acquisite. Questo è il valore di configurazione predefinito.  Questo è il valore di configurazione predefinito per[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]
  
 AUTO acquisizione query pertinenti in base esecuzione conteggio e consumo delle risorse.  Questo è il valore di configurazione predefinito per[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 NON arrestare l'acquisizione di nuove query. Archivio query continuerà a raccogliere le statistiche di compilazione e runtime per le query che già acquisite. Utilizzare questa configurazione con cautela, poiché potrebbe non essere implementato per acquisire le query importante.  
  
 QUERY_CAPTURE_MODE è di tipo **nvarchar**.  
  
 max_plans_per_query  
 Intero che rappresenta il numero massimo di piani mantenuti per ogni query. Valore predefinito è 200.  
  
 **\<recovery_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Controlla le opzioni di recupero del database e il controllo degli errori di I/O su disco.  
  
 FULL  
 Consente il recupero completo in caso di errori dei supporti tramite i backup del log delle transazioni. Se un file di dati risulta danneggiato, il recupero dei supporti consente di ripristinare tutte le transazioni di cui è stato eseguito il commit. Per altre informazioni, vedere [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
 BULK_LOGGED  
 Consente il recupero in caso di errori dei supporti, cercando di ottenere i migliori risultati a livello di prestazioni e di utilizzo della quantità minima di spazio del log per determinate operazioni su larga scala o bulk. Per informazioni sulle operazioni che supportano la registrazione minima, vedere [Log delle transazioni &#40; SQL Server &#41; ](../../relational-databases/logs/the-transaction-log-sql-server.md). Con il modello di recupero BULK_LOGGED vengono registrate informazioni minime per queste operazioni. Per altre informazioni, vedere [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
 SIMPLE  
 Viene implementata una strategia di backup semplice che usano una quantità minima di spazio del log. Lo spazio del log può essere riutilizzato automaticamente quando non è più necessario per il recupero di errori del server. Per altre informazioni, vedere [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
> [!IMPORTANT]  
>  La gestione del modello di recupero con registrazione minima risulta più semplice rispetto agli altri due modelli, ma comporta rischi maggiori di perdita dei dati in caso di danni a un file di dati. Tutte le modifiche apportate dopo l'ultimo backup completo o differenziale del database vanno perdute ed è necessario immetterle nuovamente in modo manuale.  
  
 Il modello di recupero del valore predefinito è determinato dal modello di recupero di **modello** database. Per ulteriori informazioni sulla selezione del modello di recupero appropriato, vedere [modelli di recupero &#40; SQL Server &#41; ](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare il **recovery_model** e **recovery_model_desc** colonne nella vista del catalogo sys. Databases oppure la proprietà di ripristino di DATABASEPROPERTYEX funzione.  
  
 TORN_PAGE_DETECTION { ON | OFF }  
 ON  
 Le pagine incomplete possono essere rilevate da [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 OFF  
 Le pagine incomplete non possono essere rilevate da [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
> [!IMPORTANT]  
>  La struttura della sintassi TORN_PAGE_DETECTION ON | OFF verrà rimossa a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare pertanto di usarla in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni che attualmente usano questa struttura. In alternativa, usare l'opzione PAGE_VERIFY.  
  
 PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }  
 Individua le pagine del database danneggiate in seguito a errori di percorso di I/O su disco. Gli errori di percorso di I/O su disco possono essere la causa di danneggiamenti del database e sono in genere la conseguenza di interruzioni dell'alimentazione o di errori hardware a livello di disco, che si verificano durante la scrittura della pagina su disco.  
  
 CHECKSUM  
 Calcola un checksum sul contenuto dell'intera pagina e archivia il valore nell'intestazione della pagina quando questa viene scritta su disco. In fase di lettura della pagina dal disco, il checksum viene ricalcolato e confrontato con il valore di checksum archiviato nell'intestazione della pagina. Se i valori non corrispondono, viene segnalato il messaggio di errore 824 (che indica un errore di checksum) sia nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sia nel registro eventi di Windows. Un errore di checksum indica un problema di percorso di I/O. Per determinare la causa principale del problema, è necessaria un'analisi accurata di hardware, driver del firmware, BIOS, driver dei filtri, ad esempio software antivirus, e altri componenti del percorso di I/O.  
  
 TORN_PAGE_DETECTION  
 Salva un modello a 2 bit specifico per ogni settore da 512 byte della pagina di database da 8 kilobyte (KB) e archivia tali bit nell'intestazione della pagina di database quando questa viene scritta su disco. In fase di lettura della pagina dal disco, i bit per il rilevamento di pagine incomplete archiviati nell'intestazione della pagina vengono confrontati con le informazioni effettive sui settori della pagina. La presenza di valori non corrispondenti indica che la pagina è stata scritta su disco solo in parte. In questa situazione viene segnalato il messaggio di errore 824 (che indica un errore di pagina incompleta) sia nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sia nel registro eventi di Windows. Le pagine incomplete vengono generalmente rilevate durante il recupero del database, se si tratta effettivamente di un problema di scrittura incompleta di una pagina. Altri errori di percorso di I/O possono tuttavia causare in qualsiasi momento pagine incomplete.  
  
 Nessuno  
 Le scritture di pagine di database non genereranno un valore CHECKSUM o TORN_PAGE_DETECTION. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene eseguito alcun controllo del checksum o della presenza di pagine incomplete durante una lettura, anche se nell'intestazione della pagina è presente un valore CHECKSUM o TORN_PAGE_DETECTION.  
  
 Per l'utilizzo dell'opzione PAGE_VERIFY, è importante tenere presente quanto segue:  
  
-   L'impostazione predefinita è CHECKSUM.  
  
-   Quando un utente o un database di sistema viene aggiornato a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva, il valore di PAGE_VERIFY, ovvero NONE o TORN_PAGE_DETECTION, rimane invariato. È consigliabile usare CHECKSUM.  
  
    > [!NOTE]  
    >  Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'opzione di database PAGE_VERIFY è impostata su NONE per il database tempdb e non può essere modificata. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive, il valore predefinito per il database tempdb è CHECKSUM per nuove installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando si aggiorna un'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], viene mantenuto il valore predefinito NONE. L'opzione può essere modificata. È consigliabile utilizzare CHECKSUM per il database tempdb.  
  
-   TORN_PAGE_DETECTION può consentire l'utilizzo di un numero più limitato di risorse, ma offre una protezione minore rispetto all'opzione CHECKSUM.  
  
-   È possibile impostare PAGE_VERIFY senza attivare la modalità offline per il database, senza bloccarlo o senza impedire in altro modo la concorrenza nel database.  
  
-   Le opzioni CHECKSUM e TORN_PAGE_DETECTION si escludono a vicenda. Non è possibile abilitare contemporaneamente entrambe le opzioni.  
  
 Se viene rilevato un errore di pagina incompleta o di checksum, è possibile eseguire il recupero tramite il ripristino dei dati o potenzialmente tramite la ricompilazione dell'indice se l'errore è limitato alle pagine di indice. Se si verifica un errore di checksum, eseguire DBCC CHECKDB per determinare il tipo della pagina o delle pagine del database interessate dal problema. Per ulteriori informazioni sulle opzioni di ripristino, vedere [argomenti RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md). Sebbene il ripristino dei dati consenta di risolvere il problema di danneggiamento dei dati, è necessario individuare il prima possibile la causa principale, ad esempio un errore hardware del disco, per eseguire i necessari interventi di correzione ed evitare che gli errori si ripresentino.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue quattro tentativi per qualsiasi operazione di lettura non riuscita a causa di un errore di checksum, di pagina incompleta o di I/O. Se la lettura viene completata correttamente durante uno di questi tentativi, viene scritto un messaggio nel log degli errori e l'esecuzione del comando che ha attivato la lettura continua. Se tutti i tentativi hanno esito negativo, il comando viene interrotto con il messaggio di errore 824.  
  
 Per ulteriori informazioni sui checksum, pagine incomplete, tentativi di lettura, messaggi di errore 823 e 824 e altre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità di controllo dei / o, vedere questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=47160).  
  
 L'impostazione corrente di questa opzione può essere determinata esaminando la colonna page_verify_option nella [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo oppure la proprietà IsTornPageDetectionEnabled il [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)(funzione).  
  
**\<remote_data_archive_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Abilita o disabilita l'estensione Database per il database. Per ulteriori informazioni, vedere [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
REMOTE_DATA_ARCHIVE = {ON (SERVER = \<nome_server >, {CREDENZIALE = \<db_scoped_credential_name > | FEDERATED_SERVICE_ACCOUNT = ON | OFF}) | OFF A ON  
 Abilita estensione Database per il database. Per altre informazioni, inclusi prerequisiti aggiuntivi, vedere [abilitare estensione Database per un database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Autorizzazioni**. Abilitazione di estensione Database per un database o una tabella richiede autorizzazioni db_owner. Abilitazione di estensione Database per un database richiede anche le autorizzazioni CONTROL DATABASE.  
  
SERVER = \<nome_server >  
 Specifica l'indirizzo del server Azure. Includere la `.database.windows.net` parte del nome. Ad esempio, `MyStretchDatabaseServer.database.windows.net`.  
  
CREDENZIALE = \<db_scoped_credential_name >  
 Specifica il database con ambito di credenziali che l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza per connettersi al server di Azure. Assicurarsi che sia le credenziali prima di eseguire questo comando. Per altre informazioni, vedere [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
  
FEDERATED_SERVICE_ACCOUNT = ON | DISATTIVATO  
 È possibile utilizzare un account del servizio federato per SQL Server locale per comunicare con il server Azure remoto quando vengono soddisfatte le condizioni seguenti.  
  
-   L'account del servizio usato per l'esecuzione dell'istanza di SQL Server è un account di dominio.  
  
-   L'account di dominio appartiene a un dominio il cui Active Directory è federato con Azure Active Directory.  
  
-   Il server Azure remoto è configurato per supportare l'autenticazione di Azure Active Directory.  
  
-   L'account del servizio in cui è in esecuzione l'istanza di SQL Server deve essere configurato come account dbmanager o sysadmin nel server remoto di Azure.  
  
 Se si specifica ON, è anche possibile specificare l'argomento CREDENTIAL. Se si specifica OFF, è necessario fornire l'argomento CREDENTIAL.  
  
 OFF  
 Disabilita l'estensione Database per il database. Per altre informazioni, vedere [Disabilitare Stretch Database e ripristinare i dati remoti](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
 È solo possibile disabilitare estensione Database per un database dopo il database non contiene tutte le tabelle che sono abilitate per estensione Database. Dopo aver disabilitato estensione Database, si interrompe la migrazione dei dati e i risultati della query non includono più risultati dalle tabelle remote.  
  
 La disabilitazione dell'estensione non rimuove il database remoto. Se si vuole eliminare il database remoto, è necessario eliminarlo tramite il portale di gestione di Azure.  
  
**\<service_broker_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Controlla le operazioni seguenti [!INCLUDE[ssSB](../../includes/sssb-md.md)] opzioni: Abilita o disabilita il recapito dei messaggi, imposta un nuovo [!INCLUDE[ssSB](../../includes/sssb-md.md)] identificatore o imposta le priorità di conversazione su ON o OFF.  
  
 ENABLE_BROKER  
 Indica che [!INCLUDE[ssSB](../../includes/sssb-md.md)] è abilitato per il database specificato. Il recapito dei messaggi viene avviato e il flag is_broker_enabled viene impostato su true nella vista del catalogo sys.databases. Il database mantiene l'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] esistente. Service Broker non può essere abilitato se il database è l'entità in una configurazione di mirroring del database.  
  
> [!NOTE]  
>  ENABLE_BROKER richiede un blocco esclusivo a livello di database. Se altre sessioni hanno bloccato risorse nel database, ENABLE_BROKER attende il rilascio dei blocchi da parte delle altre sessioni. Per abilitare [!INCLUDE[ssSB](../../includes/sssb-md.md)] in un database utente, accertarsi che nessun'altra sessione stia usando il database prima di eseguire l'istruzione ALTER DATABASE SET ENABLE_BROKER, ad esempio impostando il database in modalità utente singolo. Per abilitare [!INCLUDE[ssSB](../../includes/sssb-md.md)] nel database msdb, arrestare innanzitutto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per consentire a [!INCLUDE[ssSB](../../includes/sssb-md.md)] di ottenere il blocco necessario.  
  
 DISABLE_BROKER  
 Indica che [!INCLUDE[ssSB](../../includes/sssb-md.md)] è disabilitato per il database specificato. Il recapito dei messaggi viene arrestato e il flag is_broker_enabled viene impostato su false nella vista del catalogo sys.databases. Il database mantiene l'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] esistente.  
  
 NEW_BROKER  
 Specifica che al database deve essere assegnato un nuovo identificatore di Service Broker. Poiché il database viene considerato una nuova istanza di Service Broker, tutte le conversazioni esistenti nel database vengono rimosse immediatamente senza generare messaggi di fine dialogo. Tutte le route che fanno riferimento all'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] precedente devono essere ricreate con il nuovo identificatore.  
  
 ERROR_BROKER_CONVERSATIONS  
 Specifica che il recapito dei messaggi di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è abilitato. Questo consente di mantenere esistente [!INCLUDE[ssSB](../../includes/sssb-md.md)] identificatore per il database. [!INCLUDE[ssSB](../../includes/sssb-md.md)] termina tutte le conversazioni nel database con un errore. Ciò consente alle applicazioni di eseguire operazioni regolari di pulizia per le conversazioni esistenti.  
  
 HONOR_BROKER_PRIORITY {ON | OFF}  
 ON  
 Per le operazioni di invio vengono presi in considerazione i livelli di priorità assegnati alle conversazioni. I messaggi provenienti da conversazioni con livelli di priorità alti vengono inviati prima dei messaggi provenienti da conversazioni con livelli di priorità bassi.  
  
 OFF  
 Le operazioni di invio vengono eseguite come se a tutte le conversazioni fosse assegnato il livello di priorità predefinito.  
  
 Le modifiche all'opzione HONOR_BROKER_PRIORITY vengono applicate immediatamente ai nuovi dialoghi o ai dialoghi per cui non vi sono messaggi in attesa di essere inviati. Per i dialoghi con messaggi in attesa di essere inviati al momento dell'esecuzione di ALTER DATABASE, la nuova impostazione non viene applicata fino a quando alcuni messaggi del dialogo non sono stati inviati. La quantità di tempo che deve trascorrere prima che la nuova impostazione venga usata per tutti i dialoghi può variare notevolmente.  
  
 L'impostazione corrente di questa proprietà è indicata nella colonna is_broker_priority_honored il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
 **\<snapshot_option >:: =**  
  
 Determina il livello di isolamento delle transazioni.  
  
 ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
 ON  
 Abilita l'opzione relativa allo snapshot a livello di database. Quando è abilitata, le istruzioni DML iniziano la generazione di versioni di riga anche quando nessuna transazione usano l'isolamento dello snapshot. Una volta abilitata l'opzione, le transazioni possono specificare il livello di isolamento della transazione SNAPSHOT. Nelle transazioni eseguite con il livello di isolamento SNAPSHOT, tutte le istruzioni possono accedere a uno snapshot dei dati corrispondente allo stato dei dati al momento dell'avvio della transazione. Se una transazione eseguita con il livello di isolamento SNAPSHOT deve accedere ai dati in più database, è necessario impostare ALLOW_SNAPSHOT_ISOLATION su ON in tutti i database oppure ogni istruzione della transazione deve usare hint di blocco per qualsiasi riferimento in una clausola FROM a una tabella di un database per cui l'opzione ALLOW_SNAPSHOT_ISOLATION è impostata su OFF.  
  
 OFF  
 Consente di disabilitare l'opzione Snapshot a livello di database. Per le transazioni non può essere impostato il livello di isolamento della transazione SNAPSHOT.  
  
 Quando si imposta un nuovo stato per l'opzione ALLOW_SNAPSHOT_ISOLATION (da ON a OFF oppure da OFF a ON), ALTER DATABASE restituisce il controllo al chiamante solo dopo il completamento del commit di tutte le transazioni esistenti nel database. Se per il database è già attivo lo stato specificato nell'istruzione ALTER DATABASE, il controllo viene restituito immediatamente al chiamante. Se l'istruzione ALTER DATABASE non restituisca rapidamente, utilizzare [Sys.dm tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) per determinare se sono presenti transazioni a esecuzione prolungata. Se l'istruzione ALTER DATABASE viene annullata, il database rimane nello stato attivo al momento dell'avvio dell'istruzione ALTER DATABASE. Il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo indica lo stato delle transazioni di isolamento dello snapshot nel database. Se **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON, ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF verrà sei secondi e ripetere l'operazione.  
  
 Non è possibile modificare lo stato di ALLOW_SNAPSHOT_ISOLATION se il database è OFFLINE.  
  
 Se si imposta ALLOW_SNAPSHOT_ISOLATION in un database READ_ONLY, tale impostazione viene mantenuta anche se il database viene in seguito impostato su READ_WRITE.  
  
 È possibile modificare le impostazioni di ALLOW_SNAPSHOT_ISOLATION per i database master, model, msdb e tempdb. Se si modifica l'impostazione per il database tempdb, questa viene mantenuta per ogni arresto e riavvio dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Se si modifica l'impostazione per il database model, questa diventa l'impostazione predefinita per i nuovi database creati, con l'eccezione di tempdb.  
  
 L'impostazione predefinita dell'opzione è ON per i database master e msdb.  
  
 Per determinare l'impostazione corrente di questa opzione, è possibile esaminare la colonna snapshot_isolation_state nella vista del catalogo sys.databases.  
  
 READ_COMMITTED_SNAPSHOT { ON | OFF }  
 ON  
 Abilita l'opzione relativa allo snapshot Read Committed a livello di database. Quando è abilitata, le istruzioni DML iniziano la generazione di versioni di riga anche quando nessuna transazione usano l'isolamento dello snapshot. Una volta abilitata questa opzione, le transazioni che specificano il livello di isolamento Read committed usano il controllo delle versioni delle righe anziché il blocco. Quando una transazione viene eseguita con il livello di isolamento Read committed, tutte le istruzioni possono accedere a uno snapshot dei dati corrispondente allo stato dei dati all'avvio dell'istruzione.  
  
 OFF  
 Disabilita l'opzione relativa allo snapshot Read Committed a livello di database. Le transazioni per cui è impostato il livello di isolamento READ COMMITTED usano il blocco.  
  
 Per impostare READ_COMMITTED_SNAPSHOT su ON oppure OFF, è necessario che non siano presenti connessioni attive al database, ad eccezione della connessione usata per eseguire il comando ALTER DATABASE. Non è tuttavia necessario che il database sia in modalità utente singolo. Non è possibile modificare lo stato di questa opzione quando il database è OFFLINE.  
  
 Se si imposta READ_COMMITTED_SNAPSHOT in un database READ_ONLY, tale impostazione viene mantenuta anche se il database viene in seguito impostato su READ_WRITE.  
  
 Non è possibile impostare READ_COMMITTED_SNAPSHOT su ON per i database di sistema master, tempdb e msdb. Se si modifica l'impostazione per il database model, questa diventa l'impostazione predefinita per i nuovi database creati, con l'eccezione di tempdb.  
  
 Per determinare l'impostazione corrente di questa opzione, è possibile esaminare la colonna is_read_committed_snapshot_on nella vista del catalogo sys.databases.  
  
> [!WARNING]  
>  Quando viene creata una tabella con **DURABILITY = SCHEMA_ONLY**, e **READ_COMMITTED_SNAPSHOT** viene successivamente modificata usando **ALTER DATABASE**, nella tabella dati andranno perduti.  
  
 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 ON  
 Quando il livello di isolamento della transazione è impostato su un qualsiasi livello di isolamento inferiore a SNAPSHOT, ad esempio READ COMMITTED o READ UNCOMMITTED, tutte le operazioni interpretate di [!INCLUDE[tsql](../../includes/tsql-md.md)] nelle tabelle ottimizzate per la memoria vengono eseguite tramite l'isolamento SNAPSHOT. Questa operazione viene eseguita indipendentemente dal fatto che il livello di isolamento della transazione sia impostato in modo esplicito a livello di sessione o venga usata in modo implicito che l'impostazione predefinita.  
  
 OFF  
 Non eleva il livello di isolamento della transazione per le operazioni interpretate di [!INCLUDE[tsql](../../includes/tsql-md.md)] nelle tabelle ottimizzate per la memoria.  
  
 Non è possibile modificare lo stato di MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT se il database è OFFLINE.  
  
 Per impostazione predefinita, l'opzione è OFF.  
  
 L'impostazione corrente di questa opzione può essere determinata esaminando il **is_memory_optimized_elevate_to_snapshot_on** colonna il [Sys. Databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
 **\<sql_option si >:: =**  
  
 Controlla le opzioni di conformità ANSI a livello di database.  
  
 ANSI_NULL_DEFAULT { ON | OFF }  
 Determina il valore predefinito, NULL o NOT NULL, di una colonna o [tipo CLR definito dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) per il supporto di valori null non esplicitamente definito in istruzioni CREATE TABLE o ALTER TABLE. Le colonne definite con vincoli seguono le regole dei vincoli indipendentemente da questa impostazione.  
  
 ON  
 Il valore predefinito è NULL.  
  
 OFF  
 Il valore predefinito è NOT NULL.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per ANSI_NULL_DEFAULT. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta ANSI_NULL_DEFAULT su ON per la sessione quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [SET ANSI_NULL_DFLT_ON &#40; Transact-SQL &#41; ](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md).  
  
 Per motivi di compatibilità con ANSI, l'impostazione dell'opzione di database ANSI_NULL_DEFAULT su ON modifica l'impostazione predefinita del database su NULL.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_ansi_null_default_on nella vista del catalogo sys.databases oppure la proprietà IsAnsiNullDefault della funzione DATABASEPROPERTYEX.  
  
 ANSI_NULLS { ON | OFF }  
 ON  
 Tutti i confronti con un valore Null restituiscono UNKNOWN.  
  
 OFF  
 I confronti di valori non UNICODE con un valore Null restituiscono TRUE se entrambi i valori sono NULL.  
  
> [!IMPORTANT]  
>  In una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ANSI_NULLS sarà sempre impostata su ON e qualsiasi applicazione che imposta tale opzione in modo esplicito su OFF genererà un errore. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per ANSI_NULLS. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta ANSI_NULLS su ON per la sessione quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 È inoltre necessario che l'opzione SET ANSI_NULLS sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_ansi_nulls_on nella vista del catalogo sys.databases oppure la proprietà IsAnsiNullsEnabled della funzione DATABASEPROPERTYEX.  
  
 ANSI_PADDING { ON | OFF }  
 ON  
 Le stringhe vengono riempite fino alla stessa lunghezza prima della conversione o inserimento di un **varchar** o **nvarchar** tipo di dati.  
  
 Gli spazi finali in valori di tipo carattere inseriti **varchar** o **nvarchar** colonne e gli zeri finali in valori binari inseriti in **varbinary** colonne non vengono rimossi. . I valori non vengono riempiti con caratteri nulli per l'intera lunghezza della colonna.  
  
 OFF  
 Per gli spazi vuoti finali **varchar** o **nvarchar** e gli zeri per **varbinary** vengono tagliati.  
  
 Se si specifica OFF, questa impostazione ha effetto solo sulla definizione di nuove colonne.  
  
> [!IMPORTANT]  
>  In una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ANSI_PADDING sarà sempre impostata su ON e qualsiasi applicazione che imposta tale opzione in modo esplicito su OFF genererà un errore. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. È consigliabile impostare l'opzione ANSI_PADDING sempre su ON. È necessario che l'opzione ANSI_PADDING sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate.  
  
 **Char(*n*)** e **binario(*n*)** le colonne che ammettono valori null vengono riempite fino alla lunghezza della colonna quando l'opzione ANSI_PADDING è impostata. su ON, ma gli spazi vuoti e gli zeri finali vengono eliminati se ANSI_PADDING è OFF. **Char(*n*)** e **binario(*n*)** le colonne che non consentono valori null vengono sempre riempite fino alla lunghezza della colonna.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per ANSI_PADDING. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta ANSI_PADDING su ON per la sessione quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_ansi_padding_on nella vista del catalogo sys.databases oppure la proprietà IsAnsiPaddingEnabled della funzione DATABASEPROPERTYEX.  
  
 ANSI_WARNINGS { ON | OFF }  
 ON  
 Vengono generati errori o avvisi se si verificano condizioni quali la divisione per zero oppure in presenza di valori Null nelle funzioni di aggregazione.  
  
 OFF  
 Non vengono generati avvisi e vengono restituiti valori Null quando si verificano condizioni come la divisione per zero.  
  
 È necessario che l'opzione ANSI_WARNINGS sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per ANSI_WARNINGS. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta ANSI_WARNINGS su ON per la sessione quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_ansi_warnings_on nella vista del catalogo sys.databases oppure la proprietà IsAnsiWarningsEnabled della funzione DATABASEPROPERTYEX.  
  
 ARITHABORT { ON | OFF }  
 ON  
 Interrompe una query quando si verifica un overflow o un errore di divisione per zero durante l'esecuzione della query stessa.  
  
 OFF  
 Visualizza un messaggio di avviso quando si verifica uno di questi errori, ma l'elaborazione della query, del batch o della transazione prosegue come se non si fosse verificato alcun errore.  
  
 È necessario che l'opzione ARITHABORT sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_arithabort_on nella vista del catalogo sys.databases oppure la proprietà IsArithmeticAbortEnabled della funzione DATABASEPROPERTYEX.  
  
 COMPATIBILITY_LEVEL { 90 | 100 | 110 | 120}  
 Per altre informazioni, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 CONCAT_NULL_YIELDS_NULL { ON | OFF }  
 ON  
 Il risultato di un'operazione di concatenazione è NULL quando uno degli operandi è NULL. La concatenazione della stringa di caratteri "Questo è" con NULL restituisce, ad esempio, il valore NULL anziché il valore "Questo è".  
  
 OFF  
 Il valore Null viene considerato come una stringa di caratteri vuota.  
  
 È necessario che l'opzione CONCAT_NULL_YIELDS_NULL sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate.  
  
> [!IMPORTANT]  
>  In una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'opzione CONCAT_NULL_YIELDS_NULL sarà sempre impostata su ON e qualsiasi applicazione che la imposta in modo esplicito su OFF restituirà un errore. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per CONCAT_NULL_YIELDS_NULL. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta CONCAT_NULL_YIELDS_NULL su ON per la sessione quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_concat_null_yields_null_on nella vista del catalogo sys.databases oppure la proprietà IsNullConcat della funzione DATABASEPROPERTYEX.  
  
 QUOTED_IDENTIFIER { ON | OFF }  
 ON  
 È possibile usare le virgolette doppie per delimitare gli identificatori delimitati.  
  
 Tutte le stringhe delimitate da virgolette doppie vengono interpretate come identificatori di oggetto. Gli identificatori delimitati non devono necessariamente essere conformi alle regole di [!INCLUDE[tsql](../../includes/tsql-md.md)] per gli identificatori. Possono essere parole chiave e includere caratteri normalmente non consentiti negli identificatori [!INCLUDE[tsql](../../includes/tsql-md.md)]. Se una virgoletta singola (') fa parte della stringa letterale, può essere rappresentata tramite virgolette doppie (").  
  
 OFF  
 Gli identificatori non possono essere delimitati da virgolette e devono essere conformi a tutte le regole di [!INCLUDE[tsql](../../includes/tsql-md.md)] per gli identificatori. È possibile delimitare i valori letterali con virgolette singole o doppie.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente inoltre di racchiudere gli identificatori tra parentesi quadre ([ ]). Gli identificatori tra parentesi quadre possono essere sempre usati, indipendentemente dall'impostazione di QUOTED_IDENTIFIER. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  
  
 Durante la creazione di una tabella, l'opzione QUOTED IDENTIFIER viene sempre archiviata con l'impostazione ON nei metadati della tabella, anche se l'opzione viene impostata su OFF quando si crea la tabella.  
  
 Le impostazioni a livello di connessione definite usando l'istruzione SET sono prioritarie rispetto all'impostazione predefinita del database per QUOTED_IDENTIFIER. Per impostazione predefinita, i client ODBC e OLE DB eseguono un'istruzione SET a livello di connessione che imposta QUOTED_IDENTIFIER su ON quando viene stabilita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_quoted_identifier_on nella vista del catalogo sys.databases oppure la proprietà IsQuotedIdentifiersEnabled della funzione DATABASEPROPERTYEX.  
  
 NUMERIC_ROUNDABORT { ON | OFF }  
 ON  
 Viene generato un errore quando si verifica una perdita di precisione in un'espressione.  
  
 OFF  
 In seguito alla perdita di precisione non viene generato alcun messaggio di errore e il risultato viene arrotondato alla precisione della colonna o della variabile in cui viene archiviato.  
  
 È necessario che l'opzione NUMERIC_ROUNDABORT sia impostata su OFF quando vengono creati o modificati indici in colonne calcolate o viste indicizzate.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_numeric_roundabort_on nella vista del catalogo sys.databases oppure la proprietà IsNumericRoundAbortEnabled della funzione DATABASEPROPERTYEX.  
  
 RECURSIVE_TRIGGERS { ON | OFF }  
 ON  
 È consentita l'attivazione ricorsiva di trigger AFTER.  
  
 OFF  
 Solo l'attivazione ricorsiva diretta di trigger AFTER non è consentita. Per disabilitare anche la ricorsione indiretta dei trigger AFTER, impostare l'opzione nested triggers server **0** utilizzando **sp_configure**.  
  
> [!NOTE]  
>  Se l'opzione RECURSIVE_TRIGGERS è impostata su OFF, viene impedita esclusivamente la ricorsione diretta. Per disabilitare la ricorsione indiretta, è necessario impostare anche l'opzione del server nested triggers su 0.  
  
 Per determinare lo stato di questa opzione, è possibile esaminare la colonna is_recursive_triggers_on nella vista del catalogo sys.databases oppure la proprietà IsRecursiveTriggersEnabled della funzione DATABASEPROPERTYEX.  
  
 **\<target_recovery_time_option >:: =**  
  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Specifica la frequenza di checkpoint indiretti per database singolo. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] il valore predefinito per i nuovi database è 1 minuto, a indicare database utilizzerà checkpoint indiretti. Per le versioni precedenti il valore predefinito è 0, che indica che il database utilizzerà checkpoint automatici la cui frequenza dipende dall'impostazione dell'intervallo di recupero dell'istanza del server. [!INCLUDE[msCoName](../../includes/msconame-md.md)]si consiglia di 1 minuto per la maggior parte dei sistemi.  
  
 TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDI | MINUTI }  
 *target_recovery_time*  
 Specifica il limite massimo di tempo per recuperare il database specificato in caso di un arresto anomalo del sistema.  
  
 SECONDS  
 Indica che *target_recovery_time* viene espresso come numero di secondi.  
  
 MINUTES  
 Indica che *target_recovery_time* viene espresso come numero di minuti.  
  
 Per ulteriori informazioni sui checkpoint indiretti, vedere [checkpoint di Database &#40; SQL Server &#41; ](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 **CON \<terminazione >:: =**  
  
 Specifica quando eseguire il rollback di transazioni incomplete in caso di transizione dello stato del database. Se questa clausola viene omessa, l'attesa da parte dell'istruzione ALTER DATABASE è illimitata in presenza di qualsiasi blocco attivo sul database. È possibile specificare una sola clausola di terminazione, che deve seguire le clausole SET.  
  
> [!NOTE]  
>  Non tutte le opzioni di database usano WITH \<terminazione > clausola. Per ulteriori informazioni, vedere la tabella in "[impostazione delle opzioni](#SettingOptions) nella sezione"Osservazioni"di questo argomento.  
  
 ROLLBACK AFTER *intero* [SECONDS] | ROLLBACK IMMEDIATE  
 Specifica se eseguire il rollback dopo il numero di secondi specificato o immediatamente.  
  
 NO_WAIT  
 Specifica che la richiesta avrà esito negativo se non è possibile completare immediatamente la modifica dell'opzione o dello stato del database richiesta senza attendere il commit o il rollback delle transazioni.  
  
##  <a name="SettingOptions"></a>Impostazione delle opzioni  
 Per recuperare le impostazioni correnti per le opzioni di database, utilizzare il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo o [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)  
  
 Dopo avere impostato un'opzione di database, la modifica diventa effettiva immediatamente.  
  
 Per modificare i valori predefiniti di qualsiasi opzione di database per tutti i nuovi database, modificare l'opzione di database appropriata nel database model.  
  
 Non tutte le opzioni di database usano WITH \<terminazione > clausola o possono essere specificate in combinazione con altre opzioni. Nella tabella seguente sono elencate tali opzioni con indicazione del supporto della clausola di terminazione o dell'impostazione in combinazione con altre opzioni.  
  
|Categoria di opzioni|Impostazione in combinazione con altre opzioni|Utilizzare WITH \<terminazione > clausola|  
|----------------------|-----------------------------------------|---------------------------------------------|  
|\<db_state_option >|Sì|Sì|  
|\<db_user_access_option >|Sì|Sì|  
|\<db_update_option >|Sì|Sì|  
|\<delayed_durability_option >|Sì|Sì|  
|\<external_access_option >|Sì|No|  
|\<cursor_option >|Sì|No|  
|\<auto_option >|Sì|No|  
|\<sql_option si >|Sì|No|  
|\<recovery_option >|Sì|No|  
|\<target_recovery_time_option >|No|Sì|  
|\<database_mirroring_option >|No|No|  
|ALLOW_SNAPSHOT_ISOLATION|No|No|  
|READ_COMMITTED_SNAPSHOT|No|Sì|  
|MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT|Sì|Sì|  
|\<service_broker_option >|Sì|No|  
|DATE_CORRELATION_OPTIMIZATION|Sì|Sì|  
|\<parameterization_option >|Sì|Sì|  
|\<change_tracking_option >|Sì|Sì|  
|\<db_encryption >|Sì|No|  
  
 La cache dei piani per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene cancellata quando si imposta una delle opzioni seguenti:  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY||  
  
 La cache delle procedure viene inoltre scaricata negli scenari seguenti.  
  
-   L'opzione AUTO_CLOSE di un database è impostata su ON. Se il database non viene utilizzato da alcuna connessione utente, neanche come riferimento, tramite l'attività in background viene effettuato il tentativo di chiusura e di arresto automatici del database.  
  
-   Vengono eseguite diverse query su un database contenente opzioni predefinite. Successivamente, il database viene eliminato.  
  
-   Viene eliminato uno snapshot del database per un database di origine.  
  
-   Viene ricompilato correttamente il log delle transazioni per un database.  
  
-   Viene ripristinato un backup del database.  
  
-   Viene scollegato un database.  
  
 La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni di manutenzione o riconfigurazione del database". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-setting-options-on-a-database"></a>A. Impostazione di opzioni in un database  
 Nell'esempio seguente vengono impostate le opzioni relative al modello di recupero e alla verifica delle pagine di dati per il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL PAGE_VERIFY CHECKSUM;  
GO  
  
```  
  
### <a name="b-setting-the-database-to-readonly"></a>B. Impostazione del database su READ_ONLY  
 Per modificare lo stato di un database o di un filegroup impostandolo su READ_ONLY o READ_WRITE, è necessario l'accesso esclusivo al database. Nell'esempio seguente viene impostata la modalità `SINGLE_USER` per il database in modo da ottenere l'accesso esclusivo. Nell'esempio lo stato del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] viene quindi impostato su `READ_ONLY` e viene ripristinato l'accesso al database per tutti gli utenti.  
  
> [!NOTE]  
>  In questo esempio viene usata l'opzione di terminazione `WITH ROLLBACK IMMEDIATE` nella prima istruzione `ALTER DATABASE`. Verrà eseguito il rollback di tutte le transazioni incomplete e tutte le altre connessioni al database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] verranno interrotte immediatamente.  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET SINGLE_USER  
WITH ROLLBACK IMMEDIATE;  
GO  
ALTER DATABASE AdventureWorks2012  
SET READ_ONLY  
GO  
ALTER DATABASE AdventureWorks2012  
SET MULTI_USER;  
GO  
  
```  
  
### <a name="c-enabling-snapshot-isolation-on-a-database"></a>C. Abilitazione dell'isolamento dello snapshot in un database  
 Nell'esempio seguente viene abilitata l'opzione relativa al framework di isolamento dello snapshot per il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET ALLOW_SNAPSHOT_ISOLATION ON;  
GO  
-- Check the state of the snapshot_isolation_framework  
-- in the database.  
SELECT name, snapshot_isolation_state,   
    snapshot_isolation_state_desc AS description  
FROM sys.databases  
WHERE name = N'AdventureWorks2012';  
GO  
  
```  
  
 Il set di risultati indica che il framework di isolamento dello snapshot è abilitato.  
  
 |name |snapshot_isolation_state |description|  
 |-------------------- |------------------------  |----------|  
 |AdventureWorks2012   |1                        | ON |  
  
### <a name="d-enabling-modifying-and-disabling-change-tracking"></a>D. Abilitazione, modifica e disabilitazione del rilevamento delle modifiche  
 Nell'esempio seguente viene abilitato il rilevamento delle modifiche per il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e il periodo di memorizzazione viene impostato su `2` giorni.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);  
```  
  
 Nell'esempio seguente viene illustrato come modificare il periodo di memorizzazione impostandolo su `3` giorni.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);  
```  
  
 Nell'esempio seguente viene illustrato come disabilitare il rilevamento delle modifiche per il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF;  
```  
  
### <a name="e-enabling-the-query-store"></a>E. Abilitazione dell'archivio di query  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 L'esempio seguente abilita l'archivio di query e configura i relativi parametri.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET QUERY_STORE = ON   
    (  
      OPERATION_MODE = READ_ONLY   
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 5 )  
    , DATA_FLUSH_INTERVAL_SECONDS = 2000   
    , MAX_STORAGE_SIZE_MB = 10   
    , INTERVAL_LENGTH_MINUTES = 10   
    );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [Statistiche](../../relational-databases/statistics/statistics.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Abilitare e disabilitare il rilevamento delle modifiche &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)  
  
  
