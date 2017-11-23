---
title: CREARE una tabella (SQL grafico) | Documenti Microsoft
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_GRAPH_TSQL
- TABLE
- CREATE_TABLE_TSQL
- NODE
- NODE_TSQL
- AS_NODE
- AS_NODE_TSQL
- EDGE
- EDGE_TSQL
- AS_EDGE
- AS_EDGE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- graph
- SQL graph
- CREATE TABLE SQL graph
- NODE
- EDGE
- SQL graph, CREATE TABLE statement
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 92a586a3612934a4f66e5a616d969454afc87eac
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-table-sql-graph"></a>CREARE una tabella (SQL grafico)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Crea una nuova tabella grafico SQL come un `NODE` o `EDGE` tabella. 
  
> [!NOTE]   
>  Per istruzioni Transact-SQL standard, vedere [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
    AS [ NODE | EDGE ]
[ ; ]  
```  
  
  
## <a name="arguments"></a>Argomenti  
Questo documento elenca solo gli argomenti relativi al grafico SQL. Per un elenco completo e una descrizione di argomenti supportati, vedere [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)

 *database_name*    
 Nome del database in cui è viene creata la tabella. *database_name* deve specificare il nome di un database esistente. Se non specificato, *database_name* impostazioni predefinite per il database corrente. L'account di accesso per la connessione corrente deve essere associata a un ID utente esistente nel database specificato da *database_name*, e all'ID utente deve disporre delle autorizzazioni CREATE TABLE.  
  
 *schema_name*    
 Nome dello schema a cui appartiene la nuova tabella.  
  
 *table_name*    
 È il nome della tabella di nodo o bordo. I nomi di tabella devono seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md). *TABLE_NAME* può contenere un massimo di 128 caratteri, ad eccezione dei nomi di tabella temporanea locale (i nomi preceduti da un solo simbolo di cancelletto (#)) che non può superare i 116 caratteri.  
  
 NODO   
 Crea una tabella di nodo.

 BORDO  
 Crea una tabella edge.  
  
## <a name="remarks"></a>Osservazioni  
Creazione di una tabella temporanea come nodo o una tabella edge non è supportata.  

Creazione di una tabella di nodo o edge come una tabella temporale non è supportata.

Estensione database non è supportato per la tabella di nodo o bordo.

Tabelle di bordo o di nodo non possono essere tabelle esterne (Nessun supporto di polybase per le tabelle di graph). 
  
 
## <a name="examples"></a>Esempi  
  
### <a name="a-create-a-node-table"></a>A. Creare un `NODE` tabella
 Nell'esempio seguente viene illustrato come creare un `NODE` tabella

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>B. Creare un `EDGE` tabella
Gli esempi seguenti mostrano come creare `EDGE` tabelle

```
 CREATE TABLE friends (
    id integer PRIMARY KEY,
    start_date date
 ) AS EDGE;

```

```
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;

```


## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [INSERT (SQL grafico)](../../t-sql/statements/insert-sql-graph.md)]  
 [L'elaborazione con SQL Server 2017 grafico](../../relational-databases/graphs/sql-graph-overview.md)

