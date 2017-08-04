---
title: Introduzione a caratteristiche di prestazioni di SQL Server in Linux | Documenti Microsoft
description: "In questo argomento viene fornita un'introduzione delle funzionalità di prestazioni di SQL Server per gli utenti di Linux che hanno familiarità con SQL Server. Molti di questi esempi funzionano in tutte le piattaforme, ma il contesto di questo articolo è Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4f4f58b682451b7dabf336241ec94797a4d1469e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>Procedura dettagliata per le caratteristiche di prestazioni di SQL Server in Linux
Nel caso di un utente di Linux che è una novità di SQL Server, le attività seguenti illustrano alcune delle funzionalità di prestazioni. Queste non sono specifiche di Linux o univoco, ma consente di farsi un'idea delle aree per approfondire la verifica. In ogni esempio viene fornito un collegamento alla documentazione di profondità per tale area.

> [!NOTE]
> L'esempio seguente usa il database di esempio AdventureWorks. Per istruzioni su come ottenere e installare il database di esempio, vedere [ripristinare un database di SQL Server da Windows a Linux](sql-server-linux-migrate-restore-database.md).

## <a name="create-a-columnstore-index"></a>Creare un indice Columnstore
Un indice columnstore è una tecnologia per l'archiviazione e query su grandi archivi di dati in un formato a colonne di dati, detto columnstore.  

1. Aggiungere un indice Columnstore sulla tabella SalesOrderDetail tramite l'esecuzione di T-SQL riportata di seguito:

   ```sql
   CREATE NONCLUSTERED COLUMNSTORE INDEX [IX_SalesOrderDetail_ColumnStore]
      ON Sales.SalesOrderDetail
      (UnitPrice, OrderQty, ProductID)
   GO
   ```

2. Eseguire la query seguente che verrà utilizzato l'indice Columnstore per l'analisi della tabella:

   ```sql
   SELECT ProductID, SUM(UnitPrice) SumUnitPrice, AVG(UnitPrice) AvgUnitPrice,
      SUM(OrderQty) SumOrderQty, AVG(OrderQty) AvgOrderQty
   FROM Sales.SalesOrderDetail
      GROUP BY ProductID
      ORDER BY ProductID
   ```

3. Verificare che l'indice Columnstore è stato usato da ricerca di object_id per l'indice Columnstore e confermare che venga visualizzato in statistiche di utilizzo per la tabella SalesOrderDetail:

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>Utilizzo di OLTP In memoria
SQL Server fornisce funzionalità di OLTP In memoria che possono migliorare notevolmente le prestazioni dei sistemi di applicazione.  In questa sezione della Guida alla valutazione verrà illustrati i passaggi per creare una tabella con ottimizzazione per la memoria archiviata in memoria e una stored procedure compilata in modo nativo che può accedere alla tabella senza la necessità di essere compilate o interpretate.

### <a name="configure-database-for-in-memory-oltp"></a>Configurare i Database per OLTP In memoria
1. Si consiglia di impostare il database a un livello di compatibilità di almeno 130 all'utilizzo di OLTP In memoria.  Utilizzare la query seguente per verificare il livello di compatibilità corrente di AdventureWorks:  

   ```sql
   USE AdventureWorks
   GO
   SELECT d.compatibility_level
   FROM sys.databases as d
     WHERE d.name = Db_Name();
   GO
   ```
   
   Se necessario, aggiornare il livello su 130:

   ```sql
   ALTER DATABASE CURRENT
   SET COMPATIBILITY_LEVEL = 130;
   GO
   ```

2. Quando una transazione include una tabella basata su disco e una tabella con ottimizzazione per la memoria, è essenziale che la parte con ottimizzazione per la memoria della transazione operano a livello di isolamento transazione denominato SNAPSHOT.  Per applicare in modo affidabile questo livello per le tabelle con ottimizzazione per la memoria in una transazione tra contenitori, eseguire le operazioni seguenti:

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. Prima di poter creare una tabella con ottimizzazione per la memoria, è innanzitutto necessario creare un FILEGROUP con ottimizzazione per la memoria e un contenitore per i file di dati:

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>Creare una tabella con ottimizzazione per la memoria
L'archivio primario per le tabelle con ottimizzazione per la memoria è la memoria principale e pertanto a differenza delle tabelle basate su disco, i dati non dover essere letti da disco nei buffer di memoria.  Per creare una tabella con ottimizzazione per la memoria, utilizzare il MEMORY_OPTIMIZED = ON clausola.

1. Eseguire la query seguente per creare una tabella con ottimizzazione per la memoria dbo. ShoppingCart.  Per impostazione predefinita, i dati verranno resi persistenti su disco per motivi di durabilità (si noti che durabilità è anche possibile impostare in modo permanente solo lo schema). 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. Inserimento di alcuni record nella tabella:

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>Stored Procedure compilate in modo nativo
SQL Server supporta le stored procedure compilate in modo nativo che accedono alle tabelle con ottimizzazione per la memoria. Le istruzioni T-SQL vengono compilate nel codice macchina e archiviate come DLL native, abilitare l'accesso ai dati più veloce e più efficiente esecuzione della query di T-SQL tradizionale.   Le stored procedure che sono contrassegnate con NATIVE_COMPILATION vengono compilate in modo nativo. 

1. Eseguire lo script seguente per creare una stored procedure compilata in modo nativo che inserisce un numero elevato di record nella tabella ShoppingCart:


   ```sql
   CREATE PROCEDURE dbo.usp_InsertSampleCarts @InsertCount int 
    WITH NATIVE_COMPILATION, SCHEMABINDING AS 
   BEGIN ATOMIC 
   WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')

   DECLARE @i int = 0

   WHILE @i < @InsertCount 
    BEGIN 
     INSERT INTO dbo.ShoppingCart VALUES (1, SYSDATETIME() , NULL) 
     SET @i += 1 
    END
   END 
   ```
2. Inserire 1.000.000 di righe:

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. Verificare che le righe sono state inserite:

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>Altre informazioni su OLTP In memoria
Per ulteriori informazioni su OLTP In memoria, vedere gli argomenti seguenti:

- [Avvio rapido 1: Tecnologie OLTP in memoria per migliorare le prestazioni di Transact-SQL](https://msdn.microsoft.com/library/mt694156.aspx)
- [Migrazione a OLTP in memoria](https://msdn.microsoft.com/library/dn247639.aspx)
- [Tabella temporanea più rapida e variabile di tabella tramite l'ottimizzazione per la memoria](https://msdn.microsoft.com/library/mt718711.aspx)
- [Monitorare e risolvere i problemi relativi all'utilizzo della memoria](https://msdn.microsoft.com/library/dn465869.aspx)
- [OLTP in memoria (ottimizzazione per la memoria)](https://msdn.microsoft.com/library/dn133186.aspx)

## <a name="use-query-store"></a>Usare l'archivio Query
Archivio query raccoglie informazioni dettagliate prestazioni query, piani di esecuzione e le statistiche di runtime.

Archivio query non è attiva per impostazione predefinita e può essere abilitata con ALTER DATABASE:

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

Eseguire la query seguente per restituire informazioni sulle query e piani in archivio query: 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>Viste a gestione dinamica query
Viste a gestione dinamica restituiscono informazioni sullo stato di server che possono essere utilizzate per monitorare l'integrità di un'istanza del server, diagnosticare i problemi e ottimizzare le prestazioni.

Per eseguire query sulla vista a gestione dinamica dm_os_wait statistiche:

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
