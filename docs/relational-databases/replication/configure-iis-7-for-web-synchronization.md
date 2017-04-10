---
title: "Configurare IIS 7 per la sincronizzazione Web | Microsoft Docs"
ms.custom: ""
ms.date: "09/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurazione del server IIS 7 [replica di SQL Server]"
  - "sincronizzazione Web, server IIS 7"
ms.assetid: c201fe2c-0a76-44e5-a233-05e14cd224a6
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Configurare IIS 7 per la sincronizzazione Web
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le procedure descritte in questo argomento verranno semplificato il processo di configurazione manualmente [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) versione 7 e versioni successive per utilizzare con la sincronizzazione Web per la replica di tipo merge. 
  
 Configurazione di IIS 7 o versione successiva è il primo di tre passaggi necessari per abilitare la sincronizzazione Web.  
  
 Per una panoramica dell'intero processo di configurazione, vedere [Configura sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
> [!IMPORTANT]  
>  Verificare che nell'applicazione venga utilizzato solo [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] o versione successiva e che le versioni precedenti di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] non siano installate sul server IIS. Le versioni precedenti di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] possono causare errori, ad esempio "Formato di messaggio non valido durante la sincronizzazione Web. Verificare che i componenti di replica siano configurati correttamente nel server Web".  
  
 Per utilizzare la sincronizzazione Web, è necessario configurare IIS eseguendo la procedura seguente. Ogni passaggio è descritto in dettaglio in questo argomento.  
  
1.  Installare e configurare il listener per la replica di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer in cui viene eseguito IIS.  
  
2.  Configurare SSL (Secure Sockets Layer). L'utilizzo di SSL è obbligatorio per la comunicazione tra IIS e tutti i Sottoscrittori.  
  
3.  Configurare l'autenticazione IIS.  
  
4.  Configurare un account e impostare le autorizzazioni per il listener per la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Installazione del listener per la replica di SQL Server  

Sincronizzazione Web è supportata in IIS, a partire dalla versione 5.0. Configurare Web sincronizzazione guidata di IIS versione 5 e 6, non è disponibile con IIS versione 7.0 e versioni successive. **A partire da SQL Server 2012, utilizzare il componente di sincronizzazione web sul server IIS, è necessario installare SQL Server con la replica. Può essere l'edizione gratuita di SQL Server Express.**
  
#### Per installare e configurare Listener per la replica di SQL Server  
  
1.  Installare replica di SQL Server in computer che esegue IIS.

2. Creare una nuova directory di file per replisapi.dll nel computer che esegue IIS. È possibile creare la directory dove si desidera, ma è consigliabile creare la directory di \<*unità*>: \Inetpub directory. Ad esempio, creare la directory \<*unità*>: \Inetpub\SQLReplication\\.  
  
3.  Copiare replisapi. dll dalla directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com \ alla directory del file che è stato creato nel passaggio 1.  
  
4.  Registrare replisapi.dll:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**. Nel **aprire** immettere **cmd**, quindi fare clic su **OK**.  
  
    2.  Nella directory creata nel passaggio 1 eseguire il comando riportato di seguito:  
  
         **regsvr32 replisapi.dll**  
  
5.  Creare un nuovo sito Web per la replica oppure utilizzare un sito esistente. I componenti di replica accederanno al sito Web durante la sincronizzazione. Nelle procedure di questo argomento si presuppone l'utilizzo del sito Web predefinito. Per ulteriori informazioni sulla creazione di siti Web, vedere la documentazione di IIS.  
  
6.  Creare una directory virtuale in IIS. È consigliabile creare la directory virtuale nel sito Web creato nel passaggio 4 ed eseguirne il mapping alla directory creata nel passaggio 1. È consigliabile applicare le massime restrizioni nell'assegnazione delle autorizzazioni per questa directory. È necessario selezionare almeno **lettura** e **Execute** autorizzazioni.  
  
    1.  In **Gestione Internet Information Services (IIS)**, nel **connessioni** riquadro, fare doppio clic su **sito Web predefinito**, quindi selezionare **Aggiungi Directory virtuale**.  
  
    2.  Per **Alias**, immettere **SQLReplication**.  
  
    3.  Per **percorso fisico**, immettere **\< unità>: \Inetpub\SQLReplication\\**, quindi fare clic su **OK**.  
  
