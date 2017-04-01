---
title: "Visualizzazione e modifica delle impostazioni di sicurezza della replica | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying replication security settings"
  - "replication [SQL Server], security"
  - "security [SQL Server replication], viewing settings"
  - "viewing replication security settings"
  - "sicurezza [replica di SQL Server], modifica di impostazioni"
ms.assetid: 67d79532-1482-4de1-ac9f-4a23d162c85e
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# Visualizzazione e modifica delle impostazioni di sicurezza della replica
  In questo argomento viene descritto come visualizzare e modificare le impostazioni di sicurezza della replica in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects). È ad esempio possibile modificare la connessione dell'agente di lettura log al server di pubblicazione passando dall'autenticazione di SQL Server all'autenticazione integrata di Windows oppure potrebbe essere necessario modificare le credenziali utilizzate per eseguire un processo di agente al momento della modifica della password dell'account di Windows. Per informazioni sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare e modificare le impostazioni di sicurezza della replica, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
-   **Completamento:**  [dopo aver modificato le impostazioni di sicurezza](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Le stored procedure utilizzate dipenderanno dal tipo di agente e dal tipo di connessione al server.  
  
-   Le classi e le proprietà RMO utilizzate dipendono dal tipo di agente e dal tipo di connessione al server.  
  
###  <a name="Security"></a> Sicurezza  
 Per motivi di sicurezza, i valori effettivi delle password vengono mascherati nei set di risultati restituiti dalle stored procedure di replica.  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Visualizzare e modificare le impostazioni di sicurezza nelle seguenti finestre di dialogo:  
  
1.  La finestra di dialogo **Aggiorna password di replica** , disponibile nella cartella **Replica** di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Se si modifica la password di un account [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o Windows su un server di una topologia di replica, utilizzare questa finestra di dialogo anziché aggiornare la password per ogni agente che utilizza l'account. Se gli agenti di più server utilizzano lo stesso account, è necessario connettersi a ogni server e modificare la password. La password viene aggiornata in tutte le posizioni in cui viene utilizzata per la replica ma non viene aggiornata in altre posizioni, come i server collegati.  
  
2.  Il **agente protezione** pagina la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
3.  Il **Proprietà sottoscrizione - \< sottoscrizione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) e [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
4.  Il **proprietà server di distribuzione - \< distributore>** e **proprietà Database di distribuzione - \< Database>** le finestre di dialogo. Per ulteriori informazioni sull'accesso a queste finestre di dialogo, vedere [View and Modify Distributor and Publisher Properties](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
5.  Il **proprietà server di pubblicazione - \< Publisher>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, [View and Modify Distributor and Publisher Properties](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
#### Per modificare la password di un account utilizzato da uno o più agenti  
  
1.  Se l'account è di SQL Server, nella finestra di dialogo verrà modificata anche la password per tale account. Se l'account è di Windows, modificare innanzitutto la password in Windows. Per ulteriori informazioni, vedere la documentazione di Windows.  
  
    > [!NOTE]  
    >  Dopo aver modificato una password per la replica è necessario arrestare e riavviare ogni agente che utilizza la password prima che la modifica abbia effetto per tale agente.  
  
2.  Connettersi al server in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
3.  Pulsante destro del mouse il **replica** cartella e quindi fare clic su **Aggiorna password replica**.  
  
4.  Nella finestra di dialogo **Aggiorna password replica** specificare l'account e la nuova password.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le impostazioni di sicurezza per l'agente snapshot  
  
1.  Nel **agente protezione** pagina del **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo fare clic sul **le impostazioni di sicurezza** accanto al pulsante il **agente Snapshot** casella di testo.  
  
2.  Nella finestra di dialogo **Sicurezza agente snapshot** specificare l'account con il quale eseguire l'agente:  
  
    -   Immettere un nuovo account di Windows nella casella di testo **Account processo** .  
  
    -   Immettere una nuova password complessa nelle caselle di testo **Password** e **Conferma password** .  
  
3.  Specificare il contesto in cui l'agente deve connettersi dal server di distribuzione al server di pubblicazione. Se si seleziona **Tramite l'account di accesso di SQL Server seguente**, è anche necessario specificare l'account di accesso:  
  
    -   Immettere un account di accesso nella casella di testo **Account di accesso**  
  
    -   Immettere una nuova password complessa nelle caselle di testo **Password** e **Conferma password** .  
  
    > [!NOTE]  
    >  Se il server di pubblicazione è un server di pubblicazione Oracle, il contesto di connessione è specificato nella **proprietà server di distribuzione - \< distributore>**la finestra di dialogo. Per la procedura di modifica del contesto, vedere di seguito.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le impostazioni di sicurezza per l'agente di lettura log  
  
1.  Nel **agente protezione** pagina del **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo fare clic sul **le impostazioni di sicurezza** accanto al pulsante il **agente di lettura Log** casella di testo.  
  
2.  Nella finestra di dialogo **Sicurezza agente di lettura log** specificare l'account con il quale eseguire l'agente:  
  
    -   Immettere un nuovo account di Windows nella casella di testo **Account processo**  
  
    -   Immettere una nuova password complessa nelle caselle di testo **Password** e **Conferma password** .  
  
3.  Specificare il contesto in cui l'agente deve connettersi dal server di distribuzione al server di pubblicazione. Se si seleziona **Tramite l'account di accesso di SQL Server seguente**, è anche necessario specificare l'account di accesso:  
  
    -   Immettere un account di accesso nella casella di testo **Account di accesso**  
  
    -   Immettere una nuova password complessa nelle caselle di testo **Password** e **Conferma password** .  
  
    > [!NOTE]  
    >  Se il server di pubblicazione è un server di pubblicazione Oracle, il contesto di connessione è specificato nella **proprietà server di distribuzione - \< distributore>**la finestra di dialogo. Modificare il contesto utilizzando la procedura descritta di seguito.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  A ogni database pubblicato è associato un agente di lettura log. La modifica delle impostazioni di sicurezza per l'agente di una pubblicazione influisce sulle impostazioni di tutte le pubblicazioni del database di pubblicazione.  
  
#### Per modificare il contesto in cui l'agente snapshot e l'agente di lettura log di un'applicazione Oracle stabiliscono connessioni con il server di pubblicazione  
  
1.  Nel **editori** pagina della **proprietà server di distribuzione - \< distributore>** finestra di dialogo, fare clic sul pulsante delle proprietà (**...**) accanto a un server di pubblicazione.  
  
2.  Nella sezione **Connessione agente al server di pubblicazione** specificare l'account di accesso e la password utilizzati con lo schema utente di amministrazione della replica configurato. Per ulteriori informazioni, vedere [configurare un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le impostazioni di sicurezza dell'agente di distribuzione per una sottoscrizione push  
  
1.  Nel **Proprietà sottoscrizione - \< sottoscrizione>** la finestra di dialogo nel server di pubblicazione, è possibile apportare le modifiche seguenti:  
  
    -   Per modificare l'account con cui viene eseguito l'agente di distribuzione e stabilisce connessioni al server di distribuzione, fare clic sui **account processo agente** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare un account e una password nella finestra di dialogo **Sicurezza agente di distribuzione** .  
  
    -   Per modificare il contesto in cui l'agente di distribuzione si connette al server di sottoscrizione, scegliere il **connessione al sottoscrittore** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare il contesto nella finestra di dialogo **Immissione delle informazioni per la connessione** .  
  
         Se si utilizzano sottoscrizioni ad aggiornamento in coda, anche l'agente di lettura coda utilizzerà il contesto specificato per le connessioni al Sottoscrittore.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le impostazioni di sicurezza dell'agente di distribuzione per una sottoscrizione pull  
  
1.  Nel **Proprietà sottoscrizione - \< sottoscrizione>** la finestra di dialogo nel Sottoscrittore, è possibile apportare le modifiche seguenti:  
  
    -   Per modificare l'account con cui viene eseguito l'agente di distribuzione e stabilisce connessioni al server di sottoscrizione, scegliere il **account processo agente** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare un account e una password nella finestra di dialogo **Sicurezza agente di distribuzione** .  
  
         Se si utilizzano sottoscrizioni ad aggiornamento in coda, anche l'agente di lettura coda utilizzerà il contesto specificato per le connessioni al Sottoscrittore.  
  
    -   Per modificare il contesto in cui l'agente di distribuzione si connette al server di distribuzione, fare clic su di **connessione server di distribuzione** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare il contesto nella finestra di dialogo **Immissione delle informazioni per la connessione** .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le impostazioni di sicurezza dell'agente di merge per una sottoscrizione push  
  
1.  Nel **Proprietà sottoscrizione - \< sottoscrizione>** la finestra di dialogo nel server di pubblicazione, è possibile apportare le modifiche seguenti:  
  
    -   Per modificare l'account con cui l'agente di Merge viene eseguito e stabilisce le connessioni al server di pubblicazione e server di distribuzione, fare clic sui **account processo agente** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare un account e una password nella finestra di dialogo **Sicurezza agente di merge** .  
  
    -   Per modificare il contesto in cui l'agente di Merge si connette al server di sottoscrizione, scegliere il **connessione al sottoscrittore** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare il contesto nella finestra di dialogo **Immissione delle informazioni per la connessione** .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le impostazioni di sicurezza dell'agente di merge per una sottoscrizione pull  
  
1.  Nel **Proprietà sottoscrizione - \< sottoscrizione>** la finestra di dialogo nel Sottoscrittore, è possibile apportare le modifiche seguenti:  
  
    -   Per modificare l'account con cui l'agente di Merge viene eseguito e stabilisce connessioni al server di sottoscrizione, scegliere il **account processo agente** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare un account e una password nella finestra di dialogo **Sicurezza agente di merge** .  
  
    -   Per modificare il contesto in cui l'agente di Merge si connette al server di pubblicazione e server di distribuzione, fare clic su di **connessione server di pubblicazione** riga e quindi fare clic su proprietà (**...**) pulsante nella riga. Specificare il contesto nella finestra di dialogo **Immissione delle informazioni per la connessione** .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare l'account per l'esecuzione dell'agente di lettura coda  
  
1.  Nel **Generale** pagina della **proprietà server di distribuzione - \< distributore>** finestra di dialogo fare clic su proprietà (**...**) accanto a database di distribuzione.  
  
2.  Nel **proprietà Database di distribuzione - \< Database>** nella finestra di dialogo fare clic sul **le impostazioni di sicurezza** accanto al pulsante il **account processo agente** casella di testo.  
  
3.  Nella finestra di dialogo **Sicurezza agente di lettura coda** specificare l'account utilizzato per eseguire l'agente e stabilire connessioni con il server di distribuzione:  
  
    -   Immettere un nuovo account di Windows nella casella di testo **Account processo**  
  
    -   Immettere una nuova password complessa nelle caselle di testo **Password** e **Conferma password** .  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  A ogni database di distribuzione è associato un agente di lettura coda. La modifica delle impostazioni di sicurezza dell'agente influisce sulle impostazioni di tutte le pubblicazioni presenti in tutti i server di pubblicazione che utilizzano questo database di distribuzione.  
  
#### Per modificare il contesto in cui l'agente di lettura coda stabilisce connessioni con il server di pubblicazione  
  
1.  Nel **editori** pagina della **proprietà server di distribuzione - \< server di distribuzione>** finestra di dialogo, fare clic sul pulsante delle proprietà (**...**) accanto a server di pubblicazione.  
  
2.  Nella sezione **Connessione agente al server di pubblicazione** specificare il valore **Rappresenta l'account del processo dell'agente** o **Autenticazione di SQL Server** per l'opzione **Modalità di connessione dell'agente** . Se si specifica **Autenticazione di SQL Server**, immettere anche i valori per **Account di accesso** e **Password**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  A ogni database di distribuzione è associato un agente di lettura coda. La modifica delle impostazioni di sicurezza dell'agente influisce sulle impostazioni di tutte le pubblicazioni presenti in tutti i server di pubblicazione che utilizzano questo database di distribuzione.  
  
#### Per modificare il contesto in cui l'agente di lettura coda stabilisce connessioni con il Sottoscrittore  
  
-   L'agente di lettura coda utilizza lo stesso contesto di connessione dell'agente di distribuzione per la sottoscrizione. Per ulteriori informazioni, vedere le procedure descritte prima per l'agente di distribuzione.  
  
#### Per modificare le impostazioni di sicurezza per una sottoscrizione pull ad aggiornamento immediato  
  
1.  Nel **Proprietà sottoscrizione - \< sottoscrizione>** la finestra di dialogo nel Sottoscrittore, fare clic su di **connessione server di pubblicazione** riga e quindi fare clic su proprietà (**...**) pulsante nella riga.  
  
2.  Nella finestra di dialogo **Immissione delle informazioni per la connessione** selezionare una delle seguenti opzioni:  
  
    -   **Usa account di accesso di un server collegato o remoto**. Selezionare questa opzione se è stato definito un server remoto o collegato tra il server di sottoscrizione e il server di pubblicazione utilizzando [sp_addserver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], o un altro metodo.  
  
    -   **Usa autenticazione di SQL Server con l'account e la password seguenti**. Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante il processo di replica verrà automaticamente creato un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Questa procedura consente di modificare il metodo utilizzato con i trigger di replica per eseguire la connessione dal Sottoscrittore al server di pubblicazione quando vengono apportate modifiche nel Sottoscrittore. È anche possibile modificare le impostazioni associate all'agente di distribuzione per una sottoscrizione ad aggiornamento immediato. Per ulteriori informazioni, vedere le procedure descritte in precedenza in questo argomento.  
>   
>  Questa procedura è valida solo per le sottoscrizioni pull. Per le sottoscrizioni push, utilizzare la stored procedure [sp_link_publication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md).  
  
#### Per modificare la password per la connessione amministrativa dal server di pubblicazione al database di distribuzione  
  
1.  Nel **editori** pagina della **proprietà server di distribuzione - \< server di distribuzione>** finestra di dialogo, immettere una password complessa nel **Password** e **Conferma Password** caselle di testo.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  Nel **Generale** pagina della **proprietà server di pubblicazione - \< Publisher>** finestra di dialogo, immettere una password complessa nel **Password** e **Conferma Password** le caselle di testo.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
> [!IMPORTANT]  
>  In tutte le procedure descritte di seguito, quando possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se si archiviano le credenziali in un file di script, è necessario proteggere il file per impedire l'accesso non autorizzato.  
  
#### Per modificare tutte le istanze di una password archiviate in un server di replica  
  
1.  Un server in una topologia di replica nel database master, eseguire [sp_changereplicationserverpasswords](../../../relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql.md). Specificare l'account di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows o il nome di accesso di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per cui modificare la password per **@login** e la nuova password per l'account o il nome di accesso per **@password**. In questo modo viene modificata ogni istanza della password utilizzata da tutti gli agenti nel server quando si connettono ad altri server della topologia.  
  
    > [!NOTE]  
    >  Per modifica solo l'account di accesso e password per una connessione a un determinato server nella topologia (ad esempio, il server di distribuzione o il sottoscrittore), specificare il nome del server per **@server**.  
  
2.  Ripetere il passaggio 1 in ogni server della topologia di replica in cui è necessario aggiornare la password.  
  
    > [!NOTE]  
    >  Dopo aver modificato una password per la replica è necessario arrestare e riavviare ogni agente che utilizza la password prima che la modifica abbia effetto per tale agente.  
  
#### Per modificare le impostazioni di sicurezza per l'agente snapshot  
  
1.  Server di pubblicazione, eseguire [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), specificando **@publication**. Verranno restituite le impostazioni di sicurezza correnti per l'agente snapshot.  
  
2.  Server di pubblicazione, eseguire [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), specificando **@publication** e uno o più delle seguenti impostazioni di sicurezza da modificare:  
  
    -   Per modificare l'account di Windows in cui viene eseguito l'agente o solo la password per questo account, è necessario specificare **@job_login** e **@job_password**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione, specificare un valore di **1** o **0** per **@publisher_security_mode**.  
  
    -   Quando si modifica la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione da **1** a **0** o quando si modifica un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account di accesso utilizzato per la connessione, specificare **@publisher_login** e **@publisher_password**.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per modificare le impostazioni di sicurezza per l'agente di lettura log  
  
1.  Server di pubblicazione, eseguire [sp_helplogreader_agent](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md), specificando **@publisher**. Verranno restituite le impostazioni di sicurezza correnti per l'agente di lettura log.  
  
2.  Server di pubblicazione, eseguire [sp_changelogreader_agent](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md), specificando **@publication** e uno o più delle seguenti impostazioni di sicurezza da modificare:  
  
    -   Per modificare l'account di Windows in cui viene eseguito l'agente o solo la password per questo account, è necessario specificare **@job_login** e **@job_password**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione, specificare un valore di **1** o **0** per **@publisher_security_mode**.  
  
    -   Quando si modifica la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione da **1** a **0** o quando si modifica un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account di accesso utilizzato per la connessione, specificare **@publisher_login** e **@publisher_password**.  
  
    > [!NOTE]  
    >  Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per modificare le impostazioni di sicurezza dell'agente di distribuzione per una sottoscrizione push  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpsubscription](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md), specificando **@publication** e **@subscriber**. Verranno restituite le proprietà della sottoscrizione, incluse le impostazioni di sicurezza per l'agente di distribuzione eseguito nel server di distribuzione.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changesubscription](../../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md), specificando **@publication**, **@subscriber**, **@subscriber_db**, un valore di **tutti** per **@article**, il nome della proprietà di sicurezza per **@property**, e il nuovo valore della proprietà per **@value**.  
  
3.  Ripetere il passaggio 2 per ognuna delle seguenti proprietà di sicurezza da modificare:  
  
    -   Per modificare l'account di Windows in cui viene eseguito l'agente o solo la password per questo account, specificare un valore di **distrib_job_password** per **@property** e una nuova password per **@value**. Quando si modifica l'account stesso, ripetere il passaggio 2 specificando il valore **distrib_job_login** per **@property** e il nuovo account di Windows per **@value**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al sottoscrittore, specificare un valore di **subscriber_security_mode** per **@property** e il valore **1** (autenticazione integrata di Windows) o **0** (autenticazione di SQL Server) per **@value**.  
  
    -   Quando si modifica la modalità di sicurezza del sottoscrittore per l'autenticazione di SQL Server o se si modificano le informazioni di accesso per l'autenticazione di SQL Server, specificare un valore di **subscriber_password** per **@property** e la nuova password per **@value**. Ripetere il passaggio 2, specificando un valore di **subscriber_login** per **@property** e il nuovo account di accesso per **@value**.  
  
    > [!NOTE]  
    >  Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi **distrib_job_login** e **distrib_job_password**, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per modificare le impostazioni di sicurezza dell'agente di distribuzione per una sottoscrizione pull  
  
1.  Il sottoscrittore, eseguire [sp_helppullsubscription](../../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md), specificando **@publication**. Verranno restituite le proprietà della sottoscrizione, incluse le impostazioni di sicurezza per l'agente di distribuzione eseguito nel Sottoscrittore.  
  
2.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_change_subscription_properties](../../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), specificando **@publisher**, **@publisher_db**, **@publication**, il nome della proprietà di sicurezza per **@property**, e il nuovo valore della proprietà per **@value**.  
  
3.  Ripetere il passaggio 2 per ognuna delle seguenti proprietà di sicurezza da modificare:  
  
    -   Per modificare l'account di Windows in cui viene eseguito l'agente o solo la password per questo account, specificare un valore di **distrib_job_password** per **@property** e una nuova password per **@value**. Quando si modifica l'account stesso, ripetere il passaggio 2 specificando il valore **distrib_job_login** per **@property** e il nuovo account di Windows per **@value**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al server di distribuzione, specificare un valore di **distributor_security_mode** per **@property** e il valore **1** (autenticazione integrata di Windows) o **0** (autenticazione di SQL Server) per **@value**.  
  
    -   Quando si modifica la modalità di sicurezza del server di distribuzione per l'autenticazione di SQL Server o se si modificano le informazioni di accesso per l'autenticazione di SQL Server, specificare un valore di **distributor_password** per **@property** e la nuova password per **@value**. Ripetere il passaggio 2, specificando un valore di **distributor_login** per **@property** e il nuovo account di accesso per **@value**.  
  
    > [!NOTE]  
    >  Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
#### Per modificare le impostazioni di sicurezza dell'agente di merge per una sottoscrizione push  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergesubscription](../../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md), specificando **@publication**, **@subscriber**, e **@subscriber_db**. Verranno restituite le proprietà della sottoscrizione, incluse le impostazioni di sicurezza per l'agente di merge eseguito nel server di distribuzione.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergesubscription](../../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md), specificando **@publication**, **@subscriber**, **@subscriber_db**, il nome della proprietà di sicurezza per **@property**, e il nuovo valore della proprietà per **@value**.  
  
3.  Ripetere il passaggio 2 per ognuna delle seguenti proprietà di sicurezza da modificare:  
  
    -   Per modificare l'account di Windows in cui viene eseguito l'agente, o semplicemente la password per questo account, specificare un valore di **merge_job_password** per **@property** e una nuova password per **@value**. Quando si modifica l'account stesso, ripetere il passaggio 2 specificando il valore **merge_job_login** per **@property** e il nuovo account di Windows per **@value**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al sottoscrittore, specificare un valore di **subscriber_security_mode** per **@property** e il valore **1** (autenticazione integrata di Windows) o **0** (autenticazione di SQL Server) per **@value**.  
  
    -   Quando si modifica la modalità di sicurezza del sottoscrittore per l'autenticazione di SQL Server o se si modificano le informazioni di accesso per l'autenticazione di SQL Server, specificare un valore di **subscriber_password** per **@property** e la nuova password per **@value**. Ripetere il passaggio 2, specificando un valore di **subscriber_login** per **@property** e il nuovo account di accesso per **@value**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione, specificare un valore di **publisher_security_mode** per **@property** e il valore **1** (autenticazione integrata di Windows) o **0** (autenticazione di SQL Server) per **@value**.  
  
    -   Quando si modifica la modalità di sicurezza del server di pubblicazione per l'autenticazione di SQL Server o se si modificano le informazioni di accesso per l'autenticazione di SQL Server, specificare un valore di **publisher_password** per **@property** e la nuova password per **@value**. Ripetere il passaggio 2, specificando un valore di **publisher_login** per **@property** e il nuovo account di accesso per **@value**.  
  
    > [!NOTE]  
    >  Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutte le proprietà, inclusi **merge_job_login** e **merge_job_password**, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per modificare le impostazioni di sicurezza dell'agente di merge per una sottoscrizione pull  
  
1.  Il sottoscrittore, eseguire [sp_helpmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md), specificando **@publication**. Verranno restituite le proprietà della sottoscrizione, incluse le impostazioni di sicurezza per l'agente di merge eseguito nel Sottoscrittore.  
  
2.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_change_subscription_properties](../../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), specificando **@publisher**, **@publisher_db**, **@publication**, il nome della proprietà di sicurezza per **@property**, e il nuovo valore della proprietà per **@value**.  
  
