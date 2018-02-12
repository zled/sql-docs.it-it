---
title: Configurare SQL Server Machine Learning Services (In-Database) | Documenti Microsoft
ms.custom: 
ms.date: 11/15/2017
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
- l'installazione di servizi di SQL Server Machine Learning
- Configurare R Services
- installare l'apprendimento SQL
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 4d18a45b40c7f80ae2b46514f6c8245b80f6b142
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="set-up-sql-server-machine-learning-services-in-database"></a>Configurare SQL Server Machine Learning Services (In-Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo argomento viene descritto come installare e configurare il computer seguente apprendimento delle funzionalità che supportano analitica nel database di SQL Server:

+ **SQL Server 2016 R Services (In-Database)**. Se si dispone di SQL Server 2016, installare questa funzionalità per consentire l'esecuzione del codice R in SQL Server. Richiede il motore di database.

    [Impostare l'apprendimento di SQL Server 2016](#bkmk_2016top)

+ **SQL Server 2017 Machine Learning Services (In-Database)**. Se si dispone di SQL Server 2017, installare prima di eseguire codice R (o Python) in SQL Server. Richiede il motore di database. 

    [Configurare SQL Server 2017 machine learning](#bkmk_2017top)

+ Un server di machine learning con **non** SQL Server

    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione include anche l'opzione per installare una versione di "in modo autonomo" di machine learning componenti che non richiede il motore di database e non viene eseguito in SQL Server.  In genere, si consiglia di installare questa opzione in un computer diverso rispetto al computer che ospita SQL Server.
    
    [Configurare un server autonomo apprendimento](create-a-standalone-r-server.md).

In questo articolo descrive il processo di installazione che utilizza il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata. Per l'installazione da riga di comando o per scaricare i programmi di installazione da utilizzare nel server non in linea, vedere i seguenti articoli:

+ [Installare R per SQL Server dalla riga di comando](unattended-installs-of-sql-server-r-services.md)
+ [Installare Python per SQL Server dalla riga di comando](../python/unattended-installs-of-sql-server-python-services.md)
+ [Installare server autonomo machine learning dalla riga di comando](install-microsoft-r-server-from-the-command-line.md)
+ [Installare i componenti di machine learning in un server con le voci ACE non internet](installing-ml-components-without-internet-access.md)

**Si applica a:** SQL Server 2016, SQL Server 2017

## <a name="bkmk_prereqs"></a> Elenco di controllo preinstallazione

+ Machine learning in-database richiede SQL Server 2016 o versione successiva. 

+ Lingue supportate: 

    + SQL Server 2016 supporta solo R. 

    + R è disponibile anche come una funzionalità di anteprima di Database SQL di Azure, con alcune limitazioni. Per ulteriori informazioni, vedere [usando R in Database SQL di Azure](using-r-in-azure-sql-database.md)

    + Per utilizzare Python richiede SQL Server 2017 o versione successiva.

+ Se è stato usato qualsiasi versione precedente dell'ambiente di sviluppo di Revolution Analitica o i pacchetti RevoScaleR oppure se è installata una versione preliminare di SQL Server 2016, è necessario disinstallarli. Installazione side-by-side non è supportata. Per informazioni sulla rimozione delle versioni precedenti, vedere [aggiornamento e domande frequenti sull'installazione di servizi di SQL Server Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).

+ È possibile installare SQL Server 2016 R Services o i servizi di SQL Server 2017 Machine Learning in un controller di dominio. La parte di R Services o i servizi di Machine Learning del programma di installazione avrà esito negativo.

+ È possibile installare di machine learning funzionalità su un cluster di failover. Il meccanismo di sicurezza utilizzato per isolare i processi di script esterno non è compatibile con un ambiente cluster di failover di Windows Server. In alternativa, è possibile eseguire una delle operazioni seguenti:
    * Utilizzare la replica per copiare le tabelle necessarie a un'istanza di SQL Server con machine learning abilitato.
    * Installare l'apprendimento in un computer autonomo che utilizza AlwaysOn e fa parte di un gruppo di disponibilità.

+ Al termine dell'installazione, il framework di machine learning richiede un'ulteriore configurazione. I passaggi esatti dipendono l'organizzazione e i criteri di sicurezza, configurazione del server e utenti previsti. È consigliabile esaminare tutti i passaggi e determinare di configurazione aggiuntivi che potrebbe essere necessario nell'ambiente in uso.

## <a name="bkmk2016top"></a>Installare SQL Server 2016 R Services (In-Database)

> [!div class="checklist"]
> * Installare il motore di database e le funzionalità di apprendimento automatico
> * Necessari passaggi di post-installazione: abilitare l'apprendimento e riavviare
> * Passaggi di post-installazione facoltativi: aggiungere regole del firewall, gli utenti di aggiungere, modificare o configurare gli account di servizio, configurare un client di analisi scientifica dei dati remoti

**Utilizzando l'installazione guidata di SQL Server 2016**

1. Eseguire l'Installazione guidata di SQL Server.

2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.

    
     ![Installare R Services (In-Database)](media/2016-setup-installation-rsvcs.png "avviare l'installazione del motore di database con R Services")
   
3. Nel **Selezione funzionalità** pagina, selezionare le opzioni seguenti:

   - Selezionare **servizi motore di Database**. Il motore di database, è necessario in ogni istanza che usa il machine learning.
   - Selezionare **R Services (In-Database)**. Installa il supporto per l'utilizzo nel database di R.
    
     ![Selezione delle caratteristiche R Services](media/2016setup-rsvcs-features.png "selezionare queste funzionalità per R Services nel Database")

    > [!IMPORTANT]
    > Non installare R Server e R Services nello stesso momento. È in genere necessario installare R Server (Standalone) per creare un ambiente che un esperto di dati o lo sviluppatore utilizza per connettersi a SQL Server e distribuire soluzioni R. Non è quindi necessario installare entrambe le soluzioni nello stesso computer.

4.  Nel **il consenso per installare Microsoft R Open** pagina, fare clic su **Accept**.
  
    Il contratto di licenza è necessario per scaricare Microsoft R Open, che include una distribuzione di pacchetti di base R open source e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft R.
  
    Se il computer in uso non ha accesso a internet, è possibile sospendere l'installazione a questo punto per scaricare i programmi di installazione separatamente, come descritto in [componenti installare R senza accesso a internet](installing-ml-components-without-internet-access.md).
  
5. Dopo aver accettato il contratto di licenza, è una breve pausa durante l'installazione è pronto. Fare clic su **Avanti** quando il pulsante diventa disponibile.

6. Nel **pronto per l'installazione** pagina, verificare che gli elementi seguenti sono inclusi e quindi selezionano **installare**.

   + Servizi motore di database
   + R Services (In-Database)

7. Quando l'installazione è stata completata, riavviare il computer.


## <a name="bkmk2017top"></a>Installare SQL Server 2017 Machine Learning Services (In-Database)

> [!div class="checklist"]
> * Installare il motore di database e le funzionalità di apprendimento automatico
> * Necessari passaggi di post-installazione: abilitare l'apprendimento e riavviare
> * Passaggi di post-installazione facoltativi: aggiungere regole del firewall, gli utenti di aggiungere, modificare o configurare gli account di servizio, configurare un client di analisi scientifica dei dati remota.

**Introduzione**

1. Eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.

     ![Installare servizi di Machine Learning (In-Database)](media/2017setup-installation-page-mlsvcs.png "avviare l'installazione del motore di database con servizi di Machine Learning")

3. Nel **Selezione funzionalità** pagina, selezionare le opzioni seguenti:
   
    + Selezionare **servizi motore di Database**. Il motore di database, è necessario in ogni istanza che usa il machine learning.

    + Selezionare **di Machine Learning Services (In-Database)**. Questa opzione installa il supporto per l'utilizzo nel database di R. Dopo aver selezionato questa opzione, è possibile selezionare di machine learning language. È possibile selezionare solo R oppure è possibile aggiungere sia R e Python.
   
    ![Selezione delle funzionalità Servizi di Machine Learning](media/2017setup-features-page-mls-rpy.png "selezionare queste funzionalità per R Services nel Database")

    Se non si seleziona Opzioni di linguaggio Python o R, l'installazione guidata installa solo il framework di estendibilità, che include Launchpad attendibile di SQL Server e non installa i componenti specifici della lingua.  In genere si consiglia di installare almeno una lingua con cui iniziare. Tuttavia, è possibile utilizzare questa opzione se si prevede di utilizzare immediatamente il processo di associazione per l'aggiornamento di machine learning componenti. Per ulteriori informazioni, vedere [SqlBindR utilizzare per aggiornare un'istanza di R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

    È consigliabile che si **non** installare le funzionalità autonome e In Database nello stesso computer e non installarli nello stesso momento. È in genere preferibile installare Machine Learning Server (Standalone) per creare un ambiente che un esperto di dati o lo sviluppatore utilizza per connettersi a SQL Server durante la distribuzione di soluzioni. Non è quindi necessario installare entrambe le soluzioni nello stesso computer.

4.  Contratti per machine learning di licenza: a seconda di quali lingue che si esegue l'installazione, è necessario accettare i contratti di licenza per R, Python o entrambi.

    + Condizioni di licenza per il contratto di licenza r include Microsoft R Open, che include una distribuzione di pacchetti di base R open source e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft.
  
    + Condizioni di licenza per Python. Il contratto di licenza di Python Apri origine comprende anche Anaconda e strumenti correlati, nonché alcune nuove librerie di Python dal team di sviluppo Microsoft.

    Fare clic su **Accept** per indicare il contratto. Si verifica una breve pausa durante i componenti sono pronti, il **Avanti** diventa disponibile.

    Se il computer in uso non ha accesso a internet, è possibile sospendere l'installazione a questo punto per scaricare i programmi di installazione separatamente, come descritto qui: [installare i componenti di machine learning senza accesso a internet](installing-ml-components-without-internet-access.md).

6. Nel **pronto per l'installazione** pagina, verificare che gli elementi seguenti sono inclusi e quindi selezionano **installare**.

   - Servizi motore di database
   - Machine Learning Services (In-Database)
   - R Python e/o

7. Una volta completato l'installazione, prendere nota del percorso di installazione di log e quindi riavviare il computer.

###  <a name="bkmk_enableFeature"></a>Passaggio di post-installazione obbligatorio

Per motivi di sicurezza, la funzione di machine learning non è abilitata per impostazione predefinita anche se è stata installata la funzionalità. Un amministratore del server è necessario abilitare la funzionalità e riavviare l'istanza. 

In questa sezione viene descritto come riconfigurare l'istanza per machine learning. Configurazione imposta gli account di servizio esterno e avvia il servizio Launchpad.

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se non è già installato, è possibile eseguire nuovamente l'Installazione guidata di SQL Server per aprire un collegamento di download ed eseguire l'installazione.
  
2. Connettersi all'istanza in cui è installato l'apprendimento e quindi eseguire il comando seguente:

   ```SQL
   sp_configure
   ```

    Cercare il valore della **script esterni abilitato** proprietà, che deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita per ridurre la superficie di attacco.
     
3. Per abilitare la funzionalità di script esterna, eseguire l'istruzione seguente:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
4. Riavviare il servizio SQL Server per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Riavviare automaticamente anche il servizio SQL Server viene riavviato correlata [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

    È possibile riavviare il servizio utilizzando il **servizi** pannello nel Pannello di controllo oppure tramite Gestione configurazione SQL Server.

5. Per verificare che sia abilitato il servizio di esecuzione dello script esterno, in SQL Server Management Studio, aprire una nuova **Query** finestra e quindi eseguire il comando seguente:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```
    Il valore di **run_value** dovrebbe ora essere impostato su 1.
    
6. Aprire il **servizi** pannello e verificare che il servizio Launchpad per l'istanza sia in esecuzione. Se si installano più istanze, ogni istanza ha un proprio servizio Launchpad.

7. È consigliabile eseguire uno script semplice per verificare che il runtime script esterni possono comunicare con SQL Server. 

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

    Lo script può richiedere un po' durante l'esecuzione, la prima volta che viene caricato il runtime dello script esterno. I risultati dovrebbero essere simile al seguente:

    | hello |
    |----|
    | 1|


8. Se si verificano errori, passare alla sezione che descrive le modifiche di altri, facoltative che potrebbe essere necessario apportare al termine dell'installazione oppure vedere la Guida alla risoluzione dei problemi:

    + [Passaggi successivi all'installazione facoltativi: configurare servizio e autorizzazioni](#bkmk_FollowUp) 
    + [Risoluzione dei problemi di apprendimento in SQL Server](upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="bkmk_FollowUp"></a>Passaggi facoltativi di post-installazione

A seconda del caso d'uso per l'apprendimento automatico, potrebbe essere necessario apportare ulteriori modifiche al server, il firewall, gli account utilizzati dal servizio o le autorizzazioni di database. Le modifiche è necessario apportare variano dalle maiuscole o minuscole.

Scenari comuni che richiedono ulteriori modifiche includono:

* Modifica delle regole del firewall per consentire connessioni in ingresso a SQL Server.
* Abilitazione di protocolli di rete aggiuntive.
* Verificare che il server supporta le connessioni remote.
* Abilitazione *autenticazione implicita*, se gli utenti di accedere ai dati di SQL Server da un client di analisi scientifica dei dati remota e l'esecuzione di codice mediante il pacchetto RODBC o un altro provider ODBC.
* Concessione dell'accesso ai singoli database.
* Risoluzione dei problemi di sicurezza che impediscono la comunicazione con il servizio Launchpad.
* Assicurarsi che gli utenti sono autorizzati a eseguire il codice o installare i pacchetti.

> [!NOTE]
> Non tutte le modifiche elencate potrebbero essere necessarie. Tuttavia, è consigliabile esaminare tutti gli elementi per vedere se sono applicabili al proprio scenario.

Altri suggerimenti sulla risoluzione dei problemi sono disponibili qui: [domande frequenti sull'installazione e aggiornamento](../r/upgrade-and-installation-faq-sql-server-r-services.md)

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

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nell'istanza, si sono in genere l'esecuzione di script come amministratore, o almeno il proprietario del database e quindi hanno le autorizzazioni implicite per varie operazioni, tutti i dati nel database e la possibilità di installare i nuovi pacchetti in base alle esigenze.

Tuttavia, in uno scenario aziendale, la maggior parte degli utenti, inclusi quelli che accedono ai database utilizzando l'account di accesso SQL, non sono tali autorizzazioni con privilegi elevati. Pertanto, per ogni utente che verrà eseguiti gli script R o Python, è necessario concedere le autorizzazioni per eseguire gli script in ogni database in cui verranno utilizzati gli script esterni.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Serve aiuto per l'installazione? Non si è certi di aver eseguito tutti i passaggi? Utilizzare questi report personalizzati per controllare lo stato di installazione ed eseguire passaggi aggiuntivi. 
> 
> [Monitorare i servizi di Machine Learning utilizzando i report personalizzati](monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="ensure-that-the-sql-server-computer-supports-remote-connections"></a>Verificare che il computer SQL Server supporta le connessioni remote

Se non è possibile connettersi da un computer remoto, verificare che il server consenta le connessioni remote. Le connessioni remote vengono talvolta disabilitate per impostazione predefinita.

Verificare inoltre se il firewall consenta l'accesso a SQL Server. Per impostazione predefinita, la porta utilizzata da SQL Server è spesso bloccata dal firewall. Se si utilizza Windows Firewall, vedere [configurare Windows Firewall per l'accesso al motore di database](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="give-your-users-read-write-or-ddl-permissions-to-the-database"></a>Concedere agli utenti di lettura o scrittura, autorizzazioni DDL al database

L'account utente utilizzato per eseguire R o Python potrebbe essere necessario per leggere dati da altri database, creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle. Pertanto, per ogni utente che determina l'esecuzione di script R o Python, assicurarsi che l'utente disponga delle autorizzazioni appropriate per il database: *db_datareader*, *db_datawriter*, o *DB _ ddladmin*.

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

Dopo aver verificato che la funzionalità di esecuzione dello script viene eseguita in SQL Server, è possibile eseguire i comandi di R e Python da SQL Server Management Studio, codice di Visual Studio o qualsiasi altro client che può inviare istruzioni T-SQL per il server. Prima di procedere, è possibile apportare alcune modifiche alla configurazione del sistema per supportare un uso massiccio di machine learning, o aggiungere nuovi pacchetti di R.

In questa sezione sono elencate alcune ottimizzazioni comuni e le attività di formazione per machine learning.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si ritiene che è possibile usare R frequentemente o se si prevede che molti utenti da script in esecuzione contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati per il servizio Launchpad. Per ulteriori informazioni, vedere [modificare il pool di account utente per i servizi di SQL Server Machine Learning](modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Ottimizzare il server per l'esecuzione dello script esterno

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione servono per ottimizzare il bilanciamento del server per un'ampia gamma di servizi che sono supportate dal motore di database, che potrebbe includere di estrazione, trasformazione e caricamento (ETL) processi, creazione di report, il controllo, e le applicazioni che utilizzano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati. Pertanto, le impostazioni predefinite, è possibile che le risorse per machine learning talvolta con restrizioni o limitate, in particolare in operazioni a elevato utilizzo di memoria.

Per assicurarsi che i processi di machine learning sono la priorità e assegnare in modo appropriato, è consigliabile utilizzare Resource Governor di SQL Server per configurare un pool di risorse esterne. È inoltre possibile modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che eseguono il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione della memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account di R che possono essere avviati da [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per machine learning](modify-the-user-account-pool-for-sql-server-r-services.md).

Se si utilizza Standard Edition e non dispone di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows, monitoraggio, che consentono di gestire le risorse di server utilizzati da R. Per ulteriori informazioni, vedere [monitoraggio e gestione dei servizi R](managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Richiedere un minuto, per installare tutti i pacchetti R aggiuntivi che verranno utilizzati.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer o se sono installati pacchetti nelle librerie utente, non sarà in grado di utilizzare i pacchetti da T-SQL.

Il processo per l'installazione e la gestione dei pacchetti R è diverso in SQL Server 2016 e SQL Server 2017. Ad esempio, in SQL Server 2017, è possibile impostare gruppi utenti di condividere i pacchetti a livello di database o configurare ruoli del database per consentire agli utenti di installare i propri pacchetti. Per ulteriori informazioni, vedere [pacchetto gestione](r-package-management-for-sql-server-r-services.md).

In SQL Server 2016, un amministratore del database necessario installare i pacchetti R necessari per gli utenti.

Accesso amministrativo è anche necessario installare i pacchetti Python aggiuntivi nella libreria di istanza.

### <a name="upgrade-the-machine-learning-components"></a>Eseguire l'aggiornamento di machine learning componenti

Quando si installano le funzionalità di machine learning in SQL Server, ottenere la versione dei componenti R o Python che aggiornata durante il rilascio o service pack è stato pubblicato. Ogni volta che si patch o aggiornare il server, i componenti di machine learning vengono aggiornati anche.

Tuttavia, è possibile eseguire l'aggiornamento di machine learning componenti in una pianificazione più veloce rispetto a quelle supportate nelle versioni di SQL Server, tramite un processo noto come _associazione_. Quando si associa un'istanza di SQL Server, sia aggiornano le versioni di R o Python e impostare un criterio di supporto diverso che supporta gli aggiornamenti più frequenti. 

Questi aggiornamenti possono includere:

* Nuovi pacchetti R
+ Nuove API per Microsoft pacchetti come [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package).
* [Pretrained modelli](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) per l'analisi di classificazione e il testo di immagine.

Per informazioni su come aggiornare un'istanza di SQL Server, vedere [l'aggiornamento dei componenti di machine learning tramite l'associazione](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).


### <a name="tutorials"></a>Esercitazioni

Per iniziare a utilizzare alcuni semplici esempi e le informazioni di base del funzionamento di R con SQL Server, vedere [codice R tramite Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Per visualizzare esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).

### <a name="troubleshooting"></a>Risoluzione dei problemi

Se si riscontrano problemi, Tentativo di eseguire l'aggiornamento? Per le risposte alle domande più comuni e i problemi noti, vedere l'articolo seguente:

* [Aggiornamento e installazione domande frequenti - servizi di Machine Learning](upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](\r\monitor-r-services-using-custom-reports-in-management-studio.md)
