---
title: dbo. slo_assignment_history (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
- slo_assignment_history_TSQL
- dbo.slo_assignment_history_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
ms.assetid: 048a6fb5-2fc2-4d12-a436-4c53ecd413f3
caps.latest.revision: "9"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fcff1c5141e6556f8cb4184284769e3be537f80a
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="dbosloassignmenthistory-azure-sql-database"></a>dbo.slo_assignment_history (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  **Si applica solo alle [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.**  
>   
>  Questa funzionalità si trova nello stato anteprima. Non specificare una dipendenza dall'implementazione specifica di questa funzionalità perché potrebbe essere modificata o rimossa in una versione successiva.  
  
 Restituisce la cronologia delle assegnazioni SLO del database nel server, incluse le seguenti informazioni:  
  
-   La cronologia delle assegnazioni SLO del database nel server.  
  
-   L'ora di inizio e di fine di ciascuna richiesta di modifica SLO del database.  
  
-   Tutti gli errori di assegnazione SLO che sono registrati nelle colonne error_code and error_desc.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_name|**sysname**|Nome del database.|  
|database_id|**int**|ID del database.|  
|create_date|**datetimeoffset(7)**|Data di creazione del database.|  
|service_objective_name|**sysname**|Nome dell'obiettivo del livello di servizio (SLO).|  
|service_objective_id|**uniqueidentifier**|ID dello SLO.|  
|operation_id|**uniqueidentifier**|ID dell'operazione.|  
|operation_start_time|**datetimeoffset(7)**|Ora di inizio della richiesta di modifica SLO del database.|  
|operation_end_time|**datetimeoffset(7)**|Ora di fine della richiesta di modifica SLO del database.|  
|error_code|**int**|Codice di errore della richiesta di modifica SLO del database.|  
|error_desc|**nvarchar**|Descrizione dell'errore nella richiesta di modifica SLO del database.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la cronologia delle assegnazioni SLO per un database specificato.  
  
```  
SELECT *  
FROM dbo.slo_assignment_history   
WHERE database_name = '<DB NAME>’   
ORDER BY operation_start_time DESC;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di database Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
