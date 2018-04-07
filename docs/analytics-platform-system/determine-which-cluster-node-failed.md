---
title: Determinare quale nodo del Cluster non è riuscita (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e001117-a1b6-4357-bf25-e85aba3f1cf0
caps.latest.revision: 21
ms.openlocfilehash: 201d11f7c3e5e7d50e1138ab41edf4fbdb60a6b9
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="determine-which-cluster-node-failed"></a>Determinare il nodo del Cluster non riuscita
In questo argomento viene descritto come determinare il nome del nodo che non è riuscita dopo un failover del cluster si è verificato e generato un avviso di failover del cluster SQL Server PDW. Come parte della risoluzione dei problemi relativi a un cluster di failover, è necessario determinare il nome del nodo che non è riuscito prima di contattare Microsoft per risolvere il problema.  
  
## <a name="Background"></a>Sfondo  
Per la disponibilità elevata in SQL Server PDW, il nodo di controllo e i nodi di calcolo sono configurati come componenti attivi o passivi del cluster di failover di Windows. Quando un server attivo non riesce a rispondere alle richieste di sistema critiche, il server passivo viene eseguito il failover ed esegue le funzioni del server che non è riuscita.  
  
Dopo un failover del cluster, quando SQL Server PDW segnala lo stato del nodo, il server passivo è non riuscito su stato. Tuttavia, non è ovvio quale server o il nodo non è riuscita, soprattutto se il server che non è ancora online. Per risolvere l'errore del cluster, è necessario determinare il nome del nodo in cui è stato eseguito il failover.  
  
## <a name="AdminConsoleSolution"></a>Soluzione di Console di amministrazione  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>Per trovare il nome del nodo che non è riuscita  
  
1.  Aprire la Console di amministrazione. Per ulteriori informazioni sulla Console di amministrazione, vedere [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Dopo che si verifica il failover, l'evento di failover è incluso nel numero di avvisi sul **integrità** pagina. È presente un **integrità** pagina per l'area PDW, l'area HDI e per l'area dell'infrastruttura del dispositivo. Ogni pagina di stato ha un **avvisi** scheda. Per ulteriori informazioni su un avviso, fare clic sulla pagina integrità, scheda Avvisi e quindi fare clic su un avviso.  
  
## <a name="SystemView"></a>Soluzione di visualizzazione del sistema  
L'istruzione SQL seguente viene illustrato come utilizzare il [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) vista di sistema per individuare il nome del server che non è riuscita.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
