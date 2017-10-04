---
title: CREARE DATABASE (SQL Azure Data Warehouse) | Documenti Microsoft
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/14/2017
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
ms.assetid: 42819b93-b757-4b2c-8179-d4be3c512c19
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a178756610f0d0e463c21a2a62a287ada6c863a1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-azure-sql-data-warehouse"></a>CREARE DATABASE (SQL Azure Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Crea un nuovo database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 | 153600 | 204800 | 245760 } GB ,]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' }  
)  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
*database_name*  
Nome del nuovo database. Questo nome deve essere univoco in SQL server, che possono ospitare entrambi [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] database e [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] database e rispettare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] regole per gli identificatori. Per ulteriori informazioni, vedere [identificatori](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*collation_name*  
Specifica le regole di confronto predefinite per il database. È possibile usare nomi di regole di confronto di Windows o SQL. Se non specificato, il database vengono assegnate le regole di confronto predefinito, ovvero SQL_Latin1_General_CP1_CI_AS.  
  
Per ulteriori informazioni sui nomi delle regole di confronto Windows e SQL, vedere [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
*EDIZIONE*  
Specifica il livello del servizio del database. Per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] utilizzare 'datawarehouse'.  
  
*MAXSIZE*  
Le dimensioni massime del database possono raggiungere. L'impostazione di questo valore impedisce la crescita delle dimensioni del database oltre il set di dimensioni. Il valore predefinito *MAXSIZE* quando non viene specificato è 10240 GB (10 TB).  Altri valori possibili sono compresi da 250 GB fino a 240 TB.  
  
SERVICE_OBJECTIVE  
Specifica il livello di prestazioni. Per ulteriori informazioni su obiettivi di servizio per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], vedere [scalabilità delle prestazioni in SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-performance-scale/).  
  
## <a name="general-remarks"></a>Osservazioni generali  
Utilizzare [DATABASEPROPERTYEX &#40; Transact-SQL &#41; ](../../t-sql/functions/databasepropertyex-transact-sql.md) per visualizzare le proprietà del database.  
  
Utilizzare [ALTER DATABASE &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) per modificare le dimensioni massime, o valori obiettivo di servizio in un secondo momento.   

SQL Data Warehouse è impostato su 130 COMPATIBILITY_LEVEL e non può essere modificato. Per ulteriori informazioni, vedere [migliorate le prestazioni delle Query con 130 livello di compatibilità in Database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
## <a name="permissions"></a>Permissions  
Autorizzazioni necessarie:  
  
-   Server livello principale account di accesso, creato dal processo di provisioning, o  
  
-   Membro del `dbmanager` ruolo del database.  
  
## <a name="error-handling"></a>Gestione degli errori  
Se le dimensioni del database raggiungono il valore MAXSIZE verrà visualizzato il codice di errore 40544. In questo caso, è possibile inserire e aggiornare i dati o creare nuovi oggetti (ad esempio tabelle, stored procedure, viste e funzioni). È possibile comunque leggere ed eliminare i dati, troncare tabelle, eliminare tabelle e indici e ricompilare gli indici. È quindi possibile aggiornare MAXSIZE a un valore maggiore delle dimensioni correnti del database o eliminare alcuni dati per liberare spazio di archiviazione. Potrebbe verificarsi un ritardo di quindici minuti prima di poter inserire nuovi dati.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
È necessario essere connessi al database master per creare un nuovo database.  
  
L'istruzione `CREATE DATABASE` deve essere l'unica istruzione in un batch [!INCLUDE[tsql](../../includes/tsql-md.md)].

È possibile modificare le regole di confronto del database dopo la creazione del database.   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>Esempi:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. Esempio semplice  
Un esempio semplice per la creazione di un database del data warehouse. Verrà creato il database con dimensioni massime più piccolo che è la potenza di calcolo più piccolo che è DW100 GB 10240 e regole di confronto predefinite, ovvero SQL_Latin1_General_CP1_CI_AS.  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>B. Creare un database del data warehouse con tutte le opzioni  
Un esempio di creazione di un un data warehouse di 10 TB utilizzando tutte le opzioni.  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE &#40; Azure SQL Data Warehouse &#40; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) 
 [Crea una tabella &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/create-table-azure-sql-data-warehouse.md)  
 [DROP DATABASE &#40; Transact-SQL &#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  


