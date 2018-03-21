---
title: Installare SQL Server 2016 R Services (In-Database) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- installazione di SQL Server R Services
- installazione di servizi di SQL Server Machine Learning
- Configurare R Services
- installare l'apprendimento di SQL
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Active
ms.openlocfilehash: 0012b48101085b7ccb18695fbda1f25c10a6b90b
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="install-sql-server-2016-r-services-in-database"></a>Installare SQL Server 2016 R Services (In-Database) 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo illustra come installare e configurare **SQL Server 2016 R Services (In-Database)**. Se si dispone di SQL Server 2016, installare questa funzionalità per abilitare l'esecuzione del codice R in SQL Server.

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

+ SQL Server 2016 è obbligatorio. Se si dispone di SQL Server 2016, installare [SQL Server 2017 Machine Learning Services (In-Database)](sql-machine-learning-services-windows-install.md) invece.

+ Un'istanza del motore di database è obbligatorio. Non è possibile installare solo R, anche se è possibile aggiungerlo in modo incrementale a un'istanza esistente.

+ Non installare R Services in un cluster di failover. Il meccanismo di sicurezza utilizzato per isolare i processi R non è compatibile con un ambiente cluster di failover di Windows Server.

+ Non installare R Services in un controller di dominio. La parte di R Services del programma di installazione avrà esito negativo.

+ Non installare **Caratteristiche condivise** > **R Server (Standalone)** nello stesso computer che esegue un'istanza nel database. 

+ Installazione side-by-side con altre versioni di R e Python sono possibili perché l'istanza di SQL Server utilizza delle proprie copie delle distribuzioni di R e Anaconda open source. Tuttavia, in esecuzione il codice che usa R e Python nel computer SQL Server all'esterno di SQL Server possono causare diversi problemi:
    
  + Si utilizza un diverso eseguibile e la libreria diversa e ottengano risultati diversi, rispetto a quando si eseguono in SQL Server.
  + Script R e Python in esecuzione in librerie esterne non può essere gestito da SQL Server, iniziali a una contesa di risorse.
  
