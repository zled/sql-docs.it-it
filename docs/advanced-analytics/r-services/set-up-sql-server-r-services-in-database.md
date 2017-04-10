---
title: "Configurare SQL Server R Services (In-Database) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "installazione di SQL Server R Services"
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 30
---
# Configurare SQL Server R Services (In-Database)
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e versioni successive è possibile installare tutti i componenti correlati a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] usando l'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 
 
 Al termine dell'installazione, può essere necessario eseguire altri passaggi per abilitare la funzionalità R Services, configurare account e concedere agli utenti le autorizzazioni a specifici database.   
  
Se si verificano problemi di accesso al database al termine dell'installazione o è necessario disinstallare le versioni precedenti, vedere [Domande frequenti sull'installazione e sull'aggiornamento &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md).  

> [!NOTE]
> Per l'installazione di R Services (In-Database), l'unità in cui è installata la funzionalità deve supportare la creazione di nomi di file brevi con la notazione 8.3. In caso contrario, è possibile che i processi che eseguono R da SQL Server non vengano avviati. Prima di installare R Services, assicurarsi di abilitare la notazione 8.3 sul volume. Questa limitazione verrà rimossa in una versione successiva.

  
##  <a name="a-namebkmkinstallrservicesindatabasea-step-1-install-r-services-in-database-on-sql-server-2016-or-later"></a><a name="bkmk_installRServicesInDatabase"></a> Passaggio 1: Installare R Services (In-Database) in SQL Server 2016 o versioni successive  
   
  
1.  Eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    Per informazioni su come eseguire l'installazione automatica, vedere [Unattended Installs of SQL Server R Services](../../advanced-analytics/r-services/unattended-installs-of-sql-server-r-services.md).  
  
2.  Nella scheda **Installazione** fare clic su **Nuova installazione autonoma di SQL Server o aggiunta di funzionalità a un'installazione esistente**.  
  
    > [!NOTE]  
    >  Non è possibile installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un cluster di failover, ma è possibile installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un computer autonomo che usa AlwaysOn e fa parte di un gruppo di disponibilità. Per altre informazioni sull'uso di R Services in un gruppo di disponibilità AlwaysOn, vedere [Gruppi di disponibilità AlwaysOn: interoperabilità](../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md).  
  
3.  Nella pagina **Selezione funzionalità** selezionare queste opzioni:  
  
    -   **Servizi motore di database**  
  
         Per usare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]è necessaria almeno un'istanza del motore di database. È possibile usare un'istanza predefinita o denominata.  
  
    -   **R Services (In-Database)**  
  
         Questa opzione consente di configurare i servizi di database usati dai processi R e di installare le estensioni che supportano script e processi esterni.  
    > [!NOTE]
    > 
    > Se è necessario eseguire il codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assicurarsi di installare **[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]**. 
    > 
    > Al contrario, Microsoft R Server (Standalone) è un'opzione che consente di usare le librerie ScaleR in un computer Windows che non esegue SQL Server. È consigliabile installare Microsoft R Server (Standalone) in un computer portatile o in un altro computer che viene usato per lo sviluppo R, in modo da creare soluzioni R che successivamente possono essere distribuite in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che esegue R Services (In-Database).
 
  
4.  Nella pagina **Consenso per installare Microsoft R Open** fare clic su **Accetto**.  
  
     Questo contratto di licenza è necessario per il download di Microsoft R Open, che include una distribuzione di pacchetti e strumenti R open source di base, insieme a pacchetti R avanzati e a provider di connettività di Revolution Analytics.  
  
    > [!NOTE]  
    >  Se il computer in uso non ha accesso a Internet, è possibile sospendere l'installazione in questo momento per scaricare i programmi di installazione separatamente, come descritto qui: [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)  
  
     Fare clic su **Accetto**, attendere che il pulsante **Avanti** diventi attivo e quindi fare clic su **Avanti**.  
  
5.  Nella pagina **Inizio installazione** verificare che le opzioni selezionate siano incluse e fare clic su **Installa**.  
  
     **Funzionalità**  
  
     Servizi motore di database  
  
     R Services (In-Database)  
  
6.  Al termine l'installazione, riavviare il computer.   
  
  
##  <a name="a-namebkmkenablefeaturea-step-2-enable-r-services-and-verify-that-local-r-script-execution-works"></a><a name="bkmk_enableFeature"></a> Passaggio 2: Abilitare R Services e verificare l'esecuzione locale dello script R  
  
  
1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se non è già installato, è possibile eseguire nuovamente l'Installazione guidata di SQL Server per aprire un collegamento di download ed eseguire l'installazione.  
  
2. Connettersi all'istanza in cui è installato R Services (In-Database) ed eseguire il comando seguente per abilitare in modo esplicito la funzionalità R Services. In caso contrario, non sarà possibile richiamare gli script R anche se la funzionalità è stata installata.  
  
   ```    
   Exec sp_configure  'external scripts enabled', 1  
   Reconfigure  with override    
   ```  
  
