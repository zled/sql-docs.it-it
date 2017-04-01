---
title: "Catalogo SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Catalogo SSIS
  Il catalogo **SSISDB** è il punto centrale dell'utilizzo di progetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) che sono stati distribuiti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Ad esempio, è possibile impostare parametri di progetti e pacchetti, configurare ambienti per specificare valori di runtime per i pacchetti, eseguire e risolvere i problemi dei pacchetti e gestire le operazioni del server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Tra gli oggetti archiviati nel catalogo **SSISDB** sono inclusi progetti, pacchetti, parametri, ambienti e cronologia operativa.  
  
 È possibile eseguire una query sulle viste nel database **SSISDB** per verificare oggetti, impostazioni e dati operativi archiviati nel catalogo **SSISDB** . È possibile gestire gli oggetti chiamando le stored procedure nel database **SSISDB** o usando l'interfaccia utente del catalogo **SSISDB** . In molti casi è possibile eseguire la stessa attività nella UI o chiamando una stored procedure.  
  
 Per gestire il database **SSISDB** , si consiglia di applicare criteri aziendali standard per la gestione di database utente. Per informazioni sulla creazione dei piani di manutenzione, vedere [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md).  
  
 Il catalogo **SSISDB** e il database **SSISDB** supportano Windows PowerShell. Per altre informazioni sull'uso di SQL Server con Windows PowerShell, vedere [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md). Per gli esempi di come usare Windows PowerShell per completare attività quali la distribuzione di un progetto, vedere l'intervento sul blog relativo a [SSIS e PowerShell in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539)sul sito blogs.msdn.com.  
  
 Per altre informazioni sulla visualizzazione dei dati delle operazioni, vedere [Esecuzione di pacchetti e altre operazioni di monitoraggio](../../integration-services/performance/monitor-running-packages-and-other-operations.md).  
  
 È possibile accedere al catalogo **SSISDB** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eseguendo una connessione al motore di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quindi espandendo il nodo **Cataloghi di Integration Services** in Esplora oggetti. È possibile accedere al database **SSISDB** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] espandendo il nodo Database in Esplora oggetti.  
  
> [!NOTE] Non è possibile rinominare il database **SSISDB** .  
  
