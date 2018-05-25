---
title: sys.dm_io_pending_io_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_io_pending_io_requests
- dm_io_pending_io_requests
- dm_io_pending_io_requests_TSQL
- sys.dm_io_pending_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_pending_io_requests dynamic management view
ms.assetid: d1fb46dd-5c74-4c04-9ecf-8934b1bedb5b
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: eeb43f5d32b5ecfa62787c6c9c2189ea2476c7cd
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmiopendingiorequests-transact-sql"></a>sys.dm_io_pending_io_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Restituisce una riga per ogni richiesta di I/O in sospeso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_io_pending_io_requests**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**io_completion_request_address**|**varbinary(8)**|Indirizzo di memoria della richiesta di I/O. Non ammette i valori Null.|  
|**io_type**|**varchar(7)**|Tipo di richiesta di I/O in sospeso. Non ammette i valori Null.|  
|**io_pending**|**int**|Indica se la richiesta di I/O è in sospeso o è stata completata da Windows. Una richiesta di I/O può essere ancora in sospeso anche quando Windows ha completato la richiesta, ma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non ha ancora eseguito uno scambio di contesto per l'elaborazione della richiesta di I/O e la relativa rimozione dall'elenco. Non ammette i valori Null.|  
|**io_completion_routine_address**|**varbinary(8)**|Funzione interna da chiamare quando la richiesta di I/O viene completata. Ammette i valori Null.|  
|**io_user_data_address**|**varbinary(8)**|Solo per uso interno. Ammette i valori Null.|  
|**scheduler_address**|**varbinary(8)**|Utilità di pianificazione sulla quale è stata eseguita la richiesta di I/O. La richiesta di I/O verrà visualizzata nell'elenco delle richieste di I/O in sospeso dell'utilità di pianificazione. Per altre informazioni, vedere [DM os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md). Non ammette i valori Null.|  
|**io_handle**|**varbinary(8)**|Handle di file utilizzato nella richiesta di I/O. Ammette i valori Null.|  
|**io_offset**|**bigint**|Offset della richiesta di I/O. Non ammette i valori Null.|  
|**io_pending_ms_ticks**|**int**|Solo per uso interno. Non ammette i valori Null.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [È possibile O funzioni e viste a gestione dinamica relative &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


