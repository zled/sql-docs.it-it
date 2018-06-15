---
title: Sys.dm os_performance_counters (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_performance_counters
- sys.dm_os_performance_counters_TSQL
- dm_os_performance_counters_TSQL
- sys.dm_os_performance_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_performance_counters dynamic management view
ms.assetid: a1c3e892-cd48-40d4-b6be-2a9246e8fbff
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1bdbd9ea7029aaf8b18631a2303fdd1228ff0198
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34466877"
---
# <a name="sysdmosperformancecounters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Restituisce una riga per contatore delle prestazioni gestito dal server. Per informazioni su ogni contatore delle prestazioni, vedere [usare oggetti di SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_performance_counters**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Categoria di appartenenza del contatore.|  
|**counter_name**|**nchar(128)**|Nome del contatore. Per ottenere ulteriori informazioni su un contatore, questo è il nome dell'argomento da selezionare dall'elenco dei contatori [usare oggetti di SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**nome_istanza**|**nchar(128)**|Nome dell'istanza specifica del contatore. Spesso include il nome del database.|  
|**cntr_value**|**bigint**|Valore corrente del contatore.<br /><br /> **Nota:** per i contatori al secondo, questo valore è cumulativo. Il valore relativo alla frequenza deve essere calcolato tramite il campionamento del valore a intervalli di tempo discreti. La differenza tra due valori di campionamento successivi è uguale alla frequenza dell'intervallo di tempo utilizzato.|  
|**cntr_type**|**int**|Tipo di contatore definito dall'architettura di controllo delle prestazioni di Windows. Vedere [tipi di contatori delle prestazioni WMI](http://msdn2.microsoft.com/library/aa394569.aspx) su MSDN o la documentazione di Windows Server per ulteriori informazioni sui tipi di contatori delle prestazioni.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 Se l'istanza dell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di visualizzare i contatori delle prestazioni del sistema operativo Windows, utilizzare la query [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente per verificare se i contatori delle prestazioni sono stati disabilitati.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Se il valore restituito è di 0 righe, i contatori delle prestazioni sono stati disabilitati. È necessario quindi analizzare il log del programma di installazione e ricercare l'errore 3409 "Reinstallare sqlctr.ini e verificare che l'account di accesso dell'istanza disponga delle autorizzazioni di Registro di sistema appropriate".  Questo errore indica che i contatori delle prestazioni non sono stati abilitati. Gli errori immediatamente precedenti all'errore 3409 dovrebbero indicare la causa principale per l'errore relativo all'abilitazione dei contatori delle prestazioni. Per ulteriori informazioni sui file di log di installazione, vedere [visualizzare e leggere i file registro il programma di installazione di SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="permission"></a>Autorizzazione

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
 
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti i valori dei contatori di prestazioni.  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
  [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


