---
title: Installare SQL Server 2016 R Services (In-Database) | Microsoft Docs
description: R in SQL Server è disponibile quando si installa SQL Server 2016 R Services in Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 92d477434460c9395342e1a522173a301b5a0ad8
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713303"
---
# <a name="install-sql-server-2016-r-services"></a>Installare SQL Server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo illustra come installare e configurare **SQL Server 2016 R Services**. Se si dispone di SQL Server 2016, installare questa funzionalità per consentire l'esecuzione del codice R in SQL Server.

In SQL Server 2017, integrazione di R è disponibile in [servizi di Machine Learning](../r/r-server-standalone.md), che riflette l'aggiunta di Python. Se si vuole eseguire l'integrazione di R e disporre dei supporti di installazione di SQL Server 2017, vedere [installare SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md) per aggiungere la funzionalità. 

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

+ È necessaria un'istanza di motore di database. È possibile installare solo R, anche se è possibile aggiungerlo in modo incrementale a un'istanza esistente.

+ Non installare R Services in un cluster di failover. Il meccanismo di sicurezza usato per isolare i processi R non è compatibile con un ambiente cluster di failover di Windows Server.

+ Non installare R Services in un controller di dominio. La parte di R Services del programma di installazione avrà esito negativo.

+ Non installare **funzionalità condivise** > **R Server (Standalone)** nello stesso computer che esegue un'istanza nel database. 

  Installazione side-by-side con altre versioni di R e Python sono possibili in quanto l'istanza di SQL Server Usa una proprio copie delle distribuzioni open source R e Anaconda. Esecuzione di codice che usa R e Python nel computer SQL Server all'esterno di SQL Server, tuttavia, può causare problemi diversi:
    
  + Si usa una libreria diversa e un diverso eseguibile e ottengano risultati diversi, rispetto a quando si eseguono in SQL Server.
  + Gli script R e Python in esecuzione nelle librerie esterne non possono essere gestiti da SQL Server, causando una contesa delle risorse.
  
Se è stata usata una versione precedente dell'ambiente di sviluppo Revolution Analitica o dei pacchetti RevoScaleR o se è installata una versione di versioni non definitive di SQL Server 2016, è necessario disinstallarle. Che eseguono versioni precedenti e più recenti di RevoScaleR e altri pacchetti proprietari non è supportato. Per informazioni sulla rimozione di versioni precedenti, vedere [aggiornamento e domande frequenti sull'installazione di SQL Server Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Al termine dell'installazione, assicurarsi di completare i passaggi di post-configurazione aggiuntivi descritti in questo articolo. Tali passaggi includono l'abilitazione di SQL Server per usare gli script esterni e l'aggiunta di account necessari per SQL Server eseguire processi R per tuo conto. Le modifiche alla configurazione in genere richiedono un riavvio dell'istanza o un riavvio del servizio Launchpad.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch 

Microsoft ha rilevato un problema con una versione specifica dei file binari di Microsoft VC++ 2013 Runtime installati come prerequisito da SQL Server. Se l'aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server in determinati scenari. Prima di installare SQL Server, seguire le istruzioni in [Note sulla versione di SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) per vedere se il computer richiede una patch per i file binari di VC++ Runtime.  

## <a name="bkmk2016top"></a>Eseguire il programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare l'installazione guidata di SQL Server 2016.

2. Nel **installazione** scheda, seleziona **nuova installazione SQL Server autonomo o aggiungere caratteristiche a un'installazione esistente**.
    
   ![Installare R Services (In-Database)](media/2016-setup-installation-rsvcs.png "avviare l'installazione del motore di database con R Services")
   
3. Nel **Selezione funzionalità** pagina, selezionare le opzioni seguenti:

   - Selezionare **servizi motore di Database**. Il motore di database è obbligatorio in ogni istanza che usa machine learning.
   - Selezionare **R Services (In-Database)**. Installa il supporto per l'uso nel database di R.
    
     ![Selezione delle funzionalità R Services](media/2016setup-rsvcs-features.png "selezionare queste funzionalità per R Services In-Database")

    > [!IMPORTANT]
    > Non installare R Server e R Services nello stesso momento. È in genere necessario installare R Server (Standalone) per creare un ambiente che usa un data scientist o sviluppatore per la connessione a SQL Server e distribuire soluzioni R. Non è quindi necessario installare entrambe le soluzioni nello stesso computer.

