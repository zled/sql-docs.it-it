---
title: Verificare l'impostazione relativa al numero massimo di thread di lavoro | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b571ab8bebfd49bb252e9f250307d984036265b
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="verify-max-worker-threads-setting"></a>Verifica dell'impostazione relativa al numero massimo di thread di lavoro
  Questa regola consente di controllare l'opzione server relativa al numero massimo di thread di lavoro per individuare l'eventuale presenza di impostazioni non corrette. L'impostazione dell'opzione relativa al numero massimo di thread di lavoro su un valore troppo basso può comportare la presenza di un numero insufficiente di thread per l'elaborazione tempestiva delle richieste client in ingresso e provocare una mancanza di thread. L'impostazione di questa opzione su un valore elevato, tuttavia, può causare uno spreco di spazio, in quanto ogni nei server a 64 bit ogni thread attivo utilizza fino a 4 MB.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione max worker threads su 0. In questo modo, il numero corretto di thread di lavoro attivi verrà determinato automaticamente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in base alle richieste dell'utente.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Configurare l'opzione di configurazione del server max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

