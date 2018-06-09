---
title: Stored procedure (Transact-SQL) di sistema | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2016 CTP3)
f1_keywords:
- sql13.TSQLSysNoExpandPortal.f1
- sql13.TSQLSysNoExpandPortal.f1_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server]
- APIs [SQL Server]
- stored procedures [SQL Server], categories
- system stored procedures [SQL Server], categories
- system stored procedures [SQL Server]
ms.assetid: a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 481b0c451f5161231cf64402c5c758870a07be62
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34708639"
---
# <a name="system-stored-procedures-transact-sql"></a>Stored procedure di sistema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] molte attività amministrative e informative possono essere eseguite mediante le stored procedure di sistema. Le stored procedure di sistema sono raggruppate in categorie, descritte nella tabella seguente.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Category|Description|  
|--------------|-----------------|  
|[Stored procedure di replica geografica attiva](http://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)|Utilizzato per gestire le configurazioni di replica geografica attiva nel Database di SQL Azure|  
|[Stored procedure di catalogo](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)|Consentono di implementare le funzioni del dizionario dei dati ODBC e di isolare le applicazioni ODBC in caso di modifiche alle tabelle di sistema sottostanti.|  
|[Stored procedure Change Data Capture](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)|Consentono di abilitare, disabilitare o creare report relativi a oggetti Change Data Capture.|  
|[Stored procedure per cursori](../../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)|Consentono di implementare la funzionalità per le variabili di cursore.|  
|[Stored procedure di agente di raccolta dati](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)|Consentono di lavorare con l'agente di raccolta dati e i componenti seguenti: set di raccolta, elementi delle raccolte e tipi di raccolta.|  
|[Stored procedure del motore di database](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)|Consentono di eseguire le operazioni di manutenzione generale del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)|Consentono di eseguire le operazioni di posta elettronica da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Piano di manutenzione database Stored procedure](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)|Consentono di impostare le attività di manutenzione principali necessarie per gestire le prestazioni dei database.|  
|[Stored procedure per query distribuite](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)|Consentono di implementare e gestire le query distribuite.|  
|[FileStream e FileTable Stored procedure &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/54beca08-c012-4ebd-aa68-d8a10d221b64)|Utilizzato per configurare e gestire le caratteristiche FILESTREAM e FileTable.|  
|[Le regole del firewall Stored procedure &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/firewall-rules-stored-procedures-azure-sql-database.md)|Consente di configurare il firewall di Database SQL di Azure.|  
|[Stored procedure per ricerche Full-Text](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)|Consentono di implementare ed eseguire query su indici full-text.|  
|[Stored procedure estese generali](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)|Consentono di utilizzare un'interfaccia tra un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e programmi esterni per varie attività di manutenzione.|  
|[Il log Shipping Stored procedure](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)|Consentono di configurare, modificare e monitorare le configurazioni per il log shipping.|  
|[Data Warehouse gestione le Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql.md)|Consente di configurare il data warehouse di gestione.|  
|[Automazione OLE Stored procedure](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)|Consentono di abilitare gli oggetti di automazione standard per l'utilizzo all'interno di un batch [!INCLUDE[tsql](../../includes/tsql-md.md)] standard.|  
|[Stored procedure della gestione basata su criteri](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)|Consentono di implementare la gestione basata su criteri.|  
|[Stored procedure di PolyBase](http://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)|Aggiungere o rimuovere un computer da un gruppo con scalabilità orizzontale PolyBase.|  
|[Stored procedure di archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)|Utilizzato per ottimizzare le prestazioni.|  
|[Stored procedure di replica](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)|Consentono di gestire le operazioni di replica.|  
|[Stored procedure di sicurezza](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)|Consentono di gestire la sicurezza.|  
|[Stored procedure di Backup snapshot](http://msdn.microsoft.com/library/c278db87-5770-4037-a1e6-b9853a943339)|Utilizzato per eliminare i backup FILE_SNAPSHOT insieme a tutti i relativi snapshot o per eliminare un singolo file di backup di snapshot.|  
|[Indice spaziale Stored procedure](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)|Utilizzato per analizzare e migliorare le prestazioni di indicizzazione degli indici spaziali.|  
|[Stored procedure SQL Server Agent](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)|Consentono a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] di monitorare prestazione e attività.|  
|[Stored procedure di SQL Server Profiler](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|Consentono a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di gestire attività pianificate e guidate dagli eventi.|  
|[Estensione Database Stored procedure](../../relational-databases/system-stored-procedures/stretch-database-extended-stored-procedures-transact-sql.md)|Consente di gestire i database di estensione.|  
|[Le tabelle temporali Stored procedure](http://msdn.microsoft.com/library/f28ca74e-7876-4592-b794-e78e3690fff6)|Utilizzare per le tabelle temporali|  
|[Stored procedure per XML](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)|Consentono di gestire il testo XML.|  
  
> [!NOTE]  
>  Se non specificato diversamente, tutte le stored procedure di sistema restituiscono il valore 0 per indicare esito positivo. Per indicare esito negativo, viene restituito un valore diverso da zero.  
  
## <a name="api-system-stored-procedures"></a>Stored procedure di sistema (API)  
 Gli utenti che eseguono [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per applicazioni ADO, OLE DB e ODBC possono notare che queste applicazioni utilizzano stored procedure di sistema che non vengono trattate nella Guida di riferimento a [!INCLUDE[tsql](../../includes/tsql-md.md)]. Queste stored procedure vengono utilizzate per la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Provider Native Client OLE DB e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il driver ODBC Native Client per implementare la funzionalità di un'API di database. Rappresentano il meccanismo con cui il provider o il driver comunica le richieste degli utenti a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Devono essere utilizzate solo internamente dal provider o dal driver. Chiamarle esplicitamente da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-applicazione di base non è supportata.  
  
 Il sp_createorphan e sp_droporphans stored procedure vengono utilizzate per ODBC **ntext**, **testo**, e **immagine** l'elaborazione.  
  
 La stored procedure sp_reset_connection viene utilizzata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il supporto di chiamate di stored procedure remote in una transazione. Questa stored procedure causa inoltre la generazione degli eventi Audit Login e Audit Logout quando una connessione viene riutilizzata da un pool di connessioni.  
  
 Le stored procedure di sistema riportate nelle tabelle seguenti vengono utilizzate solo in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o tramite API client e non devono essere utilizzate dagli utenti finali. Sono soggette a modifiche e la compatibilità non è garantita.  
  
 Le stored procedure seguenti sono documentate nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
|||  
|-|-|  
|sp_catalogs|sp_column_privileges|  
|sp_column_privileges_ex|sp_columns|  
|sp_columns_ex|sp_databases|  
|sp_cursor|sp_cursorclose|  
|sp_cursorexecute|sp_cursorfetch|  
|sp_cursoroption|sp_cursoropen|  
|sp_cursorprepare|sp_cursorprepexec|  
|sp_cursorunprepare|sp_execute|  
|sp_datatype_info|sp_fkeys|  
|sp_foreignkeys|sp_indexes|  
|sp_pkeys|sp_primarykeys|  
|sp_prepare|sp_prepexec|  
|sp_prepexecrpc|sp_unprepare|  
|sp_server_info|sp_special_columns|  
|sp_sproc_columns|sp_statistics|  
|sp_table_privileges|sp_table_privileges_ex|  
|sp_tables|sp_tables_ex|  
  
 Le stored procedure seguenti non sono documentate:  
  
|||  
|-|-|  
|sp_assemblies_rowset|sp_assemblies_rowset_rmt|  
|sp_assemblies_rowset2|sp_assembly_dependencies_rowset|  
|sp_assembly_dependencies_rowset_rmt|sp_assembly_dependencies_rowset2|  
|sp_bcp_dbcmptlevel|sp_catalogs_rowset|  
|sp_catalogs_rowset;2|sp_catalogs_rowset;5|  
|sp_catalogs_rowset_rmt|sp_catalogs_rowset2|  
|sp_check_constbytable_rowset|sp_check_constbytable_rowset;2|  
|sp_check_constbytable_rowset2|sp_check_constraints_rowset|  
|sp_check_constraints_rowset;2|sp_check_constraints_rowset2|  
|sp_column_privileges_rowset|sp_column_privileges_rowset;2|  
|sp_column_privileges_rowset;5|sp_column_privileges_rowset_rmt|  
|sp_column_privileges_rowset2|sp_columns_90|  
|sp_columns_90_rowset|sp_columns_90_rowset_rmt|  
|sp_columns_90_rowset2|sp_columns_ex_90|  
|sp_columns_rowset|sp_columns_rowset;2|  
|sp_columns_rowset;5|sp_columns_rowset_rmt|  
|sp_columns_rowset2|sp_constr_col_usage_rowset|  
|sp_datatype_info_90|sp_ddopen;1|  
|sp_ddopen;10|sp_ddopen;11|  
|sp_ddopen;12|sp_ddopen;13|  
|sp_ddopen;2|sp_ddopen;3|  
|sp_ddopen;4|sp_ddopen;5|  
|sp_ddopen;6|sp_ddopen;7|  
|sp_ddopen;8|sp_ddopen;9|  
|sp_foreign_keys_rowset|sp_foreign_keys_rowset;2|  
|sp_foreign_keys_rowset;3|sp_foreign_keys_rowset;5|  
|sp_foreign_keys_rowset_rmt|sp_foreign_keys_rowset2|  
|sp_foreign_keys_rowset3|sp_indexes_90_rowset|  
|sp_indexes_90_rowset_rmt|sp_indexes_90_rowset2|  
|sp_indexes_rowset|sp_indexes_rowset;2|  
|sp_indexes_rowset;5|sp_indexes_rowset_rmt|  
|sp_indexes_rowset2|sp_linkedservers_rowset|  
|sp_linkedservers_rowset;2|sp_linkedservers_rowset2|  
|sp_oledb_database|sp_oledb_defdb|  
|sp_oledb_deflang|sp_oledb_language|  
|sp_oledb_ro_usrname|sp_primary_keys_rowset|  
|sp_primary_keys_rowset;2|sp_primary_keys_rowset;3|  
|sp_primary_keys_rowset;5|sp_primary_keys_rowset_rmt|  
|sp_primary_keys_rowset2|sp_procedure_params_90_rowset|  
|sp_procedure_params_90_rowset2|sp_procedure_params_rowset|  
|sp_procedure_params_rowset;2|sp_procedure_params_rowset2|  
|sp_procedures_rowset|sp_procedures_rowset;2|  
|sp_procedures_rowset2|sp_provider_types_90_rowset|  
|sp_provider_types_rowset|sp_schemata_rowset|  
|sp_schemata_rowset;3|sp_special_columns_90|  
|sp_sproc_columns_90|sp_statistics_rowset|  
|sp_statistics_rowset;2|sp_statistics_rowset2|  
|sp_stored_procedures|sp_table_constraints_rowset|  
|sp_table_constraints_rowset;2|sp_table_constraints_rowset2|  
|sp_table_privileges_rowset|sp_table_privileges_rowset;2|  
|sp_table_privileges_rowset;5|sp_table_privileges_rowset_rmt|  
|sp_table_privileges_rowset2|sp_table_statistics_rowset|  
|sp_table_statistics_rowset;2|sp_table_statistics2_rowset|  
|sp_tablecollations|sp_tablecollations_90|  
|sp_tables_info_90_rowset|sp_tables_info_90_rowset_64|  
|sp_tables_info_90_rowset2|sp_tables_info_90_rowset2_64|  
|sp_tables_info_rowset|sp_tables_info_rowset;2|  
|sp_tables_info_rowset_64|sp_tables_info_rowset_64;2|  
|sp_tables_info_rowset2|sp_tables_info_rowset2_64|  
|sp_tables_rowset;2|sp_tables_rowset;5|  
|sp_tables_rowset_rmt|sp_tables_rowset2|  
|sp_usertypes_rowset|sp_usertypes_rowset_rmt|  
|sp_usertypes_rowset2|sp_views_rowset|  
|sp_views_rowset2|sp_xml_schema_rowset|  
|sp_xml_schema_rowset2||  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Stored procedure &#40;Motore di database&#41;](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [Esecuzione di Stored procedure &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)   
 [Esecuzione di Stored procedure](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Esecuzione delle stored procedure](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
