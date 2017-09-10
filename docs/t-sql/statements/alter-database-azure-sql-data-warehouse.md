---
title: ALTER DATABASE (SQL Azure Data Warehouse) | Documenti Microsoft
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/03/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b5e328da952c853409437f7c3a4993f17022de22
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (SQL Azure Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Modifica il nome, dimensioni massime o l'obiettivo di servizio per un database.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 | 153600 | 204800 | 245760 } GB  
    | SERVICE_OBJECTIVE = { 'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000'}  
```  
  
## <a name="arguments"></a>Argomenti  
*database_name*  
Specifica il nome del database da modificare.  

Modifica nome = *new_database_name*  
Rinomina il database con il nome specificato come *new_database_name*.  
  
MAXSIZE  
Le dimensioni massime del database possono raggiungere. L'impostazione di questo valore impedisce la crescita delle dimensioni del database oltre il set di dimensioni. Il valore predefinito *MAXSIZE* quando non viene specificato è 10240 GB (10 TB). Altri valori possibili sono compresi da 250 GB fino a 240 TB.  
  
SERVICE_OBJECTIVE  
Specifica il livello di prestazioni. Per ulteriori informazioni su obiettivi di servizio per [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], vedere [scalabilità delle prestazioni in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-manage-compute-overview/).  
  
## <a name="permissions"></a>Permissions  
Queste autorizzazioni sono necessarie:  
  
-   Account di accesso dell'entità di livello server (quello creato dal processo di provisioning), o  
  
-   Membro del `dbmanager` ruolo del database.  
  
Il proprietario del database non è possibile modificare il database a meno che il proprietario è un membro del `dbmanager` ruolo.  
  
## <a name="general-remarks"></a>Osservazioni generali  
Il database corrente deve essere un database diverso da quello che stanno diffondendo, pertanto **ALTER deve essere eseguito durante la connessione al database master**.  
  
SQL Data Warehouse è impostato su 130 COMPATIBILITY_LEVEL e non può essere modificato. Per ulteriori informazioni, vedere [migliorate le prestazioni delle Query con 130 livello di compatibilità in Database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
Per ridurre le dimensioni di un database, utilizzare [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
Per eseguire ALTER DATABASE, il database deve essere online e non può essere in stato di sospensione.  
  
L'istruzione ALTER DATABASE deve eseguire in modalità autocommit, ovvero la modalità di gestione delle transazioni predefinita. Viene impostato nelle impostazioni di connessione.  
  
L'istruzione ALTER DATABASE non può essere parte di una transazione definita dall'utente.

È possibile modificare le regole di confronto del database.  
  
## <a name="examples"></a>Esempi  
Prima di eseguire questi esempi, verificare che il database a cui che stanno diffondendo non è il database corrente. Il database corrente deve essere un database diverso da quello che stanno diffondendo, pertanto **ALTER deve essere eseguito durante la connessione al database master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Modificare il nome del database  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>B. Modificare le dimensioni massime per il database  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>C. Modificare il livello di prestazioni  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>D. Modificare le dimensioni massime e il livello di prestazioni  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>Vedere anche  
[CREATE DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[elenco SQL Data Warehouse di argomenti di riferimento](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
