---
title: Opzione di configurazione del server xp_cmdshell | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6d403205c3fc3ef57fcfa7e566f0913f00604862
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="xpcmdshell-server-configuration-option"></a>Opzione di configurazione del server xp_cmdshell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'opzione **xp_cmdshell** è un'opzione di configurazione server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che consente agli amministratori di sistema di controllare se la stored procedure estesa **xp_cmdshell** può essere eseguita in un sistema. Per impostazione predefinita, nelle nuove installazioni l'opzione **xp_cmdshell** risulta disabilitata. Prima di abilitarla, è importante considerare le potenziali implicazioni per la sicurezza associate all'uso di questa opzione. Il codice appena sviluppato non deve usare questa opzione perché in genere deve rimanere disabilitata. In alcune applicazioni legacy è necessario che sia abilitata e, se non si possono modificare per evitare di usarla, è possibile abilitarla usando la gestione basata su criteri o eseguendo la stored procedure di sistema **sp_configure**, come illustrato nell'esempio di codice seguente:  
  
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
  
  
