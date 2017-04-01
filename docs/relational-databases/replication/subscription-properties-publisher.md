---
title: "Propriet&#224; sottoscrizione - Server di pubblicazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subproperties.publisher.f1"
helpviewer_keywords: 
  - "Proprietà sottoscrizione - finestra di dialogo"
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propriet&#224; sottoscrizione - Server di pubblicazione
  Il **le proprietà della sottoscrizione** la finestra di dialogo nel server di pubblicazione consente di visualizzare e impostare proprietà per le sottoscrizioni push. È inoltre possibile visualizzare alcune proprietà per le sottoscrizioni pull, ma il **le proprietà delle sottoscrizioni** la finestra di dialogo nel Sottoscrittore consente di visualizzare proprietà aggiuntive e le proprietà da modificare.  
  
 Ogni proprietà di **le proprietà della sottoscrizione** la finestra di dialogo include una descrizione. Fare clic su una proprietà per visualizzarne la descrizione nella parte inferiore della finestra di dialogo. In questo argomento vengono fornite informazioni aggiuntive su alcune proprietà che, nella maggior parte dei casi, sono visualizzate nel server di pubblicazione solo per le sottoscrizioni push. Le proprietà sono raggruppate nelle categorie seguenti:  
  
-   Proprietà che si applicano a tutte le sottoscrizioni.  
  
-   Proprietà che si applicano alle sottoscrizioni transazionali.  
  
-   Proprietà che si applicano alle sottoscrizioni di tipo merge.  
  
 Se un'opzione è visualizzata in modalità di sola lettura, può essere impostata solo al momento della creazione della sottoscrizione. Se si desidera impostare opzioni non disponibili nella Creazione guidata nuova sottoscrizione, creare la sottoscrizione tramite stored procedure. Per ulteriori informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) e [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
## Opzioni per tutte le sottoscrizioni  
 **Sicurezza**  
 Fare clic sui **account processo agente** riga e quindi fare clic sul pulsante delle proprietà (**...**) per modificare l'account con cui l'agente di distribuzione o l'agente di Merge viene eseguito nel server di distribuzione. Per modificare l'account in cui l'agente di distribuzione o l'agente di Merge stabilisce le connessioni al server di sottoscrizione, fare clic su **connessione al sottoscrittore**, e quindi fare clic sul pulsante delle proprietà (**...**).  
  
 Per ulteriori informazioni sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Opzioni per le sottoscrizioni transazionali  
 **Impedisci il loop delle transazioni**  
 Consente di stabilire se l'agente di distribuzione reinvia le transazioni originate nel Sottoscrittore al Sottoscrittore. Questa opzione viene utilizzata per la replica transazionale bidirezionale. Per ulteriori informazioni, vedere [la replica transazionale bidirezionale](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).  
  
 **Sottoscrizione aggiornabile**  
 Consente di stabilire se le modifiche del Sottoscrittore vengono replicate sul server di pubblicazione. È possibile replicare le modifiche utilizzando l'aggiornamento in coda o immediato. L'opzione **metodo di aggiornamento del sottoscrittore** determina quale metodo utilizzare. Per ulteriori informazioni, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
## Opzioni per sottoscrizioni di tipo merge  
 **Definizione partizione (HOST_NAME)**  
 Per una pubblicazione che utilizza filtri con parametri, replica di tipo merge valuta una delle due funzioni di sistema (o entrambe se il filtro fa riferimento a entrambe le funzioni) durante la sincronizzazione per determinare i dati che deve ricevere un sottoscrittore: **SUSER_SNAME ()** o **HOST_NAME ()**. Per impostazione predefinita, **HOST_NAME ()** restituisce il nome del computer in cui è in esecuzione l'agente di Merge, ma è possibile eseguire l'override di questo valore nella creazione guidata nuova sottoscrizione. Per ulteriori informazioni sui filtri con parametri e si esegue l'override **HOST_NAME ()**, vedere [filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Tipo di sottoscrizione** e **priorità**  
 Indica se la sottoscrizione è una sottoscrizione client o server. Questa impostazione non può essere modificata dopo la creazione della sottoscrizione. Le sottoscrizioni server possono ripubblicare i dati in altri Sottoscrittori. A tali sottoscrizioni è inoltre possibile assegnare una priorità per la risoluzione dei conflitti.  
  
 Se si seleziona un tipo di sottoscrizione server nella Creazione guidata nuova sottoscrizione, al Sottoscrittore viene assegnata una priorità che verrà utilizzata nella risoluzione dei conflitti.  
  
 **Risoluzione interattiva**  
 Consente di indicare di utilizzare l'interfaccia utente del sistema di risoluzione dei conflitti interattivo durante la sincronizzazione di tipo merge. Questa operazione richiede un valore di **abilitare** per **Usa Gestione sincronizzazione Microsoft Windows**. Per altre informazioni, vedere [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
## Vedere anche  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  