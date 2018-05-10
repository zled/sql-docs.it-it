---
title: Distribuire un database di SQL Server a una macchina virtuale di Microsoft Azure | Microsoft Docs
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.deploymentwizard.deploymentsettings.f1
- sql13.swb.deploymentwizard.sourcesettings.f1
- sql13.swb.deploymentwizard.summary.f1
- sql13.swb.agdashboard.agp9virtualnw.issues.f1
- sql13.swb.deploymentwizard.f1
- sql13.swb.deploymentwizard.progress.f1
- sql13.swb.usevmdialog.f1
- sql13.swb.newvmdialog.f1
- sql13.swb.sqlvmdialog.f1
- sql13.swb.deploymentwizard.results.f1
- sql13.swb.deploymentwizard.azuresignin.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Windows Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3ad29084eda4f085e090ec9f436a5dd3f170429f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a>Distribuire un database di SQL Server a una macchina virtuale di Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Usare la procedura guidata **Distribuisci il database in una macchina virtuale di Microsoft Azure** per distribuire un database da un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale (VM) di Windows Azure. La procedura guidata usa un'operazione di backup completo del database, quindi copia sempre lo schema completo del database e i dati da un database utente SQL Server. La procedura guidata esegue inoltre tutta la configurazione della macchina virtuale di Azure automaticamente, pertanto non sono necessarie operazioni preliminari per la configurazione della VM.  
  
 Non è possibile usare la procedura guidata per i backup differenziali perché non sovrascrive un database esistente avente lo stesso nome di database. Per sostituire un database esistente sulla VM, è innanzitutto necessario eliminare il database esistente o modificare il nome del database. Se si verifica un conflitto di denominazione tra il nome del database per un'operazione di distribuzione in transito e un database esistente sulla VM, la procedura guidata suggerirà un nome di database aggiunto per il database in transito per consentire il completamento dell'operazione.  
  
