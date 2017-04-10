---
title: "Inizializzazione sottoscrizioni | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.initializesubscriptions.f1"
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Inizializzazione sottoscrizioni
  È necessario inizializzare i Sottoscrittori prima che possano iniziare a ricevere dati replicati. Non è necessario un set di dati iniziale, ma è necessario che il Sottoscrittore disponga almeno dello schema per ogni oggetto replicato, nonché delle tabelle dei metadati e delle procedure necessarie per la replica.  
  
## Opzioni  
 **Proprietà sottoscrizione**  
 Selezionare la casella di controllo di **inizializzare** colonna per ogni sottoscrittore che richiede un set di dati iniziale. Se la casella di controllo non è selezionata, verranno inizializzati solo i metadati e le procedure della replica. Per ulteriori informazioni sull'inizializzazione di una sottoscrizione senza uno snapshot, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Selezionare **immediatamente** dalla casella di riepilogo a discesa di **quando** colonna per il trasferimento dell'agente di Merge o l'agente di distribuzione file di snapshot al sottoscrittore dopo aver completata questa procedura guidata. Selezionare **Alla prima sincronizzazione** per fare in modo che l'agente trasferisca i file alla successiva esecuzione pianificata dell'agente. L'opzione **Immediatamente** non è disponibile per le sottoscrizioni pull di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. L'agente di merge e l'agente di distribuzione non vengono eseguiti nelle istanze di [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. È pertanto necessario inizializzare la sottoscrizione utilizzando un altro metodo.  
  
> [!NOTE]  
>  Durante la procedura guidata è possibile che venga richiesto di selezionare la connessione al server di distribuzione per consentire l'avvio del processo appropriato per l'agente di distribuzione o l'agente di merge.  
  
## Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Inizializzazione di una sottoscrizione](../../relational-databases/replication/initialize-a-subscription.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  