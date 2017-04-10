---
title: "Transparent Data Encryption con il database SQL di Azure | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
  - "MSDN content"
  - "MSDN - SQL DB"
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-database"
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TDE, database SQL"
  - "crittografia (database SQL), TDE"
  - "Transparent Data Encryption, database SQL"
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Transparent Data Encryption con il database SQL di Azure
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx_md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] Transparent Data Encryption contribuisce alla protezione dalle minacce di attività dannose eseguendo la crittografia e la decrittografia in tempo reale del database, dei backup associati e dei file di log delle transazioni inattivi senza richiedere modifiche all'applicazione.  
  
 Transparent Data Encryption crittografa l'archivio di un intero database utilizzando una chiave simmetrica denominata chiave di crittografia del database. Nel [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] la chiave di crittografia del database è protetta con un certificato server predefinito. Il certificato server predefinito è univoco per ogni server del [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]. Se un database fa parte di una relazione GeoDR, è protetto da una chiave diversa in ogni server. Se due database sono connessi allo stesso server, condividono lo stesso certificato predefinito. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ruota automaticamente questi certificati almeno ogni 90 giorni. Per una descrizione generale di TDE, vedere [Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md).  
  
 [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] non supporta l'integrazione dell'insieme di credenziali delle chiavi di Azure con TDE. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in esecuzione in una macchina virtuale di Azure può usare una chiave asimmetrica dall'insieme di credenziali delle chiavi. Per altre informazioni, vedere [Extensible Key Management tramite l'insieme di credenziali delle chiavi di Azure &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
##  <a name="Permissions"></a> Autorizzazioni  
 Per configurare TDE con il portale di Azure usando l'API REST o PowerShell, è necessario essere connessi come proprietario, collaboratore o Gestore Sicurezza SQL di Azure.  
  
 Per configurare Transparent Data Encryption tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)] è necessario soddisfare le condizioni seguenti:  
  
-   Per eseguire l'istruzione ALTER DATABASE con l'opzione SET, è richiesta l'appartenenza al ruolo **dbmanager** .  
  
##  <a name="Preview"></a> Abilitare TDE in un database con il portale  
  
1.  Visitare il portale di Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com) e accedere con l'account amministratore o collaboratore di Azure.  
  
2.  Nel banner sinistro fare clic su **SFOGLIA**e quindi su **Database SQL**.  
  
3.  Con la voce **Database SQL** selezionata nel riquadro sinistro fare clic sul proprio database utente.  
  
4.  Nel pannello del database fare clic su **Tutte le impostazioni**.  
  
5.  Nel pannello **Impostazioni** fare clic su **Transparent Data Encryption** per aprire il pannello **Transparent Data Encryption** .  
  
6.  Nel pannello **Crittografia dati** spostare lo stato attivo del pulsante **Crittografia dati** su **Attivato** e quindi fare clic su **Salva** (in alto nella pagina) per applicare l'impostazione. Il valore di **Stato crittografia** indicherà approssimativamente lo stato di avanzamento di Transparent Data Encryption.  
  
     ![SQL Database TDE Start Encryption](../../../relational-databases/security/encryption/media/sqldb-tde-encrypt.png "SQL Database TDE Start Encryption")  
  
     È anche possibile monitorare lo stato di avanzamento della crittografia connettendosi al [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] con uno strumento di query quale [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] come utente del database con l'autorizzazione di **VISUALIZZAZIONE STATO DEL DATABASE** . Eseguire una query sulla colonna **encryption_state** della vista [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).  
  
##  <a name="Encrypt"></a> Abilitazione di TDE nel [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] tramite Transact-SQL  
 La procedura seguente consente di abilitare TDE.  
  
###  <a name="TsqlProcedure"></a>  
  
1.  Connettersi al database con un account di accesso come amministratore o membro del ruolo **dbmanager** nel database master.  
  
2.  Eseguire le istruzioni seguenti per crittografare il database.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  Per monitorare lo stato della crittografia nel [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], gli utenti del database con l'autorizzazione **VIEW DATABASE STATE** possono eseguire una query sulla colonna **encryption_state** della vista [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).  
  