-   [Prima di iniziare](#before_you_begin)  
  
-   [Limitazioni e restrizioni](#limitations)  
  
-   [Considerazioni per la distribuzione di un database abilitato per FILESTREAM](#filestream)  
  
-   [Considerazioni sulla distribuzione geografica delle risorse](#geography)  
  
-   [Impostazioni di configurazione della procedura guidata](#configuration_settings)  
  
-   [Autorizzazioni necessarie](#permissions)  
  
-   [Avvio della procedura guidata](#launch_wizard)  
  
-   [Pagine della procedura guidata](#wizard_pages)  
  
> [!NOTE]  
>  Per una descrizione dettagliata di questa procedura guidata, vedere [Eseguire la migrazione di un database di SQL Server a SQL Server in una macchina virtuale di Azure](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-migrate-onpremises-database/)  
  
##  <a name="before_you_begin"></a> Prima di iniziare  
 Per completare questa procedura guidata, è necessario essere in grado di fornire le informazioni indicate di seguito e avere configurato le seguenti impostazioni:  
  
-   Dettagli dell'account Microsoft associati alla sottoscrizione di Microsoft Azure.  
  
-   Profilo di pubblicazione di Microsoft Azure.  
  
    > [!CAUTION]  
    >  SQL Server supporta attualmente la versione del profilo di pubblicazione 2.0. Per scaricare la versione supportata del profilo di pubblicazione, vedere [Download del profilo di pubblicazione 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
  
-   Certificato di gestione caricato nella sottoscrizione di Microsoft Azure.  Creare il certificato di gestione con il cmdlet di Powershell [New-SelfSignedCertificate](https://technet.microsoft.com/library/hh848633(v=wps.630)).  Caricarlo quindi nella sottoscrizione di Microsoft Azure.  Per altre informazioni sul caricamento di un certificato di gestione, vedere [Caricare un certificato di gestione dell'API di gestione di Azure](https://azure.microsoft.com/en-us/documentation/articles/azure-api-management-certs/).  Sintassi di esempio per la creazione di un certificato di gestione tratto da [Panoramica sui certificati per i servizi cloud di Azure](https://azure.microsoft.com/en-us/documentation/articles/cloud-services-certs-create/): 

    ```powershell  
    $cert = New-SelfSignedCertificate -DnsName yourdomain.cloudapp.net -CertStoreLocation "cert:\LocalMachine\My"
    $password = ConvertTo-SecureString -String "your-password" -Force -AsPlainText
    Export-PfxCertificate -Cert $cert -FilePath ".\my-cert-file.pfx" -Password $password
    ```    

    > [!NOTE]  
    > Per creare un certificato di gestione, è anche possibile usare lo strumento MakeCert, ora tuttavia deprecato.  Per altre informazioni, vedere [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968).
   
  -   Il certificato di gestione salvato nell'archivio certificati personale sul computer in cui viene eseguita la procedura guidata.  
  
-   È necessario disporre di un percorso di archiviazione temporaneo nel computer in cui è ospitato il database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il percorso di archiviazione temporaneo deve essere disponibile nel computer in cui viene eseguita la procedura guidata.  
  
-   Se si distribuisce il database a un macchina virtuale esistente, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere configurata per rimanere in attesa su una porta TCP/IP.  
  
-   L'immagine di una macchina virtuale di Microsoft Azure o di una raccolta che si intende usare per la creazione della macchina virtuale deve disporre dell' [adattatore del cloud di SQL Server](http://msdn.microsoft.com/library/82ed0d0f-952d-4d49-aa36-3855a3ca9877) configurato e in esecuzione.  
  
-   È necessario configurare un endpoint aperto per un [adattatore del cloud di SQL Server](http://msdn.microsoft.com/library/82ed0d0f-952d-4d49-aa36-3855a3ca9877) nel gateway di Microsoft Azure con porta privata 11435.  
  
 Se inoltre si intende distribuire il database in una macchina virtuale di Microsoft Azure esistente, è necessario essere in grado di fornire anche quanto indicato di seguito:  
  
-   Nome DNS del servizio cloud che ospita la macchina virtuale.  
  
-   Credenziali dell'amministratore per la macchina virtuale.  
  
-   Credenziali con privilegi dell'operatore di backup nel database che si desidera distribuire, dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di origine.  
  
 Per altre informazioni sull'esecuzione di SQL Server in macchine virtuali di Microsoft Azure, vedere [Effettuare il provisioning di una macchina virtuale di SQL Server nel portale di Azure](https://msdn.microsoft.com/library/dn133141.aspx) ed [Eseguire la migrazione di un database di SQL Server in una macchina virtuale di Azure](http://msdn.microsoft.com/library/dn133142.aspx).  
  
 Nei computer che eseguono sistemi operativi Windows Server, è necessario usare le seguenti impostazioni di configurazione per eseguire questa procedura guidata:  
  
-   Disabilitare la configurazione della sicurezza avanzata: usare Server Manager > Server locale per impostare la configurazione della sicurezza avanzata di Internet Explorer (ESC) su **DISATTIVATO**.  
  
-   Abilitare JavaScript: Internet Explorer > Opzioni Internet > Sicurezza > Livello personalizzato > Esecuzione script > Esecuzione script attivo: **Attiva**.  
  
###  <a name="limitations"></a> Limitazioni e restrizioni  
Questa funzionalità di distribuzione è destinata solo agli account di archiviazione di Azure creati tramite il modello di distribuzione di Gestione dei servizi (classica). Per altre informazioni sui modelli di distribuzione di Microsoft Azure, vedere [Confronto tra distribuzione di Azure Resource Manager e classica](https://azure.microsoft.com/en-us/documentation/articles/resource-manager-deployment-model/).

 Il limite per le dimensioni del database per questa operazione è di 1 TB.  
  
 Questa funzionalità di distribuzione è disponibile in SQL Server Management Studio per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Questa funzionalità di distribuzione è destinata solo ai database utente. La distribuzione dei database di sistema non è supportata.  
  
 La funzionalità di distribuzione non supporta i servizi ospitati associati a un gruppo di affinità. Ad esempio, gli account di archiviazione associati a un gruppo di affinità non possono essere selezionati per l'uso nella pagina **Impostazioni di distribuzione** di questa procedura guidata.  
  
 Versioni del database di SQL Server che è possibile distribuire in una macchina virtuale di Microsoft Azure tramite questa procedura guidata:  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  

- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Versioni del database SQL Server in esecuzione in un database di Macchine virtuali di Microsoft Azure può essere distribuito in:  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  

- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Se si verifica un conflitto di denominazione tra il nome del database per un'operazione di distribuzione in transito e un database esistente sulla VM, la procedura guidata suggerirà un nome di database aggiunto per il database in transito per consentire il completamento dell'operazione.  
  
###  <a name="filestream"></a> Considerazioni per la distribuzione di un database abilitato per FILESTREAM in una macchina virtuale di Azure  
 Tenere presenti le linee guida e le limitazioni seguenti per la distribuzione di database con BLOB archiviati in oggetti FILESTREAM:  
  
-   La funzionalità di distribuzione non permette di distribuire un database abilitato per FILESTREAM in una nuova macchina virtuale. Se FILESTREAM non è abilitato nella macchina virtuale prima di eseguire la procedura guidata, l'operazione di ripristino del database avrà esito negativo e l'operazione della procedura guidata non sarà completata correttamente. Per distribuire correttamente un database che usa FILESTREAM, abilitare FILESTREAM nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nella macchina virtuale host prima di avviare la procedura guidata. Per altre informazioni, vedere [FILESTREAM (SQL Server)](http://msdn.microsoft.com/library/gg471497.aspx).  
  
-   Se il database usa OLTP in memoria, è possibile distribuirlo in una macchina virtuale di Azure senza apportare alcuna modifica al database. Per altre informazioni, vedere [OLTP in memoria (ottimizzazione per la memoria)](http://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).  
  
###  <a name="geography"></a> Considerazioni sulla distribuzione geografica delle risorse  
 Si noti che le risorse seguenti devono essere collocate nella stessa area geografica:  
  
-   Servizio cloud  
  
-   Ubicazione della macchina virtuale  
  
-   Servizio di archiviazione su disco di dati  
  
 Se le risorse elencate sopra non si trovano nella stessa area geografica, non sarà possibile completare correttamente la procedura guidata.  
  
###  <a name="configuration_settings"></a> Impostazioni di configurazione della procedura guidata  
 Usare i dettagli di configurazione seguenti per modificare le impostazioni per una distribuzione del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale di Azure.  
  
-   **Percorso predefinito per il file di configurazione** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml  
  
-   **Struttura dei file di configurazione**  
  
    -   \<DeploymentSettings>  
  
        -   \<OtherSettings  
  
            -   TraceLevel="Debug" \<!-- Livello di registrazione -->  
  
            -   BackupPath="\\\\[nome server]\\[volume]\\" \<!-- Ultimo percorso usato per il backup. Usato come impostazione predefinita nella procedura guidata. -->  
  
            -   CleanupDisabled = False /> \<! -- La procedura guidata non elimina i file intermedi e gli oggetti di Windows Azure (VM, CS, SA). -->  
  
        -   \<PublishProfile \<!-- Informazioni sull'ultimo profilo di pubblicazione usato. -->  
  
            -   Certificate="12A34B567890123ABCD4EF567A8" \<!-- Il certificato da usare nella procedura guidata. -->  
  
            -   Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- La sottoscrizione da usare nella procedura guidata. -->  
  
            -   Name="My Subscription" \<!-- Nome della sottoscrizione. -->  
  
            -   Publisher="" />  
  
    -   \</DeploymentSettings>  
  
 **Valori del file di configurazione**  
  
###  <a name="permissions"></a> Autorizzazioni  
 Il database distribuito deve essere in uno stato normale e accessibile per l'account utente che esegue la procedura guidata. L'account utente deve disporre delle autorizzazioni per eseguire un'operazione di backup.  
  
##  <a name="launch_wizard"></a> Uso della procedura guidata Distribuisci il database in una macchina virtuale di Microsoft Azure  
 **Per avviare la procedura guidata, effettuare i passaggi seguenti:**  
  
1.  Usare SQL Server Management Studio per connettere l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al database che si desidera distribuire.  
  
2.  In **Esplora oggetti**espandere il nome dell'istanza, quindi il nodo **Database** .  
  
3.  Fare clic con il pulsante destro del mouse sul database da distribuire, scegliere **Attività**, quindi **Distribuisci il database in una macchina virtuale di Microsoft Azure**  
  
##  <a name="wizard_pages"></a> Pagine della procedura guidata  
 Nelle sezioni seguenti sono fornite altre informazioni sulle impostazioni di distribuzione e sui dettagli di configurazione per questa operazione.  
  
-   [Introduzione](#Introduction)  
  
-   [Impostazioni di origine](#Source_settings)  
  
-   [Accesso di Microsoft Azure](#Azure_sign-in)  
  
-   [Impostazioni di distribuzione](#Deployment_settings)  
  
-   [Riepilogo](#Summary)  
  
-   [Risultati](#Results)  
  
##  <a name="Introduction"></a> Introduzione 
 Questa pagina descrive la procedura guidata **Distribuisci il database in una macchina virtuale di Microsoft Azure** .  
  
-   **Non visualizzare più questa pagina**  
  Selezionare la casella di controllo per evitare che la pagina Introduzione sia visualizzata nuovamente in futuro.  
  
-   **Avanti**  
Passa alla pagina **Impostazioni di origine** .  
  
-   **Annulla**  
  Annulla l'operazione e chiude la procedura guidata.  
  
-   **?**  
Avvia l'argomento della Guida di MSDN per la procedura guidata.  
  
##  <a name="Source_settings"></a> Impostazioni di origine  
 Usare questa pagina per connettere l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database da distribuire alla macchina virtuale di Microsoft Azure. È anche necessario specificare un percorso temporaneo per il salvataggio dei file dal computer locale prima di essere trasferiti a Microsoft Azure. Può essere un percorso di rete condiviso.  
 
- **SQL Server**    
Fare clic su **Connetti** e specificare i dettagli di connessione per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database da distribuire.  
  
-   **Selezione database**  
Usare l'elenco a discesa per specificare il database da distribuire.  
  
-   **Altre impostazioni**  
Nel campo specificare una cartella condivisa accessibile al servizio Macchina virtuale di Microsoft Azure.  
  
##  <a name="Azure_sign-in"></a> Accesso di Microsoft Azure  
 Accedere a Microsoft Azure con il proprio account Microsoft o aziendale. L'account Microsoft o aziendale è nel formato di un indirizzo di posta elettronica, ad esempio patc@contoso.com. Per altre informazioni sulle credenziali di Azure, vedere l’articolo relativo alle [Domande frequenti sull'account Microsoft per le organizzazioni](http://technet.microsoft.com/jj592903) e alla [risoluzione dei problemi](https://technet.microsoft.com/dn197220).  
  
##  <a name="Deployment_settings"></a> Impostazioni di distribuzione
 Usare questa pagina per specificare il server di destinazione e fornire i dettagli sul nuovo database.  
  
 **Macchina virtuale di Microsoft Azure**  
  
-   **Nome servizio cloud**  
Specificare il nome del servizio che ospita la macchina virtuale. Per creare un nuovo servizio cloud, specificare un nome per il nuovo servizio cloud.  
  
-   **Nome macchina virtuale** Specificare il nome della macchina virtuale che ospiterà il database di SQL Server. Per creare una nuova macchina virtuale di Microsoft Azure, specificare un nome per la nuova macchina virtuale.  
  
-   **Account di archiviazione**  
Selezionare l'account di archiviazione dall'elenco a discesa. Per creare un nuovo account di archiviazione, specificare un nome per il nuovo account. Si noti che gli account di archiviazione associati a un gruppo di affinità non saranno disponibili nell'elenco a discesa.  

-   **Impostazioni**  
Usare questo pulsante per creare una nuova macchina virtuale per ospitare il database di SQL Server. Se si usa una macchina virtuale esistente, le informazioni immesse saranno usate per autenticare le credenziali.  
  
**Database di destinazione**
  
-   **Nome istanza SQL**  
Dettagli della connessione per il server.  
  
-   **Nome database**  
Specificare o confermare il nome di un nuovo database. Se il nome del database esiste già nell'istanza di destinazione di SQL Server, specificare un nome di database modificato.  
  
##  <a name="Summary"></a> Riepilogo
 Usare questa pagina per esaminare le impostazioni specificate per l'operazione. Per completare l'operazione di distribuzione usando le impostazioni specificate, fare clic su **Fine**. Per annullare l'operazione di distribuzione e chiudere la procedura guidata, fare clic su **Annulla**.  Facendo clic su **Fine** verrà avviata la pagina **Stato distribuzione** .  È inoltre possibile visualizzare lo stato di avanzamento dal file di log in `"%LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM"`.
  
 Potrebbe essere richiesta l'esecuzione di passaggi manuali per distribuire i dettagli del database al database di SQL Server nella macchina virtuale di Microsoft Azure. Tali passaggi saranno descritti in dettaglio automaticamente.  
  
##  <a name="Results"></a> Risultati 
 In questa pagina è riportato l'esito positivo o negativo dell'operazione di distribuzione, indicante i risultati di ogni azione. Per ogni azione per la quale è stato rilevato un errore sarà presente un'indicazione nella colonna **Risultato** . Fare clic sul collegamento per visualizzare un report dell'errore relativo all'azione.  
  
 Fare clic su **Fine** per chiudere la procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [adattatore del cloud di SQL Server](http://msdn.microsoft.com/library/82ed0d0f-952d-4d49-aa36-3855a3ca9877)   
 [Gestione del ciclo di vita del database](../../relational-databases/database-lifecycle-management.md)   
 [Esportazione di un'applicazione livello dati](../../relational-databases/data-tier-applications/export-a-data-tier-application.md)   
 [Importare un file BACPAC per creare un nuovo database utente](../../relational-databases/data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)   
 [Backup e ripristino del database SQL di Azure.](https://msdn.microsoft.com/library/azure/jj650016.aspx)   
 [Distribuzione di SQL Server in Macchine virtuali di Microsoft Azure](http://msdn.microsoft.com/library/dn133141.aspx)   
 [Preparazione della migrazione a SQL Server in Macchine virtuali di Microsoft Azure](http://msdn.microsoft.com/library/dn133142.aspx)  
  
  
