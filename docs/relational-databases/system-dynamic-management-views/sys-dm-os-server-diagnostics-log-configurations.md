---
title: Sys.dm os_server_diagnostics_log_configurations | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d9c2ef6f2133e9fffb870b8aa89cbf6b7b9f1c94
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Restituisce una riga con la configurazione corrente per il log di diagnostica del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Queste impostazioni delle proprietà determinano se la registrazione di diagnostica è abilitata o disabilitata e il percorso, il numero e la dimensione dei file di log.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|Indica se la registrazione è abilitata o disabilitata.<br /><br /> 1 = la registrazione dei dati di diagnostica è abilitata<br /><br /> 0 = la registrazione dei dati di diagnostica è disabilitata|  
|max_size|**int**|Dimensione massima in megabyte che può raggiungere ogni log di diagnostica. Il valore predefinito è 100 MB.|  
|max_files|**int**|Numero massimo di file di log di diagnostica che è possibile archiviare nel computer prima che vengano riciclati per nuovi log di diagnostica.|  
|percorso|**nvarchar(260)**|Percorso che indica la posizione dei log di diagnostica. Il percorso predefinito è \<\MSSQL\Log> all'interno della cartella di installazione dell'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede le autorizzazioni VIEW SERVER STATE sull'istanza del cluster di failover di SQL Server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato sys.dm_os_server_diagnostics_log_configurations per restituire le impostazioni delle proprietà per i log di diagnostica del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program Files\Microsoft SQL Server\MSSQL13\MSSQL\Log >|10|10|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione e lettura del log di diagnostica dell'istanza del cluster di failover](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
