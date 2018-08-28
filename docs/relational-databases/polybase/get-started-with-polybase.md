---
title: Introduzione a PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: quickstart
helpviewer_keywords:
- PolyBase
- PolyBase, getting started
- Hadoop import
- Hadoop export
- Azure blob storage import
- Azure blob storage export
- Hadoop import, PolyBase getting started
- Hadoop export, Polybase getting started
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 62247350c54f389882e91140d0f4852ad1d4023d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034237"
---
# <a name="get-started-with-polybase"></a>Introduzione a PolyBase
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Questo argomento contiene le nozioni di base sull'esecuzione di PolyBase per un'istanza di SQL Server.
  
 La procedura seguente consente di:  
  
-   Installare ed eseguire PolyBase sul server  
  
-   Reperire esempi di istruzioni per la creazione di oggetti PolyBase  
  
-   Comprendere in che modo gestire gli oggetti PolyBase in SQL Server Management Studio (SSMS)  
  
-   Reperire esempi di query con oggetti PolyBase    

## <a name="install-polybase"></a>Installare PolyBase  
Se PolyBase non è stato installato, vedere [Installazione di PolyBase](../../relational-databases/polybase/polybase-installation.md). Nell'articolo sull'installazione vengono illustrati i prerequisiti.
  
### <a name="how-to-confirm-installation"></a>Procedura per confermare l'installazione  
 Dopo l'installazione, eseguire il comando seguente per verificare che PolyBase sia stato installato correttamente. Se installato, PolyBase restituisce 1; in caso contrario, restituisce 0.  
  
```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
##  <a name="supported"></a> Configurare PolyBase  
 Dopo l'installazione è necessario configurare SQL Server in modo che usi la versione di Hadoop o l'archiviazione BLOB di Azure. PolyBase supporta due provider di Hadoop, Hortonworks Data Platform (HDP) e Cloudera Distributed Hadoop (CDH).  Le origini dati esterne supportate includono:  
  
-   Hortonworks HDP 1.3 su Linux/Windows Server  
  
-   Hortonworks HDP 2.1 - 2.6 su Linux

-   Hortonworks HDP 2.1 - 2.3 su Windows Server  
  
-   Cloudera CDH 4.3 su Linux  
  
-   Cloudera CDH 5.1 – 5.5, 5.9 - 5.13 su Linux  
  
-   Archiviazione BLOB Azure  
 
Hadoop segue il modello "Principale.Secondaria.Versione" per le nuove versioni. Sono supportate tutte le versioni all'interno di una versione principale e secondaria supportata.
 

>  [!NOTE]
> La connettività ad Azure Data Lake Store è supportata solo in Azure SQL Data Warehouse.
  
### <a name="external-data-source-configuration"></a>Configurazione con origine dati esterna  
  
1.  Eseguire [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 'hadoop connectivity' e impostare il valore appropriato. Per impostazione predefinita, l'opzione hadoop connectivity è impostata su 7. Per trovare il valore, vedere [Configurazione della connettività di PolyBase &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
      ```sql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  È necessario riavviare SQL Server mediante **services.msc**. Il riavvio di SQL Server comporta il riavvio di questi servizi:  
  
    -   Servizio spostamento dati di PolyBase per SQL Server  
  
    -   Motore di PolyBase per SQL Server  
  
 ![arrestare e avviare i servizi PolyBase in services.msc](../../relational-databases/polybase/media/polybase-stop-start.png "arrestare e avviare i servizi PolyBase in services.msc")  
  
### <a name="pushdown-configuration"></a>Configurazione della distribuzione  
 Per migliorare le prestazioni delle query, abilitare il calcolo della distribuzione in un cluster Hadoop:  
  
1.  Trovare il file **yarn-site.xml** nel percorso di installazione di SQL Server. In genere il percorso è:  
  
    ```  
  
    C:Program FilesMicrosoft SQL ServerMSSQL13.MSSQLSERVERMSSQLBinnPolybaseHadoopconf  
  
    ```  
  
