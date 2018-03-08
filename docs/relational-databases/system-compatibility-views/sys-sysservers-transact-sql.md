---
title: sys.sysservers (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95f88c44e0501fab834bb476e0350cf48bc91757
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni server accessibile come origine dati OLE DB da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|ID del server remoto (solo per uso locale).|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|Nome del server.|  
|**srvproduct**|**sysname**|Nome del prodotto del server remoto.|  
|**providername**|**nvarchar(128)**|Nome del provider OLE DB per l'accesso al server.|  
|**datasource**|**nvarchar(4000)**|Valore dell'origine dei dati OLE DB.|  
|**location**|**nvarchar(4000)**|Valore della posizione di OLE DB.|  
|**providerstring**|**nvarchar(4000)**|Valore stringa del provider OLE DB.|  
|**schemadate**|**datetime**|Data dell'ultimo aggiornamento della riga.|  
|**topologyx**|**int**|Non usato.|  
|**topologyy**|**int**|Non usato.|  
|**catalog**|**sysname**|Catalogo utilizzato quando viene stabilita una connessione a un provider OLE DB.|  
|**srvcollation**|**sysname**|Regole di confronto del server.|  
|**connecttimeout**|**int**|Impostazione del timeout per la connessione al server.|  
|**querytimeout**|**int**|Impostazione del timeout per le query eseguite sul server.|  
|**srvnetname**|**char(30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = Server remoto.<br /><br /> 0 = Server collegato.|  
|**rpc**|**bit**|1 =  **sp_serveroption@rpc**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@rpc**  impostato su **false** o **off**.|  
|**pub**|**bit**|1 =  **sp_serveroption@pub**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@pub**  impostato su **false** o **off**.|  
|**sub**|**bit**|1 =  **sp_serveroption@sub**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@sub**  impostato su **false** o **off**.|  
|**dist**|**bit**|1 =  **sp_serveroption@dist**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@dist**  impostato su **false** o **off**.|  
|**dpub**|**bit**|1 =  **sp_serveroption@dpub**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@dpub**  impostato su **false** o **off**.|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpc out** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@rpc out** impostato su **false** o **off**.|  
|**dataaccess**|**bit**|1 =  **sp_serveroption@data accesso** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@data accesso** impostato su **false** o **off**.|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation compatibile** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@collation compatibile** impostato su **false** o **off**.|  
|**system**|**bit**|1 =  **sp_serveroption@system**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@system**  impostato su **false** o **off**.|  
|**useremotecollation**|**bit**|1 =  **sp_serveroption@remote delle regole di confronto** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@remote delle regole di confronto** impostato su **false** o **off**.|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazy convalida dello schema** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@lazy convalida dello schema** impostato su **false** o **off**.|  
|**regole di confronto**|**sysname**|Regole di confronto come impostato dal server  **sp_serveroption@collation nome**.|  
|**nonsqlsub**|bit|0 = il server è un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1 = server non è un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
