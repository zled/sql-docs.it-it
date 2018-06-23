---
title: Oggetto Workload Group Stats di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 98dfc36dc69f8b913b9b1b5939522429d585854b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167584"
---
# <a name="sql-server-workload-group-stats-object"></a>SQL Server - Oggetto Statistiche gruppi del carico di lavoro
  L'oggetto SQLServer: Statistiche gruppi del carico di lavoro contiene contatori delle prestazioni che forniscono informazioni sulle statistiche del gruppo del carico di lavoro di Resource Governor.  
  
 Ciascun gruppo del carico di lavoro attivo crea un'istanza dell'oggetto prestazioni SQLServer: Statistiche gruppi del carico di lavoro con lo stesso nome dell'istanza del gruppo del carico di lavoro di Resource Governor. Nella seguente tabella vengono descritti i contatori supportati in questa istanza.  
  
|Nome contatore|Description|  
|------------------|-----------------|  
|Richieste in coda|Numero corrente di richieste in coda in attesa di essere prelevate. Questo conteggio può essere diverso da zero se si verifica una limitazione dopo il raggiungimento del limite GROUP_MAX_REQUESTS.|  
|Richieste attive|Numero di richieste attualmente in esecuzione nel gruppo del carico di lavoro. Tale numero deve essere equivalente al conteggio di righe da sys.dm_exec_requests filtrate per ID del gruppo.|  
|Richieste completate/sec|Numero di richieste completate nel gruppo del carico di lavoro. Questo numero è cumulativo.|  
|% di utilizzo CPU|Utilizzo della larghezza di banda della CPU da parte di tutte le richieste nel gruppo del carico di lavoro misurato in relazione al computer e normalizzato a tutte le CPU del sistema. Tale valore viene modificato quando si modifica la quantità di CPU disponibile per il processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il valore non è normalizzato secondo i dati ricevuti dal processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|Tempo massimo CPU richieste (ms)|Il tempo massimo della CPU, in millisecondi, utilizzato da una richiesta attualmente in esecuzione nel gruppo del carico di lavoro.|  
|Richieste bloccate|Numero di richieste bloccate nel gruppo del carico di lavoro. Tale valore può essere utilizzato per determinare le caratteristiche del carico di lavoro.|  
|Concessioni di memoria ridotte/sec|Numero di query che ottengono una quantità di memoria inferiore a quella ideale nel gruppo del carico di lavoro.|  
|Concessione di memoria massima per le richieste (KB)|Valore massimo della concessione di memoria, in kilobyte (KB), per una query.|  
|Ottimizzazioni query/sec|Numero di ottimizzazioni di query che si sono verificate nel gruppo del carico di lavoro al secondo. Tale valore può essere utilizzato per determinare le caratteristiche del carico di lavoro.|  
|Piani non ottimali/sec|Numero di piani non ottimali generati nel gruppo del carico di lavoro al secondo.|  
|Thread paralleli attivi|Numero corrente degli utilizzi di thread paralleli.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server - Oggetto Statistiche del pool di risorse](sql-server-resource-pool-stats-object.md)   
 [Resource Governor](../resource-governor/resource-governor.md)  
  
  