2.  Nel computer Hadoop trovare il file analogo nella directory di configurazione Hadoop. Nel file trovare e copiare il valore della chiave di configurazione yarn.application.classpath.  
  
3.  Nel computer SQL Server, nel **file yarn.site.xml,** trovare la proprietà **yarn.application.classpath** . Incollare il valore dal computer Hadoop nell'elemento valore.  
  
4. Per tutte le versioni di CDH 5.X sarà necessario aggiungere i parametri di configurazione mapreduce.application.classpath alla fine del file yarn.site.xml o nel file mapred-site.xml. HortonWorks include queste configurazioni all'interno delle configurazioni yarn.application.classpath. Vedere [Configurazione di PolyBase](../../relational-databases/polybase/polybase-configuration.md) per alcuni esempi.

 
## <a name="scale-out-polybase"></a>Scalabilità orizzontale di PolyBase  
 La funzionalità gruppo di PolyBase consente di creare un cluster di istanze di SQL Server per elaborare grandi quantità di set di dati da origini dati esterne in un meccanismo di scalabilità orizzontale che consente di migliorare le prestazioni delle query.  
  
1.  Installare SQL Server con PolyBase in più computer.  
  
2.  Selezionare un server SQL Server come nodo head.  
  
3.  Aggiungere altre istanze come nodi di calcolo eseguendo [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
4.  Riavviare il servizio PolyBase Data Movement Service sui nodi di calcolo.  
  
 Per informazioni dettagliate, vedere [Gruppi con scalabilità orizzontale di PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).  
  
## <a name="create-t-sql-objects"></a>Creare oggetti T-SQL  
 Creare gli oggetti a seconda dell'origine dati esterna, ovvero Hadoop o il servizio di archiviazione di Azure.  
  
### <a name="hadoop"></a>Hadoop  
  
```sql  
-- 1: Create a database scoped credential.  
-- Create a master key on the database. This is required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- 2: Create a database scoped credential  for Kerberos-secured Hadoop clusters.  
-- IDENTITY: the Kerberos user name.  
-- SECRET: the Kerberos password  
  
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1   
WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
  
-- 3:  Create an external data source.  
-- LOCATION (Required) : Hadoop Name Node IP address and port.  
-- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
-- CREDENTIAL (Optional):  the database scoped credential, created above.  
  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
        TYPE = HADOOP,   
        LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',   
        RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',   
        CREDENTIAL = HadoopUser1        
);  
  
-- 4: Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).    
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
-- 5:  Create an external table pointing to data stored in Hadoop.  
-- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = MyHadoopCluster,  
        FILE_FORMAT = TextFileFormat  
);  
  
-- 6:  Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
### <a name="azure-blob-storage"></a>Archiviazione BLOB Azure  
  
```sql  
--1: Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Azure blob storage.  
-- IDENTITY: any string (this is not used for authentication to Azure storage).  
-- SECRET: your Azure storage account key.  
  
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential   
WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';  
  
--2:  Create an external data source.  
-- LOCATION:  Azure account storage account name and blob container name.  
-- CREDENTIAL: The database scoped credential created above.  
  
CREATE EXTERNAL DATA SOURCE AzureStorage with (  
        TYPE = HADOOP,   
        LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
        CREDENTIAL = AzureStorageCredential  
);  
  
--3:  Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat
WITH (  
       FORMAT_TYPE = DELIMITEDTEXT,   
       FORMAT_OPTIONS (
         FIELD_TERMINATOR ='|',   
         USE_TYPE_DEFAULT = TRUE
       )
);
         
  
--4: Create an external table.  
-- The external table points to data stored in Azure storage.  
-- LOCATION: path to a file or directory that contains the data (relative to the blob container).  
-- To point to all files under the blob container, use LOCATION='/'   
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = AzureStorage,  
        FILE_FORMAT = TextFileFormat  
);  
  
