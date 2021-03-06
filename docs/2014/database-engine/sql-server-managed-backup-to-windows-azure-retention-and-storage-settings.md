---
title: In Windows Azure - impostazioni di archiviazione e conservazione dei Backup gestito di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b1087efba30ef65a3b4f7e00ed82031e7318b6d
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100382"
---
# <a name="sql-server-managed-backup-to-windows-azure---retention-and-storage-settings"></a>Backup gestito di SQL Server in Windows Azure - Impostazioni di archiviazione e di memorizzazione
  In questo argomento vengono descritti i passaggi di base per configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database e per configurare le impostazioni predefinite per l'istanza. Vengono inoltre descritti i passaggi necessari per sospendere e riprendere i servizi [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per l'istanza.  
  
 Per una procedura dettagliata completa della configurazione di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] visualizzare [configurazione di SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) e [configurazione di SQL Server Managed Backup to Windows Azure per i gruppi di disponibilità](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Non abilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nei database in cui sono attualmente in uso piani di manutenzione o il log shipping. Per altre informazioni sulla interoperabilità e coesistenza con altre funzionalità di SQL Server, vedere [SQL Server Managed Backup to Windows Azure: interoperabilità e coesistenza](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   SQL Server Agent deve essere in esecuzione.  
  
    > [!WARNING]  
    >  Se SQL Server Agent viene arrestato per un periodo di tempo e poi riavviato, è possibile che venga visualizzata una maggiore attività di backup a seconda della quantità di tempo trascorso tra l'arresto e l'avvio di SQL Agent e che sia in attesa di esecuzione un backlog di backup del log. Provare a configurare SQL Server Agent in modo tale che all'avvio venga avviato automaticamente.  
  
-   Prima di configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]è consigliabile creare sia un account di archiviazione Windows Azure, sia le credenziali SQL tramite cui vengono archiviate le informazioni di autenticazione nell'account di archiviazione. Per altre informazioni, vedere la sezione [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) dell'argomento **Backup di SQL Server nell'URL** e [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
    > [!IMPORTANT]  
    >  Tramite [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] vengono creati i contenitori necessari per archiviare i backup. Il nome del contenitore viene creato utilizzando il formato "nome computer-nome istanza". Nel caso dei gruppi di disponibilità AlwaysOn, il contenitore viene denominato utilizzando il GUID del gruppo di disponibilità.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per eseguire la stored procedure che consentono [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], è necessario essere un un `System Administrator` o un membro il **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** eautorizzazioni`EXECUTE` le autorizzazioni per il **sp_delete_backuphistory**, e `smart_admin.sp_backup_master_switch` stored procedure.  Per le stored procedure e le funzioni utilizzate per esaminare le impostazioni esistenti sono in genere richieste rispettivamente le autorizzazioni `Execute` per la stored procedure e `Select` per la funzione.  
  

  
###  <a name="Considerations"></a> Considerazioni per abilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per i database e istanze  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] può essere abilitato separatamente per singoli database o per l'intera istanza. Le scelte dipendono dai requisiti di recuperabilità per i database nell'istanza, dai requisiti per la gestione di più database e istanze e dall'utilizzo del servizio di archiviazione Windows Azure in modo strategico.  
  
#### <a name="enabling-includesssmartbackupincludesss-smartbackup-mdmd-at-the-database-level"></a>Abilitazione di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di database  
 Se un database presenta requisiti specifici per il backup e il periodo di memorizzazione (SLA di recuperabilità) diversi da altri database nell'istanza, configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di database per il database in questione. Le impostazioni a livello di database hanno la priorità sulle impostazioni di configurazione a livello di istanza. Tuttavia entrambe queste opzioni possono essere utilizzate insieme nella stessa istanza. Di seguito è riportato un elenco dei vantaggi e delle considerazioni in caso di abilitazione di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di database.  
  
-   Più dettagliato: impostazioni di configurazione diverse per ogni database. Può supportare periodi di memorizzazione diversi per i singoli database.  
  
-   Vengono ignorate le impostazioni a livello di istanza per il database.  
  
-   Può essere utilizzato per ridurre i costi di archiviazione selezionando i singoli database di cui eseguire il backup.  
  
-   Richiede la gestione di ogni database.  
  
#### <a name="enabling-includesssmartbackupincludesss-smartbackup-mdmd-at-the-instance-level-with-default-settings"></a>Abilitazione di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di istanza con le impostazioni predefinite  
 Utilizzare questa impostazione se la maggior parte dei database nell'istanza presenta gli stessi requisiti per il backup e i criteri di conservazione o se si desidera l'esecuzione automatica del backup delle nuove istanze di database durante la creazione. Alcuni database che fanno eccezione ai criteri possono comunque essere configurati singolarmente. Di seguito è riportato un elenco dei vantaggi e delle considerazioni in caso di abilitazione di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di istanza.  
  
-   Automazione a livello di istanza: impostazioni comuni applicate automaticamente ai nuovi database aggiunti in seguito.  
  
-   Il backup dei nuovi database verrà eseguito automaticamente subito dopo la creazione di questi ultimi nelle istanze.  
  
-   Può essere applicato ai database che presentano gli stessi requisiti del periodo di memorizzazione.  
  
-   È comunque possibile configurare singoli database per cui è richiesto un periodo di memorizzazione diverso anche con il backup di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] abilitato a livello di istanza con le impostazioni predefinite. È inoltre possibile disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per i database se non si desidera utilizzare il servizio di archiviazione Windows Azure per i backup.  
  
