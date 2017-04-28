---
title: "Implementazione di una funzionalità MERGE in una stored procedure compilata in modo nativo | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0465daf504277e1a221d0fd553dd60617eb067a1
ms.lasthandoff: 04/11/2017

---
# <a name="implementing-merge-functionality-in-a-natively-compiled-stored-procedure"></a>Implementazione di una funzionalità MERGE in una stored procedure compilata in modo nativo
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Nell'esempio di codice Transact-SQL in questa sezione viene illustrato come è possibile simulare l'istruzione T-SQL di tipo MERGE in un modulo compilato in modo nativo. L'esempio utilizza una variabile di tabella con una colonna identity, scorre le righe nella variabile di tabella e per ogni riga esegue l'aggiornamento se soddisfa la condizione e un'operazione di inserimento se la condizione non corrisponde.
  
Di seguito viene riportata l'istruzione T-SQL MERGE che si desidera sia supportata all'interno di un processore nativo e che simula l'esempio di codice.  
  
  
  
  
    MERGE INTO dbo.Table1 t  
        USING @tvp v  
        ON t.Column1 = v.c1  
        WHEN MATCHED THEN   
            UPDATE SET Column2 = v.c2  
        WHEN NOT MATCHED THEN  
            INSERT (Column1, Column2) VALUES (v.c1, v.c2);  
  
  
  
  
Di seguito viene riportata l'istruzione T-SQL per ottenere la soluzione alternativa e simulare l'unione.  
  
  
  
  
    DROP PROCEDURE IF EXISTS dbo.usp_merge1;  
    go  
    DROP TYPE IF EXISTS dbo.Type1;  
    go  
    DROP TABLE IF EXISTS dbo.Table1;  
    go  
    -----------------------------  
    -- target table and table type used for the workaround
    -----------------------------  
  
    CREATE TABLE dbo.Table1  
    (  
        Column1  INT  NOT NULL  PRIMARY KEY NONCLUSTERED,  
        Column2  INT  NOT NULL  
    )   
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
  
    CREATE TYPE dbo.Type1 AS TABLE  
    (  
        c1  INT  NOT NULL,  
        c2  INT  NOT NULL,  
  
        RowID    INT  NOT NULL  IDENTITY(1,1),  
        INDEX ix_RowID HASH (RowID) WITH (BUCKET_COUNT=1024)  
    )   
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
    -----------------------------  
    -- stored procedure implementing the workaround
    -----------------------------  
  
    CREATE PROCEDURE dbo.usp_merge1   
        @tvp1 dbo.Type1 READONLY  
        WITH  
        NATIVE_COMPILATION, SCHEMABINDING  
    AS   
    BEGIN ATOMIC  
        WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
              LANGUAGE = N'us_english')  

        DECLARE  @i INT = 1,  @c1 INT,  @c2 INT;  
    
        WHILE @i > 0  
        BEGIN  
            SELECT @c1 = c1, @c2 = c2  
                FROM @tvp1  
                WHERE RowID = @i;  
    
            --test whether the row exists in the TVP; if not, we end the loop
            IF @@ROWCOUNT=0  
                SET @i = 0
            ELSE
            BEGIN
                -- try the update
                UPDATE dbo.Table1  
                    SET   Column2 = @c2  
                    WHERE Column1 = @c1;  
    
                -- if there was no row to update, we insert
                IF @@ROWCOUNT=0  
                    INSERT INTO dbo.Table1 (Column1, Column2)  
                        VALUES (@c1, @c2);  
    
                SET @i += 1
            END
        END  
    END  
    go  
    -----------------------------  
    -- test to validate the functionality
    -----------------------------  
  
    INSERT dbo.Table1 VALUES (1,2);  
    go  
  
    SELECT N'Before-MERGE' AS [Before-MERGE], Column1, Column2  
        FROM dbo.Table1;  
    go  
  
    DECLARE @tvp1 dbo.Type1;  
  
    INSERT @tvp1 (c1, c2) VALUES (1,33), (2,4);  
    EXECUTE dbo.usp_merge1 @tvp1;  
    go  
  
    SELECT N'After--MERGE' AS [After--MERGE], Column1, Column2  
        FROM dbo.Table1;  
    go  
    -----------------------------  

  
    /****  Actual output:  
  
    Before-MERGE   Column1   Column2  
    Before-MERGE      1         2  
  
    After--MERGE   Column1   Column2  
    After--MERGE      1        33  
    After--MERGE      2         4  
    ****/  
  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di migrazione relativi alle stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Costrutti Transact-SQL non supportati da OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  

