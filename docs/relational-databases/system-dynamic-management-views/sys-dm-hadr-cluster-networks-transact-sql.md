---
title: sys.dm_hadr_cluster_networks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_hadr_cluster_networks
- sys.dm_hadr_cluster_networks_TSQL
- sys.dm_hadr_cluster_networks
- dm_hadr_cluster_networks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_networks dynamic management view
ms.assetid: ece32b15-d63f-4f93-92b7-e2930333e97a
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 003cb7c4a9bb64bc274830e42bfe717842de64f0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmhadrclusternetworks-transact-sql"></a>sys.dm_hadr_cluster_networks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni membro del cluster WSFC che partecipa alla configurazione della subnet di un gruppo di disponibilità. È possibile utilizzare questa DMV per convalidare l'indirizzo IP virtuale di rete configurato per ogni replica di disponibilità.  
  
 Chiave primaria: **member_name** + **network_subnet_IP** + **network_subnet_prefix_length**  
  
 > [!TIP]
 > A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], questa DMV supporta Cluster di istanze di Failover AlwaysOn oltre ai gruppi di disponibilità AlwaysOn.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**MEMBER_NAME**|**nvarchar(128)**|Nome computer di un nodo nel cluster WSFC.|  
|**network_subnet_ip**|**nvarchar(48)**|Indirizzo IP di rete della subnet a cui appartiene il computer. Può trattarsi di un indirizzo IPv4 o IPv6.|  
|**network_subnet_ipv4_mask**|**nvarchar(45)**|Subnet mask di rete che specifica la subnet a cui appartiene l'indirizzo IP. **network_subnet_ipv4_mask** per specificare le opzioni < network_subnet_option > DHCP in una clausola WITH DHCP del [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) o [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.<br /><br /> NULL = Subnet IPv6.|  
||||  
|**network_subnet_prefix_length**|**int**|Lunghezza del prefisso dell'indirizzo IP di rete che specifica la subnet a cui appartiene il computer.|  
|**is_public**|**bit**|Se la rete è privata o pubblica sul cluster WSFC, uno di:<br /><br /> 0 = Privato<br /><br /> 1 = Pubblico|  
|**is_ipv4**|**bit**|Tipo di subnet, uno di:<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Clustering di failover e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Monitorare gruppi di disponibilità & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [L'esecuzione di query il catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
