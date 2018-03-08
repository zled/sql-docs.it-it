---
title: CREATE DATABASE (Database SQL di Azure) | Microsoft Docs
ms.custom: 
ms.date: 02/13/2018
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVICE_OBJECTIVE
- SERVICE_OBJECTIVE_TSQL
- ELASTIC_POOL
- ELASTIC_POOL_TSQL
- EDITION
- EDITION_TSQL
- MAXSIZE
- MAXSIZE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVICE_OBJECTIVE
- ELASTIC_POOL
- EDITION SQL Database
- MAXSIZE SQL Database
ms.assetid: 22b167f7-ae86-490b-adb3-ec02ca1c1508
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c61660015eb2f613148ad58b72386e42eb797db9
ms.sourcegitcommit: aebbfe029badadfd18c46d5cd6456ea861a4e86d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="create-database-azure-sql-database"></a>CREATE DATABASE (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Crea un nuovo database.  
  
## <a name="syntax"></a>Sintassi  
  
``` 
  
CREATE DATABASE database_name [ COLLATE collation_name ]  
{  
   (<edition_options> [, ...n])   
}  

[ WITH CATALOG_COLLATION = { DATABASE_DEFAULT | SQL_Latin1_General_CP1_CI_AS }  ]
  
<edition_options> ::=   
{  

      MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }    
    | ( EDITION = {  'basic' | 'standard' | 'premium' }   
    | SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
            | { ELASTIC_POOL(name = <elastic_pool_name>) } }  ) 
}  

 [;]  
  

```  

```
To copy a database:  
CREATE DATABASE database_name  
    AS COPY OF [source_server_name.] source_database_name  
    [ ( SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |  
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11' | 'P15'  
            | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
    ]  
 [;] 
 
```  
  
## <a name="arguments"></a>Argomenti  
 In questo diagramma di sintassi vengono illustrati gli argomenti supportati nel [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] .  
  
 *database_name*  
 Nome del nuovo database. Questo nome deve essere univoco in SQL Server, che può ospitare sia database [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sia database [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Deve anche rispettare le regole [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per gli identificatori. Per altre informazioni, vedere [Identificatori](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
 *Collation_name*  
 Specifica le regole di confronto predefinite per il database. È possibile usare nomi di regole di confronto di Windows o SQL. Se non viene specificato, al database vengono assegnate le regole di confronto predefinite, ovvero SQL_Latin1_General_CP1_CI_AS.  
  
 Per altre informazioni sui nomi delle regole di confronto Windows e SQL, vedere [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
 *CATALOG_COLLATION*  
Specifica le regole di confronto predefinite per il catalogo di metadati. *DATABASE_DEFAULT* specifica che il catalogo di metadati usato per le visualizzazioni e le tabelle di sistema viene sottoposto a confronto per la corrispondenza con le regole di confronto predefinite per il database.  Questo è il comportamento disponibile in SQL Server. 

*SQL_Latin1_General_CP1_CI_AS* specifica che il catalogo di metadati usato per le visualizzazioni e le tabelle di sistema viene sottoposto a confronto con regole di confronto fisse SQL_Latin1_General_CP1_CI_AS.  Questa è l'impostazione predefinita del database SQL di Azure se non è specificata un'altra opzione.

 *EDITION*  
 Specifica il livello del servizio del database. I valori disponibili sono "basic", "standard" e "premium". Il supporto di "premiumrs" è stato rimosso. In caso di domande, usare l'alias di posta elettronica seguente: premium-rs@microsoft.com.
  
 Quando si specifica EDITION ma non MAXSIZE, MAXSIZE viene impostato sulle dimensioni minime supportate dall'edizione.  
  
 *MAXSIZE*  
 Specifica le dimensioni massime del database. MAXSIZE deve essere valido per il livello del servizio specificato in EDITION. Nella tabella seguente sono elencati i valori MAXSIZE supportati e i valori predefiniti (P) per i livelli del servizio.  
  
|**MAXSIZE**|**Base**|**S0-S2**|**S3-S12**|**P1-P6**| **P11-P15** 
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
|300 GB|N/D|N/D|√|√|√|  
|400 GB|N/D|N/D|√|√|√|
|500 GB|N/D|N/D|√|√ (P)|√|
|750 GB|N/D|N/D|√|√|√|
|1024 GB|N/D|N/D|√|√|√ (P)|
|Da 1024 GB fino a 4096 GB con incrementi di 256 GB* |N/D|N/D|N/D|N/D|√|√|  
  
 \* P11 e P15 consentono un valore massimo di MAXSIZE pari a 4 TB. Le dimensioni predefinite sono 1024 GB.  P11 e P15 possono usare fino a 4 TB di spazio di archiviazione incluso senza addebiti aggiuntivi. Nel livello Premium, MAXSIZE maggiore di 1 TB è attualmente disponibile nelle seguenti aree: Stati Uniti orientali 2, Stati Uniti occidentali, US Gov Virginia, Europa occidentale, Germania centrale, Asia sud-orientale, Giappone orientale, Australia orientale, Canada centrale e Canada orientale. Per le limitazioni correnti, vedere [Single databases](https://docs.microsoft.com/azure/sql-database-single-database-resources) (Database singoli).  
  
 Le seguenti regole vengono applicate agli argomenti MAXSIZE ed EDITION:  
  
-   Il valore MAXSIZE, se specificato, deve essere un valore valido presente nella precedente tabella.  
  
-   Se il valore di EDITION è specificato e il valore di MAXSIZE viene omesso, viene utilizzato il valore predefinito dell'edizione. Se ad esempio EDITION è impostato su Standard e MAXSIZE non è specificato, il valore di MAXSIZE viene automaticamente impostato su 250 MB.  
  
-   Se né MAXSIZE né EDITION sono specificati, EDITION viene impostato su Standard (S0) e MAXSIZE viene impostato su 250 GB.  
  
 SERVICE_OBJECTIVE  
 Specifica il livello di prestazioni. Per descrizioni degli obiettivi di servizio e altre informazioni su dimensioni, edizioni e combinazioni di obiettivi di servizio, vedere [Livelli di servizio e livelli di prestazioni del database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) e [SQL Database resource limits](https://azure.microsoft.com/documentation/articles/sql-database-resource-limits) (Limiti di risorse per il database SQL). Se SERVICE_OBJECTIVE non è supportato da EDITION, sarà visualizzato un errore.  
  
 ELASTIC_POOL (name = \<nome_pool_elastico>) Per creare un nuovo database in un pool di database elastico, impostare SERVICE_OBJECTIVE del database su ELASTIC_POOL e specificare il nome del pool. Per altre informazioni, vedere [Create and manage a SQL Database elastic database pool (preview)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/) (Creare e gestire un pool di database elastico nel database SQL - Anteprima).  
  
 *AS COPY OF [nome_server_di_origine.]nome_database_di_origine*  
 Per la copia di un database nello stesso server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o in un server diverso.  
  
 *nome_server_di_origine*  
 Nome del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in cui si trova il database di origine. Questo parametro è facoltativo se il database di origine e il database di destinazione devono trovarsi nello stesso server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Nota: l'argomento `AS COPY OF` non supporta nomi di dominio univoci completi. In altre parole, se il nome di dominio completo del server è `serverName.database.windows.net`, usare solo `serverName` durante la copia del database.  
  
 *nome_database_di_origine*  
 Nome del database di cui eseguire la copia.  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] non supporta gli argomenti e le opzioni seguenti quando si usa l'istruzione `CREATE DATABASE`:  
  
-   Parametri correlati alla posizione fisica del file, ad esempio \<filespec> e \<filegroup>  
  
-   Opzioni di accesso esterno, ad esempio DB_CHAINING e TRUSTWORTHY  
  
-   Collegamento di un database  
  
-   Opzioni di Service Broker, ad esempio ENABLE_BROKER, NEW_BROKER e ERROR_BROKER_CONVERSATIONS  
  
-   Snapshot del database  
  
 Per altre informazioni sugli argomenti e sull'istruzione `CREATE DATABASE`, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 I database nel [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] presentano varie impostazioni predefinite impostate alla creazione del database. Per altre informazioni su queste impostazioni predefinite, vedere l'elenco di valori in [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
 MAXSIZE consente di limitare le dimensioni del database. Se le dimensioni del database raggiungono MAXSIZE, viene visualizzato il codice di errore 40544. In questo caso, non è possibile inserire o aggiornare dati, né creare nuovi oggetti quali tabelle, stored procedure, viste e funzioni. È tuttavia ancora possibile leggere ed eliminare dati, troncare tabelle, eliminare tabelle e indici e ricompilare indici. È quindi possibile aggiornare MAXSIZE a un valore maggiore delle dimensioni correnti del database o eliminare alcuni dati per liberare spazio di archiviazione. Potrebbe verificarsi un ritardo di quindici minuti prima di poter inserire nuovi dati.  
  
> [!IMPORTANT]  
>  L'istruzione `CREATE DATABASE` deve essere l'unica istruzione in un batch [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
 Per modificare le dimensioni o i valori degli obiettivi di servizio in un secondo momento, usare [ALTER DATABASE &#40;Database SQL di Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md).  

L'argomento CATALOG_COLLATION è disponibile solo durante la creazione del database. 
  
## <a name="database-copies"></a>Copie di database  
 La copia di un database tramite l'istruzione `CREATE DATABASE` è un'operazione asincrona. Pertanto, una connessione al server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] non è necessaria per la durata totale del processo di copia. L'istruzione `CREATE DATABASE` restituisce il controllo all'utente dopo la creazione della voce in sys.databases e prima che l'operazione di copia del database venga completata. In altre parole, l'istruzione `CREATE DATABASE` ha esito positivo quando la copia del database è ancora in corso.  
  
-   Monitoraggio del processo di copia in un server [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]: eseguire query sulle colonne `percentage_complete` o `replication_state_desc` in [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) o sulla colonna `state` nella visualizzazione **sys.databases**. È possibile usare anche la visualizzazione [sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) perché restituisce lo stato delle operazioni del database, inclusa la copia del database.  
  
 Al termine del processo di copia, il database di destinazione è transazionalmente coerente con il database di origine.  
  
 La sintassi e le regole semantiche seguenti si applicano all'utilizzo dell'argomento `AS COPY OF`:  
  
-   Il nome del server di origine e il nome del server per la destinazione della copia potrebbe essere uguale o diverso. Se corrispondono, questo parametro è facoltativo e il contesto del server della sessione corrente viene usato per impostazione predefinita.  
  
-   I nomi dei database di origine e di destinazione devono essere specificati, univoci e conformi alle regole di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per gli identificatori. Per altre informazioni, vedere [Identificatori](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
-   L'istruzione `CREATE DATABASE` deve essere eseguita nel contesto del database master del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in cui il nuovo database verrà creato.  
  
-   Al termine della copia, il database di destinazione deve essere gestito come database indipendente. È possibile eseguire le istruzioni `ALTER DATABASE` e `DROP DATABASE` per il nuovo database indipendentemente dal database di origine. È inoltre possibile copiare il nuovo database in un altro nuovo database.  
  
-   Il database di origine continuerà a essere accessibile durante la copia del database.  
  
 Per altre informazioni, vedere [Create a copy of an Azure SQL database using Transact-SQL](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/) (Creare una copia di un database SQL di Azure mediante Transact-SQL).  
  
## <a name="permissions"></a>Autorizzazioni  
 Per creare un database, l'account di accesso deve essere uno dei seguenti:  
  
-   Account di accesso principale di livello server  
  
-   Account amministratore di Azure AD per il server SQL di Azure  
  
-   Un account di accesso membro del ruolo del database `dbmanager`  
  
 **Requisiti aggiuntivi per l'uso della sintassi `CREATE DATABASE ... AS COPY OF`**: l'account di accesso che esegue l'istruzione sul server locale deve anche essere almeno un account `db_owner` nel server di origine. Se l'account di accesso è basato sull'autenticazione  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'account di accesso che esegue l'istruzione nel server locale deve disporre di un account di accesso corrispondente nel server [!INCLUDE[ssSDS](../../includes/sssds-md.md)] di origine, con nome e password identici.  
  
## <a name="examples"></a>Esempi  
Per un'esercitazione introduttiva che spiega come connettersi a un database SQL di Azure mediante SQL Server Management Studio, vedere [Azure SQL Database: Use SQL Server Management Studio to connect and query data](/azure/sql-database/sql-database-connect-query-ssms) (Database SQL di Azure: usare SQL Server Management Studio per la connessione e le query sui dati).  
  
### <a name="simple-example"></a>Esempio semplice  
 Esempio semplice per la creazione di un database.  
  
```sql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>Esempio semplice con Edition  
 Esempio semplice per la creazione di un database standard.  
  
```sql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>Esempio con opzioni aggiuntive  
 Esempio che usa varie opzioni.  
  
```sql  
CREATE DATABASE hito   
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS   
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>Creazione di una copia  
 Esempio di creazione di una copia di un database.  
  
```sql  
CREATE DATABASE escuela   
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>Creazione di un database in un pool elastico  
 Crea un nuovo database nel pool denominato S3M100:  
  
```sql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>Creazione di una copia di un database in un altro server  
 L'esempio seguente crea una copia del database db_original denominata db_copy nel livello di prestazioni P2 per un singolo database.  Questo vale indipendentemente dal fatto che db_original si trovi in un pool elastico o in un livello di prestazioni per un singolo database.  
  
```sql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 L'esempio seguente crea una copia del database db_original denominata db_copy in un pool elastico con nome ep1.  Questo vale indipendentemente dal fatto che db_original si trovi in un pool elastico o in un livello di prestazioni per un singolo database.  Se db_original si trova in un pool elastico con un nome diverso, db_copy viene comunque creato in ep1.  
  
```sql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original   
    (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>Creare un database con il valore di regole di confronto del catalogo specificato

L'esempio seguente imposta le regole di confronto del catalogo su DATABASE_DEFAULT durante la creazione del database. In questo modo le regole di confronto del catalogo vengono impostate in modo da corrispondere alle regole di confronto del database.

```sql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
      WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>Vedere anche  

-  [sys.dm_database_copies &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

-   [ALTER DATABASE &#40;Database SQL di Azure&#41;](alter-database-azure-sql-database.md)   
    
  

