---
title: Configurare PolyBase per l'accesso a dati esterni in SQL Server | Microsoft Docs
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
ms.openlocfilehash: 8f99f95cdec92be900e86e3b08317b77dd5dbce2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742279"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Configurare PolyBase per l'accesso a dati esterni in SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'articolo illustra come usare PolyBase in un'istanza di SQL Server per eseguire query sui dati esterni in un'altra istanza di SQL Server.

## <a name="prerequisites"></a>Prerequisites

Se PolyBase non è stato installato, vedere [Installazione di PolyBase](polybase-installation.md). Nell'articolo sull'installazione vengono illustrati i prerequisiti.

## <a name="configure-an-external-table"></a>Configurare una tabella esterna

Per eseguire query sui dati da un'origine dati SQL Server, è necessario creare tabelle esterne per fare riferimento ai dati esterni. In questa sezione è disponibile codice di esempio per creare queste tabelle esterne. 
 
È consigliabile creare le statistiche sulle colonne delle tabelle esterne, in particolare quelle usate per join, filtri e aggregazioni, per prestazioni ottimali delle query.

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
     CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Creare un'origine dati esterna con [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Specificare il percorso dell'origine dati esterna e le credenziali per SQL Server.

     ```sql
     /*  LOCATION: Server DNS name or IP address.
     *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
     *  CREDENTIAL: the database scoped credential, created above.
     */  
     CREATE EXTERNAL DATA SOURCE SqlServerInstance
     WITH ( 
     LOCATION = '<vendor>://<server>[:<port>]',
     -- PUSHDOWN = ON | OFF,
     CREDENTIAL = SqlServerCredentials
     );
     ```

1. Creare schemi per i dati esterni

     ```sql
     CREATE SCHEMA sqlserver;
     GO
     ```

1.  Creare tabelle esterne che rappresentano i dati archiviati nell'istanza di SQL Server esterna [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: sql server table/view in 'database_name.schema_name.object_name' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE sqlserver.customer(
     C_CUSTKEY INT NOT NULL,
     C_NAME VARCHAR(25) NOT NULL,
     C_ADDRESS VARCHAR(40) NOT NULL,
     C_NATIONKEY INT NOT NULL,
     C_PHONE CHAR(15) NOT NULL,
     C_ACCTBAL DECIMAL(15,2) NOT NULL,
     C_MKTSEGMENT CHAR(10) NOT NULL,
     C_COMMENT VARCHAR(117) NOT NULL
      )
      WITH (
      LOCATION='tpch_10.dbo.customer',
      DATA_SOURCE=SqlServerInstance
     );
      ```

1. Creare statistiche per una tabella esterna.

     ```sql
      CREATE STATISTICS CustomerCustKeyStatistics ON sqlserver.customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su Polybase, vedere [Che cos'è PolyBase?](polybase-guide.md).
