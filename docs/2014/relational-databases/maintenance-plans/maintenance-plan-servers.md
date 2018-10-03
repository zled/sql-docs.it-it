---
title: Piano di manutenzione (Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: df05d1f7bdbcf2f149caf1b82b592607d588b0ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050413"
---
# <a name="maintenance-plan-servers"></a>Piano di manutenzione (Server)
  Utilizzare la finestra di dialogo **Server** per selezionare i server in cui si desidera eseguire il piano di manutenzione.  
  
 Per creare un piano di manutenzione multiserver, è necessario configurare un ambiente multiserver composto da un server master e uno o più server di destinazione. Per i piani di manutenzione multiserver, il server locale deve essere configurato come server master. Negli ambienti multiserver, in questa finestra di dialogo vengono visualizzati il server master **(local)** e tutti i server di destinazione corrispondenti. Viene creato un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per il server locale. Tale processo sarà abilitato o disabilitato a seconda che si selezioni o meno il server **(local)** . Se vengono selezionati server di destinazione, viene creato un processo multiserver e tale processo viene poi scaricato in ognuno dei server di destinazione selezionati. Se non viene selezionato alcun server di destinazione, il processo multiserver viene eliminato.  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](maintenance-plans.md)   
 [Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md)   
 [Configurare un server master](../../ssms/agent/make-a-master-server.md)   
 [Configurare un server di destinazione](../../ssms/agent/make-a-target-server.md)  
  
  
