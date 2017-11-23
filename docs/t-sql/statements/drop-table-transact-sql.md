---
title: DROP TABLE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_TABLE_TSQL
- DROP TABLE
dev_langs: TSQL
helpviewer_keywords:
- removing indexes
- table removal [SQL Server]
- deleting indexes
- dropping data
- deleting tables
- dropping indexes
- removing constraints
- removing permissions
- DROP TABLE statement
- removing tables
- deleting triggers
- removing data
- dropping tables
- deleting permissions
- dropping triggers
- deleting constraints
- removing triggers
- deleting data
- dropping constraints
- dropping permissions
ms.assetid: 0b6f2b6f-3aa3-4767-943f-43df3c3c5cfd
caps.latest.revision: "61"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: df9843e4b72c6a8092756725d1d4b3f96eefec74
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="drop-table-transact-sql"></a>DROP TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove una o più definizioni di tabella e tutti i dati, gli indici, i trigger, i vincoli e le specifiche di autorizzazione associate alle tabelle in questione. Le viste o stored procedure che fa riferimento alla tabella eliminata devono essere eliminate in modo esplicito tramite [DROP VIEW](../../t-sql/statements/drop-view-transact-sql.md) o [DROP PROCEDURE](../../t-sql/statements/drop-procedure-transact-sql.md). Per segnalare le dipendenze in una tabella, utilizzare [Sys.dm sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP TABLE [ IF EXISTS ] [ database_name . [ schema_name ] . | schema_name . ]  
table_name [ ,...n ]  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database in cui è stata creata la tabella.  
  
 Il database SQL di Windows Azure supporta il formato del nome in tre parti, nome_database.[nome_schema].nome_oggetto, quando nome_database è il database corrente oppure nome_database è tempdb e nome_oggetto inizia con #. Il database SQL di Windows Azure non supporta i nomi composti da quattro parti.  
  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale la tabella solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella.  
  
 *table_name*  
 Nome della tabella da rimuovere.  
  
## <a name="remarks"></a>Osservazioni  
 Non è possibile utilizzare l'istruzione DROP TABLE per eliminare una tabella a cui fa riferimento un vincolo FOREIGN KEY. È prima necessario eliminare il vincolo FOREIGN KEY o la tabella di riferimento. Se con la stessa istruzione DROP TABLE si eliminano sia la tabella di riferimento che la tabella che contiene la chiave primaria, è necessario indicare la tabella di riferimento per prima nell'elenco.  
  
 Si possono eliminare più tabelle in qualsiasi database. Se una tabella da eliminare fa riferimento alla chiave primaria di un'altra tabella, anch'essa da eliminare, è necessario indicare la tabella di riferimento con la chiave esterna prima della tabella contenente la chiave primaria a cui fa riferimento la prima tabella.  
  
 Con l'eliminazione di una tabella, le regole o i valori predefiniti della tabella vengono disassociati e i vincoli o trigger associati alla tabella vengono eliminati automaticamente. Se la tabella viene ricreata, è necessario associare nuovamente le regole e i valori predefiniti appropriati, ricreare eventuali trigger e aggiungere tutti i vincoli necessari.  
  
 Se si elimina tutte le righe in una tabella con DELETE *tablename* o utilizzare l'istruzione TRUNCATE TABLE, la tabella esiste finché viene eliminato.  
  
 Le tabelle e gli indici di grandi dimensioni che utilizzano più di 128 extent vengono eliminati in due fasi distinte: logica e fisica. Nella fase logica, le unità di allocazione esistenti utilizzate dalla tabella vengono contrassegnate per la deallocazione e bloccate fino al completamento del commit della transazione. Nella fase fisica, le pagine IAM contrassegnate per la deallocazione vengono eliminate fisicamente in più batch.  
  
 Se si elimina una tabella che contiene una colonna VARBINARY (MAX) con l'attributo FILESTREAM, non verrà rimosso alcun dato archiviato nel file system.  
  
> [!IMPORTANT]  
>  DROP TABLE e CREATE TABLE non devono essere eseguiti nella stessa tabella nello stesso batch. In caso contrario, è possibile che si verifichi un errore imprevisto.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER per lo schema a cui appartiene la tabella, l'autorizzazione CONTROL per la tabella o l'appartenenza al ruolo predefinito del database **db_ddladmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-table-in-the-current-database"></a>A. Eliminazione di una tabella dal database corrente  
 Nell'esempio seguente vengono eliminati la tabella `ProductVendor1` e i dati e gli indici corrispondenti dal database corrente.  
  
```  
DROP TABLE ProductVendor1 ;  
```  
  
### <a name="b-dropping-a-table-in-another-database"></a>B. Eliminazione di una tabella da un database diverso da quello corrente  
 Nell'esempio seguente viene eliminata la tabella `SalesPerson2` nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. È possibile eseguire questo esempio da qualsiasi database nell'istanza del server.  
  
```  
DROP TABLE AdventureWorks2012.dbo.SalesPerson2 ;  
```  
  
### <a name="c-dropping-a-temporary-table"></a>C. Eliminazione di una tabella temporanea  
 Nell'esempio seguente viene creata una tabella temporanea, ne viene controllata l'esistenza, quindi la tabella viene eliminata e viene eseguito un ulteriore controllo dell'esistenza. Questo esempio viene utilizzato il **IF EXISTS** sintassi che è disponibile a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
CREATE TABLE #temptable (col1 int);  
GO  
INSERT INTO #temptable  
VALUES (10);  
GO  
SELECT * FROM #temptable;  
GO  
IF OBJECT_ID(N'tempdb..#temptable', N'U') IS NOT NULL   
DROP TABLE #temptable;  
GO  
--Test the drop.  
SELECT * FROM #temptable;  
  
```  
  
### <a name="d-dropping-a-table-using-if-exists"></a>D. Eliminazione di una tabella utilizzando IF EXISTS  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 L'esempio seguente crea una tabella denominata T1. La seconda istruzione elimina quindi la tabella. La terza istruzione non esegue alcuna azione perché la tabella è già stata eliminata, ma ciò non causa un errore.  
  
```  
CREATE TABLE T1 (Col1 int);  
GO  
DROP TABLE IF EXISTS T1;  
GO  
DROP TABLE IF EXISTS T1;  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [Istruzione TRUNCATE TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)   
 [DROP VIEW &#40; Transact-SQL &#41;](../../t-sql/statements/drop-view-transact-sql.md)   
 [DROP PROCEDURE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
