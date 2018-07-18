---
title: Determinare la frequenza di polling - Analitica Platform System | Documenti Microsoft
description: In questo articolo viene illustrato come determinare la frequenza di polling Analitica Platform appliance gli avvisi di sistema.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 39597e0e4623a3006709acde7fe54f97545c362f
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707619"
---
# <a name="determine-polling-frequency"></a>Determinare la frequenza di Polling
In questo articolo viene illustrato come determinare la frequenza di polling Analitica Platform appliance gli avvisi di sistema.  
  
## <a name="to-determine-the-polling-frequency"></a>Per determinare la frequenza di Polling  
Poiché PDW non supporta attualmente attiva notifiche quando si verificano avvisi, la soluzione di monitoraggio deve eseguire continuamente il polling accessorio DLL.  Internamente, PDW esegue il polling dei componenti a intervalli diversi:  
  
-   Cluster-60 secondi  
  
-   Heartbeat-60 secondi  
  
-   Tutti gli altri componenti, ovvero cinque minuti  
  
-   Contatori delle prestazioni: tre secondi  
  
È un intervallo comune per eseguire il polling per gli avvisi, viene utilizzato anche da System Center, **ogni 15 minuti**.  Ovviamente, è possibile eseguire una query più o meno frequente, ma non è consigliabile eseguire il polling inferiore a ogni sei ore.  
  
Esecuzione più frequente del polling è accettabile, ma l'esecuzione troppo frequente del polling può creare confusione il [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/library/ms177648(v=sql11).aspx) DMV.  Esecuzione troppo frequente del polling può rendere difficile per gli utenti diagnosticare le prestazioni delle query problemi quando i relativi rapidamente il rollback fuori della visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Monitoraggio dello strumento &#40;Analitica Platform System&#41;](appliance-monitoring.md)  
  