Se è stato usato qualsiasi versione precedente di pacchetti RevoScaleR o ambiente di sviluppo di Revolution Analitica, oppure se eventuali versioni non definitive di SQL Server 2016 è stato installato, è necessario disinstallarle. Che eseguono versioni precedenti e più recenti di RevoScaleR e altri pacchetti proprietarie non è supportata. Per informazioni sulla rimozione delle versioni precedenti, vedere [aggiornamento e domande frequenti sull'installazione di servizi di SQL Server Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Al termine dell'installazione, assicurarsi di completare la procedura aggiuntiva di post-configurazione descritta in questo articolo. Tali passaggi includono l'abilitazione di SQL Server da usare gli script esterni e aggiungendo gli account necessari per SQL Server eseguire i processi R per proprio conto. Le modifiche alla configurazione in genere richiedono il riavvio dell'istanza o un riavvio del servizio Launchpad.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch 

Microsoft ha rilevato un problema con una versione specifica dei file binari di Microsoft VC++ 2013 Runtime installati come prerequisito da SQL Server. Se l'aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server in determinati scenari. Prima di installare SQL Server, seguire le istruzioni in [Note sulla versione di SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) per vedere se il computer richiede una patch per i file binari di VC++ Runtime.  

## <a name="bkmk2016top"></a>Eseguire l'installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare Installazione guidata di SQL Server 2016.

2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.
    
   ![Installare R Services (In-Database)](media/2016-setup-installation-rsvcs.png "avviare l'installazione del motore di database con R Services")
   
3. Nel **Selezione funzionalità** pagina, selezionare le opzioni seguenti:

   - Selezionare **servizi motore di Database**. Il motore di database, è necessario in ogni istanza che usa il machine learning.
   - Selezionare **R Services (In-Database)**. Installa il supporto per l'utilizzo nel database di R.
    
     ![Selezione delle caratteristiche R Services](media/2016setup-rsvcs-features.png "selezionare queste funzionalità per R Services nel Database")

    > [!IMPORTANT]
    > Non installare R Server e R Services nello stesso momento. È normalmente verrebbe installare R Server (Standalone) per creare un ambiente che un esperto di dati o lo sviluppatore utilizza per connettersi a SQL Server e distribuire soluzioni R. Non è quindi necessario installare entrambe le soluzioni nello stesso computer.

4.  Nel **fornire il consenso per installare Microsoft R Open** fare clic su **Accept**.
  
    Il contratto di licenza è necessario per scaricare Microsoft R Open, che include una distribuzione di pacchetti di base R open source e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft R.
  
5. Dopo aver accettato il contratto di licenza, si verifica una breve pausa durante il programma di installazione è pronto. Fare clic su **successivo** quando il pulsante diventa disponibile.

6. Nel **pronto per l'installazione** pagina, verificare che gli elementi seguenti sono inclusi e quindi selezionano **installare**.

   + Servizi motore di database
   + R Services (In-Database)

    Nota del percorso della cartella nel percorso `..\Setup Bootstrap\Log` in cui sono archiviati i file di configurazione. Una volta completata l'installazione, è possibile esaminare i componenti installati nel file di riepilogo.

7. Una volta completato l'installazione, riavviare il computer.

##  <a name="bkmk_enableFeature"></a>Abilitare l'esecuzione dello script esterno

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > È possibile scaricare e installare la versione appropriata da questa pagina: [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > È anche possibile provare la versione di anteprima del [Studio operazioni SQL](https://docs.microsoft.com/sql/sql-operations-studio/what-is), che supporta le query su SQL Server e le attività amministrative.
  
2. Connettersi all'istanza in cui è installato Servizi di Machine Learning, fare clic su **nuova Query** per aprire una finestra query ed eseguire il comando seguente:

   ```SQL
   sp_configure
   ```
    A questo punto, il valore della proprietà `external scripts enabled` deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita. La funzionalità deve essere abilitata in modo esplicito dall'amministratore prima di poter eseguire script R o Python.
     
3. Per abilitare la funzionalità di script esterna, eseguire l'istruzione seguente:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Riavviare il servizio.

Una volta completato l'installazione, riavviare il motore di database prima di continuare a quella successiva, consentendo l'esecuzione di script.

Riavviare automaticamente anche il servizio viene riavviato la correlate [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

È possibile riavviare il servizio utilizzando il pulsante destro del mouse **riavviare** comando per l'istanza di SSMS o tramite il **Services** pannello nel Pannello di controllo oppure usando [Gestione configurazione SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Verificare l'installazione

Utilizzare la procedura seguente per verificare che tutti i componenti utilizzati per l'avvio dello script esterno siano in esecuzione.

1. In SQL Server Management Studio, aprire una nuova finestra query ed eseguire il comando seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Il valore di **run_value** dovrebbe ora essere impostato su 1.

2. Aprire la **Services** pannello o Gestione configurazione SQL Server e verificare **servizio Launchpad di SQL Server** è in esecuzione. È necessario disporre di un servizio per ogni istanza di motore di database che dispone di R o Python installato. Se non è in esecuzione, riavviare il servizio. Per altre informazioni, vedere [componenti per supportare l'integrazione di Python](../python/new-components-in-sql-server-to-support-python-integration.md).

7. Finestra di avvio è in esecuzione, sarà possibile eseguire R semplice per verificare che Runtime script esterni possono comunicare con SQL Server. 

    Aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], e quindi eseguire uno script simile al seguente:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Lo script può richiedere un po' da eseguire, la prima volta che viene caricato il runtime dello script esterno. I risultati dovrebbero essere simile al seguente:

    | hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> Configurazione aggiuntiva

Se il passaggio di verifica dello script esterno ha esito positivo, è possibile eseguire i comandi di Python da SQL Server Management Studio, Visual Studio Code o qualsiasi altro client che può inviare istruzioni T-SQL per il server.

Se si ha ricevuto un errore quando si esegue il comando, rivedere i passaggi di configurazione aggiuntive in questa sezione. Può accadere di dover creare configurazioni aggiuntive appropriate per il servizio o il database.

Scenari comuni che richiedono ulteriori modifiche includono:

* [Configurare Windows firewall per le connessioni in entrata](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Abilitare i protocolli di rete aggiuntivi](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Abilitare le connessioni remote](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Estendere le autorizzazioni predefinite per gli utenti remoti](#bkmk_configureAccounts)
* [Concedere l'autorizzazione per eseguire gli script esterni](#bkmk_AllowLogon)
* [Concedere l'accesso ai singoli database](#permissions-db)

> [!NOTE]
> Non tutte le modifiche elencate sono necessari e nessuno potrebbero essere necessarie. I requisiti dipendono lo schema di sicurezza, in cui è installato SQL Server e come si prevede che gli utenti per connettersi al database ed eseguire gli script esterni. Altri suggerimenti sulla risoluzione dei problemi sono disponibili qui: [domande frequenti sull'aggiornamento e l'installazione](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>Abilitare l'autenticazione implicita per il gruppo di account di avvio

Durante l'installazione, vengono creati alcuni nuovi account utente di Windows per eseguire le attività sotto il token di sicurezza del [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio. Quando un utente invia uno script R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibile, viene eseguito il mapping per l'identità dell'utente chiamante e viene eseguito lo script R per conto dell'utente. Questo nuovo servizio del motore di database supporta l'esecuzione di script esterni, chiamato sicuro *l'autenticazione implicita*.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione di R.

Tuttavia, se è necessario eseguire gli script R da un client di analisi scientifica dei dati remoti e si utilizza l'autenticazione di Windows, è necessario concedere questi account di lavoro autorizzato ad accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per proprio conto.

1. In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso**e quindi scegliere **Nuovo account di accesso**.
2. Nel **account di accesso - nuovo** finestra di dialogo **ricerca**.
3. Selezionare il **tipi di oggetti** e **gruppi** caselle di controllo e deselezionare tutte le altre caselle di controllo.
4. Fare clic su **avanzate**, verificare che il percorso in cui eseguire la ricerca del computer corrente e quindi fare clic su **trova**.
5. Scorrere l'elenco degli account di gruppo nel server fino a individuare una che inizia con `SQLRUserGroup`.
    
    + Il nome del gruppo a cui è associato il servizio Launchpad per il _istanza predefinita_ è sempre sufficiente **SQLRUserGroup**. Selezionare questo account solo per l'istanza predefinita.
    + Se si utilizza un _istanza denominata_, il nome dell'istanza viene aggiunto al nome predefinito, `SQLRUserGroup`. Di conseguenza, se l'istanza è denominata "MLTEST", il nome di gruppo utente predefinito per questa istanza sarebbe **SQLRUserGroupMLTest**.
5. Fare clic su **OK** per chiudere la finestra di dialogo Ricerca avanzata, verificare di aver selezionato l'account corretto per l'istanza. Ogni istanza può usare solo il proprio servizio Launchpad e il gruppo creato per tale servizio.
6. Fare clic su **OK** ancora una volta per chiudere la **Seleziona utente o gruppo** finestra di dialogo.
7. Nel **account di accesso - nuovo** finestra di dialogo, fare clic su **OK**. Per impostazione predefinita, l'account di accesso viene assegnato al ruolo **public** e dispone dell'autorizzazione per connettersi al motore di database.

### <a name="bkmk_AllowLogon"></a>Consentire agli utenti di eseguire gli script esterni

> [!NOTE]
> Se si utilizza un account di accesso SQL per l'esecuzione di script R in un contesto di calcolo di SQL Server, questo passaggio non è obbligatorio.

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un'istanza personalizzata, si sono in genere l'esecuzione di script come amministratore, o almeno come proprietario del database e pertanto con autorizzazioni implicite per varie operazioni, tutti i dati nel database e la possibilità di installare i nuovi pacchetti in base alle esigenze.

Tuttavia, in uno scenario aziendale, la maggior parte degli utenti, inclusi gli utenti che accedono a database con account di accesso SQL, non dispone tali autorizzazioni con privilegi elevati. Pertanto, per ogni utente che sarà in esecuzione gli script R, è necessario concedere le autorizzazioni per eseguire gli script in ogni database in cui verranno usati script esterni.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Serve aiuto per l'installazione? Non si è certi di aver eseguito tutti i passaggi? Utilizzare questi report personalizzati per controllare lo stato di installazione ed eseguire i passaggi aggiuntivi. 
> 
> [Monitorare i servizi di apprendimento macchina usando report personalizzati](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="permissions-db"></a> Concedere a utenti di lettura, scrittura o autorizzazioni DDL al database

L'account utente utilizzato per eseguire R potrebbe essere necessario per leggere dati da altri database, creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle. Pertanto, per ogni utente che determina l'esecuzione di script R, assicurarsi che l'utente disponga delle autorizzazioni appropriate per il database: *db_datareader*, *db_datawriter*, o *db_ddladmin*.

Ad esempio, l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente concede all'account di accesso SQL *MySQLLogin* i diritti per l'esecuzione di query T-SQL nel database *RSamples* . Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per ulteriori informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

Se si crea una soluzione di R in un computer client di analisi scientifica dei dati ed è necessario eseguire il codice utilizzando il computer SQL Server come contesto di calcolo, è possibile utilizzare un account di accesso SQL o l'autenticazione integrata di Windows.

* Per gli account di accesso SQL: assicurarsi che l'account abbia le autorizzazioni appropriate sul database in cui si leggeranno i dati. È possibile farlo mediante l'aggiunta *connettersi a* e *selezionare* autorizzazioni, o aggiungendo l'account di accesso per il *db_datareader* ruolo. Per gli account di accesso necessario per creare oggetti, aggiungere *ruoli DDL_admin* diritti. Per gli account di accesso deve salvare dati in tabelle, aggiungere l'account di accesso per il *db_datawriter* ruolo.

* Per l'autenticazione di Windows: potrebbe essere necessario configurare un'origine dati ODBC nel client di analisi scientifica dei dati che specifica il nome dell'istanza e altre informazioni di connessione. Per altre informazioni, vedere [Amministratore origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Ottimizzazioni suggerite

Ora che si dispone di tutto, è inoltre possibile ottimizzare il server per supportare l'apprendimento automatico oppure installare pretrained modelli.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si ritiene che è possibile usare R frequentemente o se si prevede che molti utenti da script in esecuzione contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati per il servizio Launchpad. Per altre informazioni, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Ottimizzare il server per l'esecuzione dello script esterno

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione servono per ottimizzare il bilanciamento del server per un'ampia gamma di servizi che sono supportate dal motore di database, che potrebbe includere di estrazione, trasformazione e caricamento (ETL) processi, creazione di report, il controllo, e le applicazioni che utilizzano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati. Pertanto, le impostazioni predefinite, si noterà che le risorse per machine learning in alcuni casi con restrizioni o limitate, in particolare nelle operazioni con utilizzo elevato della memoria.

Per garantire che i processi di machine learning sono priorità e assegnare in modo appropriato, è consigliabile utilizzare SQL Server Resource Governor per configurare un pool di risorse esterne. È inoltre possibile modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che eseguono il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione della memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account di R che può essere avviata dal [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per l'apprendimento](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Se si utilizza Standard Edition e non dispone di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows, monitoraggio, per semplificare la gestione delle risorse di server utilizzati da R. Per altre informazioni, vedere [monitoraggio e gestione dei servizi R](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Le soluzioni R che crei per SQL Server possono chiamare funzioni di base R, le funzioni dal packes properietary installato con SQL Server e pacchetti R di terze parti compatibili con la versione di R open source installati tramite SQL Server.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer o se sono installati pacchetti nelle librerie utente, non sarà in grado di utilizzare i pacchetti da T-SQL.

Il processo per l'installazione e la gestione dei pacchetti R è diverso in SQL Server 2016 e SQL Server 2017. In SQL Server 2016, un amministratore del database è necessario installare pacchetti R necessari per gli utenti. In SQL Server 2017, è possibile impostare gruppi di utenti di condividere i pacchetti a livello di singolo database o configurare i ruoli di database per consentire agli utenti di installare i propri pacchetti. Per altre informazioni, vedere [gestione del pacchetto](../r/r-package-management-for-sql-server-r-services.md).


## <a name="get-help"></a>Supporto

Assistenza sull'installazione o aggiornamento? Per le risposte alle domande più comuni e sui problemi noti, vedere l'articolo seguente:

* [Aggiornamento e l'installazione domande frequenti - servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi più comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori R possono iniziare a usare alcuni semplici esempi e apprendere le nozioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Esecuzione di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: In-database analitica per gli sviluppatori R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Per visualizzare gli esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).


