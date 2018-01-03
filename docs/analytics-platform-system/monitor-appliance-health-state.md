---
title: "Stato di integrità dello strumento di monitoraggio (Analitica piattaforma System)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91132e3c-3137-4670-adaa-8a7b234fb8d2
caps.latest.revision: "12"
ms.openlocfilehash: d83c3d35c4cf65ebf714b44bc9db7db36b11f818
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="monitor-appliance-health-state"></a>Stato di integrità dello strumento di monitoraggio
In questo argomento viene illustrato come monitorare lo stato di un dispositivo di SQL Server PDW, utilizzando la Console di amministrazione o direttamente tramite query le viste a gestione dinamica SQL Server PDW.  
  
## <a name="to-monitor-the-appliance-state"></a>Per monitorare lo stato del dispositivo  
Un amministratore di sistema è possibile utilizzare la Console di amministrazione o viste a gestione dinamica di SQL Server PDW (DMV) per recuperare la gerarchia di nodi e i componenti software completa. Nel diagramma seguente offre una comprensione di alto livello dei componenti che esegue il monitoraggio di SQL Server PDW.  
  
![Panoramica del monitoraggio](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Monitorare lo stato componente utilizzando la Console di amministrazione  
Per recuperare lo stato del componente utilizzando la Console di amministrazione:  
  
1.  Fare clic su di **stato dello strumento** scheda.  
  
2.  Nella pagina stato del dispositivo, fare clic su un nodo specifico per visualizzare i dettagli del nodo.  
  
    ![Stato della Console di amministrazione di PDW](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
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
  
-   Non critico  
  
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
[Monitoraggio dispositivo &#40; Sistema della piattaforma Analitica &#41;](appliance-monitoring.md)  
  
