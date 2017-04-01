---
title: "MSSQL_ENG020557 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG020557 - errore"
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# MSSQL_ENG020557
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20557|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Arresto dell'agente. Per ulteriori informazioni, cercare nella cronologia dei processi di SQL Server Agent il processo '%s'.|  
  
## Spiegazione  
 Un agente di replica è stato arrestato ma nella tabella di cronologia appropriata non è stato scritto nessun motivo oppure l'agente è stato arrestato durante l'esecuzione di un processo.  
  
## Azione dell'utente  
  
-   Riavviare l'agente per verificare se viene eseguito senza errori. Per ulteriori informazioni, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [concetti eseguibili dell'agente di replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Verificare nella cronologia dell'agente e nella cronologia processo la presenza di eventuali altri errori verificatisi nello stesso momento. Per informazioni su come visualizzare lo stato dell'agente e dei dettagli di errore in Monitoraggio replica, vedere gli argomenti seguenti:  
  
    -   Per l'agente Snapshot, agente di lettura Log e agente di lettura coda, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
    -   Per l'agente di distribuzione e l'agente di Merge, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
-   Verificare che funzioni connettività di base tra i computer che sono accessibili dall'agente e quindi connettono a ogni computer utilizzando un'utilità, ad esempio il **sqlcmd** utilità. Per la connessione utilizzare lo stesso account con cui l'agente effettua le connessioni. Per ulteriori informazioni sulle autorizzazioni necessarie per ogni account di agente, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Se l'errore si verifica durante la creazione o l'applicazione di uno snapshot, verificare l'eventuale presenza di errori nei file della directory snapshot.  
  
-   Se l'errore continua a verificarsi, aumentare il livello di dettaglio per la registrazione delle operazioni dell'agente e specificare un file di output per il log. A seconda del contesto dell'errore, in questo modo è possibile ottenere ulteriori informazioni sui passaggi che conducono all'errore e messaggi di errore aggiuntivi. Per ulteriori informazioni su come configurare la registrazione per la replica, vedere l'articolo della Microsoft Knowledge Base [312292](http://support.microsoft.com/kb/312292).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  