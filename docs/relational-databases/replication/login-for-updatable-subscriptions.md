---
title: "Account di accesso per sottoscrizioni aggiornabili | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.updatablesubscriptionslogin.f1"
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Account di accesso per sottoscrizioni aggiornabili
  Per un aggiornamento immediato, se si seleziona **replicare** sul **sottoscrizioni aggiornabili** pagina della procedura guidata, è necessario specificare un account con il server di sottoscrizione in cui vengono eseguite le connessioni al server di pubblicazione. 
  
 Le connessioni vengono utilizzate dai trigger attivati nel sottoscrittore e propagare le modifiche al server di pubblicazione. Questo account è necessario anche se si seleziona **Accoda le modifiche ed eseguire il commit quando possibile** sul **sottoscrizioni aggiornabili** pagina. Creazione guidata nuova sottoscrizione per impostazione predefinita consente di configurare l'aggiornamento in coda con la possibilità di passare all'aggiornamento immediato se necessario.  
  
> **IMPORTANTE** L'account specificato per la connessione solo deve essere concessa l'autorizzazione per inserire, aggiornare ed eliminare dati nelle viste che la replica viene creata nel database di pubblicazione. È opportuno non assegnare autorizzazioni aggiuntive. Concedere autorizzazioni per le viste nel database di pubblicazione denominato nel formato **syncobj _***\< HexadecimalNumber>* per l'account configurato presso ogni sottoscrittore.  
  
 Sono disponibili tre opzioni per il tipo di connessione:  
  
-   Un server collegato o remoto già definito.  
  
-   Un server collegato creato dalla replica. La connessione viene eseguita con le credenziali specificate in questa procedura guidata.  
  
-   Un server collegato creato dalla replica. La connessione viene eseguita con le credenziali dell'utente che apporta la modifica presso il Sottoscrittore.  
  
 In questa procedura guidata è possibile specificare le prime due opzioni. L'ultima opzione può essere specificato solo tramite [sp_link_publication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md); specificare un valore di **1** per il parametro **@security_mode**.  
  
## Opzioni  
 **Crea un server collegato che stabilisce la connessione utilizzando l'autenticazione di SQL Server**  
 La replica crea un server collegato utilizzando le credenziali specificate nel **accesso** e **Password** campi.  
  
 **Account di accesso**  
 Immettere un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso che disponga solo delle autorizzazioni descritte in questo argomento.  
  
 **Password**  
 Immettere una password complessa per l'account di accesso specificato in **accesso**.  
    
 **Usa un server collegato o remoto già definito**  
 Per questa opzione è necessario un server collegato o remoto già definito. Per ulteriori informazioni, vedere [motore di Database di server collegati &#40; &#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) e [server remoti](../../database-engine/configure-windows/remote-servers.md). Accertarsi che l'account di accesso utilizzato per il server collegato o remoto disponga di una password complessa e delle sole autorizzazioni descritte in questo argomento.  
  
## Vedere anche  
 [Creazione di una sottoscrizione aggiornabile di una pubblicazione transazionale](https://msdn.microsoft.com/library/ms152769.aspx)   
 [Visualizzazione e modifica delle impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  