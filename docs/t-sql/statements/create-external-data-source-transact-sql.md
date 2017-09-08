---
title: CREARE l'origine dati esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL DATA SOURCE
- CREATE_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, data source
- PolyBase, create data source
ms.assetid: 75d8a220-0f4d-4d91-8ba4-9d852b945509
caps.latest.revision: 58
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c2a0a43aefe59bc11f16445b5ee0c781179a33fa
ms.openlocfilehash: 477d2f682da2c91ba8e4bfd42186c4b1b9735f85
ms.contentlocale: it-it
ms.lasthandoff: 09/07/2017

---
# <a name="create-external-data-source-transact-sql"></a>CREARE l'origine dati esterna (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Crea un'origine dati esterna per PolyBase, query di Database elastico o archiviazione Blob di Azure. A seconda dello scenario, la sintassi è notevolmente diverso. Un'origine dati creata per PolyBase non può essere utilizzata per le query di Database elastico.  Analogamente, un'origine dati creata per le query di Database elastico non può essere utilizzata per PolyBase e così via. 
  
> [!NOTE]  
>  PolyBase è supportata solo in SQL Server 2016, Azure SQL Data Warehouse e Parallel Data Warehouse. Le query di Database elastiche sono supportate solo in Database SQL di Azure v12 o versioni successive.  
  
 Per gli scenari di PolyBase, l'origine dati esterna è un sistema di File Hadoop (HDFS), un contenitore di blob di archiviazione di Azure o archivio Azure Data Lake. Per altre informazioni, vedere [Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)(Introduzione a PolyBase).  
  
 Per gli scenari di query di Database elastici, l'origine esterna è un gestore mappe partizioni (nel Database di SQL Azure) o un database remoto (nel Database di SQL Azure).  Utilizzare [sp_execute_remote &#40; Database SQL di Azure &#41; ](../../relational-databases/system-stored-procedures/sp-execute-remote-azure-sql-database.md) dopo la creazione di un'origine dati esterna. Per ulteriori informazioni, vedere [query di Database elastico](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  

  Origine dei dati esterni di archiviazione Blob di Azure supporta `BULK INSERT` e `OPENROWSET` sintassi ed è diverso rispetto all'archiviazione Blob di Azure per PolyBase.
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- PolyBase only:  Hadoop cluster as data source   
-- (on SQL Server 2016)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,
        LOCATION = 'hdfs://NameNode_URI[:port]'  
        [, RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI[:port]' ]  
        [, CREDENTIAL = credential_name ]
    )
[;]  
  
-- PolyBase only: Azure Storage Blob as data source   
-- (on SQL Server 2016 and Azure SQL Data Warehouse)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,  
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
[;]

-- PolyBase only: Azure Data Lake Store
-- (on Azure SQL Data Warehouse)
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (
    TYPE = HADOOP,
    LOCATION = 'adl://<AzureDataLake account_name>.azuredatalake.net',
    CREDENTIAL = AzureStorageCredential
);

-- PolyBase only: Hadoop cluster as data source
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP, 
        LOCATION = 'hdfs://NameNode_URI[:port]'
        [, JOB_TRACKER_LOCATION = 'JobTracker_URI[:port]' ]
    )
[;]

-- PolyBase only: Azure Storage Blob as data source 
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP,
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
    )
[;]
  
-- Elastic Database query only: a shard map manager as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = SHARD_MAP_MANAGER,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '\<ElasticDatabase_ShardMapManagerDb'>,  
        CREDENTIAL = <ElasticDBQueryCred>,  
        SHARD_MAP_NAME = '<ShardMapName>'  
    )  
[;]  
  
-- Elastic Database query only: a remote database on Azure SQL Database as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = RDBMS,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '<Remote_Database_Name>',  
        CREDENTIAL = <SQL_Credential>  
    )  
[;]  

-- Bulk operations only: Azure Storage Blob as data source   
-- (on SQL Server 2017 or later, and Azure SQL Database).
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'https://storage_account_name.blob.core.windows.net/container_name'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Argomenti  
 *data_source_name* specifica il nome definito dall'utente per l'origine dati. Il nome deve essere univoco all'interno del database in SQL Server, Database SQL di Azure e Azure SQL Data Warehouse. Il nome deve essere univoco all'interno del server in Parallel Data Warehouse.
  
 TIPO = [HADOOP | SHARD_MAP_MANAGER | RDBMS | BLOB_STORAGE]  
 Specifica il tipo di origine dati. Usare HADOOP quando l'origine dati esterna è Hadoop o blob di archiviazione di Azure per Hadoop. Utilizzare SHARD_MAP_MANAGER durante la creazione di un'origine dati esterna per la query di Database elastico per il partizionamento orizzontale nel Database SQL Azure. Per le query tra database con query di Database elastico sul Database SQL di Azure, usare il sistema RDBMS con origini dati esterne.  Utilizzare BLOB_STORAGE durante l'esecuzione di operazioni bulk utilizzando [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) o [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) con [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
  
