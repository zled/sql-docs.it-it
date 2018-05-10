---
title: Sys.dm os_cluster_nodes (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_cluster_nodes_TSQL
- dm_os_cluster_nodes_TSQL
- dm_os_cluster_nodes
- sys.dm_os_cluster_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_cluster_nodes dynamic management view
ms.assetid: 92fa804e-2d08-42c6-a36f-9791544b1d42
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 899240e32383b283396c45d866682dc6f1bafb45
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosclusternodes-transact-sql"></a>sys.dm_os_cluster_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni nodo nella configurazione dell'istanza del cluster di failover. Se l'istanza corrente è un'istanza cluster di failover, restituisce un elenco di nodi in cui è stata definita l'istanza del cluster di failover, in precedenza denominata "server virtuale". Se l'istanza del server corrente non è un'istanza del cluster di failover, restituisce un set di righe vuoto.  
  
> **Nota:** per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oppure [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare il nome **sys.dm_pdw_nodes_os_cluster_nodes**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nodeName**|**sysname**|Nome di un nodo nella configurazione (server virtuale) dell'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|status|**int**|Stato del nodo in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza cluster di failover: 0, 1, 2, 3, -1. Per ulteriori informazioni, vedere [funzione GetClusterNodeState](http://go.microsoft.com/fwlink/?LinkId=204794).|  
|status_description|**nvarchar(20)**|Descrizione dello stato del nodo del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = funzionante<br /><br /> 1 = non funzionante<br /><br /> 2 = in pausa<br /><br /> 3 = partecipante<br /><br /> -1 = sconosciuto|  
|is_current_owner|bit|1 indica che il nodo è il proprietario corrente della risorsa cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando il clustering di failover è abilitato, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere eseguita in qualsiasi nodo del cluster di failover designato come parte della configurazione (server virtuale) dell'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> **Nota:** questa vista sostituirà la funzione fn_virtualservernodes, che sarà deprecata in una versione futura.  
  
## <a name="permissions"></a>Autorizzazioni  
 Nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è richiesta l'autorizzazione VIEW SERVER STATE nel database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata la vista sys. dm_os_cluster_nodes per determinare i nodi di un'istanza del server di cluster.  
  
```  
SELECT NodeName, status, status_description, is_current_owner   
FROM sys.dm_os_cluster_nodes;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|NodeName|status|status_description|is_current_owner|  
|--------------|------------|-------------------------|------------------------|  
|node1|0|up|1|  
|node2|0|up|0|  
|Nodo3|1|down|0|  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_os_cluster_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-properties-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  



