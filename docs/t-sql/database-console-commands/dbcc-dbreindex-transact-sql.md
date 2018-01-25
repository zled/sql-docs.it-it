---
title: DBCC DBREINDEX (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC DBREINDEX
- DBREINDEX_TSQL
- DBREINDEX
- DBCC_DBREINDEX_TSQL
dev_langs: TSQL
helpviewer_keywords:
- index rebuilding [SQL Server]
- rebuilding indexes
- dynamic index rebuilding [SQL Server]
- DBCC DBREINDEX statement
ms.assetid: 6e929d09-ccb5-4855-a6af-b616022bc8f6
caps.latest.revision: "52"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 991c16eea9a651270ca299e72cafbc822465a9b3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dbreindex-transact-sql"></a>DBCC DBREINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Ricompila uno o più indici per una tabella nel database specificato.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilizzare [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) invece.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC DBREINDEX   
(   
    table_name   
    [ , index_name [ , fillfactor ] ]  
)  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *table_name*  
 Nome della tabella che contiene l'indice o gli indici specificati da ricompilare. I nomi di tabella devono seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md)*.*  
  
 *index_name*  
 Nome dell'indice da ricompilare. I nomi degli indici devono essere conformi alle regole per gli identificatori. Se *index_name* è specificato, *table_name* deve essere specificato. Se *index_name* non è specificato o è "", vengono ricompilati tutti gli indici per la tabella.  
  
 *fillfactor*  
 Percentuale di spazio su ogni pagina di indice per l'archiviazione di dati quando l'indice viene creato o ricompilato. *fattore di riempimento* sostituisce il fattore di riempimento quando l'indice è stato creato, diventando il nuovo valore predefinito per l'indice e per altri indici non cluster ricompilati perché viene ricompilato un indice cluster.  
 Quando *fillfactor* è 0, DBCC DBREINDEX utilizza il valore del fattore di riempimento specificato per ultimo per l'indice. Questo valore viene archiviato nel **Sys. Indexes** vista del catalogo.   
 Se *fillfactor* è specificato, *table_name* e *index_name* deve essere specificato. Se *fillfactor* non viene specificato, il fattore di riempimento predefinito, 100, viene utilizzato. Per altre informazioni, vedere [Specificare un fattore di riempimento per un indice](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 WITH NO_INFOMSGS  
 Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="remarks"></a>Osservazioni  
DBCC DBREINDEX ricompila un indice di tabella o tutti gli indici definiti per una tabella. Quando è supportata la ricostruzione dinamica di un indice, è possibile ricostruire gli indici che applicano vincoli PRIMARY KEY o UNIQUE senza dover eliminare o ricreare tali vincoli. Ciò significa che un indice può essere ricostruito anche se la struttura di una tabella o i relativi vincoli non sono noti. Questa situazione potrebbe verificarsi dopo una copia bulk di dati in una tabella.

L'istruzione DBCC DBREINDEX può ricompilare tutti gli indici di una tabella in un'unica istruzione. Ciò risulta più semplice rispetto alla specificazione di più istruzioni DROP INDEX e CREATE INDEX a livello di codice. Poiché l'intera operazione viene eseguita da un'unica istruzione, DBCC DBREINDEX risulta automaticamente un'istruzione atomica. Le singole istruzioni DROP INDEX e CREATE INDEX invece risultano atomiche solo quando vengono inserite in una transazione. L'istruzione DBCC DBREINDEX è inoltre caratterizzata da un maggior numero di ottimizzazioni rispetto alle singole istruzioni DROP INDEX e CREATE INDEX.

A differenza di DBCC INDEXDEFRAG oppure di ALTER INDEX con l'opzione REORGANIZE, l'istruzione DBCC DBREINDEX viene eseguita in modalità offline. In caso di ricostruzione di un indice non cluster, viene mantenuto attivo un blocco condiviso sulla tabella in questione per l'intera durata dell'operazione. Ciò impedisce che vengano apportate modifiche alla tabella. In caso di ricostruzione di un indice cluster, viene mantenuto attivo un blocco esclusivo a livello di tabella. Ciò impedisce qualsiasi tipo di accesso alla tabella e la rende effettivamente offline. Per eseguire la ricompilazione di un indice in modalità online oppure per controllare il grado di parallelismo durante l'operazione di ricompilazione dell'indice, utilizzare l'istruzione ALTER INDEX REBUILD con l'opzione ONLINE.

Per ulteriori informazioni sulla selezione di un metodo per ricompilare o riorganizzare un indice, vedere [riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md) .
  
## <a name="restrictions"></a>Restrizioni  
DBCC DBREINDEX non è utilizzabile con gli oggetti seguenti:
-   Tabelle di sistema  
-   Indici spaziali  
-   indici columnstore ottimizzati memoria xVelocity  
  
## <a name="result-sets"></a>Set di risultati  
A meno che l'opzione NO_INFOMSGS non sia specificata (è necessario specificare il nome della tabella), DBCC DBREINDEX restituisce sempre quanto segue:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Autorizzazioni  
Chiamante deve essere proprietario della tabella o essere un membro del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database, o **db_ddladmin** ruolo predefinito del database.
  
## <a name="examples"></a>Esempi  
### <a name="a-rebuilding-an-index"></a>A. Ricompilazione di un indice  
Nell'esempio seguente viene ricompilato l'indice cluster `Employee_EmployeeID` con un fattore di riempimento pari a `80` nella tabella `Employee` del database `AdventureWorks`.
  
```sql  
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', PK_Employee_BusinessEntityID,80);  
GO  
```  
  
### <a name="b-rebuilding-all-indexes"></a>B. Ricompilazione di tutti gli indici  
Nell'esempio seguente vengono ricompilati tutti gli indici nella tabella `Employee` del database `AdventureWorks` in base a un fattore di riempimento il cui valore è `70`.
  
```sql
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', ' ', 70);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
  