PERCORSO = \<location_path > **HADOOP**    
Per HADOOP, specifica l'URI Uniform Resource Indicator () per un cluster Hadoop.  
`LOCATION = 'hdfs:\/\/*NameNode\_URI*\[:*port*\]'`  
NameNode_URI: Il nome del computer o l'indirizzo IP del cluster Hadoop Namenode.  
porta: porta il Namenode IPC. Viene indicato dal parametro di configurazione fs.default.name in Hadoop. Se il valore non è specificato, 8020 verrà utilizzato per impostazione predefinita.  
Esempio: `LOCATION = 'hdfs://10.10.10.10:8020'`

Per l'archiviazione blob di Azure con Hadoop, specifica l'URI per la connessione di archiviazione blob di Azure.  
`LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'`  
wasb [s]: Specifica il protocollo per l'archiviazione blob di Azure. [S] è facoltativo e specifica una connessione SSL protetta. dati inviati da SQL Server vengono crittografati in modo sicuro tramite il protocollo SSL. Si consiglia di utilizzare 'wasbs' anziché 'wasb'. Si noti che il percorso può utilizzare asv [s] anziché wasb [s]. La sintassi asv [s] è deprecata e verrà rimossa in una versione futura.  
contenitore: Specifica il nome del contenitore di archiviazione blob di Azure. Per specificare il contenitore radice dell'account di archiviazione di un dominio, utilizzare il nome di dominio anziché il nome del contenitore. I contenitori di radice sono di sola lettura, in modo non è possibile riscrivere al contenitore di dati.  
account_name: il nome di dominio completo (FQDN) dell'account di archiviazione Azure.  
Esempio: `LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'`

Per archivio Azure Data Lake percorso Specifica l'URI per la connessione per l'archivio Azure Data Lake.



**SHARD_MAP_MANAGER**   
 Per SHARD_MAP_MANAGER, specifica il nome logico di server che ospita il gestore mappe partizioni nel Database di SQL Azure o un database di SQL Server in una macchina virtuale di Azure.
 
 ```
 CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH
  (TYPE = SHARD_MAP_MANAGER,
  LOCATION = '<server_name>.database.windows.net',
  DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
  CREDENTIAL = ElasticDBQueryCred,
  SHARD_MAP_NAME = 'CustomerIDShardMap'
) ;
```

Per un'esercitazione dettagliata, vedere [introduzione elastica query per il partizionamento orizzontale (partizionamento orizzontale)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/).
  
**RDBMS**   
Per RDBMS, specifica il nome del server logico del database remoto nel Database di SQL Azure.  

```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';  
  
CREATE DATABASE SCOPED CREDENTIAL SQL_Credential    
WITH IDENTITY = '<username>',  
SECRET = '<password>';  
  
CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH   
    (TYPE = RDBMS,   
    LOCATION = '<server_name>.database.windows.net',   
    DATABASE_NAME = 'Customers',   
    CREDENTIAL = SQL_Credential   
) ;   
```  
  
Per un'esercitazione dettagliata su RDBMS, vedere [Guida introduttiva a query tra database (partizionamento verticale)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/).  

**BLOB_STORAGE**   
Per le operazioni bulk, solo `LOCATION` deve essere valido l'URL di archiviazione Blob di Azure e contenitore. Non inserire  **/** , nome del file o condiviso i parametri di firma di accesso alla fine del `LOCATION` URL.   
La credenziale utilizzata, deve essere creata usando `SHARED ACCESS SIGNATURE` come identità. Per altre informazioni sulle firme di accesso condiviso, vedere [Uso delle firme di accesso condiviso](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1). Per un esempio di accesso all'archiviazione blob, vedere l'esempio F di [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md). 

  
 RESOURCE_MANAGER_LOCATION = '*ResourceManager_URI*[:*porta*]'  
 Specifica il percorso di gestione risorse di Hadoop. Quando specificato, query optimizer può decidere in base al costo di pre-elaborare i dati di una query di PolyBase con funzionalità di calcolo di Hadoop MapReduce. La distribuzione del predicato di chiamata, questo può ridurre notevolmente il volume di dati trasferiti tra Hadoop e SQL e pertanto migliorare le prestazioni delle query.  
  
 Quando non viene specificato, l'inserimento di calcolo in Hadoop è disabilitata per le query PolyBase.  
 
