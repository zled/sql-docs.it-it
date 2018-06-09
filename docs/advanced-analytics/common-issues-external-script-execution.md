---
title: Problemi comuni relativi a servizio Launchpad e l'esecuzione dello script esterno in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 08ab6e2db6d6cde5e41f7ddb88c8afd1da241df7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34706839"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Problemi comuni relativi a servizio Launchpad e l'esecuzione dello script esterno in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 Servizio Launchpad attendibile di SQL Server supporta l'esecuzione dello script esterno per R e Python. In SQL Server 2016 R Services SP1 fornisce il servizio. SQL Server 2017 include il servizio Launchpad come parte dell'installazione iniziali sono.

Più possono impedire l'avvio di avvio, inclusi i problemi di configurazione o le modifiche o i protocolli di rete mancante. In questo articolo vengono fornite indicazioni sulla risoluzione dei problemi per molti problemi. Per qualsiasi abbiamo perso, è possibile pubblicare domande per la [forum di Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR).

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="determine-whether-launchpad-is-running"></a>Determinare se finestra di avvio è in esecuzione

1. Aprire il **servizi** pannello (Services.msc). In alternativa, dalla riga di comando, digitare **SQLServerManager13.msc** o **SQLServerManager14.msc** per aprire [Gestione configurazione SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Prendere nota dell'account del servizio in esecuzione nella finestra di avvio. Ogni istanza in cui è abilitato R o Python debba avere la propria istanza del servizio Launchpad. Ad esempio, il servizio per un'istanza denominata potrebbe essere simile al seguente _MSSQLLaunchpad$ InstanceName_.

3. Se il servizio viene arrestato, riavviarlo. Scegliere il riavvio, se sono presenti eventuali problemi di configurazione, un messaggio viene pubblicato nel registro eventi di sistema e viene nuovamente arrestato il servizio. Controllare il registro eventi di sistema per informazioni dettagliate sui motivi per cui il servizio è stato arrestato.

4. Esaminare il contenuto di RSetup.log e assicurarsi che non siano presenti errori nel programma di installazione. Ad esempio, il messaggio *chiusura con codice 0* indica l'errore del servizio di avvio.

5. Per cercare altri errori, esaminare il contenuto di rlauncher.log.

## <a name="check-the-launchpad-service-account"></a>Verificare l'account del servizio Launchpad

L'account del servizio predefinito potrebbe essere "NT Service\$SQL2016" o "NT Service\$SQL2017". La parte finale potrebbe variare a seconda del nome dell'istanza SQL.

Il servizio Launchpad (Launchpad.exe) viene eseguito utilizzando un account di servizio con privilegi limitati. Per avviare R e Python e comunicare con l'istanza del database, tuttavia, l'account del servizio Launchpad richiede i diritti utente di seguenti:

- Accesso come servizio (SeServiceLogonRight)
- Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)
- Ignorare controllo incrociato (SeChangeNotifyPrivilege)
- Regolazione limite risorse memoria per un processo (SeIncreaseQuotaSizePrivilege)

