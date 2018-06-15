---
title: Tenere traccia degli avvisi accessorio - Analitica Platform System | Documenti Microsoft
description: Registrare gli avvisi di dispositivo nel sistema della piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 82803e6f20e4a710f317e2e7a541c4a1c72ed08d
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539271"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Avvisi accessorio traccia Analitica Platform System
In questo argomento viene illustrato come utilizzare le Console di amministrazione e le viste di sistema per tenere traccia degli avvisi in un dispositivo di SQL Server PDW.  
  
## <a name="to-track-appliance-alerts"></a>Per tenere traccia degli avvisi di dispositivo  
SQL Server PDW crea gli avvisi per problemi di hardware e software che richiedono attenzione. Ogni avviso contiene un titolo e una descrizione del problema.  
  
Avvisi e registri di SQL Server PDW [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) DMV. Il sistema mantiene un limite di 10.000 avvisi ed elimina l'avviso meno recente prima quando viene superato il limite.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Visualizzare gli avvisi tramite la Console di amministrazione  
È presente un **avvisi** scheda per l'area PDW, l'area HDI e per l'area dell'infrastruttura del dispositivo. Dopo che si verifica il failover, l'evento di failover è incluso nel numero di avvisi nella pagina. È una pagina per l'area PDW, l'area HDI e per l'area dell'infrastruttura del dispositivo. Ogni pagina di stato è disponibile una scheda. Per ulteriori informazioni su un avviso, fare clic su di **integrità** pagina il **avvisi** scheda e quindi fare clic su un avviso.  
  
![Avvisi della Console di amministrazione PDW](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
Nel **avvisi** pagina:  
  
-   Per visualizzare la cronologia dell'avviso, fare clic su di **cronologia avviso revisione** collegamento.  
  
-   Per visualizzare il componente di avviso e i relativi valori correnti delle proprietà, fare clic sulla riga di avviso.  
  
-   Per visualizzare i dettagli relativi al nodo che ha generato l'avviso, fare clic sul nome del nodo.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Visualizzare gli avvisi tramite le viste di sistema  
Per visualizzare gli avvisi tramite le viste di sistema, eseguire una query [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). Questa DMV vengono illustrati gli avvisi che non sono stati corretti. Per informazioni su errori e avvisi di valutazione, utilizzare il [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) DMV.  
  
L'esempio seguente è una query comune per la visualizzazione di avvisi correnti.  
  
```sql  
SELECT   
    aa.[pdw_node_id],  
    n.[name] AS [node_name],  
    g.[group_name] ,  
    c.[component_name] ,  
    aa.[component_instance_id] ,   
    a.[alert_name] ,  
    a.[state] ,  
    a.[severity] ,  
    aa.[current_value] ,  
    aa.[previous_value] ,  
    aa.[create_time] ,  
    a.[description]   
FROM [sys].[dm_pdw_component_health_active_alerts] AS aa  
    INNER JOIN sys.dm_pdw_nodes AS n   
        ON aa.[pdw_node_id] = n.[pdw_node_id]  
    INNER JOIN [sys].[pdw_health_components] AS c   
        ON aa.[component_id] = c.[component_id]  
    INNER JOIN [sys].[pdw_health_component_groups] AS g   
        ON c.[group_id] = g.[group_id]  
    INNER JOIN [sys].[pdw_health_alerts] AS a   
        ON aa.[alert_id] = a.[alert_id] and aa.[component_id] = c.[component_id]  
ORDER BY  
    a.alert_id ,  
    aa.[pdw_node_id];  
```  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Monitoraggio dello strumento &#40;Analitica Platform System&#41;](appliance-monitoring.md)  
  
