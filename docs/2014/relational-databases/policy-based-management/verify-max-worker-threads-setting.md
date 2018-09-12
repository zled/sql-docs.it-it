---
title: Verificare l'impostazione relativa al numero massimo di thread di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 79634c1b0dbddd5da6a4b6697643baa52e89ea82
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808247"
---
# <a name="verify-max-worker-threads-setting"></a>Verifica dell'impostazione relativa al numero massimo di thread di lavoro
  Questa regola consente di controllare l'opzione server relativa al numero massimo di thread di lavoro per individuare l'eventuale presenza di impostazioni non corrette. L'impostazione dell'opzione relativa al numero massimo di thread di lavoro su un valore troppo basso può comportare la presenza di un numero insufficiente di thread per l'elaborazione tempestiva delle richieste client in ingresso e provocare una mancanza di thread. L'impostazione di questa opzione su un valore elevato, tuttavia, può provocare uno spreco di spazio, in quanto ogni thread attivo utilizza 512 KB nei server a 32 bit e fino a 4 MB nei server a 64 bit.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione max worker threads su 0. In questo modo, il numero corretto di thread di lavoro attivi verrà determinato automaticamente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in base alle richieste dell'utente.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Configurare l'opzione di configurazione del server max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
