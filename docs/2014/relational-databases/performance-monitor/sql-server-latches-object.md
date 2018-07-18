---
title: Oggetto Latches di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 19b5d3f6cca79241d18c6bc5a91826a4cc590331
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150632"
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
  
  
