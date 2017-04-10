---
title: "Aggiunta e rimozione di server di pubblicazione da Monitoraggio replica | Microsoft Docs"
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
  - "Monitoraggio replica, aggiunta e rimozione di server di pubblicazione"
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Aggiunta e rimozione di server di pubblicazione da Monitoraggio replica
  Se il server dal quale viene avviato Monitoraggio replica è un server di pubblicazione, quest'ultimo verrà automaticamente aggiunto al monitoraggio. È possibile aggiungere ulteriori server di pubblicazione tramite il **Aggiungi server di pubblicazione** la finestra di dialogo. Dopo l'aggiunta di un server di pubblicazione, questo viene visualizzato in un gruppo di server nel riquadro sinistro di Monitoraggio replica. Il **server di pubblicazione personali** gruppo è inclusa per impostazione predefinita, ma è possibile creare nuovi gruppi per gestire uno o più topologie di replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per aggiungere un server di pubblicazione SQL Server  
  
1.  Pulsante destro del mouse il **Monitoraggio replica** nodo o un server di pubblicazione nodo nel riquadro a sinistra di gruppo e quindi fare clic su **Aggiungi server di pubblicazione**.  
  
2.  Nel **Aggiungi server di pubblicazione** la finestra di dialogo, fare clic su **Aggiungi**, e quindi fare clic su **aggiungere pubblicazione SQL Server**.  
  
3.  Nel **Connetti al Server** nella finestra di dialogo immettere il nome del server di pubblicazione e quindi selezionare il tipo di autenticazione. Se si seleziona **autenticazione di SQL Server**, immettere un account di accesso e una password. Le credenziali specificate vengono salvate da Monitoraggio replica per poterle utilizzare per le connessioni future a questo server. L'account di Windows o account di accesso di SQL Server specificato deve essere un membro del **sysadmin** predefinito o un membro del server il **replmonitor** ruolo predefinito del database nel database di distribuzione.  
  
4.  Fare clic su **Connetti**. Se il server di pubblicazione utilizza un server di distribuzione remoto, verrà richiesto di connettersi al server di distribuzione nel **Connetti al Server** la finestra di dialogo. Le credenziali specificate vengono salvate da Monitoraggio replica per poterle utilizzare per le connessioni future a questo server. L'account di Windows o account di accesso di SQL Server specificato deve essere un membro del **sysadmin** predefinito o un membro del server il **replmonitor** ruolo predefinito del database nel database di distribuzione.  
  
5.  Il nome del server di pubblicazione e server di distribuzione vengono visualizzati nel **avviare il monitoraggio di server di pubblicazione seguenti** griglia.  
  