10. Riavviare il servizio SQL Server per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Viene riavviato automaticamente anche il servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] correlato. È possibile riavviare il servizio usando il pannello Servizi nel Pannello di controllo oppure tramite Gestione configurazione SQL Server.  
  
9. Dopo che il servizio SQL Server è disponibile, verificare che la funzionalità R sia abilitata eseguendo il comando seguente e verificando che *run_value* sia impostato su 1:  
  
    ```    
    Exec sp_configure  'external scripts enabled'    
    ```  
   Facoltativamente, aprire il pannello **Servizi** e verificare che il servizio Launchpad per l'istanza sia in esecuzione. Ogni istanza ha un proprio servizio Launchpad.
   
10. A questo punto, dovrebbe essere possibile eseguire script R semplici come il seguente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
    ```  
    exec sp_execute_external_script  @language =N'R',  
    @script=N'OutputDataSet<-InputDataSet',    
    @input_data_1 =N'select 1 as hello'  
    with result sets (([hello] int not null));  
    go  
    ```  
  
    **Risultati**  
  
    *hello*  
    *1*   
  
> [!IMPORTANT]  Se è necessario accedere ai dati di SQL Server o eseguire comandi R da un client remoto per l'analisi scientifica dei dati, sono necessari alcuni passaggi aggiuntivi. I passaggi seguenti descrivono in dettaglio questi requisiti aggiuntivi.
 
  
##  <a name="a-namebkmkconfigureaccountsa-step-3-enable-implied-authentication-for-launchpad-accounts"></a><a name="bkmk_configureAccounts"></a> Passaggio 3: Abilitare l'autenticazione implicita per gli account Launchpad  
   
  
Durante l'installazione, vengono creati 20 nuovi account utente di Windows allo scopo di eseguire attività in base al token di sicurezza del servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Quando un utente invia uno script R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibile, ne esegue il mapping all'identità dell'utente chiamante ed esegue lo script R per conto dell'utente. Si tratta di un nuovo servizio del motore di database che supporta l'esecuzione sicura di script esterni, definito *autenticazione implicita*. 

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**.  Se è necessario eseguire script R da un client remoto per l'analisi scientifica dei dati e si usa l'autenticazione di Windows, questi account di lavoro devono ricevere l'autorizzazione di accesso all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per conto del cliente.  
  
1. In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso** e quindi scegliere **Nuovo account di accesso**.  
2. Nella finestra di dialogo **Account di accesso - Nuovo** fare clic su **Cerca**.  
3. Fare clic su **Tipi di oggetto** e selezionare **Gruppi**. Deselezionare tutte le altre opzioni.  
4. In Inserire il nome oggetto da selezionare digitare *SQLRUserGroup* e fare clic su **Controlla nomi**.  
5. Il nome del gruppo locale associato al servizio Launchpad dell'istanza deve essere risolto in un nome simile a *nomeistanza\SQLRUserGroup*. Scegliere **OK**.  
6. Per impostazione predefinita, l'account di accesso viene assegnato al ruolo **public** e dispone dell'autorizzazione per connettersi al motore di database. 
7. Scegliere **OK**.  
  
> [!NOTE] Se si usa un account di accesso SQL per l'esecuzione di script R in un contesto di calcolo di SQL Server, questo passaggio aggiuntivo non è necessario.
  
  
## <a name="step-4-give-non-admin-users-r-script-permissions"></a>Passaggio 4: Concedere autorizzazioni per l'esecuzione di script R agli utenti senza privilegi di amministratore  
  
Se si è installato personalmente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e si eseguono script R nell'istanza in uso, si dispone in genere di diritti di amministratore per l'esecuzione di script e si ha quindi un'autorizzazione implicita su varie operazioni e su tutti i dati nel database, oltre alla possibilità di installare nuovi pacchetti R in base alle esigenze.  
  
Tuttavia, in uno scenario aziendale, la maggior parte degli utenti, inclusi quelli che accedono al database tramite account SQL, non dispone di autorizzazioni con privilegi così elevati. Pertanto, a ogni utente che eseguirà script esterni, è necessario concedere autorizzazioni utente per l'esecuzione di script R in ogni database in cui verrà usato R.   
  
  
```  
USE <database_name>  
GO  
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]  
```  

> [!TIP] Serve aiuto per l'installazione? Non si è certi di aver eseguito tutti i passaggi?
>
> Usare questi report personalizzati per controllare lo stato di installazione di R Services. Per altre informazioni, vedere [Monitorare R Services tramite i report personalizzati](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md).    
  
##  <a name="a-namebkmkadditionala-optional-modifications"></a><a name="bkmk_Additional"></a> Modifiche facoltative  
  
