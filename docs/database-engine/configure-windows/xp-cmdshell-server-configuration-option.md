---
title: Opzione di configurazione del server xp_cmdshell | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords: xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Active
ms.openlocfilehash: 26f411ba59dba9213e5432cd1ef36f346caed509
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="xpcmdshell-server-configuration-option"></a>Opzione di configurazione del server xp_cmdshell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'opzione **xp_cmdshell** è un'opzione di configurazione server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che consente agli amministratori di sistema di controllare se la stored procedure estesa **xp_cmdshell** può essere eseguita in un sistema. Nelle nuove installazioni l'opzione **xp_cmdshell** è disabilitata per impostazione predefinita e può essere abilitata usando la gestione basata su criteri oppure eseguendo la stored procedure di sistema **sp_configure** , come illustrato nell'esempio di codice seguente:  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
