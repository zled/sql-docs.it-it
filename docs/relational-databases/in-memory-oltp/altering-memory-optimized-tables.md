---
title: Modifica di tabelle con ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/19/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7
ms.openlocfilehash: bd27f9755945abf7c09118a5997bb3745e66ab57
ms.contentlocale: it-it
ms.lasthandoff: 06/23/2017

---
# Modifica di tabelle con ottimizzazione per la memoria
<a id="altering-memory-optimized-tables" class="xliff"></a>
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Le modifiche dello schema e dell'indice nelle tabelle con ottimizzazione per la memoria possono essere eseguite con l'istruzione ALTER TABLE. In SQL Server 2016 e nel database SQL di Azure le operazioni ALTER TABLE su tabelle ottimizzate per la memoria sono OFFLINE, vale a dire che la tabella non è disponibile per eseguire una query mentre è in corso l'operazione. L'applicazione di database può proseguire l'esecuzione e qualsiasi operazione che accede alla tabella viene bloccata fino al termine del processo di modifica. È possibile combinare più operazioni ADD, DROP o ALTER in una singola istruzione ALTER TABLE.
  
## ALTER TABLE
<a id="alter-table" class="xliff"></a>  
 
La sintassi ALTER TABLE viene usata per apportare modifiche allo schema della tabella e per aggiungere, eliminare e ricompilare gli indici. Gli indici sono considerati parte della definizione di tabella:  
  
-   La sintassi ALTER TABLE … ADD/DROP/ALTER INDEX è supportata solo per le tabelle con ottimizzazione per la memoria.  
  
-   Se non si usa l'istruzione ALTER TABLE, le istruzioni CREATE INDEX, DROP INDEX e ALTER INDEX *non* sono supportate per gli indici nelle tabelle con ottimizzazione per la memoria.  
  
 Di seguito è riportata la sintassi per le clausole ADD, DROP e ALTER INDEX nell'istruzione ALTER TABLE.  
  
```
| ADD   
     {   
        <column_definition>  
      | <table_constraint>  
      | <table_index>    
     } [ ,...n ]  
  
| DROP   
     {  
         [ CONSTRAINT ]   
         {   
              constraint_name   
         } [ ,...n ]  
         | COLUMN   
         {  
              column_name   
         } [ ,...n ]  
         | INDEX   
         {  
              index_name   
         } [ ,...n ]  
     } [ ,...n ]  
  
| ALTER INDEX index_name  
     {   
         REBUILD WITH ( <rebuild_index_option> )     
     }  
}  
```  
  
 Sono supportati i tipi di modifiche seguenti:  
  
-   Modifica del numero di bucket  
  
-   Aggiunta e rimozione di un indice  
  
-   Modifica, aggiunta e rimozione di una colonna  
  
-   Aggiunta e rimozione di un vincolo  
  
 Per altre informazioni sulla funzionalità ALTER TABLE e per la sintassi completa, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
## Dipendenza associata a schema
<a id="schema-bound-dependency" class="xliff"></a>  
 Le stored procedure compilate in modo nativo devono essere associate a schema, ovvero devono avere una dipendenza associata a schema rispetto alle tabelle con ottimizzazione per la memoria a cui accedono e alle colonne a cui fanno riferimento. Una dipendenza associata a schema è una relazione tra due entità che impedisce l'eliminazione o la modifica incompatibile dell'entità a cui si fa riferimento finché esiste l'entità di riferimento.  
  
 Ad esempio, se una stored procedure compilata in modo nativo con associazione a schema fa riferimento a una colonna *c1* dalla tabella *mytable*, la colonna *c1* non può essere eliminata. Analogamente, se esiste una procedura con un'istruzione INSERT senza elenco di colonne, ad esempio, `INSERT INTO dbo.mytable VALUES (...)`, non è possibile eliminare alcuna colonna nella tabella.  
 
## Registrazione di ALTER TABLE nelle tabelle con ottimizzazione per la memoria
<a id="logging-of-alter-table-on-memory-optimized-tables" class="xliff"></a>
In una tabella con ottimizzazione per la memoria, la maggior parte degli scenari ALTER TABLE ora viene eseguita in parallelo, con conseguente ottimizzazione delle operazioni di scrittura nel log delle transazioni. L'ottimizzazione si ottiene registrando nel log delle transazioni solo le modifiche ai metadati. Le operazioni ALTER TABLE seguenti vengono tuttavia eseguite a thread singolo e non sono ottimizzate per il log.

In questo caso l'operazione a thread singolo registrerebbe l'intero contenuto della tabella modificata nel log delle transazioni. Di seguito è riportato un elenco di operazioni a thread singolo:

- Modificare o aggiungere una colonna per usare un tipo LOB (Large Object): nvarchar(max), varchar(max) o varbinary(max).

- Aggiungere o eliminare un indice COLUMNSTORE.

- Quasi tutto ciò che interessa una [colonna all'esterno di righe](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md).

    - Spostare una colonna dall'interno di righe all'esterno di righe.

    - Spostare una colonna dall'esterno di righe all'interno di righe.

    - Creare una nuova colonna all'esterno di righe.

    - *Eccezione:* il prolungamento di una colonna già all'esterno di righe viene registrato in modo ottimizzato. 
  
## Esempi
<a id="examples" class="xliff"></a>  
 L'esempio seguente modifica il numero di bucket di un indice hash esistente. L'indice hash viene ricompilato con il nuovo numero di bucket mentre le altre proprietà dell'indice hash rimangono invariate.  
  
```tsql
ALTER TABLE Sales.SalesOrderDetail_inmem   
       ALTER INDEX imPK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID  
              REBUILD WITH (BUCKET_COUNT=67108864);  
GO
```
  
 L'esempio seguente aggiunge una colonna con un vincolo NON NULL e una definizione DEFAULT e usa WITH VALUES per fornire valori per ogni riga esistente nella tabella. Se non si utilizza WITH VALUES, a ogni riga della nuova colonna viene associato il valore NULL.  
  
```tsql  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD Comment NVARCHAR(100) NOT NULL DEFAULT N'' WITH VALUES;  
GO
```  
  
 L'esempio seguente aggiunge un vincolo di chiave primaria a una colonna esistente.  
  
```tsql
CREATE TABLE dbo.UserSession (   
   SessionId int not null,   
   UserId int not null,   
   CreatedDate datetime2 not null,   
   ShoppingCartId int,   
   index ix_UserId nonclustered hash (UserId) with (bucket_count=400000)   
)   
WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_ONLY) ;  
GO  
  
ALTER TABLE dbo.UserSession  
       ADD CONSTRAINT PK_UserSession PRIMARY KEY NONCLUSTERED (SessionId);  
GO
```  
  
 L'esempio seguente rimuove un indice.  
  
```tsql
ALTER TABLE Sales.SalesOrderDetail_inmem  
       DROP INDEX ix_ModifiedDate;  
GO
```  
  
 L'esempio seguente aggiunge un indice.  
  
```tsql  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD INDEX ix_ModifiedDate (ModifiedDate);  
GO  
```  
  
 L'esempio seguente aggiunge più colonne, con un indice e vincoli.  
  
```tsql
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD    CustomerID int NOT NULL DEFAULT -1 WITH VALUES,  
              ShipMethodID int NOT NULL DEFAULT -1 WITH VALUES,  
              INDEX ix_Customer (CustomerID);  
GO  
```


<a name="logging-of-alter-table-on-memory-optimized-tables-124"></a>


## Vedere anche
<a id="see-also" class="xliff"></a>  

[Tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  