--5: Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## <a name="polybase-queries"></a>Query PolyBase  
 PolyBase è adatto per assolvere a una triplice funzione:  
  
-   esecuzione di query ad hoc su tabelle esterne  
  
-   importazione di dati.  
  
-   esportazione di dati.  
  
### <a name="query-examples"></a>Esempi di query  
  
-   Query ad hoc  
  
    ```sql  
    -- PolyBase Scenario 1: Ad-Hoc Query joining relational with Hadoop data   
    -- Select customers who drive faster than 35 mph: joining structured customer data stored   
    -- in SQL Server with car sensor data stored in Hadoop.  
    SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,   
            Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
    FROM Insured_Customers, CarSensor_Data  
    WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35   
    ORDER BY CarSensor_Data.Speed DESC  
    OPTION (FORCE EXTERNALPUSHDOWN);    -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
    ```  
  
-   Importazione di dati  
  
    ```sql  
    -- PolyBase Scenario 2: Import external data into SQL Server.  
    -- Import data for fast drivers into SQL Server to do more in-depth analysis and  
    -- leverage Columnstore technology.  
  
    SELECT DISTINCT   
            Insured_Customers.FirstName, Insured_Customers.LastName,   
            Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
    INTO Fast_Customers from Insured_Customers INNER JOIN   
    (  
            SELECT * FROM CarSensor_Data where Speed > 35   
    ) AS SensorD  
    ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
    ORDER BY YearlyIncome  
  
    CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
    ```  
  
-   Esportazione di dati  
  
    ```  
    -- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
  
    -- Enable INSERT into external table  
    sp_configure ‘allow polybase export’, 1;  
    reconfigure  
  
    -- Create an external table.   
    CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
            [FirstName] char(25) NOT NULL,   
            [LastName] char(25) NOT NULL,   
            [YearlyIncome] float NULL,   
            [MaritalStatus] char(1) NOT NULL  
    )  
    WITH (  
            LOCATION='/old_data/2009/customerdata',  
            DATA_SOURCE = HadoopHDP2,  
            FILE_FORMAT = TextFileFormat,  
            REJECT_TYPE = VALUE,  
            REJECT_VALUE = 0  
    );  
  
    -- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
    INSERT INTO dbo.FastCustomer2009  
    SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
    ON (T1.CustomerKey = T2.CustomerKey)  
    WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
    ```  
  
## <a name="managing-polybase-objects-in-ssms"></a>Gestione di oggetti PolyBase in SQL Server Management Studio  
 In SQL Server Management Studio, le tabelle esterne vengono visualizzate in una cartella separata **Tabelle esterne**. Le origini dati esterne e i formati di file esterni si trovano nelle sottocartelle in **External Resources**.  
  
 ![Oggetti PolyBase in SSMS](../../relational-databases/polybase/media/polybase-management.png "Oggetti PolyBase in SSMS")  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 Usare le DMV per risolvere i problemi relativi alle prestazioni e alle query. Per informazioni dettagliate, vedere [Risoluzione dei problemi di PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md).  
  
 Dopo l'aggiornamento da SQL Server 2016 RC1 a RC2 o RC3, le query potrebbero non riuscire. Per informazioni dettagliate e una soluzione, vedere [Note sulla versione di SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md) e cercare "PolyBase".  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per comprendere la funzionalità di scalabilità orizzontale, vedere [Gruppi con scalabilità orizzontale di PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).  Per monitorare PolyBase, vedere [Risoluzione dei problemi di PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md). Per informazioni sulla risoluzione dei problemi relativi alle prestazioni di PolyBase, vedere [PolyBase troubleshooting with dynamic management views](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80) (Risoluzione dei problemi di PolyBase con DMV).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida a PolyBase](../../relational-databases/polybase/polybase-guide.md)   
 [Gruppi con scalabilità orizzontale di PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)   
 [Stored procedure di PolyBase](http://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
