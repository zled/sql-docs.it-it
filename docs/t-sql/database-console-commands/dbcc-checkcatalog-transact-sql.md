---
title: DBCC CHECKCATALOG (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_CHECKCATALOG_TSQL
- DBCC CHECKCATALOG
- CHECKCATALOG_TSQL
- CHECKCATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- catalogs [SQL Server], consistency checks
- checking catalog consistency
- DBCC CHECKCATALOG statement
- integrity [SQL Server], catalogs
- consistency [SQL Server], catalogs
ms.assetid: 8076eb4e-f049-44bf-9a35-45cdd6ef0105
caps.latest.revision: 51
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f63850a2cf39d783daee65431da349d04cba3b03
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-checkcatalog-transact-sql"></a>DBCC CHECKCATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Verifica la consistenza dei cataloghi all'interno del database specificato. Il database deve essere online.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DBCC CHECKCATALOG   
[   
    (   
    database_name | database_id | 0  
    )  
]  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name* | *database_id* | 0  
 Nome o ID del database per il quale verificare la consistenza dei cataloghi. Se questo argomento viene omesso oppure se viene specificato il valore 0, viene utilizzato il database corrente. I nomi dei database devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 WITH NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
  
## <a name="remarks"></a>Osservazioni  
Dopo il completamento del comando DBCC CATALOG, viene scritto un messaggio nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se il comando DBCC viene eseguito correttamente, il messaggio indica il completamento corretto e la durata dell'esecuzione del comando. Se il comando DBCC viene arrestato prima del completamento del controllo a causa di un errore, il messaggio indica che il comando è stato terminato e specifica un valore di stato e la durata dell'esecuzione del comando. Nella tabella seguente sono elencati e descritti i valori di stato che possono essere inclusi nel messaggio.
  
|State|Description|  
|-----------|-----------------|  
|0|È stato generato l'errore numero 8930. Indica che il comando DBCC è stato terminato a causa di un danneggiamento dei metadati.|  
|1|È stato generato l'errore numero 8967. Si è verificato un errore DBCC interno.|  
|2|Si è verificato un errore durante un ripristino di database in modalità di emergenza.|  
|3|Indica che il comando DBCC è stato terminato a causa di un danneggiamento dei metadati.|  
|4|È stata rilevata una violazione di accesso o asserzione.|  
|5|Si è verificato un errore sconosciuto che ha causato l'interruzione del comando DBCC.|  
  
DBCC CHECKCATALOG esegue vari controlli di consistenza tra le tabelle di metadati di sistema. DBCC CHECKCATALOG utilizza uno snapshot interno del database per garantire la consistenza necessaria a livello di transazioni per eseguire queste verifiche. Per ulteriori informazioni, vedere [visualizzare le dimensioni del File Sparse di uno Snapshot del Database &#40; Transact-SQL &#41; ](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) e la sezione "DBCC dell'utilizzo di Snapshot interno del Database" in [DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-transact-sql.md).
Se risulta impossibile creare uno snapshot, DBCC CHECKCATALOG acquisisce un blocco esclusivo a livello di database per ottenere la consistenza richiesta. Le eventuali inconsistenze rilevate non potranno essere riparate e pertanto sarà necessario ripristinare il database da un backup.
  
> [!NOTE]  
>  Esecuzione di DBCC CHECKCATALOG su **tempdb** non esegue alcun controllo. Questo avviene perché, per motivi di prestazioni, gli snapshot del database non sono disponibili in **tempdb**. Ciò significa che non è possibile ottenere la consistenza delle transazioni necessaria. Riciclare il server per risolvere gli eventuali **tempdb** problemi relativi ai metadati.  
  
> [!NOTE]  
>  I dati di FILESTREAM non vengono controllati da DBCC CHECKCATALOG. Tramite FILESTREAM vengono archiviati oggetti binari di grandi dimensioni (BLOB) nel file system.  
  
DBCC CHECKCATALOG viene inoltre eseguita come parte di [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).
  
## <a name="result-sets"></a>Set di risultati  
Se non si specifica alcun database, DBCC CHECKCATALOG restituisce:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Se come nome del database si specifica [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], DBCC CHECKCATALOG restituisce:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **sysadmin** ruolo predefinito del server, o **db_owner** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene eseguito il controllo dell'integrità dei cataloghi nel database corrente e nel database `AdventureWorks`.
  
```sql
-- Check the current database.  
DBCC CHECKCATALOG;  
GO  
-- Check the AdventureWorks2012 database.  
DBCC CHECKCATALOG (AdventureWorks2012);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Tabelle di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)
  

