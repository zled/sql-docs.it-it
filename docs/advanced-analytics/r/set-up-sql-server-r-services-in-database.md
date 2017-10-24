---
title: Configurare SQL Server Machine Learning Services (In-Database) | Documenti Microsoft
ms.custom: 
ms.date: 09/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- installazione di SQL Server R Services
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 36
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: 9b3449e8c1f19ee69b36107f3530eac80fae0227
ms.contentlocale: it-it
ms.lasthandoff: 09/29/2017

---
# <a name="set-up-sql-server-machine-learning-services-in-database"></a>Configurare SQL Server Machine Learning Services (In-Database)

In questo argomento viene descritto come configurare servizi di Machine Learning in SQL Server utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata.

**Si applica a:** SQL Server 2016 R Services (solo R) SQL Server 2017 Machine Learning Services (R e Python)

## <a name="machine-learning-options-in-sql-server-setup"></a>Machine learning opzioni nell'installazione di SQL Server

Installazione di SQL Server fornisce le seguenti opzioni per l'installazione di apprendimento:

* Installare l'apprendimento con il database di SQL Server

  Questa opzione consente di eseguire gli script R o Python utilizzando una stored procedure. È anche possibile utilizzare il computer SQL Server come contesto di calcolo remoto per R o Python script eseguiti da una connessione esterna.

  Per installare questa opzione:
  
  * In SQL Server 2016, selezionare **R Services (In-Database)**.
  * In SQL Server 2017, selezionare **Machine Learning Services (In-Database)**.


* Installare server autonomo machine learning

  Questa opzione Crea un ambiente di sviluppo per machine learning soluzioni che non richiedono né utilizzano SQL Server. Pertanto, in genere consiglia di installare questa opzione in un computer diverso da quello di un Server di hosting SQL. Per ulteriori informazioni su questa opzione, vedere [creare un Server di Standalone R](../r/create-a-standalone-r-server.md).

Il processo di installazione richiede più passaggi, alcuni dei quali sono facoltativi. Gli aspetti facoltativi dipendano da entrambe come si prevede di usare machine learning e lo stato dell'ambiente di sicurezza. 

## <a name="bkmk_prereqs"></a> Prerequisiti

*  Evitare di installare R Server sia R Services nello stesso momento. È in genere necessario installare R Server (Standalone) per creare un ambiente che un esperto di dati o lo sviluppatore utilizza per connettersi a SQL Server e distribuire soluzioni R. Non è quindi necessario installare entrambe le soluzioni nello stesso computer.

* Se è stato usato qualsiasi versione precedente dell'ambiente di sviluppo di Revolution Analitica o i pacchetti RevoScaleR oppure se è installata una versione preliminare di SQL Server 2016, è necessario disinstallarli. Installazione side-by-side non è supportata. Per informazioni sulla rimozione delle versioni precedenti, vedere [aggiornamento e domande frequenti sull'installazione di SQL Server R Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

* È possibile installare servizi di Machine Learning in un cluster di failover. Il motivo è che il meccanismo di sicurezza utilizzato per isolare i processi di script esterno non è compatibile con un ambiente cluster di failover di Windows Server. In alternativa, è possibile eseguire una delle operazioni seguenti:
    * Utilizzare la replica per copiare le tabelle necessarie per un'istanza di SQL Server autonomo con R Services.
    * Installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un computer autonomo che utilizza AlwaysOn e fa parte di un gruppo di disponibilità.

> [!IMPORTANT]
> Al termine dell'installazione, sono necessari alcuni passaggi aggiuntivi per consentire di machine learning funzionalità. È possibile inoltre necessario concedere agli utenti le autorizzazioni per database specifici, modificare o configurare gli account o configurare un client di analisi scientifica dei dati remota.

##  <a name="bkmk_installExt"></a>Passaggio 1: Installare le funzionalità di estendibilità e scegliere un linguaggio di apprendimento

Per utilizzare l'apprendimento, è necessario installare SQL Server 2016 o versione successiva. Per utilizzare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è necessaria almeno un'istanza del motore di database. È possibile usare un'istanza predefinita o denominata.

1. Eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    Per informazioni su come eseguire le installazioni automatiche, vedere [installazione automatica di SQL Server R Services](../r/unattended-installs-of-sql-server-r-services.md).
  
2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.
   
3. Nel **Selezione funzionalità** i processi di pagina, per installare i servizi di database utilizzati da R e installare le estensioni che supportano script e processi esterni, selezionare le opzioni seguenti:
   
   **SQL Server 2016**
   - Selezionare **servizi motore di Database**.
   - Selezionare **R Services (In-Database)**.

   **SQL Server 2017**
   - Selezionare **servizi motore di Database**.
   - Selezionare **di Machine Learning Services (In-Database)**.
   - Selezionare almeno una di machine learning lingua da attivare. È possibile selezionare solo R oppure è possibile aggiungere sia R e Python.
   
   > [!NOTE]
   > Se non si seleziona Opzioni di linguaggio Python o R, l'installazione guidata installa solo il framework di estendibilità, che include Launchpad attendibile di SQL Server, ma non installa i componenti specifici della lingua. Questa opzione è per associare l'istanza di SQL Server a R o Python come parte dei criteri del ciclo di vita moderna Microsoft. Per ulteriori informazioni, vedere [SqlBindR utilizzare per aggiornare un'istanza di R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

4.  Nel **il consenso per installare Microsoft R Open** selezionare **Accept**.
  
     Il contratto di licenza è necessario per scaricare Microsoft R Open, che include una distribuzione di pacchetti di base R open source e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft R.
  
    > [!NOTE]
    >  Se il computer in uso non ha accesso a internet, è possibile sospendere l'installazione a questo punto per scaricare i programmi di installazione separatamente, come descritto in [componenti installare R senza accesso a internet](installing-ml-components-without-internet-access.md).
  
5. Fare clic su **Avanti**.

6. Nel **pronto per l'installazione** pagina, verificare che gli elementi seguenti sono inclusi e quindi selezionano **installare**.

   **SQL Server 2017**
   - Servizi motore di database
   - Machine Learning Services (In-Database)
   - R Python e/o

   **SQL Server 2016**
   - Servizi motore di database
   - R Services (In-Database)

7. Una volta completato l'installazione, riavviare il computer.

##  <a name="bkmk_enableFeature"></a>Passaggio 2: Abilitare i servizi di script esterni

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se non è già installato, è possibile eseguire nuovamente l'Installazione guidata di SQL Server per aprire un collegamento di download ed eseguire l'installazione.
  
2. Connettersi all'istanza in cui è installato l'apprendimento e quindi eseguire il comando seguente:

   ```SQL
   sp_configure
   ```

    Il valore per il **script esterni abilitato** proprietà dovrebbe ora essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita per ridurre la superficie di attacco e deve essere abilitato in modo esplicito da un amministratore.
     
3. Per abilitare la funzionalità di script esterna, eseguire l'istruzione seguente:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
4. Riavviare il servizio SQL Server per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Riavviare automaticamente anche il servizio SQL Server viene riavviato correlata [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

    È possibile riavviare il servizio utilizzando il **servizi** pannello nel Pannello di controllo oppure tramite Gestione configurazione SQL Server.

## <a name="bkmk_TestScript"></a>Passaggio 3: Verificare che l'esecuzione di script funziona a livello locale

Verificare che il servizio di esecuzione dello script esterno sia abilitato.

1. In SQL Server Management Studio, aprire una nuova **Query** finestra e quindi eseguire il comando seguente:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```
    Il valore di **run_value** dovrebbe ora essere impostato su 1.
    
2. Aprire il **servizi** pannello e verificare che il servizio Launchpad per l'istanza sia in esecuzione. Se si installano più istanze, ogni istanza ha un proprio servizio Launchpad.
   
3. Aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi eseguire un semplice script R, ad esempio le operazioni seguenti:
  
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```
  
    **Risultati**
  
    *Hello* *1*
  
   Se il comando viene eseguito senza errori, passare alla procedura seguente. Se si verifica un errore, per un elenco di alcuni problemi comuni, vedere [domande frequenti sull'installazione e aggiornamento](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="bkmk_FollowUp"></a>Passaggio 4: Di configurazione aggiuntive

A seconda del caso d'uso per R o Python, potrebbe essere necessario apportare ulteriori modifiche al server, il firewall, gli account utilizzati dal servizio o le autorizzazioni di database. Le modifiche è necessario apportare variano dalle maiuscole o minuscole.

Scenari comuni che richiedono ulteriori modifiche includono:

* Modifica delle regole del firewall per consentire connessioni in ingresso a SQL Server.
* Abilitazione di protocolli di rete aggiuntive.
* Verificare che il server supporta le connessioni remote.
* Abilitazione *autenticazione implicita*, se gli utenti accedere ai dati di SQL Server da un terminale lo sviluppo di R remoto ed eseguire codice R tramite il pacchetto RODBC o altri provider di Microsoft Open Database Connectivity (ODBC).
* Assegnazione di autorizzazioni agli utenti per eseguire script R o utilizzare i database.
* Risoluzione dei problemi di sicurezza che impediscono la comunicazione con il servizio Launchpad.
* Assicurarsi che gli utenti sono autorizzati a eseguire il codice R o installare i pacchetti.

> [!NOTE]
> Non tutte le modifiche elencate potrebbero essere necessarie. Tuttavia, è consigliabile esaminare tutti gli elementi per vedere se sono applicabili al proprio scenario.

### <a name="bkmk_configureAccounts"></a>Abilitare l'autenticazione implicita per il gruppo di account di avvio

Durante l'installazione, vengono creati alcuni nuovi account utente di Windows per l'esecuzione di attività con il token di sicurezza del [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio. Quando un utente invia uno script R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili, ne esegue il mapping per l'identità dell'utente chiamante e viene eseguito lo script R per conto dell'utente. Questo nuovo servizio del motore di database supporta l'esecuzione di script esterni, chiamato sicura *autenticazione implicita*.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione di R.

Tuttavia, se è necessario eseguire gli script R da un client di analisi scientifica dei dati remota e si utilizza l'autenticazione di Windows, è necessario concedere questi account di lavoro dell'autorizzazione per accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per conto dell'utente.

1. In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso**e quindi scegliere **Nuovo account di accesso**.
2. Nel **accesso - nuovo** nella finestra di dialogo **ricerca**.
3. Selezionare il **tipi di oggetto** e **gruppi** caselle di controllo e deselezionare tutte le altre caselle di controllo.
4. Fare clic su **avanzate**, verificare che il percorso per la ricerca del computer corrente e quindi fare clic su **trova**.
5. Scorrere l'elenco di account di gruppo nel server finché non si trova un a partire da `SQLRUserGroup`.
    
    + Il nome del gruppo a cui è associato al servizio di avvio per il _istanza predefinita_ è sempre solo **SQLRUserGroup**. Selezionare questo account solo per l'istanza predefinita.
    + Se si utilizza un _istanza denominata_, il nome dell'istanza viene aggiunto al nome predefinito, `SQLRUserGroup`. Di conseguenza, se l'istanza è denominata "MLTEST", il nome di gruppo utente predefinito per questa istanza sarà **SQLRUserGroupMLTest**.
5. Fare clic su **OK** per chiudere la finestra di dialogo Ricerca avanzata, verificare di aver selezionato l'account corretto per l'istanza. Ogni istanza può utilizzare solo il proprio servizio di avvio e il gruppo creato per tale servizio.
6. Fare clic su **OK** per chiudere la **Seleziona utente o gruppo** la finestra di dialogo.
7. Nel **accesso - nuovo** la finestra di dialogo, fare clic su **OK**. Per impostazione predefinita, l'account di accesso viene assegnato al ruolo **public** e dispone dell'autorizzazione per connettersi al motore di database.

### <a name="bkmk_AllowLogon"></a>Consentire agli utenti di eseguire gli script esterni

> [!NOTE]
> Se si utilizza un account di accesso SQL per l'esecuzione di script R in un contesto di calcolo di SQL Server, questo passaggio non è obbligatorio.

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed eseguono gli script R in un'istanza personalizzata, in genere si eseguono script come amministratore, o almeno il proprietario del database e quindi hanno le autorizzazioni implicite per varie operazioni, tutti i dati nel database e la possibilità Per installare i nuovi pacchetti R come necessario.

Tuttavia, in uno scenario aziendale, la maggior parte degli utenti, inclusi quelli che accedono ai database utilizzando l'account di accesso SQL, non sono tali autorizzazioni con privilegi elevati. Pertanto, per ogni utente che verrà eseguiti gli script R o Python, è necessario concedere le autorizzazioni per eseguire gli script in ogni database in cui verranno utilizzati gli script esterni.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Serve aiuto per l'installazione? Non si è certi di aver eseguito tutti i passaggi? Usare questi report personalizzati per controllare lo stato di installazione di R Services. Per altre informazioni, vedere [Monitorare R Services tramite i report personalizzati](monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="ensure-that-the-sql-server-computer-supports-remote-connections"></a>Verificare che il computer SQL Server supporta le connessioni remote

Se non è possibile connettersi da un computer remoto, verificare che il server consenta le connessioni remote. Le connessioni remote vengono talvolta disabilitate per impostazione predefinita.

Verificare inoltre se il firewall consenta l'accesso a SQL Server. Per impostazione predefinita, la porta utilizzata da SQL Server è spesso bloccata dal firewall. Se si utilizza Windows Firewall, vedere [configurare Windows Firewall per l'accesso al motore di database](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="give-your-users-read-write-or-ddl-permissions-to-the-database"></a>Concedere agli utenti di lettura o scrittura, autorizzazioni DDL al database

Durante l'esecuzione degli script R, l'account utente o un account di accesso SQL potrebbe essere necessario per leggere dati da altri database, creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle.

Per ogni account utente o un account di accesso SQL che determina l'esecuzione di script R, assicurarsi che l'account o un account di accesso dispone delle autorizzazioni appropriate per il database: *db_datareader*, *db_datawriter*, o  *db_ddladmin*.

Ad esempio, l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente concede all'account di accesso SQL *MySQLLogin* i diritti per l'esecuzione di query T-SQL nel database *RSamples* . Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per ulteriori informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).

### <a name="use-machine-learning-in-an-azure-vm"></a>Usa machine learning in una macchina virtuale di Azure

Se è installato in una macchina virtuale di Azure Machine Learning Services (o R Services), si potrebbe essere necessario modificare alcuni valori predefiniti aggiuntivi. Per ulteriori informazioni, vedere [l'installazione di SQL Server Machine Learning in una macchina virtuale Azure](installing-sql-server-r-services-on-an-azure-virtual-machine.md).

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

Se si crea una soluzione di R in un computer client di analisi scientifica dei dati ed è necessario eseguire il codice utilizzando il computer SQL Server come contesto di calcolo, è possibile utilizzare un account di accesso SQL o l'autenticazione integrata di Windows.

* Per gli account di accesso SQL: assicurarsi che l'account abbia le autorizzazioni appropriate sul database in cui si leggeranno i dati. È possibile farlo mediante l'aggiunta di *connettersi* e *selezionare* autorizzazioni, o aggiungendo l'account di accesso di *db_datareader* ruolo. Per gli account di accesso necessarie per creare oggetti, aggiungere *ruoli DDL_admin* diritti. Per gli account di accesso deve salvare dati in tabelle, aggiungere l'account di accesso di *db_datawriter* ruolo.

* Per l'autenticazione di Windows: È necessario configurare un'origine dati ODBC nel client di analisi scientifica dei dati che specifica il nome dell'istanza e altre informazioni di connessione. Per ulteriori informazioni, vedere [Amministrazione origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="next-steps"></a>Passaggi successivi

Dopo aver verificato che la funzionalità di esecuzione dello script viene eseguita in SQL Server, è possibile eseguire i comandi di R e Python da SQL Server Management Studio, codice di Visual Studio o qualsiasi altro client che può inviare istruzioni T-SQL per il server.

Tuttavia, è consigliabile apportare alcune modifiche alla configurazione del sistema per supportare un uso massiccio di machine learning, o aggiungere nuovi pacchetti di R.

Questa sezione vengono elencate alcune modifiche comuni che è possibile apportare per supportare l'apprendimento.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si ritiene che è possibile usare R frequentemente o se si prevede che molti utenti da script in esecuzione contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati per il servizio Launchpad. Per ulteriori informazioni, vedere [modificare il pool di account utente per SQL Server R Services](modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Ottimizzare il server per l'esecuzione dello script esterno

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione servono per ottimizzare il bilanciamento del server per un'ampia gamma di servizi che sono supportate dal motore di database, che potrebbe includere di estrazione, trasformazione e caricamento (ETL) processi, creazione di report, il controllo, e le applicazioni che utilizzano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati. Pertanto, le impostazioni predefinite, è possibile che le risorse per machine learning talvolta con restrizioni o limitate, in particolare in operazioni a elevato utilizzo di memoria.

Per assicurarsi che i processi di machine learning sono la priorità e assegnare in modo appropriato, è consigliabile utilizzare Resource Governor di SQL Server per configurare un pool di risorse esterne. È inoltre possibile modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che eseguono il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione della memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account di R che possono essere avviati da [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per machine learning](modify-the-user-account-pool-for-sql-server-r-services.md).

Se si utilizza Standard Edition e non dispone di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows, monitoraggio, che consentono di gestire le risorse di server utilizzati da R. Per ulteriori informazioni, vedere [monitoraggio e gestione dei servizi R](managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Richiedere un minuto, per installare tutti i pacchetti R aggiuntivi che verranno utilizzati.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer o se sono installati pacchetti nelle librerie utente, non sarà in grado di utilizzare i pacchetti da T-SQL. Per ulteriori informazioni, vedere [installare pacchetti R aggiuntivi su SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).

È anche possibile impostare gruppi utenti di condividere i pacchetti a livello di database o configurare i ruoli di database per consentire agli utenti di installare i propri pacchetti. Per ulteriori informazioni, vedere [pacchetto gestione](r-package-management-for-sql-server-r-services.md).

### <a name="upgrade-the-machine-learning-components"></a>Eseguire l'aggiornamento di machine learning componenti

Quando si installa R Services tramite SQL Server 2016, ottenere la versione dei componenti R che è stata aggiornata durante il rilascio o service pack è stato pubblicato. Ogni volta che si patch o aggiornare il server, i componenti di machine learning vengono aggiornati anche.

Tuttavia, è possibile eseguire l'aggiornamento di machine learning componenti in una pianificazione più veloce rispetto a quelle supportate nelle versioni di SQL Server, mediante l'installazione di Microsoft R Server e l'istanza di associazione. Quando esegue l'aggiornamento, è anche possibile ottenere le nuove funzionalità seguenti, che sono supportate nelle versioni recenti di Microsoft R Server:

* Nuovi pacchetti di R, tra cui [sqlrutils](https://docs.microsoft.com/r-server/r-reference/sqlrutils/sqlrutils), [olapR](https://docs.microsoft.com/r-server/r-reference/olapr/olapr), e [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package).
* [Pretrained modelli](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) per l'analisi di classificazione e il testo di immagine.

Per informazioni su come aggiornare un'istanza di SQL Server 2016, vedere [componenti R aggiornare tramite l'associazione](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

Se non si verificare quale versione di R è associata all'istanza, è possibile eseguire un comando analogo al seguente:

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'
myvar <- version$version.string
OutputDataSet <- as.data.frame(myvar);'
```

> [!NOTE]
> Gli aggiornamenti tramite il processo di associazione saranno supportati anche per SQL Server 2017. Tuttavia, attualmente gli aggiornamenti sono supportati solo per le istanze di SQL Server 2016.

### <a name="tutorials"></a>Esercitazioni

Per iniziare a utilizzare alcuni semplici esempi e le informazioni di base del funzionamento di R con SQL Server, vedere [codice R tramite Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Per visualizzare esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).

### <a name="troubleshooting"></a>Risoluzione dei problemi

Se si riscontrano problemi, Tentativo di eseguire l'aggiornamento? Per le risposte alle domande più comuni e i problemi noti, vedere l'articolo seguente:

* [Aggiornamento e installazione domande frequenti - servizi di Machine Learning](upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](monitor-r-services-using-custom-reports-in-management-studio.md)

