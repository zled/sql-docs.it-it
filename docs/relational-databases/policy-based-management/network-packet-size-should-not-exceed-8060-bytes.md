---
title: Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte | Microsoft Docs
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
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2ca4493da06287669788b14976a4f1628e1f6bf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Se il valore specificato per sp_configure 'network packet size' o se le dimensioni del pacchetto di rete di qualsiasi utente connesso sono maggiori di 8060 byte, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue operazioni di allocazione della memoria diverse. In questo caso, può verificarsi un aumento dello spazio degli indirizzi virtuali dei processi non riservato per il pool di buffer.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Le dimensioni del pacchetto di rete non devono superare 8060 byte.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Articolo 903002 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
