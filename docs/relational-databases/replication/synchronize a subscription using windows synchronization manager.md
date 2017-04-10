---
title: "Sincronizzazione di una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows (Gestione sincronizzazione Microsoft Windows) | Microsoft Docs"
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
  - "sincronizzazione [replica di SQL Server], Gestione sincronizzazione Windows"
  - "Gestione sincronizzazione Microsoft Windows"
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Sincronizzazione di una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows (Gestione sincronizzazione Microsoft Windows)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Gestione sincronizzazione Microsoft Windows è utilizzabile solo per sincronizzare le sottoscrizioni a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pubblicazioni se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione nello stesso computer come Gestione sincronizzazione (può anche essere utilizzato per sincronizzare i file offline e pagine Web). Per utilizzare Gestione sincronizzazione:  
  
1.  Abilitare la sincronizzazione delle sottoscrizioni pull con Gestione sincronizzazione Microsoft Windows nel **Proprietà sottoscrizione - \< sottoscrittore>: \< SubscriptionDatabase>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [visualizzare e modificare le proprietà di sottoscrizione Pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
2.  Accedere a Gestione sincronizzazione tramite il **avviare** dal menu di Windows.  
  
 Gestione sincronizzazione consente di utilizzare il sistema di risoluzione interattivo per le sottoscrizioni di tipo merge. Generalmente, i conflitti rilevati durante la sincronizzazione vengono risolti automaticamente, ma se la risoluzione interattiva è abilitata, essi possono essere risolti da un utente in fase di sincronizzazione. Se una sincronizzazione viene eseguita all'esterno di Gestione sincronizzazione Microsoft Windows (come sincronizzazione pianificata o sincronizzazione su richiesta in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Monitoraggio replica), i conflitti vengono risolti automaticamente senza richiedere l'intervento dell'utente, in base al sistema di risoluzione specificato per l'articolo.  
  
> [!NOTE]  
>  A partire da [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] e [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], le versioni a 64 bit di Gestione sincronizzazione Microsoft Windows non possono rilevare sottoscrizioni a 32 bit.  
  
### Per abilitare la sincronizzazione delle sottoscrizioni pull con Gestione sincronizzazione Microsoft Windows  
  
1.  Nel **Generale** pagina della **Proprietà sottoscrizione - \< sottoscrittore>: \< SubscriptionDatabase>** la finestra di dialogo, selezionare un valore di **abilitare** per il **Usa Gestione sincronizzazione Microsoft Windows** opzione.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Per sincronizzare una sottoscrizione pull con Gestione sincronizzazione  
  
1.  Avviare Gestione sincronizzazione in uno dei modi seguenti:  
  
    -   In Internet Explorer, fare clic su **strumenti**, quindi fare clic su **Synchronize**.  
  
    -   Fare clic su **avviare**, scegliere **programmi** o **tutti i programmi**, scegliere **Accessori**, quindi fare clic su **Synchronize**.  
  
    -   Fare clic su **avviare**, quindi fare clic su **eseguire.** Nel **eseguire** la finestra di dialogo, digitare **mobsync.exe** nel **aprire** campo e quindi fare clic su **OK**.  
  
2.  Nel **sincronizzazione elementi** finestra di dialogo, selezionare le sottoscrizioni da sincronizzare. Le sottoscrizioni vengono elencate al di sotto delle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer.  
  
3.  Fare clic su **sincronizzare**.  
  
### Per reinizializzare una sottoscrizione pull con Gestione sincronizzazione  
  
1.  Nel **sincronizzazione elementi** nella finestra di dialogo selezionare una sottoscrizione e quindi fare clic su **proprietà**.  
  
2.  Nel **Proprietà sottoscrizione SQL Server** la finestra di dialogo, fare clic su **Reinizializza sottoscrizione**.  
  
3.  Scegliere **Sì**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Alla successiva sincronizzazione, per impostazione predefinita verrà applicato un nuovo snapshot al database di sottoscrizione. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
> [!NOTE]  
>  La replica di tipo merge consente il caricamento nel server di pubblicazione delle eventuali modifiche in attesa prima dell'applicazione dello snapshot. Tale opzione tuttavia non è disponibile da Gestione sincronizzazione. Per caricare le modifiche, sincronizzare la sottoscrizione prima di reinizializzarla.  
  
### Per impostare le proprietà di una sottoscrizione pull in Gestione sincronizzazione  
  
1.  Nel **sincronizzazione elementi** nella finestra di dialogo selezionare una sottoscrizione e quindi fare clic su **proprietà**.  
  
2.  Visualizzare e modificare le proprietà nelle schede seguenti:  
  
    -   **Identificazione**  
  
    -   **Account di accesso**, **account di accesso**, e **pubblicazione** (replica di tipo merge solo)  
  
    -   **Informazioni Server Web** (per sottoscrizioni di tipo merge nei Sottoscrittori che eseguono SQL Server 2005 o versioni successive)  
  
    -   **Altro**  
  
     È consigliabile utilizzare l'autenticazione di Windows per tutte le connessioni. Per informazioni sulle autorizzazioni necessarie per l'agente di distribuzione e l'agente di Merge, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Per rimuovere una sottoscrizione pull da Gestione sincronizzazione  
  
1.  Nel **sincronizzazione elementi** nella finestra di dialogo selezionare una sottoscrizione e quindi fare clic su **proprietà**.  
  
2.  Nel **Proprietà sottoscrizione SQL Server** la finestra di dialogo, fare clic su **Rimuovi sottoscrizione**.  
  
3.  Selezionare un'opzione di **Rimuovi sottoscrizione** la finestra di dialogo.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Per utilizzare il sistema di risoluzione interattivo  
  
1.  Abilitare l'articolo e la sottoscrizione per l'utilizzo della risoluzione interattiva. Per ulteriori informazioni, vedere [specificare risoluzione interattiva dei conflitti per articoli di Merge](../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md).  
  
2.  In seguito all'inizio della sincronizzazione della sottoscrizione in Gestione sincronizzazione, il sistema di risoluzione interattivo viene avviato automaticamente se la risoluzione interattiva dei conflitti è abilitata e si sono verificati conflitti tra uno o più articoli. In tale sistema i conflitti vengono visualizzati uno alla volta, con un suggerimento di risoluzione per ogni conflitto (in base al sistema di risoluzione dei conflitti specificato al momento della creazione della pubblicazione e della sottoscrizione).  
  
3.  Facoltativamente, modificare le colonne visualizzate nel sistema di risoluzione interattivo e quindi fare clic su uno dei pulsanti seguenti per risolvere il conflitto:  
  
    -   **Accetta soluzione proposta**  
  
    -   **Accetta server di pubblicazione**  
  
    -   **Accetta Sottoscrittore**  
  
    -   **Risolvi tutti automaticamente** (tutti i conflitti correnti vengono risolti senza ulteriore input)  
  
     La riga selezionata viene quindi applicata al server di pubblicazione e/o al Sottoscrittore e propagata ad altri nodi nella topologia durante le sincronizzazioni successive.  
  
> [!NOTE]  
>  Le modifiche vengono applicate solo se fanno parte della riga scelta per la risoluzione. Ad esempio, se si apportano modifiche nel **Publisher**, quindi fare clic su **Accetta Sottoscrittore**, le modifiche verranno ignorate.  
  
## Vedere anche  
 [Risoluzione dei conflitti interattiva](../../relational-databases/replication/merge/interactive-conflict-resolution.md)  
  
  