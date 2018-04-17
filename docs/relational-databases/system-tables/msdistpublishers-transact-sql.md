---
title: MSdistpublishers (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dc2adcd101a2f974b441cef792668dcd61c25d4c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Il **MSdistpublishers** tabella contiene una riga per ogni server di pubblicazione remoto supportato dal server di distribuzione locale. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del server di pubblicazione remoto supportato dal server di distribuzione locale.|  
|**distribution_db**|**sysname**|Nome del database di distribuzione.|  
|**working_directory**|**nvarchar(255)**|Nome della directory di lavoro utilizzata per archiviare i file dei dati e di schema per la pubblicazione|  
|**security_mode**|**int**|Modalità di sicurezza implementata nel server di distribuzione.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.<br /><br /> **1** = autenticazione di Windows.|  
|**login**|**sysname**|ID dell'account di accesso per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524**|Password (crittografata) per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Attiva**|**bit**|Indica se il server di distribuzione locale viene utilizzato dal server di pubblicazione remoto.|  
|**attendibile**|**bit**|Indica se il server di pubblicazione remoto utilizza la stessa password del server di distribuzione locale:<br /><br /> **0** = A password è necessaria nel server di pubblicazione remoto per connettersi al server di distribuzione.<br /><br /> **1** = No è necessaria la password.|  
|**third_party**|**bit**|Indica se il server di pubblicazione è un computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione. **1** = origine dei dati eterogenee.|  
|**publisher_type**|**sysname**|Tipo di server di pubblicazione:<br /><br /> **MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.<br /><br /> **ORACLE** = server di pubblicazione Oracle standard.<br /><br /> **ORACLE GATEWAY** = server di pubblicazione Oracle Gateway.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
