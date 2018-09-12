---
title: Installare SQL Server Machine Learning Services (In-Database) in Windows | Microsoft Docs
description: R in SQL Server o Python in SQL Server è disponibile quando si installa Servizi Machine Learning di SQL Server 2017 in Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 285745a36552a0029ae0df383fc629b94632d524
ms.sourcegitcommit: 8008ea52e25e65baae236631b48ddfc33014a5e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44311651"
---
# <a name="install-sql-server-machine-learning-services"></a>Installare SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

A partire da SQL Server 2017, R e Python supportano per analitica nel database viene fornito in SQL Server Machine Learning Services, il successore [SQL Server R Services](../r/sql-server-r-services.md) introdotta in SQL Server 2016. Librerie di funzioni sono disponibili in R e Python ed eseguire come script esterni in un'istanza del motore di database. 

Questo articolo illustra come installare il componente di machine learning tramite l'esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata e segue il le istruzioni visualizzate.

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

+ Il programma di installazione di SQL Server 2017 è necessaria per servizi di Machine Learning con R e Python. Se invece si dispone di supporto di installazione di SQL Server 2016, vedere [installare SQL Server 2016 R Services](sql-r-services-windows-install.md) per ottenere supporto del linguaggio R.

+ È necessaria un'istanza di motore di database. È possibile installare solo le funzionalità R o Python, anche se è possibile aggiungerli in modo incrementale a un'istanza esistente.

+ Non installare servizi di Machine Learning in un cluster di failover. Il meccanismo di sicurezza utilizzato per isolare i processi R e Python non è compatibile con un ambiente cluster di failover di Windows Server.

+ Non installare servizi di Machine Learning in un controller di dominio. La parte di servizi di Machine Learning del programma di installazione avrà esito negativo.

+ Non installare **funzionalità condivise** > **Machine Learning Server (Standalone)** nello stesso computer che esegue un'istanza nel database. Un server autonomo verrà si contendono le risorse stesse, compromettendo le prestazioni di entrambe le installazioni.

+ Installazione side-by-side con altre versioni di R e Python è supportata ma non consigliata. È supportata perché istanza di SQL Server Usa una proprio copie delle distribuzioni open source R e Anaconda. Ma non è consigliabile perché l'esecuzione del codice che usa R e Python nel computer SQL Server all'esterno di SQL Server può causare problemi diversi:
    
  + Si usa una libreria diversa e un diverso eseguibile e ottengano risultati diversi, rispetto a quando si eseguono in SQL Server.
  + Gli script R e Python in esecuzione nelle librerie esterne non possono essere gestiti da SQL Server, causando una contesa delle risorse.
  
> [!IMPORTANT]
> Al termine dell'installazione, assicurarsi di completare i passaggi di post-configurazione descritti in questo articolo. Tali passaggi includono l'abilitazione di SQL Server per usare gli script esterni e l'aggiunta di account necessari per SQL Server eseguire processi R e Python per tuo conto. Le modifiche alla configurazione in genere richiedono un riavvio dell'istanza o un riavvio del servizio Launchpad.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare l'installazione guidata di SQL Server 2017. È possibile scaricare 
  
