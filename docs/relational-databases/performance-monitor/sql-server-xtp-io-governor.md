---
title: XTP IO Governor di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 6a82a841dcda9a663c9645cab5f04598c3407bda
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033318"
---
# <a name="sql-server-xtp-io-governor"></a>XTP IO Governor di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L'oggetto prestazione XTP IO Governor di SQL Server include i contatori correlati a IO Rate Governor di OLTP in memoria.

Questa tabella descrive i contatori di **SQL Server XTP IO Governor** .

|Contatore|Descrizione|  
|-------------|-----------------|  
|**Insufficient Credits Waits/sec (Attese crediti insufficienti/sec)**|Numero di attese a causa di crediti insufficienti negli oggetti frequenza (al secondo).|
|**Io Issued/sec (IO rilasciati/sec)**|Numero di I/O rilasciati per secondo dai thread di scaricamento.|
|**Log Blocks/sec (Blocchi del log/sec)**|Numero di blocchi di log elaborati dal controller al secondo.|
|**Missed Credit Slots (Slot crediti persi)**|Numero di slot crediti persi a causa dell'attesa di crediti dall'oggetto frequenza.|
|**Stale Rate Object Waits/sec (Attese di oggetti frequenza non aggiornati/sec)**|Numero di attese a causa di oggetti frequenza non aggiornati (al secondo).|
|**Total Rate Objects Published (Frequenza totale oggetti pubblicati)**|Numero totale di oggetti frequenza pubblicati.|
 

## <a name="see-also"></a>Vedere anche  
[Contatori delle prestazioni XTP &#40;OLTP in memoria&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
