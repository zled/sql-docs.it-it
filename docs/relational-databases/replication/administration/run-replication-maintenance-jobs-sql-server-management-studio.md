---
title: "Esecuzione di processi di manutenzione della replica (SQL Server Management Studio) | Microsoft Docs"
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
  - "processi [replica di SQL Server]"
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Esecuzione di processi di manutenzione della replica (SQL Server Management Studio)
  Nella replica vengono utilizzati i seguenti processi di manutenzione:  
  
-   **Reinizializzazione delle sottoscrizioni con errori di convalida dei dati**  
  
-   **Eliminazione del contenuto della cronologia dell'agente: distribuzione**  
  
-   **Aggiornamento del monitoraggio della replica per la distribuzione.**  
  
-   **Controllo degli agenti di replica**  
  
-   **Eliminazione del contenuto della distribuzione: distribuzione**  
  
-   **Pulizia dei riferimenti alla sottoscrizione scaduta**  
  
 Avviare e arrestare questi processi dal **processi** cartella [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e dal **agenti** scheda in Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md). Visualizzare e modificare le proprietà per ogni processo nel **proprietà processo - \< processo>** la finestra di dialogo, che è disponibile nella cartella e alla scheda stessa.  
  
### Per avviare e arrestare un processo di manutenzione della replica in Management Studio  
  
1.  Connettersi al server di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Fare doppio clic su un processo e quindi fare clic su **Avvia processo** o **Arresta processo**.  
  
### Per avviare e arrestare un processo di manutenzione della replica in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione in Monitoraggio replica e quindi selezionare un server di pubblicazione.  
  
2.  Fare clic su di **agenti** scheda.  
  
3.  Fare doppio clic su un processo nella griglia e quindi fare clic su **Avvia processo** o **Arresta processo**.  
  
### Per visualizzare e modificare le proprietà per un processo di manutenzione della replica in Management Studio  
  
1.  Connettersi al server di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Fare doppio clic su un processo e quindi fare clic su **proprietà**.  
  
4.  Nel **proprietà processo - \< processo>** la finestra di dialogo, modificare le proprietà se necessario e quindi fare clic su **OK**.  
  
### Per visualizzare e modificare le proprietà per un processo di manutenzione della replica in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione in Monitoraggio replica e quindi selezionare un server di pubblicazione.  
  
2.  Fare clic su di **agenti** scheda.  
  
3.  Fare doppio clic su un processo nella griglia e quindi fare clic su **proprietà**.  
  
4.  Nel **proprietà processo - \< processo>** la finestra di dialogo, modificare le proprietà se necessario e quindi fare clic su **OK**.  
  
## Vedere anche  
 [Avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Consente di visualizzare informazioni ed eseguire attività per un server di pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  