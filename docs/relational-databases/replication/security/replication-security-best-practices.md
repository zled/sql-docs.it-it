---
title: "Procedure consigliate per la sicurezza della replica | Microsoft Docs"
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
  - "sicurezza [replica di SQL Server], procedure consigliate"
  - "sicurezza [replica di SQL Server], tra domini"
  - "autenticazione [replica di SQL Server]"
  - "Internet [replica di SQL Server], sicurezza"
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Procedure consigliate per la sicurezza della replica
  La replica implica lo spostamento di dati in ambienti distribuiti che includono reti Intranet in un singolo dominio, applicazioni che accedono a dati tra domini non attendibili e Internet. È importante individuare l'approccio migliore per la protezione delle connessioni di replica in queste diverse circostanze.  
  
 Le informazioni seguenti sono applicabili alla replica in qualsiasi ambiente:  
  
-   Crittografare le connessioni tra computer in una topologia di replica utilizzano un metodo standard, ad esempio le reti private virtuali (VPN, Virtual Private Network), la crittografia SSL (Secure Sockets Layer) o lo standard IPSec (Internet Protocol Security). Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md). Per informazioni sull'utilizzo di reti VPN e del protocollo SSL per la replica di dati su Internet, vedere [Securing Replication Over the Internet](../../../relational-databases/replication/security/securing-replication-over-the-internet.md).  
  
     Se si utilizza SSL per proteggere le connessioni tra computer in una topologia di replica, specificare un valore di **1** o **2** per il **- EncryptionLevel** parametro di ogni agente di replica (il valore **2** è consigliato). Un valore pari a **1** indica che è utilizzata la crittografia, ma l'agente non verifica che il certificato SSL del server sia firmato da un'autorità emittente attendibile; un valore pari a **2** indica che il certificato viene verificato. I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
    -   [Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Visualizzare e modificare i parametri di prompt dei comandi dell'agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concetti di base relativi ai file eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
-   Eseguire ogni agente di replica con un diverso account di Windows e utilizzare l'autenticazione di Windows per tutte le connessioni agli agenti di replica. Per ulteriori informazioni sull'impostazione degli account, vedere [gestire account di accesso e password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Concedere agli agenti solo le autorizzazioni necessarie. Per ulteriori informazioni, vedere la sezione "Autorizzazioni necessarie da agenti" di [modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Verificare che tutti gli account degli agenti di merge e di distribuzione siano inclusi nell'elenco di accesso alla pubblicazione. Per ulteriori informazioni, vedere [proteggere il server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
-   Attenersi al principio dei privilegi minimi, concedendo agli account nell'elenco di accesso alla pubblicazione solo le autorizzazioni necessarie per eseguire le attività di replica. Non aggiungere gli account di accesso ad alcun ruolo predefinito del server che non sia necessario per la replica.  
  
-   Configurare la condivisione snapshot in modo da consentire l'accesso in lettura a tutti gli agenti di merge e di distribuzione. Se vengono utilizzati snapshot per pubblicazioni con filtri con parametri, verificare che ogni cartella sia configurata per l'accesso in lettura solo per gli account degli agenti di merge appropriati.  
  
-   Configurare la condivisione snapshot per consentire l'accesso in scrittura all'agente snapshot.  
  
-   Se si utilizzano sottoscrizioni pull, inserire la cartella snapshot in una condivisione di rete anziché in un percorso locale.  
  
 Se nella topologia di replica sono inclusi computer di domini diversi o di domini che non hanno relazioni di trust, è possibile utilizzare l'autenticazione di Windows o l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per le connessioni eseguite dagli agenti. Per ulteriori informazioni sui domini, vedere la documentazione di Windows. È consigliabile, dal punto di vista della sicurezza, utilizzare l'autenticazione di Windows.  
  
-   Per utilizzare l'autenticazione di Windows:  
  
    -   Aggiungere un account di Windows locale (non un account di dominio) per ogni agente nei nodi appropriati, utilizzando lo stesso nome e password per ogni nodo. Ad esempio, l'agente di distribuzione per una sottoscrizione push viene eseguito nel server di distribuzione e stabilisce connessioni al server di distribuzione e al Sottoscrittore. L'account di Windows per l'agente di distribuzione deve essere aggiunto al server di distribuzione e al Sottoscrittore.  
  
    -   Verificare che un determinato agente, ad esempio l'agente di distribuzione per una sottoscrizione, venga eseguito con lo stesso account in ogni computer.  
  
-   Per utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
    -   Aggiungere un account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ogni agente nei nodi appropriati, utilizzando lo stesso nome e password per ogni nodo. Ad esempio, l'agente di distribuzione per una sottoscrizione push viene eseguito nel server di distribuzione e stabilisce connessioni al server di distribuzione e al Sottoscrittore. L'account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per l'agente di distribuzione deve essere aggiunto al server di distribuzione e al Sottoscrittore.  
  
    -   Verificare che un determinato agente, ad esempio l'agente di distribuzione per una sottoscrizione, stabilisca connessioni utilizzando lo stesso account in ogni computer.  
  
    -   Nei casi in cui è necessaria l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'accesso alle condivisioni snapshot UNC spesso non è disponibile, ad esempio, può essere bloccato da un firewall. In tal caso, è possibile trasferire lo snapshot ai Sottoscrittori tramite FTP. Per ulteriori informazioni, vedere [trasferire gli snapshot tramite FTP](../../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
## Vedere anche  
 [Abilitare connessioni crittografate al motore di Database & #40; Gestione configurazione SQL Server & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [Replica su Internet](../../../relational-databases/replication/replication-over-the-internet.md)   
 [Sicurezza del Sottoscrittore](../../../relational-databases/replication/security/secure-the-subscriber.md)   
 [Sicurezza del database di distribuzione](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [Sicurezza del server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  