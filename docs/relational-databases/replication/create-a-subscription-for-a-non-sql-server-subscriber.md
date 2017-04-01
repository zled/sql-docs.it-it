---
title: "Creazione di una sottoscrizione per un Sottoscrittore non SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subscriptions [SQL Server replication], non-SQL Server Subscribers"
  - "Subscribers [SQL Server replication], non-SQL Server Subscribers"
  - "Sottoscrittori non SQL Server, sottoscrizioni"
ms.assetid: 5020ee68-b988-4d57-8066-67d183e61237
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Creazione di una sottoscrizione per un Sottoscrittore non SQL Server
  In questo argomento viene descritto come creare una sottoscrizione per un Sottoscrittore non SQL Server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. La replica transazionale e la replica snapshot supportano la pubblicazione di dati su Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni su piattaforme di sottoscrittori supportate, vedere [sottoscrittori Non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Contenuto dell'argomento**  
  
-   **Per creare una sottoscrizione per un Sottoscrittore non SQL Server, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Per creare una sottoscrizione per un Sottoscrittore non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
1.  Installare e configurare il software client e il provider o i provider OLE DB appropriati sul database di distribuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) e [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  Creare una pubblicazione utilizzando la Creazione guidata nuova pubblicazione. Per ulteriori informazioni sulla creazione di pubblicazioni, vedere [creare una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md) e [creare una pubblicazione da un Database Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md). Specificare le opzioni seguenti nella Creazione guidata nuova pubblicazione.  
  
    -   Nella pagina **Tipo di pubblicazione** selezionare **Pubblicazione snapshot** o **Pubblicazione transazionale**.  
  
    -   Nella pagina **Agente snapshot** , deselezionare **Crea snapshot immediatamente**.  
  
         Lo snapshot viene creato dopo che la pubblicazione è stata attivata per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in modo da garantire che l'agente snapshot generi uno snapshot e script di inizializzazione che siano adatti ai Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Abilitare per la pubblicazione non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori che utilizzano il **Proprietà pubblicazione - \< PublicationName>** la finestra di dialogo. Per ulteriori informazioni su questo passaggio, vedere [Publication Properties, Subscription Options](../../relational-databases/replication/publication-properties-subscription-options.md) .  
  
4.  Creare una sottoscrizione utilizzando la Creazione guidata nuova sottoscrizione. In questo argomento sono presenti ulteriori informazioni su questo passaggio.  
  
5.  (Facoltativo) Modifica il **pre_creation_cmd** proprietà per mantenere le tabelle nel sottoscrittore dell'articolo. In questo argomento sono presenti ulteriori informazioni su questo passaggio.  
  
6.  Generare uno snapshot per la pubblicazione. In questo argomento sono presenti ulteriori informazioni su questo passaggio.  
  
7.  Sincronizzare la sottoscrizione. Per altre informazioni, vedere [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Per abilitare una pubblicazione per Sottoscrittori non SQL Server  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare doppio clic su pubblicazione e quindi fare clic su **proprietà**.  
  
4.  Nel **Opzioni di sottoscrizione** pagina, selezionare un valore di **True** per l'opzione **Consenti sottoscrittori non SQL Server**. Se si seleziona questa opzione vengono modificate alcune proprietà in modo che la pubblicazione sia compatibile con i Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Selezionando **True** Imposta il valore di **pre_creation_cmd** proprietà su 'drop' dell'articolo. In base a tale impostazione, se una tabella nel Sottoscrittore corrisponde al nome della tabella nell'articolo, tale tabella verrà eliminata dalla replica. Se si dispone di tabelle esistenti nel server di sottoscrizione che si desidera mantenere, utilizzare il [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) stored procedure per ogni articolo e specificare il valore 'none' per **pre_creation_cmd**: `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Verrà richiesto di creare un nuovo snapshot per la pubblicazione. Se non si desidera crearlo in questo momento, utilizzare i passaggi descritti nella "Procedura" seguente in un momento successivo.  
  
#### Per creare una sottoscrizione per un Sottoscrittore non SQL Server  
  
1.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
2.  Fare doppio clic su pubblicazione appropriata e quindi fare clic su **nuove sottoscrizioni**.  
  
3.  Verificare che l'opzione **Esegui tutti gli agenti nel server di distribuzione** nella pagina **Posizione in cui eseguire l'agente di distribuzione** sia selezionata. I Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supportano l'esecuzione di agenti nel Sottoscrittore.  
  
4.  Nel **sottoscrittori** pagina, fare clic su **Aggiungi Sottoscrittore** e quindi fare clic su **Aggiungi Sottoscrittore Non SQL Server**.  
  
5.  Nel **Aggiungi Sottoscrittore Non SQL Server** finestra di dialogo, selezionare il tipo di sottoscrittore.  
  
6.  Inserire un valore nella casella **Nome origine dati**:  
  
    -   Per Oracle, si tratta del nome TNS che è stato configurato.  
  
    -   Per IBM, può essere qualsiasi nome. In genere viene utilizzato per specificare l'indirizzo di rete del Sottoscrittore.  
  
     Il nome origine dati immesso in questo passaggio e le credenziali specificate nel passaggio 9 non vengono convalidati da questa procedura guidata. Non vengono utilizzati dalla replica fino all'esecuzione dell'agente di distribuzione per la sottoscrizione. Assicurarsi che tutti i valori sono stati testati tramite la connessione al sottoscrittore utilizzando uno strumento client (ad esempio **sqlplus** per Oracle). Per ulteriori informazioni, vedere [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) e [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Nel **sottoscrittori** ora viene visualizzata la pagina della procedura guidata, il server di sottoscrizione nel **sottoscrittore** colonna con una proprietà di sola lettura **(destinazione predefinita)** nel **Database di sottoscrizione** colonna:  
  
    -   Per Oracle, un server include al massimo un database e pertanto non è necessario specificare il database.  
  
    -   Per IBM DB2, il database viene specificato nella proprietà **Catalogo iniziale** della stringa di connessione DB2, che può essere inserita nel campo **Opzioni di connessione aggiuntive** descritto più avanti in questo processo.  
  
8.  Nel **sicurezza agente di distribuzione** fare clic sul pulsante delle proprietà (**...**) accanto al sottoscrittore per accedere al **sicurezza agente di distribuzione** la finestra di dialogo.  
  
9. Nella finestra di dialogo **Sicurezza agente di distribuzione** :  
  
    -   Nei campi **Account processo**, **Password**e **Conferma password** , inserire l'account e la password di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con cui deve essere eseguito l'agente di distribuzione e stabilire le connessioni locali al server di distribuzione.  
  
         L'account richiede le autorizzazioni minime: membro del **db_owner** fisso ruolo del database nel database di distribuzione, membro dell'elenco di accesso (PAL) alla pubblicazione, le autorizzazioni di lettura per la condivisione snapshot; e autorizzazioni di lettura per la directory di installazione del provider OLE DB. Per ulteriori informazioni sull'elenco di accesso, vedere [proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md).  
  
    -   Nei campi **Nome account di accesso**, **Password**e **Conferma password**di **Connessione al Sottoscrittore** , inserire il nome account di accesso e la password da utilizzare per la connessione al Sottoscrittore. Questo nome account di accesso dovrebbe essere già configurato ed avere autorizzazioni sufficienti per la creazione di oggetti nel database di sottoscrizione.  
  
    -   Nel **ulteriori opzioni di connessione** specificare eventuali opzioni di connessione per il sottoscrittore sotto forma di stringa di connessione (Oracle non richiede opzioni aggiuntive). Le opzioni devono essere separate dal punto e virgola. L'esempio seguente illustra una stringa di connessione DB2 (le interruzioni di riga sono inserite per agevolare la lettura):  
  
        ```  
        Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
        PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
        Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
        Persist Security Info=False;Connection Pooling=True;  
        ```  
  
         La maggior parte delle opzioni nella stringa è specifica per il server DB2 configurato, ma è necessario che l'opzione **Process Binary as Character** sia sempre impostata su **False**. È necessario specificare un valore per l'opzione **Initial Catalog** per identificare il database di sottoscrizione.  
  
10. Nel **pianificazione della sincronizzazione** pagina, selezionare una pianificazione per l'agente di distribuzione dal **pianificazione dell'agente** menu (la pianificazione è in genere **vengono eseguiti continuamente**).  
  
11. Nella pagina **Inizializzazione sottoscrizioni** , specificare se la sottoscrizione deve essere inizializzata e quando:  
  
    -   Deselezionare **Inizializzazione di** solo se nel database di sottoscrizione sono stati creati tutti gli oggetti e sono stati aggiunti tutti i dati necessari.  
  
    -   Selezionare **immediatamente** dall'elenco a discesa nel **quando** colonna per trasferire l'agente di distribuzione file di snapshot al sottoscrittore dopo aver completata questa procedura guidata. Selezionare **Alla prima sincronizzazione** per fare in modo che l'agente trasferisca i file alla successiva esecuzione pianificata dell'agente.  
  
12. Nella pagina **Azioni procedura guidata** , se si desidera, creare lo script della sottoscrizione. Per altre informazioni, vedere [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
#### Per mantenere le tabelle nel Sottoscrittore  
  
-   Per impostazione predefinita, attiva una pubblicazione per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori imposta il valore di **pre_creation_cmd** proprietà su 'drop' dell'articolo. In base a tale impostazione, se una tabella nel Sottoscrittore corrisponde al nome della tabella nell'articolo, tale tabella verrà eliminata dalla replica. Se si dispone di tabelle esistenti nel server di sottoscrizione che si desidera mantenere, utilizzare il [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) stored procedure per ogni articolo e specificare il valore 'none' per **pre_creation_cmd**. `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
#### Per generare uno snapshot per la pubblicazione.  
  
1.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
2.  Fare doppio clic su pubblicazione e quindi fare clic su **Visualizza stato agente Snapshot**.  
  
3.  Nel **Visualizza stato agente Snapshot - \< pubblicazione>** la finestra di dialogo, fare clic su **avviare**.  
  
 Al termine della generazione dello snapshot da parte dell'agente, viene visualizzato un messaggio come ""[100%] Generato uno snapshot di 17 articoli."  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile creare sottoscrizioni push a Sottoscrittori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a livello di programmazione tramite le stored procedure di replica.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
#### Per creare una sottoscrizione push per una pubblicazione transazionale o snapshot in un Sottoscrittore non SQL Server  
  
1.  Installare il provider OLE DB più recente per il Sottoscrittore non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia nel server di pubblicazione che nel server di distribuzione. Per i requisiti di replica per un provider OLE DB, vedere [sottoscrittori Non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), [sottoscrittori Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md), [nei Sottoscrittori DB2 IBM](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  Nel server di pubblicazione nel database di pubblicazione, verificare che la pubblicazione supporta non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori eseguendo [sp_helppublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Se il valore di **enabled_for_het_sub** è 1, non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori sono supportati.  
  
    -   Se il valore di **enabled_for_het_sub** è 0, eseguire [sp_changepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando **enabled_for_het_sub** per **@property** e **true** per **@value**.  
  
        > [!NOTE]  
        >  Prima di modificare **enabled_for_het_sub** a **true**, è necessario eliminare le sottoscrizioni esistenti per la pubblicazione. Non è possibile impostare **enabled_for_het_sub** a **true** quando la pubblicazione supporta anche sottoscrizioni aggiornabili. Modifica **enabled_for_het_sub** influirà su altre proprietà della pubblicazione. Per ulteriori informazioni, vedere [sottoscrittori Non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare **@publication**, **@subscriber**, un valore di **(destinazione predefinita)** per **@destination_db**, un valore di **push** per **@subscription_type**, e un valore pari a 3 per **@subscriber_type** (specifica un provider OLE DB).  
  
4.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare le opzioni seguenti:  
  
    -   I parametri **@subscriber**e **@publication** .  
  
    -   Il valore **(destinazione predefinita)** per **@subscriber_db**,  
  
    -   Le proprietà di non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati per **@subscriber_provider**, **@subscriber_datasrc**, **@subscriber_location**, **@subscriber_provider_string**, e **@subscriber_catalog**.  
  
    -   Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] le credenziali di Windows con cui viene eseguito l'agente di distribuzione nel server di distribuzione per **@job_login** e **@job_password**.  
  
        > [!NOTE]  
        >  Le connessioni stabilite utilizzando sempre l'autenticazione integrata di Windows utilizzano le credenziali Windows specificate da **@job_login** e **@job_password**. L'agente di distribuzione esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore utilizzando l'autenticazione integrata di Windows.  
  
    -   Il valore **0** per **@subscriber_security_mode** e le informazioni di accesso del provider OLE DB per **@subscriber_login** e **@subscriber_password**.  
  
    -   Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione. Per altre informazioni, vedere [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Quando si crea una sottoscrizione push in un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
## Vedere anche  
 [Sottoscrittori IBM DB2](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Sottoscrittori Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)   
 [Altri Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/other-non-sql-server-subscribers.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  