Per informazioni su questi diritti, vedere la sezione "diritti e privilegi di Windows" in [Windows configurare account del servizio e autorizzazioni](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Se si ha familiarità con l'utilizzo dello strumento di supporto diagnostica piattaforma SDP () per la diagnostica di SQL Server, è possibile utilizzare SDP per esaminare il file di output con il nome MachineName_UserRights.txt.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Gruppo di utenti per la finestra di avvio non può accedere localmente

Durante l'installazione di servizi di Machine Learning, SQL Server crea il gruppo di utenti Windows **SQLRUserGroup** e quindi viene eseguito il provisioning, con tutti i diritti necessari per la finestra di avvio per connettersi a SQL Server ed eseguire processi di script esterni. Se questo gruppo di utenti è abilitato, è anche possibile eseguire script Python.

Tuttavia, nelle organizzazioni in cui vengono applicati i criteri di sicurezza più restrittivi, potrebbero avere i diritti necessari per questo gruppo sia stato rimosso manualmente o potrebbe essere revocati automaticamente dai criteri. Se sono stati rimossi i diritti, finestra di avvio non può più connettersi a SQL Server e SQL Server non è possibile chiamare il runtime esterno.

Per correggere il problema, assicurarsi che il gruppo **SQLRUserGroup** abbia il diritto di sistema **Consenti accesso locale**.

Per ulteriori informazioni, vedere [Windows configurare account del servizio e autorizzazioni](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

## <a name="permissions-to-run-external-scripts"></a>Autorizzazioni necessarie per eseguire gli script esterni

Anche se Launchpad è configurato correttamente, restituisce un errore se l'utente non dispone dell'autorizzazione per eseguire gli script R o Python.

Se è installato SQL Server come amministratore di database o il proprietario del database, questa autorizzazione sono concesse automaticamente. Tuttavia, altri utenti in genere sono più di autorizzazioni limitate. Se si tenta di eseguire uno script R, ricevono un errore di avvio.

Per risolvere il problema, in SQL Server Management Studio, un amministratore della sicurezza può modificare l'account di accesso SQL o un account utente di Windows eseguendo lo script seguente:

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Per ulteriori informazioni, vedere [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Errori più comuni di finestra di avvio

Questa sezione elenca i messaggi di errore più comuni restituiti dalla finestra di avvio.

## <a name="unable-to-launch-runtime-for-r-script"></a>"Impossibile avviare il runtime per lo script R"

Se il gruppo di Windows per gli utenti di R (utilizzato anche per Python) non è possibile accedere all'istanza che esegue servizi di R, verranno visualizzati gli errori seguenti:

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

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"Errore durante l'accesso: l'utente non è stato concesso il tipo di accesso richiesto"

Per impostazione predefinita, [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] utilizza il seguente account di avvio: `NT Service\MSSQLLaunchpad`. L'account è configurato per [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] il programma di installazione di tutte le autorizzazioni necessarie.

Se si assegna un account diverso per una finestra di avvio o di destra viene rimosso da un criterio nel computer SQL Server, l'account potrebbe non disporre delle autorizzazioni necessarie e si potrebbe essere visualizzato questo errore:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Errore durante l'accesso. L'utente non ha ottenuto il tipo di accesso richiesto a questo computer.*

Per concedere le autorizzazioni necessarie per il nuovo account di servizio, utilizzare l'applicazione di criteri di sicurezza locali e aggiornare le autorizzazioni per l'account da includere le autorizzazioni seguenti:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>"Impossibile comunicare con il servizio Launchpad"

Se è stato installato e attivato quindi l'apprendimento, ma questo errore si verifica quando si tenta di eseguire uno script R o Python, il servizio Launchpad per l'istanza potrebbe siano in esecuzione.

1. Dal prompt dei comandi di Windows aprire Gestione configurazione SQL Server. Per altre informazioni, vedere [Gestione configurazione SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Finestra di avvio di SQL Server per l'istanza e quindi scegliere **proprietà**.

3. Selezionare il **servizio** scheda e quindi verificare che il servizio sia in esecuzione. Se non è in esecuzione, modificare il **modalità di avvio** a **automatica**, quindi selezionare **applica**.

4. Il riavvio del servizio in genere consente di correggere il problema, in modo che sia possibile eseguire gli script di machine learning. Se il riavvio non risolve il problema, si noti il percorso e gli argomenti di **percorso binario** , proprietà ed eseguire le operazioni seguenti:

    A. Esaminare i file con estensione config dell'utilità di avvio e verificare che la directory di lavoro sia valida.

    B. Verificare che il gruppo di Windows che viene utilizzato dalla finestra di avvio è possibile connettersi all'istanza di SQL Server, come descritto nel [precedente sezione](#bkmk_LaunchpadTS).

    c. Se si modifica una qualsiasi delle proprietà del servizio, riavviare il servizio Launchpad.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>"Creazione di un errore irreversibile di tmpFile non riuscita"

In questo scenario, è stato installato correttamente le funzionalità di machine learning e finestra di avvio è in esecuzione. Si tenta di eseguire il codice R o Python semplice, ma Launchpad genera un errore simile al seguente: 

>*Impossibile comunicare con il runtime per lo script R. Controllare i requisiti del runtime di R.*

Allo stesso tempo, il runtime dello script esterno scrive il messaggio seguente come parte del messaggio STDERR: 

>*Errore irreversibile: la creazione di tmpfile non riuscita.*

Questo errore indica che l'account di avvio sta tentando di utilizzare non dispone dell'autorizzazione per accedere al database. Questa situazione può verificarsi quando vengono implementati i criteri di sicurezza rigidi. Per determinare se questo è il caso, esaminare i registri di SQL Server e controllare per vedere se l'account MSSQLSERVER01 negato all'account di accesso. Viene fornite le stesse informazioni nei registri di specifiche di R\_servizi o PYTHON\_servizi. Cercare ExtLaunchError.log.

Per impostazione predefinita, 20 account sono impostato e associato al processo Launchpad.exe, con i nomi MSSQLSERVER01 tramite MSSQLSERVER20. Se si apportano un uso massiccio di R o Python, è possibile aumentare il numero di account.

Per risolvere il problema, verificare che il gruppo abbia *Consenti accesso locale* delle autorizzazioni per l'istanza locale in cui le funzionalità di machine learning state installate e abilitate. In alcuni ambienti, questo livello di autorizzazione potrebbe richiedere un'eccezione dell'oggetto Criteri di gruppo dell'amministratore di rete.

## <a name="not-enough-quota-to-process-this-command"></a>"Non sono sufficienti per eseguire il comando"quote

Questo errore può indicare una delle seguenti operazioni:

- Finestra di avvio potrebbe essere insufficiente agli utenti esterni di eseguire la query esterna. Ad esempio, se si eseguono contemporaneamente più di 20 query esterne e sono disponibili solo 20 utenti predefinito, una o più query potrebbe non riuscire.

- Memoria disponibile è insufficiente per l'elaborazione dell'attività di R. Questo errore si verifica in genere in un ambiente predefinito, in SQL Server potrebbe essere utilizzata fino al 70% delle risorse del computer. Per informazioni su come modificare la configurazione del server per il supporto maggiore utilizzo delle risorse da R, vedere [operatività del codice R](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>"Impossibile trovare il pacchetto"

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

*[1] "c:\\file di programma\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "c: / programma file/Microsoft SQL Server/MSSQL13. SQL2016/R_SERVICES/libreria"*

Per risolvere il problema, è necessario reinstallare il pacchetto nella raccolta di istanza di SQL Server.

>[!NOTE]
>Se è stata aggiornata un'istanza di SQL Server 2016 da usare la versione più recente di Microsoft R, il percorso di libreria predefinito è diverso. Per ulteriori informazioni, vedere [SqlBindR utilizzare per aggiornare un'istanza di R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Finestra di avvio viene arrestato a causa di DLL non corrispondenti

Se si installa il motore di database con altre funzionalità, patch, il server e quindi aggiunta la funzionalità di Machine Learning usando il supporto originale, la versione errata di componenti di Machine Learning potrebbe essere installata. Quando Launchpad rileva una mancata corrispondenza di versione, arresta e crea un file di dump.

Per evitare questo problema, assicurarsi di installare le nuove funzionalità a livello di patch stesso come istanza del server.

**Il modo non corretto per eseguire l'aggiornamento:**

1. Installare SQL Server 2016 senza R Services.
2. Eseguire l'aggiornamento di SQL Server 2016 aggiornamento cumulativo 2.
3. Installare R Services (In-Database) utilizzando il supporto RTM.

**Il modo corretto per eseguire l'aggiornamento:**

1. Installare SQL Server 2016 senza R Services.
2. Aggiornare SQL Server 2016 a livello di patch desiderato. Ad esempio, installare Service Pack 1 e quindi l'aggiornamento cumulativo 2.
3. Per aggiungere la funzionalità a livello di patch corretto, eseguire nuovamente l'installazione di SP1 e CU2 e quindi scegliere R Services (In-Database). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Finestra di avvio non viene avviato se 8dot3 notazione è obbligatorio

> [!NOTE] 
> Nei sistemi precedenti, è possibile eseguire start se non c'è un requisito di notazione 8dot3 Launchpad. Questo requisito è stato rimosso nelle versioni successive. SQL Server 2016 R Services è consigliabile installare uno dei valori seguenti:
> * SQL Server 2016 SP1 e CU1: [aggiornamento cumulativo 1 per SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, l'aggiornamento cumulativo 3 e ciò [hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), disponibile su richiesta.

Per compatibilità con R, SQL Server 2016 R Services (In-Database) è richiesto l'unità in cui la funzionalità viene installata per supportare la creazione di nomi file brevi usando *notazione 8dot3*. Viene chiamato anche un nome 8.3 file un *nome file breve*, e viene utilizzato per la compatibilità con le versioni precedenti di Microsoft Windows o un'alternativa ai nomi file lunghi.

Se il volume in cui si installa R non supporta nomi di file brevi, i processi che avviano R da SQL Server potrebbero non essere in grado di individuare l'eseguibile corretto e finestra di avvio non verrà avviato.

In alternativa, è possibile abilitare la notazione 8dot3 nel volume in cui è installato SQL Server e in cui è installato R Services. È quindi necessario specificare il nome breve per la directory di lavoro nel file di configurazione di R Services.

1. Per abilitare la notazione 8dot3, eseguire l'utilità fsutil con il *8dot3name* argomento come descritto qui: [8dot3name fsutil](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Dopo aver abilitata la notazione 8dot3, aprire il file RLauncher.config e prendere nota della proprietà di `WORKING_DIRECTORY`. Per informazioni su come trovare questo file, vedere [raccolta dei dati per la risoluzione dei problemi di Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Usare l'utilità fsutil con il *file* argomento per specificare un percorso di file breve per la cartella specificata nella WORKING_DIRECTORY.

4. Modificare il file di configurazione per specificare la directory di lavoro stesso immesso nella proprietà WORKING_DIRECTORY. In alternativa, è possibile specificare un'altra directory di lavoro e scegliere un percorso esistente che già è compatibile con la notazione 8dot3.


## <a name="next-steps"></a>Passaggi successivi

[Problemi noti e risoluzione dei problemi di Machine Learning Services](machine-learning-troubleshooting-faq.md)

[Raccolta dei dati per la risoluzione dei problemi di apprendimento automatico](data-collection-ml-troubleshooting-process.md)

[Domande frequenti sull'installazione e sull'aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Risolvere i problemi di connessioni al motore di database](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
