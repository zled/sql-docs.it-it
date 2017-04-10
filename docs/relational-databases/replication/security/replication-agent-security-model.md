---
title: "Modello di sicurezza dell&#39;agente di replica | Microsoft Docs"
ms.custom: ""
ms.date: "10/07/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agente snapshot, sicurezza"
  - "agenti [replica di SQL Server], sicurezza"
  - "agente di distribuzione, sicurezza"
  - "account di accesso [replica di SQL Server], autorizzazioni per gli agenti"
  - "sicurezza [replica di SQL Server], modello di sicurezza dell'agente"
  - "agente di lettura log, sicurezza"
  - "agente di lettura coda, sicurezza"
  - "agente di merge, sicurezza"
  - "replica [SQL Server], agenti e profili"
ms.assetid: 6d09fc8d-843a-4a7a-9812-f093d99d8192
caps.latest.revision: 72
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 72
---
# Modello di sicurezza dell&#39;agente di replica
  Il modello di sicurezza dell'agente di replica consente un controllo accurato degli account utilizzati per l'esecuzione e le connessioni degli agenti. È possibile specificare un account diverso per ogni agente. Per ulteriori informazioni su come specificare gli account, vedere [gestire account di accesso e password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
> [!IMPORTANT]  
>  Quando un membro del ruolo predefinito del server **sysadmin** configura la replica, è possibile configurare gli agenti di replica in modo che rappresentino l'account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent. A tale scopo è necessario non specificare un account di accesso e una password per un agente di replica. Si tratta comunque di un approccio non consigliato. Ai fini della sicurezza, è consigliabile invece specificare un account per ogni agente dotato delle autorizzazioni minime descritte nella sezione "Autorizzazioni richieste per gli agenti" più avanti in questo argomento.  
  
 Gli agenti di replica, come tutti i file eseguibili, vengono eseguiti nel contesto di un account di Windows. Utilizzano tale account per le connessioni con sicurezza integrata di Windows. L'account con il quale viene eseguito l'agente dipende dalla modalità di avvio di quest'ultimo:  
  
-   Avvio dell'agente da un processo predefinito di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent: quando si utilizza un processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent per avviare un agente di replica, l'agente viene eseguito nel contesto di un account specificato al momento della configurazione della replica. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent e la replica, vedere la sezione "Sicurezza agente in SQL Server Agent" più avanti in questo argomento. Per informazioni sulle autorizzazioni che sono necessari per l'account con cui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene eseguito l'agente, vedere [configurare SQL Server Agent](../../../ssms/agent/configure-sql-server-agent.md).  
  
-   Avvio dell'agente da una riga dei comandi MS-DOS, direttamente o tramite uno script: l'agente viene eseguito nel contesto dell'account dell'utente che esegue l'agente dalla riga di comando.  
  
-   Avvio dell'agente da un'applicazione che utilizza oggetti RMO (Replication Management Objects) o un controllo ActiveX: l'agente viene eseguito nel contesto dell'applicazione che chiama gli oggetti RMO o il controllo ActiveX.  
  
    > [!NOTE]  
    >  I controlli ActiveX sono deprecati.  
  
 È consigliabile stabilire le connessioni nel contesto della sicurezza integrata di Windows. Per motivi di compatibilità con le versioni precedenti, è anche possibile utilizzare la sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per ulteriori informazioni sulle procedure consigliate, vedere [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## Autorizzazioni richieste per gli agenti  
 Gli account utilizzati per l'esecuzione e le connessioni degli agenti richiedono varie autorizzazioni. Tali autorizzazioni sono descritte nella tabella seguente. È consigliabile eseguire ogni agente con un account di Windows differente e assegnare all'account solo le autorizzazioni necessarie. Per informazioni sull'elenco di accesso alla pubblicazione (PAL), che è rilevante per un numero di agenti, vedere [proteggere il server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
> [!NOTE]  
>  Controllo account utente in alcuni sistemi operativi Windows può impedire l'accesso amministrativo alla condivisione snapshot. Le autorizzazioni per la condivisione snapshot devono pertanto essere concesse in modo esplicito agli account di Windows utilizzati dall'agente snapshot, dall'agente di distribuzione e dall'agente di merge. È necessario eseguire questa operazione anche se gli account di Windows sono membri del gruppo Administrators. Per ulteriori informazioni, vedere [sicurezza della cartella Snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
|Agente|Autorizzazioni|  
|-----------|-----------------|  
|agente snapshot|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Tale account deve:<br /><br /> -At minimo, essere un membro del **db_owner** ruolo predefinito del database nel database di distribuzione.<br /><br /> - Avere le autorizzazioni di lettura, scrittura e modifica per la condivisione snapshot.<br /><br /> <br /><br /> Si noti che l'account che viene usato per *connettersi* al server di pubblicazione deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di pubblicazione.|  
|Agente di lettura log|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Questo account deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di distribuzione.<br /><br /> L'account utilizzato per connettersi al server di pubblicazione deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di pubblicazione.<br /><br /> Quando si seleziona il **sync_type** Opzioni *solo supporto replica*, *inizializzazione con backup*, o *inizializzazione da lsn*, l'agente di lettura log è necessario eseguire dopo l'esecuzione di **sp_addsubscription**, in modo che gli script di configurazione vengono scritti nel database di distribuzione. L'agente di lettura log deve essere in esecuzione con un account membro del ruolo predefinito del server **sysadmin** . Quando il **sync_type** opzione è impostata su *automatica*, è necessaria alcuna azione di agente lettura log speciali.|  
|Agente di distribuzione per una sottoscrizione push|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Tale account deve:<br /><br /> -Almeno essere membro del **db_owner** ruolo predefinito del database nel database di distribuzione.<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.<br /><br /> - Avere le autorizzazioni di lettura per la directory di installazione del provider OLE DB per il Sottoscrittore se la sottoscrizione riguarda un Sottoscrittore non SQL Server.<br /><br /> -Quando la replica dei dati LOB, l'agente di distribuzione è necessario disporre delle autorizzazioni di scrittura per la replica **C:\Program Files\Microsoft SQL Server\XX\COMfolder** dove XX rappresenta l'ID istanza.<br /><br /> <br /><br /> Si noti che l'account che viene usato per *connettersi* al Sottoscrittore deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione o disporre di autorizzazioni equivalenti se la sottoscrizione è per un sottoscrittore non SQL Server.<br /><br /> Si noti inoltre che quando si utilizza `-subscriptionstreams >= 2` sull'agente di distribuzione è inoltre necessario concedere il **View Server State** l'autorizzazione per i sottoscrittori per rilevare i deadlock.|  
|Agente di distribuzione per una sottoscrizione pull|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al Sottoscrittore. Questo account deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione. L'account utilizzato per la connessione al server di distribuzione deve:<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.<br /><br /> -Quando la replica dei dati LOB, l'agente di distribuzione è necessario disporre delle autorizzazioni di scrittura per la replica **C:\Program Files\Microsoft SQL Server\XX\COMfolder** dove XX rappresenta l'ID istanza.<br /><br /> <br /><br /> Si noti che quando si utilizza `-subscriptionstreams >= 2` sull'agente di distribuzione è inoltre necessario concedere il **View Server State** l'autorizzazione per i sottoscrittori per rilevare i deadlock.|  
|Agente di merge per una sottoscrizione push|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di pubblicazione e al server di distribuzione. Tale account deve:<br /><br /> -Almeno essere membro del **db_owner** ruolo predefinito del database nel database di distribuzione.<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Essere un account di accesso associato a un utente nel database di pubblicazione.<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.<br /><br /> <br /><br /> Si noti che l'account utilizzato per *connettersi* al Sottoscrittore deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione.|  
|Agente di merge per una sottoscrizione pull|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al Sottoscrittore. Questo account deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione. L'account utilizzato per la connessione al server di pubblicazione e al server di distribuzione deve:<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Essere un account di accesso associato a un utente nel database di pubblicazione.<br /><br /> - Essere un account di accesso associato a un utente nel database di distribuzione. L'utente può essere l'utente **Guest** .<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.|  
|Agente di lettura coda|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Questo account deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di distribuzione.<br /><br /> L'account utilizzato per connettersi al server di pubblicazione deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di pubblicazione.<br /><br /> L'account utilizzato per la connessione al Sottoscrittore deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione.|  
  
## Sicurezza agente in SQL Server Agent  
 Quando si configura la replica mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], le procedure [!INCLUDE[tsql](../../../includes/tsql-md.md)] o gli oggetti RMO, per impostazione predefinita viene creato un processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent per ogni agente. Gli agenti vengono quindi eseguiti nel contesto di un passaggio del processo, indipendentemente dal fatto che l'esecuzione sia continua, in base a una pianificazione o su richiesta. È possibile visualizzare tali processi nella cartella **Processi** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Nella tabella seguente sono elencati i nomi dei processi.  
  
|Agente|Nome processo|  
|-----------|--------------|  
|agente snapshot|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< numero intero>**|  
|Agente snapshot per una partizione di una pubblicazione di tipo merge|**Dyn_ \< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< GUID>**|  
|Agente di lettura log|**\< server di pubblicazione>-\< PublicationDatabase>-\< numero intero>**|  
|Agente di merge per le sottoscrizioni pull|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< SubscriptionDatabase>-\< numero intero>**|  
|Agente di merge per le sottoscrizioni push|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>**|  
|Agente di distribuzione per le sottoscrizioni push|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>***|  
|Agente di distribuzione per le sottoscrizioni pull|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< SubscriptionDatabase>-\< GUID>***\*|  
|Agente di distribuzione per le sottoscrizioni push di Sottoscrittori non SQL Server|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>**|  
|Agente di lettura coda|**[\< distributor>]. \< numero intero>**|  
  
 \*Per le sottoscrizioni push a pubblicazioni Oracle, è il nome del processo **\< server di pubblicazione>-\< Publisher**> invece di **\< server di pubblicazione>-\< PublicationDatabase>**.  
  
 \*\*Per le sottoscrizioni pull a pubblicazioni Oracle, è il nome del processo **\< server di pubblicazione>-\< DistributionDatabase**> invece di **\< server di pubblicazione>-\< PublicationDatabase>**.  
  
 Durante la configurazione della replica si specificano gli account utilizzati per l'esecuzione degli agenti. Tutti i passaggi del processo, tuttavia, vengono eseguiti nel contesto di sicurezza di un *proxy*e pertanto la replica esegue internamente i mapping seguenti per gli account dell'agente specificati:  
  
-   Viene innanzitutto eseguito il mapping tra l'account e una credenziale utilizzando l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] [di](../../../t-sql/statements/create-credential-transact-sql.md) . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent utilizzano le credenziali per archiviare le informazioni sugli account utente di Windows.  
  
-   Il [sp_add_proxy](../../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md) stored procedure viene chiamata e la credenziale viene utilizzata per creare un proxy...  
  
> [!NOTE]  
>  Queste informazioni vengono fornite allo scopo di illustrare i processi richiesti per l'esecuzione degli agenti nel contesto di sicurezza appropriato. Non è in genere necessario interagire direttamente con le credenziali o i proxy creati.  
  
## Vedere anche  
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Sicurezza della cartella snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  