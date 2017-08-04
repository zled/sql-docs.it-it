---
title: Abilitare Estensione database per un database | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, enabling database
- enabling database for Stretch Database
ms.assetid: 37854256-8c99-4566-a552-432e3ea7c6da
caps.latest.revision: 70
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 189aef1d316d4e8569a48a413ec72cfbc6a6673c
ms.contentlocale: it-it
ms.lasthandoff: 07/29/2017

---
# <a name="enable-stretch-database-for-a-database"></a>Enable Stretch Database for a database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per configurare un database esistente per Estensione database, selezionare **Attività | Estensione | Abilita** per un database in SQL Server Management Studio in modo da aprire la procedura guidata **Abilitare il database per l'estensione**. È anche possibile usare Transact-SQL per abilitare Estensione database in un database.  
  
 Se si seleziona **Attività | Estensione | Abilita** per una tabella e il database non è ancora abilitato per Estensione database, la procedura guidata consente di configurare il database per Estensione database e di configurare le tabelle come parte del processo. Seguire la procedura in questo argomento anziché i passaggi descritti in [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 L'abilitazione di Estensione database su un database o una tabella richiede autorizzazioni db_owner. L'abilitazione di Estensione database su un database richiede anche le autorizzazioni CONTROL DATABASE.  

 >   [!NOTE]
 > Se successivamente si disabilita Estensione database, tenere presente che questa operazione per una tabella o per un database non elimina l'oggetto remoto. Se si vuole eliminare la tabella remota o il database remoto, è necessario eliminarlo tramite il portale di gestione di Azure. Gli oggetti remoti continuano a generare costi di Azure fino a quando non vengono eliminati manualmente. 
 
## <a name="before-you-get-started"></a>Prima di iniziare  
  
-   Prima di configurare un database per Estensione, è consigliabile eseguire Stretch Database Advisor per identificare i database e le tabelle idonee per Estensione. Stretch Database Advisor identifica anche i problemi di blocco. Per altre informazioni, vedere [Identificare i database e le tabelle per Estensione database eseguendo Stretch Database Advisor](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md).  
  
-   Rivedere [Limitazioni della superficie di attacco e problemi che causano il blocco per Estensione database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
-   Estensione database esegue la migrazione dei dati in Azure. È quindi necessario avere un account Azure e una sottoscrizione per la fatturazione. Per creare un account Azure, [fare clic qui](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
-   Recuperare le informazioni sulla connessione e sull'account di accesso necessarie per creare un nuovo server di Azure o selezionare un server di Azure esistente.  
  
##  <a name="EnableTSQLServer"></a> Prerequisito: abilitare Estensione database nel server  
 Prima di abilitare Estensione database su un database o una tabella, è necessario abilitarla nel server locale. Questa operazione richiede le autorizzazioni sysadmin o serveradmin.  
  
-   Se si dispone delle autorizzazioni amministrative necessarie, la procedura guidata **Abilitare il database per l'estensione** configura il server per Estensione.  
  
-   Se non si dispone delle autorizzazioni necessarie, l'amministratore deve abilitare l'opzione manualmente eseguendo **sp_configure** prima che venga avviata la procedura guidata o deve eseguire la procedura guidata.  
  
 Per abilitare manualmente Estensione database nel server, eseguire **sp_configure** e attivare l'opzione **remote data archive** . L'esempio seguente abilita l'opzione **remote data archive** impostandone il valore su 1.  
  
```  
EXEC sp_configure 'remote data archive' , '1';  
GO

RECONFIGURE;  
GO  
```  
  
 Per altre informazioni, vedere [Configure the remote data archive Server Configuration Option](../../database-engine/configure-windows/configure-the-remote-data-archive-server-configuration-option.md) (Configurare l'opzione di configurazione remote data archive) e [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
##  <a name="Wizard"></a> Usare la procedura guidata per abilitare Estensione database in un database  
 Per informazioni sulla procedura guidata Abilitare il database per l'estensione e sulle informazioni da immettere e le scelte da compiere, vedere [Get started by running the Enable Database for Stretch Wizard](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md)(Iniziare eseguendo la procedura guidata Abilitare il database per l'estensione).  
  
##  <a name="EnableTSQLDatabase"></a> Usare Transact-SQL per abilitare Estensione database in un database  
 Prima di abilitare Estensione database sulle singole tabelle, è necessario abilitarla nel database.  
  
 L'abilitazione di Estensione database su un database o una tabella richiede autorizzazioni db_owner. L'abilitazione di Estensione database su un database richiede anche le autorizzazioni CONTROL DATABASE.  
  
1.  Prima di iniziare, scegliere un server di Azure esistente per i dati di cui Estensione database esegue la migrazione o creare un nuovo server.  
  
2.  Nel server di Azure, creare una regola del firewall con l'intervallo di indirizzi IP di SQL Server che permette la comunicazione tra SQL Server e il server remoto.  

    Per trovare facilmente i valori necessari e creare la regola del firewall, provare a connettersi al server di Azure da Esplora oggetti in SQL Server Management Studio (SSMS). SQL Server Management Studio consente di creare la regola aprendo la finestra di dialogo seguente, che include già i valori dell'indirizzo IP richiesti.
    
    ![Regola del firewall per l'estensione](../../sql-server/stretch-database/media/firewall-rule-for-stretch.png)
  
3.  Per configurare un database di SQL Server per Estensione database, il database deve disporre di una chiave master del database. La chiave master del database consente di proteggere le credenziali usate da Estensione database per la connessione al database remoto. L'esempio che segue crea una nuova chiave master del database.  
  
    ```tsql  
    USE <database>; 
    GO  
  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD='<password>'; 
    GO
    ```  
    Per altre informazioni sulla chiave master del database, vedere [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md) e [Creazione della chiave master di un database](../../relational-databases/security/encryption/create-a-database-master-key.md).
    
4.  Quando si configura un database per Estensione database, è necessario specificare le credenziali per Estensione database da usare per la comunicazione tra SQL Server locale e il server Azure remoto. Sono disponibili due opzioni.  
  
    -   È possibile fornire le credenziali amministratore.  
  
        -   Se si abilita Estensione database con la procedura guidata, è possibile creare le credenziali in quel momento.  
  
        -   Se si abilita Estensione database eseguendo **ALTER DATABASE**, è necessario creare manualmente le credenziali prima di eseguire **ALTER DATABASE** per abilitare Estensione database. 
        
        L'esempio che segue crea una nuova credenziale.
  
        ```tsql  
        CREATE DATABASE SCOPED CREDENTIAL <db_scoped_credential_name>  
            WITH IDENTITY = '<identity>' , SECRET = '<secret>' ;
        GO   
        ```  

         Per altre informazioni sulla credenziale, vedere [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). Per la creazione delle credenziali, è necessaria l'autorizzazione ALTER ANY CREDENTIAL.  

    -   È possibile usare un account del servizio federato per SQL Server per comunicare con il server remoto di Azure quando vengono soddisfatte le condizioni seguenti.  
  
        -   L'account del servizio usato per l'esecuzione dell'istanza di SQL Server è un account di dominio.  
  
        -   L'account di dominio appartiene a un dominio il cui Active Directory è federato con Azure Active Directory.  
  
        -   Il server Azure remoto è configurato per supportare l'autenticazione di Azure Active Directory.  
  
        -   L'account del servizio in cui è in esecuzione l'istanza di SQL Server deve essere configurato come account dbmanager o sysadmin nel server remoto di Azure.  
  
5.  Per configurare un database per Estensione database, eseguire il comando ALTER DATABASE.  
  
    1.  Per l'argomento SERVER, specificare il nome di un server di Azure esistente, inclusa la parte del nome `.database.windows.net` , ad esempio `MyStretchDatabaseServer.database.windows.net`.  
  
    2.  Fornire le credenziali di amministratore esistenti con l'argomento CREDENTIAL o specificare FEDERATED_SERVICE_ACCOUNT = ON. L'esempio seguente fornisce credenziali esistenti.  
  
    ```tsql  
    ALTER DATABASE <database name>  
        SET REMOTE_DATA_ARCHIVE = ON  
            (  
                SERVER = '<server_name>' ,  
                CREDENTIAL = <db_scoped_credential_name>  
            ) ;  
    GO
    ```  
  
## <a name="next-steps"></a>Passaggi successivi  
-   [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) per abilitare altre tabelle.  
  
-   [Monitor and troubleshoot data migration &#40;Stretch Database&#41; (Monitorare e risolvere i problemi relativi alla migrazione dei dati (Estensione database))](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) per visualizzare lo stato della migrazione dei dati.  
  
-   [Pause and resume data migration &#40;Stretch Database&#41; (Sospendere e riprendere la migrazione dei dati (Estensione database))](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
-   [Gestione e risoluzione dei problemi di Estensione database](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
-   [Backup e ripristino di database abilitati per l'estensione](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
  
-   [Restore Stretch-enabled databases (Ripristinare database abilitati per l'estensione)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Identificare i database e le tabelle per Estensione database eseguendo Stretch Database Advisor](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md)   
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  

