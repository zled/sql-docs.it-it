---
title: dbo.slo_service_objectives (Database SQL di Azure) | Documenti Microsoft
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/04/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
f1_keywords:
- dbo.slo_service_objectives
- dbo.slo_service_objectives_TSQL
- slo_service_objectives
- slo_service_objectives_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_service_objectives
- slo_service_objectives
ms.assetid: d5dd7ed9-440a-4432-ad45-644e4e72318f
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5330bc8977c0e043f27cb5f035510c5da007e0c4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="dbosloserviceobjectives-azure-sql-database"></a>dbo.slo_service_objectives (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

    
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
|create_date|**DateTimeOffset(7)**|Data di creazione dell'obiettivo del livello di servizio nel server.|  
|is_system|**bit**|1 = obiettivo del livello di servizio di sistema|  
|is_default|**bit**|1 = viene utilizzato l'obiettivo del livello di servizio predefinito.|  
|state|**tinyint**|1 = l'obiettivo del livello di servizio è abilitato.<br /><br /> 2 = l'obiettivo del livello di servizio è disabilitato.|  
|state_desc|**nvarchar**|Descrizione dell'obiettivo del livello di servizio.|  
|metadata_version|**decimal**|Versione dell'obiettivo del livello di servizio.|  
  
## <a name="permissions"></a>Permissions  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di database Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
