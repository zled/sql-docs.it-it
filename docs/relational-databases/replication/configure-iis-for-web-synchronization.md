---
title: "Configurazione di IIS per la sincronizzazione Web | Microsoft Docs"
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
  - "configurazione di server IIS [replica di SQL Server]"
  - "websync.log"
  - "Sincronizzazione Web, server IIS"
ms.assetid: d651186e-c9ca-4864-a444-2cd6943b8e35
caps.latest.revision: 88
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 88
---
# Configurazione di IIS per la sincronizzazione Web
  Le procedure descritte in questo argomento rappresentano il secondo passaggio nella configurazione della sincronizzazione Web per la replica di tipo merge. Questo passaggio è successivo all'abilitazione di una pubblicazione per la sincronizzazione Web. Per una panoramica del processo di configurazione, vedere [Configura sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md). Al termine delle procedure indicate in questo argomento, procedere al terzo passaggio, che consiste nella configurazione di una sottoscrizione per l'utilizzo della sincronizzazione Web. Questo terzo passaggio è descritto negli argomenti seguenti:  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [How to: Configure a Subscription to Use Web Synchronization \(SQL Server Management Studio\)](http://msdn.microsoft.com/library/ms345214.aspx)  
  
-   Replica [!INCLUDE[tsql](../../includes/tsql-md.md)] programming: [procedura: configurare una sottoscrizione a Usa sincronizzazione Web (programmazione Transact-SQL della replica)](http://msdn.microsoft.com/library/ms345206.aspx)  
  
-   RMO: [procedura: configurare una sottoscrizione per utilizzare la sincronizzazione Web (programmazione RMO)](http://msdn.microsoft.com/library/ms345207.aspx)  
  
 Nella sincronizzazione Web viene utilizzato un computer che esegue [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) per sincronizzare le sottoscrizioni pull con le pubblicazioni di tipo merge. IIS versione 5.0, IIS versione 6.0 e [!INCLUDE[iisver](../../includes/iisver-md.md)] sono supportati. La configurazione guidata sincronizzazione Web non è supportata in [!INCLUDE[iisver](../../includes/iisver-md.md)].  
  
> [!IMPORTANT]  
>  Verificare che nell'applicazione venga utilizzato solo [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] o versione successiva e che le versioni precedenti di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] non siano installate sul server IIS. Le versioni precedenti di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] possono causare errori come, ad esempio, "Formato di messaggio non valido durante la sincronizzazione Web. Verificare che i componenti di replica siano configurati correttamente nel server Web".  
  
> [!CAUTION]  
>  Non utilizzare contemporaneamente sia WebSync sia percorsi alternativi della cartella snapshot.  
  
 Per utilizzare la sincronizzazione Web, è necessario configurare IIS eseguendo la procedura seguente. Ogni passaggio è descritto in dettaglio in questo argomento.  
  
1.  Configurare SSL (Secure Sockets Layer). L'utilizzo di SSL è obbligatorio per la comunicazione tra IIS e tutti i Sottoscrittori.  
  
2.  Installare [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i componenti di connettività del computer che esegue IIS tramite il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata. Se si intende utilizzare la procedura di configurazione guidata della sincronizzazione Web citata nel passaggio 3, è necessario installare anche [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nel computer che esegue IIS.  
  
3.  Configurare il computer che esegue IIS per la sincronizzazione Web. È possibile configurare manualmente il computer oppure utilizzare la procedura di configurazione guidata della sincronizzazione Web. È consigliabile utilizzare la procedura guidata.  
  
    > [!NOTE]  
    >  Se nel computer con IIS viene eseguita una versione a 64 bit di Windows, è necessario eseguire il comando seguente per garantire la corretta configurazione del server per le applicazioni ISAPI. Per ulteriori informazioni, vedere la documentazione di IIS.  
  
    ```  
    cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 1  
    ```  
  
4.  Impostare le autorizzazioni appropriate per Listener per la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Eseguire la sincronizzazione Web in modalità diagnostica per testare la connessione al computer che esegue IIS e verificare la corretta installazione del certificato SSL (Secure Sockets Layer).  
  
## Configurazione di SSL (Secure Sockets Layer)  
 Per configurare SSL, specificare un certificato che il computer che esegue IIS deve utilizzare. La sincronizzazione Web per la replica di tipo merge supporta l'utilizzo di certificati server ma non di certificati client. Per configurare IIS per la distribuzione, è innanzitutto necessario ottenere un certificato da un'autorità di certificazione. Un'autorità di certificazione è un'entità responsabile di determinare e garantire l'autenticità delle chiavi di crittografia pubbliche appartenenti a utenti, computer o altre autorità di certificazione. Per ulteriori informazioni sui certificati, vedere la documentazione di IIS. Dopo l'installazione del certificato, è necessario associare il certificato al sito Web utilizzato nella sincronizzazione Web.  
  
#### Per specificare un certificato per la distribuzione  
  
1.  Accedere come amministratore al computer che esegue IIS.  
  
2.  Avviare **Gestione Internet Information Services (IIS)**:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare **inetmgr**, quindi fare clic su **OK**.  
  
3.  Eseguire la Gestione guidata certificati IIS:  
  
    1.  In **Gestione Internet Information Services (IIS)**, espandere il **computer locale** nodo, quindi espandere il **siti Web** cartella.  
  
    2.  Fare doppio clic su **Default Web Site**, quindi fare clic su **proprietà**.  
  
    3.  Nel **Proprietà sito Web predefinito** della finestra di dialogo di **Protezione Directory** fare clic su **certificato Server**.  
  
    4.  Completare la Gestione guidata certificati server Web.  
  
4.  Scegliere **OK**.  
  
 Se non è possibile ottenere un certificato server da un'autorità di certificazione, è possibile specificare un certificato per l'esecuzione di test. Per configurare IIS 6.0 per l'esecuzione di test, installare un certificato mediante l'utilità SelfSSL disponibile nel Resource Kit di IIS 6.0. È possibile scaricare gli strumenti di [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=30958). Per IIS 5.0, vedere [Microsoft Help and Support](http://go.microsoft.com/fwlink/?LinkId=46229).  
  
> [!NOTE]  
>  Affinché un sito Web possa utilizzare SSL, è necessario che a tale sito sia associato un certificato. SelfSSL associa automaticamente il certificato al sito Web predefinito. Se si dispone già di un certificato oppure si installa successivamente un certificato di un'autorità di certificazione, è necessario associare tale certificato in modo esplicito al sito Web utilizzato nella sincronizzazione Web. Assicurarsi che al sito Web utilizzato per la sincronizzazione delle sottoscrizioni sia associato un solo certificato. Se sono associati più certificati, il Sottoscrittore utilizzerà il primo sito Web disponibile.  
  
#### Per specificare un certificato per l'esecuzione di test in IIS 6.0  
  
1.  Accedere come amministratore al computer che esegue IIS.  
  
2.  Scaricare e installare SelfSSL. Per impostazione predefinita, l'applicazione viene installata in \<*unità*>: \programmi\iis resources\selfssl.. Applicazione e alla documentazione vengono copiati in \<*unità*>: \Documents and Settings\All Users\Menu start\programmi\iis resources\selfssl..  
  
3.  Eseguire SelfSSL:  
  
    -   Per eseguire SelfSSL con i valori predefiniti per tutti i parametri, individuare la directory di installazione dell'applicazione e fare doppio clic su SelfSSL.exe.  
  
        > [!NOTE]  
        >  Per impostazione predefinita, il certificato installato da SelfSSL ha una validità di sette giorni.  
  
    -   Specificare i valori per uno o più parametri: fare clic su **avviare**, quindi fare clic su **eseguire**. Nel **aprire** immettere **cmd**, quindi fare clic su **OK**. Individuare la directory di installazione di SelfSSL, digitare `SelfSSL` e quindi specificare i valori per uno o più parametri. Per un elenco di parametri, digitare `SelfSSL -?`.  
  
## Installazione di componenti di connettività e SQL Server Management Studio  
  
#### Per installare i componenti di connettività di SQL Server e SQL Server Management Studio  
  
1.  Accedere come amministratore al computer che esegue IIS.  
  
2.  Dal disco di installazione di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] avviare l'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [installare SQL Server 2016 da installazione guidata di & #40; Il programma di installazione & #41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
3.  Nel **Selezione funzionalità** selezionare **Connettività strumenti Client**.  
  
4.  Se si prevede di utilizzare la configurazione guidata sincronizzazione Web, selezionare **Management Tools - Basic**.  
  
5.  Completare la procedura guidata e quindi riavviare il computer.  
  
    > [!NOTE]  
    >  È possibile installare componenti aggiuntivi, ma per la sincronizzazione Web sono necessari soltanto i componenti di connettività.  
  
## Configurazione del computer che esegue IIS utilizzando la procedura di configurazione guidata della sincronizzazione Web  
 Configurare il server IIS mediante la procedura di configurazione guidata della sincronizzazione Web o manualmente. Sebbene sia consigliabile utilizzare la procedura guidata, nella prossima sezione verranno illustrati i passaggi necessari per la configurazione manuale. La configurazione guidata sincronizzazione Web è disponibile con [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] può essere utilizzato solo per le pubblicazioni create in un server di pubblicazione che esegue [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], o un server di pubblicazione è stato aggiornato a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Non può essere utilizzata per le pubblicazioni in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Può essere utilizzata con le sottoscrizioni in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive e [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 e versioni successive.  
  
 La configurazione presenta le funzionalità seguenti:  
  
-   Utilizza il sito Web predefinito in IIS. È comunque possibile utilizzare un altro sito Web. Per ulteriori informazioni sulla creazione di siti Web, vedere la documentazione di IIS.  
  
    > [!NOTE]  
    >  Il sito Web specificato garantisce l'accesso ai componenti utilizzati nella sincronizzazione Web e consente l'accesso ad altri dati o ad altre pagine Web solo se configurato a tale scopo.  
  
-   Crea una directory virtuale e gli alias associati. L'alias viene utilizzato per l'accesso ai componenti della sincronizzazione Web. Ad esempio, se l'indirizzo IIS è https://*server.dominio.com* e si specifica l'alias 'websync1', l'indirizzo per accedere al componente replisapi. dll sarà https://*server.dominio.com*/websync1/replisapi.dll.  
  
-   Utilizza l'autenticazione di base. È consigliabile utilizzare l'autenticazione di base poiché consente di eseguire IIS e il server di pubblicazione/distribuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in computer separati (configurazione consigliata) senza la delega Kerberos. L'utilizzo di SSL con l'autenticazione di base assicura la crittografia degli account di accesso, delle password e di tutti i dati in transito. SSL è necessario indipendentemente dal tipo di autenticazione utilizzato. Per ulteriori informazioni sulle procedure consigliate per la sincronizzazione Web, vedere la sezione "Sicurezza procedure consigliate per la sincronizzazione Web" in [Configura sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
#### Per configurare il computer che esegue IIS utilizzando la procedura di configurazione guidata della sincronizzazione Web  
  
1.  Nel computer che esegue IIS avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  Connettersi al server di pubblicazione e quindi espandere il nodo del server.  
  
3.  Espandere il **pubblicazioni locali** cartella, fare doppio clic su pubblicazione e quindi fare clic su **Configura sincronizzazione Web**.  
  
4.  Nella configurazione guidata sincronizzazione Web, nel **tipo di sottoscrittore** selezionare **SQL Server**.  
  
5.  Nel **Server Web** pagina:  
  
    1.  Selezionare l'istanza di IIS che eseguirà la sincronizzazione delle sottoscrizioni.  
  
    2.  Selezionare **creare una nuova directory virtuale**.  
  
    3.  Nel riquadro inferiore della pagina, espandere l'istanza di IIS, espandere **siti Web**, quindi fare clic su **sito Web predefinito**.  
  
6.  Nel **informazioni Directory virtuale** pagina:  
  
    1.  Nel **Alias** immettere un alias per la directory virtuale.  
  
    2.  Nel **percorso** immettere un percorso della directory virtuale. Ad esempio, se è stato immesso **websync1** nel **Alias** immettere **C:\Inetpub\wwwroot\websync1** nel **percorso** casella. Scegliere **Avanti**.  
  
    3.  In entrambe le finestre di dialogo, fare clic su **Sì**. In questo modo viene specificato che si intende creare una nuova cartella e copiare la DLL ISAPI (Internet Server API) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. .  
  
7.  Nel **accesso autenticato** pagina:  
  
    1.  Assicurarsi che **autenticazione integrata di Windows** e **l'autenticazione del Digest per server di dominio Windows** vengono cancellati.  
  
    2.  Selezionare **l'autenticazione di base**.  
  
    3.  Nel **dominio predefinito** e **Realm** caselle, immettere il dominio del computer che esegue IIS.  
  
8.  Nel **accesso alla Directory** pagina:  
  
    1.  Fare clic su **Aggiungi**, e quindi la **Seleziona utenti o gruppi** finestra di dialogo, aggiungere gli account con cui i sottoscrittori saranno le connessioni a IIS. Questi sono gli account che verranno specificati nella **informazioni sul Server Web** pagina della procedura guidata nuova sottoscrizione o come valore per il [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)*@internet_login* parametro.  
  
9. Nel **accesso alla condivisione Snapshot** pagina, immettere la condivisione snapshot. In questa condivisione vengono impostate le autorizzazioni appropriate affinché i Sottoscrittori possano accedere ai file di snapshot. Per ulteriori informazioni sulle autorizzazioni per la condivisione, vedere [sicurezza della cartella Snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
10. Nel **Completamento procedura guidata** pagina, fare clic su **Fine**.  
  
     In caso di errore, ad esempio un errore di rete durante il tentativo di configurazione di un computer remoto che esegue IIS, verrà eseguito il rollback di tutte le azioni completate e tutte le restanti azioni verranno annullate. Se un'azione completata non può essere annullata, lo stato nella pagina finale della procedura guidata verrà **successo** e mantenuto il commit delle azioni completate.  
  
11. Se nel computer con IIS è in esecuzione una versione a 64 bit di Windows, è necessario copiare replisapi.dll nella directory appropriata:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**. Nel **aprire** immettere **iisreset**, quindi fare clic su **OK**.  
  
    2.  Dopo l'arresto e il riavvio di IIS, copiare il file replisapi.dll da [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi nella directory specificata nel passaggio 6b.  
  
    3.  Fare clic su **avviare**, quindi fare clic su **eseguire**. Nel **aprire** immettere **cmd**, quindi fare clic su **OK**.  
  
    4.  Nella directory specificata al passaggio 6b eseguire il comando seguente:  
  
         **regsvr32 replisapi.dll**  
  
## Configurazione manuale del computer che esegue IIS  
 Per configurare manualmente il computer che esegue IIS, è necessario installare e configurare Listener per la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quindi configurare l'autorizzazione per i Sottoscrittori che si connetteranno a IIS.  
  
#### Per installare e configurare Listener per la replica di SQL Server  
  
1.  Creare una directory di file nel computer che esegue IIS per contenere replisapi.dll. È possibile creare la directory dove si desidera, ma è consigliabile creare la directory di \<*unità*>: \Inetpub directory. Ad esempio, creare la directory \<*unità*>: \Inetpub\SQLReplication\\.  
  
    > [!IMPORTANT]  
    >  È consigliabile creare questa directory in una partizione del file system NTFS anziché in un file system FAT. Quando si utilizza il file system NTFS, è possibile utilizzare le autorizzazioni di tale file system per controllare esattamente gli utenti che possono accedere alla replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Copiare replisapi.dll dalla directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ alla directory di file creata nel passaggio 1.  
  
3.  Registrare replisapi.dll:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**. Nel **aprire** immettere **cmd**, quindi fare clic su **OK**.  
  
    2.  Nella directory creata al passaggio 1 eseguire il comando seguente:  
  
         **regsvr32 replisapi.dll**  
  
4.  Creare un nuovo sito Web per la replica oppure utilizzare un sito esistente. I componenti di replica accederanno al sito Web durante la sincronizzazione. Per ulteriori informazioni sulla creazione di siti Web, vedere la documentazione di IIS.  
  
5.  Creare una directory virtuale in IIS. È consigliabile creare la directory virtuale nel sito Web creato nel passaggio 4 ed eseguirne il mapping alla directory creata nel passaggio 1. Per ulteriori informazioni sulla creazione di directory virtuali, vedere la documentazione di IIS. È consigliabile applicare le massime restrizioni nell'assegnazione delle autorizzazioni per questa directory. È necessario selezionare **lettura** e **Execute** autorizzazioni, ma è possibile deselezionare **eseguire gli script**, **scrivere**, e **Sfoglia** autorizzazioni.  
  
6.  Configurare IIS in modo da consentire l'esecuzione di replisapi.dll. Le autorizzazioni assegnate nel passaggio 4 sono sufficienti per le versioni precedenti di IIS, ma IIS 6.0 richiede l'abilitazione delle estensioni ISAPI (Internet Server API). Per ulteriori informazioni, vedere le sezioni relative alla configurazione di estensioni ISAPI e all'abilitazione e disabilitazione di contenuto dinamico nella documentazione di IIS 6.0.  
  
#### Per configurare l'autenticazione di IIS  
  
-   Quando i Sottoscrittori si connettono a IIS, è necessario che vengano autenticati da IIS affinché possano accedere a risorse e processi. IIS offre tre tipi di autenticazione: anonima, di base e integrata. L'autenticazione può essere applicata all'intero sito Web oppure alla directory virtuale creata.  
  
     È consigliabile utilizzare l'autenticazione di base con SSL. SSL è necessario indipendentemente dal tipo di autenticazione utilizzato. Per ulteriori informazioni sulla configurazione dell'autenticazione, vedere la documentazione di IIS.  
  
## Impostazione delle autorizzazioni per Listener per la replica di SQL Server  
 Quando un Sottoscrittore si connette al computer che esegue IIS, viene autenticato mediante il tipo di autenticazione specificato durante la configurazione di IIS. Dopo l'autenticazione del Sottoscrittore, IIS controlla se il Sottoscrittore è autorizzato a richiamare la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per controllare gli utenti autorizzati a richiamare le replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario impostare le autorizzazioni per replisapi.dll. La corretta configurazione delle autorizzazioni è fondamentale per impedire l'accesso non autorizzato alla replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Per configurare le autorizzazioni minime per l'account utilizzato per l'esecuzione di Listener per la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , completare la procedura seguente. I passaggi nella procedura si applicano a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] che eseguono IIS 6.0.  
  
 Oltre a eseguire la procedura seguente, assicurarsi che gli account di accesso necessari siano inclusi nell'elenco di accesso alla pubblicazione. Per ulteriori informazioni sull'elenco di accesso, vedere [proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md).  
  
#### Per configurare l'account e le autorizzazioni  
  
1.  Creare un account locale nel computer che esegue IIS:  
  
    1.  Fare doppio clic su **risorse del Computer**, quindi fare clic su **Gestisci**.  
  
    2.  In **Gestione Computer**, espandere **utenti e gruppi locali**.  
  
    3.  Fare doppio clic su **utenti**, quindi fare clic su **nuovo utente**.  
  
    4.  Immettere un nome utente e una password complessa.  
  
    5.  Fare clic su **Crea**, quindi fare clic su **Chiudi**.  
  
2.  Aggiungere l'account al gruppo IIS_WPG:  
  
    1.  In **Gestione Computer**, espandere **utenti e gruppi locali**, quindi fare clic su **gruppi**.  
  
    2.  Fare doppio clic su **IIS_WPG**, quindi fare clic su **aggiungere al gruppo**.  
  
    3.  Nel **proprietà-IIS_WPG** la finestra di dialogo, fare clic su **Aggiungi**.  
  
    4.  Nel **Seleziona utenti, computer o gruppi** finestra di dialogo, aggiungere l'account creato nel passaggio 1.  
  
    5.  Assicurarsi che il nome nella **da questo percorso** campo è il nome del computer locale anziché in un dominio. Se il nome non è un computer locale, fare clic su **percorsi**. Nel **percorsi** la finestra di dialogo, selezionare il computer locale e quindi fare clic su **OK**.  
  
    6.  Nel **Seleziona utenti** la finestra di dialogo e **proprietà-IIS_WPG** la finestra di dialogo, fare clic su **OK**.  
  
3.  Concedere all'account le autorizzazioni minime per la cartella contenente replisapi.dll:  
  
    1.  Individuare la cartella creata per replisapi. dll, fare clic sulla cartella e quindi fare clic su **condivisione e sicurezza**.  
  
    2.  Nel **sicurezza** scheda, fare clic su **Aggiungi**.  
  
    3.  Nel **Seleziona utenti, computer o gruppi** finestra di dialogo, aggiungere l'account creato nel passaggio 1.  
  
    4.  Assicurarsi che il nome nella **da questo percorso** campo è il nome del computer locale anziché in un dominio. Se il nome non è un computer locale, fare clic su **percorsi**. Nel **percorsi** la finestra di dialogo, selezionare il computer locale e quindi fare clic su **OK**.  
  
    5.  Assicurarsi che l'account sia concesse soltanto **lettura**, **lettura ed esecuzione**, e **visualizzazione contenuto cartella** le autorizzazioni.  
  
    6.  Selezionare gli utenti o gruppi che non richiedono l'accesso alla directory e quindi fare clic su **rimuovere**.  
  
    7.  Scegliere **OK**.  
  
4.  Creare un pool di applicazioni in **Gestione Internet Information Services (IIS)**:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare **inetmgr**, quindi fare clic su **OK**.  
  
    3.  In **Gestione Internet Information Services (IIS)**, espandere il **computer locale** nodo.  
  
    4.  Fare doppio clic su **pool di applicazioni**, scegliere **New** e quindi fare clic su **Pool di applicazioni**.  
  
    5.  Immettere un nome per il pool nel **ID pool di applicazioni** campo e quindi fare clic su **OK**.  
  
5.  Associare l'account al pool di applicazioni:  
  
    1.  In **Gestione Internet Information Services (IIS)**, espandere il **computer locale** nodo, quindi espandere **pool di applicazioni**.  
  
    2.  Fare doppio clic su pool di applicazioni creato e quindi fare clic su **proprietà**.  
  
    3.  Nel **\< Nomepoolapplicazioni> proprietà** della finestra di dialogo di **identità** fare clic su **configurabile**.  
  
    4.  Nel **nome utente** e **password** campi, immettere l'account e password creati nel passaggio 1.  
  
    5.  Scegliere **OK**.  
  
6.  Associare il pool di applicazioni alla directory virtuale utilizzata per la sincronizzazione Web:  
  
    1.  In **Gestione Internet Information Services (IIS)**, espandere il **computer locale** nodo, quindi espandere **siti Web**.  
  
    2.  Espandere il sito Web che sta utilizzando per la sincronizzazione Web, fare doppio clic su directory virtuale creata per la sincronizzazione Web e quindi fare clic su **proprietà**.  
  
    3.  Nel **Directory virtuale** scheda il **\< nomedirectoryvirtuale> proprietà** nella finestra di dialogo dal **pool di applicazioni** elenco a discesa, selezionare il pool di applicazioni creato nel passaggio 5.  
  
    4.  Scegliere **OK**.  
  
## Test della connessione a replisapi.dll  
 Eseguire la sincronizzazione Web in modalità diagnostica per testare la connessione al computer che esegue IIS e verificare la corretta installazione del certificato SSL (Secure Sockets Layer). Per eseguire la sincronizzazione Web in modalità diagnostica, è necessario disporre dei privilegi di amministratore sul computer che esegue IIS.  
  
#### Per testare la connessione a replisapi.dll  
  
1.  Assicurarsi che le impostazioni per la rete LAN (Local Area Network) nel Sottoscrittore siano corrette:  
  
    1.  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, il **strumenti** menu, fare clic su **Opzioni Internet**.  
  
    2.  Nel **connessioni** scheda, fare clic su **Impostazioni LAN**.  
  
    3.  Se un server proxy non è utilizzato nella rete LAN, deselezionare **rileva automaticamente impostazioni** e **utilizza un server proxy per le connessioni LAN**.  
  
    4.  Se viene utilizzato un server proxy, selezionare **utilizza un server proxy per le connessioni LAN** e **Ignora server proxy per indirizzi locali**.  
  
    5.  Scegliere **OK**.  
  
2.  Nel Sottoscrittore, in Internet Explorer, connettersi al server in modalità diagnostica aggiungendo `?diag` alla fine dell'indirizzo di replisapi.dll. Ad esempio: https://server.domain.com/directory/replisapi.dll? diag.  
  
3.  Se il certificato specificato per IIS non viene riconosciuto dal sistema operativo Windows, il **avviso di sicurezza** viene visualizzata la finestra di dialogo. Questo avviso può essere visualizzato perché il certificato è un certificato di prova o è stato emesso da un'autorità di certificazione non riconosciuta da Windows.  
  
    > [!NOTE]  
    >  Se questa finestra di dialogo non viene visualizzata, verificare che il certificato per il server a cui si accede sia stato aggiunto all'archivio certificati nel Sottoscrittore come certificato attendibile. Per ulteriori informazioni sull'esportazione dei certificati, vedere la documentazione di IIS.  
  
    1.  Nel **avviso di sicurezza** la finestra di dialogo, fare clic su **Visualizza certificato**.  
  
    2.  Nel **certificato** della finestra di dialogo di **Generale** scheda, fare clic su **Installa certificato**.  
  
    3.  Completare l'Importazione guidata certificati, accettando le impostazioni predefinite.  
  
    4.  Nel **avviso di sicurezza** la finestra di dialogo, fare clic su **Sì**.  
  
    5.  Nella finestra di dialogo di conferma di importazione guidata certificati, fare clic su **OK**.  
  
    6.  Chiudi il **certificato** la finestra di dialogo.  
  
    7.  Nel **avviso di sicurezza** la finestra di dialogo, fare clic su **Sì**.  
  
    > [!NOTE]  
    >  I certificati vengono installati per gli utenti. Questo processo deve pertanto essere eseguito per ogni utente che eseguirà la sincronizzazione con IIS.  
  
4.  Nel **connettersi a \< ServerName>** finestra di dialogo, specificare l'account di accesso e la password che verrà utilizzato l'agente di Merge per la connessione a IIS. Queste credenziali verranno inoltre specificate nella Creazione guidata nuova sottoscrizione.  
  
5.  Nella finestra di Internet Explorer denominata **informazioni diagnostica SQL Websync**, verificare che il valore in ogni **stato** colonna nella pagina **successo**.  
  
6.  Assicurarsi che il certificato sia installato correttamente nel Sottoscrittore:  
  
    1.  Chiudere e riaprire Internet Explorer.  
  
    2.  Connettersi al server in modalità diagnostica. Se il certificato sia installato correttamente, il **avviso di sicurezza** non verrà visualizzata la finestra di dialogo. Se la finestra di dialogo viene visualizzata, i tentativi dell'agente di merge di connettersi al computer che esegue IIS avranno esito negativo. È necessario verificare che il certificato per il server a cui si accede sia stato aggiunto all'archivio certificati del Sottoscrittore come certificato attendibile. Per ulteriori informazioni sull'esportazione dei certificati, vedere la documentazione di IIS.  
  
## Vedere anche  
 [Configurazione della sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md)  
  
  