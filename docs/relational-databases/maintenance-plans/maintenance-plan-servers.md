---
title: Piano di manutenzione (Server) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8732096583ee6ebb02bf81ab5cb9d4f392927cac
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="maintenance-plan-servers"></a>Piano di manutenzione (Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Usare la finestra di dialogo **Server** per selezionare i server in cui si vuole eseguire il piano di manutenzione.  
  
 Per creare un piano di manutenzione multiserver, è necessario configurare un ambiente multiserver composto da un server master e uno o più server di destinazione. Per i piani di manutenzione multiserver, il server locale deve essere configurato come server master. Negli ambienti multiserver, in questa finestra di dialogo vengono visualizzati il server master **(local)** e tutti i server di destinazione corrispondenti. Viene creato un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per il server locale. Tale processo sarà abilitato o disabilitato a seconda che si selezioni o meno il server **(local)** . Se vengono selezionati server di destinazione, viene creato un processo multiserver e tale processo viene poi scaricato in ognuno dei server di destinazione selezionati. Se non viene selezionato alcun server di destinazione, il processo multiserver viene eliminato.  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Creazione di un ambiente multiserver](http://msdn.microsoft.com/library/edc2b60d-15da-40a1-8ba3-f1d473366ee6)   
 [Configurare un server master](http://msdn.microsoft.com/library/05739a73-1fdf-4d9d-92a6-70f328380322)   
 [Configurare un server di destinazione](http://msdn.microsoft.com/library/13aabe2d-67fe-4c67-8d49-2928dd705b7a)  
  
  
