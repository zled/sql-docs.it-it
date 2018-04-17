---
title: Sys. remote_data_archive_tables (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_tables
- sys.remote_data_archive_tables_TSQL
- remote_data_archive_tables
- remote_data_archive_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_tables catalog view
ms.assetid: 765069b7-60fd-414c-875f-3455460b75cd
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 29d6916024358efb9e806a5f8d1eeaf6a3715d89
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stretch-database-catalog-views---sysremotedataarchivetables"></a>Estensione delle viste del catalogo del Database - remote_data_archive_tables
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni tabella remota che archivia i dati da una tabella locale abilitata per l'estensione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|L'ID di oggetto della tabella locale abilitata per l'estensione.|  
|**remote_database_id**|**int**|L'identificatore di locale generato automaticamente del database remoto.|  
|**remote_table_name**|**sysname**|Il nome della tabella nel database remoto corrispondente alla tabella locale abilitata per l'estensione.|  
|**filter_predicate**|**nvarchar(max)**|Il predicato del filtro, se presente, che identifica le righe della tabella per la migrazione. Se il valore è null, l'intera tabella è idonea per la migrazione.<br /><br /> Per altre informazioni, vedere [abilitare estensione Database per una tabella](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) e [selezionare righe di cui eseguire la migrazione con un predicato del filtro](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).|  
|**migration_direction**|**tinyint**|La direzione in cui dati sono in corso la migrazione. I valori disponibili sono le seguenti.<br/>1 (in uscita)<br/>2 (in ingresso)|  
|**migration_direction_desc**|**nvarchar(60)**|Descrizione della direzione in cui dati sono in corso la migrazione. I valori disponibili sono le seguenti.<br/>in uscita (1)<br/>connessioni in entrata (2)|  
|**is_migration_paused**|**bit**|Indica se è attualmente sospesa la migrazione.|  
|**is_reconciled**|**bit**| Indica se la tabella remota e la tabella di SQL Server sono sincronizzati.<br/><br/>Quando il valore di **is_reconciled** è 1 (true), la tabella remota e la tabella di SQL Server sono sincronizzati ed è possibile eseguire query che includono i dati remoti.<br/><br/>Quando il valore di **is_reconciled** è 0 (false), la tabella remota e la tabella di SQL Server non sono sincronizzati. Recentemente le righe migrate devono essere eseguita nuovamente la migrazione. Questo errore si verifica quando si ripristina il database remoto di Azure o quando si elimina manualmente le righe dalla tabella remota. Fino a quando non si risolvere le differenze tra le tabelle, è possibile eseguire query che includono i dati remoti. Per risolvere le differenze tra le tabelle, eseguire [sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md). |  
  
## <a name="see-also"></a>Vedere anche  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

