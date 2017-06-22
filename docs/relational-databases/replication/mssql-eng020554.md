---
title: MSSQL_ENG020554 | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e3c5e6ae34945bda4ec27846f242a5c4bfd73daa
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng020554"></a>MSSQL_ENG020554
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20554|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Nessun messaggio di stato registrato dall'agente di replica negli ultimi %ld minuti. Questa condizione può indicare che l'agente non risponde oppure che l'attività del sistema è elevata. Verificare che i record vengano replicati nella destinazione e che le connessioni al Sottoscrittore, al server di pubblicazione e al server di distribuzione siano ancora attive.|  
  
## <a name="explanation"></a>Spiegazione  
 Il processo **Controllo degli agenti di replica** viene eseguito a intervalli di tempo specificati (per impostazione predefinita ogni 10 minuti) per verificare lo stato di ogni agente di replica. Se un agente non ha registrato alcun messaggio di stato dall'ultima esecuzione del processo di controllo, viene generato l'errore MSSQL_ENG020554. È previsto che l'agente registri almeno messaggi di cronologia anche se non vi è nessun'altra attività di replica in corso. Sebbene l'agente di replica non risponda come previsto, non significa necessariamente che la sua attività si sia arrestata o non sia riuscita. In quest'ultimo caso verrebbe generato l'errore MSSQL_ENG020536.  
  
 L'errore MSSQL_ENG020554 può essere generato dai problemi seguenti:  
  
-   L'agente è occupato.  
  
     Se l'agente è occupato a rispondere al polling del processo di controllo degli agenti, non sarà possibile verificare se è in funzione in modo appropriato. Vi sono vari motivi per cui l'agente di replica potrebbe essere occupato. È possibile che vi siano molti dati in fase di replica oppure problemi di sviluppo o di configurazione delle applicazioni che determinano lunghi tempi di elaborazione dei processi.  
  
-   L'agente non è in grado di accedere a uno dei computer nella topologia.  
  
     Tutti gli agenti hanno un parametro **-LoginTimeOut** (per impostazione predefinita pari a 15 secondi) che determina la durata del tentativo di accesso di un agente a un nodo di replica, ad esempio il tempo di accesso di un agente di merge al server di pubblicazione. Se il valore impostato per **-LoginTimeOut** è superiore all'intervallo in cui viene eseguito il processo di controllo degli agenti di replica, la causa principale dell'errore potrebbe essere un problema di accesso, ovvero l'errore MSSQL_ENG020554 viene generato prima che l'agente riesca a generare un errore più specifico.  
  
## <a name="user-action"></a>Azione dell'utente  
 A seconda della causa dell'errore è necessaria un'azione specifica:  
  
-   Per tutti i casi in cui viene generato questo errore:  
  
     Controllare i dettagli dell'errore in Monitoraggio replica e quindi riavviare l'agente se si è arrestato. Nei dettagli dell'errore potrebbero essere contenute informazioni aggiuntive sui motivi del malfunzionamento dell'agente. Se l'agente è in esecuzione, non arrestarlo né riavviarlo, poiché ciò potrebbe aggravare il problema. Per informazioni sulla visualizzazione dello stato dell'agente e dei dettagli di errore in Monitoraggio replica, vedere gli argomenti seguenti:  
  
    -   Per l'agente snapshot, l'agente di lettura log e l'agente di lettura coda, vedere [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
    -   Per l'agente di distribuzione e l'agente di merge, vedere [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
-   Se l'errore viene generato spesso perché l'agente è occupato:  
  
     Potrebbe essere necessario riprogettare l'applicazione in modo da ridurre il tempo di elaborazione.  
  
     È possibile aumentare l'intervallo di controllo dello stato dell'agente tramite la finestra di dialogo **Proprietà processo** . Per informazioni sull'accesso a questa finestra di dialogo per processi di replica, vedere [Visualizzare le informazioni ed eseguire attività relative a un server di pubblicazione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md).  
  
-   Se l'agente non è in grado di accedere a uno dei computer nella topologia:  
  
     È consigliabile impostare il parametro **-LoginTimeOut** su un valore inferiore rispetto all'intervallo di esecuzione del processo di controllo degli agenti di replica. In alcuni casi, il valore di **-LoginTimeOut** è superiore a causa di problemi di rete che determinano il timeout degli accessi. Impostando **-LoginTimeOut** su un valore inferiore, sarà possibile ricevere errori più specifici e quindi risolvere più facilmente i problemi di accesso che potrebbero essere causati da autorizzazioni, problemi di rete o altro. I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
    -   [Usare i profili agenti di replica](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Visualizzare e modificare i parametri del prompt dei comandi dell'agente di replica &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agente distribuzione repliche](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agente merge repliche](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
