---
title: DBCC CHECKCATALOG (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7c8b73259e599e0001706cfaf09dca30d7d31a5b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkcatalog-transact-sql"></a>DBCC CHECKCATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
> Esecuzione di DBCC CHECKCATALOG su **tempdb** non esegue alcun controllo. Questo avviene perché, per motivi di prestazioni, gli snapshot del database non sono disponibili in **tempdb**. Ciò significa che non è possibile ottenere la consistenza delle transazioni necessaria. Riciclare il server per risolvere gli eventuali **tempdb** problemi relativi ai metadati.  
  
> [!NOTE]  
> I dati di FILESTREAM non vengono controllati da DBCC CHECKCATALOG. Tramite FILESTREAM vengono archiviati oggetti binari di grandi dimensioni (BLOB) nel file system.  
  
DBCC CHECKCATALOG viene inoltre eseguita come parte di [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).
  
## <a name="result-sets"></a>Set di risultati  
Se non si specifica alcun database, DBCC CHECKCATALOG restituisce:
  
```
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Se come nome del database si specifica [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], DBCC CHECKCATALOG restituisce:
  
```
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Autorizzazioni  
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
[System Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)
  
