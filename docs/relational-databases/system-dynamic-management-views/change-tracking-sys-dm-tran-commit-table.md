---
title: sys.dm_tran_commit_table (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_tran_commit_table
- dm_tran_commit_table_TSQL
- sys.dm_tran_commit_table
- sys.dm_tran_commit_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_commit_table dynamic management view
ms.assetid: 732d23c5-1f6c-4e96-bc85-8f29b520cf0e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17e42e8bf81db76b3034c6bf1e2e0111a6fc9671
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="change-tracking---sysdmtrancommittable"></a>Rilevamento modifiche - Sys.dm tran_commit_table
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Visualizza una riga per ogni transazione di cui viene eseguito il commit per una tabella rilevata mediante il rilevamento delle modifiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La vista di gestione sys.dm_tran_commit_table, fornita per scopi di supporto, espone le informazioni correlate alla transazione archiviate tramite il rilevamento delle modifiche nella tabella di sistema sys.syscommittab. La tabella sys.syscommittab fornisce un efficiente mapping persistente da un ID di transazione specifico del database al numero di sequenza del file di log (LSN) del commit della transazione e al timestamp del commit. I dati archiviati nella tabella sys.syscommittab ed esposti in questa vista di gestione sono soggetti al processo di pulizia in base al periodo di memorizzazione specificato durante la configurazione del rilevamento delle modifiche.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_tran_commit_table**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|Numero a incremento progressivo costante che funge da timestamp specifico del database per ogni transazione di cui viene eseguito il commit.|  
|xdes_id|**bigint**|ID interno specifico del database per la transazione.|  
|commit_lbn|**bigint**|Numero del blocco del log contenente il record del log del commit per la transazione.|  
|commit_csn|**bigint**|Numero di sequenza del commit specifico dell'istanza per la transazione.|  
|commit_time|**smalldatetime**|Ora in cui è stato eseguito il commit della transazione.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Informazioni sul rilevamento delle modifiche &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


