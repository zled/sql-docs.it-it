---
title: Sys.dm os_child_instances (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs: TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d13a86c17d95f31d2ffe99fa6675a0e0fe877ecd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmoschildinstances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni istanza utente creata dall'istanza del server padre.  
  
> **IMPORTANTE** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Le informazioni restituite da **Sys.dm os_child_instances** può essere utilizzato per determinare lo stato di ogni istanza utente (heart_beat) e per ottenere il nome della pipe (instance_pipe_name) che può essere utilizzato per creare una connessione all'utente Istanza utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o SQLCmd. È possibile connettersi a un'istanza utente solo dopo che è stata avviata da un processo esterno, ad esempio un'applicazione client. Gli strumenti di gestione di SQL non possono avviare un'istanza utente.  
  
> **Nota:** le istanze utente sono una funzionalità di [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] solo.  
  
> **Nota** da chiamare [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_child_instances**.  
  
|Colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|Nome dell'utente per cui è stata creata l'istanza utente.|  
|owning_principal_sid|nvarchar(256)|ID di sicurezza (SID) dell'entità proprietaria dell'istanza utente. Questo valore corrisponde al SID di Windows.|  
|owning_principal_sid_binary|varbinary(85)|Versione binaria del SID dell'utente proprietario dell'istanza utente|  
|**instance_name**|**nvarchar (128)**|Nome dell'istanza utente.|  
|**instance_pipe_name**|**nvarchar (260)**|Quando si crea un'istanza utente viene creata anche una named pipe a cui possono connettersi le applicazioni. Questo nome può essere utilizzato in una stringa di connessione per connettersi all'istanza utente.|  
|**os_process_id**|**Int**|ID del processo di Windows per l'istanza utente.|  
|**os_process_creation_date**|**DateTime**|Data e ora dell'ultimo avvio di questo processo dell'istanza utente.|  
|**heart_beat**|**nvarchar (5)**|Stato corrente dell'istanza utente, ovvero ALIVE o DEAD.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sulla vista a gestione dinamica, vedere [funzioni e viste a gestione dinamica &#40; Transact-SQL &#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione in linea.  
  
## <a name="see-also"></a>Vedere anche  
 [Istanze utente per utenti Non amministratori](http://msdn.microsoft.com/en-us/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



