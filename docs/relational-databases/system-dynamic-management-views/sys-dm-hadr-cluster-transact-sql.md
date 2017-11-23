---
title: Sys.dm hadr_cluster (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
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
- sys.dm_hadr_cluster
- dm_hadr_cluster_HADR
- sys.dm_hadr_cluster_TSQL
- dm_hadr_cluster
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: 13ce70e4-9d43-4a80-a826-099e6213bf85
caps.latest.revision: "20"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea7fef3018ef9e7c88100c1a0c3a7b444bfaeac7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadrcluster-transact-sql"></a>sys.dm_hadr_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Se il nodo di Windows Server Failover Clustering (WSFC) che ospita un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abilitato per [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] dispone del quorum WSFC, **Sys.dm hadr_cluster** restituisce una riga che espone il nome del cluster e informazioni sul quorum. Se il nodo WSFC non dispone di quorum, non viene restituita alcuna riga.  
 > [!TIP]
 > A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], questa DMV supporta Cluster di istanze di Failover AlwaysOn oltre ai gruppi di disponibilità AlwaysOn.

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**cluster_name**|**nvarchar (128)**|Nome del cluster WSFC che ospita le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abilitate per [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].|  
|**quorum_type**|**tinyint**|Tipo di quorum utilizzato da questo cluster WSFC, uno di:<br /><br /> 0 = Maggioranza dei nodi. Questa configurazione del quorum può sostenere errori della metà dei nodi (arrotondata) meno uno. Su un cluster a sette nodi, ad esempio, questa configurazione del quorum può sostenere tre errori di nodo.<br /><br /> 1 = Maggioranza dei nodi e dei dischi. Se il disco di controllo rimane online, questa configurazione del quorum può sostenere errori della metà dei nodi (arrotondamento per eccesso). Ad esempio, un cluster a sei nodi in cui il disco di controllo è online potrebbe sostenere tre errori di nodo. Se il disco di controllo viene portato offline o su di esso si verifica un errore, questa configurazione del quorum può sostenere errori della metà dei nodi (arrotondamento per eccesso) meno uno. Ad esempio, un cluster a sei nodi con un disco di controllo su cui si è verificato un errore potrebbe sostenere due (3-1=2) errori di nodo.<br /><br /> 2 = Maggioranza dei nodi e delle condivisioni file. Questa configurazione del quorum funziona in modo simile alla Maggioranza dei nodi e del disco, ma utilizza un server di controllo della condivisione file anziché un disco di controllo.<br /><br /> 3 = Nessuna maggioranza: solo disco. Se il disco del quorum è online, questa configurazione del quorum può sostenere errori di tutti i nodi tranne uno.|  
|**quorum_type_desc**|**varchar(50)**|Descrizione di **quorum_type**, uno di:<br /><br /> NODE_MAJORITY<br /><br /> NODE_AND_DISK_MAJORITY<br /><br /> NODE_AND_FILE_SHARE_MAJORITY<br /><br /> NO_MAJORITY:_DISK_ONLY|  
|**quorum_state**|**tinyint**|Stato del quorum WSFC, uno di:<br /><br /> 0 = Stato del quorum sconosciuto<br /><br /> 1 = Quorum normale<br /><br /> 2 = Quorum forzato|  
|**quorum_state_desc**|**varchar(50)**|Descrizione di **quorum_state**, uno di:<br /><br /> UNKNOWN_QUORUM_STATE<br /><br /> NORMAL_QUORUM<br /><br /> FORCED_QUORUM|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e DMV di Gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Viste del catalogo dei gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql.md)  
  
  
