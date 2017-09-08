---
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a16d4a7a10eb4f36d0ead2a19f8e37d251e417f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Visualizza il numero di righe, lo spazio su disco riservato e spazio su disco utilizzato per una tabella specifica o per tutte le tabelle in un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database.
  
![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ *database_name* . [ *schema_name* ]. | *schema_name* . ] *table_name*  
 L'una, due o tre parti della tabella da visualizzare. Per due o nomi di tabella composto da tre parti, il nome devono essere racchiusa tra virgolette doppie (""). Utilizzo delle virgolette che racchiudono un nome di tabella composto da una parte è facoltativo. Quando non viene specificato alcun nome di tabella, le informazioni vengono visualizzate per il database corrente.  
  
## <a name="permissions"></a>Permissions  
È richiesta l'autorizzazione VIEW SERVER STATE.
  
## <a name="result-sets"></a>Set di risultati  
Questo è il set di risultati per tutte le tabelle.
  
|Colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|reserved_space|bigint|Spazio totale utilizzato per il database, in KB.|  
|data_space|bigint|Spazio utilizzato per i dati, in KB.|  
|index_space|bigint|Spazio utilizzato per gli indici, in KB.|  
|unused_space|bigint|Spazio che è parte di spazio riservato e non viene utilizzata, in KB.|  
|pdw_node_id|int|Nodo di calcolo che viene utilizzato per i dati.|  
  
Questo è il set di risultati per una tabella.
  
|Colonna|Tipo di dati|Description|Intervallo|  
|------------|---------------|-----------------|-----------|  
|rows|bigint|Numero di righe.||  
|reserved_space|bigint|Spazio totale riservato per l'oggetto, in KB.||  
|data_space|bigint|Spazio utilizzato per i dati, in KB.||  
|index_space|bigint|Spazio utilizzato per gli indici, in KB.||  
|unused_space|bigint|Spazio che è parte di spazio riservato e non viene utilizzata, in KB.||  
|pdw_node_id|int|Nodo di calcolo che viene utilizzato per l'utilizzo dello spazio di report.||  
|distribution_id|int|Distribuzione che viene utilizzata per l'utilizzo dello spazio di report.|Valore è -1 per le tabelle replicate.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowspaceused-basic-syntax"></a>A. Sintassi di base PDW_SHOWSPACEUSED DBCC  
Nell'esempio seguente mostra i diversi modi per visualizzare il numero di righe, riservato spazio su disco e spazio su disco utilizzato dalla tabella FactInternetSales nel [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] database.
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. Mostra lo spazio su disco utilizzato da tutte le tabelle nel database corrente  
 Nell'esempio seguente viene illustrato lo spazio su disco riservato e utilizzato da tutte le tabelle utente e le tabelle di sistema di [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] database.  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>Vedere anche
[Operazione DBCC PDW_SHOWEXECUTIONPLAN &#40; Transact-SQL &#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS &#40; Transact-SQL &#41;](dbcc-pdw-showpartitionstats-transact-sql.md)

  

