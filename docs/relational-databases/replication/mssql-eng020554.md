---
title: "MSSQL_ENG020554 | Microsoft Docs"
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
  - "MSSQL_ENG020554 - errore"
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG020554
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20554|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Nessun messaggio di stato registrato dall'agente di replica negli ultimi %ld minuti. Questa condizione può indicare che l'agente non risponde oppure che l'attività del sistema è elevata. Verificare che i record vengano replicati nella destinazione e che le connessioni al Sottoscrittore, al server di pubblicazione e al server di distribuzione siano ancora attive.|  
  
## Spiegazione  
 Il **controllo degli agenti di replica** processo viene eseguito in un intervallo specificato (10 minuti per impostazione predefinita) per controllare lo stato di ogni agente di replica. Se un agente non ha registrato alcun messaggio di stato dall'ultima esecuzione del processo di controllo, viene generato l'errore MSSQL_ENG020554. È previsto che l'agente registri almeno messaggi di cronologia anche se non vi è nessun'altra attività di replica in corso. Sebbene l'agente di replica non risponda come previsto, non significa necessariamente che la sua attività si sia arrestata o non sia riuscita. In quest'ultimo caso verrebbe generato l'errore MSSQL_ENG020536.  
  
 L'errore MSSQL_ENG020554 può essere generato dai problemi seguenti:  
  
-   L'agente è occupato.  
  
     Se l'agente è occupato a rispondere al polling del processo di controllo degli agenti, non sarà possibile verificare se è in funzione in modo appropriato. Vi sono vari motivi per cui l'agente di replica potrebbe essere occupato. È possibile che vi siano molti dati in fase di replica oppure problemi di sviluppo o di configurazione delle applicazioni che determinano lunghi tempi di elaborazione dei processi.  
  
-   L'agente non è in grado di accedere a uno dei computer nella topologia.  
  
     Tutti gli agenti dispongono di un parametro **- LoginTimeOut** (impostato su 15 secondi per impostazione predefinita), che determina quanto tempo un agente tenta di accedere a un nodo di replica, ad esempio accesso al server di pubblicazione un agente di Merge. Se il **- LoginTimeOut** valore impostato è superiore all'intervallo in cui viene eseguito il processo di controllo degli agenti di replica, un problema di accesso potrebbe essere la causa dell'errore: errore MSSQL_ENG020554 viene generato prima che l'agente è in grado di generare un errore più specifico.  
  
## Azione dell'utente  
 A seconda della causa dell'errore è necessaria un'azione specifica:  
  
-   Per tutti i casi in cui viene generato questo errore:  
  
     Controllare i dettagli dell'errore in Monitoraggio replica e quindi riavviare l'agente se si è arrestato. Nei dettagli dell'errore potrebbero essere contenute informazioni aggiuntive sui motivi del malfunzionamento dell'agente. Se l'agente è in esecuzione, non arrestarlo né riavviarlo, poiché ciò potrebbe aggravare il problema. Per informazioni sulla visualizzazione dello stato dell'agente e dei dettagli di errore in Monitoraggio replica, vedere gli argomenti seguenti:  
  
    -   Per l'agente Snapshot, agente di lettura Log e agente di lettura coda, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
    -   Per l'agente di distribuzione e l'agente di Merge, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
-   Se l'errore viene generato spesso perché l'agente è occupato:  
  
     Potrebbe essere necessario riprogettare l'applicazione in modo da ridurre il tempo di elaborazione.  
  
     È possibile aumentare l'intervallo con l'agente viene controllato lo stato utilizzando la **proprietà processo** la finestra di dialogo. Per informazioni sull'accesso a questa finestra di dialogo per i processi di replica, vedere [visualizzare le informazioni ed esecuzione delle attività per un server di pubblicazione e 40 #; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md).  
  
-   Se l'agente non è in grado di accedere a uno dei computer nella topologia:  
  
     È consigliabile che il **- LoginTimeOut** valore inferiore rispetto all'intervallo al quale viene eseguito il processo di controllo degli agenti di replica. In alcuni casi, il valore per **- LoginTimeOut** è superiore a causa di problemi di rete che determinano il timeout degli accessi. Se il **- LoginTimeOut** è impostato inferiore, sarà possibile ricevere errori più specifici, che consente di risolvere i problemi di accesso che potrebbero essere causati da autorizzazioni, problemi di rete o altri problemi. I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Visualizzare e modificare i parametri di prompt dei comandi dell'agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concetti di file eseguibili dell'agente replica](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## Vedere anche  
 [Amministrazione dell'agente di replica](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agente distribuzione repliche](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agente merge repliche](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Agente snapshot repliche](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  