> [!NOTE] Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui è collegato il database **SSISDB** viene arrestata o non risponde, il processo ISServerExec.exe termina. Un messaggio verrà scritto nel log eventi di Windows.  
>   
>  Se si verifica un failover delle risorse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come parte del failover di un cluster, i pacchetti in esecuzione non vengono riavviati. È possibile usare i checkpoint per riavviare i pacchetti. Per ulteriori informazioni, vedere [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="in-this-topic"></a>Contenuto dell'argomento  
  
-   [Identificatori dell'oggetto catalogo](../../integration-services/service/ssis-catalog.md#CatalogObjectIdentifiers)  
  
-   [Configurazione del catalogo](../../integration-services/service/ssis-catalog.md#Configuration)  
  
-   [Autorizzazioni](../../integration-services/service/ssis-catalog.md#Permissions)  
  
-   [Cartelle](../../integration-services/service/ssis-catalog.md#Folders)  
  
-   [Progetti e pacchetti](../../integration-services/service/ssis-catalog.md#ProjectsAndPackages)  
  
-   [Parametri](../../integration-services/service/ssis-catalog.md#Parameters)  
  
-   [Ambienti server, variabili del server e riferimenti all'ambiente del server](../../integration-services/service/ssis-catalog.md#ServerEnvironments)  
  
-   [Esecuzioni e convalide](../../integration-services/service/ssis-catalog.md#Executions)  
  
-   [Supporto di AlwaysOn](../../integration-services/service/ssis-catalog.md#AlwaysOn)  
  
-   [Attività correlate](../../integration-services/service/ssis-catalog.md#RelatedTasks)  
  
-   [Contenuto correlato](../../integration-services/service/ssis-catalog.md#RelatedContent)  
  
##  <a name="a-namecatalogobjectidentifiersa-catalog-object-identifiers"></a><a name="CatalogObjectIdentifiers"></a> Identificatori dell'oggetto catalogo  
 Quando si crea un nuovo oggetto nel catalogo, assegnare un nome all'oggetto. Il nome di un oggetto costituisce l'identificatore. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definisce le regole per i caratteri che possono essere usati in un identificatore. I nomi degli oggetti seguenti devono rispettare le regole per gli identificatori.  
  
-   Cartella  
  
-   Progetto  
  
-   Ambiente  
  
-   Parametro  
  
-   Variabile di ambiente  
  
###  <a name="a-namefoldera-folder-project-environment"></a><a name="Folder"></a> Cartella, progetto, ambiente  
 Quando si rinomina una cartella, un progetto o un ambiente, considerare le regole riportate di seguito.  
  
-   I caratteri non validi includono i caratteri ASCII/Unicode compresi tra 1 e 31, le virgolette ("), i simboli minore di (\<) e maggiore di (>), la barra verticale (|), il backspace (\b), il valore Null (\0) e la tabulazione (\t).  
  
-   Nel nome potrebbero non essere contenuti spazi iniziali o finali.  
  
-   Il simbolo @ non è consentito come primo carattere, ma può essere usato nei caratteri successivi.  
  
-   La lunghezza del nome deve essere maggiore di 0 e minore o uguale a 128.  
  
###  <a name="a-nameparametera-parameter"></a><a name="Parameter"></a> Parametro  
 Quando si rinomina un parametro, considerare le regole seguenti:  
  
-   Il primo carattere del nome deve essere una lettera, come definito nello standard Unicode 2.0, o un carattere di sottolineatura (_).  
  
-   I caratteri successivi possono includere lettere o numeri, come definito nello standard Unicode 2.0, o un carattere di sottolineatura (_).  
  
###  <a name="a-nameenvironmentvariablea-environment-variable"></a><a name="EnvironmentVariable"></a> Variabile di ambiente  
 Quando si rinomina una variabile di ambiente, considerare le regole seguenti:  
  
-   I caratteri non validi includono i caratteri ASCII/Unicode compresi tra 1 e 31, le virgolette ("), i simboli minore di (\<) e maggiore di (>), la barra verticale (|), il backspace (\b), il valore Null (\0) e la tabulazione (\t).  
  
-   Nel nome potrebbero non essere contenuti spazi iniziali o finali.  
  
-   Il simbolo @ non è consentito come primo carattere, ma può essere usato nei caratteri successivi.  
  
-   La lunghezza del nome deve essere maggiore di 0 e minore o uguale a 128.  
  
-   Il primo carattere del nome deve essere una lettera, come definito nello standard Unicode 2.0, o un carattere di sottolineatura (_).  
  
-   I caratteri successivi possono includere lettere o numeri, come definito nello standard Unicode 2.0, o un carattere di sottolineatura (_).  
  
##  <a name="a-nameconfigurationa-catalog-configuration"></a><a name="Configuration"></a> Configurazione del catalogo  
 È possibile ottimizzare la modalità di comportamento del catalogo modificandone le relative proprietà. Le proprietà del catalogo consentono di definire come vengono crittografati i dati sensibili e come vengono mantenuti i dati del controllo delle versioni dei progetti. Per impostare le proprietà del catalogo, usare la finestra di dialogo **Proprietà catalogo** o chiamare la stored procedure [catalog.configure_catalog &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md). Per visualizzare le proprietà, usare la finestra di dialogo o eseguire una query su [catalog.catalog_properties &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md). È possibile accedere alla finestra di dialogo facendo clic con il pulsante destro del mouse su **SSISDB** in Esplora oggetti.  
  
###  <a name="a-namecleanupa-operations-and-project-version-cleanup"></a><a name="Cleanup"></a> Operazioni e pulizia della versione del progetto  
 I dati dello stato per molte delle operazioni nel catalogo vengono archiviati nelle tabelle di database interne. Ad esempio, tramite il catalogo si tiene traccia dello stato delle esecuzioni dei pacchetti e delle distribuzioni dei progetti. Per gestire le dimensioni dei dati delle operazioni, è possibile usare **Processo di manutenzione del server SSIS** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per rimuovere i dati vecchi. Questo processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene creato quando viene installato [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 È possibile aggiornare o ridistribuire un progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] distribuendolo con lo stesso nome nella stessa cartella del catalogo. Per impostazione predefinita, ogni volta che si ridistribuisce un progetto, il catalogo **SSISDB** mantiene la versione precedente del progetto. Per gestire le dimensioni dei dati delle operazioni, è possibile usare **Processo di manutenzione del server SSIS** per rimuovere le versioni precedenti dei progetti.  
 
Per eseguire il **processo di manutenzione del server SSIS**, SSIS crea l'accesso di SQL Server **##MS_SSISServerCleanupJobLogin##**. Questo accesso è destinato esclusivamente all'uso interno da parte di SSIS.
  
 Tramite le seguenti proprietà del catalogo **SSISDB** viene definito il comportamento di questo processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. È possibile visualizzare e modificare le proprietà tramite la finestra di dialogo **Proprietà catalogo** oppure usando [catalog.catalog_properties &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) e [catalog.configure_catalog &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 **Pulisci log periodicamente**  
 Il passaggio del processo per la pulizia delle operazioni viene eseguito quando questa proprietà è impostata su **True**.  
  
 **Periodo di memorizzazione (giorni)**  
 Definisce la validità massima di dati di operazioni consentiti (in giorni). I dati più obsoleti vengono rimossi.  
  
 Il valore minimo è 1 giorno. Il valore massimo è limitato solo dal valore massimo dei dati **int** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni su questo tipo di dati, vedere [int, bigint, smallint e tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).  
  
 **Rimuovi periodicamente versioni precedenti**  
 Il passaggio del processo per la pulizia della versione del progetto viene eseguito quando questa proprietà è impostata su **True**.  
  
 **Numero massimo di versioni per progetto**  
 Viene definito il numero di versioni di un progetto che vengono archiviate nel catalogo. Le versioni precedente dei progetti vengono rimosse.  
  
###  <a name="a-nameencryptiona-encryption-algorithm"></a><a name="Encryption"></a> Algoritmo di crittografia  
 La proprietà **Algoritmo di crittografia** consente di specificare il tipo di crittografia usato per crittografare i valori dei parametri sensibili. È possibile scegliere tra i tipi di crittografia seguenti:  
  
-   AES_256 (predefinito)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 Quando si distribuisce un progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], il catalogo crittografa automaticamente i dati del pacchetto e i valori sensibili. Il catalogo inoltre decrittografa automaticamente i dati quando viene recuperato. Il catalogo SSISDB usano il livello di protezione **ServerStorage** . Per altre informazioni, vedere [Access Control for Sensitive Data in Packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md).  
  
 La modifica dell'algoritmo di crittografia è un'operazione che richiede molto tempo. Innanzitutto, nel server deve essere usato l'algoritmo specificato in precedenza per decrittografare tutti i valori di configurazione. Successivamente, deve essere usato il nuovo algoritmo per crittografare nuovamente i valori. Durante questa fase, nel server non è possibile eseguire altre operazioni usando [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pertanto, per consentire il funzionamento di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] senza interruzioni, l'algoritmo di crittografia è un valore di sola lettura nella finestra di dialogo di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Per modificare l'impostazione della proprietà **Algoritmo di crittografia** , impostare il database **SSISDB** sulla modalità utente singolo e quindi chiamare la stored procedure catalog.configure_catalog. Usare ENCRYPTION_ALGORITHM per l'argomento *property_name*. Per i valori di proprietà supportati, vedere [catalog.catalog_properties &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md). Per altre informazioni sulla stored procedure, vedere [catalog.configure_catalog &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 Per altre informazioni sulla modalità utente singolo, vedere [Impostare un database in modalità utente singolo](../../relational-databases/databases/set-a-database-to-single-user-mode.md). Per informazioni sulla crittografia e sui relativi algoritmi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere gli argomenti della sezione [Crittografia di SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md).  
  
 Per la crittografia viene usata una chiave master del database. La chiave viene creata durante la creazione del catalogo. Per altre informazioni, vedere [Creare il catalogo SSIS](../../integration-services/service/create-the-ssis-catalog.md).  
  
 Nella tabella seguente vengono elencati i nomi delle proprietà visualizzati nella finestra di dialogo **Proprietà catalogo** e le proprietà corrispondenti nella vista del database.  
  
|Nome proprietà (finestra di dialogo**Proprietà catalogo** )|Nome proprietà (vista di database)|  
|---------------------------------------------------------|-------------------------------------|  
|Nome algoritmo di crittografia|ENCRYPTION_ALGORITHM|  
|Pulisci log periodicamente|OPERATION_CLEANUP_ENABLED|  
|Periodo di memorizzazione (giorni)|RETENTION_WINDOW|  
|Rimuovi periodicamente versioni precedenti|VERSION_CLEANUP_ENABLED|  
|Numero massimo di versioni per progetto|MAX_PROJECT_VERSIONS|  
|Livello di registrazione predefinito per l'intero server|SERVER_LOGGING_LEVEL|  
  
##  <a name="a-namepermissionsa-permissions"></a><a name="Permissions"></a> Autorizzazioni  
 I progetti, gli ambienti e i pacchetti sono contenuti in cartelle che sono oggetti a protezione diretta. È possibile concedere le autorizzazioni a una cartella, inclusa l'autorizzazione MANAGE_OBJECT_PERMISSIONS. L'autorizzazione MANAGE_OBJECT_PERMISSIONS consente di delegare l'amministrazione del contenuto di una cartella a un utente senza dover concedere all'utente l'appartenenza al ruolo ssis_admin. È inoltre possibile concedere autorizzazioni per progetti, ambienti e operazioni. Le operazioni includono l'inizializzazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], la distribuzione di progetti, la creazione e l'avvio di esecuzioni, la convalida di progetti e pacchetti e la configurazione del catalogo **SSISDB** .  
  
 Per altre informazioni sui ruoli di database, vedere [Ruoli a livello di database](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 Il catalogo SSISDB usano un trigger DDL, ddl_cleanup_object_permissions, per applicare l'integrità delle informazioni sulle autorizzazioni per le entità a protezione diretta di SSIS. Il trigger viene attivato quando un'entità di database, ad esempio un utente del database, un ruolo del database o un ruolo applicazione di database, viene rimossa dal database SSISDB.  
  
 Se l'entità ha concesso o negato le autorizzazioni ad altre entità, è necessario revocare le autorizzazioni fornite dall'utente che concede le autorizzazioni, prima di poter rimuovere l'entità. In caso contrario, viene restituito un messaggio di errore quando il sistema tenta di rimuovere l'entità. Tramite il trigger vengono rimossi tutti i record di autorizzazione in cui l'entità di database è un utente autorizzato.  
  
 È consigliabile che il trigger non sia disabilitato perché in questo modo viene assicurata l'assenza di record di autorizzazione orfani dopo l'eliminazione di un'entità di database dal database **SSISDB** .  
  
### <a name="managing-permissions"></a>Gestione delle autorizzazioni  
 È possibile gestire le autorizzazioni tramite l'interfaccia utente di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , le stored procedure e lo spazio dei nomi <xref:Microsoft.SqlServer.Management.IntegrationServices> .  
  
 Per gestire le autorizzazioni mediante l'interfaccia utente di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , usare le finestre di dialogo seguenti.  
  
-   Per una cartella, usare la pagina **Autorizzazioni** in [Folder Properties Dialog Box](../../integration-services/service/folder-properties-dialog-box.md).  
  
-   Per un progetto, usare la pagina **Autorizzazioni** in [Project Properties Dialog Box](../../integration-services/service/project-properties-dialog-box.md).  
  
-   Per un ambiente, usare la pagina **Autorizzazioni** nella finestra di dialogo [NIB: Proprietà ambiente](http://msdn.microsoft.com/it-it/6a91a8d4-0006-4cfd-9759-3e4295ae452b).  
  
 Per gestire le autorizzazioni usando Transact-SQL, chiamare [catalog.grant_permission &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md), [catalog.deny_permission &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md) e [catalog.revoke_permission &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md). Per visualizzare le autorizzazioni valide per l'entità corrente per tutti gli oggetti, eseguire una query su [catalog.effective_object_permissions &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md). In questo argomento vengono fornite le descrizioni dei diversi tipi di autorizzazioni. Per visualizzare le autorizzazioni assegnate in modo esplicito all'utente, eseguire una query su [catalog.explicit_object_permissions &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md).  
  
##  <a name="a-namefoldersa-folders"></a><a name="Folders"></a> Cartelle  
 Nel catalogo di **SSISDB** della cartella sono contenuti uno o più pacchetti e ambienti. È possibile usare la vista [catalog.folders &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-folders-ssisdb-database.md) per accedere alle informazioni sulle cartelle del catalogo. È possibile usare le stored procedure seguenti per gestire cartelle.  
  
-   [catalog.create_folder &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
  
-   [catalog.delete_folder &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
  
-   [catalog.rename_folder &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
  
-   [catalog.set_folder_description &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
  
##  <a name="a-nameprojectsandpackagesa-projects-and-packages"></a><a name="ProjectsAndPackages"></a> Progetti e pacchetti  
 Ogni progetto può contenere più pacchetti. I progetti e i pacchetti possono contenere entrambi i parametri e i riferimenti agli ambienti. È possibile accedere ai parametri e ai riferimenti agli ambienti tramite [Configure Dialog Box](../../integration-services/service/configure-dialog-box.md).  
  
 È possibile eseguire altre attività progetto chiamando le stored procedure seguenti.  
  
-   [catalog.delete_project &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
  
-   [catalog.deploy_project &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
  
-   [catalog.get_project &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
  
-   [catalog.move_project &#40;&#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-move-project-ssisdb-database.md)  
  
-   [catalog.restore_project &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
  
 Queste viste forniscono i dettagli su pacchetti, progetti e versioni di progetto.  
  
-   [catalog.projects &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
  
-   [catalog.packages &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
  
-   [catalog.object_versions &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
  
##  <a name="a-nameparametersa-parameters"></a><a name="Parameters"></a> Parametri  
 È possibile usare i parametri per assegnare i valori alle proprietà dei pacchetti durante la fase di esecuzione. Per impostare il valore di un parametro del pacchetto o del progetto e per cancellare il valore, chiamare [catalog.set_object_parameter_value &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md) e [catalog.clear_object_parameter_value &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md). Per impostare il valore di un parametro per un'istanza di esecuzione, chiamare [catalog.set_execution_parameter_value &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md). È possibile recuperare i valori di parametro predefiniti chiamando [catalog.get_parameter_values &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md).  
  
 Queste viste mostrano i parametri per tutti i pacchetti e i progetti nonché i valori del parametro usati per un'istanza di esecuzione.  
  
-   [catalog.object_parameters &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
  
-   [catalog.execution_parameter_values &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
  
##  <a name="a-nameserverenvironmentsa-server-environments-server-variables-and-server-environment-references"></a><a name="ServerEnvironments"></a> Ambienti server, variabili del server e riferimenti all'ambiente del server  
 Gli ambienti del server contengono le variabili del server. I valori delle variabili possono essere usati quando un pacchetto viene eseguito o convalidato nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Le stored procedure seguenti consentono di effettuare molte altre attività di gestione per ambienti e variabili.  
  
-   [catalog.create_environment &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
  
-   [catalog.delete_environment &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
  
-   [catalog.move_environment &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
  
-   [catalog.rename_environment &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
  
-   [catalog.set_environment_property &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
  
-   [catalog.create_environment_variable &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
  
-   [catalog.delete_environment_variable &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_property &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_value &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
  
 Chiamando la stored procedure [catalog.set_environment_variable_protection &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md) è possibile impostare il bit di importanza per una variabile.  
  
 Per usare il valore di una variabile del server, specificare il riferimento tra il progetto e l'ambiente del server. È possibile usare le stored procedure seguenti per creare ed eliminare riferimenti. È anche possibile indicare se l'ambiente può essere individuato nella stessa cartella del progetto o in una cartella diversa.  
  
-   [catalog.create_environment_reference &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
  
-   [catalog.delete_environment_reference &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
  
-   [catalog.set_environment_reference_type &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
  
 Per ulteriori dettagli sugli ambienti e le variabili, eseguire una query su queste viste.  
  
-   [catalog.environments &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
  
-   [catalog.environment_variables &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
  
-   [catalog.environment_references &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
  
##  <a name="a-nameexecutionsa-executions-and-validations"></a><a name="Executions"></a> Esecuzioni e convalide  
 Un'esecuzione è un'istanza di un'esecuzione del pacchetto. Chiamare [catalog.create_execution &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md) e [catalog.start_execution &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md) per creare e avviare un'esecuzione. Per interrompere un'esecuzione o una convalida del pacchetto/progetto, chiamare [catalog.stop_operation &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md).  
  
 Per interrompere un pacchetto in esecuzione e creare un file di dump, chiamare la stored procedure catalog.create_execution_dump. Un file di dump fornisce le informazioni sull'esecuzione di un pacchetto che possono consentire di risolvere i problemi dell'esecuzione. Per altre informazioni sulla generazione e sulla configurazione dei file di dump, vedere [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).  
  
 Per i dettagli sulle esecuzioni, le convalide, i messaggi registrati durante le operazioni e le informazioni contestuali correlate agli errori, eseguire una query su queste viste.  
  
-   [catalog.executions &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
  
-   [catalog.operations &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
  
-   [catalog.operation_messages &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
  
-   [catalog.extended_operation_info &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
  
-   [catalog.event_messages](../../integration-services/system-views/catalog-event-messages.md)  
  
-   [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
 È possibile convalidare i progetti e i pacchetti chiamando le stored procedure [catalog.validate_project &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md) e [catalog.validate_package &#40;Database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md). La vista [catalog.validations &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-validations-ssisdb-database.md) fornisce dettagli sulle convalide, ad esempio i riferimenti all'ambiente server considerati nella convalida, se si tratta di una convalida della dipendenza o di una convalida completa e se viene usato il runtime a 32 bit o a 64 bit per eseguire il pacchetto.  
  
##  <a name="a-namealwaysona-alwayson-support"></a><a name="AlwaysOn"></a> Supporto di AlwaysOn  
 La funzionalità Gruppi di disponibilità AlwaysOn è una soluzione per la disponibilità elevata e il ripristino di emergenza che offre un'alternativa di livello enterprise al mirroring del database. Un gruppo di disponibilità supporta un ambiente di failover per un set discreto di database utente, noti come database di disponibilità, su cui viene effettuato il failover. Per altre informazioni, vedere [Gruppi di disponibilità AlwaysOn](https://msdn.microsoft.com/library/hh510230.aspx).  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], SQL Server Integration Services (SSIS) introduce nuove funzionalità che consentono di distribuire facilmente a un catalogo SSIS centralizzato (ad esempio, il database utente SSISDB). Per garantire una disponibilità elevata del database SSISDB e del relativo contenuto (progetti, pacchetti, log di esecuzione e così via), è possibile aggiungere il database SSISDB a un gruppo di disponibilità AlwaysOn con le stesse modalità usate per gli altri database utente. Quando si verifica un failover, uno dei nodi secondari diventa automaticamente il nuovo nodo primario.  
  
 Per una panoramica e istruzioni dettagliate sull'abilitazione di AlwaysOn per SSISDB, vedere [Catalogo SSIS per AlwaysOn &#40;SSISDB&#41;](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md).  
  
##  <a name="a-namerelatedtasksa-related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare il catalogo SSIS](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [Backup, ripristino e spostamento del catalogo SSIS](../../integration-services/service/backup-restore-and-move-the-ssis-catalog.md)  
  
##  <a name="a-namerelatedcontenta-related-content"></a><a name="RelatedContent"></a> Contenuto correlato  
  
-   Intervento nel blog su [SSIS e PowerShell in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539)sul sito Web blogs.msdn.com.  
  
-   Intervento nel blog sui [suggerimenti per il controllo dell'accesso al catalogo SSIS](http://go.microsoft.com/fwlink/?LinkId=246669)sul sito Web blogs.msdn.com.  
  
-   Intervento nel blog relativo a [uno sguardo rapido del modello a oggetti gestito del catalogo SSIS](http://go.microsoft.com/fwlink/?LinkId=254267)su blogs.msdn.com.  
  
  