---
title: XTP Garbage Collection | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c2a968f1fa15f0f61d988f5068ab5ce39be0808e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299934"
---
# <a name="xtp-garbage-collection"></a>XTP Garbage Collection
  L'oggetto prestazione XTP Garbage Collection contiene contatori correlati al Garbage Collector del motore XTP.  
  
 La tabella seguente descrive la **XTP garbage Collection** contatori.  
  
|Contatore|Description|  
|-------------|-----------------|  
|**Tentativi di analisi di elementi nascosti/sec (GC- pubblicato)**|Numero medio di tentativi di analisi dovuti a conflitti di scrittura durante le operazioni su elementi nascosti eseguite dal Garbage Collector, al secondo. Si tratta di un contatore di livello molto basso, non destinato all'uso da parte del cliente.|  
|**Elementi di lavoro GC principali/sec**|Numero di elementi di lavoro elaborati dal thread GC principale.|  
|**Elemento di lavoro GC parallelo/sec**|Numero di volte in cui un thread parallelo ha eseguito un elemento di lavoro GC.|  
|**Righe elaborate/sec**|Numero medio di righe elaborate dal Garbage Collector, al secondo.|  
|**Righe elaborate/sec (innanzitutto in bucket e rimosse)**|Numero medio di righe elaborate dal Garbage Collector che erano prima nel bucket di hash corrispondente e che è stato possibile rimuovere immediatamente, al secondo.|  
|**Righe elaborate/sec (innanzitutto in bucket)**|Numero medio di righe elaborate dal Garbage Collector che erano prima nel bucket di hash corrispondente, al secondo.|  
|**Righe elaborate/sec (contrassegnate per essere scollegate)**|Numero medio di righe elaborate dal Garbage Collector che erano già contrassegnate per essere scollegate, al secondo.|  
|**Righe elaborate/sec (nessuna operazione necessaria)**|Numero medio di righe elaborate dal Garbage Collector che non richiederanno un'operazione su elementi nascosti, al secondo.|  
|**Righe scadute rimosse/sec operazioni**|Numero medio di righe scadute rimosse durante le operazioni su elementi nascosti, al secondo.|  
|**Righe scadute interessate/sec operazioni**|Numero medio di righe scadute interessate durante le operazioni su elementi nascosti, al secondo.|  
|**Righe in scadenza interessate/sec operazioni**|Numero medio di righe in scadenza interessate durante le operazioni su elementi nascosti, al secondo.|  
|**Righe interessate/sec operazioni**|Numero medio di righe interessate durante le operazioni su elementi nascosti, al secondo.|  
|**Analisi avviate/sec operazioni**|Numero medio di analisi di operazioni su elementi nascosti avviate, al secondo.|  
  
## <a name="see-also"></a>Vedere anche  
 [XTP &#40;OLTP In memoria&#41; i contatori delle prestazioni](../../integration-services/performance/performance-counters.md)  
  
  