3.  Ripetere il passaggio 2 per ognuna delle seguenti proprietà di sicurezza da modificare:  
  
    -   Per modificare l'account di Windows in cui viene eseguito l'agente o solo la password per questo account, specificare un valore di **merge_job_password** per **@property** e nuova password per **@value**. Quando si modifica l'account stesso, ripetere il passaggio 2 specificando il valore **merge_job_login** per **@property** e il nuovo account di Windows per **@value**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al server di distribuzione, specificare un valore di **distributor_security_mode** per **@property** e il valore **1** (autenticazione integrata di Windows) o **0** (autenticazione di SQL Server) per **@value**.  
  
    -   Quando si modifica la modalità di sicurezza del server di distribuzione per l'autenticazione di SQL Server o se si modificano le informazioni di accesso per l'autenticazione di SQL Server, specificare un valore di **distributor_password** per **@property** e la nuova password per **@value**. Ripetere il passaggio 2, specificando un valore di **distributor_login** per **@property** e il nuovo account di accesso per **@value**.  
  
    -   Per modificare la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione, specificare un valore di **publisher_security_mode** per **@property** e il valore **1** (autenticazione integrata di Windows) o **0** (autenticazione di SQL Server) per **@value**.  
  
    -   Quando si modifica la modalità di sicurezza del server di pubblicazione per l'autenticazione di SQL Server o se si modificano le informazioni di accesso per l'autenticazione di SQL Server, specificare un valore di **publisher_password** per **@property** e la nuova password per **@value**. Ripetere il passaggio 2, specificando un valore di **publisher_login** per **@property** e il nuovo account di accesso per **@value**.  
  
    > [!NOTE]  
    >  Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
