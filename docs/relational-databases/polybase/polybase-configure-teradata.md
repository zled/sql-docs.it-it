---
title: Configurare PolyBase per l'accesso a dati esterni in Teradata | Microsoft Docs
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
ms.openlocfilehash: 1140e537e4ea7614df90f964ae280b7d86741d31
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806631"
---
# <a name="configure-polybase-to-access-external-data-in-teradata"></a>Configurare PolyBase per l'accesso a dati esterni in Teradata

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'articolo illustra come usare PolyBase in un'istanza di SQL Server per eseguire query sui dati esterni in Teradata.

## <a name="prerequisites"></a>Prerequisites

Se PolyBase non è stato installato, vedere [Installazione di PolyBase](polybase-installation.md). Nell'articolo sull'installazione vengono illustrati i prerequisiti.

Per usare PolyBase in Teradata, è necessario il ridistribuibile di VC++.
 
## <a name="configure-an-external-table"></a>Configurare una tabella esterna

Per eseguire query sui dati da un'origine dati Teradata, è necessario creare tabelle esterne per fare riferimento ai dati esterni. In questa sezione è disponibile codice di esempio per creare queste tabelle esterne. 

In questa sezione verranno creare questi oggetti:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Creare una chiave master nel database, se non esiste già. Questo passaggio è necessario per crittografare il segreto delle credenziali.

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
     WITH IDENTITY = 'username', Secret = 'password'
     ```

1. Creare un'origine dati esterna con [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    * CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = teradata://<server address>[:<port>],
   -- PUSHDOWN = ON | OFF,
    CREDENTIAL =credential_name
    );

     ```

1.  Creare tabelle esterne che rappresentano i dati archiviati nel sistema esterno Teradata [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: Teradata table/view in '<database_name>.<object_name>' format
      *  DATA_SOURCE: the external data source, created above.
      */
     CREATE EXTERNAL TABLE customer(
      L_ORDERKEY INT NOT NULL,
      L_PARTKEY INT NOT NULL,
     L_SUPPKEY INT NOT NULL,
     L_LINENUMBER INT NOT NULL,
     L_QUANTITY DECIMAL(15,2) NOT NULL,
     L_EXTENDEDPRICE DECIMAL(15,2) NOT NULL,
     L_DISCOUNT DECIMAL(15,2) NOT NULL,
     L_TAX DECIMAL(15,2) NOT NULL,
     L_RETURNFLAG CHAR NOT NULL,
     L_LINESTATUS CHAR NOT NULL,
     L_SHIPDATE DATE NOT NULL,
     L_COMMITDATE DATE NOT NULL,
     L_RECEIPTDATE DATE NOT NULL,
     L_SHIPINSTRUCT CHAR(25) NOT NULL,
     L_SHIPMODE CHAR(10) NOT NULL,
     L_COMMENT VARCHAR(44) NOT NULL
     )
     WITH (
     LOCATION='customer',
     DATA_SOURCE= external_data_source_name
     );
     ```

1. **Facoltativo:** Creare statistiche per una tabella esterna.

    È consigliabile creare le statistiche sulle colonne delle tabelle esterne, in particolare quelle usate per join, filtri e aggregazioni, per prestazioni ottimali delle query.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su PolyBase, vedere [Che cos'è PolyBase?](polybase-guide.md).