7.  Configurare IIS in modo da consentire l'esecuzione di replisapi.dll.  
  
    1.  In **Gestione Internet Information Services (IIS)**, fare clic su **sito Web predefinito**.  
  
    2.  Nel riquadro centrale, fare clic su **Handler Mappings**.  
  
    3.  Nel **azioni** riquadro, fare clic su **Aggiungi Mapping moduli**.  
  
    4.  Per **richiesta** percorso, immettere **replisapi. dll**.  
  
    5.  Dal **modulo** elenco a discesa, selezionare **modulo IsapiModule**.  
  
    6.  Per **eseguibile**, immettere **\< unità>: \Inetpub\SQLReplication\replisapi.dll**.  
  
    7.  Per **nome**, immettere **Replisapi**.  
  
    8.  Fare clic sul **restrizioni richieste** scegliere il **accesso** scheda e quindi fare clic su **Execute**.  
  
    9. Fare clic su **OK** per chiudere la **restrizioni richieste** la finestra di dialogo e quindi fare clic su **OK** per chiudere la **Aggiungi Mapping moduli** la finestra di dialogo. Quando viene chiesto di consentire l'estensione ISAPI, fare clic su **Sì** per aggiungere l'estensione.  
  
    10. Verificare che replisapi. dll sia elencato sotto il **Enabled** Mapping gestori. Se si trova nel **disabilitato** pulsante destro del mouse sulla voce Replisapi e quindi fare clic **Modifica autorizzazioni funzionalità**. Controllare il **Execute** casella e quindi fare clic su **OK**.  
  
## Configurazione dell'autenticazione IIS  
 Quando i computer Sottoscrittori si connettono a IIS, è necessario che vengano autenticati da IIS per poter accedere a risorse e processi. L'autenticazione può essere applicata all'intero sito Web oppure alla directory virtuale creata.  
  
 È consigliabile utilizzare l'autenticazione di base con SSL. SSL è necessario indipendentemente dal tipo di autenticazione utilizzato.  
  
 È consigliabile utilizzare l'autenticazione di base con SSL. SSL è necessario indipendentemente dal tipo di autenticazione utilizzato.  
  
#### Per configurare l'autenticazione IIS  
  
1.  In **Gestione Internet Information Services (IIS)**, fare clic su **sito Web predefinito**.  
  
2.  Nel riquadro centrale fare doppio clic su **autenticazione**.  
  
3.  Fare clic con il pulsante destro del mouse su Autenticazione anonima, quindi scegliere Disabilita.  
  
4.  Fare clic con il pulsante destro del mouse su Autenticazione di base, quindi scegliere Abilita.  
  
## Configurazione di SSL (Secure Sockets Layer)  
 Per configurare SSL, specificare un certificato che verrà utilizzato dal computer che esegue IIS. La sincronizzazione Web per la replica di tipo merge supporta l'utilizzo di certificati server, ma non di certificati client. Per configurare IIS per la distribuzione, è innanzitutto necessario ottenere un certificato da un'autorità di certificazione. Per ulteriori informazioni sui certificati, vedere la documentazione di IIS.  
  
 Dopo l'installazione del certificato, è necessario associare il certificato al sito Web utilizzato nella sincronizzazione Web. Per lo sviluppo e i test, è possibile specificare un certificato autofirmato. Con IIS 7 è possibile creare un certificato e registrarlo nel computer.  
  
 La differenza tra la distribuzione per la produzione e le procedure fornite in questo argomento è data dal fatto che nei test di produzione e pre-produzione si utilizza un certificato rilasciato da una CA anziché un certificato autofirmato.  
  
> [!IMPORTANT]  
>  Non è consigliabile utilizzare un certificato autofirmato per un'installazione di produzione. I certificati autofirmati non sono sicuri. Utilizzare tali certificati solo ai fini di sviluppo e test.  
  
 Per configurare SSL, verranno eseguiti i passaggi riportati di seguito:  
  
