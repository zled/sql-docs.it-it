---
title: Sys.dm tran_session_transactions (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/30/2017
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
- dm_tran_session_transactions
- sys.dm_tran_session_transactions
- sys.dm_tran_session_transactions_TSQL
- dm_tran_session_transactions_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_session_transactions dynamic management view
ms.assetid: c7157491-58c2-49fe-87d7-0c9723113adf
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b247ada006579e642a6ce4c9c4b7b17b153e69c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtransessiontransactions-transact-sql"></a>sys.dm_tran_session_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce informazioni di correlazione per le sessioni e le transazioni associate.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_tran_session_transactions**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|ID della sessione nella quale viene eseguita la transazione.|  
|transaction_id|**bigint**|ID della transazione.|  
|transaction_descriptor|**Binary (8)**|Identificatore di transazione utilizzato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante la comunicazione con il driver client.|  
|enlist_count|**int**|Numero di richieste attive nella sessione della transazione.|  
|is_user_transaction|**bit**|1 = La transazione è stata iniziata da una richiesta utente.<br /><br /> 0 = Transazione di sistema.|  
|is_local|**bit**|1 = Transazione locale.<br /><br /> 0 = Transazione distribuita o transazione di sessione associata integrata.|  
|is_enlisted|**bit**|1 = Transazione distribuita integrata.<br /><br /> 0 = Non è una transazione distribuita integrata.|  
|is_bound|**bit**|1 = La transazione è attiva nella sessione tramite sessioni associate.<br /><br /> 0 = La transazione non è attiva nella sessione tramite sessioni associate.|  
|open_transaction_count||Numero di transazioni aperte per ogni sessione.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
 
 
  
## <a name="remarks"></a>Osservazioni  
 È possibile che una transazione venga eseguita in più di una sessione tramite sessioni associate e transazioni distribuite. In tali casi, sys.dm_tran_session_transactions visualizzerà più righe per lo stesso transaction_id, una per ogni sessione in cui viene eseguita la transazione.  
  
 Eseguendo più richieste in modalità autocommit e utilizzando MARS (Multiple Active Result Sets), è possibile che vi siano più transazioni attive in una singola sessione. In tali casi, sys.dm_tran_session_transactions visualizzerà più righe per lo stesso transaction_id, una per ogni transazione eseguita nella sessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative alle transazioni &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


