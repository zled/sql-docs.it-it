---
title: "Aggiungi server di pubblicazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.addpublisher.f1"
helpviewer_keywords: 
  - "Aggiungi server di pubblicazione - finestra di dialogo"
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Aggiungi server di pubblicazione
  La finestra di dialogo **Aggiungi server di pubblicazione** consente di aggiungere uno o più server di pubblicazione al riquadro sinistro di Monitoraggio replica. Dopo l'aggiunta di un server di pubblicazione, selezionare il server nel riquadro sinistro per visualizzare le informazioni relative nel riquadro destro.  
  
## Opzioni  
 **Aggiungi**  
 Fare clic per selezionare un tipo di server di pubblicazione per aggiungere, che consente di avviare il **Connetti al Server** la finestra di dialogo. Le opzioni disponibili sono le seguenti:  
  
-   **Aggiungi server di pubblicazione SQL Server**  
  
     Consente di connettersi al server di pubblicazione utilizzando la finestra di dialogo **Connetti al server** .  
  
-   **Aggiungi server di pubblicazione Oracle**  
  
     Consente di connettersi al server di distribuzione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associato al server di pubblicazione Oracle utilizzando la finestra di dialogo **Connetti al server** .  
  
-   **Specificare un server di distribuzione e aggiungere i relativi server di pubblicazione**  
  
     Consente di connettersi al server di distribuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associato a uno o più server di pubblicazione utilizzando la finestra di dialogo **Connetti al server** .  
  
 Dopo avere stabilito la connessione al server di pubblicazione o di distribuzione, il nome di ogni server di pubblicazione e il nome del relativo server di distribuzione vengono visualizzati nella griglia posta nella parte superiore della finestra di dialogo.  
  
> [!NOTE]  
>  Il server di distribuzione e il server di pubblicazione vengono spesso eseguiti sulla stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma il server di distribuzione può essere eseguito su un'altra istanza. Tale configurazione viene definita server di distribuzione remoto.  
  
 **Rimuovi**  
 Selezionare un server di pubblicazione nella griglia nella parte superiore della finestra di dialogo e fare clic su **rimuovere** per rimuovere il server di pubblicazione dall'elenco dei server di pubblicazione da aggiungere.  
  
> [!NOTE]  
>  Non è possibile utilizzare questo pulsante per rimuovere un server di pubblicazione già visualizzato in Monitoraggio replica. Per rimuovere un server di pubblicazione già visualizzato, fare doppio clic su server di pubblicazione nel riquadro sinistro di monitoraggio replica e fare clic su **rimuovere**.  
  
 **Connetti automaticamente all'avvio di Monitoraggio replica**  
 Selezionare questa casella di controllo per consentire a Monitoraggio replica di connettersi automaticamente al server di distribuzione e di recuperare informazioni sullo stato del server di pubblicazione selezionato nella griglia posta nella parte superiore della finestra di dialogo. Se questa casella di controllo è deselezionata, è necessario connettersi manualmente dopo l'avvio di monitoraggio replica: server di pubblicazione nel riquadro sinistro di monitoraggio replica di mouse e scegliere **Connect**.  
  
 **Aggiorna automaticamente lo stato del server di pubblicazione e delle sue pubblicazioni**  
 Selezionare questa opzione per consentire a Monitoraggio replica di aggiornare automaticamente lo stato del server di pubblicazione selezionato nella griglia posta nella parte superiore della finestra di dialogo. Se questa opzione è selezionata, Monitoraggio replica esegue il polling del server di distribuzione per ottenere informazioni sullo stato del server di pubblicazione e delle relative pubblicazioni. L'intervallo di polling viene impostato dall'opzione **Frequenza di aggiornamento** . Per ulteriori informazioni sull'aggiornamento in Monitoraggio replica, vedere [la memorizzazione nella cache, aggiornamento e prestazioni di monitoraggio replica](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Frequenza di aggiornamento**  
 Immettere un valore, espresso in secondi, per specificare la frequenza di polling del server di distribuzione per ottenere informazioni sullo stato da parte di Monitoraggio replica. Valori inferiori indicano un polling più frequente, che influisce sulle prestazioni del server di distribuzione se il monitoraggio include un numero elevato di server di pubblicazione. È consigliabile eseguire prove sul sistema per determinare un valore appropriato. L'impostazione **Frequenza di aggiornamento** viene utilizzata anche se si seleziona **Aggiornamento automatico** in una delle finestre dei dettagli di Monitoraggio replica.  
  
 **Mostra server di pubblicazione nel gruppo seguente**  
 Selezionare un gruppo di server di pubblicazione nell'elenco. Il server di pubblicazione viene visualizzato in questo gruppo nel riquadro sinistro. I gruppi consentono di organizzare i server di pubblicazione e non influiscono sul funzionamento della replica. Se non sono definiti gruppi o si desidera creare un nuovo gruppo fare clic su **Nuovo gruppo**.  
  
 **Nuovo gruppo**  
 Fare clic su questa opzione per creare un nuovo gruppo di server di pubblicazione. Un gruppo di server di pubblicazione consente di organizzare facilmente i server di pubblicazione all'interno di Monitoraggio replica. I gruppi non influiscono sulla replica dei dati o sulla relazione tra i server in una topologia di replica.  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  