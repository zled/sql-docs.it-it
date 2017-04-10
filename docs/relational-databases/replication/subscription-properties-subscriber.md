---
title: "Propriet&#224; sottoscrizione - Sottoscrittore | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.subproperties.subscriber.f1"
helpviewer_keywords: 
  - "Proprietà sottoscrizione - finestra di dialogo"
ms.assetid: bef66929-3234-4a45-8ec4-3b271519d07a
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Propriet&#224; sottoscrizione - Sottoscrittore
  Il **le proprietà della sottoscrizione** la finestra di dialogo nel Sottoscrittore consente di visualizzare e impostare proprietà per le sottoscrizioni pull.  
  
 Ogni proprietà di **le proprietà della sottoscrizione** la finestra di dialogo include una descrizione. Fare clic su una proprietà per visualizzarne la descrizione nella parte inferiore della finestra di dialogo. In questo argomento sono specificate informazioni aggiuntive su diverse proprietà. Le proprietà sono raggruppate nelle categorie seguenti:  
  
-   Proprietà che si applicano a tutte le sottoscrizioni.  
  
-   Proprietà che si applicano alle sottoscrizioni transazionali.  
  
-   Proprietà che si applicano alle sottoscrizioni di tipo merge.  
  
 Se un'opzione è visualizzata in modalità di sola lettura, può essere impostata solo al momento della creazione della sottoscrizione. Se si desidera impostare opzioni non disponibili nella Creazione guidata nuova sottoscrizione, creare la sottoscrizione tramite stored procedure. Per ulteriori informazioni, vedere [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) e [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
> [!NOTE]  
>  Se non è stato ancora creato un processo dell'agente di merge o di distribuzione per la sottoscrizione, numerose proprietà non verranno visualizzate. Per creare un processo dell'agente per una sottoscrizione pull, eseguire [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) (per una sottoscrizione a una pubblicazione snapshot o transazionale) o [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) (per una sottoscrizione di una pubblicazione di tipo merge).  
  
## Opzioni per tutte le sottoscrizioni  
 **Inizializza dati pubblicati da uno snapshot**  
 Consente di stabilire se le sottoscrizioni vengono inizializzate tramite uno snapshot, impostazione predefinita, o un altro metodo. Per ulteriori informazioni sull'inizializzazione delle sottoscrizioni, vedere [inizializzare una sottoscrizione](../../relational-databases/replication/initialize-a-subscription.md).  
  
 **Posizione snapshot**  
 Consente di determinare la posizione da cui si accede ai file di snapshot durante l'inizializzazione o una nuova inizializzazione. La posizione può essere uno dei valori seguenti:  
  