##  <a name="DatabaseConfigure"></a> Abilitare e configurare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un Database  
 La stored procedure di sistema `smart_admin.sp_set_db_backup` viene utilizzata per abilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database specifico. Quando [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] viene abilitato per la prima volta nel database, è necessario specificare le informazioni seguenti oltre ad abilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:  
  
-   Nome del database.  
  
-   Periodo di memorizzazione.  
  
-   Credenziali SQL utilizzate per autenticare l'account di archiviazione Windows Azure.  
  
-   Specificare di non eseguire operazioni di crittografia usando *@encryption_algorithm*  =  **NO_ENCRYPTION** oppure specificare un algoritmo di crittografia supportati. Per ulteriori informazioni sulla crittografia, vedere [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per la configurazione a livello di database è supportato solo tramite Transact-SQL.  
  
 Una volta abilitato [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database, queste informazioni sono persistenti. Se si modifica la configurazione, saranno necessari solo il nome del database e l'impostazione da modificare. Se non specificati, in [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verranno utilizzati i valori esistenti per gli altri parametri.  
  
> [!IMPORTANT]  
>  Prima di configurarlo in un database, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] potrebbe essere utile nella configurazione esistente, se disponibile. Il passaggio per verificare le impostazioni di configurazione per un database è illustrato più avanti in questa sezione.  
  
-   **Utilizzo di Transact-SQL:**  
  
     Se si sta abilitando [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per la prima volta, i parametri obbligatori sono: *@database_name*, *@credential_name*, *@encryption_algorithm*, *@enable_backup* Il *@storage_url* parametro è facoltativo. Se non si specifica un valore per il @storage_url parametro, il valore viene ottenuto utilizzando le informazioni sull'account di archiviazione delle credenziali SQL. Se si specifica l'URL di archiviazione, fornire solo l'URL per la radice dell'account di archiviazione, che deve corrispondere alle informazioni specificate nelle credenziali SQL.  
  
    1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
    2.  Dalla barra Standard fare clic su **Nuova query**.  
  
    3.  Copiare e incollare l'esempio seguente nella finestra di query e fare clic su `Execute`. In questo esempio viene abilitato [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per il database "TestDB". Il periodo di memorizzazione è impostato su 30 giorni. In questo esempio vengono utilizzate l'opzione di crittografia tramite cui viene specificato l'algoritmo di crittografia e le informazioni sul componente di crittografia.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO  
  
    ```  
  
    > [!IMPORTANT]  
    >  Il periodo di memorizzazione può essere impostato su un valore compreso tra 1 e 30 giorni.  
    >   
    >  Per ulteriori informazioni sulla creazione di un certificato per la crittografia, vedere il passaggio Creare un certificato di backup in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
     Per altre informazioni su questa stored procedure, vedere [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)  
  
     Per verificare le impostazioni di configurazione per un database, utilizzare la query seguente:  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="InstanceConfigure"></a> Abilitare e configurare predefinito [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] impostazioni per l'istanza  
 È possibile abilitare e configurare l'impostazione predefinita [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] le impostazioni a livello di istanza in due modi: tramite il sistema stored procedure `smart_backup.set_instance_backup` oppure **SQL Server Management Studio**. I due metodi sono illustrati di seguito:  
  
 **smart_backup.set_instance_backup:**. Specificando il valore **1** per *@enable_backup* parametro, è possibile abilitare il backup e impostare le configurazioni predefinite. Una volta applicate a livello di istanza, queste impostazioni predefinite sono valide per qualsiasi nuovo database aggiunto a questa istanza.  Quando [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] viene abilitato per la prima volta, è necessario specificare le informazioni seguenti oltre ad abilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nell'istanza:  
  
-   Periodo di memorizzazione.  
  
-   Credenziali SQL utilizzate per autenticare l'account di archiviazione Windows Azure.  
  
-   Opzione di crittografia. Specificare di non eseguire operazioni di crittografia usando *@encryption_algorithm*  =  **NO_ENCRYPTION** oppure specificare un algoritmo di crittografia supportati. Per ulteriori informazioni sulla crittografia, vedere [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 Una volta abilitate, queste impostazioni sono persistenti. Se si modifica la configurazione, saranno necessari solo il nome del database e l'impostazione da modificare. Se non specificati, in [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verranno utilizzati i valori esistenti.  
  
> [!IMPORTANT]  
>  Prima di configurarlo in un'istanza, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] potrebbe essere utile per verificare la configurazione esistente, se disponibile. Il passaggio per verificare le impostazioni di configurazione per un database è illustrato più avanti in questa sezione.  
  
 **SQL Server Management Studio:** per eseguire questa attività in SQL Server Management Studio, aprire Esplora oggetti, espandere il nodo **Gestione** , fare clic con il pulsante destro del mouse su **Backup gestito**. Selezionare **Configura**. Viene aperta la finestra di dialogo **Backup gestito** . Utilizzare questa finestra di dialogo per specificare il periodo di memorizzazione, le credenziali SQL, l'URL di archiviazione e le impostazioni di crittografia. Per informazioni specifiche su questa finestra di dialogo, vedere [configurare il Backup gestito di &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).  
  
#### <a name="using-transact-sql"></a>Utilizzo di Transact-SQL  
  
1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra di query e fare clic su `Execute`.  
  
```  
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  Il periodo di memorizzazione può essere impostato su un valore compreso tra 1 e 30 giorni.  
>   
>  Per ulteriori informazioni sulla creazione di un certificato per la crittografia, vedere il passaggio Creare un certificato di backup in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
 Per visualizzare le impostazioni di configurazione predefinite per l'istanza, utilizzare la query seguente:  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
```  
  
#### <a name="using-powershell"></a>Utilizzo di PowerShell  
  
1.  Avviare un'istanza di PowerShell  
  
2.  Eseguire lo script riportato di seguito dopo averlo modificato per rispettare le impostazioni  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin –BackupEnabled $True –BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  Quando si crea un nuovo database dopo la configurazione delle impostazioni predefinite, potrebbero essere necessari fino a 15 minuti per configurarlo con le impostazioni in questione. Lo stesso vale anche per i database il cui modello di recupero viene modificato da **Simple** a **Full** o **Bulk-Logged**  
  
##  <a name="DatabaseDisable"></a> Disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database  
 È possibile disabilitare le impostazioni di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilizzando la stored procedure di sistema `sp_set_db_backup`. Il *@enableparameter* consente di abilitare e disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurazioni per un database specifico, dove 1 abilita e 0 disabilita le impostazioni di configurazione.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmd-for-a-specific-database"></a>Per disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un database specifico:  
  
1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra di query e fare clic su `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO  
  
```  
  
##  <a name="DatabaseAllDisable"></a> Disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per tutti i database dell'istanza  
 La procedura seguente viene utilizzata quando si desidera disabilitare le impostazioni di configurazione di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] da tutti i database con [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] abilitato attualmente nell'istanza.  Le impostazioni di configurazione come l'URL di archiviazione, la memorizzazione e le credenziali SQL rimarranno nei metadati e possono essere utilizzate se [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] viene abilitato per il database in un secondo momento. Se si desidera sospendere solo temporaneamente i servizi [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , è possibile utilizzare il parametro master descritto nelle sezioni seguenti, più avanti in questo argomento.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmdfor-all-the-databases"></a>Per disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]per tutti i database:  
  
1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra di query e fare clic su `Execute`. Nell'esempio seguente viene identificato se [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] è configurato a livello di istanza e in tutti i database abilitati da [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nell'istanza e viene eseguita la stored procedure di sistema `sp_set_db_backup` per disabilitare [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
```  
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM   
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames  
  
       select @rowid = min(RowID)  
       FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin  
  
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END  
  
```  
  
 Per verificare le impostazioni di configurazione per tutti i database nell'istanza, utilizzare la query seguente:  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO  
  
```  
  
##  <a name="InstanceDisable"></a> Disabilitare le impostazioni predefinite di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per l'istanza  
 Le impostazioni predefinite a livello di istanza vengono applicate a tutti i nuovi database creati nell'istanza in questione.  Se le impostazioni predefinite non sono più necessarie o richieste, è possibile disabilitare questa configurazione usando la stored procedure di sistema **smart_admin.sp_set_instance_backup** . La disabilitazione non comporta la rimozione delle altre impostazioni di configurazione come l'URL di archiviazione, l'impostazione di memorizzazione o il nome delle credenziali SQL. Queste impostazioni verranno utilizzate se [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] viene abilitato per l'istanza in un secondo momento.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmd-default-configuration-settings"></a>Per disabilitare le impostazioni di configurazione predefinite di [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] :  
  
1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra di query e fare clic su `Execute`.  
  
    ```  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO  
  
    ```  
  
#### <a name="using-powershell"></a>Utilizzo di PowerShell  
  
1.  Avviare un'istanza di PowerShell  
  
2.  Eseguire lo script riportato di seguito:  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Set-SqlSmartAdmin –BackupEnabled $False  
    ```  
  
##  <a name="InstancePause"></a> Sospendere [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di istanza  
 In alcuni casi è possibile che sia necessario sospendere temporaneamente i servizi [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] per un breve periodo.  La stored procedure di sistema `smart_admin.sp_backup_master_switch` consente di disabilitare il servizio [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] a livello di istanza.  La stessa stored procedure viene utilizzata per riprendere [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Il parametro @state viene usato per definire se [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] deve essere disabilitato o abilitato.  
  
#### <a name="to-pause-includesssmartbackupincludesss-smartbackup-mdmd-services-using-transact-sql"></a>Per sospendere i servizi [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tramite Transact-SQL:  
  
1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra di query e quindi fare clic su `Execute`  
  
```  
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-includesssmartbackupincludesss-smartbackup-mdmd-using-powershell"></a>Per sospendere [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tramite PowerShell  
  
1.  Avviare un'istanza di PowerShell  
  
2.  Eseguire lo script riportato di seguito dopo averlo modificato per rispettare le impostazioni  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin –MasterSwitch $False  
    ```  
  
#### <a name="to-resume-includesssmartbackupincludesss-smartbackup-mdmd-using-transact-sql"></a>Per riprendere [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tramite Transact-SQL  
  
1.  Connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra di query e quindi fare clic su `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO  
  
```  
  
#### <a name="to-resume-includesssmartbackupincludesss-smartbackup-mdmd-using-powershell"></a>Per riprendere [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tramite PowerShell  
  
1.  Avviare un'istanza di PowerShell  
  
2.  Eseguire lo script riportato di seguito dopo averlo modificato per rispettare le impostazioni  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin –MasterSwitch $True  
    ```  
  
  
