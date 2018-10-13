---
title: Sys.dm server_services (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8acb2fae0aa0edadf1995a0a103ff60b66a912a9
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072135"
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui servizi SQL Server, Full-text e SQL Server Agent nell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Per segnalare informazioni sullo stato di tali servizi, utilizzare la DMV.  
  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Nome del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Full-text, o un servizio di SQL Server Agent. Non può essere null.|  
|startup_type|**int**|Indica la modalità di avvio del servizio. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> 0: altro<br />1: altro<br />2: automatica<br />3: manuale<br />4: disabilitato<br /><br /> Ammette i valori Null.|  
|startup_desc|**nvarchar(256)**|Descrive la modalità di avvio del servizio. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> Altro: Altro (esecuzione avvio)<br />Altro: Altro (avvio del sistema)<br />Automatico: L'avvio automatico<br />Manuale: Avvio richiesta<br />Disabilitato: disabilitato<br /><br /> Non può essere null.|  
|status|**int**|Indica lo stato corrente del servizio. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> 1: arrestato<br />2: altro (avvio in sospeso)<br />3: altri (arresto in sospeso)<br />4: in esecuzione<br />5: altro (in attesa della ripresa)<br />6: altre (sospensione in sospeso)<br />7: in pausa<br /><br /> Ammette i valori Null.|  
|status_desc|**nvarchar(256)**|Descrive lo stato corrente del servizio. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> Arrestato: Il servizio viene arrestato.<br />Altri (operazione di avvio in sospeso): il servizio è in corso di avvio.<br />Altri (operazione di arresto in sospeso): il servizio è in corso l'arresto.<br />In esecuzione: Il servizio è in esecuzione.<br />Altri (continuare le operazioni in sospeso): il servizio è in sospeso.<br />Altra (in attesa della sospensione): il servizio è in corso la sospensione.<br />Sospeso: Il servizio è sospeso.<br /><br /> Non può essere null.|  
|process_id|**int**|ID di processo del servizio. Non può essere null.|  
|last_startup_time|**datetimeoffset(7)**|Data e ora dell'ultimo avvio del servizio. Ammette i valori Null.|  
|service_account|**nvarchar(256)**|Account autorizzato a controllare il servizio. L'account consente di avviare o arrestare il servizio oppure di modificarne le proprietà. Non può essere null.|  
|filename|**nvarchar(256)**|Percorso e nome file dell'eseguibile del servizio. Non può essere null.|  
|is_clustered|**nvarchar(1**|Indica se il servizio è installato come risorsa di un server di cluster. Non può essere null.|  
|cluster_nodename|**nvarchar(256)**|Il nome del nodo del cluster su cui è installato il servizio. Ammette i valori Null.|
|instant_file_initialization_enabled|**nvarchar(1**|Specifica se l'inizializzazione immediata dei file è abilitato per il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] servizio.<br /><br />Y = inizializzazione immediata dei file è abilitato per il servizio.<br /><br />N = inizializzazione immediata dei file è disabilitato per il servizio.<br /><br /> Ammette i valori Null.<br /><br /> **Nota:** non si applica ad altri servizi, ad esempio SQL Server Agent.<br /><br /> **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  

## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione `VIEW SERVER STATE` per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
