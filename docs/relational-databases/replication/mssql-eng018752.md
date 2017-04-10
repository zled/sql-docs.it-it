---
title: "MSSQL_ENG018752 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG018752 - errore"
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG018752
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|18752|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|A un database può connettersi un solo agente di lettura log o una sola procedura correlata ai log (sp_repldone, sp_replcmds e sp_replshowcmds) alla volta. Se è stata eseguita una procedura correlata ai log, eliminare la connessione utilizzata per eseguire la procedura oppure eseguire sp_replflush tramite tale connessione prima di avviare l'agente di lettura log o di eseguire un'altra procedura relativa ai log.|  
  
## Spiegazione  
 Più connessioni correnti stanno tentando di eseguire le seguenti operazioni: **sp_repldone**, **sp_replcmds**, o **sp_replshowcmds**. Le stored procedure [sp_repldone & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md) e [sp_replcmds & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) sono stored procedure utilizzate dall'agente di lettura Log per individuare e aggiornare le informazioni sulle transazioni replicate in un database pubblicato. La stored procedure [sp_replshowcmds & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md) viene utilizzato per risolvere determinati tipi di problemi relativi alla replica transazionale.  
  
 Questo errore viene generato nelle circostanze seguenti:  
  
-   Se l'agente di lettura log di un database pubblicato è in esecuzione e un secondo agente di lettura log tenta l'esecuzione sullo stesso database, per il secondo agente viene generato l'errore, che appare nella cronologia dell'agente.  
  
     In una situazione in cui compaiono più agenti, è possibile che uno di loro sia il risultato di un processo orfano.  
  
-   Se l'agente di lettura Log per un database pubblicato viene avviato e un utente esegue **sp_repldone**, **sp_replcmds**, o **sp_replshowcmds** nello stesso database, viene generato l'errore nell'applicazione in cui è stata eseguita la stored procedure (ad esempio **sqlcmd**).  
  
-   Se nessun agente di lettura Log è in esecuzione per un database pubblicato e un utente esegue **sp_repldone**, **sp_replcmds**, o **sp_replshowcmds** e non chiude la connessione su cui è stata eseguita la procedura, l'errore viene generata quando l'agente di lettura Log tenta di connettersi al database.  
  
## Azione dell'utente  
 I passaggi seguenti possono contribuire alla risoluzione del problema. Se uno dei passaggi consente l'avvio senza errori dell'agente di lettura log, non è necessario completare i passaggi rimanenti.  
  
-   Verificare nella cronologia dell'agente di lettura log la presenza di eventuali altri errori che potrebbero contribuire a questo errore. Per informazioni sulla visualizzazione dei dettagli di errore e di stato dell'agente in Monitoraggio replica, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   Verificare nell'output di [sp_who & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) per i numeri di identificazione di processo (SPID) connessi al database pubblicato. Chiudere tutte le connessioni che potrebbero aver eseguito **sp_repldone**, **sp_replcmds**, o **sp_replshowcmds**.  
  
-   Riavviare l'agente di lettura log. Per ulteriori informazioni, vedere [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (metterlo offline oppure online in un cluster) sul server di distribuzione. Se vi è possibilità che un processo pianificato abbia eseguito **sp_repldone**, **sp_replcmds**, o **sp_replshowcmds** da qualsiasi altro [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dell'istanza, riavviare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente per anche tali istanze. Per ulteriori informazioni, vedere [avviare, arrestare o sospendere il servizio SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
-   Eseguire [sp_replflush & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) nel server di pubblicazione nel database di pubblicazione e quindi riavviare l'agente di lettura Log.  
  
-   Se l'errore continua a verificarsi, aumentare il livello di dettaglio per la registrazione delle operazioni dell'agente e specificare un file di output per il log. A seconda del contesto dell'errore, in questo modo si potrebbero ottenere ulteriori informazioni sui passaggi che conducono all'errore e/o messaggi di errore aggiuntivi.  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
  