##  <a name="EncryptPS"></a> Abilitazione e disabilitazione di TDE in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] con PowerShell  
 Con Azure PowerShell è possibile eseguire il comando seguente per attivare o disattivare TDE. Prima di eseguire il comando, è necessario connettere l'account alla finestra di PowerShell. Personalizzare l'esempio per usare i propri valori per i parametri `ServerName`, `ResourceGroupName`e `DatabaseName` . Per altre informazioni su PowerShell, vedere [Come installare e configurare Azure PowerShell](http://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!NOTE]  
>  Per continuare, è necessario installare e configurare la versione 1.0 di Azure PowerShell. È possibile usare la versione 0.9.8, che però è stata deprecata e richiede il passaggio ai cmdlet di AzureResourceManager con il comando `PS C:\> Switch-AzureMode -Name AzureResourceManager` .  
  
###  <a name="PSlProcedure"></a>  
  
1.  Per abilitare TDE, tornare al relativo stato e visualizzare l'attività di crittografia:  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
    ```  
  
     Se si usa la versione 0.9.8 usare i comandi Set-AzureSqlDatabaseTransparentDataEncryption, Get-AzureSqlDatabaseTransparentDataEncryption e Get-AzureSqlDatabaseTransparentDataEncryptionActivity.  
  
2.  Per disabilitare TDE:  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    ```  
  
     Se si usa la versione 0.9.8 usare il comando Set-AzureSqlDatabaseTransparentDataEncryption.  
  
##  <a name="Decrypt"></a> Decrittografia di un database protetto con TDE nel [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
  
#### Per disabilitare TDE tramite il portale di Azure  
  
1.  Visitare il portale di Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com) e accedere con l'account amministratore o collaboratore di Azure.  
  
2.  Nel banner sinistro fare clic su **SFOGLIA**e quindi su **Database SQL**.  
  
3.  Con la voce **Database SQL** selezionata nel riquadro sinistro fare clic sul proprio database utente.  
  
4.  Nel pannello del database fare clic su **Tutte le impostazioni**.  
  
5.  Nel pannello **Impostazioni** fare clic su **Transparent Data Encryption** per aprire il pannello **Transparent Data Encryption** .  
  
6.  Nel pannello **Transparent Data Encryption** spostare lo stato attivo del pulsante **Crittografia dati** su **Attivato** e quindi fare clic su **Salva** (in alto nella pagina) per applicare l'impostazione. Il valore di **Stato crittografia** indicherà approssimativamente lo stato di avanzamento della decrittografia trasparente dei dati.  
  
     È anche possibile monitorare lo stato di avanzamento della decrittografia connettendosi al [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] con uno strumento di query quale [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] come utente del database con l'autorizzazione di **VISUALIZZAZIONE STATO DEL DATABASE** . Eseguire una query sulla colonna **encryption_state** della vista [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).  
  
#### Per disabilitare TDE tramite Transact-SQL  
  
1.  Connettersi al database con un account di accesso come amministratore o membro del ruolo **dbmanager** nel database master.  
  
2.  Eseguire le istruzioni seguenti per decrittografare il database.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  Per monitorare lo stato della crittografia nel [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], gli utenti del database con l'autorizzazione **VIEW DATABASE STATE** possono eseguire una query sulla colonna **encryption_state** della vista [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).  
  
##  <a name="Working"></a> Spostamento di un database protetto con TDE in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
 Non è necessario decrittografare i database per eseguire operazioni all'interno di Azure. Le impostazioni di Transparent Data Encryption nel database di origine o nel database primario vengono ereditate in modo trasparente nel database di destinazione. Sono incluse le operazioni che prevedono le attività seguenti:  
  
-   Ripristino geografico  
  
-   Ripristino temporizzato self-service  
  
-   Ripristino di un database eliminato  
  
-   Replica a livello geografico attiva  
  
-   Creazione di una copia del database  
  
 Quando si esporta un database protetto con TDE usando la funzione Esporta database nel portale del [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] o con l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il contenuto esportato del database non è crittografato. Questo contenuto esportato viene archiviato nei file con estensione bacpac non crittografati. Assicurarsi di proteggere i file BACPAC nel modo appropriato e abilitare TDE al termine dell'importazione del nuovo database. 
 
 Ad esempio, se il file bacpac viene esportato da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] locale, il contenuto importato del nuovo database non verrà crittografato automaticamente. Analogamente, anche se il file bacpac viene esportato da [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] locale, il nuovo database non verrà crittografato automaticamente.  
 
 L'unica eccezione riguarda l'esportazione verso e da [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)]: TDE viene abilitato nel nuovo database, ma il file bacpac resta non crittografato.
  
## Argomento correlato a SQL Server  
 [Abilitare TDE in SQL Server con EKM](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## Vedere anche  
 [Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql.md)  
  
  