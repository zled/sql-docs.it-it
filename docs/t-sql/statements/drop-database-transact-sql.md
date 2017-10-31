---
title: ELIMINARE il DATABASE (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 09/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP DATABASE
- DROP_DATABASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], deleting
- removing databases
- database snapshots [SQL Server], removing
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- DROP DATABASE statement
- database removal [SQL Server], DROP DATABASE statement
ms.assetid: 477396a9-92dc-43c9-9b97-42c8728ede8e
caps.latest.revision: 83
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 6e1a96bb64c8cb6a81311f422d370e36d9489ca4
ms.contentlocale: it-it
ms.lasthandoff: 10/24/2017

---
# <a name="drop-database-transact-sql"></a>DROP DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Rimuove uno o più database utente o snapshot di database da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- SQL Server Syntax  
DROP DATABASE [ IF EXISTS ] { database_name | database_snapshot_name } [ ,...n ] [;]  
```  
  
```  
-- Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse Syntax   
DROP DATABASE database_name [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale il database solo se esiste già.  
  
 *database_name*  
 Specifica il nome del database da rimuovere. Per visualizzare un elenco di database, utilizzare il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
 *database_snapshot_name*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il nome di uno snapshot del database da rimuovere.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Un database può essere rimosso indipendentemente dallo stato: offline, di sola lettura, sospetto e così via. Per visualizzare lo stato corrente di un database, utilizzare il **Sys. Databases** vista del catalogo.  
  
 È possibile ricreare un database rimosso solo tramite il ripristino di un backup. Non è possibile eseguire il backup degli snapshot di un database e, di conseguenza, non è possibile ripristinarli.  
  
 Quando viene eliminato un database, il [database master](../../relational-databases/databases/master-database.md) deve essere eseguito il backup.  
  
 La rimozione di un database comporta l'eliminazione del database da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dei relativi file su disco utilizzati. Se il database o uno dei relativi file è offline quando viene rimosso, i file su disco non vengono eliminati. Questi file possono essere eliminati manualmente tramite Esplora risorse. Per rimuovere un database dal server corrente senza eliminare i file dal file system, utilizzare [sp_detach_db](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md).  
  
> [!WARNING]  
>  Rimozione di un database con FILE_SNAPSHOT associati backup avrà esito positivo, ma non verranno eliminati i file di database a cui sono associati snapshot per evitare di invalidare i backup che fa riferimento a questi file di database. Il file verrà troncato, ma non verranno fisicamente eliminato per mantenere i backup FILE_SNAPSHOT intatto. Per altre informazioni, vedere [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 La rimozione di uno snapshot di database comporta l'eliminazione dello snapshot del database in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dei file sparse fisici del file system NTFS utilizzati dallo snapshot. Per informazioni sull'utilizzo dei file sparse dagli snapshot del database, vedere [snapshot del Database &#40; SQL Server &#41; ](../../relational-databases/databases/database-snapshots-sql-server.md). La rimozione di uno snapshot del database comporta la cancellazione della cache dei piani per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La cancellazione della cache dei piani comporta la ricompilazione di tutti i piani di esecuzione successivi e può causare un peggioramento improvviso e temporaneo delle prestazioni di esecuzione delle query. Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene il messaggio informativo seguente per ogni archivio cache cancellato nella cache dei piani: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato %d occorrenza/e di scaricamento dell'archivio cache '%s' (parte della cache dei piani) a causa di operazioni di manutenzione o riconfigurazione del database". Questo messaggio viene registrato ogni cinque minuti per tutta la durata dello scaricamento della cache.  
  
## <a name="interoperability"></a>Interoperabilità  
  
### <a name="sql-server"></a>SQL Server  
 Per rimuovere un database pubblicato per la replica transazionale, o pubblicato o sottoscritto per la replica di tipo merge, è necessario innanzitutto rimuovere la replica dal database. Se un database è danneggiato, se non è possibile rimuovere prima la replica o se si verificano entrambe le situazioni, nella maggior parte dei casi è comunque possibile eliminare il database tramite ALTER DATABASE per impostarlo offline e, successivamente, rimuoverlo.  
  
 Se il database è coinvolto nel log shipping, rimuovere quest'ultimo prima di eliminare il database. Per altre informazioni, vedere [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 [Database di sistema](../../relational-databases/databases/system-databases.md) non può essere eliminata.  
  
 L'istruzione DROP DATABASE deve essere eseguita in modalità autocommit e non è consentita in una transazione esplicita o implicita. La modalità autocommit è la modalità predefinita per la gestione delle transazioni.  
  
 Non è possibile rimuovere un database in uso, ovvero aperto per la lettura o la scrittura da parte di un utente. Per rimuovere gli utenti dal database, utilizzare ALTER DATABASE per impostare il database su SINGLE_USER.  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Prima di poter rimuovere un database, è necessario eliminare tutti gli snapshot del database.  
  
 Eliminazione di un database per abilitare per l'estensione Database non rimuove i dati remoti. Se si desidera eliminare i dati remoti, è necessario rimuoverlo manualmente.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 È necessario essere connessi al database master per eliminare un database.
  
 L'istruzione DROP DATABASE deve essere l'unica istruzione in un batch SQL ed è possibile eliminare un solo database alla volta.
  
### [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
 È necessario essere connessi al database master per eliminare un database.
  
 L'istruzione DROP DATABASE deve essere l'unica istruzione in un batch SQL ed è possibile eliminare un solo database alla volta.

## <a name="permissions"></a>Permissions  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Richiede il **controllo** autorizzazione per il database, o **ALTER ANY DATABASE** autorizzazione o l'appartenenza di **db_owner** ruolo predefinito del database.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Solo il livello di server di accesso dell'entità (creato dal processo di provisioning) o i membri del **dbmanager** ruolo del database può eliminare un database.  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Richiede il **controllo** autorizzazione per il database, o **ALTER ANY DATABASE** autorizzazione o l'appartenenza di **db_owner** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-single-database"></a>A. Rimozione di un singolo database  
 Nell'esempio seguente viene rimosso il database `Sales`.  
  
```  
DROP DATABASE Sales;  
```  
  
### <a name="b-dropping-multiple-databases"></a>B. Rimozione di più database  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nell'esempio seguente vengono rimossi tutti i database elencati.  
  
```  
DROP DATABASE Sales, NewSales;  
```  
  
### <a name="c-dropping-a-database-snapshot"></a>C. Eliminazione di uno snapshot del database  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nell'esempio seguente viene rimosso uno snapshot del database, denominato `sales_snapshot0600`, senza influire sul database di origine.  
  
```  
DROP DATABASE sales_snapshot0600;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  

