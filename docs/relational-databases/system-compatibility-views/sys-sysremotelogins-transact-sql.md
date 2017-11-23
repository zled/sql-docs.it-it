---
title: Sys.sysremotelogins (Transact-SQL) | Documenti Microsoft
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
- sysremotelogins
- sysremotelogins_TSQL
- sys.sysremotelogins
- sys.sysremotelogins_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysremotelogins system table
- sys.sysremotelogins compatibility view
ms.assetid: b7ffcfa6-aed8-41d4-8b70-845439ab813d
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b5e4b4e9bfc12526e3257621dcda35f46884f2c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syssysremotelogins-transact-sql"></a>sys.sysremotelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni utente remoto che è autorizzato a chiamare stored procedure remote in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**remoteserverid**|**smallint**|Identificazione del server remoto.|  
|**remoteusername**|**sysname**|Nome dell'account di accesso dell'utente in un server remoto.|  
|**status**|**smallint**|Viene restituito 0.|  
|**SID**|**varbinary (85)**|ID di sicurezza dell'utente di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|  
|**ChangeDate**|**datetime**|Data e ora di aggiunta dell'utente remoto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