6.  Per specificare le opzioni di aggiornamento e connessione del server di pubblicazione, selezionare il server nella griglia e modificare le opzioni in base alle necessità. Per ulteriori informazioni sulle opzioni di aggiornamento, vedere [la memorizzazione nella cache, aggiornamento e prestazioni di monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Selezionare il gruppo all'interno del quale deve essere visualizzato il server di pubblicazione in Monitoraggio replica. Per creare un nuovo gruppo, fare clic su **nuovo gruppo**, quindi immettere un nome di gruppo, selezionare il gruppo nel **Mostra server di pubblicazione nel gruppo seguente** elenco.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per aggiungere un server di pubblicazione Oracle  
  
1.  Pulsante destro del mouse il **Monitoraggio replica** nodo o un server di pubblicazione nodo nel riquadro a sinistra di gruppo e quindi fare clic su **Aggiungi server di pubblicazione**.  
  
2.  Nel **Aggiungi server di pubblicazione** la finestra di dialogo, fare clic su **Aggiungi**, e quindi fare clic su **Aggiungi server di pubblicazione Oracle**.  
  
3.  Nel **Connetti al Server** finestra di dialogo, immettere il nome del [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server di distribuzione associato al server di pubblicazione Oracle e quindi selezionare il tipo di autenticazione. Se si seleziona **autenticazione di SQL Server**, immettere un account di accesso e una password. Le credenziali specificate vengono salvate da Monitoraggio replica per poterle utilizzare per le connessioni future a questo server. L'account di Windows o account di accesso di SQL Server specificato deve essere un membro del **sysadmin** predefinito o un membro del server il **replmonitor** ruolo predefinito del database nel database di distribuzione.  
  
4.  Fare clic su **Connetti**.  
  
5.  Il nome del server di pubblicazione e server di distribuzione vengono visualizzati nel **avviare il monitoraggio di server di pubblicazione seguenti** griglia.  
  
6.  Per specificare le opzioni di aggiornamento e connessione del server di pubblicazione, selezionare il server nella griglia e modificare le opzioni in base alle necessità. Per ulteriori informazioni sulle opzioni di aggiornamento, vedere [la memorizzazione nella cache, aggiornamento e prestazioni di monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Selezionare il gruppo all'interno del quale deve essere visualizzato il server di pubblicazione in Monitoraggio replica. Per creare un nuovo gruppo, fare clic su **nuovo gruppo**, quindi immettere un nome di gruppo, selezionare il gruppo nel **Mostra server di pubblicazione nel gruppo seguente** elenco.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per aggiungere uno o più server di pubblicazione che utilizzano lo stesso server di distribuzione  
  
1.  Pulsante destro del mouse il **Monitoraggio replica** nodo o un server di pubblicazione nodo nel riquadro a sinistra di gruppo e quindi fare clic su **Aggiungi server di pubblicazione**.  
  
2.  Nel **Aggiungi server di pubblicazione** la finestra di dialogo, fare clic su **Aggiungi**, e quindi fare clic su **specificare un server di distribuzione e aggiungere il server di pubblicazione**.  
  
3.  Nel **Connetti al Server** nella finestra di dialogo immettere il nome del server di distribuzione e quindi selezionare il tipo di autenticazione. Se si seleziona **autenticazione di SQL Server**, immettere un account di accesso e una password. Le credenziali specificate vengono salvate da Monitoraggio replica per poterle utilizzare per le connessioni future a questo server. L'account di Windows o account di accesso di SQL Server specificato deve essere un membro del **sysadmin** predefinito o un membro del server il **replmonitor** ruolo predefinito del database nel database di distribuzione.  
  
4.  Fare clic su **Connetti**.  
  
5.  Il nome del server di distribuzione e ogni server di pubblicazione vengono visualizzati nel **avviare il monitoraggio di server di pubblicazione seguenti** griglia. Se un server di pubblicazione è già stato aggiunto a Monitoraggio replica, non verrà visualizzato nella griglia.  
  
6.  Per specificare le opzioni di aggiornamento e connessione del server di pubblicazione, selezionare il server nella griglia e modificare le opzioni in base alle necessità. Per ulteriori informazioni sulle opzioni di aggiornamento, vedere [la memorizzazione nella cache, aggiornamento e prestazioni di monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Selezionare il gruppo all'interno del quale devono essere visualizzati i server di pubblicazione in Monitoraggio replica. Per creare un nuovo gruppo, fare clic su **nuovo gruppo**, quindi immettere un nome di gruppo, selezionare il gruppo nel **Mostra server di pubblicazione nel gruppo seguente** elenco.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per modificare le impostazioni del server di pubblicazione e dei gruppi di server di pubblicazione  
  
1.  Fare doppio clic su un server di pubblicazione nel riquadro a sinistra e quindi fare clic su **Impostazioni server di pubblicazione**.  
  
2.  Apportare le modifiche nella **Impostazioni server di pubblicazione** la finestra di dialogo:  
  
    -   Per modificare le credenziali utilizzate per connettersi a un server di monitoraggio replica, fare clic su **connessione server di pubblicazione** o **connessione server di distribuzione**, quindi immettere le credenziali nel **Connetti al Server** la finestra di dialogo.  
  
    -   Per spostare un server di pubblicazione da un gruppo a un altro, selezionare il server di pubblicazione nel **avviare il monitoraggio di server di pubblicazione seguenti** griglia, quindi selezionare il nuovo gruppo nel **Mostra server di pubblicazione nel gruppo seguente** elenco.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per rimuovere un server di pubblicazione da Monitoraggio replica  
  
1.  Fare clic con il pulsante destro del mouse su un server di pubblicazione nel riquadro sinistro.  
  
2.  Scegliere **Rimuovi**.  
  
### Per aggiungere un gruppo di server di pubblicazione a Monitoraggio replica  
  
1.  È possibile creare gruppi di server di pubblicazione solo quando si aggiunge un server di pubblicazione o si modificano le impostazioni di un server di pubblicazione. Per ulteriori informazioni, vedere le procedure relative all'aggiunta di un server di pubblicazione.  
  
### Per rimuovere un gruppo di server di pubblicazione da Monitoraggio replica  
  
1.  Spostare tutti i server di pubblicazione in un gruppo diverso oppure rimuoverli da Monitoraggio replica. Per ulteriori informazioni, vedere le procedure precedenti in questo argomento.  
  
2.  Pulsante destro del mouse il gruppo di server di pubblicazione e quindi fare clic su **rimuovere**.  
  
## Vedere anche  
 [Configurazione della distribuzione](../../../relational-databases/replication/configure-distribution.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  