Se la porta non è specificata, il valore predefinito è determinato mediante l'impostazione corrente per la configurazione di 'hadoop connectivity'.

|Connettività Hadoop|Porta di gestione risorse predefinita|
|-------------------|-----------------------------|
|1|50300|
|2|50300|
|3|8021|
|4|8032|
|5|8050|
|6|8032|
|7|8050|

Per un elenco completo di distribuzioni di Hadoop e le versioni supportate da ogni valore di connettività, vedere [configurazione della connettività di PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).
  
> [!IMPORTANT]  
>  Il valore RESOURCE_MANAGER_LOCATION è una stringa e non viene convalidato quando si crea l'origine dati esterna. Immettere un valore non corretto possono causare ritardi futuri quando il percorso di accesso.  
  
 Esempi di Hadoop:  
  
-   Hortonworks HDP 2.0, 2.1, 2.2. 2.3 su Windows:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
-   Hortonworks HDP 1.3 su Windows:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Hortonworks HDP 2.0, 2.1, 2.2 e 2.3 su Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8050'  
    ```  
  
-   Hortonworks HDP 1.3 su Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Cloudera 4.3 su Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8021'  
    ```  
  
-   Cloudera 5.1 5.11 su Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
 CREDENZIALE = *credential_name*  
 Specifica una credenziale con ambito database per l'autenticazione per l'origine dati esterna. Per un esempio, vedere [C. creazione di un'origine dati esterna di archiviazione blob di Azure](../../t-sql/statements/create-external-data-source-transact-sql.md#credential). Per creare una credenziale, vedere [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md). Si noti che le CREDENZIALI non sono necessaria per i set di dati pubblici che consente l'accesso anonimo. 
  
 DATABASE_NAME = *'QueryDatabaseName'*  
 Il nome del database che funziona come il gestore mappe partizioni (per SHARD_MAP_MANAGER) o il database remoto (per sistema RDBMS).  
  
 SHARD_MAP_NAME = *'ShardMapName'*  
 Per SHARD_MAP_MANAGER. Il nome della mappa partizioni. Per ulteriori informazioni sulla creazione di una mappa partizioni, vedere [Guida introduttiva a query di Database elastico](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)  
  
## <a name="polybase-specific-notes"></a>Note sulla specifica di PolyBase  
Per un elenco completo delle origini dati esterne supportate, vedere [configurazione della connettività di PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

 Per usare PolyBase, è necessario creare questi tre oggetti:  
  
-   Un'origine dati esterna.  
  
-   Un formato di file esterno, e  
  
-   Una tabella esterna che fa riferimento l'origine dati esterna e il formato di file esterno.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione CONTROL sul database nel data Warehouse di SQL, SQL Server, APS 2016 e database di SQL Server.

> [!IMPORTANT]  
>  Nelle versioni precedenti di PDW, creare le autorizzazioni ALTER ANY EXTERNAL DATA SOURCE di origine necessari dati esterni.
  
  
## <a name="error-handling"></a>Gestione degli errori  
 Se non sono coerenti che RESOURCE_MANAGER_LOCATION definito le origini dati di Hadoop esterne, si verificherà un errore di runtime. Ovvero, è possibile specificare due origini dati esterne che fanno riferimento dello stesso cluster Hadoop e quindi fornendo il percorso di gestione risorse per uno e non per gli altri.  
  
 Il motore di SQL non verifica l'esistenza dell'origine dati esterna quando viene creato l'oggetto origine dati esterna. Se non esiste l'origine dati durante l'esecuzione di query, si verificherà un errore.  
  
## <a name="general-remarks"></a>Osservazioni generali  
Per PolyBase, l'origine dati esterna è con ambito database in SQL Server e SQL Data Warehouse. È con ambito server in Parallel Data Warehouse.
  
Per PolyBase, quando viene definito RESOURCE_MANAGER_LOCATION o JOB_TRACKER_LOCATION, query optimizer prenderà in considerazione l'ottimizzazione di ogni query avviando una mappa ridurre processo Hadoop origine esterna e riduzione di calcolo. Ciò è interamente una decisione basata sui costi.  

Per garantire l'esito positivo delle query di PolyBase nel caso di failover Hadoop NameNode, considerare l'utilizzo di un indirizzo IP virtuale per NameNode del cluster Hadoop. Se non si utilizza un indirizzo IP virtuale per il Hadoop NameNode, in caso di failover di Hadoop NameNode sarà necessario oggetto ALTER EXTERNAL DATA SOURCE in modo da puntare alla nuova posizione.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Tutte le origini dati definite nella stessa posizione di cluster Hadoop devono utilizzare la stessa impostazione per RESOURCE_MANAGER_LOCATION o JOB_TRACKER_LOCATION. Se è presente un'incoerenza, si verificherà un errore di runtime.  
  
 Se il cluster Hadoop è configurato con un nome e l'origine dati esterna Usa l'indirizzo IP per il percorso del cluster, PolyBase deve comunque essere in grado di risolvere il nome del cluster quando viene utilizzata l'origine dati. Per risolvere il nome, è necessario abilitare un server d'inoltro DNS.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco condiviso sull'oggetto origine dati esterna.  
  
##  <a name="examples"></a>Esempi: SQL Server 2016  
  
### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Creare l'origine dati esterna da riferimento Hadoop  
Per creare un'origine dati esterna per fare riferimento a cluster Hortonworks o Cloudera Hadoop, specificare il nome del computer o indirizzo IP della porta e Hadoop Namenode.  
  
```tsql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);

```  
  
### <a name="b-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>B. Creare l'origine dati esterna da riferimento Hadoop con la distribuzione abilitata  
Specificare l'opzione RESOURCE_MANAGER_LOCATION per abilitare push-down dei calcoli in Hadoop per le query PolyBase. Una volta abilitato, PolyBase utilizza una decisione basata sui costi per determinare se il calcolo di query che devono essere inviato in Hadoop o tutti i dati devono essere spostati per elaborare la query in SQL Server.
  
```tsql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
);

```
  
###  <a name="credential"></a> C. Creare l'origine dati esterna per fare riferimento a Hadoop protetto con Kerberos  
Per verificare se il cluster Hadoop protetto con Kerberos, controllare il valore della proprietà hadoop.security.authentication in core-Site.XML Hadoop. Per fare riferimento a un cluster Hadoop protetto con Kerberos, è necessario specificare le credenziali con ambito database che contiene il nome utente di Kerberos e la password. La chiave master del database viene utilizzata per crittografare la chiave privata credenziali con ambito database. 
  
```tsql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1 
WITH IDENTITY = '<hadoop_user_name>', 
SECRET = '<hadoop_password>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (
    TYPE = HADOOP, 
    LOCATION = 'hdfs://10.10.10.10:8050', 
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050', 
    CREDENTIAL = HadoopUser1
);
```

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>D. Creare l'origine dati esterna per fare riferimento a archiviazione blob di Azure
Per creare un'origine dati esterna per fare riferimento nel contenitore dell'archiviazione blob di Azure, specificare l'URI di archiviazione blob di Azure e le credenziali con ambito database che contiene la chiave dell'account di archiviazione di Azure.

In questo esempio, l'origine dati esterna viene denominato dailylogs con account di archiviazione di Azure denominato myaccount un contenitore di archiviazione blob di Azure. L'archiviazione di Azure è origine dati esterna per il trasferimento di dati di sola lettura. e non supporta la distribuzione del predicato.

In questo esempio viene illustrato come creare le credenziali con ambito database per l'autenticazione per archiviazione di Azure. Specificare la chiave di account di archiviazione di Azure in segreto della credenziale di database. Specificare l'identità delle credenziali con ambito di qualsiasi stringa nel database, non viene utilizzato per l'autenticazione per archiviazione di Azure. Quindi, la credenziale viene usata nell'istruzione che crea un'origine dati esterna.

```
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
    TYPE = HADOOP, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```

## <a name="examples-azure-sql-database"></a>Esempi: Database SQL di Azure

### <a name="e-create-a-shard-map-manager-external-data-source"></a>E. Creare un'origine dati esterna gestione di partizioni della mappa
Per creare un'origine dati esterna per fare riferimento a un SHARD_MAP_MANAGER, specificare il nome logico di server che ospita il gestore mappe partizioni nel Database di SQL Azure o un database di SQL Server in una macchina virtuale di Azure.

```tsql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = SHARD_MAP_MANAGER,
    LOCATION = '<server_name>.database.windows.net',
    DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
    CREDENTIAL = ElasticDBQueryCred,
    SHARD_MAP_NAME = 'CustomerIDShardMap'
);
```

### <a name="f-create-an-rdbms-external-data-source"></a>F. Creare un'origine dati esterna RDBMS
Per creare un'origine dati esterna per fare riferimento a un sistema RDBMS, specifica il nome del server logico del database remoto nel Database di SQL Azure.

```tsql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL SQL_Credential  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = RDBMS, 
    LOCATION = '<server_name>.database.windows.net', 
    DATABASE_NAME = 'Customers', 
    CREDENTIAL = SQL_Credential 
);
```

## <a name="examples-azure-sql-data-warehouse"></a>Esempi: Azure SQL Data Warehouse

### <a name="g-create-external-data-source-to-reference-azure-blob-storage"></a>G. Creare l'origine dati esterna per fare riferimento a archiviazione blob di Azure
Per creare un'origine dati esterna per fare riferimento nel contenitore dell'archiviazione blob di Azure, specificare l'URI di archiviazione blob di Azure e le credenziali con ambito database che contiene la chiave dell'account di archiviazione di Azure.

In questo esempio, l'origine dati esterna viene denominato dailylogs con account di archiviazione di Azure denominato myaccount un contenitore di archiviazione blob di Azure. L'origine dati esterna di archiviazione di Azure per il trasferimento dei dati e non supporta la distribuzione del predicato.

In questo esempio viene illustrato come creare le credenziali con ambito database per l'autenticazione per archiviazione di Azure. Specificare la chiave di account di archiviazione di Azure in segreto della credenziale di database. Specificare l'identità delle credenziali con ambito di qualsiasi stringa nel database, non viene utilizzato per l'autenticazione per archiviazione di Azure. Quindi, la credenziale viene usata nell'istruzione che crea un'origine dati esterna.

```tsql
-- Create a database master key if one does not already exist. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage 
WITH (
    TYPE = HADOOP, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```
### <a name="h-create-external-data-source-to-reference-azure-data-lake-store"></a>H. Creare l'origine dati esterna da riferimento archivio Azure Data Lake
Connettività archivio Azure Data lake dipende l'URI di ADLS ed entità servizio dell'applicazione Azure Active directory. Documentazione per la creazione di questa applicazione è reperibile in[autenticazione di archivio Data lake tramite Active Directory](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory).

```tsql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = '<ADLS URI>'
)
```



## <a name="examples-parallel-data-warehouse"></a>Esempi: Parallel Data Warehouse

### <a name="i-create-external-data-source-to-reference-hadoop"></a>I. Creare l'origine dati esterna da riferimento Hadoop
Per creare un'origine dati esterna per fare riferimento a cluster Hortonworks o Cloudera Hadoop, specificare il nome del computer o indirizzo IP della porta e Hadoop Namenode.

```tsql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);
```

### <a name="j-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>J. Creare l'origine dati esterna da riferimento Hadoop con la distribuzione abilitata
Specificare l'opzione JOB_TRACKER_LOCATION per abilitare push-down dei calcoli in Hadoop per le query PolyBase. Una volta abilitato, PolyBase utilizza una decisione basata sui costi per determinare se il calcolo di query che devono essere inviato in Hadoop o tutti i dati devono essere spostati per elaborare la query in SQL Server. 

```tsql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    JOB_TRACKER_LOCATION = '10.10.10.10:8050'
);
```

### <a name="k-create-external-data-source-to-reference-azure-blob-storage"></a>K. Creare l'origine dati esterna per fare riferimento a archiviazione blob di Azure
PERCORSO di origine origine dati per fare riferimento nel contenitore dell'archiviazione blob di Azure, specificare l'URI di archiviazione blob di Azure come i dati esterni per creare un riferimento esterno. Aggiungere la chiave dell'account di archiviazione di Azure per file core-Site.XML PDW per l'autenticazione.

In questo esempio, l'origine dati esterna viene denominato dailylogs con account di archiviazione di Azure denominato myaccount un contenitore di archiviazione blob di Azure. L'origine dati esterna di archiviazione di Azure per il trasferimento dei dati e non supporta la distribuzione del predicato.

```tsql
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
        TYPE = HADOOP, 
        LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'
);
```

## <a name="examples-bulk-operations"></a>Esempi: Le operazioni di massa   
### <a name="l-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>L. Creare un'origine dati esterna per le operazioni bulk, il recupero dei dati dall'archiviazione Blob di Azure.   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].   
Utilizzare l'origine dati seguente per le operazioni bulk utilizzando [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) o [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). La credenziale utilizzata, deve essere creata usando `SHARED ACCESS SIGNATURE` come identità. Per altre informazioni sulle firme di accesso condiviso, vedere [Uso delle firme di accesso condiviso](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).   
```tsql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = AccessAzureInvoices
    );   
```   
Per questo esempio in uso, vedere [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).
  
## <a name="see-also"></a>Vedere anche
[MODIFICARE l'origine dati esterna (Transact-SQL)](../../t-sql/statements/alter-external-data-source-transact-sql.md)  
[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
[CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[CREATE TABLE AS SELECT &#40; Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
[Sys.external_data_sources (Transact-SQL)](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)  
  
  


