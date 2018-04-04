---
title: Problemi comuni relativi a esecuzione dello script esterno in SQL Server | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 10/11/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
caps.latest.revision: 1
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: cf86d1e6d4150736b5d2d6be8d90172bb9cd6f82
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="common-issues-with-external-script-execution-in-sql-server"></a>Problemi comuni relativi a esecuzione dello script esterno in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo contiene un elenco di problemi noti e problemi comuni relativi all'esecuzione di codice Python o R in SQL Server.

Prima di iniziare, si consiglia di raccogliere alcune informazioni relative al sistema. Per altre informazioni, vedere [la raccolta dei dati per la risoluzione dei problemi](data-collection-ml-troubleshooting-process.md).

Inoltre, esaminare l'elenco dei problemi comuni che sono specifiche di configurazione o la configurazione iniziale: [programma di installazione e domande frequenti sull'aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md).

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="launchpad-issues"></a>Problemi di avvio

Il servizio Launchpad attendibile di SQL Server gestisce l'esecuzione di script esterni e la comunicazione con R, Python o altri runtime esterni. Più possono impedire l'avvio dall'avvio, inclusi i problemi di configurazione o le modifiche o mancante protocolli di rete.

Come parte del processo di risoluzione dei problemi, iniziare da rispondere alle domande seguenti:

- È stata Launchpad sempre non può essere eseguito o arresti utilizzo?
- Quale account di servizio Launchpad si trovi in?
- Quali sono i diritti utente dispone dell'account del servizio Launchpad?

### <a name="determine-whether-launchpad-is-running"></a>Determinare se è in esecuzione Launchpad

1. Aprire la **Services** pannello (Services. msc). In alternativa, dalla riga di comando, digitare **SQLServerManager13.msc** oppure **SQLServerManager14.msc** per aprire [Gestione configurazione SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Prendere nota dell'account del servizio in esecuzione nella finestra di avvio. Ogni istanza in cui è abilitato R o Python debba avere la propria istanza del servizio Launchpad. Ad esempio, il servizio per un'istanza denominata potrebbe essere analogo a quello _MSSQLLaunchpad$ InstanceName_.

3. Se il servizio viene arrestato, riavviarlo. Al riavvio, se sono presenti eventuali problemi con la configurazione, un messaggio viene pubblicato nel registro eventi di sistema e il servizio viene arrestato nuovamente. Controllare il registro eventi di sistema per informazioni dettagliate sui motivi per cui il servizio arrestato.

4. Esaminare il contenuto di RSetup.log e assicurarsi che non siano presenti errori nel programma di installazione. Ad esempio, il messaggio *chiusura con codice 0* indica un errore del servizio di avvio.

5. Per cercare altri errori, esaminare il contenuto di rlauncher. log.

### <a name="check-the-launchpad-service-account"></a>Verificare l'account del servizio Launchpad

L'account del servizio predefinito potrebbe essere "NT Service\$SQL2016" o "NT Service\$SQL2017". La parte finale potrebbe variare, a seconda del nome dell'istanza SQL.

Il servizio Launchpad (Launchpad.exe) viene eseguita usando un account del servizio con privilegi limitati. Per avviare R e Python e comunicare con l'istanza del database, tuttavia, l'account del servizio Launchpad richiede diritti utente seguenti:

- Accesso come servizio (SeServiceLogonRight)
- Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)
- Ignorare controllo incrociato (SeChangeNotifyPrivilege)
- Regolazione limite risorse memoria per un processo (SeIncreaseQuotaSizePrivilege)