Questa sezione descrive le altre modifiche che è possibile apportare alla configurazione dell'istanza, o del client per l'analisi scientifica dei dati, per supportare l'esecuzione di script R.
  
### <a name="modify-the-number-of-worker-accounts-used-by-includersqllaunchpadtokenrsqllaunchpadmdmd"></a>Modificare il numero di account di lavoro usati da [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]
  
Se si pensa di usare R in modo intensivo o si prevede che molti utenti eseguano script contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati al servizio Launchpad. Per altre informazioni, vedere [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).  
  
  
### <a name="give-your-r-users-or-logins-read-write-or-ddl-permissions-as-needed-in-additional-databases"></a>Assegnare a utenti o account di accesso R autorizzazioni di lettura, scrittura o DDL in altri database in base alle esigenze  
  
Durante l'esecuzione di script R, è possibile che l'account utente debba leggere dati da altri database, creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle. 
     
Per ogni utente che eseguirà script R, verificare che il relativo account disponga di autorizzazioni **db_datareader**, **db_datawriter** o **db_ddladmin** sul database specifico.   
       
Ad esempio, l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente concede all'account di accesso SQL *MySQLLogin* i diritti per l'esecuzione di query T-SQL nel database *RSamples*. Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.  
  
```  
USE RSamples  
GO  
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'  
```  
  
Per altre informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [Ruoli a livello di database](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
  
### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati  
  
Se si crea una soluzione R in un computer client per l'analisi scientifica dei dati ed è necessario connettersi al computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come contesto di calcolo, è possibile usare un account di accesso SQL o l'autenticazione integrata di Windows.  
  
Se si usa un account di accesso SQL, assicurarsi che l'account disponga delle autorizzazioni appropriate sul database in cui si leggeranno i dati. A tale scopo, aggiungere le autorizzazioni *Connetti a* e *SELECT* oppure aggiungere l'account di accesso al ruolo **db_datareader**. Per creare oggetti, è necessario disporre dei diritti **DDL_admin**.  Per salvare dati in tabelle, aggiungere l'account di accesso al ruolo **db_datawriter**.  
  
Se si usa l'autenticazione di Windows, è necessario configurare un'origine dati ODBC nel client per l'analisi scientifica dei dati che specifica il nome dell'istanza e altre informazioni di connessione.  
  
Per altre informazioni, vedere [Using the ODBC Data Source Administrator](http://windows.microsoft.com/windows/using-odbc-data-source-administrator) (Uso di Amministrazione origine dati ODBC).  
  
### <a name="optimize-the-server-for-r"></a>Ottimizzare il server per R  

Le impostazioni predefinite per il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consentono di ottimizzare il bilanciamento del server per un'ampia gamma di servizi supportati dal motore di database, che possono includere processi ETL, servizi di controllo e creazione di report e applicazioni che usano dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Di conseguenza, le impostazioni predefinite possono includere risorse per le operazioni R limitate, in particolare nel caso di operazioni a elevato utilizzo di memoria.  
  
 Per assicurarsi che per le attività R siano definite le priorità e siano assegnate le risorse in modo appropriato, è consigliabile usare Resource Governor per configurare un pool di risorse esterne specifico per l'operazione R. È inoltre possibile modificare la quantità di memoria allocata al motore di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o aumentare il numero di account in esecuzione con il servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)].  
  
-   Configurare un pool di risorse per la gestione di risorse esterne  
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)  
  
-   Modificare la quantità di memoria riservata per il motore di database  
  
     [Opzioni di configurazione del server Server Memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
-   Modificare il numero di account R che possono essere avviati da [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]  
  
     [Modificare il pool di account utente per SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  
  
### <a name="get-the-r-source-code-optional"></a>Ottenere il codice sorgente R (facoltativo)  

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] include una distribuzione di pacchetti R open source di base.  
  
Facoltativamente, fare clic su uno di questi collegamenti per iniziare immediatamente il download di codice sorgente GPL/LPGL modificato. Il codice sorgente è reso disponibile in conformità con la licenza GNU General Public License, ma non è necessario per installare o usare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
-   Compatibile con RC2: scaricare l'archivio [rre-gpl-src.8.0.2.tar.gz](http://go.microsoft.com/fwlink/?LinkId=786770) 
  
-   Compatibile con RC3: scaricare l'archivio [rre-gpl-src.8.0.3.tar.gz](http://go.microsoft.com/fwlink/?LinkId=786771) 

-   Compatibile con RTM: scaricare l'archivio [rre-gpl-src.8.0.3.tar.gz](http://go.microsoft.com/fwlink/?LinkID=786771)
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 Se si riscontrano problemi, vedere questo elenco dei problemi comuni durante l'installazione di versioni non definitive di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
 [Domande frequenti sull'installazione e sull'aggiornamento &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un client per l'analisi scientifica dei dati](../../advanced-analytics/r-services/set-up-a-data-science-client.md)   
 [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md)  
  
  