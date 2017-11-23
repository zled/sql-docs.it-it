---
title: Sys. sysservers (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e05b06dd6a37f6330f715b374e3fe46515c3f37d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni server accessibile come origine dati OLE DB da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**srvID**|**smallint**|ID del server remoto (solo per uso locale).|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SRVNAME**|**sysname**|Nome del server.|  
|**srvproduct**|**sysname**|Nome del prodotto del server remoto.|  
|**ProviderName**|**nvarchar (128)**|Nome del provider OLE DB per l'accesso al server.|  
|**origine dati**|**nvarchar(4000)**|Valore dell'origine dei dati OLE DB.|  
|**percorso**|**nvarchar(4000)**|Valore della posizione di OLE DB.|  
|**PROVIDERSTRING**|**nvarchar(4000)**|Valore stringa del provider OLE DB.|  
|**schemadate**|**datetime**|Data dell'ultimo aggiornamento della riga.|  
|**topologyx**|**int**|Non usato.|  
|**topologyy**|**int**|Non usato.|  
|**catalogo**|**sysname**|Catalogo utilizzato quando viene stabilita una connessione a un provider OLE DB.|  
|**srvcollation**|**sysname**|Regole di confronto del server.|  
|**ConnectTimeout**|**int**|Impostazione del timeout per la connessione al server.|  
|**QueryTimeout**|**int**|Impostazione del timeout per le query eseguite sul server.|  
|**srvnetname**|**Char (30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = Server remoto.<br /><br /> 0 = Server collegato.|  
|**RPC**|**bit**|1 =  **sp_serveroption@rpc**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@rpc**  impostato su **false** o **off**.|  
|**pubblicazione**|**bit**|1 =  **sp_serveroption@pub**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@pub**  impostato su **false** o **off**.|  
|**Sub**|**bit**|1 =  **sp_serveroption@sub**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@sub**  impostato su **false** o **off**.|  
|**Dist**|**bit**|1 =  **sp_serveroption@dist**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@dist**  impostato su **false** o **off**.|  
|**dpub**|**bit**|1 =  **sp_serveroption@dpub**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@dpub**  impostato su **false** o **off**.|  
|**rpcout**|**bit**|1 =  **sp_serveroption@rpc out** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@rpc out** impostato su **false** o **off**.|  
|**DataAccess**|**bit**|1 =  **sp_serveroption@data accesso** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@data accesso** impostato su **false** o **off**.|  
|**collationcompatible**|**bit**|1 =  **sp_serveroption@collation compatibile** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@collation compatibile** impostato su **false** o **off**.|  
|**sistema**|**bit**|1 =  **sp_serveroption@system**  impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@system**  impostato su **false** o **off**.|  
|**UseRemoteCollation**|**bit**|1 =  **sp_serveroption@remote delle regole di confronto** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@remote delle regole di confronto** impostato su **false** o **off**.|  
|**lazyschemavalidation**|**bit**|1 =  **sp_serveroption@lazy convalida dello schema** impostato su **true** o **su**.<br /><br /> 0 =  **sp_serveroption@lazy convalida dello schema** impostato su **false** o **off**.|  
|**regole di confronto**|**sysname**|Regole di confronto come impostato dal server  **sp_serveroption@collation nome**.|  
|**nonsqlsub**|bit|0 = il server è un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1 = il server non è un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
