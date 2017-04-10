---
title: "Sicurezza del server di pubblicazione | Microsoft Docs"
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
  - "logins [SQL Server replication], publication access list"
  - "publications [SQL Server replication], publication access lists"
  - "publication access list (PAL)"
  - "elenco di accesso alla pubblicazione"
  - "server di pubblicazione [replica di SQL Server], sicurezza"
  - "pubblicazioni [replica di SQL Server], sicurezza"
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# Sicurezza del server di pubblicazione
  Gli agenti di replica seguenti si connettono al server di pubblicazione:  
  
-   Agente di lettura log  
  
-   agente snapshot  
  
-   Agente di lettura coda  
  
-   Agente di merge  
  
 È importante specificare un account di accesso appropriato per questi agenti, attenendosi al principio di concedere i diritti minimi necessari e proteggere l'archiviazione di tutte le password. Per informazioni sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Oltre a gestire gli account di accesso e le password in modo appropriato, è importante comprendere il ruolo dell'elenco di accesso alla pubblicazione. Questo elenco viene utilizzato per consentire agli account di accedere ai dati di pubblicazione, limitando nel contempo l'accesso ad hoc al database nel server di pubblicazione.  
  
## Elenco di accesso alla pubblicazione  
 L'elenco di accesso alla pubblicazione costituisce il principale sistema di protezione delle pubblicazioni nel server di pubblicazione. che funziona in maniera analoga a un elenco di controllo di accesso [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Quando si crea una pubblicazione, la replica crea un elenco di accesso alla pubblicazione per la pubblicazione creata. Tale elenco può essere configurato per contenere l'elenco degli account di accesso e dei gruppi autorizzati ad accedere alla pubblicazione. Quando un agente si connette al server di pubblicazione o al server di distribuzione e richiede l'accesso a una pubblicazione, i dati di autenticazione dell'elenco di accesso alla pubblicazione vengono confrontati con l'account di accesso al server di pubblicazione specificato dall'agente. Ciò garantisce un maggior livello di sicurezza del server di pubblicazione, impedendo che gli account di accesso del server di pubblicazione e del server di distribuzione vengano utilizzati da uno strumento client per apportare modifiche direttamente nel server di pubblicazione.  
  
> [!NOTE]  
>  La replica crea un ruolo sul server di pubblicazione per ogni pubblicazione, in modo da applicare l'appartenenza all'elenco di accesso alla pubblicazione. Il ruolo dispone di un nome nel formato **msmerge _***\< PublicationID>* per la replica di tipo merge e **msreplpal _***\< PublicationDatabaseID>***_***\< PublicationID>* per la replica transazionale e snapshot.  
  
 Per impostazione predefinita, gli account di accesso seguenti sono inclusi nell'elenco di accesso: i membri del **sysadmin** ruolo predefinito del server al momento della creazione della pubblicazione e l'account di accesso utilizzato per creare la pubblicazione. Per impostazione predefinita, tutti gli accessi che sono membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database nel database di pubblicazione possono sottoscrivere una pubblicazione senza essere aggiunti esplicitamente all'elenco di accesso.  
  
 Quando si utilizza l'elenco di accesso alla pubblicazione, tenere presenti le indicazioni seguenti:  
  
-   Prima di aggiungere l'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] all'elenco di accesso alla pubblicazione, è necessario associarlo a un utente di database nel database di pubblicazione.  
  
-   Attenersi al principio dei privilegi minimi, concedendo agli account nell'elenco di accesso alla pubblicazione solo le autorizzazioni necessarie per eseguire le attività di replica. Non aggiungere gli account di accesso a ruoli predefiniti del database o del server che non sono necessari per la replica. Per ulteriori informazioni sulle autorizzazioni necessarie, vedere [il modello di protezione agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md) e [procedure ottimali di protezione della replica](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
-   Se si usano un server di distribuzione remoto, gli account nell'elenco di accesso alla pubblicazione devono essere disponibili sia nel server di pubblicazione che nel server di distribuzione. L'account deve essere un account di dominio o un account locale definito in entrambi i server. Le password associate a entrambi gli account di accesso devono essere identiche.  
  
-   Se l'elenco di accesso alla pubblicazione contiene account di Windows e il dominio utilizza Active Directory, l'account con cui viene eseguito [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deve disporre dell'autorizzazione di lettura da Active Directory. In caso di problemi con gli account di Windows, assicurarsi che l'account utilizzato per l'esecuzione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] disponga di autorizzazioni sufficienti. Per ulteriori informazioni, vedere la documentazione di Windows.  
  
 Per gestire l'elenco di accesso, vedere [gestire gli account di accesso nell'elenco di accesso alla pubblicazione](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md).  
  
## agente snapshot  
 Per ogni pubblicazione esiste un solo agente snapshot. Per altre informazioni, vedere [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
## Recapito snapshot FTP  
 Se si specifica che gli snapshot devono essere resi disponibili tramite una condivisione FTP anziché una condivisione UNC, quando si configura l'accesso FTP è necessario specificare un account di accesso e una password. Per ulteriori informazioni, vedere [recapitare Snapshot tramite FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
## Agente di lettura log  
 Per ogni database pubblicato per la replica transazionale, esiste un solo agente di lettura log. Per altre informazioni, vedere [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
## Agente di lettura coda  
 Per tutti i server di pubblicazione e le pubblicazioni (che consentono le sottoscrizioni ad aggiornamento in coda) associate a uno specifico database di distribuzione esiste un solo agente di lettura coda. Per ulteriori informazioni, vedere [abilitare sottoscrizioni ad aggiornamento per le pubblicazioni transazionali](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md).  
  
## Vedere anche  
 [Abilitare connessioni crittografate al motore di Database & #40; Gestione configurazione SQL Server & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  