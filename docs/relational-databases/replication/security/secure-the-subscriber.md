---
title: "Sicurezza del Sottoscrittore | Microsoft Docs"
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
  - "sottoscrizioni [replica di SQL Server], sicurezza"
  - "Sottoscrittori [replica di SQL Server], sicurezza"
  - "sicurezza [replica di SQL Server], Sottoscrittori"
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Sicurezza del Sottoscrittore
  Gli agenti di merge e di distribuzione si connettono al Sottoscrittore. Queste connessioni possono essere stabilite nel contesto di un account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o di Windows. È importante specificare un account di accesso appropriato per questi agenti, attenendosi al principio di concedere i diritti minimi necessari e proteggere l'archiviazione di tutte le password. Per informazioni sulle autorizzazioni necessarie per ogni agente, vedere [il modello di protezione agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Agente di distribuzione  
 È possibile utilizzare un agente di distribuzione per sottoscrizione, ovvero un agente indipendente in base all'impostazione predefinita per le pubblicazioni create nella Creazione guidata nuova pubblicazione, oppure un agente di distribuzione per coppia di database di pubblicazione e database di sottoscrizione, ovvero un agente condiviso. T  
  
 Per specificare informazioni di connessione per le sottoscrizioni push, vedere [creare una sottoscrizione Push](../../../relational-databases/replication/create-a-push-subscription.md).  
  
 Per specificare informazioni di connessione per le sottoscrizioni pull, vedere [creare una sottoscrizione Pull](../../../relational-databases/replication/create-a-pull-subscription.md)  
  
## Agente di merge  
 Per ogni sottoscrizione di tipo merge è disponibile un agente di merge specifico che si connette sia al server di pubblicazione che al Sottoscrittore, aggiornandoli entrambi.  
  
 Per specificare informazioni di connessione per le sottoscrizioni push, vedere [creare una sottoscrizione Push](../../../relational-databases/replication/create-a-push-subscription.md).  
  
 Per specificare informazioni di connessione per le sottoscrizioni pull, vedere [creare una sottoscrizione Pull](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
## Sottoscrizioni ad aggiornamento immediato  
 Quando si configura una sottoscrizione ad aggiornamento immediato, si specifica un account nel Sottoscrittore con cui vengono stabilite le connessioni al server di pubblicazione. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Sono disponibili tre opzioni per il tipo di connessione:  
  
-   Server collegato creato dalla replica. La connessione viene stabilita con le credenziali specificate in fase di configurazione.  
  
-   Un server collegato creato dalla replica. La connessione viene eseguita con le credenziali dell'utente che apporta la modifica presso il Sottoscrittore.  
  
-   Un server collegato o remoto già definito.  
  
> [!IMPORTANT]  
>  Per specificare le informazioni di connessione, utilizzare la stored procedure [sp_link_publication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). È inoltre possibile utilizzare il **account di accesso per sottoscrizioni aggiornabili** pagina della creazione guidata sottoscrizione, che chiama **sp_link_publication**. In alcune condizioni, questa stored procedure può avere esito negativo se nel Sottoscrittore è in esecuzione [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) o versioni successive e nel server di pubblicazione è in esecuzione una versione precedente. Se la stored procedure ha esito negativo in questo scenario, aggiornare il server di pubblicazione a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 o versioni successive.  
  
 Per ulteriori informazioni, vedere [creare una sottoscrizione aggiornabile di una pubblicazione transazionale](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) e [visualizzare e modificare le impostazioni di sicurezza](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
> [!IMPORTANT]  
>  È consigliabile concedere all'account specificato per la connessione solo le autorizzazioni necessarie per l'inserimento, l'aggiornamento e l'eliminazione dei dati delle viste create dalla replica nel database di pubblicazione. Concedere autorizzazioni per le viste nel database di pubblicazione che sono denominate nel formato **syncobj _***\< HexadecimalNumber>* all'account configurato presso ogni sottoscrittore.  
  
## Sottoscrizioni ad aggiornamento in coda  
 Quando si configurano sottoscrizioni ad aggiornamento in coda, è necessario tenere in considerazione due aspetti relativi alla sicurezza.  
  
-   Esiste un solo agente di lettura coda per ogni server di distribuzione. Per ogni server di distribuzione è consigliabile configurare al massimo una pubblicazione abilitata per le sottoscrizioni ad aggiornamento in coda.  
  
-   L'agente di lettura coda stabilisce connessioni al server di distribuzione, al server di pubblicazione e a ogni Sottoscrittore:  
  
    -   L'account con cui l'agente viene eseguito e stabilisce connessioni al server di distribuzione viene specificato al momento della creazione dell'agente. Se si utilizza la Creazione guidata nuova pubblicazione, l'agente viene creato quando si crea una pubblicazione abilitata per le sottoscrizioni aggiornabili.  
  
    -   L'account con cui l'agente stabilisce connessioni al server di pubblicazione viene specificato quando si configura la distribuzione per un server di pubblicazione. Specificare l'account di Windows con cui l'agente viene eseguito oppure un account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    -   L'account con cui l'agente stabilisce connessioni al Sottoscrittore viene specificato quando si crea la sottoscrizione.  
  
    > [!IMPORTANT]  
    >  Utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per le connessioni ai Sottoscrittori e specificare un diverso account per la connessione a ogni Sottoscrittore. Se si utilizza una sottoscrizione pull, la connessione viene sempre impostata dalla replica in modo da utilizzare l'autenticazione di Windows. Per le sottoscrizioni pull, la replica non può infatti accedere ai metadati nel Sottoscrittore necessari per utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. In questo caso, modificare la connessione in modo da utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dopo la configurazione della sottoscrizione.  
  
     Per ulteriori informazioni, vedere Procedura: creare una sottoscrizione aggiornabile di una pubblicazione transazionale (SQL Server Management Studio) e [visualizzare e modificare le impostazioni di sicurezza](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Vedere anche  
 [Abilitare connessioni crittografate al motore di Database & #40; Gestione configurazione SQL Server & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  