1.  Configurare il sito Web per richiedere SSL e ignorare i certificati client.  
  
2.  Ottenere un certificato da una CA o creare un certificato autofirmato.  
  
3.  Associare il certificato al sito Web per la replica.  
  
#### Per richiedere la sicurezza SSL per un sito Web  
  
1.  In **Gestione Internet Information Services (IIS)**, espandere il nodo del server locale e quindi fare clic sul **sito Web predefinito** (o sul sito di sincronizzazione Web se è diverso dal sito Web predefinito).  
  
2.  Nel riquadro centrale fare doppio clic su **impostazioni SSL**.  
  
3.  Controllare il **Richiedi SSL** (opzione). In **i certificati Client**, verificare che il **Ignora** pulsante è selezionato.  
  
#### Per creare un certificato autofirmato per i test  
  
1.  In **Gestione Internet Information Services (IIS)**, fare clic sul nodo del server locale e quindi nel riquadro centrale, fare doppio clic su **certificati Server**.  
  
2.  Nel **azioni** riquadro, fare clic su **Crea certificato autofirmato**.  
  
3.  Nel **Crea certificato autofirmato** nella finestra di dialogo immettere un nome per il certificato e quindi fare clic su **OK**.  
  
###### Per associare un certificato a un sito Web  
  
1.  Nel **connessioni** riquadro, fare clic sul **sito Web predefinito** (o sul sito di sincronizzazione Web, se è diverso dal sito Web predefinito).  
  
2.  Nel **azioni** riquadro, fare clic su **associazioni**, quindi fare clic su **Aggiungi**. Il **Aggiungi Binding sito** verrà visualizzata la finestra di dialogo.  
  
3.  Dal **tipo** elenco a discesa, selezionare **https**. Lasciare le impostazioni predefinite per **l'indirizzo IP** e **porta**.  
  
4.  Dal **certificato SSL** -elenco a discesa, selezionare il certificato creato in "Per creare un certificato autofirmato per il test," fare clic su **OK**, quindi fare clic su **Chiudi**.  
  
###### Per testare il certificato  
  
1.  In **Gestione Internet Information Services (IIS)**, fare clic su **sito Web predefinito.**  
  
2.  Dal **azioni** riquadro, fare clic su **Sfoglia \*: 443(https)**.  
  
3.  Verrà aperto Internet Explorer e verrà visualizzato il messaggio "Si è verificato un problema con il certificato di sicurezza del sito Web". Questo avviso suggerisce che il certificato associato non è stato rilasciato da una CA riconosciuta e potrebbe non essere attendibile. Si tratta di un avviso previsto, quindi fare clic su **con il sito Web (scelta non consigliato)**.  
  
4.  Se viene richiesto di **Connetti a localhost**, immettere un nome utente e password per continuare. Dovrebbe venire visualizzata la pagina predefinita del sito Web.  
  