Per informazioni su questi diritti, vedere la sezione "diritti e privilegi di Windows" nella [configurare Windows account del servizio e autorizzazioni](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Se si ha familiarità con l'uso dello strumento di supporto diagnostica piattaforma SDP () per la diagnostica di SQL Server, è possibile utilizzare SDP di esaminare il file di output con il nome MachineName_UserRights.txt.

### <a name="review-launchpad-requirements"></a>Rivedere i requisiti di finestra di avvio

Uno dei diversi problemi che possono impedire l'avvio finestra di avvio. Il servizio Launchpad potrebbe avviare e arrestare o potrebbe smettere di arresto anomalo del sistema o il servizio con un timeout di connessione. In questi casi, il sistema è in genere stato modificato o configurato in modo che non possono essere eseguiti Launchpad.

#### <a name="determine-whether-8dot3-notation-is-enabled"></a>Determinare se è abilitata una notazione 8dot3

Per la compatibilità con R, SQL Server 2016 R Services (In-Database) è richiesto l'unità in cui la funzionalità viene installata per supportare la creazione di nomi di file brevi usando *notazione 8dot3*. Un nome di 8.3 file viene chiamato anche un *nome file breve*, e viene utilizzata per la compatibilità con le versioni precedenti di Microsoft Windows o come alternativa ai nomi file lunghi.

Se il volume in cui si installa R non supporta nomi di file brevi, i processi che avviano R da SQL Server potrebbero non essere in grado di trovare l'eseguibile corretto e finestra di avvio non verrà avviato.

In alternativa, è possibile abilitare la notazione 8dot3 nel volume in cui è installato SQL Server e in cui è installato R Services. È quindi necessario specificare il nome breve per la directory di lavoro nel file di configurazione di R Services.

1. Per abilitare la notazione 8dot3, eseguire l'utilità fsutil con il *8dot3name* argomento come descritto qui: [8dot3name fsutil](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Dopo aver abilitata la notazione 8dot3, aprire il file RLauncher.config e prendere nota della proprietà di `WORKING_DIRECTORY`. Per informazioni su come individuare questo file, vedere [raccolta dei dati per la risoluzione dei problemi di Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Usare l'utilità fsutil con il *file* argomento per specificare un percorso di file breve per la cartella specificata nella WORKING_DIRECTORY.

4. Modificare il file di configurazione per specificare la stessa directory di lavoro immesso nella proprietà WORKING_DIRECTORY. In alternativa, è possibile specificare un'altra directory di lavoro e scegliere un percorso esistente che già è compatibile con la notazione 8dot3.

> [!NOTE] 
> Questa limitazione è stata rimossa in una versione successiva. Se si riscontra questo problema, installare uno dei valori seguenti:
> * SQL Server 2016 SP1 e CU1: [aggiornamento cumulativo 1 per SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, aggiornamento cumulativo 3 e ciò [hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), disponibile su richiesta.

#### <a name="the-user-group-for-launchpad-cannot-log-on-locally"></a>Il gruppo di utenti per la finestra di avvio non può accedere localmente

Durante l'installazione dei servizi di Machine Learning, SQL Server crea il gruppo di utenti di Windows **SQLRUserGroup** e quindi si esegue il provisioning con tutti i diritti necessari per la finestra di avvio per connettersi a SQL Server ed eseguire processi di script esterni. Se questo gruppo di utenti è abilitato, viene utilizzato anche per eseguire script Python.

Tuttavia, nelle organizzazioni in cui vengono applicati i criteri di sicurezza più restrittivi, potrebbero avere i diritti necessari per questo gruppo sia stato rimosso manualmente o potrebbe essere revocati automaticamente dai criteri. Se sono stati rimossi i diritti, finestra di avvio non può più connettersi a SQL Server e SQL Server non è possibile chiamare il runtime esterno.

Per correggere il problema, assicurarsi che il gruppo **SQLRUserGroup** abbia il diritto di sistema **Consenti accesso locale**.

Per altre informazioni, vedere [configurare Windows account del servizio e autorizzazioni](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

#### <a name="improper-setup-leading-to-mismatched-dlls"></a>Programma di installazione non corretta iniziali per le DLL non corrispondenti

Se si installa il motore di database con altre funzionalità, patch, il server e quindi aggiunta la funzionalità di Machine Learning usando il supporto originale, potrebbe essere installata la versione errata di componenti di Machine Learning. Quando Launchpad rileva una mancata corrispondenza di versione, viene chiuso e viene creato un file di dump.

Per evitare questo problema, assicurarsi di installare tutte le nuove funzionalità a livello di patch stessa istanza del server.

**Il modo non corretto per eseguire l'aggiornamento:**

1. Installare SQL Server 2016 senza R Services.
2. Eseguire l'aggiornamento di SQL Server 2016 aggiornamento cumulativo 2.
3. Installare R Services (In-Database) utilizzando il supporto RTM.

**Il modo corretto per eseguire l'aggiornamento:**

1. Installare SQL Server 2016 senza R Services.
2. Aggiornare SQL Server 2016 per il livello di patch desiderato. Ad esempio, installare Service Pack 1 e quindi l'aggiornamento cumulativo 2.
3. Per aggiungere la funzionalità a livello di patch corretto, eseguire nuovamente l'installazione di SP1 e CU2 e quindi scegliere R Services (In-Database). 

#### <a name="check-whether-a-user-has-rights-to-run-external-scripts"></a>Controllare se un utente dispone di diritti per eseguire gli script esterni

Anche se Launchpad sia configurato correttamente, restituirà un errore se l'utente non dispone delle autorizzazioni necessarie per eseguire gli script R o Python.

Se è stato installato SQL Server come un amministratore del database o dispone di un database, sono concesse automaticamente questa autorizzazione. Tuttavia, altri utenti in genere sono più di autorizzazioni limitate. Se si prova a eseguire uno script R, ricevono un errore di avvio.

Per risolvere il problema, in SQL Server Management Studio, un amministratore della sicurezza può modificare l'account di accesso SQL o un account utente di Windows eseguendo lo script seguente:

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Per altre informazioni, vedere [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

### <a name="common-launchpad-errors"></a>Errori comuni di finestra di avvio

Questa sezione elenca i messaggi di errore più comuni che restituisce Launchpad.

#### <a name="error-unable-to-launch-runtime-for-r-script"></a>Errore: *Impossibile avviare il runtime per lo script R*

Se il gruppo di Windows per gli utenti di R (utilizzato anche per Python) non è possibile accedere all'istanza che esegue servizi di R, è possibile visualizzare gli errori seguenti:

- Errori generati quando si tenta di eseguire gli script R:

    * *Non è stato possibile avviare il runtime per lo script 'R'. Verificare la configurazione del runtime di 'R'.*

    * *Si è verificato un errore dello script esterno. Non è stato possibile avviare il runtime.*

- Gli errori generati dal [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] servizio:

    * *Failed to initialize the launcher RLauncher.dll*

    * *No launcher dlls were registered!*

    * *I log di sicurezza indicano che l'account del servizio NT non è riuscito per l'accesso*

Per informazioni su come concedere al gruppo utente le autorizzazioni necessarie, vedere [installare SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Questa limitazione non si applica se si usano account di accesso SQL per eseguire script R da una workstation remota.

#### <a name="error-logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>Errore: *errore durante l'accesso: l'utente non dispone del tipo di accesso*

Per impostazione predefinita [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] utilizza il seguente account all'avvio: `NT Service\MSSQLLaunchpad`. L'account è configurato per [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] l'installazione abbia tutte le autorizzazioni necessarie.

Se si assegna un account diverso alla finestra di avvio o di destra viene rimosso da un criterio nel computer SQL Server, l'account non disponga delle autorizzazioni necessarie e si potrebbe essere visualizzato questo errore:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Errore durante l'accesso. L'utente non ha ottenuto il tipo di accesso richiesto a questo computer.*

Per concedere le autorizzazioni necessarie per il nuovo account del servizio, utilizzare l'applicazione di criteri di sicurezza locali e aggiornare le autorizzazioni per l'account da includere le autorizzazioni seguenti:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

#### <a name="error-unable-to-communicate-with-the-launchpad-service"></a>Errore: *Impossibile comunicare con il servizio Launchpad*

Se è stato installato e attivato quindi apprendimento, ma questo errore si verifica quando si tenta di eseguire uno script R o Python, il servizio Launchpad per l'istanza potrebbe siano in esecuzione.

1. Dal prompt dei comandi di Windows aprire Gestione configurazione SQL Server. Per altre informazioni, vedere [Gestione configurazione SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Finestra di avvio di SQL Server per l'istanza e quindi scegliere **proprietà**.

3. Selezionare il **servizio** scheda e quindi verificare che il servizio sia in esecuzione. Se non è in esecuzione, modificare il **modalità di avvio** a **automatica**, quindi selezionare **applica**.

4. Il riavvio del servizio in genere corregge il problema in modo che sia possibile eseguire gli script di machine learning. Se il riavvio non risolve il problema, tenere presente il percorso e gli argomenti in di **percorso binario** proprietà ed eseguire le operazioni seguenti:

    A. Esaminare i file con estensione config dell'utilità di avvio e verificare che la directory di lavoro sia valida.

    B. Verificare che il gruppo di Windows che viene utilizzato dalla finestra di avvio è possibile connettersi all'istanza di SQL Server, come descritto nel [precedente sezione](#bkmk_LaunchpadTS).

    c. Se si modifica una qualsiasi delle proprietà del servizio, riavviare il servizio Launchpad.

#### <a name="error-fatal-error-creation-of-tmpfile-failed"></a>Errore: *creazione errore irreversibile del tmpFile non riuscita*

In questo scenario, è stato installato correttamente le funzionalità di machine learning e finestra di avvio è in esecuzione. Si tenta di eseguire il codice Python o R semplice, ma Launchpad ha esito negativo con un errore simile al seguente: 

>*Impossibile comunicare con il runtime per lo script R. Controllare i requisiti del runtime di R.*

Allo stesso tempo, il runtime dello script esterno scrive il messaggio seguente come parte del messaggio STDERR: 

>*Errore irreversibile: la creazione di tmpfile non riuscita.*

Questo errore indica che l'account di avvio sta cercando di utilizzare non dispone dell'autorizzazione per accedere al database. Questa situazione può verificarsi quando vengono implementati i criteri di sicurezza rigidi. Per determinare se questo è il caso, esaminare i registri di SQL Server e controllare per vedere se l'account MSSQLSERVER01 negato all'account di accesso. Le stesse informazioni viene fornite nei log che sono specifiche di R\_servizi o PYTHON\_servizi. Cercare ExtLaunchError.log.

Per impostazione predefinita, 20 account sono impostato e associato al processo Launchpad.exe, con i nomi MSSQLSERVER01 tramite MSSQLSERVER20. Se si apportano un uso massiccio di R o Python, è possibile aumentare il numero di account.

Per risolvere il problema, assicurarsi che il gruppo abbia *Consenti accesso locale* delle autorizzazioni per l'istanza locale in cui le funzionalità di machine learning state installate e abilitate. In alcuni ambienti, questo livello di autorizzazione potrebbe richiedere un'eccezione di oggetto Criteri di gruppo dell'amministratore di rete.

## <a name="r-script-issues"></a>Problemi di script R

In questa sezione contiene alcuni problemi comuni che sono specifici per l'esecuzione di script R e gli errori di script R. L'elenco non è completo, poiché sono presenti numerosi pacchetti R e gli errori potrebbero essere diversi tra versioni diverse dello stesso pacchetto R. È consigliabile che la registrazione degli errori di script R nella [forum di Microsoft R Server](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR), che offre un supporto di machine learning componenti usati in R Services (In-Database), servizi di apprendimento macchine con Python, il Client R Microsoft e Microsoft R Server.

### <a name="multiple-r-instances-on-the-same-computer"></a>Più istanze di R nello stesso computer

Può essere più facile trovare autonomamente con più distribuzioni di R nello stesso computer, nonché più copie dello stesso pacchetto R in diverse versioni. Ad esempio, se si installano le Machine Learning Server (Standalone) e Machine Learning Services (In-Database), i programmi di installazione creare versioni distinte delle librerie R. 

Tale funzionalità diventa un problema quando si tenta di eseguire uno script dalla riga di comando e non si è certi le librerie in uso. In alternativa, è possibile installare un pacchetto per la libreria non corretta e quindi in un secondo momento chiedersi perché non è possibile trovare il pacchetto da SQL Server.

+ Evitare l'uso diretto di librerie R e strumenti che vengono installati per l'utilizzo dell'istanza di SQL Server, tranne in alcuni casi, ad esempio la risoluzione dei problemi o installazione di nuovi pacchetti. 
+ Se è necessario utilizzare uno strumento da riga di comando di R, è possibile installare [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client). 
+ SQL Server consente nel database Gestione di pacchetti R. Questo è il modo più semplice per creare librerie del pacchetto R che possono essere condivisa fra gli utenti. Per altre informazioni, vedere [gestione dei pacchetti R per SQL Server](r/r-package-management-for-sql-server-r-services.md).

### <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Non deselezionare l'area di lavoro durante l'esecuzione R in un contesto di calcolo SQL

Anche se la cancellazione l'area di lavoro è comune quando si lavora nella console di R, può avere conseguenze impreviste in un database SQL di contesto di calcolo.

`revoScriptConnection` è un oggetto in area di lavoro R che contiene informazioni su una sessione R che viene chiamata da SQL Server. Tuttavia, se il codice R include un comando per cancellare l'area di lavoro (ad esempio `rm(list=ls())`), viene cancellate anche tutte le informazioni sulla sessione e altri oggetti nell'area di lavoro R.

In alternativa, evitare di compensazione indiscriminato di variabili e altri oggetti durante l'esecuzione R in SQL Server. È possibile eliminare variabili specifiche usando il **rimuovere** funzione:

```R
remove('name1', 'name2', ...)
```

Se sono presenti più variabili da eliminare, è consigliabile salvare i nomi delle variabili temporanee per un elenco e quindi eseguire periodicamente operazioni di garbage collection su nell'elenco.

### <a name="implied-authentication-for-remote-execution-via-odbc"></a>Autenticazione implicita per l'esecuzione remota tramite ODBC

Se ci si connette ai [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer per eseguire R comandi utilizzando il **RevoScaleR** funzioni, è possibile che venga visualizzato un errore quando si utilizzano chiamate ODBC che scrivono dati al server. Questo errore si verifica solo quando si utilizza l'autenticazione di Windows.

Il motivo è che gli account di lavoro che vengono creati per R Services non dispone dell'autorizzazione per connettersi al server. Pertanto, chiamate ODBC non possono essere eseguite per proprio conto. Il problema non viene eseguito con account di accesso SQL in quanto, con account di accesso SQL, le credenziali vengono passate in modo esplicito dal client R per l'istanza di SQL Server e quindi per ODBC. Tuttavia, utilizzando gli account di accesso SQL è meno sicura rispetto all'uso l'autenticazione di Windows.

Per abilitare le credenziali di Windows deve essere passato in modo sicuro da uno script che ha avviato in modalità remota, SQL Server deve emulare le proprie credenziali. Questo processo è detto _l'autenticazione implicita_. Per ottenere questo risultato, il lavoro che eseguono script Python o R nel computer SQL Server devono disporre delle autorizzazioni corrette.

1. Apri [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] come amministratore nell'istanza in cui si desidera eseguire il codice R.

2. Eseguire lo script seguente. Ricordarsi di modificare il nome del gruppo utente, se è stato modificato il valore predefinito e i nomi di computer e istanza.

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

### <a name="the-r-script-works-outside-of-t-sql-but-not-in-a-stored-procedure"></a>Lo script R funziona all'esterno di T-SQL, ma non in una stored procedure

Prima di wrapping del codice R in una stored procedure, è consigliabile eseguire il codice R in un IDE esterno o in uno degli strumenti di R, ad esempio RTerm o RGui. Usando questi metodi, eseguire il test e il debug del codice utilizzando i messaggi di errore dettagliati restituiti da R.

Tuttavia, in alcuni casi il codice che funziona perfettamente nell'IDE o utilità esterna potrebbe non riuscire per l'esecuzione in una stored procedure o in un Server SQL contesto di calcolo. In questo caso, esistono numerosi problemi da cercare prima che si può presupporre che il pacchetto non funziona in SQL Server.

1. Verificare se finestra di avvio è in esecuzione.

2. Esaminare i messaggi per verificare se i dati di input o output dei dati contiene colonne con tipi di dati incompatibili o non supportato. Ad esempio, le query su un database SQL spesso restituiscono GUID o rowguid, entrambi i quali non sono supportati. Per altre informazioni, vedere [tipi di dati e delle librerie R](r/r-libraries-and-data-types.md).

3. Esaminare le pagine della Guida per le singole funzioni R determinare se tutti i parametri sono supportati per il contesto di calcolo di SQL Server. Per informazioni sulla ScaleR, utilizzare i comandi della Guida in linea R oppure vedere [riferimento al pacchetto](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

### <a name="you-get-different-results-from-the-same-script-when-running-in-sql-compared-to-other-environments"></a>Si ottengono risultati diversi dallo stesso script durante l'esecuzione in SQL rispetto ad altri ambienti

Gli script R possono restituire valori diversi in un contesto di SQL Server, per diversi motivi:

- Conversione implicita del tipo viene eseguita automaticamente alcuni tipi di dati, quando i dati vengono passati tra Server SQL e R. Per altre informazioni, vedere [tipi di dati e delle librerie R](r/r-libraries-and-data-types.md).

- Determinare se al numero di bit è un fattore. Ad esempio, sono spesso le differenze nei risultati di operazioni matematiche per librerie di punto a virgola mobile a 32 e 64 bit.

- Determinare se i valori NaN prodotte in qualsiasi operazione. Ciò può invalidare i risultati.

- Quando si utilizza un reciproco di un numero vicino a zero, è possano amplificate piccole differenze.

- Errori di arrotondamento accumulati possono provocare elementi come valori che sono minori di zero anziché zero.

### <a name="error-not-enough-quota-to-process-this-command"></a>Errore: *risorse insufficienti per eseguire il comando*

Questo errore può indicare una delle seguenti operazioni:

- Finestra di avvio potrebbe contenere utenti esterni insufficienti per eseguire la query esterna. Ad esempio, se si eseguono contemporaneamente più di 20 query esterne e sono disponibili solo 20 utenti predefinito, una o più query potrebbe non riuscire.

- Memoria disponibile è insufficiente per l'elaborazione dell'attività di R. Questo errore si verifica in genere in un ambiente predefinito, in SQL Server potrebbe essere utilizzata fino al 70 percento delle risorse del computer. Per informazioni su come modificare la configurazione del server per il supporto maggiore utilizzo delle risorse da R, vedere [operatività del codice R](r/operationalizing-your-r-code.md).

### <a name="error-cant-find-package"></a>Errore: *non è possibile trovare il pacchetto*

Se eseguire il codice R in SQL Server e il messaggio, ma non hanno ricevuto il messaggio quando è stato eseguito lo stesso codice all'esterno di SQL Server, significa che il pacchetto non è stato installato nel percorso di libreria predefinito utilizzato da SQL Server.

Questo errore può verificarsi in molti modi:

- È stato installato un nuovo pacchetto nel server, ma è stato negato l'accesso, in modo che R sia installato il pacchetto in una raccolta di utenti.

- È installato Servizi R e quindi installato un altro strumento di R o set di librerie, incluse Microsoft R Server (Standalone), Microsoft R Client, RStudio e così via.

Per determinare il percorso della libreria di pacchetti R che viene utilizzato dall'istanza, aprire SQL Server Management Studio (o qualsiasi altro strumento di query di database), connettersi all'istanza e quindi eseguire la stored procedure seguente:

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Risultati dell'esempio

*Messaggi STDOUT dallo script esterno:*

*[1] "c:\\file di programma\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "c: / programma file/Microsoft SQL Server/MSSQL13. SQL2016/R_SERVICES/libreria"*

Per risolvere il problema, è necessario reinstallare il pacchetto nella raccolta di istanza di SQL Server.

>[!NOTE]
>Se è stato eseguito l'aggiornamento di un'istanza di SQL Server 2016 da usare la versione più recente di Microsoft R, il percorso di libreria predefinito è diverso. Per altre informazioni, vedere [SqlBindR utilizzare per aggiornare un'istanza di R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="next-steps"></a>Passaggi successivi

[Problemi noti e risoluzione dei problemi di Machine Learning Services](machine-learning-troubleshooting-faq.md)

[Raccolta dei dati per la risoluzione dei problemi di apprendimento automatico](data-collection-ml-troubleshooting-process.md)

[Domande frequenti sull'installazione e sull'aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Risolvere i problemi di connessioni al motore di database](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
