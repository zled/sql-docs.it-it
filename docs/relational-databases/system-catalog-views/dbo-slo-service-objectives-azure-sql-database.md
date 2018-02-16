---
title: dbo.slo_service_objectives (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
f1_keywords:
- dbo.slo_service_objectives
- dbo.slo_service_objectives_TSQL
- slo_service_objectives
- slo_service_objectives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.slo_service_objectives
- slo_service_objectives
ms.assetid: d5dd7ed9-440a-4432-ad45-644e4e72318f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a5d3a911aa1ffa5088f2a817c2434c98eb7cbe3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="dbosloserviceobjectives-azure-sql-database"></a>dbo.slo_service_objectives (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  Questa funzionalità è in uno stato di anteprima ed è stata deprecata in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (V12). Non specificare una dipendenza dall'implementazione specifica di questa funzionalità perché potrebbe essere modificata o rimossa in una versione successiva.  
  
 Restituisce le informazioni sull'obiettivo del livello di servizio (SLO) nel server corrente.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11.|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|objective_id|**uniqueidentifier**|ID dell'obiettivo del livello di servizio.|  
|name|**sysname**|Nome dell'obiettivo del livello di servizio.|  
|description|**nvarchar**|Descrizione dell'obiettivo del livello di servizio.|  
|create_date|**datetimeoffset(7)**|Data di creazione dell'obiettivo del livello di servizio nel server.|  
|is_system|**bit**|1 = obiettivo del livello di servizio di sistema|  
|is_default|**bit**|1 = viene utilizzato l'obiettivo del livello di servizio predefinito.|  
|state|**tinyint**|1 = l'obiettivo del livello di servizio è abilitato.<br /><br /> 2 = l'obiettivo del livello di servizio è disabilitato.|  
|state_desc|**nvarchar**|Descrizione dell'obiettivo del livello di servizio.|  
|metadata_version|**decimal**|Versione dell'obiettivo del livello di servizio.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di database Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
