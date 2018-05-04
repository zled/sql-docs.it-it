---
title: MSsubscriber_info (Transact-SQL) | Documenti Microsoft
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
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 33b09b942cea3fc8e2da711ef956e86e85119a5d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mssubscriberinfo-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSsubscriber_info** tabella contiene una riga per ogni coppia server di pubblicazione/sottoscrizione che è vengono inviate sottoscrizioni push dal server di distribuzione locale. Questa tabella è archiviata nel database di distribuzione.  
  
 **Nota** questa tabella di sistema è stata deprecata e viene mantenuta per supportare le versioni precedenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**subscriber**|**sysname**|Nome del Sottoscrittore.|  
|**type**|**tinyint**|Tipo di Sottoscrittore:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittore.<br /><br /> **1** = origine dati ODBC.|  
|**login**|**sysname**|Account di accesso per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Viene archiviata in forma crittografata se il Sottoscrittore viene aggiunto con la modalità di autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524**|Password utilizzata per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Viene archiviata in forma crittografata se il Sottoscrittore viene aggiunto con la modalità di autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**description**|**nvarchar(255)**|Descrizione del Sottoscrittore.|  
|**security_mode**|**int**|Modalità di sicurezza implementata:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l'autenticazione di Windows.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
