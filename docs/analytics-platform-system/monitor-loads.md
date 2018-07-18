---
title: Monitorare i caricamenti per Parallel Data Warehouse | Documenti Microsoft
description: Monitoraggio attivo e recente carica utilizzando la Console di amministrazione Analitica Platform System (AP) o le viste di sistema di Data Warehouse (PDW) parallele."
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8980259b69dfa74c2bb27c9406553a5b5810348a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585673"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Monitorare i caricamenti in Parallel Data Warehouse
Monitoraggio attivo e recente [dwloader](dwloader.md) carica utilizzando la Console di amministrazione di sistema della piattaforma Analitica (AP) o Parallel Data Warehouse (PDW) [viste di sistema](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/). 
  
> [!TIP]  
> Alcuni carichi vengono avviate tramite le istruzioni INSERT o strumenti di business intelligence che utilizzano istruzioni SQL per eseguire il caricamento. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>Prerequisiti  
Indipendentemente dal metodo utilizzato per monitorare il carico, l'accesso deve disporre dell'autorizzazione per accedere alle origini dati sottostanti. 

<!-- MISSING LINKS
For the permissions to grant, see “Use All of the Admin Console” in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Carica il monitoraggio  
Nelle sezioni seguenti viene descritto come monitorare i caricamenti.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Per monitorare i caricamenti utilizzando la Console di amministrazione  
  
1.  Accedere a una Console di amministrazione. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  Nel menu in alto, fare clic su **carichi**. Si noterà una tabella ordinabile che mostra tutti i recenti e di caricamenti attivi oltre a informazioni aggiuntive, ad esempio se il carico è stata completata o se è ancora attivo. Fare clic sulle intestazioni di colonna per ordinare le righe.  
  
3.  Per visualizzare dettagli aggiuntivi per un determinato carico, scegliere il carico **ID** nella colonna sinistra. Nella visualizzazione dettagliata, è possibile visualizzare lo stato di avanzamento su ogni passaggio del carico.  
  
Visualizzare le viste di sistema per informazioni sui metadati relative al carico che viene visualizzato nella Console di amministrazione:  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Per monitorare i caricamenti utilizzando viste di sistema  
Per monitorare i caricamenti attivi e recenti utilizzando viste di SQL Server PDW, attenersi alla procedura seguente. Per ogni vista di sistema utilizzata, vedere la documentazione per la visualizzazione per informazioni sulle colonne e i possibili valori restituiti dalla vista.  
  
1.  Trovare il `request_id` per il carico nel [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) visualizzazione mediante la riga di comando del caricatore della ricerca di `command` colonna per la visualizzazione.  
  
    Ad esempio, il comando seguente restituisce il testo del comando e lo stato corrente, più il `request_id`.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Utilizzare il `request_id` per recuperare informazioni aggiuntive per il carico utilizzando il [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) , e [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) viste. Ad esempio, la query seguente restituisce il `run_id` e informazioni sull'inizio, fine e l'ora di durata del carico, più eventuali errori e informazioni sul numero di righe elaborate:  
  
    ```sql  
    SELECT lbr.run_id,   
    er.submit_time, er.end_time, er.total_elapsed_time, er.error_id, lbr.rows_processed, lbr.rows_rejected, lbr.rows_inserted   
    FROM sys.dm_pdw_exec_requests er   
    LEFT OUTER JOIN   
    sys.pdw_loader_backup_runs lbr   
    ON (er.request_id=lbr.requst_id)   
    WHERE er.request_id=’12738’;  
    ```  
  
<!-- MISSING LINKS

## See Also  
[Common metadata query examples](metadata-query-examples.md)
-->  
  
