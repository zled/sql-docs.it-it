---
title: Installare SQL Server 2017 di Machine Learning Services (In-Database) in Windows | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 23fed22efe90a91905c4b36c967ad5fa72717b3f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585873"
---
# <a name="install-sql-server-2017-machine-learning-services-in-database-on-windows"></a>Installare SQL Server 2017 di Machine Learning Services (In-Database) in Windows 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Consente di aggiungere il componente di Machine Learning Services di SQL Server nel database analitica predittiva, analisi statistica, visualizzazione e algoritmi di machine learning. Librerie di funzioni sono disponibili in R e Python ed eseguire come script esterno in un'istanza del motore di database. 

In questo articolo viene descritto come installare il componente di machine learning eseguendo il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata e segue il le istruzioni visualizzate.

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

+ Il programma di installazione di SQL Server 2017 è necessaria se si desidera installare servizi di Machine Learning con supporto delle lingue per R, Python o entrambi. Se invece si dispone di supporto di installazione di SQL Server 2016, è possibile installare [SQL Server 2016 R Services (In-Database)](sql-r-services-windows-install.md) per ottenere supporto del linguaggio R.

+ Un'istanza del motore di database è obbligatorio. Non è possibile installare solo R o Python funzionalità, anche se è possibile aggiungerli in modo incrementale a un'istanza esistente.

+ Non installare servizi di Machine Learning in un cluster di failover. Il meccanismo di sicurezza utilizzato per isolare i processi R e Python non è compatibile con un ambiente cluster di failover di Windows Server.

+ Non installare servizi di Machine Learning in un controller di dominio. La parte di Machine Learning Services del programma di installazione avrà esito negativo.

+ Non installare **Caratteristiche condivise** > **Machine Learning Server (Standalone)** nello stesso computer che esegue un'istanza nel database. Un server autonomo competono per le stesse risorse, indebolendo le prestazioni di entrambe le installazioni.

+ Installazione side-by-side con altre versioni di R e Python è supportata ma non consigliata. È supportato perché l'istanza di SQL Server utilizza una proprio copie delle distribuzioni di R e Anaconda open source. Ma non è consigliabile perché in esecuzione il codice che usa R e Python nel computer SQL Server all'esterno di SQL Server può comportare vari problemi:
    
  + Si utilizza un diverso eseguibile e la libreria diversi e ottenere risultati diversi, rispetto a quando si eseguono in SQL Server.
  + Script R e Python in esecuzione in librerie esterne non può essere gestito da SQL Server, iniziali a una contesa di risorse.
  
> [!IMPORTANT]
> Al termine dell'installazione, assicurarsi di completare i passaggi di post-configurazione descritti in questo articolo. Tali passaggi includono l'abilitazione di SQL Server da usare gli script esterni e aggiungendo gli account necessari per SQL Server eseguire i processi R e Python per proprio conto. Modifiche di configurazione in genere richiedono il riavvio dell'istanza o un riavvio del servizio Launchpad.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare Installazione guidata di SQL Server 2017. È possibile scaricare 
  
