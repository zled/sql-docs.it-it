---
title: Oggetto Wait Statistics di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6366376f25df6f8407f3ff5a81f585b785fbe759
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32951076"
---
# <a name="sql-server-wait-statistics-object"></a>Oggetto Statistiche attesa di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto prestazioni **SQLServer:Statistiche attesa** contiene contatori delle prestazioni che forniscono informazioni sullo stato di attesa.  
  
 Nella tabella seguente sono elencati i contatori inclusi nell'oggetto Statistiche attesa.  
  
|Contatori dell'oggetto Statistiche attesa di SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Attese di blocco**|Statistiche relative ai processi in attesa di un blocco.|  
|**Attese buffer log**|Statistiche relative ai processi in attesa che il buffer del log diventi disponibile.|  
|**Attese scrittura log**|Statistiche relative ai processi in attesa di scrittura nel buffer del log.|  
|**Attese coda concessione memoria**|Statistiche relative ai processi in attesa di una concessione di memoria.|  
|**Attese I/O di rete**|Statistiche relative alle attese per operazioni di I/O di rete.|  
|**Attese latch non di pagina**|Statistiche relative ai latch non di pagina.|  
|**Attese latch I/O di pagina**|Statistiche relative ai latch di I/O di pagina.|  
|**Attese latch pagina**|Statistiche relative ai latch di pagina, esclusi i latch di I/O.|  
|**Attesa oggetti memoria affidabili**|Statistiche relative ai processi in attesa di allocatori di memoria affidabili.|  
|**Attese proprietà transazione**|Statistiche relative alla sincronizzazione dell'accesso dei processi alla transazione.|  
|**Attesa thread di lavoro**|Statistiche relative ai processi in attesa che il thread di lavoro diventi disponibile.|  
|**Attese sincronizzazione area di lavoro**|Statistiche relative alla sincronizzazione dell'accesso dei processi all'area di lavoro.|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Elemento|Description|  
|----------|-----------------|  
|**Tempo medio di attesa (ms)**|Tempo medio per il tipo di attesa selezionato.|  
|**Tempo di attesa (ms) cumulativo al secondo**|Tempo di attesa aggregato al secondo per il tipo di attesa selezionato|  
|**Attese in corso**|Numero di processi attualmente in attesa del tipo seguente.|  
|**Attese avviate al secondo**|Numero di attese avviate al secondo del tipo di attesa selezionato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
