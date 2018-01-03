---
title: ALTER DATABASE (Database SQL Azure) | Documenti Microsoft
ms.custom: 
ms.date: 12/20/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: "37"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e8d0df617bef08305166f4112fcb4f4d371137d2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Modifica un [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Modifica il nome di un obiettivo del database, l'edizione e il servizio di un database, join di un pool elastico e imposta le opzioni di database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name }  
{  
    MODIFY NAME = new_database_name  
  | MODIFY ( <edition_options> [, ... n] )   
  | SET { <option_spec> [ ,... n ] }   
  | ADD SECONDARY ON SERVER <partner_server_name>  
      [WITH ( <add-secondary-option>::= [, ... n] ) ]  
  | REMOVE SECONDARY ON SERVER <partner_server_name>  
  | FAILOVER  
  | FORCE_FAILOVER_ALLOW_DATA_LOSS  
}  
[;] 

<edition_options> ::=   
{  

      MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }    
    | EDITION = { 'basic' | 'standard' | 'premium' | 'premiumrs' }   
    | SERVICE_OBJECTIVE = 
                 {  <service-objective>
                 | { ELASTIC_POOL (name = <elastic_pool_name>) }   
                 }   
}  

<add-secondary-option> ::=  
   {  
      ALLOW_CONNECTIONS = { ALL | NO }  
     | SERVICE_OBJECTIVE =   
                 {  <service-objective> 
                 | { ELASTIC_POOL ( name = <elastic_pool_name>) }   
                 }   
   }  

<service-objective> ::=  { 'S0' | 'S1' | 'S2' | 'S3'| 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |
                 | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15' | 
                 | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' | }

```  
  
```
-- SET OPTIONS AVAILABLE FOR SQL Database  
-- Full descriptions of the set options are available in the topic   
-- ALTER DATABASE SET Options. The supported syntax is listed here.  

<option_spec> ::=   
{  
    <auto_option>   
  | <change_tracking_option> 
  | <cursor_option>   
  | <db_encryption_option>  
  | <db_update_option>   
  | <db_user_access_option>   
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option>   
  | <target_recovery_time_option>   
  | <termination>  
  | <temporal_history_retention>  
}  
  
<auto_option> ::=   
{  
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }   
  | AUTO_SHRINK { ON | OFF }   
  | AUTO_UPDATE_STATISTICS { ON | OFF }   
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
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

<cursor_option> ::=   
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }   
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
  
<db_update_option> ::=  
    { READ_ONLY | READ_WRITE }  
  
<db_user_access_option> ::=  
    { RESTRICTED_USER | MULTI_USER }  
  
<delayed_durability_option> ::=    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<parameterization_option> ::=  
    PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
    QUERY_STORE   
    {  
          = OFF   
        | = ON [ ( <query_store_option_list> [,... n] ) ]  
        | ( < query_store_option_list> [,... n] )  
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
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }  
}  
<sql_option> ::=   
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 100 | 110 | 120 | 130 | 140 }  
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  

<temporal_history_retention>  ::=  TEMPORAL_HISTORY_RETENTION { ON | OFF }
```  
  
 Per una descrizione completa delle opzioni set, vedere [opzioni ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) e [modificare a livello di compatibilità del DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database da modificare.  
  
 CURRENT  
 Specifica che il database corrente in uso deve essere modificato.  
  
 Modifica nome  **=**  *new_database_name*  
 Rinomina il database con il nome specificato come *new_database_name*. Nell'esempio seguente modifica il nome di un database `db1` a `db2`:   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

 Modifica (edizione  **=**  ['base' | 'standard' | 'premium' | 'premiumrs'])    
 Modifica il livello di servizio del database. L'esempio seguente modifica edition a `premium`:
  
```  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

