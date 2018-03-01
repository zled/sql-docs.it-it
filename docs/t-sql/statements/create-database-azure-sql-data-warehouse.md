---
title: CREATE DATABASE (Azure SQL Data Warehouse) | Microsoft Docs
ms.custom: 
ms.date: 02/14/20178
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
author: barbkess
ms.author: barbkess
manager: craigg
ms.openlocfilehash: 3a802dc74793ef79ca35b177b4416d9464a8c34f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="create-database-azure-sql-data-warehouse"></a>CREATE DATABASE (Azure SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Crea un nuovo database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 
          250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 
        | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 
        | 153600 | 204800 | 245760 
      } GB ,
    ]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 
         'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' 
        | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' 
        | 'DW1000c' | 'DW1500c' | 'DW2000c' | 'DW2500c' | 'DW3000c' | 'DW5000c' 
        | 'DW6000c' | 'DW7500c' | 'DW10000c' | 'DW15000c' | 'DW30000c'
    }  
)  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
*database_name*  
Nome del nuovo database. Questo nome deve essere univoco in SQL Server, che può ospitare sia database [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sia database [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Deve anche rispettare le regole [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per gli identificatori. Per altre informazioni, vedere [Identificatori](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*nome_regole_di_confronto*  
Specifica le regole di confronto predefinite per il database. È possibile usare nomi di regole di confronto di Windows o SQL. Se non vengono specificate, al database vengono assegnate le regole di confronto predefinite, ovvero SQL_Latin1_General_CP1_CI_AS.  
  
Per altre informazioni sui nomi delle regole di confronto Windows e SQL, vedere [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
*EDITION*  
Specifica il livello del servizio del database. Per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] usare 'datawarehouse'.  
  
*MAXSIZE*  
Il valore predefinito è 245.760 GB (240 TB).  

**Si applica a:** livello di prestazioni Ottimizzato per l'elasticità

Dimensioni massime consentite per il database. Le dimensioni del database non possono superare il valore di MAXSIZE. 

**Si applica a:** livello di prestazioni Ottimizzato per il calcolo

Dimensioni massime consentite per i dati rowstore nel database. Le dimensioni dei dati archiviati nelle tabelle rowstore, nel deltastore di un indice columnstore o in un indice non cluster in un indice columnstore cluster non possono superare MAXSIZE.  I dati compressi in formato columnstore non hanno un limite di dimensioni e non sono limitati dal valore MAXSIZE.
  
SERVICE_OBJECTIVE  
Specifica il livello di prestazioni. Per altre informazioni sugli obiettivi di servizio per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], vedere [Livelli di prestazioni](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="general-remarks"></a>Osservazioni generali  
Usare [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md) per visualizzare le proprietà del database.  
  
Usare [ALTER DATABASE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) per modificare le dimensioni massime o i valori degli obiettivi di servizio in un secondo momento.   

SQL Data Warehouse è impostato su COMPATIBILITY_LEVEL 130 e non può essere modificato. Per altri dettagli, vedere [Improved Query Performance with Compatibility Level 130 in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/) (Prestazioni di query migliorate con Compatibility Level 130 nel database SQL di Azure).
  
## <a name="permissions"></a>Autorizzazioni  
Autorizzazioni necessarie:  
  
-   Accesso principale di livello server (creato dal processo di provisioning) oppure  
  
-   Membro del ruolo del database `dbmanager`.  
  
## <a name="error-handling"></a>Gestione degli errori  
Se le dimensioni del database raggiungono il valore MAXSIZE, viene visualizzato il codice di errore 40544. In questo caso non è possibile inserire e aggiornare dati, né creare nuovi oggetti quali tabelle, stored procedure, viste e funzioni. È ancora possibile leggere ed eliminare dati, troncare tabelle, eliminare tabelle e indici e ricompilare indici. È quindi possibile aggiornare MAXSIZE a un valore maggiore delle dimensioni correnti del database o eliminare alcuni dati per liberare spazio di archiviazione. Potrebbe verificarsi un ritardo di quindici minuti prima di poter inserire nuovi dati.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
È necessario essere connessi al database master per creare un nuovo database.  
  
L'istruzione `CREATE DATABASE` deve essere l'unica istruzione in un batch [!INCLUDE[tsql](../../includes/tsql-md.md)].

Non è possibile modificare le regole di confronto del database dopo la creazione del database stesso.   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. Esempio semplice  
Esempio semplice per la creazione di un database del data warehouse. Crea il database con le dimensioni massime più ridotte, ovvero 10240 GB, le regole di confronto predefinite, ovvero SQL_Latin1_General_CP1_CI_AS e la potenza di elaborazione più ridotta, pari a DW100.  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>B. Creare un database del data warehouse con tutte le opzioni  
Esempio di creazione di un data warehouse di 10 TB usando tutte le opzioni.  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE &#40;Azure SQL Data Warehouse&#40;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)
[CREATE TABLE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) 
[DROP DATABASE &#40;Transact-SQL&#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  