#### Per modificare impostazioni di sicurezza per l'agente snapshot e generare uno snapshot filtrato per un Sottoscrittore  
  
1.  Server di pubblicazione, eseguire [sp_helpdynamicsnapshot_job](../../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md), specificando **@publication**. Nel risultato impostata, prendere nota del valore di **job_name** per la partizione del sottoscrittore da modificare.  
  
2.  Server di pubblicazione, eseguire [sp_changedynamicsnapshot_job](../../../relational-databases/system-stored-procedures/sp-changedynamicsnapshot-job-transact-sql.md), specificando **@publication**, il valore ottenuto nel passaggio 1 per **@dynamic_snapshot_jobname**, e una nuova password per **@job_password** o account di accesso e password per l'account di Windows con cui viene eseguito l'agente per **@job_login** e **@job_password**.  
  
    > [!IMPORTANT]  
    >  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per ulteriori informazioni, vedere [abilitare connessioni crittografate al motore di Database & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Per modificare le impostazioni di sicurezza per l'agente di lettura coda  
  
1.  Nel server di distribuzione, eseguire [sp_helpqreader_agent](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md). Verrà restituito l'account di Windows corrente utilizzato per eseguire l'agente di lettura coda.  
  
    -   Nel server di distribuzione, eseguire [sp_changeqreader_agent](../../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md), specificando le impostazioni dell'account Windows per **@job_login** e **@job_passwsord**.  
  
    > [!NOTE]  
    >  Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica. A ogni database di distribuzione è associato un agente di lettura coda. La modifica delle impostazioni di sicurezza dell'agente influisce sulle impostazioni di tutte le pubblicazioni presenti in tutti i server di pubblicazione che utilizzano questo database di distribuzione.  
  
2.  L'agente di lettura coda esegue le connessioni al Sottoscrittore utilizzando lo stesso contesto di connessione dell'agente di distribuzione per la sottoscrizione.  
  
#### Per modificare la modalità di sicurezza utilizzata da un Sottoscrittore ad aggiornamento immediato per la connessione al server di pubblicazione  
  
1.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Specificare **@publisher**, **@publication**, il nome del database di pubblicazione per **@publisher_db**, e uno dei seguenti valori per **@security_mode**:  
  
    -   **0** per utilizzare l'autenticazione di SQL Server quando si eseguono aggiornamenti nel server di pubblicazione. Questa opzione richiede di specificare un account di accesso valido nel server di pubblicazione per **@login** e **@password**.  
  
    -   **1** per utilizzare il contesto di sicurezza dell'utente che esegue le modifiche nel Sottoscrittore quando ci si connette al server di pubblicazione. Vedere [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) per le restrizioni relative a questa modalità di sicurezza.  
  
    -   **2** per utilizzare un oggetto esistente, definito dall'utente collegato utilizzando account di accesso server [sp_addlinkedserver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
#### Per modificare la password per un server di distribuzione remoto  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_changedistributor_password](../../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md), specificando la nuova password per questo account di accesso per **@password**.  
  
    > [!IMPORTANT]  
    >  Non modificare la password per **distributor_admin** direttamente.  
  
2.  Ogni server di pubblicazione che utilizza questo server di distribuzione remoto, eseguire [sp_changedistributor_password](../../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md), specificare la password dal passaggio 1 per **@password**.  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Per modificare tutte le istanze di una password archiviate in un server di replica  
  
1.  Creare una connessione al server di replica utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe tramite la connessione del passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeReplicationServerPasswords%2A> metodo. Specificare i parametri seguenti:  
  
    -   *security_mode* - <xref:Microsoft.SqlServer.Replication.ReplicationSecurityMode> valore che specifica il tipo di autenticazione per il quale vengono modificate tutte le istanze della password.  
  
    -   *account di accesso* -l'account di accesso per il quale vengono modificate tutte le istanze della password.  
  
    -   *password* -nuovo valore della password.  
  
        > [!IMPORTANT]  
        >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](http://go.microsoft.com/fwlink/?LinkId=34733) offerti da Windows .NET Framework.  
  
        > [!NOTE]  
        >  Solo un membro con il **sysadmin** ruolo predefinito del server può chiamare questo metodo.  
  
4.  Ripetere i passaggi da 1 a 3 in ogni server della topologia di replica in cui è necessario aggiornare la password.  
  
#### Per modificare le impostazioni di sicurezza dell'agente di distribuzione per una sottoscrizione push in una pubblicazione transazionale  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, e <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> le proprietà per la sottoscrizione, quindi impostare la connessione creata nel passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste.  
  
5.  Impostare uno o più delle seguenti proprietà di sicurezza nell'istanza di <xref:Microsoft.SqlServer.Replication.TransSubscription>:  
  
    -   Per modificare le credenziali per l'account di Windows con cui viene eseguito l'agente, impostare il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>.  
  
    -   Per specificare l'autenticazione integrata di Windows come il tipo di autenticazione utilizzato dall'agente quando si connette al sottoscrittore, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> proprietà **true**.  
  
    -   Per specificare l'autenticazione di SQL Server come il tipo di autenticazione utilizzato dall'agente quando si connette al sottoscrittore, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> proprietà **false**, e specificare le credenziali di accesso sottoscrittore per il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> campi.  
  
        > [!NOTE]  
        >  Connessione dell'agente al server di distribuzione viene sempre eseguita utilizzando le credenziali Windows specificate da <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>. Questo account viene utilizzato anche per stabilire connessioni remote tramite l'autenticazione di Windows.  
  
6.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
#### Per modificare le impostazioni di sicurezza dell'agente di distribuzione per una sottoscrizione pull in una pubblicazione transazionale  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> le proprietà per la sottoscrizione, quindi impostare la connessione creata nel passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste.  
  
5.  Impostare uno o più delle seguenti proprietà di sicurezza nell'istanza di <xref:Microsoft.SqlServer.Replication.TransPullSubscription>:  
  
    -   Per modificare le credenziali per l'account di Windows con cui viene eseguito l'agente, impostare il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>.  
  
    -   Per specificare l'autenticazione integrata di Windows come il tipo di autenticazione utilizzato dall'agente quando si connette al server di distribuzione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> proprietà **true**.  
  
    -   Per specificare l'autenticazione di SQL Server come il tipo di autenticazione utilizzato dall'agente quando si connette al server di distribuzione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> proprietà **false**, e specificare le credenziali di accesso del server di distribuzione per il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> campi.  
  
        > [!NOTE]  
        >  Connessione dell'agente al sottoscrittore viene sempre eseguita utilizzando le credenziali Windows specificate da <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>. Questo account viene utilizzato anche per stabilire connessioni remote tramite l'autenticazione di Windows.  
  
6.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
#### Per modificare le impostazioni di sicurezza dell'agente di merge per una sottoscrizione pull in una pubblicazione di tipo merge  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, e <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> le proprietà per la sottoscrizione, quindi impostare la connessione creata nel passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste.  
  
5.  Impostare uno o più delle seguenti proprietà di sicurezza nell'istanza di <xref:Microsoft.SqlServer.Replication.MergePullSubscription>:  
  
    -   Per modificare le credenziali per l'account di Windows con cui viene eseguito l'agente, impostare il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>.  
  
    -   Per specificare l'autenticazione integrata di Windows come il tipo di autenticazione utilizzato dall'agente quando si connette al server di distribuzione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> proprietà **true**.  
  
    -   Per specificare l'autenticazione di SQL Server come il tipo di autenticazione utilizzato dall'agente quando si connette al server di distribuzione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> proprietà **false**, e specificare le credenziali di accesso del server di distribuzione per il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> campi.  
  
    -   Per specificare l'autenticazione integrata di Windows come il tipo di autenticazione utilizzato dall'agente quando si connette al server di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> proprietà **true**.  
  
    -   Per specificare l'autenticazione di SQL Server come il tipo di autenticazione utilizzato dall'agente quando si connette al server di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> proprietà **false**, e specificare le credenziali di accesso del server di pubblicazione per il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> campi.  
  
        > [!NOTE]  
        >  Connessione dell'agente al sottoscrittore viene sempre eseguita utilizzando le credenziali Windows specificate da <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>. Questo account viene utilizzato anche per stabilire connessioni remote tramite l'autenticazione di Windows.  
  
6.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
#### Per modificare le impostazioni di sicurezza dell'agente di merge per una sottoscrizione push in una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, e <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> le proprietà per la sottoscrizione, quindi impostare la connessione creata nel passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della sottoscrizione non sono state definite in modo corretto nel passaggio 3 oppure la sottoscrizione non esiste.  
  
5.  Impostare uno o più delle seguenti proprietà di sicurezza nell'istanza di <xref:Microsoft.SqlServer.Replication.MergeSubscription>:  
  
    -   Per modificare le credenziali per l'account di Windows con cui viene eseguito l'agente, impostare il <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> e <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> i campi di <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>.  
  
    -   Per specificare l'autenticazione integrata di Windows come il tipo di autenticazione utilizzato dall'agente quando si connette al sottoscrittore, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> proprietà **true**.  
  
    -   Per specificare l'autenticazione di SQL Server come il tipo di autenticazione utilizzato dall'agente quando si connette al sottoscrittore, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> proprietà **false**, e specificare le credenziali di accesso sottoscrittore per il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> campi.  
  
    -   Per specificare l'autenticazione integrata di Windows come il tipo di autenticazione utilizzato dall'agente quando si connette al server di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.MergeSubscription.PublisherSecurity%2A> proprietà **true**.  
  
    -   Per specificare l'autenticazione di SQL Server come il tipo di autenticazione utilizzato dall'agente quando si connette al server di pubblicazione, impostare il <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> campo di <xref:Microsoft.SqlServer.Replication.MergeSubscription.PublisherSecurity%2A> proprietà **false**, e specificare le credenziali di accesso del server di pubblicazione per il <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext.SqlStandardLogin%2A> e <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext.SqlStandardPassword%2A> campi.  
  
        > [!NOTE]  
        >  Connessione dell'agente al server di distribuzione viene sempre eseguita utilizzando le credenziali Windows specificate da <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>. Questo account viene utilizzato anche per stabilire connessioni remote tramite l'autenticazione di Windows.  
  
6.  (Facoltativo) Se si specifica un valore di **true** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore di **false** per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate al server immediatamente.  
  
#### Per modificare le informazioni di accesso utilizzate da un Sottoscrittore ad aggiornamento immediato quando si connette al server di pubblicazione transazionale  
  
1.  Creare una connessione al sottoscrittore utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe per il database di sottoscrizione. Specificare <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.Name%2A> e <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1 per <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà del database non sono state definite in modo corretto nel passaggio 2 oppure il database di sottoscrizione non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LinkPublicationForUpdateableSubscription%2A> passando i parametri seguenti:  
  
    -   *Server di pubblicazione* -il nome del server di pubblicazione.  
  
    -   *PublisherDB* -il nome del database di pubblicazione.  
  
    -   *Pubblicazione* : il nome della pubblicazione a cui è stato sottoscritto il sottoscrittore ad aggiornamento immediato.  
  
    -   *Server di distribuzione* -il nome del server di distribuzione.  
  
    -   *PublisherSecurity* - <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext> oggetto che specifica il tipo di modalità di sicurezza utilizzata dal server di sottoscrizione ad aggiornamento immediato quando ci si connette alle credenziali del server di pubblicazione e account di accesso per la connessione.  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene controllato il valore di accesso fornito e vengono modificate tutte le password per l'account di accesso di Windows o di SQL Server specificato archiviate dalla replica nel server.  
  
 [!code-csharp[HowTo#rmo_ChangeServerPasswords](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changeserverpasswords)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeServerPasswords](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changeserverpasswords)]  
  
##  <a name="FollowUp"></a> Completamento: dopo avere modificato le impostazioni di sicurezza della replica  
 Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
## Vedere anche  
 [Concetti di base relativi a RMO (Replication Management Objects)](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Aggiornare gli script di replica & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [Gestione degli account di accesso e delle password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  