## Impostazione delle autorizzazioni per Listener per la replica di SQL Server  
 Quando un computer Sottoscrittore si connette al computer che esegue IIS, viene autenticato mediante il tipo di autenticazione specificato durante la configurazione di IIS. Dopo l'autenticazione del Sottoscrittore, in IIS viene controllato se il Sottoscrittore è autorizzato a richiamare la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per controllare gli utenti autorizzati a richiamare le replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario impostare le autorizzazioni per replisapi.dll. La corretta configurazione delle autorizzazioni è fondamentale per impedire l'accesso non autorizzato alla replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Per configurare le autorizzazioni minime per l'account utilizzato per l'esecuzione di Listener per la replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , completare la procedura seguente. I passaggi della procedura seguente sono validi per [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008 con IIS 7.0.  
  
 Oltre a eseguire la procedura seguente, assicurarsi che gli account di accesso necessari siano inclusi nell'elenco di accesso alla pubblicazione. Per ulteriori informazioni sull'elenco di accesso, vedere [proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md).  
  
 **Importante** l'account creato in questa sezione è l'account che si connetterà al server di pubblicazione e server di distribuzione durante la sincronizzazione. È necessario aggiungere questo account come account di accesso SQL nel server di distribuzione e di pubblicazione.  
  
 L'account utilizzato per il listener per la replica di SQL Server deve disporre di autorizzazioni come descritto nell'argomento Sicurezza dell'agente di merge, nella sezione "Connettersi al server di pubblicazione o al database di distribuzione".  
  
 In breve è necessario che l'account:  
  
-   sia membro dell'elenco di accesso alla pubblicazione;  
  
-   sia sottoposto a mapping a un account di accesso associato a un utente nel database di pubblicazione;  
  
-   sia sottoposto a mapping a un account di accesso associato a un utente nel database di distribuzione;  
  
-   disponga delle autorizzazioni di lettura per la condivisione snapshot.  
  
#### Per configurare l'account e le autorizzazioni  
  
1.  Creare un account locale nel computer che esegue IIS:  
  
    1.  Aprire **Server Manager**. Dal menu Start, fare doppio clic su **Computer**, quindi fare clic su **Gestisci**.  
  
    2.  In **Server Manager**, espandere **configurazione**, quindi espandere **utenti e gruppi locali**.  
  
    3.  Fare doppio clic su **utenti**, quindi fare clic su **nuovo utente**.  
  
    4.  Immettere un nome utente e una password complessa. Deselezionare **Cambiamento obbligatorio password all'accesso successivo**.  
  
    5.  Fare clic su **Crea**, quindi fare clic su **Chiudi**.  
  
2.  Aggiungere l'account al gruppo IIS_IUSRS:  
  
    1.  In **Server Manager**, espandere **configurazione**, espandere **utenti e gruppi locali**, quindi fare clic su **gruppi**.  
  
    2.  Fare doppio clic su **IIS_IUSRS**, quindi fare clic su **aggiungere al gruppo**.  
  
    3.  Nel **proprietà-IIS_IUSRS** la finestra di dialogo, fare clic su **Aggiungi**.  
  
    4.  Nel **Seleziona utenti, computer o gruppi** finestra di dialogo, aggiungere l'account creato nel passaggio 1.  
  
    5.  Verificare che **da questo percorso** Visualizza il nome del computer locale (non a un dominio). Se questo campo non viene visualizzato il nome del computer locale, fare clic su **percorsi**. Nel **percorsi** la finestra di dialogo, selezionare il computer locale e quindi fare clic su **OK**.  
  
    6.  Nel **Seleziona utenti** la finestra di dialogo e **proprietà-IIS_IUSRS** la finestra di dialogo, fare clic su**OK**.  
  
3.  Concedere all'account le autorizzazioni minime per la cartella contenente replisapi.dll:  
  
    1.  In Esplora risorse, fare clic sulla cartella creata per replisapi. dll e quindi fare clic su **proprietà**.  
  
    2.  Nella scheda **Sicurezza** fare clic su **Modifica**.  
  
    3.  Nel **le autorizzazioni per \< nomecartella>** la finestra di dialogo, fare clic su **Aggiungi** per aggiungere l'account creato nel passaggio 1.  
  
    4.  Verificare che **da questo percorso** Visualizza il nome del computer locale (non a un dominio). Se questo campo non viene visualizzato il nome del computer locale, fare clic su **percorsi**. Nel **percorsi** la finestra di dialogo, selezionare il computer locale e quindi fare clic su **OK**.  
  
    5.  Verificare che l'account sia concesse soltanto **lettura**, **lettura ed esecuzione**, e **visualizzazione contenuto cartella** le autorizzazioni.  
  
    6.  Selezionare tutti gli utenti o gruppi che non richiedono l'accesso alla directory, fare clic su **rimuovere**, quindi fare clic su **OK**.  
  
4.  Creare un pool di applicazioni in **Gestione Internet Information Services (IIS)**:  
  
    1.  In **Gestione Internet Information Services (IIS)**, nel **connessioni** riquadro, espandere il nodo del server locale.  
  
    2.  Fare doppio clic su **pool di applicazioni**, quindi fare clic su **Aggiungi Pool di applicazioni**.  
  
    3.  Immettere un nome per il pool di applicazioni, lasciare i valori predefiniti nei campi rimanenti e quindi fare clic su **OK**.  
  
    > [!NOTE]  
    >  Se si prevede di utilizzare più di due client di sincronizzazione simultanei, è necessario creare un Web garden. Per ulteriori informazioni, vedere "Creazione di un Web Garden" in [Configura sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
5.  Associare l'account al pool di applicazioni:  
  
    1.  In **Gestione Internet Information Services (IIS)**, espandere il nodo del server locale e quindi fare clic su **pool di applicazioni**.  
  
    2.  Fare doppio clic su pool di applicazioni creato e quindi fare clic su **impostazioni predefinite Pool di applicazioni**.  
  
    3.  Nel **predefinite Pool di applicazioni** la finestra di dialogo, scorrere fino a visualizzare il **modello di processo** sezione e quindi fare clic su di **identità** campo.  
  
    4.  Fare clic sul pulsante con puntini di sospensione sul lato destro di **identità** riga.  
  
    5.  Fare clic sui **Account personalizzato** pulsante di opzione e quindi fare clic su **impostare**.  
  
    6.  Nel **nome utente** e **Password** campi, immettere l'account e password creati nel passaggio 1 e quindi fare clic su **OK**.  
  
    7.  Fare clic su **OK** per chiudere la **identità Pool di applicazioni** la finestra di dialogo e quindi fare clic su **OK** per chiudere la **predefinite Pool di applicazioni**la finestra di dialogo.  
  
6.  Associare il pool di applicazioni al sito Web per la replica:  
  
    1.  In **Gestione Internet Information Services (IIS)**, espandere il nodo del server locale e quindi fare clic sul **sito Web predefinito** (o sul sito di sincronizzazione Web se è diverso dal sito Web predefinito).  
  
    2.  Nel **azioni** riquadro, in **Gestisci sito Web**, fare clic su **Impostazioni avanzate**.  
  
    3.  Nel **Impostazioni avanzate** la finestra di dialogo, fare clic sul pulsante con puntini di sospensione a destra del **Pool di applicazioni**.  
  
    4.  Dal **pool di applicazioni** elenco a discesa, selezionare il pool di applicazioni creato nel passaggio 4 e quindi fare clic su **OK**.  
  
    5.  Fare clic su **OK** per chiudere impostazioni avanzate.  
  
## Test della connessione a replisapi.dll  
 Eseguire la sincronizzazione Web in modalità diagnostica per testare la connessione al computer che esegue IIS e verificare la corretta installazione del certificato SSL (Secure Sockets Layer). Per eseguire la sincronizzazione Web in modalità diagnostica, è necessario disporre dei privilegi di amministratore sul computer che esegue IIS.  
  
#### Per testare la connessione a replisapi.dll  
  
1.  Assicurarsi che le impostazioni per la rete LAN (Local Area Network) nel Sottoscrittore siano corrette:  
  
    1.  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, il **strumenti** menu, fare clic su **Opzioni Internet**.  
  
    2.  Nel **connessioni** scheda, fare clic su **Impostazioni LAN**.  
  
    3.  Se un server proxy non è utilizzato nella rete LAN, deselezionare **rileva automaticamente impostazioni** e **utilizza un server proxy per le connessioni LAN**.  
  
    4.  Se viene utilizzato un server proxy, fare clic su **utilizza un server proxy per le connessioni LAN** e **Ignora server proxy per indirizzi locali**, quindi fare clic su **OK**.  
  
2.  Nel Sottoscrittore, in Internet Explorer, connettersi al server in modalità diagnostica aggiungendo `?diag` alla fine dell'indirizzo di replisapi.dll. Ad esempio: **https://server.domain.com/directory/replisapi.dll?diag**.  
  
    > [!NOTE]  
    >  Nell'esempio precedente, **server.dominio.com** deve essere sostituito con l'esatto **rilasciato a** nome sotto il **certificati Server** section in Gestione IIS.  
  
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
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)   
 [Configurazione della sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md)  
  
  