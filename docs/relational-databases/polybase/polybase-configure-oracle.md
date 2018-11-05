---
title: Configurare PolyBase per l'accesso a dati esterni in Oracle | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: bf8c9e4d9bdc59d60569594006676b6fa766071a
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806561"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Configurare PolyBase per l'accesso a dati esterni in Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'articolo illustra come usare PolyBase in un'istanza di SQL Server per eseguire query sui dati esterni in Oracle.

## <a name="prerequisites"></a>Prerequisites

Se PolyBase non è stato installato, vedere [Installazione di PolyBase](polybase-installation.md).

## <a name="configure-an-external-table"></a>Configurare una tabella esterna

Per eseguire query sui dati da un'origine dati Oracle, è necessario creare tabelle esterne per fare riferimento ai dati esterni. In questa sezione è disponibile codice di esempio per creare queste tabelle esterne. 
 
In questa sezione verranno creare questi oggetti:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Creare una chiave master nel database, se non ne esiste già. Questo passaggio è necessario per crittografare il segreto delle credenziali.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
     ```
    ## <a name="arguments"></a>Argomenti
    PASSWORD ='password'

    Password utilizzata per crittografare la chiave master nel database. password deve soddisfare i requisiti per i criteri password di Windows del computer che esegue l'hosting dell'istanza di SQL Server.

1. Creare credenziali con ambito database.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
      CREATE DATABASE SCOPED CREDENTIAL credential_name
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Creare un'origine dati esterna con [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Specificare il percorso dell'origine dati esterna e le credenziali per l'origine dati Oracle.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    * CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = oracle://<server address>[:<port>],
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
     ```

1.  Creare tabelle esterne che rappresentano i dati archiviati nel sistema esterno Oracle [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
      ```sql
      /*  LOCATION: Oracle table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
      CREATE EXTERNAL TABLE customers(
      [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_ORDERPRIORITY] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
     [O_CLERK] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
     [O_SHIPPRIORITY] DECIMAL(38) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
      LOCATION='customer',
      DATA_SOURCE=  external_data_source_name
     );
     ```

1. **Facoltativo:** Creare statistiche per una tabella esterna.

    È consigliabile creare le statistiche sulle colonne delle tabelle esterne, in particolare quelle usate per join, filtri e aggregazioni, per prestazioni ottimali delle query.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su PolyBase, vedere [Che cos'è PolyBase?](polybase-guide.md).
