---
title: Categoria di eventi Errori e avvisi (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2a91599ccb601c1072ad05e1294c176f30d63a26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065832"
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Categoria di eventi Errori e avvisi (Motore di database)
  La categoria di eventi **Errori e avvisi** include eventi generali relativi a errori e avvisi.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento Attention](attention-event-class.md)|Indica che è si è verificato un evento **Attention** .|  
|[Classe di evento Background Job Error](background-job-error-event-class.md)|Indica l'interruzione anomala di un processo in background.|  
|[Classe di evento Bitmap Warning](bitmap-warning-event-class.md)|Indica che il filtro bitmap è stato disabilitato in una query.|  
|[Classe di evento Blocked Process Report](blocked-process-report-event-class.md)|Indica che un'attività è rimasta bloccata per un periodo di tempo maggiore di quello specificato.|  
|[Classe di evento CPU Threshold Exceeded](cpu-threshold-exceeded-event-class.md)|Indica che il Resource Governor rileva una query che supera la soglia della CPU specificata.|  
|[Classe di evento ErrorLog](errorlog-event-class.md)|Indica che sono stati registrati eventi di errore nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe di evento EventLog](eventlog-event-class.md)|Indica la registrazione di eventi nel registro eventi di Windows.|  
|[Classe di evento Exception](exception-event-class.md)|Indica la generazione di un'eccezione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Classe di evento Exchange Spill](exchange-spill-event-class.md)|Indica che i buffer di comunicazione in un piano di query parallelo sono stati scritti nel database tempdb.|  
|[Classe di evento Execution Warnings](execution-warnings-event-class.md)|Indica la generazione di avvisi di concessione di memoria durante l'esecuzione di un'istruzione o di una stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe di evento Hash Warning](hash-warning-event-class.md)|Indica il verificarsi di una ricorsione di hash o un hash bailout durante un'operazione di hashing.|  
|[Classe di evento Missing Column Statistics](missing-column-statistics-event-class.md)|Indica che le statistiche di colonna utili per Query Optimizer non sono disponibili.|  
|[Classe di evento Missing Join Predicate](missing-join-predicate-event-class.md)|Indica che è in esecuzione una query senza predicato di join.|  
|[Classe di evento Sort Warnings](sort-warnings-event-class.md)|Indica le operazioni di ordinamento per cui la memoria disponibile risulta insufficiente.|  
|[Classe di evento User Error Message](user-error-message-event-class.md)|Visualizza messaggi di errore per gli utenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
