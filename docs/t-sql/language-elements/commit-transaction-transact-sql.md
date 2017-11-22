---
title: COMMIT della transazione (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COMMIT
- COMMIT TRANSACTION
- COMMIT_TSQL
- COMMIT_TRANSACTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- ending transactions [SQL Server]
- user-defined transactions [SQL Server]
- committed transactions
- transactions [SQL Server], ending
- marking end of transactions [SQL Server]
- implicit transactions
- distributed transactions [SQL Server], committed
- transactions [SQL Server], committed
- COMMIT TRANSACTION statement
- rolling back transactions, COMMIT TRANSACTION
ms.assetid: f8fe26a9-7911-497e-b348-4e69c7435dc1
caps.latest.revision: "53"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: b2f6bffa6a19007fc98796daa9ff34bda729bd4d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="commit-transaction-transact-sql"></a>COMMIT TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Contrassegna la fine di una transazione esplicita o implicita completata correttamente. Se @@TRANCOUNT è 1, COMMIT TRANSACTION rende tutte le modifiche dei dati eseguite dall'inizio della transazione una parte permanente del database, libera le risorse utilizzate dalla transazione e decrementa @@TRANCOUNT su 0. Se @@TRANCOUNT è maggiore di 1, COMMIT TRANSACTION riduce @@TRANCOUNT solo da 1 e la transazione rimane attiva.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Applies to SQL Server (starting with 2008) and Azure SQL Database
  
COMMIT [ { TRAN | TRANSACTION }  [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
[ ; ]  
```  
 
```  
-- Applies to Azure SQL Data Warehouse and Parallel Data Warehouse Database
  
COMMIT [ TRAN | TRANSACTION ] 
[ ; ]  
``` 
 
  
## <a name="arguments"></a>Argomenti  
 *transaction_name*  
 **Si applica a:** SQL Server e Database SQL di Azure
 
 Ignorato dal [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. *transaction_name* specifica il nome di una transazione assegnato da un'istruzione BEGIN TRANSACTION precedente. *transaction_name*deve essere conforme alle regole per gli identificatori, ma non può superare i 32 caratteri. *transaction_name* utilizzabile come supporto per migliorare la leggibilità i primi quale istruzione nidificata BEGIN TRANSACTION, COMMIT TRANSACTION è associato.  
  
 *@tran_name_variable*  
 **Si applica a:** SQL Server e Database SQL di Azure  
 
Nome di una variabile definita dall'utente contenente un nome di transazione valido. La variabile deve essere dichiarata con un tipo di dati char, varchar, nchar o nvarchar. Se vengono passati più di 32 caratteri alla variabile vengono utilizzati solo i primi 32 caratteri. Quelli rimanenti vengono troncati.  
  
 DELAYED_DURABILITY  
 **Si applica a:** SQL Server e Database SQL di Azure   

 Opzione che richiede il commit della transazione con durabilità posticipata. La richiesta viene ignorata se il database è stato modificato con `DELAYED_DURABILITY = DISABLED` o `DELAYED_DURABILITY = FORCED`. Vedere l'argomento [controllo della durabilità delle transazioni](../../relational-databases/logs/control-transaction-durability.md) per ulteriori informazioni.  
  
## <a name="remarks"></a>Osservazioni  
 È compito del programmatore di [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguire l'istruzione COMMIT TRANSACTION solo quando tutti i dati a cui la transazione fa riferimento sono logicamente corretti.  
  
 Se la transazione di cui è stato eseguito il commit è una transazione distribuita di [!INCLUDE[tsql](../../includes/tsql-md.md)], l'istruzione COMMIT TRANSACTION attiva l'utilizzo di un protocollo di commit in due fasi in MS DTC per il commit di tutti i server coinvolti nella transazione. Se una transazione locale si estende su due o più database nella stessa istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)], per eseguire il commit di tutti i database coinvolti nella transazione viene utilizzato un commit a due fasi interno.  
  
 Quando viene eseguito in transazioni nidificate, il commit delle transazioni interne non libera risorse o non rende permanenti le modifiche. Queste operazioni vengono eseguite solo durante il commit delle transazioni esterne. Ogni COMMIT TRANSACTION eseguita quando @@TRANCOUNT è maggiore di 1 semplicemente decrementa @@TRANCOUNT di 1. Quando @@TRANCOUNT è uguale a 0, l'intera transazione esterna viene eseguito il commit. Poiché *transaction_name* viene ignorato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)], esecuzione di COMMIT TRANSACTION che fa riferimento il nome di una transazione esterna quando esistono transazioni interne in attesa solo decrementa @@TRANCOUNT di 1.  
  
 Esecuzione di COMMIT TRANSACTION quando @@TRANCOUNT è uguale a 0 genera un errore; non esiste alcuna istruzione BEGIN TRANSACTION corrispondente.  
  
 Non è possibile eseguire il rollback di una transazione dopo l'esecuzione di un'istruzione COMMIT TRANSACTION. Le modifiche dei dati del database sono diventate permanenti.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] incrementa il conteggio delle transazioni all'interno di un'istruzione solo quando il numero di transazioni all'inizio dell'istruzione è uguale a 0.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-committing-a-transaction"></a>A. Esecuzione del commit di una transazione  
**Si applica a:** SQL Server, Database SQL di Azure, Azure SQL Data Warehouse e Parallel Data Warehouse   

Nell'esempio seguente viene eliminato un candidato di processo. Utilizza AdventureWorks. 
  
```   
BEGIN TRANSACTION;   
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;   
COMMIT TRANSACTION;   
```  
  
### <a name="b-committing-a-nested-transaction"></a>B. Esecuzione del commit di una transazione nidificata  
**Si applica a:** SQL Server e Database SQL di Azure    

Nell'esempio seguente viene creata una tabella, viene generata una transazione nidificata su tre livelli e viene quindi eseguito il commit della transazione nidificata. Sebbene ogni `COMMIT TRANSACTION` istruzione presenta un *transaction_name* parametro, non vi è alcuna relazione tra il `COMMIT TRANSACTION` e `BEGIN TRANSACTION` istruzioni. Il *transaction_name* i parametri sono semplicemente leggibilità del codice per consentire al programmatore di verificare che il numero adeguato di commit venga codificato per decrementare `@@TRANCOUNT` su 0 e quindi eseguire il commit della transazione esterna. 
  
```   
IF OBJECT_ID(N'TestTran',N'U') IS NOT NULL  
    DROP TABLE TestTran;  
GO  
CREATE TABLE TestTran (Cola int PRIMARY KEY, Colb char(3));  
GO  
-- This statement sets @@TRANCOUNT to 1.  
BEGIN TRANSACTION OuterTran;  
  
PRINT N'Transaction count after BEGIN OuterTran = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
 
INSERT INTO TestTran VALUES (1, 'aaa');  
 
-- This statement sets @@TRANCOUNT to 2.  
BEGIN TRANSACTION Inner1;  
 
PRINT N'Transaction count after BEGIN Inner1 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
INSERT INTO TestTran VALUES (2, 'bbb');  
  
-- This statement sets @@TRANCOUNT to 3.  
BEGIN TRANSACTION Inner2;  
  
PRINT N'Transaction count after BEGIN Inner2 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
INSERT INTO TestTran VALUES (3, 'ccc');  
  
-- This statement decrements @@TRANCOUNT to 2.  
-- Nothing is committed.  
COMMIT TRANSACTION Inner2;  
 
PRINT N'Transaction count after COMMIT Inner2 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
 
-- This statement decrements @@TRANCOUNT to 1.  
-- Nothing is committed.  
COMMIT TRANSACTION Inner1;  
 
PRINT N'Transaction count after COMMIT Inner1 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
-- This statement decrements @@TRANCOUNT to 0 and  
-- commits outer transaction OuterTran.  
COMMIT TRANSACTION OuterTran;  
  
PRINT N'Transaction count after COMMIT OuterTran = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [OPERAZIONI di COMMIT &#40; Transact-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40; Transact-SQL &#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
