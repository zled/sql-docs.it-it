---
title: "SQL Server, Memory Node | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# SQL Server, Memory Node
  L'oggetto **Memory Node** di Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce contatori per il monitoraggio dell'utilizzo della memoria del server in nodi NUMA.  
  
## Contatori Memory Node  
 Nella tabella seguente vengono descritti i contatori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** .  
  
|Contatori Memory Manager di SQL Server|Descrizione|  
|----------------------------------------|-----------------|  
|**Memoria nodo database (KB)**|Specifica la quantità di memoria utilizzata dal server nel nodo per le pagine del database.|  
|**Memoria nodo disponibile (KB)**|Specifica la quantità di memoria non utilizzata dal server nel nodo.|  
|**Memoria nodo esterna (KB)**|Specifica la quantità di memoria non locale NUMA nel nodo.|  
|**Memoria nodo prelevata (KB)**|Specifica la quantità di memoria utilizzata dal server nel nodo per scopi diversi dalle pagine del database.|  
|**Memoria nodo di destinazione**|Specifica la quantità di memoria ideale per il nodo.|  
|**Memoria nodo totale**|Indica la quantità totale di memoria riservata dal server nel nodo.|  
  
## Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Oggetto di Gestione buffer di SQL Server](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  