2. Nel **installazione** scheda, seleziona **nuova installazione SQL Server autonomo o aggiungere caratteristiche a un'installazione esistente**.

   ![Installazione di Machine Learning Services nel database](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Nella pagina **Selezione funzionalità** selezionare queste opzioni:
  
    -   **Servizi motore di database**
  
         Per usare R e Python con SQL Server, è necessario installare un'istanza del motore di database. È possibile usare un valore predefinito o un'istanza denominata.
  
    -   **Machine Learning Services (In-Database)**
  
         Questa opzione per installare i servizi di database che supportano R e l'esecuzione di script Python.

    -   **R**

        Selezionare questa opzione per aggiungere i pacchetti Microsoft R, interprete e open source R. 

    -   **Python**

        Selezionare questa opzione per aggiungere i pacchetti Python di Microsoft, il file eseguibile Python 3.5 e selezionare la distribuzione Anaconda librerie.
        
        ![Opzioni per R e Python delle funzionalità](media/2017setup-features-page-mls-rpy.png "opzioni di installazione per Python")

        > [!NOTE]
        > 
        > Non selezionare l'opzione **Machine Learning Server (Standalone)**. L'opzione di installazione di Machine Learning Server sotto **Caratteristiche condivise** è destinato all'uso in un computer separato.

4. Nel **fornire il consenso per installare R** pagina, selezionare **Accept**. Il contratto di licenza include Microsoft R Open, che include una distribuzione di pacchetti R open source di base e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft.

5. Nel **fornire il consenso per installare Python** pagina, selezionare **Accept**. Il contratto di licenza open source di Python include inoltre Anaconda e strumenti correlati, nonché alcune nuove librerie Python dal team di sviluppo Microsoft.
     
     ![Contratto di licenza di Python](media/2017setup-python-license.png "licenza contratto per Python")
  
    > [!NOTE]
    >  Se il computer in che uso non ha accesso a internet, è possibile sospendere il programma di installazione in questo momento per scaricare i programmi di installazione separatamente. Per altre informazioni, vedere [installa i componenti di apprendimento automatico senza accesso a internet](../install/sql-ml-component-install-without-internet-access.md).
  
     Selezionare **Accept**, attendere finché il **successiva** pulsante diventa attivo e quindi selezionare **Avanti**.
  
6. Nel **pronto per l'installazione** pagina, verificare che queste selezioni sono incluse e selezionare **installare**.
  
    + Servizi motore di database
    + Machine Learning Services (In-Database)
    + R o Python oppure entrambi

    Nota del percorso della cartella nel percorso `..\Setup Bootstrap\Log` in cui sono archiviati i file di configurazione. Una volta completato il programma di installazione, è possibile esaminare i componenti installati nel file di riepilogo.

7. Al termine dell'installazione, se viene richiesto di riavviare il computer, farlo ora. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="bkmk_enableFeature"></a>Abilitare l'esecuzione di script

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > È possibile scaricare e installare la versione appropriata da questa pagina: [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > È anche possibile provare la versione di anteprima dei [SQL Operations Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is), che supporta le attività amministrative e query su SQL Server.
  
2. Connettersi all'istanza in cui è installato Servizi di Machine Learning, fare clic su **nuova Query** per aprire una finestra query ed eseguire il comando seguente:

   ```SQL
   sp_configure
   ```

    A questo punto, il valore della proprietà `external scripts enabled` deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita. La funzionalità deve essere abilitata in modo esplicito da un amministratore prima di poter eseguire script R o Python.
    
3.  Per abilitare la funzionalità di script esterne, eseguire l'istruzione seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Se è già stata abilitata la funzionalità per il linguaggio R, non vengono eseguiti riconfigurare una seconda volta per Python. La piattaforma di estendibilità sottostante supporta entrambi i linguaggi.

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
   
3. Se Launchpad è in esecuzione, è necessario essere in grado di eseguire semplici script R e Python per verificare che il runtime di scripting esterno possa comunicare con SQL Server.

   Aprire una nuova **Query** finestra in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi eseguire uno script simile al seguente:
    
    + Per R
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Per Python
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

 **Risultati**

    Lo script può richiedere del tempo per l'esecuzione, la prima volta che viene caricato il runtime dello script esterno. I risultati dovrebbero essere simile al seguente:

    | hello |
    |----|
    | 1|


> [!NOTE]
> Le colonne o le intestazioni usate nello script di Python non vengono restituite, per impostazione predefinita. Per aggiungere nomi di colonna per l'output, è necessario specificare lo schema per il set di dati restituito. Eseguire questa operazione usando il parametro con risultati della stored procedure, le colonne di denominazione e specificando il tipo di dati SQL.
> 
> Ad esempio, è possibile aggiungere la riga seguente per generare un nome di colonna arbitrario: `WITH RESULT SETS ((Col1 AS int))`

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Se il passaggio di verifica dello script esterno ha esito positivo, è possibile eseguire i comandi di Python da SQL Server Management Studio, Visual Studio Code o qualsiasi altro client che può inviare istruzioni T-SQL al server.

Se è stato visualizzato un errore quando si esegue il comando, rivedere i passaggi di configurazione aggiuntive in questa sezione. Si potrebbe essere necessario effettuare altre configurazioni appropriate per il servizio o il database.

Scenari comuni che richiedono modifiche aggiuntive includono:

* [Configurare Windows firewall per le connessioni in ingresso](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Abilitare i protocolli di rete aggiuntivi](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Abilitare le connessioni remote](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Estendere le autorizzazioni predefinite per gli utenti remoti](#bkmk_configureAccounts)
* [Concedere l'autorizzazione per eseguire gli script esterni](#permissions-external-script)
* [Concedere l'accesso ai singoli database](#permissions-db)

> [!NOTE]
> Non tutte le modifiche elencate sono necessari e nessuno potrebbero essere necessarie. I requisiti variano a seconda lo schema di sicurezza, in cui è installato SQL Server e come si prevede che gli utenti per connettersi al database ed eseguire gli script esterni. Altri suggerimenti sulla risoluzione dei problemi sono disponibili qui: [domande frequenti su installazione e aggiornamento](../r/upgrade-and-installation-faq-sql-server-r-services.md)

###  <a name="bkmk_configureAccounts"></a> Abilitare l'autenticazione implicita per gruppo di account Launchpad

Durante l'installazione, vengono creati diversi nuovi account utente di Windows allo scopo di eseguire attività in base al token di sicurezza del servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Quando un utente invia uno script Python o R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili. Quindi ne esegue il mapping all'identità dell'utente chiamante e viene eseguito lo script per conto dell'utente.

Questa operazione viene definita *l'autenticazione implicita*, ed è un servizio del motore di database. Questo servizio supporta l'esecuzione sicura di script esterni in SQL Server 2016 e SQL Server 2017.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione di script esterni.

> [!IMPORTANT]
> Il gruppo di lavoro viene denominato **SQLRUserGroup** indipendentemente dal fatto che sia installato R o Python. È presente un gruppo singolo per ogni istanza.

Se è necessario eseguire gli script da un client di analisi scientifica dei dati remoti e si usa l'autenticazione di Windows, esistono ulteriori considerazioni. Questi account di lavoro devono essere concessa l'autorizzazione per accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per tuo conto.

1. Nelle [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Esplora oggetti, espandere **sicurezza**. Quindi fare doppio clic su **gli account di accesso**e selezionare **nuovo account di accesso**.
2. Nel **account di accesso - nuovo** finestra di dialogo **ricerca**.
3. Selezionare **tipi di oggetti**e selezionare **gruppi**. Cancellare tutto il resto.
4. Nelle **immettere il nome dell'oggetto da selezionare**, digitare *SQLRUserGroup*e selezionare **Controlla nomi**.
5. Il nome del gruppo locale associato al servizio Launchpad dell'istanza deve essere risolto in un nome simile a *nomeistanza\SQLRUserGroup*. Fare clic su **OK**.
6. Per impostazione predefinita, il gruppo viene assegnato per il **pubblica** ruolo, e dispone dell'autorizzazione per connettersi al motore di database.
7. Fare clic su **OK**.

> [!NOTE]
> Se si usa un' **account di accesso SQL** per l'esecuzione degli script in un contesto di calcolo di SQL Server, questo passaggio aggiuntivo non è obbligatorio.

### <a name="permissions-external-script"></a> Concedere agli utenti l'autorizzazione per eseguire gli script esterni

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manualmente, mentre si eseguono gli script R o Python nella tua istanza di, è in genere eseguire gli script come amministratore. In questo modo, si dispone dell'autorizzazione implicita su varie operazioni e tutti i dati nel database.

La maggior parte degli utenti, tuttavia, si dispone di tali autorizzazioni con privilegi elevati. Ad esempio, gli utenti in un'organizzazione che usano account di accesso SQL per accedere al database in genere non è le autorizzazioni con privilegi elevate. Pertanto, per ogni utente che usa R o Python, è necessario concedere agli utenti di servizi di Machine Learning l'autorizzazione per eseguire gli script esterni in ogni database in cui viene utilizzata la lingua. Ecco come:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorizzazioni non sono specifiche del linguaggio di script supportato. In altre parole, non esistono livelli di autorizzazione separati per lo script R e lo script Python. Se è necessario mantenere separate le autorizzazioni per queste lingue, installare R e Python in istanze separate.

### <a name="permissions-db"></a> Assegnare la definizione di lettura, scrittura o dati agli utenti le autorizzazioni di language (DDL) per database

Mentre un utente è in esecuzione gli script, l'utente potrebbe essere necessario leggere i dati da altri database. L'utente potrebbe essere necessario anche creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle.

Per ogni account utente di Windows o account di accesso SQL che esegue gli script R o Python, verificare che abbia le autorizzazioni appropriate sul database specifico: `db_datareader`, `db_datawriter`, o `db_ddladmin`.

Ad esempio, il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione offre l'accesso SQL *MySQLLogin* i diritti per eseguire query T-SQL *ML_Samples* database. Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per altre informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

È possibile creare una soluzione di machine learning in un computer client di analisi scientifica dei dati. Se è necessario eseguire il codice usando il computer SQL Server come contesto di calcolo, sono disponibili due opzioni: accedere all'istanza con un account di accesso SQL o utilizzando un Windows dell'account.

+ Per gli account di accesso SQL: assicurarsi che l'account di accesso disponga delle autorizzazioni appropriate per il database in cui si esegue la lettura dei dati. Questo scopo, è possibile aggiungere *connettersi a* e *seleziona* autorizzazioni, o aggiungendo l'account di accesso per il `db_datareader` ruolo. Per creare oggetti, assegnare `DDL_admin` diritti. Se è necessario salvare i dati in tabelle, aggiungere il `db_datawriter` ruolo.

+ Per l'autenticazione di Windows: si potrebbe essere necessario creare un'origine dati ODBC nel client di data science che specifica il nome dell'istanza e altre informazioni sulla connessione. Per altre informazioni, vedere [Amministrazione origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Delle ottimizzazioni suggerite

Ora che avete accertato il corretto funzionamento, si potrebbe anche voler ottimizzare il server per supportare l'apprendimento automatico o installazione pretrained modelli.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si prevede che molti utenti sia in esecuzione gli script contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati al servizio Launchpad. Per altre informazioni, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Ottimizzare il server per l'esecuzione di script

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione consentono di ottimizzare l'equilibrio tra il server per un'ampia gamma di servizi che sono supportati dal motore di database, che potrebbe includere estrazione, trasformazione e caricamento (ETL) dei processi, creazione di report, il controllo, e le applicazioni che usano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei dati. Di conseguenza, le impostazioni predefinite, si noterà che le risorse per machine learning vengono talvolta limitate o limitate, in particolare nelle operazioni a elevato utilizzo di memoria.

Per garantire che i processi di machine learning sono la priorità e risorse assegnati in modo appropriato, è consigliabile utilizzare SQL Server Resource Governor per configurare un pool di risorse esterne. Potrebbe anche voler modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che vengono eseguiti nel [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account R che può essere avviata dal [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per l'apprendimento](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Se si usa l'edizione Standard e sono privi di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows, che consente di gestire le risorse del server di monitoraggio. Per altre informazioni, vedere [monitoraggio e gestione dei servizi R](../r/managing-and-monitoring-r-solutions.md) e [monitoraggio e gestione dei servizi Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Le soluzioni R create per SQL Server, è possono chiamare funzioni R di base, funzioni dai pacchetti proprietari installati con SQL Server e i pacchetti R di terze parti compatibile con la versione di R open source installati tramite SQL Server.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer, o se si installano pacchetti nelle librerie utente, sarà possibile usare questi pacchetti da T-SQL.

Il processo per l'installazione e la gestione dei pacchetti di R è diverso in SQL Server 2016 e SQL Server 2017. In SQL Server 2016, un amministratore del database è necessario installare pacchetti R che gli utenti devono avere. In SQL Server 2017, è possibile configurare i gruppi di utenti di condividere i pacchetti in un livello di database, o configurare i ruoli di database per consentire agli utenti di installare i propri pacchetti. Per altre informazioni, vedere [installare nuovi pacchetti R in SQL Server](../r/install-additional-r-packages-on-sql-server.md).


## <a name="get-help"></a>Supporto

Serve aiuto con l'installazione o aggiornamento? Per le risposte alle domande più frequenti e problemi noti, vedere l'articolo seguente:

* [Aggiornamento e installazione domande frequenti: servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato dell'installazione dell'istanza e risolvere problemi comuni, provare questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori di R possono iniziare a usare alcuni semplici esempi e informazioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Eseguire R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: Nel database analitica per gli sviluppatori di R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python è possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Eseguire Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: Nel database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare esempi di machine learning basate su scenari reali, vedere [di Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).
