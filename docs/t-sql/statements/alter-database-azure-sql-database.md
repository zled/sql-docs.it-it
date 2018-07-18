---
title: ALTER DATABASE (database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 05/15/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 73ad135ab3cf54c96956be380bb50207895ab372
ms.sourcegitcommit: 02c889a1544b0859c8049827878d66b2301315f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225369"
---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Modifica un [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Modifica il nome di un database, l'edizione e l'obiettivo di servizio di un database, aggiunge un pool elastico e imposta le opzioni di database.  
  
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
  | EDITION = { 'basic' | 'standard' | 'premium' | 'GeneralPurpose' | 'BusinessCritical'} 
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
       | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' | 'GP_GEN4_24' |
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 'BC_GEN4_24' |
      | 'GP_GEN5_2' | 'GP_GEN5_4' | 'GP_GEN5_8' | 'GP_GEN5_16' | 'GP_GEN5_24' | 'GP_GEN5_32' | 'GP_GEN5_48' | 'GP_GEN5_80' |
      | 'BC_GEN5_2' | 'BC_GEN5_4' | 'BC_GEN5_8' | 'BC_GEN5_16' | 'BC_GEN5_24' | 'BC_GEN5_32' | 'BC_GEN5_48' | 'BC_GEN5_80' |
      }

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
  
<delayed_durability_option> ::=  DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
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
  
 Per una descrizione completa delle opzioni di impostazione, vedere [Opzioni &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) e [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="arguments"></a>Argomenti  

*database_name*  

Nome del database da modificare.  
  
CURRENT  

Specifica che il database corrente in uso deve essere modificato.  
  
MODIFY NAME **=***new_database_name*  

Rinomina il database con il nome specificato come *new_database_name*. Nell'esempio seguente il nome di un database `db1` viene modificato in `db2`:   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

MODIFY (EDITION **=** ['basic' | 'standard' | 'premium' |'GeneralPurpose' | 'BusinessCritical'])    

Modifica il livello di servizio del database. Il supporto di "premiumrs" è stato rimosso. In caso di domande, usare l'alias di posta elettronica seguente: premium-rs@microsoft.com.

Nell'esempio seguente l'edizione viene modificata in `premium`:
  
```  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

La modifica di EDITION ha esito negativo se la proprietà MAXSIZE per il database è impostata su un valore non compreso nell'intervallo valido supportato da questa edizione.  

MODIFY (MAXSIZE **=** [100 MB | 500 MB | 1 | 1024…4096] GB)  

Specifica le dimensioni massime del database. Le dimensioni massime devono essere conformi al set valido di valori per la proprietà EDITION del database. La modifica delle dimensioni massime del database può causare la modifica del valore di EDITION del database. Nella tabella seguente sono elencati i valori MAXSIZE supportati e i valori predefiniti (P) per i livelli del servizio di [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
**Modello basato su DTU**

|**MAXSIZE**|**Base**|**S0-S2**|**S3-S12**|**P1-P6**|**P11-P15**|  
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
|Da 1024 GB fino a 4096 GB con incrementi di 256 GB*|N/D|N/D|N/D|N/D|√|√|  
  
\* P11 e P15 consentono un valore massimo di MAXSIZE pari a 4 TB. Le dimensioni predefinite sono 1024 GB.  P11 e P15 possono usare fino a 4 TB di spazio di archiviazione incluso senza addebiti aggiuntivi. Nel livello Premium, MAXSIZE maggiore di 1 TB è attualmente disponibile nelle seguenti aree: Stati Uniti orientali 2, Stati Uniti occidentali, US Gov Virginia, Europa occidentale, Germania centrale, Asia sud-orientale, Giappone orientale, Australia orientale, Canada centrale e Canada orientale. Per altri dettagli relativi ai limiti delle risorse per il modello basato su DTU, vedere [DTU-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) (Limiti delle risorse basate su DTU).  

Il valore MAXSIZE per il modello basato su DTU, se specificato, deve essere un valore valido presente nella tabella precedente per il livello di servizio specificato.
 
**Modello basato su vCore**

**Livello di servizio Utilizzo generico: piattaforma di calcolo generazione 4**
|MAXSIZE|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|GP4_24|
|:--- | --: |--: |--: |--: |--: |--:|
|Dimensioni massime dei dati (GB)|1024|1024|1536|3072|4096|4096|

**Livello di servizio Utilizzo generico: piattaforma di calcolo generazione 5**
|MAXSIZE|GP_Gen5_2|GP_Gen5_4|GP_Gen5_8|GP_Gen5_16|GP_Gen5_24|GP_Gen5_32|GP_Gen5_48|GP_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Dimensioni massime dei dati (GB)|1024|1024|1536|3072|4096|4096|4096|4096|


**Livello di servizio Business critical: piattaforma di calcolo generazione 4**
|Livello di prestazioni|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|
|:--- | --: |--: |--: |--: |--: |--: |
|Dimensioni massime dei dati (GB)|1024|1024|1024|1024|1024|1024|

**Livello di servizio Business critical: piattaforma di calcolo generazione 5**
|MAXSIZE|BC_Gen5_2|BC_Gen5_4|BC_Gen5_8|BC_Gen5_16|BC_Gen5_24|BC_Gen5_32|BC_Gen5_48|BC_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Dimensioni massime dei dati (GB)|1024|1024|1024|1024|2048|4096|4096|4096|

Se non viene impostato alcun `MAXSIZE`valore quando viene usato il modello vCore, il valore predefinito è 32 GB. Per altri dettagli relativi ai limiti delle risorse per il modello basato su vCore, vedere [DTU-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) (Limiti delle risorse basate su vCore).
  
Le seguenti regole vengono applicate agli argomenti MAXSIZE ed EDITION:  
  
- Se il valore di EDITION è specificato e il valore di MAXSIZE viene omesso, viene utilizzato il valore predefinito dell'edizione. Ad esempio, se EDITION è impostato su Standard e MAXSIZE non è specificato, il valore di MAXSIZE viene automaticamente impostato su 500 MB.  
  
- Se né MAXSIZE né EDITION sono specificati, EDITION viene impostato su Standard (S0) e MAXSIZE viene impostato su 250 GB.  

MODIFY (SERVICE_OBJECTIVE = \<service-objective>)  

Specifica il livello di prestazioni. Nell'esempio seguente l'obiettivo di servizio di un database Premium viene modificato in `P6`:
 
```sql  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  

Specifica il livello di prestazioni. I valori disponibili per l'obiettivo di servizio sono:  `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`,    `GP_Gen5_8`,    `GP_Gen5_16`,   `GP_Gen5_24`,   `GP_Gen5_32`,   `GP_Gen5_48`,   `GP_Gen5_80`, `BC_Gen5_2`,  `BC_Gen5_4`,    `BC_Gen5_8`,    `BC_Gen5_16`,   `BC_Gen5_24`,   `BC_Gen5_32`,   `BC_Gen5_48`,   `BC_Gen5_80`.  

Per le descrizioni degli obiettivi di servizio e altre informazioni su dimensioni, edizioni e combinazioni di obiettivi di servizio, vedere [Azure SQL Database Service Tiers and Performance Levels](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) (Livelli di servizio e livelli di prestazioni del database SQL di Azure), [DTU-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) (Limiti delle risorse basate su DTU) e [vCore-based resource limits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) (Limiti delle risorse basate su vCore). Il supporto per gli obiettivi di servizio PRS è stato rimosso. In caso di domande, usare l'alias di posta elettronica seguente: premium-rs@microsoft.com. 
  
MODIFY (SERVICE_OBJECTIVE = ELASTIC\_POOL (name = \<elastic_pool_name>)  

Per aggiungere un database esistente a un pool elastico, impostare SERVICE_OBJECTIVE del database su ELASTIC_POOL e specificare il nome del pool elastico. È anche possibile usare questa opzione per modificare il database in un pool elastico all'interno dello stesso server. Per altre informazioni, vedere [Creare e gestire un pool elastico in un database SQL](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Per rimuovere un database da un pool elastico, usare ALTER DATABASE per impostare SERVICE_OBJECTIVE su un livello di prestazioni di un unico database.  

ADD SECONDARY ON SERVER \<partner_server_name>  

Crea un database secondario con replica geografica usando lo stesso nome in un server partner e trasformando il database locale in un database con replica geografica. Avvia la replica asincrona dei dati dal database primario nel nuovo database secondario. Se esiste già un database con lo stesso nome nel database secondario, il comando non riesce. Il comando viene eseguito nel database master sul server che ospita il database locale, il quale diventa il database primario.  
  
WITH ALLOW_CONNECTIONS { **ALL** | NO }  

Se non si specifica ALLOW_CONNECTION, il valore ALL viene impostato per impostazione predefinita. Se viene impostato ALL, il database è di sola lettura e consente a tutti gli account che hanno le autorizzazioni necessarie di connettersi.  
  
WITH SERVICE_OBJECTIVE {  `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`,    `GP_Gen5_8`,    `GP_Gen5_16`,   `GP_Gen5_24`,   `GP_Gen5_32`,   `GP_Gen5_48`,   `GP_Gen5_80`, `BC_Gen5_2`,  `BC_Gen5_4`,    `BC_Gen5_8`,    `BC_Gen5_16`,   `BC_Gen5_24`,   `BC_Gen5_32`,   `BC_Gen5_48`,   `BC_Gen5_80` }  

Se non si specifica SERVICE_OBJECTIVE, il database secondario viene creato allo stesso livello di servizio del database primario. Se si specifica SERVICE_OBJECTIVE, il database secondario viene creato al livello specificato. Questa opzione supporta la creazione di database secondari con replica geografica con livelli di servizio meno costosi. Il valore SERVICE_OBJECTIVE specificato deve rientrare nella stessa edizione dell'origine. Ad esempio, non è possibile specificare S0 se l'edizione è Premium.  
  
ELASTIC_POOL (name = \<elastic_pool_name>)  

Se non si specifica ELASTIC_POOL, il database secondario non viene creato in un pool elastico. Se si specifica ELASTIC_POOL, il database secondario viene creato nel pool specificato.  
  
> [!IMPORTANT]  
>  Chi esegue il comando ADD SECONDARY deve avere il ruolo DBManager nel server primario, db_owner membership nel database locale e DBManager nel server secondario.  
  
REMOVE SECONDARY ON SERVER  \<partner_server_name>  

Rimuove il database secondario con replica geografica nel server specificato. Il comando viene eseguito nel database master sul server che ospita il database primario.  
  
> [!IMPORTANT]  
>  Chi esegue il comando REMOVE SECONDARY deve avere il ruolo DBManager nel server primario.  
  
FAILOVER  

Alza di livello il database secondario nella relazione con replica geografica in cui il comando viene eseguito perché il database diventi primario e abbassa di livello il database corrente perché diventi il nuovo database secondario. Durante questo processo, la modalità di replica geografica passa temporaneamente dalla modalità asincrona alla modalità sincrona. Durante il processo di failover:  
  
1.  Il database primario non accetta più nuove transazioni.  
  
2.  Tutte le transazioni in sospeso vengono scaricate nel database secondario.  
  
3.  Il database secondario diventa il database primario e la replica geografica asincrona viene avviata con il database primario precedente e il nuovo database secondario.  
  
Questa sequenza impedisce la perdita di dati. I due database non sono disponibili generalmente per un periodo di tempo compreso tra 0 e 25 secondi, il tempo necessario per lo scambio dei ruoli. L'operazione totale non richiederà più di un minuto circa. Se il database primario non è disponibile quando viene eseguito questo comando, il comando ha esito negativo e genera un messaggio di errore indicando che il database primario non è disponibile. Se il processo di failover non viene completato e sembra bloccato, è possibile usare il comando per forzare il failover e accettare la perdita di dati. Se è necessario recuperare i dati persi, chiamare la metodologia DevOps (CSS).  
  
> [!IMPORTANT]  
>  Chi esegue il comando FAILOVER deve avere il ruolo DBManager sia nel server primario sia nel server secondario.  
  
FORCE_FAILOVER_ALLOW_DATA_LOSS  

Alza di livello il database secondario nella relazione con replica geografica in cui il comando viene eseguito perché il database diventi primario e abbassa di livello il database corrente perché diventi il nuovo database secondario. Usare questo comando solo quando il database primario corrente non è più disponibile. È progettato per essere usato solo in caso di ripristino di emergenza, quando la disponibilità di ripristino è critica e la perdita di dati è accettabile.  
  
Durante un failover forzato:  
  
1. Il database secondario specificato diventa immediatamente il database primario e inizia ad accettare nuove transazioni.  
  
2. Quando il database primario originale si riconnette al nuovo database primario, viene eseguito un backup incrementale nel database primario originale e il database primario originale diventa un nuovo database secondario.  
  
3. Per ripristinare i dati da questo backup incrementale nel database primario precedente, è necessario usare la metodologia DevOps/CSS.  
  
4. Se esistono altri database secondari, vengono riconfigurati automaticamente per diventare i database secondari del nuovo database primario. Questo processo è asincrono. Fino al suo completamento, è possibile assistere a un ritardo. Quando la riconfigurazione è completa, i database secondari continuano a essere database secondari del database primario precedente.  
  
> [!IMPORTANT]  
>  Chi esegue il comando FORCE_FAILOVER_ALLOW_DATA_LOSS deve avere il ruolo DBManager sia nel server primario sia nel server secondario.  
  
## <a name="remarks"></a>Remarks  

Per rimuovere un database usare [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
Per ridurre le dimensioni di un database, usare [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
L'istruzione ALTER DATABASE deve essere eseguita in modalità autocommit (modalità predefinita di gestione delle transazioni) e non è consentita in una transazione esplicita o implicita.  
  
La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni di manutenzione o riconfigurazione del database". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.  
  
La cache delle procedure viene inoltre scaricata negli scenari seguenti:  
  
- L'opzione AUTO_CLOSE di un database è impostata su ON. Se il database non viene utilizzato da alcuna connessione utente, neanche come riferimento, tramite l'attività in background viene effettuato il tentativo di chiusura e di arresto automatici del database.  
  
- Vengono eseguite diverse query su un database contenente opzioni predefinite. Successivamente, il database viene eliminato.  
  
- Viene ricompilato correttamente il log delle transazioni per un database.  
  
- Viene ripristinato un backup del database.  
  
- Viene scollegato un database.  
  
## <a name="viewing-database-information"></a>Visualizzazione delle informazioni sui database  

Per restituire informazioni su database, file e filegroup, è possibile usare viste del catalogo, funzioni di sistema e stored procedure di sistema.  
  
## <a name="permissions"></a>Autorizzazioni  

Solo l'account di accesso dell'entità a livello di server (creato dal processo di provisioning) o i membri del ruolo del database `dbmanager` possono modificare un database.  
  
> [!IMPORTANT]  
>  Il proprietario del database può modificare il database solo se è un membro del ruolo `dbmanager`.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Controllare le opzioni di edizione e modificarle:

```sql
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>B. Spostare un database in un pool elastico diverso  

Sposta un database esistente in un pool denominato pool1:  
  
```sql  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>C. Aggiungere un database secondario con replica geografica  

Crea un database secondario leggibile denominato db1 nel server `secondaryserver` di db1 nel server locale.  
  
```sql  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = ALL )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>D. Rimuovere un database secondario con replica geografica  
 
Rimuove il database secondario db1 nel server `secondaryserver`.  
  
```sql  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>E. Eseguire il failover di un database secondario con replica geografica  

Alza di livello un database secondario db1 nel server `secondaryserver` perché diventi il nuovo database primario quando viene eseguito nel server `secondaryserver`.  
  
```sql  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>Vedere anche
  
[CREATE DATABASE (Database SQL di Azure)](../../t-sql/statements/create-database-azure-sql-database.md)   
 [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Database di sistema.](../../relational-databases/databases/system-databases.md)  
  
  
