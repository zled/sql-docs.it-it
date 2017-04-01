---
title: "Installazione e configurazione di Master Data Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 37
---
# Installazione e configurazione di Master Data Services
  Questo articolo descrive come installare [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in un computer Windows Server 2012 R2, impostare il database MDS e il sito Web e distribuire i modelli e i dati di esempio. [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) consente alle organizzazioni di gestire una versione attendibile dei dati.   
   
Per una panoramica sull'organizzazione dei dati in [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], vedere [Panoramica di Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md).     
  
 Per informazioni sulle nuove funzionalità di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], vedere [Novità in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md).  
 
Per i link a video e altre risorse di training per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], vedere [Informazioni su SQL Server Master Data Services](../master-data-services/learn-sql-server-master-data-services.md). 
  
> **Download**  
>-   Scaricare [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]dalla pagina  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
>-   Se si ha un account di Azure,  fare clic **[qui](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** per creare rapidamente una macchina virtuale in cui è già installato [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  .  
 
> **Impossibile creare un sito Web di MDS**
>>Leggere quest'articolo del supporto tecnico Microsoft per istruzioni sulla risoluzione del problema.
[Impossibile creare un sito Web di MDS tramite un account con privilegi limitati in SQL Server 2016](https://aka.ms/mdssupport) 
  
## <a name="installing-master-data-services-and-iis-roles-and-features"></a>Installazione di Master Data Services e ruoli e funzionalità IIS  
 Per installare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usare l'installazione guidata di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]o un prompt dei comandi.  
  
 **Per installare [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tramite [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup in un computer Windows Server 2012 R2**  
  
1.  Fare doppio clic su Setup.exe e seguire i passaggi dell'installazione guidata.  
  
2.  Nella pagina [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Selezione funzionalità **selezionare** in **Funzionalità condivise**.  
  
     Vengono installati [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], gli assembly, uno snap-in di Windows PowerShell, nonché cartelle e file per i servizi e le applicazioni Web.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  Eseguire i passaggi dell'Installazione guidata.  
  
4.  In [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]fare clic sull'icona **Server Manager** sulla barra delle applicazioni sul **Desktop**.  
  
     ![Icon for the Server Manager in Windows Server 2012 taskbar](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Icon for the Server Manager in Windows Server 2012 taskbar")  
  
5.  In **Server Manager**fare clic su **Aggiungi ruoli e funzionalità** nel menu **Gestisci** .  
  
     ![In Server Manage, the Add Roles and Features menu command](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "In Server Manage, the Add Roles and Features menu command")  
  
6.  Nella pagina **Tipo di installazione** dell' **Aggiunta guidata ruoli e funzionalità**accettare il valore predefinito**Installazione basata su ruoli o basata su funzionalità**e fare clic su **Avanti**.  
  
7.  Fare clic su **Selezionare un server dal pool di server**e quindi fare clic sul server in cui è installato [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     ![Server Selection page on the Add Roles and Features Wizard](../master-data-services/media/mds-servermanagerdashboard-addrolesandfeatureswizard-serverselection.png "Server Selection page on the Add Roles and Features Wizard")  
  
8.  Nella casella **Ruoli** fare clic sui ruoli e sui servizi ruolo obbligatori per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] in [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]e quindi fare clic su **Avanti**. Le immagini seguenti mostrano i ruoli selezionati e obbligatori e i servizi ruolo.  
  
    > [!WARNING]  
    >  Non installare il servizio ruolo Pubblicazioni WebDAV. Pubblicazioni WebDAV non è compatibile con [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
    > [!IMPORTANT]  
    > La funzionalità **Compressione contenuto dinamico** è abilitata per impostazione predefinita. Questo riduce in modo significativo le dimensioni della risposta XML e salva le operazioni I/O di rete, anche se aumenta l'utilizzo della CPU.  Per altre informazioni, vedere **[CTP 2.0] Prestazioni migliorate** in [What's New in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
    |Ruoli e servizi ruolo|Ruoli e servizi ruolo|  
    |-----------------------------|-----------------------------|  
    |![Common HTTP Features](../master-data-services/media/mds-servermanagerdashboard-commonhttpfeaturesroles.png "Common HTTP Features")|![Health Diagnostics Roles](../master-data-services/media/mds-servermanagerdashboard-healthdiagnosticsroles.png "Health Diagnostics Roles")|  
    |![Performance Roles](../master-data-services/media/mds-servermanagerdashboard-performanceroles.png "Performance Roles")|![Security Roles](../master-data-services/media/mds-servermanagerdashboard-securityroles.png "Security Roles")|  
    |![WebServer Application Development Roles](../master-data-services/media/mds-servermanagerdashboard-webserverapplicationdevelopmentroles.png "WebServer Application Development Roles")|![Management Tools](../master-data-services/media/mds-servermanagerdashboard-managementtoolsroles.png "Management Tools")|  
  
     Per un elenco dei ruoli e dei servizi ruolo obbligatori per altri sistemi operativi, vedere [Requisiti dell'applicazione Web &#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
9. Nella casella **Funzionalità** fare clic sulle funzionalità obbligatorie per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] in [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]e quindi fare clic su **Avanti**. Le immagini seguenti mostrano le funzionalità selezionate e obbligatorie.  
  
    |Funzionalità|Funzionalità|  
    |--------------|--------------|  
    |![Net Framework Features](../master-data-services/media/mds-servermanagerdashboard-netframeworkfeatures.png "Net Framework Features")|![Windows Process Features](../master-data-services/media/mds-servermanagerdashboard-windowsprocessfeatures.png "Windows Process Features")|  
  
     Per un elenco delle funzionalità obbligatorie per altri sistemi operativi, vedere [Requisiti dell'applicazione Web &#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
 Per altre informazioni sull'installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite il programma di installazione, vedere [Installare SQL Server 2016 dall'Installazione guidata &#40;programma di installazione&#41;](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
 Per altre informazioni sull'installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite un prompt dei comandi, vedere [Installazione di SQL Server 2016 dal prompt dei comandi](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Se si utilizza un prompt dei comandi, [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è disponibile come parametro della funzionalità.  
  
 Per una breve descrizione con collegamenti a informazioni aggiuntive sulle attività di pre-installazione, vedere [Installazione di Master Data Services](../master-data-services/install-windows/install-master-data-services.md).  
  
##  <a name="a-namesetupweba-setting-up-the-database-and-website"></a><a name="SetUpWeb"></a> Impostazione del database e del sito Web  
 **Per impostare il database e il sito Web usando [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]**  
  
1.  Avviare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]e fare clic su **Configurazione database** nel riquadro sinistro.  
  
2.  Fare clic su **Crea database**e quindi fare clic su **Avanti** nella **Creazione guidata database**.  
  
3.  Nella pagina **Server di database** selezionare il **Tipo di autenticazione** e fare clic su **Test connessione** per verificare di poter stabilire la connessione al database usando le credenziali per il tipo di autenticazione selezionato.  
  
    > [!NOTE]  
    >  Quando si seleziona il tipo di autenticazione **Utente corrente - sicurezza integrata** , la casella **Nome utente** è di sola lettura e visualizza il nome dell'account utente di Windows connesso al computer.  
  
     ![The Database server page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-serverpage.png "The Database server page in the Create Database Wizard")  
  
4.  Digitare un nome nel campo **Nome database** . Facoltativamente, per selezionare regole di confronto di Windows e specificare una o più opzioni disponibili, ad esempio **Distinzione maiuscole/minuscole**, deselezionare la casella di controllo **Regole di confronto predefinite di SQL Server** .  
  
     ![The Database page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-databasepage.png "The Database page in the Create Database Wizard")  
  
     Per altre informazioni sulle regole di confronto di Windows, vedere [Windows_collation_name (Transact-SQL)](https://msdn.microsoft.com/library/ms188046.aspx).  
  
5.  Nel campo **Nome utente** specificare l'account di Windows dell'utente che sarà l'utente con privilegi avanzati predefinito di Master Data Services. L'utente con privilegi avanzati ha accesso a tutte le aree funzionali e può aggiungere, eliminare e aggiornare tutti i modelli.  
  
     ![The Administrator Account page in the Create Database Wizard.](../master-data-services/media/mds-configurationmanager-createdatabasewizard-adminpage.png "The Administrator Account page in the Create Database Wizard.")  
  
6.  Fare clic su **Avanti** per visualizzare un riepilogo delle impostazioni per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] e quindi fare di nuovo clic su **Avanti** per creare il database.  
  
     Per altre informazioni sulle impostazioni della **Creazione guidata database**, vedere [Procedura guidata Crea database &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
7.  Nella pagina Configurazione database in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] fare clic su Selezione database.  
  
8.  Fare clic su **Connetti**e quindi selezionare il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] creato nel passaggio 6.  
  
     ![Connect to Database dialog box for the Database Configuration page](../master-data-services/media/mds-configurationmanager-selectdatabasebutton-connecttodatabasedialog.png "Connect to Database dialog box for the Database Configuration page")  
  
     L'impostazione del database è stata completata. La pagina **Configurazione database** visualizza ora l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a cui si è connessi per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], il database creato e la versione del database corrente.  
  
     ![Database Configuration page in the Configuration Manager shows a completed database setup.](../master-data-services/media/mds-configurationmanager-databaseconfig-completed.png "Database Configuration page in the Configuration Manager shows a completed database setup.")  
  
9. In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]fare clic su **Configurazione Web** nel riquadro sinistro.  
  
10. Nella casella di riepilogo **Sito Web** fare clic su **Sito Web predefinito**e quindi fare clic su **Crea** per creare un'applicazione Web.  
  
    > [!NOTE]  
    >  Quando si seleziona **Sito Web predefinito**, è necessario creare un'applicazione Web. Se si seleziona **Crea nuovo sito Web** nella casella di riepilogo, l'applicazione viene creata automaticamente.  
  
     ![Web Configuration page in the Configuration Manager](../master-data-services/media/mds-configurationmanager-webconfig.png "Web Configuration page in the Configuration Manager")  
  
11. Nella sezione **Pool di applicazioni** eseguire una di queste operazioni.  
  
    -   Immettere lo stesso nome utente specificato nel passaggio 5 per l' **Account amministratore**del database, immettere la password e quindi fare clic su **OK**.  
  
         **Oppure**  
  
    -   Immettere un nome utente diverso, immettere la password e quindi fare clic su OK.  
  
         Non è necessario usare lo stesso account quando si crea il database e l'applicazione Web.  
  
     ![Create Web Application dialog box, Web Configuration page](../master-data-services/media/mds-configurationmanager-webconfig-createwebapplication.png "Create Web Application dialog box, Web Configuration page")  
  
     Per altre informazioni sula finestra di dialogo **Crea applicazione Web**, vedere [Finestra di dialogo Crea applicazione Web &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
12. Nella pagina **Configurazione Web** nella casella **Applicazione Web** fare clic sull'applicazione creata e quindi fare clic su **Seleziona** nella sezione **Associare l'applicazione al database**.  
  
13. Fare clic su **Connetti**, selezionare il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] che si vuole associare all'applicazione Web e quindi fare clic su **OK**.  
  
     L'impostazione del sito Web è stata completata. La pagina **Configurazione Web** visualizza ora il sito Web selezionato, l'applicazione Web creata e il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] associato all'applicazione.  
  
     ![The completed Web site configuration](../master-data-services/media/mds-configurationmanager-webconfig-completed.png "The completed Web site configuration")  
  
     Per altre informazioni sulle impostazioni della pagina Configurazione Web, vedere [Pagina Configurazione Web &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
 È anche possibile usare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per specificare altre impostazioni per le applicazioni e i servizi Web associati al database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Ad esempio, è possibile specificare la frequenza con cui i dati vengono caricati o quella con cui viene inviata la posta elettronica della convalida. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
##  <a name="a-namedeploysamplea-deploying-sample-models-and-data"></a><a name="deploySample"></a> Distribuzione di modelli di esempio e dati  
 I seguenti tre pacchetti di modelli di esempio sono inclusi con  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].   Questi modelli di esempio includono dati. **Il percorso predefinito dei pacchetti dei modelli di esempio è %programfiles%\Microsoft SQL Server\130\Master Data Services\Samples\Packages.**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 I pacchetti vengono distribuiti con lo strumento MDSModelDeploy. Il percorso predefinito dello strumento MDSModelDeploy è *unità*\Programmi\Microsoft SQL Server\ 130\Master Data Services\Configuration.  
  
 Per informazioni sui prerequisiti per l'esecuzione di questo strumento, vedere [Distribuire un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
 Per informazioni sugli aggiornamenti dei dati per il supporto delle nuove funzionalità in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vedere [Esempi: pacchetti di distribuzione di modelli &#40;Master Data Services&#41;](../Topic/Samples:%20Model%20Deployment%20Packages%20\(Master%20Data%20Services\).md).  
  
 **Per distribuire i modelli di esempio**  
  
1.  Copiare i pacchetti di modelli di esempio in *unità*\Programmi\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
2.  Aprire un prompt dei comandi di amministratore e passare a MDSModelDeploy.exe eseguendo il comando seguente.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration  
    ```  
  
3.  Distribuire ogni modello di esempio a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] eseguendo ciascuno dei comandi seguenti.  
  
    > [!IMPORTANT]  
    >  Negli esempi seguenti, il valore del servizio `MDS1` è specificato. Il valore viene usato se è stata selezionata l'opzione  **Sito Web predefinito** durante l'impostazione del sito Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  Vedere la sezione [Impostazione del database e del sito Web](#SetUpWeb) .  
    >   
    >  Se è stato creato un nuovo sito Web o è stato selezionato un altro sito Web, eseguire il comando seguente per determinare il valore del servizio corretto.  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  Il primo valore di servizio dell'elenco di valori restituiti è il valore specificato per la distribuzione di un modello.  
  
     **Per distribuire il modello di esempio chartofaccounts_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model ChartofAccounts -service MDS1  
    ```  
  
     **Per distribuire il modello di esempio customer_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **Per distribuire il modello di esempio product_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Product -service MDS1  
  
    ```  
  
     Quando la distribuzione di un modello è stata completata, viene visualizzato il messaggio **Operazione MDSModelDeploy completata** .  
  
     L'immagine seguente mostra il comando per la distribuzione del modello di esempio product_en.pkg.  
  
     ![Command line for deploying the Product sample model](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Command line for deploying the Product sample model")  
  
4.  Per visualizzare i modelli di esempio, eseguire le operazioni seguenti.  
  
    1.  Passare al sito Web di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] impostato. Vedere la sezione [Impostazione del database e del sito Web](#SetUpWeb) .  
  
         L'indirizzo del sito Web è http://*nome server*/*applicazione Web*/.  
  
    2.  Selezionare un modello dalla casella di riepilogo **Modello** e fare clic su **Visualizzatore**.  
  
         ![MDS Web site, home page.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "MDS Web site, home page.")  
  
## <a name="next-step"></a>Passaggio successivo  
 Creare un nuovo modello e le entità per i dati. Vedere [Creare un modello &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md) e [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 Per una panoramica sull'uso di un modello e delle entità per creare una struttura per i dati in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vedere [Panoramica di Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
## <a name="did-this-article-help-you-were-listening"></a>Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services)  
  
## <a name="see-also"></a>Vedere anche  
 [Master Data Services Database](../master-data-services/master-data-services-database.md)   
 [Applicazione Web Gestione dati master](../master-data-services/master-data-manager-web-application.md)   
 [Pagina Configurazione database &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Novità in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  