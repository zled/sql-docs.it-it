---
title: CREATE DATABASE (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 08/28/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
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
dev_langs: TSQL
helpviewer_keywords:
- SERVICE_OBJECTIVE
- ELASTIC_POOL
- EDITION SQL Database
- MAXSIZE SQL Database
ms.assetid: 22b167f7-ae86-490b-adb3-ec02ca1c1508
caps.latest.revision: "62"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64686457f1f5f4057635eb4a4c9a0f3d4030d8fa
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
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
    | ( EDITION = {  'basic' | 'standard' | 'premium' | 'premiumrs'}   
    | SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
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
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
            | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
    ]  
 [;] 
 
```  
  
## <a name="arguments"></a>Argomenti  
 In questo diagramma di sintassi vengono illustrati gli argomenti supportati nel [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] .  
  
 *database_name*  
 Nome del nuovo database. Questo nome deve essere univoco in SQL server, che possono ospitare entrambi [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] database e [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] database e rispettare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] regole per gli identificatori. Per ulteriori informazioni, vedere [identificatori](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
 *Collation_name*  
 Specifica le regole di confronto predefinite per il database. È possibile usare nomi di regole di confronto di Windows o SQL. Se non viene specificato, al database vengono assegnate le regole di confronto predefinite, ovvero SQL_Latin1_General_CP1_CI_AS.  
  
 Per ulteriori informazioni sui nomi delle regole di confronto Windows e SQL, [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
 *CATALOG_COLLATION*  
Specifica le regole di confronto predefinito per il catalogo dei metadati. *DATABASE_DEFAULT* specifica che il catalogo di metadati utilizzato per le viste di sistema e le tabelle di sistema essere confrontati in base a regole di confronto predefinite per il database.  Questo è il comportamento disponibili in SQL Server. 

*SQL_Latin1_General_CP1_CI_AS* specifica che il catalogo di metadati utilizzati per tabelle e viste di sistema fascicolate a regole di confronto SQL_Latin1_General_CP1_CI_AS fisso.  Se non viene specificato, questo è l'impostazione predefinita in Database SQL di Azure.

 *EDIZIONE*  
 Specifica il livello del servizio del database. I valori disponibili sono: 'basic', 'standard', 'premium' e 'premiumrs'.  
  
 Quando si specifica l'edizione ma MAXSIZE non è specificato, MAXSIZE è impostato per le dimensioni più limitate supportate dall'edizione.  
  
 *MAXSIZE*  
 Specifica le dimensioni massime del database. MAXSIZE deve essere valido per il livello del servizio specificato in EDITION. Nella tabella seguente sono elencati i valori MAXSIZE supportati e i valori predefiniti (P) per i livelli del servizio.  
  
|**MAXSIZE**|**Basic**|**S0 S2**|**S3 S12**|**P1 P6 e PRS1 PRS6**| **P11 P15** 
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
|Da 1024 GB fino a 4096 GB con incrementi di 256 GB * |N/D|N/D|N/D|N/D|√|√|  
  
 \*P11 e P15 consentono MAXSIZE fino a 4 TB con 1024 GB da quelle predefinite.  P11 e P15 possono utilizzare fino a 4 TB di spazio di archiviazione incluse senza costi aggiuntivi. Nel livello Premium, MAXSIZE maggiore di 1 TB è attualmente disponibile nelle seguenti aree: ci East2, Stati Uniti occidentali, ci Gov Virginia, Europa occidentale, Germania centrale, Sud Asia sudorientale, Giappone orientale, Australia orientale, Canada centrale e Canada orientale. Per le limitazioni attuali, vedere [singolo database](https://docs.microsoft.com/azure/sql-database-single-database-resources).  
  
 Le seguenti regole vengono applicate agli argomenti MAXSIZE ed EDITION:  
  
-   Il valore MAXSIZE, se specificato, deve essere un valore valido presente nella precedente tabella.  
  
-   Se il valore di EDITION è specificato e il valore di MAXSIZE viene omesso, viene utilizzato il valore predefinito dell'edizione. Ad esempio, se EDITION è impostato su Standard e MAXSIZE non è specificato, quindi il valore di MAXSIZE viene automaticamente impostato a 250 MB.  
  
-   Se né MAXSIZE né EDITION vengono specificati, EDITION viene impostato su Standard (S0) e MAXSIZE viene impostato su 250 GB.  
  
 SERVICE_OBJECTIVE  
 Specifica il livello di prestazioni. Per descrizioni degli obiettivi di servizio e altre informazioni sulle dimensioni, edizioni e combinazioni di obiettivi di servizio, vedere [livelli di servizio di Database SQL Azure e i livelli di prestazioni](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) e [risorsa del Database SQL limiti](https://azure.microsoft.com/documentation/articles/sql-database-resource-limits). Se SERVICE_OBJECTIVE non è supportato da EDITION, sarà visualizzato un errore.  
  
 ELASTIC_POOL (nome = \<elastic_pool_name >) per creare un nuovo database in un pool di database elastici, impostare ELASTIC_POOL di SERVICE_OBJECTIVE del database e specificare il nome del pool. Per ulteriori informazioni, vedere [creare e gestire un pool di database elastico del Database SQL (anteprima)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/).  
  
 *COME copia di [source_server_name]. source_database_name*  
 Per la copia di un database nello stesso server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o in un server diverso.  
  
 *source_server_name*  
 Nome del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in cui si trova il database di origine. Questo parametro è facoltativo se il database di origine e il database di destinazione devono trovarsi nello stesso server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Nota: l'argomento `AS COPY OF` non supporta nomi di dominio univoci completi. In altre parole, se il nome di dominio completo del server è `serverName.database.windows.net`, usare solo `serverName` durante la copia del database.  
  
 *source_database_name*  
 Nome del database di cui eseguire la copia.  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]non supporta gli argomenti e le opzioni seguenti quando si utilizza il `CREATE DATABASE` istruzione:  
  
-   Parametri relativi alla posizione fisica del file, ad esempio \<filespec > e \<filegroup >  
  
-   Opzioni di accesso esterno, ad esempio DB_CHAINING e TRUSTWORTHY  
  
-   Collegamento di un database  
  
-   Opzioni di Service Broker, ad esempio ENABLE_BROKER, NEW_BROKER e ERROR_BROKER_CONVERSATIONS  
  
-   Snapshot del database  
  
 Per ulteriori informazioni sugli argomenti e `CREATE DATABASE` istruzione, vedere [CREATE DATABASE &#40; SQL Server Transact-SQL &#41; ](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 I database nel [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] presentano varie impostazioni predefinite impostate alla creazione del database. Per ulteriori informazioni su queste impostazioni predefinite, vedere l'elenco di valori in [DATABASEPROPERTYEX &#40; Transact-SQL &#41; ](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
 MAXSIZE consente di limitare le dimensioni del database. Se le dimensioni del database raggiungono il valore MAXSIZE, verrà visualizzato il codice di errore 40544. In questo caso, non è possibile inserire o aggiornare dati, né creare nuovi oggetti quali tabelle, stored procedure, viste e funzioni. È tuttavia ancora possibile leggere ed eliminare dati, troncare tabelle, eliminare tabelle e indici e ricompilare indici. È quindi possibile aggiornare MAXSIZE a un valore maggiore delle dimensioni correnti del database o eliminare alcuni dati per liberare spazio di archiviazione. Potrebbe verificarsi un ritardo di quindici minuti prima di poter inserire nuovi dati.  
  
> [!IMPORTANT]  
>  L'istruzione `CREATE DATABASE` deve essere l'unica istruzione in un batch [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
 Per modificare le dimensioni, l'edizione o valori obiettivo del servizio in un secondo momento, utilizzare [ALTER DATABASE &#40; Database SQL di Azure &#41; ](../../t-sql/statements/alter-database-azure-sql-database.md).  

L'argomento CATALOG_COLLATION è disponibile solo durante la creazione del database. 
  
## <a name="database-copies"></a>Copie di database  
 Copia di un database utilizzando il `CREATE DATABASE` istruzione è un'operazione asincrona. Pertanto, una connessione al server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] non è necessaria per la durata totale del processo di copia. Il `CREATE DATABASE` istruzione restituisce il controllo utente dopo la creazione della voce in sys. Databases ma prima della copia del database è stata completata l'operazione. In altre parole, l'istruzione `CREATE DATABASE` ha esito positivo quando la copia del database è ancora in corso.  
  
-   Il monitoraggio del processo di copia su un [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] server: Query il `percentage_complete` o `replication_state_desc` colonne il [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) o `state` colonna il **Sys. Databases** Consente di visualizzare. Il [Sys.dm operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) vista può essere utilizzata anche come restituisce lo stato delle operazioni di database, tra cui copia del database.  
  
 Al termine del processo di copia, il database di destinazione è transazionalmente coerente con il database di origine.  
  
 La sintassi e le regole semantiche seguenti si applicano all'utilizzo dell'argomento `AS COPY OF`:  
  
-   Il nome del server di origine e il nome del server per la destinazione della copia potrebbe essere uguale o diverso. Se sono uguali, questo parametro è facoltativo e il contesto server della sessione corrente viene utilizzato per impostazione predefinita.  
  
-   I nomi dei database di origine e di destinazione devono essere specificati, univoci e conformi alle regole di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per gli identificatori. Per ulteriori informazioni, vedere [identificatori](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
-   L'istruzione `CREATE DATABASE` deve essere eseguita nel contesto del database master del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in cui il nuovo database verrà creato.  
  
-   Al termine della copia, il database di destinazione deve essere gestito come database indipendente. È possibile eseguire le istruzioni `ALTER DATABASE` e `DROP DATABASE` per il nuovo database indipendentemente dal database di origine. È inoltre possibile copiare il nuovo database in un altro nuovo database.  
  
-   Il database di origine continuerà a essere accessibile durante la copia del database.  
  
 Per ulteriori informazioni, vedere [creare una copia di un database SQL di Azure mediante Transact-SQL](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/).  
  
## <a name="permissions"></a>Permissions  
 Per creare un account di accesso di un database deve essere uno dei valori seguenti:  
  
-   L'account di accesso a livello di server principale  
  
-   L'amministratore di Azure AD per il Server locale di SQL Azure  
  
-   Un account di accesso è membro il `dbmanager` ruolo del database  
  
 **Requisiti aggiuntivi per l'utilizzo di `CREATE DATABASE ... AS COPY OF` sintassi:** account di accesso, l'esecuzione dell'istruzione nel server locale deve essere almeno di `db_owner` nel server di origine. Se l'account di accesso è basato su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione, l'account di accesso l'esecuzione dell'istruzione nel server locale deve disporre di un account di accesso corrispondente nell'origine [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server, con un nome identico e una password.  
  
## <a name="examples"></a>Esempi  
Per un'esercitazione introduttiva che mostra come connettersi a un database di SQL Azure mediante SQL Server Management Studio, vedere [Database SQL di Azure: utilizzare SQL Server Management Studio per connettersi ed eseguire query sui dati](/azure/sql-database/sql-database-connect-query-ssms).  
  
### <a name="simple-example"></a>Esempio semplice  
 Un esempio semplice per la creazione di un database.  
  
```tsql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>Semplice esempio con l'edizione  
 Un esempio semplice per la creazione di un database standard.  
  
```tsql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>Esempio con opzioni aggiuntive  
 Un esempio di utilizzo più opzioni.  
  
```tsql  
CREATE DATABASE hito   
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS   
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>Creazione di una copia  
 Un esempio di creazione di una copia di un database.  
  
```tsql  
CREATE DATABASE escuela   
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>Creazione di un Database in un Pool elastico  
 Crea nuovo database nel pool denominato S3M100:  
  
```tsql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>Creazione di una copia di un Database in un altro Server  
 Nell'esempio seguente crea una copia del database db_original, denominato db_copy nel livello di prestazioni P2 per un singolo database.  Questo vale indipendentemente dal fatto che db_original un livello di prestazioni per un singolo database o di un pool elastico.  
  
```tsql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 Nell'esempio seguente crea una copia del database db_original, denominato db_copy in un pool elastico denominato uscita ep1.  Questo vale indipendentemente dal fatto che db_original un livello di prestazioni per un singolo database o di un pool elastico.  Se db_original si trova in un pool elastico con un nome diverso, db_copy viene comunque creato in uscita ep1.  
  
```tsql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original   
    (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>Creare database con il valore di regole di confronto del catalogo specificato

Nell'esempio seguente imposta le regole di confronto del catalogo DATABASE_DEFAULT durante la creazione di database, che imposta le regole di confronto del catalogo deve corrispondere alle regole di confronto del database.

```tsql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
      WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>Vedere anche  

-  [Sys.dm database_copies &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

-   [ALTER DATABASE &#40; Database SQL di Azure &#41;](alter-database-azure-sql-database.md)   
    
  

