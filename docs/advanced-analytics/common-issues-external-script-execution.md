---
title: Problemi comuni con l'esecuzione dello script esterno in SQL Server | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 10/11/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4f515ba26c4eeae70eaf9244c0eaedaa954954b4
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="common-issues-with-external-script-execution-in-sql-server"></a>Problemi comuni con l'esecuzione dello script esterno in SQL Server

In questo articolo contiene un elenco di problemi noti e i problemi comuni relativi all'esecuzione di codice R o Python in SQL Server.

Prima di iniziare, è consigliabile raccogliere alcune informazioni relative al sistema. Per ulteriori informazioni, vedere [raccolta dei dati per la risoluzione dei problemi](data-collection-ml-troubleshooting-process.md).

Inoltre, esaminare l'elenco dei problemi comuni che sono specifici per la configurazione iniziale o configurazione: [il programma di installazione e aggiornamento domande frequenti su](r/upgrade-and-installation-faq-sql-server-r-services.md).

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="launchpad-issues"></a>Problemi di avvio

Il servizio Launchpad attendibile di SQL Server gestisce l'esecuzione di script esterni e la comunicazione con altri runtime esterni, Python o R. Più possono impedire l'avvio di avvio, inclusi i problemi di configurazione o le modifiche o i protocolli di rete mancante.

Come parte del processo di risoluzione dei problemi, iniziare da rispondere alle domande seguenti:

- Ha Launchpad sempre esito negativo per l'esecuzione o arresti utilizzo?
- Quali account del servizio esegue in finestra di avvio?
- Quali sono i diritti utente dispone dell'account del servizio Launchpad?

### <a name="determine-whether-launchpad-is-running"></a>Determinare se finestra di avvio è in esecuzione

1. Aprire il **servizi** pannello (Services.msc). In alternativa, dalla riga di comando, digitare **SQLServerManager13.msc** o **SQLServerManager14.msc** per aprire [Gestione configurazione SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Prendere nota dell'account del servizio in esecuzione nella finestra di avvio. Ogni istanza in cui è abilitato R o Python debba avere la propria istanza del servizio Launchpad. Ad esempio, il servizio per un'istanza denominata potrebbe essere simile al seguente _MSSQLLaunchpad$ InstanceName_.

3. Se il servizio viene arrestato, riavviarlo. Scegliere il riavvio, se sono presenti eventuali problemi di configurazione, un messaggio viene pubblicato nel registro eventi di sistema e viene nuovamente arrestato il servizio. Controllare il registro eventi di sistema per informazioni dettagliate sui motivi per cui il servizio è stato arrestato.

4. Esaminare il contenuto di RSetup.log e assicurarsi che non siano presenti errori nel programma di installazione. Ad esempio, il messaggio *chiusura con codice 0* indica l'errore del servizio di avvio.

5. Per cercare altri errori, esaminare il contenuto di rlauncher.log.

### <a name="check-the-launchpad-service-account"></a>Verificare l'account del servizio Launchpad

L'account del servizio predefinito potrebbe essere "NT Service\$SQL2016" o "NT Service\$SQL2017". La parte finale potrebbe variare a seconda del nome dell'istanza SQL.

Il servizio Launchpad (Launchpad.exe) viene eseguito utilizzando un account di servizio con privilegi limitati. Per avviare R e Python e comunicare con l'istanza del database, tuttavia, l'account del servizio Launchpad richiede i diritti utente di seguenti:

- Accesso come servizio (SeServiceLogonRight)
- Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)
- Ignorare controllo incrociato (SeChangeNotifyPrivilege)
- Regolazione limite risorse memoria per un processo (SeIncreaseQuotaSizePrivilege)