La modifica dell'edizione ha esito negativo se la proprietà MAXSIZE per il database è impostata su un valore non compreso nell'intervallo valido supportato dall'edizione.  

 MODIFICARE (MAXSIZE  **=**  [100 MB | 500 MB | 1 | 1024... 4096] GB)  
 Specifica le dimensioni massime del database. Le dimensioni massime devono essere conformi al set valido di valori per la proprietà EDITION del database. La modifica delle dimensioni massime del database può causare la modifica del valore di EDITION del database. Nella tabella seguente sono elencati i valori MAXSIZE supportati e i valori predefiniti (P) per i livelli del servizio di [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|**MAXSIZE**|**Basic**|**S0 S2**|**S3 S12**|**P1 P6 e PRS1 PRS6**|**P11 P15**|  
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------|  
|100 MB|√|√|√|√|√|  
|250 MB|√|√|√|√|√|  
|500 MB|√|√|√|√|√|  
|1 GB|√|√|√|√|√|  
|2 GB|√ (P)|√|√|√|√|  
|5 GB|N/D|√|√|√|√|  
|10 GB|N/D|√|√|√|√|  
|20 GB|N/D|√|√|√|√|  
|30 GB|N/D|√|√|√|√|  
|40 GB|N/D|√|√|√|√|  
|50 GB|N/D|√|√|√|√|  
|100 GB|N/D|√|√|√|√|  
|150 GB|N/D|√|√|√|√|  
|200 GB|N/D|√|√|√|√|  
|250 GB|N/D|√ (P)|√ (P)|√|√|  
|300 GB|N/D|√|√|√|√|  
|400 GB|N/D|√|√|√|√|  
|500 GB|N/D|√|√|√ (P)|√|  
|750 GB|N/D|√|√|√|√|  
|1024 GB|N/D|√|√|√|√ (P)|  
|Da 1024 GB fino a 4096 GB con incrementi di 256 GB *|N/D|N/D|N/D|N/D|√|√|  
  
 \*P11 e P15 consentono MAXSIZE fino a 4 TB con 1024 GB da quelle predefinite.  P11 e P15 possono utilizzare fino a 4 TB di spazio di archiviazione incluse senza costi aggiuntivi. Nel livello Premium, MAXSIZE maggiore di 1 TB è attualmente disponibile nelle seguenti aree: ci East2, Stati Uniti occidentali, ci Gov Virginia, Europa occidentale, Germania centrale, Sud Asia sudorientale, Giappone orientale, Australia orientale, Canada centrale e Canada orientale. Per le limitazioni attuali, vedere [singolo database](https://docs.microsoft.com/azure/sql-database-single-database-resources).  

  
 Le seguenti regole vengono applicate agli argomenti MAXSIZE ed EDITION:  
  
-   Il valore MAXSIZE, se specificato, deve essere un valore valido presente nella tabella precedente.  
  
-   Se il valore di EDITION è specificato e il valore di MAXSIZE viene omesso, viene utilizzato il valore predefinito dell'edizione. Ad esempio, se EDITION è impostato su Standard e MAXSIZE non è specificato, il valore di MAXSIZE viene automaticamente impostato su 500 MB.  
  
-   Se né MAXSIZE né EDITION vengono specificati, EDITION viene impostato su Standard (S0) e MAXSIZE viene impostato su 250 GB.  
 

 Modifica (SERVICE_OBJECTIVE = \<obiettivo di servizio >)  
 Specifica il livello di prestazioni. Nell'esempio seguente servizio obiettivo di un database premium per `P6`:
 
```  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  
 I valori disponibili per l'obiettivo di servizio sono: `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `PRS1`, `PRS2`, `PRS4`, e `PRS6`. Per descrizioni degli obiettivi di servizio e altre informazioni sulle dimensioni, edizioni e combinazioni di obiettivi di servizio, vedere [livelli di servizio di Database SQL Azure e i livelli di prestazioni](http://msdn.microsoft.com/library/azure/dn741336.aspx). Se il SERVICE_OBJECTIVE specificato non è supportato dall'edizione, viene visualizzato un errore. Per cambiare il valore di SERVICE_OBJECTIVE da un livello a un altro (ad esempio da S1 a P1), è necessario modificare anche il valore EDITION.  
  
 Modifica (SERVICE_OBJECTIVE = ELASTICA\_POOL (nome = \<elastic_pool_name >)  
 Per aggiungere un database esistente a un pool elastico, impostare l'ELASTIC_POOL SERVICE_OBJECTIVE del database e specificare il nome del pool elastico. È inoltre possibile utilizzare questa opzione per modificare il database a un pool elastico diversi nello stesso server. Per ulteriori informazioni, vedere [creare e gestire un pool elastico SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Per rimuovere un database da un pool elastico, utilizzare ALTER DATABASE per impostare il SERVICE_OBJECTIVE a livello di prestazioni un singolo database.  

 Aggiungere SERVER secondario ON \<partner_server_name >  
 Crea un database di replica geografica secondaria con lo stesso nome in un server partner, rendendo il database locale in una replica geografica primaria e viene avviata in modo asincrono la replica dei dati dal database primario per il nuovo database secondario. Se un database con lo stesso nome esiste già nel database secondario, il comando non riesce. Il comando viene eseguito nel database master nel server che ospita il database locale diventa il database primario.  
  
 CON L'ARGOMENTO ALLOW_CONNECTIONS {TUTTI | **N** }  
 Quando l'argomento ALLOW_CONNECTIONS viene omesso, viene impostata su NO per impostazione predefinita. Se è impostato tutti, è un database di sola lettura che consente a tutti gli account di accesso con le autorizzazioni appropriate per la connessione.  
  
 CON SERVICE_OBJECTIVE {'S0' | 'S1' | 'S2 ' IN CORSO... | ' S3 "| 'S4' | 'S6' | 'S7' | 'S9' | 'S12' | 'P1' | 'P2' | 'P4' | 'P6' | 'P11' | 'P15' | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6'}  
 Se SERVICE_OBJECTIVE non è specificato, il database secondario viene creato a livello di servizio stesso come database primario. Se SERVICE_OBJECTIVE è impostata, il database secondario viene creato al livello specificato. Questa opzione supporta la creazione di database secondari con replica geografica con i livelli di servizio meno costosi. Il SERVICE_OBJECTIVE specificato deve essere compresa la stessa edizione come origine. Ad esempio, è possibile specificare S0 se l'edizione premium.  
  
 ELASTIC_POOL (nome = \<elastic_pool_name)  
 Quando ELASTIC_POOL non viene specificato, il database secondario non viene creato in un pool elastico. Quando viene specificato ELASTIC_POOL, il database secondario viene creato nel pool specificato.  
  
> [!IMPORTANT]  
>  L'utente che esegue il comando Aggiungi database secondario deve essere DBManager nel server primario, sono membri di db_owner nel database locale e DBManager nel server secondario.  
  
 Rimuovi SERVER secondario ON \<partner_server_name >  
 Rimuove il replica geografica secondario database specificato nel server specificato. Il comando viene eseguito nel database master nel server che ospita il database primario.  
  
> [!IMPORTANT]  
>  L'utente che esegue il comando rimuovere secondario deve essere DBManager nel server primario.  
  
 FAILOVER  
 Alza di livello database secondario nella relazione di replica geografica in cui il comando viene eseguito per principale e Abbassa di livello il database primario corrente per diventare il nuovo database secondario. Come parte di questo processo, la modalità di replica geografica temporaneamente passa dalla modalità asincrona in modalità sincrona. Durante il processo di failover:  
  
1.  Il database primario viene arrestato accettando nuove transazioni.  
  
2.  Tutte le transazioni in sospeso vengono scaricate nel database secondario.  
  
3.  Il database secondario diventa la primaria e viene avviata la replica geografica asincrona con primario precedente o il nuovo database secondario.  
  
 Questa sequenza assicura che si verifica alcuna perdita di dati. Il periodo durante il quale non sono disponibili entrambi i database è nell'ordine di secondi 0-25, mentre i ruoli vengono scambiati. L'operazione totale richiede non più di circa un minuto. Se il database primario è disponibile quando viene eseguito questo comando, il comando ha esito negativo con un messaggio di errore che indica che il database primario non è disponibile. Se il processo di failover non viene completata e sembra bloccato, è possibile utilizzare il comando di failover forzato e accettare la perdita di dati e quindi, se è necessario recuperare i dati persi, chiamare devops (CSS) per recuperare i dati perduti.  
  
> [!IMPORTANT]  
>  L'utente che esegue il comando FAILOVER deve essere DBManager nel server primario e il server secondario.  
  
 FORCE_FAILOVER_ALLOW_DATA_LOSS  
 Alza di livello database secondario nella relazione di replica geografica in cui il comando viene eseguito per principale e Abbassa di livello il database primario corrente per diventare il nuovo database secondario. Utilizzare questo comando solo quando il database primario corrente non è più disponibile. È progettato per il ripristino di emergenza, solo quando la disponibilità di ripristino è critico e perdita di dati è accettabile.  
  
 Durante un failover forzato:  
  
1.  Il database secondario specificato immediatamente diventa il database primario e inizia ad accettare nuove transazioni.  
  
2.  Quando la replica primaria originale può riconnettersi con il nuovo database primario, un backup incrementale viene eseguito sull'originale primario e la replica primaria originale diventa un nuovo database secondario.  
  
3.  Per ripristinare dati da questo backup incrementale sul database primario precedente, l'utente si attiva devops/CSS.  
  
4.  Se sono presenti altri database secondari, vengono riconfigurati automaticamente per diventano database secondari del nuovo database primario. Questo processo è asincrono e potrebbe verificarsi un ritardo fino al completamento di questo processo. Fino a quando non è stata completata la riconfigurazione, i database secondari continuano a essere repliche secondarie del database primario precedente.  
  
> [!IMPORTANT]  
>  L'utente che esegue il comando FORCE_FAILOVER_ALLOW_DATA_LOSS deve essere DBManager nel server primario e il server secondario.  
  
## <a name="remarks"></a>Osservazioni  
 Per rimuovere un database, utilizzare [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Per ridurre le dimensioni di un database, utilizzare [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
 L'istruzione ALTER DATABASE deve essere eseguita in modalità autocommit (modalità predefinita di gestione delle transazioni) e non è consentita in una transazione esplicita o implicita.  
  
 La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni di manutenzione o riconfigurazione del database". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.  
  
 La cache delle procedure viene inoltre scaricata negli scenari seguenti:  
  
-   L'opzione AUTO_CLOSE di un database è impostata su ON. Se il database non viene utilizzato da alcuna connessione utente, neanche come riferimento, tramite l'attività in background viene effettuato il tentativo di chiusura e di arresto automatici del database.  
  
-   Vengono eseguite diverse query su un database contenente opzioni predefinite. Successivamente, il database viene eliminato.  
  
-   Viene ricompilato correttamente il log delle transazioni per un database.  
  
-   Viene ripristinato un backup del database.  
  
-   Viene scollegato un database.  
  
## <a name="viewing-database-information"></a>Visualizzazione delle informazioni sui database  
 Per restituire informazioni su database, file e filegroup, è possibile usare viste del catalogo, funzioni di sistema e stored procedure di sistema.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo l'account di accesso dell'entità a livello di server (creato dal processo di provisioning) o i membri del ruolo del database `dbmanager` possono modificare un database.  
  
> [!IMPORTANT]  
>  Il proprietario del database può modificare il database solo se è un membro del ruolo `dbmanager`.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Controllare le opzioni di edizione e modificarli in:

```
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>B. Spostare un database in un altro pool elastico  
 Sposta un database esistente in un pool denominato pool1:  
  
```  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>C. Aggiungere un database di replica geografica secondario  
 Crea un database secondario non leggibile di db1 sul server `secondaryserver` del db1 nel server locale.  
  
```  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = NO )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>D. Rimuovere la replica geografica secondaria  
 Rimuove il database secondario db1 sul server `secondaryserver`.  
  
```  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>E. Failover a un database di replica geografica secondario  
 Alza di livello db1 un database secondario nel server `secondaryserver` per diventare il nuovo database primario quando viene eseguito sul server `secondaryserver`.  
  
```  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Crea DATABASE &#40; Database SQL di Azure &#41;](../../t-sql/statements/create-database-azure-sql-database.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys. FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys. master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Database di sistema.](../../relational-databases/databases/system-databases.md)  
  
  
