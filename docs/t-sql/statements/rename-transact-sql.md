---
title: RENAME (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 11/20/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 0907cfd9-33a6-4fa6-91da-7d6679fee878
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3c08b4d991717d877ca33cd2d136d0dbf0d30483
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="rename-transact-sql"></a>RENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Rinomina una tabella creata dall'utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Rinomina una tabella creata dall'utente o un database in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
> [!NOTE]  
>  Per rinominare un database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare la stored procedure [sp_renamedb &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-renamedb-transact-sql.md). Per rinominare un database nel database SQL di Azure, usare l'istruzione [ALTER DATABASE (database SQL di Azure)](/statements/alter-database-azure-sql-database.md). 
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
-- Rename a table.  
RENAME OBJECT [ :: ]  [ [ database_name .  [schema_name ] ] . ] | [schema_name . ] ] table_name TO new_table_name  
[;]  
  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- Rename a table  
RENAME OBJECT [::] [ [ database_name . [ schema_name ] . ] | [ schema_name . ] ] table_name TO new_table_name  
[;]  
  
-- Rename a database  
RENAME DATABASE [::] database_name TO new_database_name  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 RINOMINARE L'OGGETTO [:]   
          [[*database_name* . [ *schema_name* ]. ] | [ *schema_name* . ]]*table_name* a *new_table_name*  
 **SI APPLICA A:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Modificare il nome di una tabella definita dall'utente. Specificare la tabella da rinominare con un una, due o nome in tre parti.    Specificare la nuova tabella *new_table_name* come nome di una sola parte.  
  
 RINOMINARE IL DATABASE [:]   
          [ *database_name* a *new_database_name*  
 **SI APPLICA A:**  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Modificare il nome di un database definito dall'utente da *database_name* a *new_database_name*.  Non è possibile rinominare un database a uno di questi [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]database nomi riservati:  
  
-   master  
  
-   model  
  
-   msdb  
  
-   tempdb  
  
-   pdwtempdb1  
  
-   pdwtempdb2  
  
-   DWConfiguration  
  
-   DWDiagnostics  
  
-   DWQueue  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa autorizzazione è necessaria per eseguire questo comando:  
  
-   **ALTER** autorizzazione per la tabella  
   
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
  
### <a name="cannot-rename-an-external-table-indexes-or-views"></a>Non è possibile rinominare una tabella esterna, gli indici o viste
È possibile rinominare una tabella esterna, gli indici o viste. Anziché rinominare, è possibile eliminare la tabella esterna, vista o indice e quindi ricrearlo con il nuovo nome.

### <a name="cannot-rename-a-table-in-use"></a>Non è possibile rinominare una tabella in uso  
 È possibile rinominare una tabella o un database mentre è in uso. Ridenominazione di una tabella richiede un blocco esclusivo sulla tabella. Se la tabella è in uso, si potrebbe essere necessario terminare le sessioni che utilizzano la tabella. Per terminare una sessione è possibile utilizzare il comando KILL. Utilizzare KILL con cautela, poiché quando una sessione è terminata. tutte le operazioni di commit eseguito il rollback. Le sessioni in SQL Data Warehouse sono precedute da 'SID'. È necessario includere questo e il numero della sessione quando si richiama il comando KILL. In questo esempio visualizza un elenco delle sessioni attive o inattive e quindi termina la sessione 'SID1234'.  
  
### <a name="views-are-not-updated"></a>Non sono aggiornate  
 Quando si rinomina un database, tutte le viste che utilizzano il nome del database precedente diventerà non valide. Questo vale per le visualizzazioni all'interno e all'esterno del database. Ad esempio, se il database di vendite viene rinominato, una vista che contiene `SELECT * FROM Sales.dbo.table1` diventeranno non validi. Per risolvere questo problema, è possibile evitare di utilizzare nomi in tre parti nelle viste o aggiornare le visualizzazioni per fare riferimento il nuovo nome del database.  
  
 Quando si rinomina una tabella, le viste non vengono aggiornate per il nuovo nome della tabella di riferimento. Ogni vista, all'interno o all'esterno del database, che fa riferimento il nome della tabella precedente non sarà più valido. Per risolvere questo problema, è possibile aggiornare ogni visualizzazione per il nuovo nome della tabella di riferimento.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Ridenominazione di una tabella accetta un blocco condiviso per l'oggetto di DATABASE, un blocco condiviso per l'oggetto SCHEMA e un blocco esclusivo sulla tabella.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-rename-a-database"></a>A. Rinominare un database  
 **Si applica a:** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] solo  
  
 In questo esempio Rinomina il database definito dall'utente AdWorks a AdWorks2.  
  
```  
-- Rename the user defined database AdWorks  
RENAME DATABASE AdWorks to AdWorks2;  
  
```  
  
 Quando si rinomina una tabella, tutti gli oggetti e proprietà associate alla tabella vengono aggiornate per il nuovo nome della tabella di riferimento. Tabella, ad esempio, definizioni, indici, vincoli e vengono aggiornate le autorizzazioni. Non sono aggiornate.  
  
### <a name="b-rename-a-table"></a>B. Rinominare una tabella  
 **SI APPLICA A:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 In questo esempio Rinomina la tabella Customer in Customer1.  
  
```  
-- Rename the customer table  
RENAME OBJECT Customer TO Customer1;  
  
RENAME OBJECT mydb.dbo.Customer TO Customer1;  
```  
  
 Quando si rinomina una tabella, tutti gli oggetti e proprietà associate alla tabella vengono aggiornate per il nuovo nome della tabella di riferimento. Tabella, ad esempio, definizioni, indici, vincoli e vengono aggiornate le autorizzazioni. Non sono aggiornate.  
   
  
### <a name="c-move-a-table-to-a-different-schema"></a>C. Spostare una tabella in un altro schema  
 **SI APPLICA A:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Se si intende spostare l'oggetto in un altro schema, utilizzare [ALTER SCHEMA &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-schema-transact-sql.md). Ad esempio, si sposta l'elemento tabella dallo schema prodotto dello schema dbo.  
  
```  
ALTER SCHEMA dbo TRANSFER OBJECT::product.item;  
```  
  
### <a name="d-terminate-sessions-before-renaming-a-table"></a>D. Terminare le sessioni prima di rinominare una tabella  
 **SI APPLICA A:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 È importante ricordare che è possibile rinominare una tabella mentre è in uso. Un'operazione di ridenominazione di una tabella richiede un blocco esclusivo sulla tabella. Se la tabella è in uso, si potrebbe essere necessario terminare la sessione utilizzando la tabella. Per terminare una sessione è possibile utilizzare il comando KILL. Utilizzare KILL con cautela, poiché quando una sessione è terminata. tutte le operazioni di commit eseguito il rollback. Le sessioni in SQL Data Warehouse sono precedute da 'SID'. È necessario includere questo e il numero della sessione quando si richiama il comando KILL. In questo esempio visualizza un elenco delle sessioni attive o inattive e quindi termina la sessione 'SID1234'.  
  
```  
-- View a list of the current sessions  
SELECT session_id, login_name, status   
FROM sys.dm_pdw_exec_sessions   
WHERE status='Active' OR status='Idle';  
  
-- Terminate a session using the session_id.  
KILL 'SID1234';  
```  
  
  