2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.

   ![Installare servizi nel database di apprendimento automatico](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Nella pagina **Selezione funzionalità** selezionare queste opzioni:
  
    -   **Servizi motore di database**
  
         Per usare R e Python con SQL Server, è necessario installare un'istanza del motore di database. È possibile utilizzare un valore predefinito o un'istanza denominata.
  
    -   **Machine Learning Services (In-Database)**
  
         Questa opzione consente di installare servizi di database che supportano R ed esecuzione di script Python.

    -   **R**

        Selezionare questa opzione per aggiungere i pacchetti Microsoft R, interprete e open source R. 

    -   **Python**

        Selezionare questa opzione per aggiungere i pacchetti Python Microsoft, il file eseguibile 3.5 Python e selezionare le raccolte dalla distribuzione Anaconda.
        
        ![Funzionalità di opzioni per R e Python](media/2017setup-features-page-mls-rpy.png "opzioni di installazione per Python")

        > [!NOTE]
        > 
        > Non si seleziona l'opzione per **Machine Learning Server (Standalone)**. L'opzione per installare Server di Machine Learning in **Caratteristiche condivise di** è destinata all'utilizzo in un computer separato.

4. Nel **fornire il consenso per installare R** pagina, selezionare **Accept**. Il contratto di licenza copre Microsoft R Open, che include una distribuzione di pacchetti di base R open source e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft.

5. Nel **il consenso per installare Python** selezionare **Accept**. Il contratto di licenza di Python Apri origine comprende anche Anaconda e strumenti correlati, nonché alcune nuove librerie di Python dal team di sviluppo Microsoft.
     
     ![Contratto di licenza di Python](media/2017setup-python-license.png "contratto per Python di licenza")
  
    > [!NOTE]
    >  Se il computer in che uso non ha accesso a internet, è possibile sospendere l'installazione a questo punto per scaricare i programmi di installazione separatamente. Per altre informazioni, vedere [installare i componenti di machine learning senza accesso a internet](../install/sql-ml-component-install-without-internet-access.md).
  
     Selezionare **Accept**, attendere finché il **Avanti** diventa attivo e quindi selezionare **Avanti**.
  
6. Nel **pronto per l'installazione** pagina, verificare che le selezioni sono incluse e selezionare **installare**.
  
    + Servizi motore di database
    + Machine Learning Services (In-Database)
    + R Python e/o

    Nota del percorso della cartella nel percorso `..\Setup Bootstrap\Log` in cui sono archiviati i file di configurazione. Una volta completato il programma di installazione, è possibile esaminare i componenti installati nel file di riepilogo.

## <a name="restart-the-service"></a>Riavviare il servizio.

Una volta completato l'installazione, riavviare il motore di database prima di continuare a quella successiva, consentendo l'esecuzione di script.

Riavviare automaticamente anche il servizio viene riavviato la correlate [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

È possibile riavviare il servizio utilizzando il pulsante destro del mouse **riavviare** comando per l'istanza di SSMS o tramite il **Services** pannello nel Pannello di controllo oppure usando [Gestione configurazione SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="bkmk_enableFeature"></a>Abilitare l'esecuzione dello script esterno

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > È possibile scaricare e installare la versione appropriata da questa pagina: [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > È anche possibile provare la versione di anteprima di [operazioni SQL Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is), che supporta le query su SQL Server e le attività amministrative.
  
2. Connettersi all'istanza in cui è installato Servizi di Machine Learning, fare clic su **nuova Query** per aprire una finestra query ed eseguire il comando seguente:

   ```SQL
   sp_configure
   ```

    A questo punto, il valore della proprietà `external scripts enabled` deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita. La funzionalità deve essere abilitata in modo esplicito dall'amministratore prima di poter eseguire script R o Python.
    
3.  Per abilitare la funzionalità di script esterna, eseguire l'istruzione seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Se è già stata abilitata la funzionalità per il linguaggio R, non vengono eseguiti riconfigurare una seconda volta per Python. La piattaforma di estendibilità sottostante supporta entrambi i linguaggi.

4. Riavviare il servizio SQL Server per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Riavviare automaticamente anche il servizio SQL Server viene riavviato correlata [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

    È possibile riavviare il servizio utilizzando il pulsante destro del mouse **riavviare** comando per l'istanza di SSMS o tramite il **Services** pannello nel Pannello di controllo oppure usando [Gestione configurazione SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Verificare l'installazione

Utilizzare la procedura seguente per verificare che tutti i componenti utilizzati per l'avvio dello script esterno siano in esecuzione.

1. In SQL Server Management Studio, aprire una nuova finestra query ed eseguire il comando seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Il valore di **run_value** dovrebbe ora essere impostato su 1.
    
2. Aprire la **Services** pannello o Gestione configurazione SQL Server e verificare **servizio Launchpad di SQL Server** è in esecuzione. È necessario disporre di un servizio per ogni istanza di motore di database che dispone di R o Python installato. Se non è in esecuzione, riavviare il servizio. Per ulteriori informazioni, vedere [componenti per supportare l'integrazione di Python](../python/new-components-in-sql-server-to-support-python-integration.md). 
   
3. Se è in esecuzione Launchpad, dovrebbe essere in grado di eseguire script R e Python semplici per verificare che Runtime script esterni possono comunicare con SQL Server.

   Aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi eseguire uno script simile al seguente:
    
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

    Lo script può richiedere un po' durante l'esecuzione, la prima volta che viene caricato il runtime dello script esterno. I risultati dovrebbero essere simile al seguente:

    | hello |
    |----|
    | 1|


> [!NOTE]
> Le colonne o intestazioni utilizzate nello script Python non vengono restituite, in base alla progettazione. Per aggiungere nomi di colonna per l'output, è necessario specificare lo schema per il set di dati restituito. Eseguire questa operazione usando il parametro con risultati della stored procedure, le colonne di denominazione e specificare il tipo di dati SQL.
> 
> Ad esempio, è possibile aggiungere la riga seguente per generare un nome di colonna arbitrario: `WITH RESULT SETS ((Col1 AS int))`

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Se il passaggio di verifica dello script esterno ha esito positivo, è possibile eseguire i comandi di Python da SQL Server Management Studio, Visual Studio Code o qualsiasi altro client che può inviare istruzioni T-SQL per il server.

Se si ha ricevuto un errore quando si esegue il comando, rivedere i passaggi di configurazione aggiuntive in questa sezione. Potrebbe essere necessario apportare ulteriori configurazioni appropriate per il servizio o il database.

Scenari comuni che richiedono ulteriori modifiche includono:

* [Configurare Windows firewall per le connessioni in entrata](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Abilitare i protocolli di rete aggiuntivi](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Abilitare le connessioni remote](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Estendere le autorizzazioni predefinite per gli utenti remoti](#bkmk_configureAccounts)
* [Concedere l'autorizzazione per eseguire gli script esterni](#permissions-external-script)
* [Concedere l'accesso ai singoli database](#permissions-db)

> [!NOTE]
> Non tutte le modifiche elencate sono necessari e nessuno potrebbero essere necessarie. I requisiti variano lo schema di sicurezza, in cui è installato SQL Server e come si prevedono di connettersi al database ed eseguire gli script esterni. Altri suggerimenti sulla risoluzione dei problemi sono disponibili qui: [domande frequenti sull'aggiornamento e l'installazione](../r/upgrade-and-installation-faq-sql-server-r-services.md)

###  <a name="bkmk_configureAccounts"></a> Abilitare l'autenticazione implicita per gruppo di account di avvio

Durante l'installazione, vengono creati diversi nuovi account utente di Windows allo scopo di eseguire attività in base al token di sicurezza del servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Quando un utente invia uno script Python o R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili. Quindi esegue il mapping per l'identità dell'utente chiamante e viene eseguito lo script per conto dell'utente.

Si tratta di *autenticazione implicita*, ed è un servizio del motore di database. Questo servizio supporta l'esecuzione sicura di script esterni in SQL Server 2016 e SQL Server 2017.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione dello script esterno.

> [!IMPORTANT]
> Il gruppo di lavoro è denominato **SQLRUserGroup** indipendentemente dal fatto che sia stato installato R o Python. È disponibile un singolo gruppo per ogni istanza.

Se è necessario eseguire gli script da un client di analisi scientifica dei dati remota e si utilizza l'autenticazione di Windows, esistono ulteriori considerazioni. Questi account di lavoro devono essere concessa l'autorizzazione per accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per conto dell'utente.

1. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Esplora oggetti, espandere **sicurezza**. Quindi fare doppio clic su **gli account di accesso**e selezionare **nuovo account di accesso**.
2. Nel **accesso - nuovo** nella finestra di dialogo **ricerca**.
3. Selezionare **tipi di oggetto**e selezionare **gruppi**. Deselezionare tutte le altre operazioni.
4. In **immettere il nome di oggetto da selezionare**, tipo *SQLRUserGroup*e selezionare **Controlla nomi**.
5. Il nome del gruppo locale associato al servizio Launchpad dell'istanza deve essere risolto in un nome simile a *nomeistanza\SQLRUserGroup*. Fare clic su **OK**.
6. Per impostazione predefinita, il gruppo è assegnato il **pubblica** ruolo, e dispone dell'autorizzazione per connettersi al motore di database.
7. Fare clic su **OK**.

> [!NOTE]
> Se si utilizza un **account di accesso SQL** per l'esecuzione di script in un contesto di calcolo di SQL Server, questo passaggio aggiuntivo non è necessario.

### <a name="permissions-external-script"></a> Consentire agli utenti di eseguire gli script esterni

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se stessi e si eseguono gli script R o Python in un'istanza personalizzata, è in genere eseguire gli script come amministratore. In questo modo, si dispone dell'autorizzazione di implicita su varie operazioni e tutti i dati nel database.

La maggior parte degli utenti, tuttavia, si dispone di tali autorizzazioni con privilegi elevati. Ad esempio, gli utenti in un'organizzazione che utilizzano account di accesso SQL per accedere al database in genere non dispone di autorizzazioni elevate. Pertanto, per ogni utente che sta utilizzando Python o R, è necessario concedere agli utenti di Machine Learning Services l'autorizzazione all'esecuzione di script esterni in ogni database in cui viene utilizzata la lingua. Ecco come:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorizzazioni non sono specifiche del linguaggio di script supportato. In altre parole, non esistono livelli di autorizzazione separati per lo script R e script Python. Se è necessario mantenere separate le autorizzazioni per queste lingue, è possibile installare R e Python in istanze separate.

### <a name="permissions-db"></a> Assegnare la definizione di lettura, scrittura o dati agli utenti le autorizzazioni di language (DDL) per i database

Durante l'esecuzione degli script di un utente, l'utente potrebbe essere necessario leggere dati da altri database. L'utente potrebbe essere necessario anche creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle.

Per ogni account utente di Windows o account di accesso SQL che esegue gli script R o Python, verificare che abbia le autorizzazioni appropriate sul database specifico: `db_datareader`, `db_datawriter`, o `db_ddladmin`.

Ad esempio, [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione fornisce l'accesso a SQL *MySQLLogin* i diritti per l'esecuzione di query T-SQL nel *ML_Samples* database. Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per ulteriori informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

È possibile creare una soluzione in un computer client di analisi scientifica dei dati di apprendimento. Se è necessario eseguire il codice utilizzando il computer SQL Server come contesto di calcolo, sono disponibili due opzioni: accedere all'istanza utilizzando un account di accesso SQL, oppure utilizzando un account.

+ Per gli account di accesso SQL: verificare che l'account di accesso dispone delle autorizzazioni appropriate per il database in cui vengono letti i dati. Questo scopo, è possibile aggiungere *connettersi* e *selezionare* autorizzazioni o aggiungendo l'account di accesso per il `db_datareader` ruolo. Per creare oggetti, assegnare `DDL_admin` diritti. Se è necessario salvare i dati in tabelle, aggiungere il `db_datawriter` ruolo.

+ Per l'autenticazione di Windows: È necessario creare un'origine dati ODBC nel client di analisi scientifica dei dati che specifica il nome dell'istanza e altre informazioni di connessione. Per ulteriori informazioni, vedere [Amministrazione origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Ottimizzazioni suggerite

Dopo aver creato tutti gli elementi di lavoro, è inoltre possibile ottimizzare il server per supportare l'apprendimento o installazione pretrained modelli.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si prevede che molti utenti di eseguire gli script contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati per il servizio Launchpad. Per ulteriori informazioni, vedere [modificare il pool di account utente per i servizi di SQL Server Machine Learning](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Ottimizzare il server per l'esecuzione di script

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione servono per ottimizzare il bilanciamento del server per un'ampia gamma di servizi che sono supportate dal motore di database, che potrebbe includere di estrazione, trasformazione e caricamento (ETL) processi, creazione di report, il controllo, e le applicazioni che utilizzano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati. Pertanto, le impostazioni predefinite, è possibile che le risorse per machine learning talvolta con restrizioni o limitate, in particolare in operazioni a elevato utilizzo di memoria.

Per assicurarsi che i processi di machine learning sono la priorità e assegnare in modo appropriato, è consigliabile utilizzare Resource Governor di SQL Server per configurare un pool di risorse esterne. È inoltre possibile modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che eseguono il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione della memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account di R che possono essere avviati da [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per machine learning](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Se si utilizza Standard Edition e non dispone di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows, per semplificare la gestione delle risorse di server di monitoraggio. Per altre informazioni, vedere [monitoraggio e gestione dei servizi R](../r/managing-and-monitoring-r-solutions.md) e [monitoraggio e gestione dei servizi di Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Le soluzioni R che crei per SQL Server possono chiamare funzioni di base R, le funzioni dal packes properietary installato con SQL Server e pacchetti R di terze parti compatibili con la versione di R open source installati tramite SQL Server.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer o se sono installati pacchetti nelle librerie utente, non sarà in grado di utilizzare i pacchetti da T-SQL.

Il processo per l'installazione e la gestione dei pacchetti R è diverso in SQL Server 2016 e SQL Server 2017. In SQL Server 2016, un amministratore del database necessario installare i pacchetti R necessari per gli utenti. In SQL Server 2017, è possibile impostare gruppi di utenti di condividere i pacchetti a livello di singolo database o configurare i ruoli di database per consentire agli utenti di installare i propri pacchetti. Per altre informazioni, vedere [installare i nuovi pacchetti di R in SQL Server](../r/install-additional-r-packages-on-sql-server.md).


## <a name="get-help"></a>Supporto

Assistenza sull'installazione o aggiornamento? Per le risposte alle domande più comuni e i problemi noti, vedere l'articolo seguente:

* [Aggiornamento e l'installazione domande frequenti - servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori R possono iniziare a usare alcuni semplici esempi e apprendere le nozioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Esecuzione di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: In-database analitica per gli sviluppatori R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Esecuzione di Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: In-database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).
