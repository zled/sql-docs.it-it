---
title: ALTER DATABASE (Azure SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 02/15/2018
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2e89ba1dde52c1b5cb919ff34181d7ca723b6c61
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (Azure SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Modifica il nome, la dimensione massima o l'obiettivo di servizio per un database.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 
            250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 
          | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 
          | 92160 | 102400 | 153600 | 204800 | 245760 
      } GB  
      | SERVICE_OBJECTIVE = { 
            'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' 
          | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' 
          | 'DW3000' | 'DW6000' | 'DW1000c' | 'DW1500c' | 'DW2000c' 
          | 'DW2500c' | 'DW3000c' | 'DW5000c' | 'DW6000c' | 'DW7500c' 
          | 'DW10000c' | 'DW15000c' | 'DW30000c'
      }  
```  
  
## <a name="arguments"></a>Argomenti  
*database_name*  
Specifica il nome del database da modificare.  

MODIFY NAME = *new_database_name*  
Rinomina il database con il nome specificato come *new_database_name*.  
  
MAXSIZE  
Il valore predefinito è 245.760 GB (240 TB).  

**Si applica a:** livello di prestazioni Ottimizzato per l'elasticità

Dimensioni massime consentite per il database. Le dimensioni del database non possono superare il valore di MAXSIZE. 

**Si applica a:** livello di prestazioni Ottimizzato per il calcolo

Dimensioni massime consentite per i dati rowstore nel database. Le dimensioni dei dati archiviati nelle tabelle rowstore, nel deltastore di un indice columnstore o in un indice non cluster in un indice columnstore cluster non possono superare MAXSIZE.  I dati compressi in formato columnstore non hanno un limite di dimensioni e non sono limitati dal valore MAXSIZE. 
  
SERVICE_OBJECTIVE  
Specifica il livello di prestazioni. Per altre informazioni sugli obiettivi di servizio per [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], vedere [Livelli di prestazioni](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="permissions"></a>Autorizzazioni  
Richiede le autorizzazioni seguenti:  
  
-   Accesso principale di livello server (creato dal processo di provisioning) oppure  
  
-   Membro del ruolo del database `dbmanager`.  
  
Il proprietario del database può modificare il database solo se è un membro del ruolo `dbmanager`.  
  
## <a name="general-remarks"></a>Osservazioni generali  
Poiché il database corrente deve essere un database diverso da quello in fase di modifica, **ALTER deve essere eseguito durante la connessione al database master**.  
  
SQL Data Warehouse è impostato su COMPATIBILITY_LEVEL 130 e non può essere modificato. Per altri dettagli, vedere [Improved Query Performance with Compatibility Level 130 in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/) (Prestazioni di query migliorate con Compatibility Level 130 nel database SQL di Azure).
  
Per ridurre le dimensioni di un database, usare [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
Per eseguire ALTER DATABASE, il database deve essere online e non può essere in pausa.  
  
L'istruzione ALTER DATABASE deve essere eseguita in modalità autocommit, ovvero la modalità di gestione delle transazioni predefinita. Questa opzione è specificata nelle impostazioni di connessione.  
  
L'istruzione ALTER DATABASE non può essere parte di una transazione definita dall'utente.

Le regole di confronto del database non possono essere modificate.  
  
## <a name="examples"></a>Esempi  
Prima di eseguire questi esempi, verificare che il database da modificare non sia il database corrente. Poiché il database corrente deve essere un database diverso da quello in fase di modifica, **ALTER deve essere eseguito durante la connessione al database master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Modificare il nome del database  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>B. Modificare la dimensione massima del database  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>C. Modificare il livello di prestazioni  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>D. Modificare la dimensione massima e il livello di prestazioni  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>Vedere anche  
[CREATE DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[Elenco degli argomenti di riferimento di SQL Data Warehouse](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
