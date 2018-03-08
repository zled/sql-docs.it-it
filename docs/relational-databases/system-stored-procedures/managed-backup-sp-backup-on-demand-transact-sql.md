---
title: managed_backup.sp_backup_on_demand (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smart_admin.sp_backup_on_demand
- smart_admin.sp_backup_on_demand_TSQL
- sp_backup_on_demand_TSQL
- sp_backup_on_demand
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.sp_backup_on_demand
- sp_backup_on_demand
ms.assetid: 638f809f-27fa-4c44-a549-9cf37ecc920c
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6db602abb8706f94c90b0b583f2468b7a02a251d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="managedbackupspbackupondemand-transact-sql"></a>managed_backup.sp_backup_on_demand (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Richiede al [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] di eseguire un backup del database specificato.  
  
 Utilizzare questa stored procedure per l'esecuzione dei backup ad hoc per un database configurato con il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Ciò impedisce qualsiasi interruzione nella catena di backup, i processi del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] vengono riconosciuti e il backup viene archiviato nello stesso contenitore di archiviazione BLOB di Windows Azure.  
  
 Al completamento del backup, viene restituito il percorso del file di backup completo che include il nome e la posizione del nuovo file di backup risultante dall'operazione di backup.  
  
 Viene restituito un errore se il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è in fase di esecuzione di un backup di un determinato tipo per il database specificato. In questo caso, il messaggio di errore restituito include il percorso del file di backup completo in cui il backup corrente viene caricato.  
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @database_name  
 Nome del database in cui deve essere eseguito il backup. Il @database_name è **SYSNAME**.  
  
 @type  
 Tipo di backup da eseguire: database o log. Il @type parametro **NVARCHAR(32)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** , autorizzazioni e **EXECUTE** le autorizzazioni per **sp_delete _ BackupHistory**stored procedure.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una richiesta di backup per il database 'TestDB'. Per questo database è stato abilitato il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 Per ogni frammento di codice, selezionare 'tsql' nel campo dell'attributo di linguaggio.  
  
  
