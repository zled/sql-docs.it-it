---
title: XTP Phantom Processor di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 722137db4fdddd79f8ed4bfe8d5a7c3ed4531738
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-xtp-phantom-processor"></a>XTP Phantom Processor di SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  L'oggetto prestazione SQL Server XTP Phantom Processor contiene contatori correlati al sottosistema di elaborazione fantasma del motore OLTP in memoria. Con questo componente è possibile rilevare le righe fantasma nelle transazioni in esecuzione a livello di isolamento SERIALIZABLE, nonché la convalida dei vincoli negli scenari di concorrenza.  
  
 Nella tabella seguente sono descritti i contatori di **SQL Server XTP Phantom Processor** .  
  
|Contatore|Descrizione|  
|-------------|-----------------|  
|**Tentativi di analisi di elementi nascosti/sec (eseguiti dal processore fantasma)**|Numero medio di tentativi di analisi dovuti a conflitti di scrittura durante le operazioni su elementi nascosti eseguite dal processore fantasma, al secondo. Si tratta di un contatore di livello molto basso, non destinato all'uso da parte del cliente.|  
|**Righe fantasma scadute rimosse/sec**|Numero medio di righe scadute rimosse dalle analisi fantasma, al secondo.|  
|**Righe fantasma scadute interessate/sec**|Numero medio di righe scadute interessate dalle analisi fantasma, al secondo.|  
|**Righe fantasma in scadenza interessate/sec**|Numero medio di righe in scadenza interessate dalle analisi fantasma, al secondo.|  
|**Righe fantasma interessate/sec**|Numero medio di righe interessate dalle analisi fantasma, al secondo.|  
|**Analisi fantasma avviate/sec**|Numero medio di analisi fantasma avviate, al secondo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Contatori delle prestazioni XTP &#40;OLTP in memoria&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
