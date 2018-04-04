---
title: Piano di manutenzione (Gestisci connessioni) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
caps.latest.revision: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f7a35cc6e39beb2e81b092d862b881e4922c491
ms.sourcegitcommit: 6e16d1616985d65484c72f5e0f34fb2973f828f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2018
---
# <a name="maintenance-plan-manage-connections"></a>Piano di manutenzione (Gestisci connessioni)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilizzare la finestra di dialogo **Gestisci connessioni** per specificare le proprietà delle connessioni utilizzate dai piani di manutenzione. Quando si crea un piano di manutenzione viene creata una connessione locale al server in cui è stato creato il piano. Utilizzare questa connessione per creare le attività che vengono eseguite nella connessione locale. Se richiesto, utilizzare la finestra di dialogo **Gestisci connessioni** per aggiungerle. Le connessioni aggiuntive configurate vengono visualizzate nella casella delle connessioni di ogni attività.  
  
## <a name="options"></a>Opzioni  
 **Server**  
 Istanza del server.  
  
 **Autenticazione**  
 Indica se la connessione utilizza l'autenticazione di Windows oppure l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

> [!IMPORTANT]  
> Il pacchetto è archiviato nel database **msdb** insieme al relativo set **ProtectionLevel** impostato su **ServerStorage**. In questo modo, se si usa l'*autenticazione di SQL Server*, la password non sarà crittografata in **msdb**. È possibile usare l'*autenticazione di SQL Server* purché il database **msdb** sia protetto. È tuttavia consigliabile usare l'*autenticazione di Windows*

## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