Per informazioni su questi diritti, vedere la sezione "diritti e privilegi di Windows" in [Windows configurare account del servizio e autorizzazioni](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Se si ha familiarità con l'utilizzo dello strumento di supporto diagnostica piattaforma SDP () per la diagnostica di SQL Server, è possibile utilizzare SDP per esaminare il file di output con il nome MachineName_UserRights.txt.

### <a name="review-launchpad-requirements"></a>Rivedere i requisiti di finestra di avvio

Uno dei numerosi problemi possono impedire l'avvio finestra di avvio. Il servizio Launchpad potrebbe avviare e arrestare o con un timeout di connessione potrebbe smettere di arresto anomalo del sistema o il servizio. In questi casi, il sistema è in genere stato modificato o configurato in modo che non è possibile eseguire l'avvio.

#### <a name="determine-whether-8dot3-notation-is-enabled"></a>Determinare se è abilitata la notazione 8dot3

Per compatibilità con R, SQL Server 2016 R Services (In-Database) è richiesto l'unità in cui la funzionalità viene installata per supportare la creazione di nomi file brevi usando *notazione 8dot3*. Viene chiamato anche un nome 8.3 file un *nome file breve*, e viene utilizzato per la compatibilità con le versioni precedenti di Microsoft Windows o un'alternativa ai nomi file lunghi.

Se il volume in cui si installa R non supporta nomi di file brevi, i processi che avviano R da SQL Server potrebbero non essere in grado di individuare l'eseguibile corretto e finestra di avvio non verrà avviato.

In alternativa, è possibile abilitare la notazione 8dot3 nel volume in cui è installato SQL Server e in cui è installato R Services. È quindi necessario specificare il nome breve per la directory di lavoro nel file di configurazione di R Services.

1. Per abilitare la notazione 8dot3, eseguire l'utilità fsutil con il *8dot3name* argomento come descritto qui: [8dot3name fsutil](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Dopo aver abilitata la notazione 8dot3, aprire il file RLauncher.config e prendere nota della proprietà di `WORKING_DIRECTORY`. Per informazioni su come trovare questo file, vedere [raccolta dei dati per la risoluzione dei problemi di Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Usare l'utilità fsutil con il *file* argomento per specificare un percorso di file breve per la cartella specificata nella WORKING_DIRECTORY.

4. Modificare il file di configurazione per specificare la directory di lavoro stesso immesso nella proprietà WORKING_DIRECTORY. In alternativa, è possibile specificare un'altra directory di lavoro e scegliere un percorso esistente che già è compatibile con la notazione 8dot3.

> [!NOTE] 
> Questa limitazione è stata rimossa in una versione successiva. Se si riscontra questo problema, installare uno dei valori seguenti:
> * SQL Server 2016 SP1 e CU1: [aggiornamento cumulativo 1 per SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, l'aggiornamento cumulativo 3 e ciò [hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), disponibile su richiesta.

#### <a name="the-user-group-for-launchpad-cannot-log-on-locally"></a>Il gruppo di utenti per la finestra di avvio non può accedere localmente

Durante l'installazione di servizi di Machine Learning, SQL Server crea il gruppo di utenti Windows **SQLRUserGroup** e quindi viene eseguito il provisioning, con tutti i diritti necessari per la finestra di avvio per connettersi a SQL Server ed eseguire processi di script esterni. Se questo gruppo di utenti è abilitato, è anche possibile eseguire script Python.

Tuttavia, nelle organizzazioni in cui vengono applicati i criteri di sicurezza più restrittivi, potrebbero avere i diritti necessari per questo gruppo sia stato rimosso manualmente o potrebbe essere revocati automaticamente dai criteri. Se sono stati rimossi i diritti, finestra di avvio non può più connettersi a SQL Server e SQL Server non è possibile chiamare il runtime esterno.

Per correggere il problema, assicurarsi che il gruppo **SQLRUserGroup** abbia il diritto di sistema **Consenti accesso locale**.

Per ulteriori informazioni, vedere [Windows configurare account del servizio e autorizzazioni](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

#### <a name="improper-setup-leading-to-mismatched-dlls"></a>Programma di installazione non corretta iniziali per le DLL non corrispondenti

Se si installa il motore di database con altre funzionalità, patch, il server e quindi aggiunta la funzionalità di Machine Learning usando il supporto originale, la versione errata di componenti di Machine Learning potrebbe essere installata. Quando Launchpad rileva una mancata corrispondenza di versione, arresta e crea un file di dump.

Per evitare questo problema, assicurarsi di installare le nuove funzionalità a livello di patch stesso come istanza del server.

**Il modo corretto per l'aggiornamento:**

1. Installare SQL Server 2016 senza R Services.
2. Eseguire l'aggiornamento di SQL Server 2016 aggiornamento cumulativo 2.
3. Installare R Services (In-Database) utilizzando il supporto RTM.

**Il modo corretto per l'aggiornamento:**

1. Installare SQL Server 2016 senza R Services.
2. Aggiornare SQL Server 2016 a livello di patch desiderato. Ad esempio, installare Service Pack 1 e quindi l'aggiornamento cumulativo 2.
3. Per aggiungere la funzionalità a livello di patch corretto, eseguire nuovamente l'installazione di SP1 e CU2 e quindi scegliere R Services (In-Database). 

#### <a name="check-whether-a-user-has-rights-to-run-external-scripts"></a>Controllare se un utente dispone di diritti per eseguire gli script esterni

Anche se Launchpad è configurato correttamente, restituisce un errore se l'utente non dispone dell'autorizzazione per eseguire gli script R o Python.

Se è installato SQL Server come amministratore di database o il proprietario del database, questa autorizzazione sono concesse automaticamente. Tuttavia, altri utenti in genere sono più di autorizzazioni limitate. Se si tenta di eseguire uno script R, ricevono un errore di avvio.

Per risolvere il problema, in SQL Server Management Studio, un amministratore della sicurezza può modificare l'account di accesso SQL o un account utente di Windows eseguendo lo script seguente:

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Per ulteriori informazioni, vedere [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

### <a name="common-launchpad-errors"></a>Errori più comuni di finestra di avvio

Questa sezione elenca i messaggi di errore più comuni restituiti dalla finestra di avvio.

#### <a name="error-unable-to-launch-runtime-for-r-script"></a>Errore: *non è possibile avviare il runtime per lo script R*

Se il gruppo di Windows per gli utenti di R (utilizzato anche per Python) non è possibile accedere all'istanza che esegue servizi di R, verranno visualizzati gli errori seguenti:

- Errori generati quando si tenta di eseguire gli script R:

    * *Non è stato possibile avviare il runtime per lo script 'R'. Verificare la configurazione del runtime di 'R'.*

    * *Si è verificato un errore dello script esterno. Non è stato possibile avviare il runtime.*

- Gli errori generati dal [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] servizio:

    * *Failed to initialize the launcher RLauncher.dll*

    * *No launcher dlls were registered!*

    * *I log di sicurezza indicano che l'account del servizio NT non è riuscito per l'accesso*

Per informazioni su come concedere al gruppo utente le autorizzazioni necessarie, vedere [configurare SQL Server R Services](r/set-up-sql-server-r-services-in-database.md).

> [!NOTE]
> Questa limitazione non si applica se si usano account di accesso SQL per eseguire script R da una workstation remota.

#### <a name="error-logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>Errore: *errore durante l'accesso: l'utente non dispone del tipo di accesso*

Per impostazione predefinita, [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] utilizza il seguente account di avvio: `NT Service\MSSQLLaunchpad`. L'account è configurato per [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] il programma di installazione di tutte le autorizzazioni necessarie.

Se si assegna un account diverso per una finestra di avvio o di destra viene rimosso da un criterio nel computer SQL Server, l'account potrebbe non disporre delle autorizzazioni necessarie e si potrebbe essere visualizzato questo errore:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Errore durante l'accesso. L'utente non ha ottenuto il tipo di accesso richiesto a questo computer.*

Per concedere le autorizzazioni necessarie per il nuovo account di servizio, utilizzare l'applicazione di criteri di sicurezza locali e aggiornare le autorizzazioni per l'account da includere le autorizzazioni seguenti:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

#### <a name="error-unable-to-communicate-with-the-launchpad-service"></a>Errore: *Impossibile comunicare con il servizio Launchpad*

Se è stato installato e attivato quindi l'apprendimento, ma questo errore si verifica quando si tenta di eseguire uno script R o Python, il servizio Launchpad per l'istanza potrebbe siano in esecuzione.

1. Dal prompt dei comandi di Windows aprire Gestione configurazione SQL Server. Per altre informazioni, vedere [Gestione configurazione SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Finestra di avvio di SQL Server per l'istanza e quindi scegliere **proprietà**.

3. Selezionare il **servizio** scheda e quindi verificare che il servizio sia in esecuzione. Se non è in esecuzione, modificare il **modalità di avvio** a **automatica**, quindi selezionare **applica**.

4. Il riavvio del servizio in genere consente di correggere il problema, in modo che sia possibile eseguire gli script di machine learning. Se il riavvio non risolve il problema, si noti il percorso e gli argomenti di **percorso binario** , proprietà ed eseguire le operazioni seguenti:

    A. Esaminare i file con estensione config dell'utilità di avvio e verificare che la directory di lavoro sia valida.

    B. Verificare che il gruppo di Windows che viene utilizzato dalla finestra di avvio è possibile connettersi all'istanza di SQL Server, come descritto nel [precedente sezione](#bkmk_LaunchpadTS).

    c. Se si modifica una qualsiasi delle proprietà del servizio, riavviare il servizio Launchpad.

#### <a name="error-fatal-error-creation-of-tmpfile-failed"></a>Errore: *creazione di un errore irreversibile del tmpFile non riuscita*

In questo scenario, è stato installato correttamente le funzionalità di machine learning e finestra di avvio è in esecuzione. Si tenta di eseguire il codice R o Python semplice, ma Launchpad genera un errore simile al seguente: 

>*Impossibile comunicare con il runtime per lo script R. Verificare i requisiti del runtime di R.*

Allo stesso tempo, il runtime dello script esterno scrive il messaggio seguente come parte del messaggio STDERR: 

>*Errore irreversibile: creazione di tmpfile non riuscita.*

Questo errore indica che l'account di avvio sta tentando di utilizzare non dispone dell'autorizzazione per accedere al database. Questa situazione può verificarsi quando vengono implementati i criteri di sicurezza rigidi. Per determinare se questo è il caso, esaminare i registri di SQL Server e controllare per vedere se l'account MSSQLSERVER01 negato all'account di accesso. Viene fornite le stesse informazioni nei registri di specifiche di R\_servizi o PYTHON\_servizi. Cercare ExtLaunchError.log.

Per impostazione predefinita, 20 account sono impostato e associato al processo Launchpad.exe, con i nomi MSSQLSERVER01 tramite MSSQLSERVER20. Se si apportano un uso massiccio di R o Python, è possibile aumentare il numero di account.

Per risolvere il problema, verificare che il gruppo abbia *Consenti accesso locale* delle autorizzazioni per l'istanza locale in cui le funzionalità di machine learning state installate e abilitate. In alcuni ambienti, questo livello di autorizzazione potrebbe richiedere un'eccezione dell'oggetto Criteri di gruppo dell'amministratore di rete.

## <a name="r-script-issues"></a>Problemi di script R

In questa sezione contiene alcuni problemi comuni che sono specifici per l'esecuzione di script R e gli errori di script R. L'elenco non è completo, perché sono presenti numerosi pacchetti R e gli errori potrebbero essere diversi tra versioni diverse dello stesso pacchetto R. È consigliabile che la registrazione di errori di script R nella [forum di Microsoft R Server](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR), che supporta di machine learning componenti utilizzati in Machine Learning servizi con Python, il Client R Microsoft e Microsoft R di R Services (In-Database) Server.

### <a name="multiple-r-instances-on-the-same-computer"></a>Più istanze di R nello stesso computer

Può essere più facile trovare autonomamente con più distribuzioni di R nello stesso computer, nonché di più copie dello stesso pacchetto R in diverse versioni. Ad esempio, se si installa Machine Learning Server (Standalone) e Machine Learning Services (In-Database), i programmi di installazione creare versioni distinte delle librerie R. 

Tale funzionalità diventa un problema quando si tenta di eseguire uno script dalla riga di comando e non si è certi le librerie in uso. In alternativa, è possibile installare un pacchetto per la libreria non corretta e quindi in un secondo momento chiedersi perché non è possibile trovare il pacchetto da SQL Server.

+ Evitare l'uso diretto di librerie R e strumenti che vengono installati per l'utilizzo dell'istanza di SQL Server, tranne in alcuni casi, ad esempio la risoluzione dei problemi o l'installazione di nuovi pacchetti. 
+ Se è necessario utilizzare uno strumento da riga di comando di R, è possibile installare [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client). 
+ SQL Server sono disponibili nel database Gestione di pacchetti R. Questo è il modo più semplice per creare librerie del pacchetto R che possono essere condivisi tra gli utenti. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](r/r-package-management-for-sql-server-r-services.md).

### <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Non deselezionare l'area di lavoro durante l'esecuzione in un contesto di calcolo SQL R

Anche se l'area di lavoro di cancellazione è comune quando si lavora nella console di R, può avere conseguenze impreviste in un database SQL di contesto di calcolo.

`revoScriptConnection`è un oggetto nell'area di lavoro R che contiene informazioni su una sessione R che viene chiamata da SQL Server. Tuttavia, se il codice R include un comando per cancellare l'area di lavoro (ad esempio `rm(list=ls())`), tutte le informazioni sulla sessione e altri oggetti nell'area di lavoro R vengano deselezionate anche.

In alternativa, evitare di cancellazione indiscriminata di variabili e altri oggetti durante l'esecuzione R in SQL Server. È possibile eliminare variabili specifiche tramite la **rimuovere** funzione:

```R
remove('name1', 'name2', ...)
```

Se sono presenti più variabili da eliminare, è consigliabile salvare i nomi delle variabili temporanee per un elenco e quindi eseguire periodicamente operazioni di garbage collection nell'elenco.

### <a name="implied-authentication-for-remote-execution-via-odbc"></a>Autenticazione implicita per l'esecuzione remota tramite ODBC

Se ci si connette a di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dei comandi di computer per l'esecuzione di R usando il **RevoScaleR** funzioni, è possibile che venga visualizzato un errore quando si utilizzano chiamate ODBC di scrittura dei dati al server. Questo errore si verifica solo quando si utilizza l'autenticazione di Windows.

Il motivo è che gli account di lavoro che vengono creati per R Services non dispone dell'autorizzazione per connettersi al server. Pertanto, chiamate ODBC non possono essere eseguite per conto dell'utente. Il problema non viene eseguito con l'account di accesso SQL in quanto, con l'account di accesso SQL, le credenziali vengono passate in modo esplicito dal client R per l'istanza di SQL Server e quindi per ODBC. Tuttavia, utilizzando l'account di accesso SQL è anche meno sicura rispetto all'utilizzo di autenticazione di Windows.

Per abilitare le credenziali di Windows deve essere passato in modo sicuro da uno script che ha avviato in modalità remota, SQL Server deve emulare le credenziali. Questo processo è detto _autenticazione implicita_. Per ottenere questo risultato, il lavoro che eseguono gli script R o Python nel computer SQL Server devono disporre delle autorizzazioni corrette.

1. Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] come amministratore nell'istanza in cui si desidera eseguire il codice R.

2. Eseguire lo script seguente. Assicurarsi di modificare il nome del gruppo utente, se è stato modificato il valore predefinito e i nomi di computer e istanza.

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

### <a name="the-r-script-works-outside-of-t-sql-but-not-in-a-stored-procedure"></a>Lo script R funziona all'esterno di T-SQL, ma non in una stored procedure

Prima di wrapping del codice R in una stored procedure, è consigliabile eseguire il codice R in un IDE esterno o in uno degli strumenti di R, ad esempio RTerm o RGui. Usando questi metodi, eseguire il test e debug del codice utilizzando i messaggi di errore dettagliati restituiti da R.

Tuttavia, in alcuni casi il codice funzioni perfettamente in IDE o un'utilità esterna potrebbe non riuscire per l'esecuzione in una stored procedure o in un Server SQL contesto di calcolo. In questo caso, esistono una serie di problemi da cercare prima che si può presupporre che il pacchetto non funziona in SQL Server.

1. Verificare se finestra di avvio è in esecuzione.

2. Esaminare i messaggi per verificare se i dati di input o di dati di output contengono colonne con tipi di dati incompatibili o non supportato. Le query su un database SQL, ad esempio, restituiscono spesso GUID o rowguid, entrambi i quali non sono supportati. Per ulteriori informazioni, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

3. Esaminare le pagine della Guida per le singole funzioni R determinare se tutti i parametri sono supportati per il contesto di calcolo di SQL Server. Per informazioni su ScaleR, utilizzare i comandi della Guida in linea R o vedere [riferimento pacchetto](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

### <a name="you-get-different-results-from-the-same-script-when-running-in-sql-compared-to-other-environments"></a>Si ottengano risultati diversi dallo stesso script durante l'esecuzione in SQL rispetto ad altri ambienti

Gli script R possono restituire valori diversi in un contesto di SQL Server, per diversi motivi:

- Conversione implicita del tipo viene eseguita automaticamente alcuni tipi di dati, quando i dati vengono passati tra il Server SQL e R. Per ulteriori informazioni, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

- Determinare se al numero di bit è un fattore. Ad esempio, sono spesso le differenze nei risultati di operazioni matematiche per librerie di punto a virgola mobile a 32 e 64 bit.

- Determinare se NaN vengono generati in qualsiasi operazione. Questo può invalidare i risultati.

- Quando crei un reciproco di un numero prossimo a zero, è possano amplificate piccole differenze.

- Errori di arrotondamento accumulati possono provocare ad esempio i valori che sono minori di zero anziché zero.

### <a name="error-not-enough-quota-to-process-this-command"></a>Errore: *risorse insufficienti per eseguire il comando*

Questo errore può indicare una delle seguenti operazioni:

- Finestra di avvio potrebbe essere insufficiente agli utenti esterni di eseguire la query esterna. Ad esempio, se si eseguono contemporaneamente più di 20 query esterne e sono disponibili solo 20 utenti predefinito, una o più query potrebbe non riuscire.

- Memoria disponibile è insufficiente per l'elaborazione dell'attività di R. Questo errore si verifica in genere in un ambiente predefinito, in SQL Server potrebbe essere utilizzata fino al 70% delle risorse del computer. Per informazioni su come modificare la configurazione del server per il supporto maggiore utilizzo delle risorse da R, vedere [operatività del codice R](r/operationalizing-your-r-code.md).

### <a name="error-cant-find-package"></a>Errore: *Impossibile trovare il pacchetto*

Se eseguire il codice R in SQL Server e il messaggio, ma non hanno ricevuto il messaggio quando è stato eseguito lo stesso codice all'esterno di SQL Server, significa che il pacchetto non è stato installato nel percorso di libreria predefinito utilizzato da SQL Server.

Questo errore può verificarsi in molti modi:

- Il server è installato un nuovo pacchetto, ma è stato negato l'accesso, in modo R è installato il pacchetto in una raccolta di utenti.

- È installato Servizi R e quindi installato un altro strumento di R o set di librerie, incluso Microsoft R Server (Standalone), Microsoft R Client, RStudio e così via.

Per determinare il percorso della libreria di pacchetti R che viene utilizzato dall'istanza, aprire SQL Server Management Studio (o qualsiasi altro strumento di query di database), connettersi all'istanza e quindi eseguire la stored procedure seguente:

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Risultati dell'esempio

*Messaggi STDOUT dallo script esterno:*

*[1] "c:\\i file di programma\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "/ programma c: file/Microsoft SQL Server/MSSQL13. R_SERVICES/SQL2016/libreria"*

Per risolvere il problema, è necessario reinstallare il pacchetto nella raccolta di istanza di SQL Server.

>[!NOTE]
>Se è stata aggiornata un'istanza di SQL Server 2016 da usare la versione più recente di Microsoft R, il percorso di libreria predefinito è diverso. Per ulteriori informazioni, vedere [SqlBindR utilizzare per aggiornare un'istanza di R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="next-steps"></a>Passaggi successivi

[Problemi noti e risoluzione dei problemi di Machine Learning Services](machine-learning-troubleshooting-faq.md)

[Raccolta dei dati per la risoluzione dei problemi di apprendimento](data-collection-ml-troubleshooting-process.md)

[Domande frequenti sull'installazione e sull'aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Risolvere i problemi relativi a connessioni al motore di database](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
