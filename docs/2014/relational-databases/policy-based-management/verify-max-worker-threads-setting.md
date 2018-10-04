---
title: Verificare l'impostazione relativa al numero massimo di thread di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 01e397437c7ed2912b6d6225ee1f3bd5073a405c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185021"
---
# <a name="verify-max-worker-threads-setting"></a>Verifica dell'impostazione relativa al numero massimo di thread di lavoro
  Questa regola consente di controllare l'opzione server relativa al numero massimo di thread di lavoro per individuare l'eventuale presenza di impostazioni non corrette. L'impostazione dell'opzione relativa al numero massimo di thread di lavoro su un valore troppo basso può comportare la presenza di un numero insufficiente di thread per l'elaborazione tempestiva delle richieste client in ingresso e provocare una mancanza di thread. L'impostazione di questa opzione su un valore elevato, tuttavia, può provocare uno spreco di spazio, in quanto ogni thread attivo utilizza 512 KB nei server a 32 bit e fino a 4 MB nei server a 64 bit.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione max worker threads su 0. In questo modo, il numero corretto di thread di lavoro attivi verrà determinato automaticamente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in base alle richieste dell'utente.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Configurare l'opzione di configurazione del server max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
