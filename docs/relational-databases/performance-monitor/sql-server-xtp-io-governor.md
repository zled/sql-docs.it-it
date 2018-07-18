---
title: XTP IO Governor di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
caps.latest.revision: 2
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: c370bb68474c29d04615316ff7782ee1d532a561
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-xtp-io-governor"></a>XTP IO Governor di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L'oggetto prestazione XTP IO Governor di SQL Server include i contatori correlati a IO Rate Governor di OLTP in memoria.

Questa tabella descrive i contatori di **SQL Server XTP IO Governor** .

|Contatore|Description|  
|-------------|-----------------|  
|**Insufficient Credits Waits/sec (Attese crediti insufficienti/sec)**|Numero di attese a causa di crediti insufficienti negli oggetti frequenza (al secondo).|
|**Io Issued/sec (IO rilasciati/sec)**|Numero di I/O rilasciati per secondo dai thread di scaricamento.|
|**Log Blocks/sec (Blocchi del log/sec)**|Numero di blocchi di log elaborati dal controller al secondo.|
|**Missed Credit Slots (Slot crediti persi)**|Numero di slot crediti persi a causa dell'attesa di crediti dall'oggetto frequenza.|
|**Stale Rate Object Waits/sec (Attese di oggetti frequenza non aggiornati/sec)**|Numero di attese a causa di oggetti frequenza non aggiornati (al secondo).|
|**Total Rate Objects Published (Frequenza totale oggetti pubblicati)**|Numero totale di oggetti frequenza pubblicati.|
 

## <a name="see-also"></a>Vedere anche  
[Contatori delle prestazioni XTP &#40;OLTP in memoria&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
