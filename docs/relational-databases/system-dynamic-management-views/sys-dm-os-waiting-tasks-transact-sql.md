---
title: Sys.dm os_waiting_tasks (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_waiting_tasks
- sys.dm_os_waiting_tasks_TSQL
- dm_os_waiting_tasks_TSQL
- sys.dm_os_waiting_tasks
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_waiting_tasks dynamic management view
ms.assetid: ca5e6844-368c-42e2-b187-6e5f5afc8df3
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d8df7b1a31a649962f4074c936ff4310cf16a942
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmoswaitingtasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce informazioni sulla coda di attesa relativa alle attività che sono in attesa di una risorsa.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_waiting_tasks**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary (8)**|Indirizzo dell'attività in attesa.|  
|**session_id**|**smallint**|ID della sessione associata all'attività.|  
|**exec_context_id**|**int**|ID del contesto di esecuzione associato all'attività.|  
|**wait_duration_ms**|**bigint**|Tempo totale di attesa per questo tipo di attesa, in millisecondi. In questo caso si comprende **signal_wait_time**.|  
|**wait_type**|**nvarchar(60)**|Nome del tipo di attesa.|  
|**resource_address**|**varbinary (8)**|Indirizzo della risorsa attesa dall'attività.|  
|**blocking_task_address**|**varbinary (8)**|Attività che mantiene bloccata la risorsa.|  
|**blocking_session_id**|**smallint**|ID della sessione che sta bloccando la richiesta. Se questa colonna è NULL, la richiesta non è bloccata oppure non sono disponibili o identificabili informazioni di sessione per la sessione da cui è bloccata.<br /><br /> -2 = La risorsa di blocco appartiene a una transazione distribuita orfana.<br /><br /> -3 = La risorsa di blocco appartiene a una transazione di recupero posticipata.<br /><br /> -4 = Non è possibile determinare l'ID di sessione del proprietario del latch di blocco a causa di transizioni nello stato del latch interno.|  
|**blocking_exec_context_id**|**int**|ID del contesto di esecuzione dell'attività di blocco.|  
|**resource_description**|**nvarchar(3072)**|Descrizione della risorsa attualmente occupata. Per ulteriori informazioni, vedere l'elenco riportato di seguito.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="resourcedescription-column"></a>Colonna resource_description  
 La colonna resource_description include i valori possibili seguenti.  
  
 **Proprietario risorsa pool di thread:**  
  
-   id pool di thread dell'utilità di pianificazione =\<hex-address >  
  
 **Proprietario risorsa query parallela:**  
  
-   id exchangeEvent = {porta | Pipe}\<hex-address > WaitType =\<-tipo di attesa exchange > nodeId =\<exchange-nodo-id >  
  
 **Tipo di attesa Exchange**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Proprietario della risorsa di blocco:**  
  
-   \<tipo-specific-description > id = blocco\<blocco-hex-address > modalità =\<modalità > associatedObjectId =\<associata-obj-id >  
  
     **\<tipo-specific-description > può essere:**  
  
    -   Per DATABASE: Databaselock subresource =\<databaselock-subresource > dbid =\<db-id >  
  
    -   Per il FILE: Filelock fileid =\<file-id > subresource =\<filelock-subresource > dbid =\<db-id >  
  
    -   Per OBJECT: Objectlock lockPartition =\<lock-partition-id > objid =\<obj-id > subresource =\<objectlock-subresource > dbid =\<db-id >  
  
    -   Per PAGE: Pagelock fileid =\<file-id > pageid =\<pagina-id > dbid =\<db-id > subresource =\<pagelock-subresource >  
  
    -   Per Key: Keylock hobtid =\<hobt-id > dbid =\<db-id >  
  
    -   Per EXTENT: Extentlock fileid =\<file-id > pageid =\<pagina-id > dbid =\<db-id >  
  
    -   Per RID: Ridlock fileid =\<file-id > pageid =\<pagina-id > dbid =\<db-id >  
  
    -   Per APPLICATION: Applicationlock hash =\<hash > databasePrincipalId =\<ruolo-id > dbid =\<db-id >  
  
    -   Per METADATA: Metadatalock subresource =\<metadati-subresource > classid =\<metadatalock-description > dbid =\<db-id >  
  
    -   Per HOBT: Hobtlock hobtid =\<hobt-id > subresource =\<hobt-subresource > dbid =\<db-id >  
  
    -   Per ALLOCATION_UNIT: Allocunitlock hobtid =\<hobt-id > subresource =\<alloc-unit-subresource > dbid =\<db-id >  
  
     **\<modalità > può essere:**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Proprietario risorsa esterna:**  
  
-   ExternalResource esterno =\<-tipo di attesa >  
  
 **Proprietario risorsa generica:**  
  
-   Area di lavoro TransactionInfo TransactionMutex =\<id area di lavoro >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Proprietario risorsa latch:**  
  
-   \<DB-id >:\<file-id >:\<nel file di paging >  
  
-   \<GUID >  
  
-   \<classe di latch > (\<latch-indirizzo >)  
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
 
## <a name="example"></a>Esempio
In questo esempio identificherà le sessioni bloccate.  Eseguire il [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguire una query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
```tsql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>Vedere anche  
  [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