-   **Percorso predefinito**: il percorso predefinito, che viene definito quando si configura un server di distribuzione. Per ulteriori informazioni, vedere [specificare la posizione predefinita degli Snapshot & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
-   **Cartella alternativa**: un percorso alternativo, che può essere specificato nel **Proprietà pubblicazione** la finestra di dialogo. Per ulteriori informazioni, vedere [percorsi della cartella Snapshot alternativa](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
-   **Cartella snapshot dinamici**: il percorso dello snapshot per pubblicazioni di tipo merge che utilizzano filtri di riga con parametri. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
-   **Cartella FTP**: una cartella accessibile a un server di protocollo FTP (File Transfer). Per ulteriori informazioni, vedere [trasferire gli snapshot tramite FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
 **Cartella snapshot**  
 Se si seleziona qualsiasi valore diverso da **percorso predefinito** per il **posizione Snapshot** opzione, è necessario specificare un percorso della cartella snapshot.  
  
 **Usa Gestione sincronizzazione Microsoft Windows**  
 Consente di stabilire se è possibile sincronizzare la sottoscrizione tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Sicurezza**  
 Fare clic sui **account processo agente** riga e quindi fare clic sul pulsante delle proprietà (**...**) per modificare l'account con cui l'agente di distribuzione o l'agente di Merge viene eseguito nel Sottoscrittore. Le opzioni di sicurezza correlate a connessioni dipendono dal tipo di sottoscrizione:  
  
-   Per le sottoscrizioni di una pubblicazione transazionale: per modificare l'account in cui l'agente di distribuzione stabilisce le connessioni al server di distribuzione, fare clic su **connessione server di distribuzione**, e quindi fare clic sul pulsante delle proprietà (**...**).  
  
-   Per le sottoscrizioni ad aggiornamento immediato di una pubblicazione transazionale: oltre la connessione di database di distribuzione descritta in precedenza, è possibile modificare il metodo utilizzato per propagare le modifiche dal Sottoscrittore al server di pubblicazione: fare clic su **connessione server di pubblicazione**, e quindi fare clic sul pulsante delle proprietà (**...**).  
  
-   Per le sottoscrizioni di pubblicazioni di tipo merge fare clic su **connessione server di pubblicazione**, e quindi fare clic sul pulsante delle proprietà (**...**).  
  
 Per ulteriori informazioni sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Opzioni per le sottoscrizioni transazionali  
 **Sottoscrizione aggiornabile**  
 Consente di stabilire se le modifiche del Sottoscrittore vengono replicate sul server di pubblicazione. È possibile replicare le modifiche utilizzando l'aggiornamento in coda o immediato. L'opzione **metodo di aggiornamento del sottoscrittore** determina quale metodo utilizzare. Per ulteriori informazioni, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
## Opzioni per sottoscrizioni di tipo merge  
 **Definizione partizione (HOST_NAME)**  
 Per una pubblicazione che utilizza filtri con parametri, replica di tipo merge valuta una delle due funzioni di sistema (o entrambe se il filtro fa riferimento a entrambe le funzioni) durante la sincronizzazione per determinare i dati che deve ricevere un sottoscrittore: **SUSER_SNAME ()** o **HOST_NAME ()**. Per impostazione predefinita, **HOST_NAME ()** restituisce il nome del computer in cui è in esecuzione l'agente di Merge, ma è possibile eseguire l'override di questo valore nella creazione guidata nuova sottoscrizione. Per ulteriori informazioni sui filtri con parametri e si esegue l'override **HOST_NAME ()**, vedere [filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Tipo di sottoscrizione** e **priorità**  
 Indica se la sottoscrizione è una sottoscrizione client o server. Questa impostazione non può essere modificata dopo la creazione della sottoscrizione. Le sottoscrizioni server possono ripubblicare i dati in altri Sottoscrittori. A tali sottoscrizioni è inoltre possibile assegnare una priorità per la risoluzione dei conflitti.  
  
 Se si seleziona un tipo di sottoscrizione server nella Creazione guidata nuova sottoscrizione, al Sottoscrittore viene assegnata una priorità che verrà utilizzata nella risoluzione dei conflitti  
  
 **Risoluzione interattiva**  
 Consente di indicare di utilizzare l'interfaccia utente del sistema di risoluzione dei conflitti interattivo durante la sincronizzazione di tipo merge. Questa operazione richiede un valore di **abilitare** per **Usa Gestione sincronizzazione Microsoft Windows**. Per altre informazioni, vedere [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
 **Sincronizzazione Web**  
 **Utilizzare la sincronizzazione Web** determina se la connessione a un [!INCLUDE[msCoName](../../includes/msconame-md.md)] server Internet Information Services (IIS) per sincronizzare la sottoscrizione. Questa opzione è disponibile solo se la pubblicazione è abilitata per la sincronizzazione Web. Per ulteriori informazioni, vedere [sincronizzazione Web per la replica di tipo Merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Se si seleziona **True** per **Usa sincronizzazione Web**:  
  
-   Immettere l'indirizzo completo del server IIS in **indirizzo server Web**.  
  
-   Fare clic su di **connessione al Server Web** di riga e quindi fare clic sul pulsante delle proprietà (**...**) per impostare o modificare l'account con cui il sottoscrittore si connette al server IIS.  
  
-   Modifica **timeout del server Web** se necessario. Il timeout rappresenta il tempo di attesa, in secondi, prima della scadenza di una richiesta di sincronizzazione Web.  
  
 Per ulteriori informazioni sulla configurazione, vedere [Configura sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Vedere anche  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  