---
title: "MSSQL_ENG014160 | Microsoft Docs"
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
  - "MSSQL_ENG014160 - errore"
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014160
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14160|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|È stata impostata la soglia [%s:%s] per la pubblicazione [%s]. Una o più sottoscrizioni della pubblicazione sono scadute.|  
  
## Spiegazione  
 La replica consente di attivare avvisi per numerose condizioni, tra cui la scadenza imminente della sottoscrizione. Le sottoscrizioni possono scadere se non vengono sincronizzate entro un determinato *periodo di memorizzazione*. Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 Quando si attiva un avviso utilizzando Monitoraggio replica o [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), si specifica una soglia che determina quando viene attivato un avviso. Quando tale soglia viene raggiunta o superata, viene visualizzato un avviso in Monitoraggio replica e viene registrato un evento nel registro eventi di Windows. Il raggiungimento di una soglia può inoltre generare un avviso SQL Server Agent. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) e [monitoraggio a livello di programmazione della replica](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## Azione dell'utente  
 La risoluzione del problema dipende dal motivo per il quale è stato generato l'avviso:  
  
-   Se la soglia è stata superata ma la sottoscrizione non è ancora scaduta, sincronizzare la sottoscrizione. Per ulteriori informazioni, vedere [sincronizzare dati](../../relational-databases/replication/synchronize-data.md).  
  
-   È possibile che la sottoscrizione scada se l'agente è stato eseguito ma la replica delle modifiche non è stata completata correttamente. Per la replica transazionale verificare che l'agente di distribuzione e l'agente di lettura log siano in esecuzione. Per la replica di tipo merge verificare che l'agente di merge sia in esecuzione. Per informazioni su come avviare questi agenti, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Se la sottoscrizione è scaduta, sarà necessario reinizializzarla oppure eliminarla e ricrearla, a seconda del tipo di sottoscrizione e da quanto tempo è scaduta. Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  