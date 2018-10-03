---
title: Oggetto Latches di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3b4953b71343dfa5bae3c0622369fb9bf3722c5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145686"
---
# <a name="sql-server-latches-object"></a>Oggetto Latch di SQL Server
  L'oggetto **SQLServer:Latch** in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce contatori per monitorare i blocchi di risorsa interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , definiti latch. Il monitoraggio dei latch per determinare l'attività degli utenti e l'utilizzo delle risorse può essere utile per identificare eventuali colli di bottiglia.  
  
 Nella tabella seguente vengono illustrati i contatori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **di** .  
  
|Contatori di SQLServer:Latch|Description|  
|---------------------------------|-----------------|  
|**Tempo medio di attesa latch (ms)**|Tempo medio di attesa di latch da parte delle richieste di latch (in millisecondi).|  
|**Attese latch/sec**|Numero di richieste di latch non soddisfatte immediatamente.|  
|**Numero di SuperLatch**|Numero di latch utilizzati attualmente come SuperLatch.|  
|**Abbassamenti di livello SuperLatch/sec**|Numero di SuperLatch abbassati al livello di latch normali nell'ultimo secondo.|  
|**Promozioni a SuperLatch/sec**|Numero di latch promossi a SuperLatch nell'ultimo secondo.|  
|**Tempo totale di attesa latch (ms)**|Tempo totale di attesa di latch da parte delle richieste di latch nell'ultimo secondo (in millisecondi).|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
