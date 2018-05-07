---
title: sys.dm_os_stacks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bf5e45daa77d65528d9662dc186e3e098ec7d23c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Questa vista a gestione dinamica viene utilizzata internamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per:  
  
-   Tenere traccia dei dati di debug quali le allocazioni in sospeso.  
  
-   Utilizzare o convalidare la logica utilizzata dai componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dove il componente specifico presume che sia stata eseguita una determinata chiamata.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Indirizzo univoco per l'allocazione di stack. Non ammette i valori Null.|  
|**frame_index**|**int**|Ogni riga rappresenta una funzione chiamata che, quando ordinato in ordine crescente in base all'indice di frame per un particolare **stack_address**, restituisce lo stack di chiamate completo. Non ammette i valori Null.|  
|**frame_address**|**varbinary(8)**|Indirizzo della chiamata di funzione. Non ammette i valori Null.|  
  
## <a name="remarks"></a>Osservazioni  
 **Sys.dm_os_stacks** richiede che i simboli del server e altri componenti sia presente nel server per visualizzare correttamente le informazioni.  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   


## <a name="see-also"></a>Vedere anche  
  [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
