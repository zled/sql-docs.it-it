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
ms.openlocfilehash: 4038f6ee6be90e3c6cf11a3b7c70ec9576e6ee8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818859"
---
# <a name="configure-polybase-to-access-external-data-in-teradata"></a>Configurare PolyBase per l'accesso a dati esterni in Teradata

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'articolo illustra come usare PolyBase in un'istanza di SQL Server per eseguire query sui dati esterni in Teradata.

## <a name="prerequisites"></a>Prerequisites

Se PolyBase non è stato installato, vedere [Installazione di PolyBase](polybase-installation.md). Nell'articolo sull'installazione vengono illustrati i prerequisiti.

Per usare PolyBase in Teradata, è necessario il ridistribuibile di VC++. 
 
## <a name="configure-an-external-table"></a>Configurare una tabella esterna

Per eseguire query sui dati da un'origine dati Teradata, è necessario creare tabelle esterne per fare riferimento ai dati esterni. In questa sezione è disponibile codice di esempio per creare queste tabelle esterne. 
 
È consigliabile creare le statistiche sulle colonne delle tabelle esterne. In particolare quelle usate per join, filtri e aggregazioni, per prestazioni ottimali delle query.

In questa sezione verranno creare questi oggetti:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL FILE FORMAT (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)


1. Creare una chiave master nel database. Questo passaggio è necessario per crittografare il segreto delle credenziali.

     ```sql
     CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. Creare credenziali con ambito database.
 
     ```sql
     /*  specify credentials to external data source
      *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL TeradataCredentials 
     WITH IDENTITY = 'username', Secret = 'password'
     ```

1. Creare un'origine dati esterna con [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Specificare il percorso dell'origine dati esterna e le credenziali per Teradata.

     ```sql
      /*  LOCATION: Server DNS name or IP address.
     *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
     *  CREDENTIAL: the database scoped credential, created above.
     */  
     CREATE EXTERNAL DATA SOURCE TeradataInstance
     WITH ( 
     LOCATION = '<vendor>://<server>[:<port>]',
     -- PUSHDOWN = ON | OFF,
       CREDENTIAL = TeradataCredentials
     );
     ```

1. Creare schemi per i dati esterni

     ```sql
     CREATE SCHEMA teradata;
     GO
     ```

1.  Creare tabelle esterne che rappresentano i dati archiviati nel sistema esterno Teradata [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: Teradata table/view in '<database_name>.<object_name>' format
      *  DATA_SOURCE: the external data source, created above.
      */
     CREATE EXTERNAL TABLE teradata.lineitem(
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
     LOCATION='tpch.lineitem',
     DATA_SOURCE=TeradataInstance
     );
     ```

1. Creare statistiche per una tabella esterna per prestazioni ottimali.

     ```sql
      CREATE STATISTICS LineitemOrderKeyStatistics ON teradata.lineitem(L_ORDERKEY) WITH FULLSCAN; 
      ```



## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su Polybase, vedere [Che cos'è PolyBase?](polybase-guide.md).
