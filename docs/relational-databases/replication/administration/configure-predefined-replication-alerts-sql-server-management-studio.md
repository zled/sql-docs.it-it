---
title: "Configurazione degli avvisi di replica predefiniti (SQL Server Management Studio) | Microsoft Docs"
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
  - "avvisi [replica di SQL Server]"
  - "avvisi di replica predefiniti [replica di SQL Server]"
ms.assetid: c0414147-7ffe-4f9a-908c-71c1b5201584
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Configurazione degli avvisi di replica predefiniti (SQL Server Management Studio)
  La replica offre gli avvisi predefiniti seguenti, configurabili in risposta a eventi di replica:  
  
-   **Replica: operazione dell'agente riuscita**  
  
-   **Replica: errore dell'agente**  
  
-   **Replica: nuovo tentativo dell'agente**  
  
-   **Replica: eliminata sottoscrizione scaduta**  
  
-   **Replica: la sottoscrizione è stata reinizializzata dopo l'errore di convalida**  
  
-   **Replica: la convalida dei dati nel Sottoscrittore non è riuscita**  
  
-   **Replica: la convalida dei dati nel Sottoscrittore è riuscita**  
  
-   **Replica: arresto dell'agente personalizzato**  
  
 Configurare gli avvisi dal **avvisi** cartella [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o **avvisi** scheda in Monitoraggio replica. Per ulteriori informazioni sull'accesso a questa scheda, vedere [visualizzare le informazioni ed esecuzione delle attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md).  
  
 In aggiunta a questi avvisi, in Monitoraggio replica è disponibile un set di avvisi relativi allo stato e alle prestazioni. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). È inoltre possibile definire avvisi per altri eventi di replica utilizzando l'infrastruttura degli avvisi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [creare un evento definito dall'utente](../../../ssms/agent/create-a-user-defined-event.md).  
  
### Per configurare un avviso di replica predefinito in Management Studio  
  
1.  Connettersi al server di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere il **SQL Server Agent** cartella, quindi espandere il **avvisi** cartella.  
  
3.  Fare doppio clic su un avviso di replica e quindi fare clic su **proprietà**.  
  
4.  Impostare le opzioni **\< AlertName> proprietà dell'avviso** la finestra di dialogo:  
  
    -   Nella pagina **Generale** fare clic su **Abilita**e specificare il database a cui si desidera applicare l'avviso.  
  
    -   Nel **risposta** specificare se deve essere inviato un messaggio di posta e/o un processo deve essere eseguito.  
  
         Se l'avviso è **replica: sottoscrittore non supera la convalida dei dati**, è possibile specificare il processo di risposta disponibile nella replica per questo avviso: selezionare **Esegui processo**, quindi fare clic sul pulsante Sfoglia (**...**). Nel **Individua processo** la finestra di dialogo, fare clic su **Sfoglia**. Nel **Cerca oggetti** nella finestra di dialogo **reinizializzazione delle sottoscrizioni con errori di convalida dei dati**. Fare clic su **OK** in entrambe le finestre di dialogo. Durante l'esecuzione il processo utilizza una chiamata di procedura remota (RPC) a una stored procedure che reinizializza la sottoscrizione. Se il server di pubblicazione utilizza un server di distribuzione remoto, è necessario definire un account di accesso al server remoto sul server di pubblicazione in modo che sia possibile eseguire la chiamata di procedura remota (RPC) dal server di distribuzione al server di pubblicazione.  
  
    -   Nella pagina **Opzioni** personalizzare il testo della risposta.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per configurare un avviso per una soglia in Monitoraggio replica  
  
1.  Nel **avvisi** fare clic sulla scheda **Configura avvisi**.  
  
2.  Nella finestra di dialogo **Configura avvisi di replica** selezionare un avviso e quindi fare clic su **Configura**.  
  
3.  Impostare le opzioni **\< AlertName> proprietà dell'avviso** la finestra di dialogo:  
  
    -   Nella pagina **Generale** fare clic su **Abilita**e specificare il database a cui si desidera applicare l'avviso.  
  
    -   Nel **risposta** specificare se deve essere inviato un messaggio di posta e/o un processo deve essere eseguito.  
  
         Se l'avviso è **replica: sottoscrittore non supera la convalida dei dati**, è possibile specificare il processo di risposta disponibile nella replica per questo avviso: selezionare **Esegui processo**, quindi fare clic sul pulsante Sfoglia (**...**). Nel **Individua processo** la finestra di dialogo, fare clic su **Sfoglia**. Nel **Cerca oggetti** nella finestra di dialogo **reinizializzazione delle sottoscrizioni con errori di convalida dei dati**. Fare clic su **OK** in entrambe le finestre di dialogo. Durante l'esecuzione il processo utilizza una chiamata di procedura remota (RPC) a una stored procedure che reinizializza la sottoscrizione. Se il server di pubblicazione utilizza un server di distribuzione remoto, è necessario definire un account di accesso al server remoto sul server di pubblicazione in modo che sia possibile eseguire la chiamata di procedura remota (RPC) dal server di distribuzione al server di pubblicazione.  
  
    -   Nella pagina **Opzioni** personalizzare il testo della risposta.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Scegliere **Chiudi**.  
  
## Vedere anche  
 [Utilizzare gli avvisi per gli eventi degli agenti di replica](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)  
  
  