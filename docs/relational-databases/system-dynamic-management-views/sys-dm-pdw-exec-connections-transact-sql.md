---
title: sys.dm_pdw_exec_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8f55c2f5b98aa1778c8772dc30fffd16fe522ca7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Restituisce informazioni sulle connessioni stabilite per questa istanza di [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e i dettagli di ogni connessione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifica la sessione associata alla connessione Utilizzare `SESSION_ID()` per restituire il `session_id` della connessione corrente.|  
|connect_time|**datetime**|Timestamp relativo al momento in cui è stata stabilita la connessione. Non ammette i valori Null.|  
|encrypt_option|**nvarchar(40)**|Indica TRUE (connessione è crittografata) o FALSE (connessione non è enctypred).|  
|auth_scheme|**nvarchar(40)**|Specifica lo schema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Autenticazione di Windows utilizzato con questa connessione. Non ammette i valori Null.|  
|client_id|**varchar(48)**|Indirizzo IP del client che si connette al server. Ammette i valori Null.|  
|sql_spid|**int**|ID del processo server della connessione. Utilizzare `@@SPID` per restituire il `sql_spid` della connessione corrente. Per più illustrativi, utilizzare il `session_id` invece.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede **VIEW SERVER STATE** autorizzazione nel server.  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|Uno-a-uno|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|Molti-a-uno|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Query tipica per raccogliere informazioni su una connessione query personalizzata.  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

