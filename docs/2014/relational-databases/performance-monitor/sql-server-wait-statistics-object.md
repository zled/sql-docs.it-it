---
title: Oggetto Wait Statistics di SQL Server | Microsoft Docs
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
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0da9fe7a76acc3cb7e6cb7713c2c498e9683fd26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162722"
---
# <a name="sql-server-wait-statistics-object"></a>Oggetto Statistiche attesa di SQL Server
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
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
