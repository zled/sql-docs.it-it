---
title: "Domande frequenti sull&#39;installazione e sull&#39;aggiornamento (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 58
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 47
---
# Domande frequenti sull&#39;installazione e sull&#39;aggiornamento (SQL Server R Services)
  Questo argomento include le risposte alle domande frequenti sull'installazione e alle domande sugli aggiornamenti delle versioni di anteprima di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
 Se si installa [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] per la prima volta, seguire le procedure per configurare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e i componenti R, come descritto qui: [Configurare SQL Server R Services &#40;In-Database&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  

   
## <a name="important-changes-from-pre-releae-versions"></a>Modifiche importanti rispetto alle versioni non definitive  
 Se si è installata una versione non definitiva di SQL Server 2016 o si usano le istruzioni di installazione pubblicate prima del rilascio della versione pubblica di SQL Server 2016, è importante sapere che la procedura di installazione delle versioni non definitive è completamente diversa da quella delle versioni RTM. Queste modifiche interessano sia le opzioni disponibili nell'Installazione guidata di SQL Server sia i passaggi successivi all'installazione. 
   
> [!WARNING] La nuova installazione di una versione non definitiva di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non è più supportata. È consigliabile eseguire l'aggiornamento non appena possibile.  
+ Se si è installato [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in CTP3, CTP3.1, CTP3.2, RC0 o RC1, è necessario eseguire nuovamente lo script di installazione post-configurazione per disinstallare le versioni precedenti dei componenti R e di R Services. 
+ Lo script di installazione post-configurazione viene fornito esclusivamente per aiutare i clienti a disinstallare le versioni non definitive.  Non eseguire lo script durante l'installazione di una versione più recente.

## <a name="how-to-uninstall-previous-versions-of-r-services"></a>Come disinstallare le versioni precedenti di R Services

È importante disinstallare le versioni precedenti di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] e i componenti R correlati nell'ordine corretto.

### <a name="1-run-script-to-deregister-windows-user-group-and-components-before-uninstalling-previous-components"></a>1. Eseguire lo script per annullare la registrazione dei componenti e del gruppo di utenti Windows prima di disinstallare i componenti precedenti
Se si è installata una versione non definitiva di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è necessario eseguire prima lo script `RegisteREext.exe` con l'argomento `/uninstall`.

In questo modo, si annulla la registrazione di componenti obsoleti e si rimuove il gruppo di utenti Windows associato a Launchpad. Se non si esegue questa operazione, non sarà possibile creare il gruppo di utenti Windows necessario per le nuove istanze da installare.
  
Se ad esempio R Services è installato nell'istanza predefinita, eseguire questo comando dalla directory in cui è installato lo script:  
  
~~~~
    RegisterRExt.exe /UNINSTALL  
~~~~ 
  
Se invece R Services è installato in un'istanza denominata, specificare il nome dell'istanza dopo *INSTANCE:*  
  
~~~~ 
RegisterRExt.exe /UNINSTALL /INSTANCE:<instancename>   
~~~~  

Per rimuovere tutti i componenti, può essere necessario eseguire più volte lo script.

> [!NOTE]
> Il percorso predefinito per questo script è diverso, a seconda della versione non definitiva installata. Se si prova a eseguire la versione errata dello script, è possibile che venga restituito un errore. 
> 
>  + Se è installata la versione CTP 3.1, 3.2 o 3.3, prima di disinstallare i componenti è necessario scaricare una versione aggiornata dello script di configurazione post-installazione dall'[Area download Microsoft](http://go.microsoft.com/fwlink/?LinkId=723194). La versione aggiornata dello script supporta l'annullamento della registrazione dei componenti meno recenti. Fare clic sul collegamento e selezionare **Salva con nome** per salvare lo script in una cartella locale. Rinominare lo script esistente e quindi copiare il nuovo script nella cartella in cui verrà eseguito lo script. 
>  + Per la versione RC0, viene installato il file di script corretto, che si trova in questa cartella: `C:\Program Files\Microsoft\MRO-for-RRE\8.0\R-3.2.2\library\RevoScaleR\rxLibs\x64`  
>  + Per le versioni finali (13.0.1601.5 o successive), non è necessario eseguire script per installare o configurare i componenti. Lo script deve essere usato esclusivamente per rimuovere i componenti meno recenti. 


### <a name="2-uninstall-any-older-versions-of-the-revolution-enterprise-tools-including-components-installed-with-ctp-releases"></a>2. Disinstallare le versioni precedenti degli strumenti Revolution Enterprise, inclusi i componenti installati con le versioni CTP.

L'ordine di disinstallazione dei componenti R è fondamentale. Disinstallare sempre prima [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)] e quindi [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)].  

 Se per sbaglio si disinstalla prima R Open e poi viene visualizzato un errore durante il tentativo di disinstallare Revolution R Enterprise, si può reinstallare rivoluzione Revolution R Open o Microsoft R Open e quindi disinstallare entrambi i componenti nell'ordine corretto.  

### <a name="3-uninstall-any-other-version-of-microsoft-r-open"></a>3. Disinstallare qualsiasi altra versione di Microsoft R Open

Disinstallare infine tutte le altre versioni di Microsoft R Open.
 
### <a name="4-upgrade-sql-server"></a>4. Eseguire l'aggiornamento di SQL Server  
  
Dopo che tutti i componenti non definitivi sono stati disinstallati, riavviare il computer. Questo è un requisito di installazione di SQL Server. Non è possibile procedere con un'installazione aggiornata finché non è stato completato un riavvio.     

Al termine, eseguire l'installazione di SQL Server e seguire queste istruzioni per installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]: [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
Non sono necessari componenti aggiuntivi; i pacchetti R e i pacchetti di connettività vengono installati dal programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 


## <a name="upgrading-r-components"></a>Aggiornamento dei componenti R

A mano a mano che vengono rilasciati hotfix o miglioramenti di SQL Server 2016, anche i componenti R vengono aggiornati, se l'istanza include già la funzionalità R Services. 

Tuttavia, quando si aggiornano server non connessi a Internet o si applicano patch a tali server, è necessario scaricare manualmente una versione aggiornata dei componenti R prima di iniziare l'aggiornamento. Per altre informazioni, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).

## <a name="problems-uninstalling-older-versions-of-r"></a>Problemi di disinstallazione delle versioni precedenti di R  
In alcuni casi, le versioni precedenti di Revolution R Open o Revolution R Enterprise non vengano completamente rimosse dal processo di disinstallazione.  
  
 Nel caso di problemi relativi alla rimozione di una versione precedente, è anche possibile modificare il Registro di sistema per rimuovere le chiavi correlate.  
  
 Aprire il Registro di sistema di Windows e individuare questa chiave: `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.  
  
 Eliminare una qualsiasi delle voci seguenti, se presente e se la chiave contiene un singolo valore `sEstimatedSize2`:  
  
-   E0B2C29E-B8FC-490B-A043-2CAE75634972        (per 8.0.2)  
  
-   46695879-954E-4072-9D32-1CC84D4158F4        (per 8.0.1)  
  
-   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (per 8.0.0)  
  
-   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (per 7.5.0)  


## <a name="new-license-agreement-for-r-components-required-for-unattended-installs"></a>Nuovo contratto di licenza per i componenti R necessari per le installazioni automatiche  
 Se si usa la riga di comando per aggiornare un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in cui è già installato [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è necessario modificare la riga di comando in modo da usare il nuovo parametro del contratto di licenza, */IACCEPTROPENLICENSEAGREEMENT*. 
 
 Il mancato uso dell'argomento corretto può causare un errore di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="after-running-setup-includersqlproductnametokenrsqlproductnamemdmd-is-still-not-enabled"></a>Dopo l'installazione, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non è ancora abilitato  
 La funzionalità che supporta l'esecuzione di script esterni è disabilitata per impostazione predefinita, anche se è installata. Si tratta di una scelta di progettazione, pensata per ridurre la superficie di attacco.  
  
 Per abilitare gli script R, un amministratore può eseguire l'istruzione seguente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
1.  Nell'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in cui si vuole usare R, eseguire questa istruzione.  
  
    ```  
    sp_configure 'external scripts enabled',1 
    reconfigure with override  
    ```  
  
2.  Riavviare l'istanza.  
  
3.  Dopo il riavvio dell'istanza, aprire **Gestione configurazione SQL Server** o il pannello **Servizi** e verificare che il servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] sia in esecuzione.  

> [!TIP] Per installare un'istanza di R Services preconfigurata, usare l'immagine di macchina virtuale di Azure che include l'edizione Enterprise con R Services abilitato. Per altre informazioni, vedere [Installazione di SQL Server R Services in una macchina virtuale di Azure](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md).
 

## <a name="setup-of-includersqlproductnametokenrsqlproductnamemdmd-not-available-in-a-failover-cluster"></a>Installazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non disponibile in un cluster di failover  
 Attualmente non è possibile installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un cluster di failover,  
    
 ma è possibile installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un computer autonomo che usa AlwaysOn e fa parte di un gruppo di disponibilità. Per altre informazioni sull'uso di R Services in un gruppo di disponibilità AlwaysOn, vedere [Gruppi di disponibilità AlwaysOn: interoperabilità](../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md).  

In alternativa, è possibile configurare una replica in un'istanza diversa di SQL Server allo scopo di eseguire script R. La replica può essere creata usando la funzionalità di replica o di log shipping.
 
## <a name="launchpad-service-cannot-be-started"></a>Il servizio Launchpad non può essere avviato  

Il problema di avvio di Launchpad può essere dovuto a varie cause.
+ **La notazione 8.3 non è abilitata**.  Per l'installazione di R Services (In-Database), l'unità in cui è installata la funzionalità deve supportare la creazione di nomi di file brevi con la notazione **8.3**.  Un nome di file 8.3 è definito anche breve e viene usato per la compatibilità con le versioni precedenti di Microsoft Windows o come nome alternativo al nome di file lungo. 

  Se il volume in cui si installa [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non supporta i nomi di file brevi, è possibile che i processi che avviano R da SQL Server non siano in grado di individuare il file eseguibile corretto e quindi [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] non viene avviato.  
  
   Come soluzione alternativa, è necessario abilitare la notazione 8.3 nel volume in cui sono installati SQL Server e R Services. È quindi necessario specificare il nome breve per la directory di lavoro nel file di configurazione di R Services. 

    1. Per abilitare la notazione 8.3, eseguire l'utilità **fsutil** con l'argomento *8dot3name* come descritto qui: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).
    2. Dopo aver abilitato la notazione 8.3, aprire il file RLauncher.config. In un'installazione predefinita il file RLauncher.config si trova in C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn
    3. Prendere nota della proprietà relativa a WORKING_DIRECTORY.
    4. Usare l'utilità fsutil con l'argomento *file* per specificare un percorso di file breve per la cartella specificata in WORKING_DIRECTORY.
    5. Modificare il file di configurazione in modo da usare il nome breve per WORKING_DIRECTORY.   
     
In alternativa, per WORKING_DIRECTORY è possibile specificare una directory diversa che abbia un percorso compatibile con la notazione 8.3.     
   
   > [!NOTE] Questa limitazione verrà rimossa in una versione successiva. 
 
+ **L'account che esegue Launchpad è stato modificato o le autorizzazioni necessarie sono state rimosse.** Per impostazione predefinita, all'avvio di [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] viene usato l'account seguente, che è configurato dal programma di installazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] con tutte le autorizzazioni necessarie: NT Service\MSSQLLaunchpad

  Pertanto, se si assegna a Launchpad un account diverso o il diritto viene rimosso da un criterio sul computer di SQL Server, è possibile che l'account non abbia le autorizzazioni necessarie e che venga visualizzato questo errore: *ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Errore durante l'accesso. L'utente non ha ottenuto il tipo di accesso richiesto a questo computer.*

  Per concedere le autorizzazioni necessarie al nuovo account di servizio, usare l'applicazione **Criteri di sicurezza locali** e aggiornare le autorizzazioni per l'account in modo da includere le seguenti:
  + Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
  + Ignorare controllo incrociato (SeChangeNotifyPrivilege)
  + Accesso come servizio (SeServiceLogonRight)
  + Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

  Per altre informazioni sulle autorizzazioni per l'esecuzione dei servizi di SQL Server, vedere [Configurare account di servizio e autorizzazioni di Windows](https://msdn.microsoft.com/library/ms143504.aspx#Windows).
  
## <a name="side-by-side-installation-not-supported"></a>Installazione side-by-side non supportata  
 Non creare un'installazione affiancata con un'altra versione di R o versioni diverse da Revolution Analytics.  

## <a name="offline-installation-of-r-components-for-localized-version-of-sql-server"></a>Installazione offline dei componenti R per la versione localizzata di SQL Server 
Se si installa R Services in un computer che non dispone di accesso a Internet, è necessario eseguire due passaggi aggiuntivi, ossia scaricare il programma di installazione dei componenti R in una cartella locale prima dell'installazione di SQL Server e modificare il file del programma di installazione per assicurarsi che venga installata la lingua corretta. 

L'identificatore della lingua usato per i componenti R deve corrispondere a quello usato per la lingua di installazione di SQL Server, altrimenti il pulsante **Avanti** è disabilitato e non è possibile completare l'installazione.

Per altre informazioni, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md). 
  
## <a name="unable-to-launch-runtime-for-r-script"></a>Non è possibile avviare il runtime per lo script R
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] crea un gruppo di utenti Windows che viene usato da [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] per l'esecuzione dei processi R. Questo gruppo di utenti deve essere in grado di accedere all'istanza che esegue R Services in modo da eseguire R per conto di utenti remoti che usano l'autenticazione integrata di Windows.
  
 In un ambiente in cui il gruppo di Windows per gli utenti di R (**SQLRUsers**) non ha questa autorizzazione, è possibile che vengano visualizzati gli errori seguenti:  
  
-   Quando si prova a eseguire gli script R:  
  
     *Non è stato possibile avviare il runtime per lo script 'R'. Verificare la configurazione del runtime di 'R'.*  
  
     *Si è verificato un errore dello script esterno. Non è stato possibile avviare il runtime.*  
  
-   Errori generati dal servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]:  
  
     *Failed to initialize the launcher RLauncher.dll* (Non è stato possibile inizializzare l'utilità di avvio RLauncher.dll)  
  
     *No launcher dlls were registered!* (Non è stata registrata alcuna DLL dell'utilità di avvio.)  
  
-   I registri di sicurezza indicano che non è stato possibile accedere con l'account NT SERVICE\MSSQLLAUNCHPAD.  
  
Per informazioni su come assegnare le autorizzazioni necessarie a questo gruppo di utenti, vedere [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md). 

> [!NOTE]
> 
> Questa limitazione non si applica se si usano account di accesso SQL per eseguire script R da una workstation remota. 

  
## <a name="remote-execution-via-odbc"></a>Esecuzione remota tramite ODBC   
 Se si usa una workstation per l'analisi scientifica dei dati e ci si connette al computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire comandi R tramite le funzioni **RevoScaleR**, è possibile che venga restituito un errore durante l'uso di chiamate ODBC che scrivono dati sul server. 
 
 Il motivo è identico a quello descritto nella sezione precedente. In fase di installazione, R Services crea un gruppo di account di lavoro che vengono usati per l'esecuzione delle attività di R. Se tuttavia questi account non possono connettersi al server, le chiamate ODBC non possono essere eseguite per conto dell'utente. 
 
 Si noti che questa limitazione non si applica se si usano account di accesso SQL per eseguire script R da una workstation remota perché le credenziali di accesso SQL vengono passate in modo esplicito dal client R all'istanza di SQL Server e quindi a ODBC.
  
Per abilitare l'autenticazione implicita, è necessario concedere le autorizzazioni a questo gruppo di account di lavoro come indicato di seguito:  
    
1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] come amministratore dell'istanza in cui si eseguirà il codice R. 

2. Eseguire lo script seguente. Assicurarsi di modificare il nome del gruppo di utenti, se è stato cambiato quello predefinito, e anche i nomi del computer e dell'istanza.
    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO  
    ```

Per altre informazioni e per la procedura che consente di eseguire questa operazione tramite l'interfaccia utente di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vedere [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).

    
## <a name="errors-during-setup-because-r-components-cannot-be-installed"></a>Errori di installazione dei componenti R  
 Quando si installa R Services (In-Database) tramite il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e si fa clic su **Accetto** nella pagina contenente le condizioni di licenza di Microsoft R Open, il programma di installazione dovrebbe individuare i componenti e avviare l'installazione quando vengono installati altri componenti. In questi casi, tuttavia, è possibile che l'installazione dei componenti non venga completata:  
  
-   Si sta eseguendo un'installazione offline e i componenti non possono essere scaricati.  
  
     [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)  
  
-   Si usa l'opzione che consente di verificare la disponibilità di aggiornamenti e il servizio di aggiornamento restituisce un errore perché non riesce a trovare la versione corretta del componente.  
  
  Questo è un problema noto che è stato risolto nella versione RC3.  
  
 
  
## <a name="upgrade-of-r-server-standalone-to-rc3-requires-uninstallation-using-the-rc2-setup-utility"></a>L'aggiornamento di R Server (Standalone) alla versione RC3 richiede la disinstallazione tramite l'utilità di installazione della versione RC2
 Microsoft R Server (Standalone) è diventato disponibile in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2. Per eseguire l'aggiornamento alla versione RC3 di Microsoft R Server, è necessario prima disinstallarlo tramite il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2 e quindi reinstallarlo con il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC3.  
  
1.  Disinstallare R Server (Standalone) per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2 usando il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Eseguire l'aggiornamento di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] alla versione RC3 e selezionare l'opzione per installare R Services (In-Database). In questo modo, l'istanza di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] viene aggiornata alla versione RC3. Non sono necessarie altre operazioni di configurazione.  
  
3.  Eseguire il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per RC3 ancora una volta e installare Microsoft R Server (Standalone).  

Questa soluzione non è necessaria quando si esegue l'aggiornamento alla versione RTM di Microsoft R Server.

## <a name="see-also"></a>Vedere anche  
 [Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [Introduzione a Microsoft R Server &#40;Standalone&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  