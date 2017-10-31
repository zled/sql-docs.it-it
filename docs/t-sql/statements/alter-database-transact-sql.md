---
title: ALTER DATABASE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_TSQL
- ALTER DATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- databases [SQL Server], modifying
- ALTER DATABASE statement
- databases [SQL Server], renaming
- renaming databases
- database modifications [SQL Server]
- ALTER DATABASE statement, syntax described
- database names [SQL Server], ALTER DATABASE
- modifying databases
- collations [SQL Server], modifying
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 15f8affd-8f39-4021-b092-0379fc6983da
caps.latest.revision: 282
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 6c498acedd2821127137ec6be1bd2e04e6b3da09
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="alter-database-transact-sql"></a>ALTER DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di modificare un database oppure i file e i filegroup associati al database. Consente di aggiungere o rimuovere file e filegroup in un database, modificare gli attributi di un database oppure dei relativi file e filegroup, modificare le regole di confronto e impostare le opzioni del database. Non è possibile modificare snapshot di database. Per modificare le opzioni di database associate alla replica, utilizzare [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
   
 A causa della lunghezza, la sintassi di ALTER DATABASE è separata negli argomenti seguenti:  
  
 ALTER DATABASE  
 L'argomento corrente fornisce la sintassi per la modifica del nome e le regole di confronto di un database.  
  
 [Opzioni ALTER DATABASE File e Filegroup](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
 Fornisce la sintassi per l'aggiunta e la rimozione di file e filegroup da un database e per la modifica degli attributi di file e filegroup.  
  
 [Opzioni ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
 Fornisce la sintassi per la modifica degli attributi di un database utilizzando le opzioni SET di ALTER DATABASE.  
  
 [Database ALTER DATABASE Mirroring](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)  
 Include la sintassi per le opzioni SET di ALTER DATABASE relative al mirroring del database.  
  
 [ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)  
 Fornisce la sintassi per la [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] opzioni di ALTER DATABASE per la configurazione di un database secondario in una replica secondaria di un gruppo di disponibilità Always On.  
  
 [Livello di compatibilità di ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
 Fornisce la sintassi per le opzioni SET di ALTER DATABASE relative ai livelli di compatibilità del database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
Database SQL di Azure, vedere [ALTER DATABASE &#40; Database SQL di Azure &#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
Per Azure SQL Data Warehouse, vedere [ALTER DATABASE &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
Per Parallel Data Warehouse, vedere [ALTER DATABASE &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).
  
## <a name="syntax"></a>Sintassi  
  
```  
-- SQL Server Syntax  
ALTER DATABASE { database_name  | CURRENT }  
{  
    MODIFY NAME = new_database_name   
  | COLLATE collation_name  
  | <file_and_filegroup_options>  
  | <set_database_options>  
}  
[;]  
  
<file_and_filegroup_options >::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  
  
<set_database_options>::=  
  <optionspec>::=   
  <auto_option> ::=   
  <change_tracking_option> ::=  
  <cursor_option> ::=   
  <database_mirroring_option> ::=   
  <date_correlation_optimization_option> ::=  
  <db_encryption_option> ::=  
  <db_state_option> ::=  
  <db_update_option> ::=  
  <db_user_access_option> ::=  <delayed_durability_option> ::=  <external_access_option> ::=  
  <FILESTREAM_options> ::=  
  <HADR_options> ::=    
  <parameterization_option> ::=  
  <query_store_options> ::=  
  <recovery_option> ::=   
  <service_broker_option> ::=  
  <snapshot_option> ::=  
  <sql_option> ::=   
  <termination> ::=  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database da modificare.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 CURRENT  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che il database corrente in uso deve essere modificato.  
  
 Modifica nome  **=**  *new_database_name*  
 Rinomina il database con il nome specificato come *new_database_name*.  
  
 COLLATE *collation_name*  
 Specifica le regole di confronto per il database. *collation_name* può essere un nome di regole di confronto Windows o un nome di regole di confronto SQL. Se omesso, al database vengono assegnate le regole di confronto dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Quando si creano database con regole di confronto diverse da quelle predefinite, i dati nel database rispettano sempre le regole di confronto specificate. Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quando si crea un database indipendente, le informazioni del catalogo interno vengono mantenute usando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , regole di confronto predefinite **Latin1_General_100_CI_AS_WS_KS_SC**.  
  
 Per ulteriori informazioni sui nomi delle regole di confronto Windows e SQL, vedere [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 **\<delayed_durability_option >:: =**  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per ulteriori informazioni vedere [opzioni ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) e [controllare la durabilità delle transazioni](../../relational-databases/logs/control-transaction-durability.md).  
  
 **\<file_and_filegroup_options >:: =**  
 Per ulteriori informazioni, vedere [File ALTER DATABASE e le opzioni di Filegroup &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per rimuovere un database, utilizzare [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Per ridurre le dimensioni di un database, utilizzare [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
 L'istruzione ALTER DATABASE deve essere eseguita in modalità autocommit (modalità predefinita di gestione delle transazioni) e non è consentita in una transazione esplicita o implicita.  
  
 Lo stato di un file di database, ad esempio online o offline, viene mantenuto indipendentemente dallo stato del database. Per ulteriori informazioni, vedere [degli stati di File](../../relational-databases/databases/file-states.md). Lo stato dei file all'interno di un filegroup determina la disponibilità dell'intero filegroup. Un filegroup è disponibile se tutti i file in esso inclusi sono online. Se un filegroup è offline, qualsiasi tentativo di accesso al filegroup tramite un'istruzione SQL avrà esito negativo e verrà generato un errore. Per la compilazione di piani delle query per istruzioni SELECT, Query Optimizer evita gli indici non cluster e le viste indicizzate presenti in filegroup offline. Ciò consente la corretta esecuzione di tali istruzioni. Se tuttavia il filegroup offline contiene l'indice cluster o heap della tabella di destinazione, l'istruzione SELECT avrà esito negativo, così come tutte le istruzioni INSERT, UPDATE o DELETE che implicano la modifica di una tabella tramite un indice incluso in un filegroup offline.  
  
 Quando un database è nello stato RESTORING, la maggior parte delle istruzioni ALTER DATABASE avrà esito negativo. Un'alternativa consiste nell'impostare le opzioni di mirroring del database. Lo stato RESTORING può essere impostato durante un'operazione di ripristino attiva o quando un'operazione di ripristino di un database o di un file di log ha esito negativo a causa di un file di backup danneggiato.  
  
 La cache dei piani per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene cancellata quando si imposta una delle opzioni seguenti.  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY|PAGE_VERIFY|  
  
 La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni di manutenzione o riconfigurazione del database". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.  
  
 La cache delle procedure viene inoltre scaricata negli scenari seguenti:  
  
-   L'opzione AUTO_CLOSE di un database è impostata su ON. Se il database non viene utilizzato da alcuna connessione utente, neanche come riferimento, tramite l'attività in background viene effettuato il tentativo di chiusura e di arresto automatici del database.  
  
-   Vengono eseguite diverse query su un database contenente opzioni predefinite. Successivamente, il database viene eliminato.  
  
-   Viene eliminato uno snapshot del database per un database di origine.  
  
-   Viene ricompilato correttamente il log delle transazioni per un database.  
  
-   Viene ripristinato un backup del database.  
  
-   Viene scollegato un database.  
  
## <a name="changing-the-database-collation"></a>Modifica delle regole di confronto del database  
 Prima di applicare regole di confronto diverse a un database, verificare che siano soddisfatte le condizioni seguenti:  
  
-   Nessun altro utente sta utilizzando il database.  
  
-   Nessun oggetto associato a schema dipende dalle regole di confronto del database.  
  
     Se gli oggetti seguenti, che dipendono da regole di confronto del database, esistono nel database, l'istruzione ALTER DATABASE*database_name*istruzione COLLATE avrà esito negativo. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituirà un messaggio di errore per ogni oggetto che blocca l'azione ALTER:  
  
    -   Funzioni definite dall'utente e viste create con SCHEMABINDING.  
  
    -   Colonne calcolate.  
  
    -   Vincoli CHECK.  
  
    -   Funzioni con valori di tabella che restituiscono tabelle contenenti colonne di tipo carattere con regole di confronto ereditate dalle regole di confronto predefinite del database.  
  
     Le informazioni sulle dipendenze per le entità non associate a schemi vengono aggiornate automaticamente quando vengono modificate le regole di confronto del database.  
  
 La modifica delle regole di confronto del database non comporta la creazione di duplicati per i nomi di sistema degli oggetti di database. Se la modifica delle regole di confronto genera nomi duplicati, gli spazi dei nomi seguenti potrebbero impedire tale modifica:  
  
-   Nomi di oggetti, quali stored procedure, tabelle, trigger e viste.  
  
-   Nomi di schemi.  
  
-   Entità, come gruppi, ruoli o utenti.  
  
-   Nomi di tipi di dati scalari, come i tipi di dati di sistema e definiti dall'utente.  
  
-   Nomi di cataloghi full-text.  
  
-   Nomi di colonne o parametri in un oggetto.  
  
-   Nomi di indici in una tabella.  
  
Se vengono generati nomi duplicati in seguito all'applicazione delle nuove regole di confronto, l'azione di modifica avrà esito negativo e in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà visualizzato un messaggio di errore che indica lo spazio dei nomi in cui è stato identificato il duplicato.  
  
## <a name="viewing-database-information"></a>Visualizzazione delle informazioni sui database  
 Per restituire informazioni su database, file e filegroup, è possibile usare viste del catalogo, funzioni di sistema e stored procedure di sistema.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-name-of-a-database"></a>A. Modifica del nome di un database  
 Nell'esempio seguente il nome del database `AdventureWorks2012` viene modificato in `Northwind`.  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
### <a name="b-changing-the-collation-of-a-database"></a>B. Modifica delle regole di confronto del database  
 Nell'esempio seguente viene creato un database denominato `testdb` con le regole di confronto `SQL_Latin1_General_CP1_CI_A`S, quindi vengono modificate le regole di confronto del database `testdb` in `COLLATE French_CI_AI`.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE master;  
GO  
  
CREATE DATABASE testdb  
COLLATE SQL_Latin1_General_CP1_CI_AS ;  
GO  
  
ALTER DATABASE testDB  
COLLATE French_CI_AI ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
- [ALTER DATABASE &#40; Database SQL di Azure &#41;](alter-database-azure-sql-database.md)  
- [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
- [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
- [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
- [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
- [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
- [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
- [sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
- [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
- [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
- [database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
- [data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
- [Sys. FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
- [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
- [Database di sistema.](../../relational-databases/databases/system-databases.md)  
  

