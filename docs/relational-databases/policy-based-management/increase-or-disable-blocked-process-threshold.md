---
title: Aumentare o disabilitare l'opzione blocked process threshold | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 01454bfb5bf11f0ed6136bd4caca4937f198ba0b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="increase-or-disable-blocked-process-threshold"></a>Aumento o disabilitazione dell'opzione blocked process threshold
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Queste regole controllano che l'opzione blocked process threshold sia impostata su 0, o disabilitata, o su un valore maggiore o uguale a 5 (secondi). L'impostazione dell'opzione blocked process threshold su un valore compreso tra 1 e 4 comporta l'esecuzione continua del monitoraggio deadlock. È consigliabile utilizzare i valori compresi tra 1 e 4 solo per la risoluzione dei problemi e mai a lungo termine o in un ambiente di produzione senza l'assistenza del Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Per risolvere questo problema, impostare l'opzione blocked process threshold su un valore maggiore o uguale a 5 oppure su 0 per disabilitarla. Per impostare l'opzione su un valore di `5` secondi, eseguire l'istruzione seguente:  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzione di configurazione del server blocked process threshold](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
