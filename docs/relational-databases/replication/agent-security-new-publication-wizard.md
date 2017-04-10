---
title: "Sicurezza agente (Creazione guidata nuova pubblicazione) | Microsoft Docs"
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
  - "sql13.rep.agentsecurity.articles.f1"
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Sicurezza agente (Creazione guidata nuova pubblicazione)
  Il **agente protezione** pagina consente di specificare gli account con cui eseguire gli agenti seguenti e stabilire connessioni ai computer in una topologia di replica:  
  
-   Agente snapshot per tutte le pubblicazioni.  
  
-   Agente di lettura log per tutte le pubblicazioni transazionali.  
  
-   Agente di lettura coda per le pubblicazioni transazionali con sottoscrizioni aggiornabili. Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processo dell'agente per questo agente viene creato se è stato specificato **pubblicazione transazionale con sottoscrizioni aggiornabili** sul **tipo di pubblicazione** pagina, indipendentemente dal tipo di sottoscrizioni aggiornabili utilizzate. Per ulteriori informazioni sulle sottoscrizioni aggiornabili, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 Per informazioni sulle autorizzazioni necessarie per gli agenti e le procedure consigliate per la sicurezza della replica, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md) e [procedure ottimali di protezione della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## Opzioni  
 **agente snapshot**  
 Visualizzato per tutte le pubblicazioni. Fare clic su **le impostazioni di sicurezza** per specificare impostazioni di protezione di **sicurezza agente Snapshot** la finestra di dialogo.  
  
 Fare clic su **Guida** sul **sicurezza agente Snapshot** la finestra di dialogo per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dall'agente Snapshot.  
  
 **Agente di lettura log**  
 Visualizzato per tutte le pubblicazioni transazionali. Fare clic su **le impostazioni di sicurezza** per specificare impostazioni di protezione di **sicurezza agente di lettura Log** la finestra di dialogo.  
  
 Fare clic su **Guida** sul **sicurezza agente di lettura Log** la finestra di dialogo per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dall'agente di lettura Log.  
  
> [!NOTE]  
>  esiste un agente di lettura log per ogni database pubblicato tramite la replica transazionale. Se esiste già una replica transazionale nel database, le impostazioni di sicurezza sono di sola lettura. È possibile modificare le impostazioni di **Proprietà pubblicazione** la finestra di dialogo, ma le modifiche influiscono su tutte le pubblicazioni transazionali nel database.  
  
 **Agente di lettura coda**  
 Visualizzato per le pubblicazioni transazionali con sottoscrizioni aggiornabili. Fare clic su **le impostazioni di sicurezza** per specificare impostazioni di protezione di **sicurezza agente di lettura coda** la finestra di dialogo. Un processo di agente di lettura coda viene creato al termine della procedura guidata indipendentemente dalla creazione di sottoscrizioni ad aggiornamento in coda. Se non si prevede di creare sottoscrizioni ad aggiornamento in coda, è possibile disabilitare il processo. Fare il processo (il formato: *[\< server di pubblicazione>]. \< integer>*.) nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente **processi** cartella e quindi fare clic su **disabilitare**.  
  
 Fare clic su **Guida** sul **sicurezza agente di lettura coda** la finestra di dialogo per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dall'agente di lettura coda.  
  
> [!NOTE]  
>  Esiste un unico agente di lettura coda per ogni database di distribuzione e tutti i server di pubblicazione che utilizzano il database. Se esiste già una pubblicazione transazionale che consente sottoscrizioni con aggiornamento in coda in uno qualsiasi dei server di pubblicazione che utilizzano un database di distribuzione specifico, le impostazioni di sicurezza sono di sola lettura. È possibile modificare l'account con cui viene eseguito l'agente di lettura coda e stabilisce le connessioni nel **proprietà server di distribuzione** la finestra di dialogo, ma le modifiche avranno effetto su tutti i server di pubblicazione che utilizzano il database di distribuzione.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Creazione di una sottoscrizione aggiornabile di una pubblicazione transazionale](https://msdn.microsoft.com/library/mt740635.aspx)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  