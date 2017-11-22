---
title: ALTER DATABASE (SQL Azure Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: "20"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.openlocfilehash: 758f303efd228d806db53075f92cc8dd4664d40b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (SQL Azure Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Modifica il nome, dimensioni massime o l'obiettivo di servizio per un database.  
  
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

Modifica nome = *new_database_name*  
Rinomina il database con il nome specificato come *new_database_name*.  
  
MAXSIZE  
Il valore predefinito è 10.240 GB (10 TB).  

**Si applica a:** ottimizzato per il livello di prestazioni di elasticità

La dimensione massima consentita per il database. Il database non può aumentare oltre MAXSIZE. 

**Si applica a:** ottimizzato per il livello di prestazioni di calcolo

La dimensione massima consentita per i dati del rowstore nel database. Dati archiviati in tabelle rowstore, deltastore di un indice columnstore o un indice non cluster in un indice columnstore cluster non possono superare MAXSIZE.  I dati compattati nel formato columnstore non dispone di un limite di dimensione e non è influenzati dal valore MAXSIZE. 
  
SERVICE_OBJECTIVE  
Specifica il livello di prestazioni. Per ulteriori informazioni su obiettivi di servizio per [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], vedere [livelli di prestazioni](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
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
  
