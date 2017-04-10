---
title: "MSSQL_ENG014164 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014164 - errore"
ms.assetid: cd81b601-2ec3-4358-ad58-c2655496e6a1
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG014164
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14164|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|È stata impostata la soglia [%s:%s] per la pubblicazione [%s]. Verificare che l'agente di merge sia in esecuzione e sia in grado di rispettare i requisiti previsti.|  
  
## Spiegazione  
 La replica consente di attivare avvisi per numerose condizioni, tra cui la mancata elaborazione di un numero di righe sufficiente durante la sincronizzazione delle modifiche tra un server di pubblicazione e un Sottoscrittore. È possibile specificare momenti diversi per connessioni LAN e remote.  
  
 Quando si attiva un avviso utilizzando Monitoraggio replica o [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), si specifica una soglia che determina quando viene attivato un avviso. Quando tale soglia viene raggiunta o superata, viene visualizzato un avviso in Monitoraggio replica e viene registrato un evento nel registro eventi di Windows. Il raggiungimento di una soglia può inoltre generare un avviso SQL Server Agent. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) e [monitoraggio a livello di programmazione della replica](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## Azione dell'utente  
 Se una sottoscrizione non è conforme a una soglia di elaborazione delle righe, è necessario stabilire se il fenomeno dipende da un problema di prestazioni del sistema o se la soglia deve essere regolata. Dopo avere configurato la replica, sviluppare dati di riferimento per le prestazioni in modo da poter stabilire il comportamento della replica in presenza del carico di lavoro tipico delle applicazioni e della topologia in uso. Includere nei dati di riferimento anche il numero di righe elaborate al fine di poter impostare un valore appropriato per la soglia.  
  
 Se il valore soglia è appropriato ma viene superato, è necessario individuare l'area del sistema a cui è dovuto il collo di bottiglia a livello di prestazioni. Per ulteriori informazioni sul monitoraggio e la risoluzione dei problemi delle prestazioni di replica, vedere gli argomenti seguenti:  
  
-   [Monitorare le prestazioni con Monitoraggio replica](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) (in particolare la sezione "Visualizzazione dettagliate sincronizzazione sulle prestazioni per la replica di tipo Merge")  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  