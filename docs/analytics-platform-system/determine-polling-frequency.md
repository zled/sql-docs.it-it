---
title: Determinare la frequenza di Polling (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062c0e3d-f7d0-44f1-aeab-a9bd17dc6fdd
caps.latest.revision: "7"
ms.openlocfilehash: fb32abc38a90cd7450dc310a9f73eb7a5d72b5fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="determine-polling-frequency"></a>Determinare la frequenza di Polling
In questo argomento viene illustrato come determinare la frequenza di polling per gli avvisi di SQL Server PDW appliance.  
  
## <a name="to-determine-the-polling-frequency"></a>Per determinare la frequenza di Polling  
Poiché PDW non supporta attualmente attiva notifiche quando si verificano avvisi, la soluzione di monitoraggio deve eseguire continuamente il polling accessorio DLL.  Internamente, PDW esegue il polling dei componenti a intervalli diversi:  
  
-   Cluster-60 secondi  
  
-   Heartbeat-60 secondi  
  
-   Tutti gli altri componenti, ovvero 5 minuti  
  
-   Contatori delle prestazioni-3 secondi  
  
È un intervallo comune per eseguire il polling per gli avvisi, viene utilizzato anche da System Center, **ogni 15 minuti**.  Ovviamente, è possibile eseguire una query più o meno frequente, ma non è consigliabile eseguire il polling inferiore a ogni 6 ore.  
  
Esecuzione più frequente del polling è accettabile, ma l'esecuzione troppo frequente del polling può creare confusione il [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/en-us/library/ms177648(v=sql11).aspx) DMV.  Questo può rendere difficile per gli utenti diagnosticare i problemi di prestazioni delle query, se presente rapidamente query transita fuori della visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Monitoraggio dispositivo &#40; Sistema della piattaforma Analitica &#41;](appliance-monitoring.md)  
  
