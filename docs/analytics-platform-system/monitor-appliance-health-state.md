---
title: Monitoraggio dell'integrità del dispositivo - Analitica Platform System
description: Come monitorare lo stato di un dispositivo di sistema della piattaforma Analitica utilizzando la Console di amministrazione o direttamente tramite query le viste a gestione dinamica Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d8616d291dcaa8afadc01c9bd237903ca6c13573
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="monitor-appliance-health-state"></a>Stato di integrità dello strumento di monitoraggio
In questo articolo viene illustrato come monitorare lo stato di un dispositivo di sistema della piattaforma Analitica utilizzando la Console di amministrazione o direttamente tramite query le viste a gestione dinamica Parallel Data Warehouse. 
  
## <a name="to-monitor-the-appliance-state"></a>Per monitorare lo stato del dispositivo  
Un amministratore di sistema è possibile utilizzare la Console di amministrazione o viste a gestione dinamica di SQL Server PDW (DMV) per recuperare la gerarchia di nodi e i componenti software completa. Nel diagramma seguente offre una comprensione di alto livello dei componenti che esegue il monitoraggio di SQL Server PDW.  
  
![Panoramica dei monitoraggi](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Monitorare lo stato componente utilizzando la Console di amministrazione  
Per recuperare lo stato del componente utilizzando la Console di amministrazione:  
  
1.  Fare clic su di **stato dello strumento** scheda.  
  
2.  Nella pagina stato del dispositivo, fare clic su un nodo specifico per visualizzare i dettagli del nodo.  
  
    ![PDW Admin Console State](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Monitorare lo stato componente utilizzando viste di sistema  
Per recuperare lo stato del componente utilizzando viste di sistema, utilizzare [sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Ad esempio, la query seguente recupera lo stato per tutti i componenti.  
  
```sql  
SELECT   
   s.[pdw_node_id],  
   n.[name] as [node_name],  
   n.[address] ,  
   g.[group_id] ,  
   g.[group_name] ,  
   c.[component_id] ,  
   c.[component_name] ,  
   s.[component_instance_id] ,   
   p.[property_name] ,  
   s.[property_value] ,  
   s.[update_time]  
FROM [sys].[dm_pdw_component_health_status] AS s  
JOIN sys.dm_pdw_nodes AS n   
   ON s.[pdw_node_id] = n.[pdw_node_id]  
JOIN [sys].[pdw_health_components] AS c   
   ON s.[component_id] = c.[component_id]  
JOIN [sys].[pdw_health_component_groups] AS g   
   ON c.[group_id] = g.[group_id]  
JOIN [sys].[pdw_health_component_properties] AS p   
   ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
WHERE p.property_name = 'Status'  
ORDER BY  
   s.[pdw_node_id],  
   g.[group_name] ,   
   s.[component_instance_id] ,  
   c.[component_name] ,   
   p.[property_name];  
```  
  
Sono possibili valori restituiti per la proprietà Status:  
  
-   OK  
  
-   NonCritical  
  
-   Critico  
  
-   Unknown  
  
-   Non supportato  
  
-   Non è raggiungibile  
  
-   Errore irreversibile  
  
Per visualizzare tutte le proprietà per tutti i componenti, rimuovere il `WHERE  p.property_name = 'Status'` clausola.  
  
Il **[update_time]** colonna indica l'ultima volta che il componente è stato eseguito il polling dagli agenti di integrità di SQL Server PDW.  
  
> [!CAUTION]  
> Assicurarsi di esaminare il problema, quando un componente non è stato polling per 5 minuti o più; potrebbe esserci un avviso che indica un problema con l'heartbeat del software.  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Monitoraggio dello strumento &#40;Analitica Platform System&#41;](appliance-monitoring.md)  
  
