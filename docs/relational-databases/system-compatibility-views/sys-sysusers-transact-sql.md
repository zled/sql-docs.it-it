---
title: sys.sysusers (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs:
- TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 661d42fbc8b55250ac38fb84e44faa33701c20b2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni [!INCLUDE[msCoName](../../includes/msconame-md.md)] utente di Windows, il gruppo di Windows, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utente, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruolo nel database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**uid**|**smallint**|ID utente, univoco all'interno del database.<br /><br /> 1 = Proprietario del database.<br /><br /> Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|Nome utente o di gruppo, univoco all'interno del database.|  
|**sid**|**varbinary(85)**|Identificatore di sicurezza per la voce specificata.|  
|**ruoli**|**varbinary(2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|Data in cui è stato aggiunto l'account.|  
|**updatedate**|**datetime**|Data dell'ultima modifica dell'account.|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
|**password**|**varbinary(256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**gid**|**smallint**|ID del gruppo a cui appartiene l'utente. Se **uid** equivale **gid**, questa voce viene definito un gruppo. Causa un errore di overflow o restituisce NULL se il numero combinato di gruppi e utenti è maggiore di 32.767.|  
|**environ**|**varchar(255)**|Riservato.|  
|**hasdbaccess**|**int**|1 = L'account ha accesso al database.|  
|**islogin**|**int**|1 = L'account è un gruppo di Windows, un utente di Windows oppure un utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con un account di accesso.|  
|**isntname**|**int**|1 = L'account è un utente o un gruppo di Windows.|  
|**isntgroup**|**int**|1 = L'account è un gruppo di Windows.|  
|**isntuser**|**int**|1 = L'account è un utente di Windows.|  
|**issqluser**|**int**|1 = L'account è un utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isaliased**|**int**|1 = L'account è assegnato come alias a un altro utente.|  
|**issqlrole**|**int**|1 = L'account è un ruolo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isapprole**|**int**|1 = L'account è un ruolo applicazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
