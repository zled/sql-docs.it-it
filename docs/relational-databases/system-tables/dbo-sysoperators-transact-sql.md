---
title: dbo.sysoperators (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs: TSQL
helpviewer_keywords: sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0b48cdf057e17d0c043f2716071868b9188874d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni operatore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'operatore.|  
|**name**|**sysname**|Nome dell'operatore.|  
|**abilitato**|**tinyint**|Stato delle notifiche di avvisi (booleano). Se **1**, questo operatore può ricevere notifiche quando viene generato un avviso.|  
|**email_address**|**nvarchar (100)**|Indirizzo di posta elettronica dell'operatore.|  
|**last_email_date**|**int**|Data dell'ultima notifica di avviso tramite posta elettronica ricevuta dall'operatore.|  
|**last_email_time**|**int**|Ora dell'ultima notifica di avviso tramite posta elettronica ricevuta dall'operatore.|  
|**pager_address**|**nvarchar (100)**|Indirizzo cercapersone dell'operatore.|  
|**last_pager_date**|**int**|Data dell'ultima notifica di avviso tramite cercapersone ricevuta dall'operatore.|  
|**last_pager_time**|**int**|Ora dell'ultima notifica di avviso tramite cercapersone ricevuta dall'operatore|  
|**weekday_pager_start_time**|**int**|Ora dopo la quale l'operatore è disponibile per ricevere notifiche di avvisi tramite cercapersone nei giorni feriali (da lunedì a venerdì).|  
|**weekday_pager_end_time**|**int**|Ora dopo la quale l'operatore non è disponibile per ricevere notifiche di avvisi tramite cercapersone nei giorni feriali (da lunedì a venerdì).|  
|**saturday_pager_start_time**|**int**|Ora dopo la quale l'operatore è disponibile per ricevere notifiche di avvisi tramite cercapersone il sabato.|  
|**saturday_pager_end_time**|**int**|Ora dopo la quale l'operatore non è disponibile per ricevere notifiche di avvisi tramite cercapersone il sabato.|  
|**sunday_pager_start_time**|**int**|Ora dopo la quale l'operatore è disponibile per ricevere notifiche di avvisi tramite cercapersone la domenica.|  
|**sunday_pager_end_time**|**int**|Ora dopo la quale l'operatore non è disponibile per ricevere notifiche di avvisi tramite cercapersone la domenica.|  
|**pager_days**|**tinyint**|Maschera di bit che rappresenta i giorni della settimana durante i quali l'operatore è disponibile per ricevere una notifica di avviso tramite cercapersone.|  
|**netsend_address**|**nvarchar (100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**int**|Data dell'ultimo messaggio di rete inviato all'ID dell'operatore specificato.|  
|**last_netsend_time**|**int**|Ora dell'ultimo messaggio di rete inviato all'ID dell'operatore specificato.|  
|**category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di SQL Server Agent &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
