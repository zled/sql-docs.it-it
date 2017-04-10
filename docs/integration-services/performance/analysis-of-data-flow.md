---
title: "Analisi del flusso di dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Analisi del flusso di dati
  È possibile usare la vista database [execution_data_statistics](../../integration-services/system-views/catalog-execution-data-statistics.md) **SSISDB** per analizzare il flusso di dati dei pacchetti. In questa vista viene visualizzata una riga ogni volta che un componente del flusso di dati invia dati a un componente a valle. Le informazioni possono essere utilizzate per acquisire una comprensione più approfondita delle righe inviate a ciascun componente.  
  
> [!NOTE]  
>  Il livello di registrazione deve essere impostato su **Dettagliato** per acquisire informazioni con la vista catalog.execution_data_statistics.  
  
 Nell'esempio seguente viene visualizzato il numero di righe inviate tra i componenti di un pacchetto.  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 Nell'esempio seguente viene calcolato il numero di righe per millisecondi inviate da ogni componente per un'esecuzione specifica. I valori calcolati sono:  
  
-   **total_rows**: somma di tutte le righe inviate dal componente  
  
-   **wall_clock_time_ms**: tempo totale di esecuzione trascorso, in millisecondi, per ogni componente  
  
-   **num_rows_per_millisecond**: numero di righe per millisecondi inviate da ogni componente  
  
 La clausola **HAVING** viene usata per impedire un errore di divisione per zero nei calcoli.  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## Attività correlate  
 [Debug di un flusso di dati](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
 [Risoluzione dei problemi relativi agli strumenti per l'esecuzione del pacchetto](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## Vedere anche  
 [Dati nei flussi di dati](../../integration-services/data-flow/data-in-data-flows.md)  
  
  