4.  Nel **fornire il consenso per installare Microsoft R Open** pagina, fare clic su **Accept**.
  
    Il contratto di licenza è necessario per scaricare Microsoft R Open, che include una distribuzione di pacchetti R open source di base e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo di Microsoft R.
  
5. Dopo aver accettato il contratto di licenza, si verifica una breve pausa durante il programma di installazione è pronto. Fare clic su **successivo** quando il pulsante diventa disponibile.

6. Nel **pronto per l'installazione** pagina, verificare che gli elementi seguenti sono inclusi e quindi selezionare **installare**.

   + Servizi motore di database
   + R Services (In-Database)

    Nota del percorso della cartella nel percorso `..\Setup Bootstrap\Log` in cui sono archiviati i file di configurazione. Una volta completato il programma di installazione, è possibile esaminare i componenti installati nel file di riepilogo.

7. Al termine dell'installazione, se viene richiesto di riavviare il computer, farlo ora. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).


##  <a name="bkmk_enableFeature"></a>Abilitare l'esecuzione di script

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > È possibile scaricare e installare la versione appropriata da questa pagina: [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > È anche possibile provare la versione di anteprima dei [Studio di Azure Data](../../azure-data-studio/what-is.md), che supporta le attività amministrative e query su SQL Server.
  
2. Connettersi all'istanza in cui è installato Servizi di Machine Learning, fare clic su **nuova Query** per aprire una finestra query ed eseguire il comando seguente:

   ```SQL
   sp_configure
   ```
    A questo punto, il valore della proprietà `external scripts enabled` deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita. La funzionalità deve essere abilitata in modo esplicito da un amministratore prima di poter eseguire script R o Python.
     
3. Per abilitare la funzionalità di script esterne, eseguire l'istruzione seguente:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Riavviare il servizio.

Una volta completata l'installazione, riavviare il motore di database prima di procedere al successivo, consentendo l'esecuzione dello script.

Riavviare automaticamente anche il servizio viene riavviato correlato [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

È possibile riavviare il servizio utilizzando il pulsante destro del mouse **riavviare** comando per l'istanza di SQL Server Management Studio o tramite il **Services** pannello nel Pannello di controllo oppure usando [Gestione configurazione SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Verificare l'installazione

Utilizzare la procedura seguente per verificare che tutti i componenti usati per avviare script esterni siano in esecuzione.

1. In SQL Server Management Studio, aprire una nuova finestra query ed eseguire il comando seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Il valore di **run_value** dovrebbe ora essere impostato su 1.

2. Aprire il **Services** pannello o Gestione configurazione SQL Server e verificare **Launchpad di SQL Server service** è in esecuzione. È necessario un servizio per ogni istanza di motore di database con R o Python installato. Per altre informazioni sul servizio, vedere [framework di estendibilità](../concepts/extensibility-framework.md).

7. Se Launchpad è in esecuzione, sarà possibile eseguire R semplice per verificare che il runtime di scripting esterno possa comunicare con SQL Server. 

    Aprire una nuova **Query** finestra in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi eseguire uno script simile al seguente:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Lo script può richiedere del tempo per l'esecuzione, la prima volta che viene caricato il runtime dello script esterno. I risultati dovrebbero essere simile al seguente:

    | hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> Configurazione aggiuntiva

Se il passaggio di verifica dello script esterno ha esito positivo, è possibile eseguire i comandi di Python da SQL Server Management Studio, Visual Studio Code o qualsiasi altro client che può inviare istruzioni T-SQL al server.

Se è stato visualizzato un errore quando si esegue il comando, rivedere i passaggi di configurazione aggiuntive in questa sezione. Si potrebbe essere necessario effettuare altre configurazioni appropriate per il servizio o il database.

Scenari comuni che richiedono modifiche aggiuntive includono:

* [Configurare Windows firewall per le connessioni in ingresso](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Abilitare i protocolli di rete aggiuntivi](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Abilitare le connessioni remote](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Estendere le autorizzazioni predefinite per gli utenti remoti](#bkmk_configureAccounts)
* [Concedere l'autorizzazione per eseguire gli script esterni](#bkmk_AllowLogon)
* [Concedere l'accesso ai singoli database](#permissions-db)

> [!NOTE]
> Non tutte le modifiche elencate sono necessari e nessuno potrebbero essere necessarie. I requisiti variano a seconda lo schema di sicurezza, in cui è installato SQL Server e come si prevede che gli utenti per connettersi al database ed eseguire gli script esterni. Altri suggerimenti sulla risoluzione dei problemi sono disponibili qui: [domande frequenti su installazione e aggiornamento](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>Abilitare l'autenticazione implicita per il gruppo di account Launchpad

Durante l'installazione, vengono creati alcuni nuovi account utente di Windows per l'esecuzione di attività con il token di sicurezza del [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio. Quando un utente invia uno script R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili, viene eseguito il mapping all'identità dell'utente chiamante ed esegue lo script R per conto dell'utente. Questo nuovo servizio del motore di database supporta l'esecuzione sicura di script esterni, definito *l'autenticazione implicita*.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione di R.

Tuttavia, se è necessario eseguire gli script R da un client di analisi scientifica dei dati remoti e Usa l'autenticazione di Windows, è necessario concedere questi account di lavoro l'autorizzazione per accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per tuo conto.

1. In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso**e quindi scegliere **Nuovo account di accesso**.
2. Nel **account di accesso - nuovo** finestra di dialogo **ricerca**.
3. Selezionare il **tipi di oggetti** e **gruppi** caselle di controllo e deselezionare tutte le altre caselle di controllo.
4. Fare clic su **avanzate**, verificare che la posizione in cui cercare il computer corrente e quindi fare clic su **trova ora**.
5. Scorrere l'elenco degli account di gruppo nel server fino a individuare che inizia con `SQLRUserGroup`.
    
    + Il nome del gruppo di cui è associato il servizio Launchpad per il _istanza predefinita_ è sempre sufficiente **SQLRUserGroup**. Selezionare questo account solo per l'istanza predefinita.
    + Se si usa un' _istanza denominata_, il nome dell'istanza viene aggiunto al nome predefinito, `SQLRUserGroup`. Di conseguenza, se l'istanza è denominata "MLTEST", il nome di gruppo utente predefinito per questa istanza sarebbe **SQLRUserGroupMLTest**.
5. Fare clic su **OK** per chiudere la finestra di dialogo di ricerca avanzata, verificare di aver selezionato l'account corretto per l'istanza. Ogni istanza può usare solo il proprio servizio Launchpad e il gruppo creato per tale servizio.
6. Fare clic su **OK** ancora una volta per chiudere la **Seleziona utente o gruppo** nella finestra di dialogo.
7. Nel **account di accesso - nuovo** finestra di dialogo, fare clic su **OK**. Per impostazione predefinita, l'account di accesso viene assegnato al ruolo **public** e dispone dell'autorizzazione per connettersi al motore di database.

### <a name="bkmk_AllowLogon"></a>Concedere agli utenti l'autorizzazione per eseguire gli script esterni

> [!NOTE]
> Se si usa un account di accesso SQL per l'esecuzione di script R in un contesto di calcolo di SQL Server, questo passaggio non è obbligatorio.

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nella tua istanza di, si sono in genere l'esecuzione di script come amministratore, o almeno un proprietario del database, e pertanto disporre di autorizzazioni implicite per varie operazioni, tutti i dati nel database e la possibilità di installare nuovi pacchetti in base alle esigenze.

Tuttavia, in uno scenario aziendale, la maggior parte degli utenti, inclusi quelli che hanno accesso al database usando l'account di accesso SQL, non hanno tali autorizzazioni con privilegi elevati. Pertanto, per ogni utente che eseguirà script R, è necessario concedere le autorizzazioni per eseguire gli script in ogni database in cui verranno usati gli script esterni.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Serve aiuto per l'installazione? Non si è certi di aver eseguito tutti i passaggi? Usare questi report personalizzati per controllare lo stato di installazione ed eseguire passaggi aggiuntivi. 
> 
> [Monitorare servizi di Machine Learning tramite i report personalizzati](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="permissions-db"></a> Assegnare l'utenti di lettura, scrittura o autorizzazioni DDL per il database

L'account utente usato per eseguire R potrebbe essere necessario per leggere i dati da altri database, creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle. Pertanto, per ogni utente che eseguirà script R, verificare che l'utente disponga delle autorizzazioni appropriate sul database: *db_datareader*, *db_datawriter*, o *db_ddladmin*.

Ad esempio, l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente concede all'account di accesso SQL *MySQLLogin* i diritti per l'esecuzione di query T-SQL nel database *RSamples* . Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per altre informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

Se si crea una soluzione R in un computer client di analisi scientifica dei dati ed è necessario eseguire il codice usando il computer SQL Server come contesto di calcolo, è possibile usare un account di accesso SQL o l'autenticazione integrata di Windows.

* Per gli account di accesso SQL: assicurarsi che l'account abbia le autorizzazioni appropriate sul database in cui si leggeranno i dati. È possibile farlo aggiungendo *connettersi a* e *selezionare* autorizzazioni, o aggiungendo l'account di accesso per il *db_datareader* ruolo. Per gli account di accesso necessario per creare oggetti, aggiungere *DDL_admin* diritti. Per gli account di accesso deve salvare dati in tabelle, aggiungere l'account di accesso per il *db_datawriter* ruolo.

* Per l'autenticazione di Windows: si potrebbe essere necessario configurare un'origine dati ODBC nel client di data science che specifica il nome dell'istanza e altre informazioni sulla connessione. Per altre informazioni, vedere [Amministrazione origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Delle ottimizzazioni suggerite

Ora che avete accertato il corretto funzionamento, si potrebbe anche voler ottimizzare il server per supportare l'apprendimento automatico o installazione pretrained modelli.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si ritiene che è possibile usare R in modo rilevante, o se si prevede che molti utenti sia gli script in esecuzione contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati al servizio Launchpad. Per altre informazioni, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Ottimizzare il server per l'esecuzione di script esterni

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione consentono di ottimizzare l'equilibrio tra il server per un'ampia gamma di servizi che sono supportati dal motore di database, che potrebbe includere estrazione, trasformazione e caricamento (ETL) dei processi, creazione di report, il controllo, e le applicazioni che usano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei dati. Di conseguenza, le impostazioni predefinite, si noterà che le risorse per machine learning vengono talvolta limitate o limitate, in particolare nelle operazioni a elevato utilizzo di memoria.

Per garantire che i processi di machine learning sono la priorità e risorse assegnati in modo appropriato, è consigliabile utilizzare SQL Server Resource Governor per configurare un pool di risorse esterne. Potrebbe anche voler modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che vengono eseguiti nel [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account R che può essere avviata dal [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per l'apprendimento](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Se si usa l'edizione Standard e sono privi di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows di monitoraggio, che consente di gestire le risorse di server che vengono usate da R. Per altre informazioni, vedere [monitoraggio e gestione dei servizi R](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Le soluzioni R create per SQL Server, è possono chiamare funzioni R di base, funzioni dai pacchetti proprietari installati con SQL Server e i pacchetti R di terze parti compatibile con la versione di R open source installati tramite SQL Server.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer, o se si installano pacchetti nelle librerie utente, sarà possibile usare questi pacchetti da T-SQL.

Il processo per l'installazione e la gestione dei pacchetti di R è diverso in SQL Server 2016 e SQL Server 2017. In SQL Server 2016, un amministratore del database è necessario installare pacchetti R che gli utenti devono avere. In SQL Server 2017, è possibile configurare i gruppi di utenti di condividere i pacchetti in un livello di database, o configurare i ruoli di database per consentire agli utenti di installare i propri pacchetti. Per altre informazioni, vedere [installare nuovi pacchetti R](../r/install-additional-r-packages-on-sql-server.md).


## <a name="get-help"></a>Supporto

Serve aiuto con l'installazione o aggiornamento? Per le risposte alle domande più frequenti e problemi noti, vedere l'articolo seguente:

* [Aggiornamento e installazione domande frequenti: servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato dell'installazione dell'istanza e risolvere problemi comuni, provare questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori di R possono iniziare a usare alcuni semplici esempi e informazioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Eseguire R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: Nel database analitica per gli sviluppatori di R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Per visualizzare esempi di machine learning basate su scenari reali, vedere [di Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).


