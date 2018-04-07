---
title: Transparent Data Encryption per Parallel Data Warehouse
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: Crittografia dati trasparente (TDE) esegue la crittografia dei / o in tempo reale e la decrittografia dei dati e i file di log delle transazioni e i file di log PDW speciali.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d
caps.latest.revision: 22
ms.openlocfilehash: d93d76018baeed1577b6831cbde359002c89416e
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="transparent-data-encryption"></a>Transparent Data Encryption
Per proteggere il database è possibile adottare alcune accortezze, tra cui la progettazione di un sistema sicuro, la crittografia dei dati riservati e la compilazione di un firewall attorno ai server di database. Tuttavia, nel caso in cui i supporti fisici (ad esempio unità o nastri di backup) venissero rubati, un malintenzionato potrebbe ripristinare o collegare il database e accedere ai dati. Una soluzione per ovviare al problema consiste nel crittografare i dati sensibili nel database e proteggere con un certificato le chiavi usate per la crittografia. In questo modo si impedisce a chi è sprovvisto delle chiavi di usare i dati; tuttavia, questo tipo di protezione deve essere pianificato in anticipo.  
  
*Crittografia dati trasparente* (TDE) esegue la crittografia dei / o in tempo reale e la decrittografia dei dati e file di log file di log delle transazioni e PDW speciali. Per la crittografia viene usata una chiave di crittografia del database (DEK), archiviata nel record di avvio del database affinché sia disponibile durante le operazioni di recupero. La chiave DEK è una chiave simmetrica protetta tramite un certificato archiviato nel database master di SQL Server PDW. TDE consente di proteggere i dati "non operativi", ovvero i file di dati e di log, e assicura la conformità a numerose leggi, normative e linee guida stabilite in vari settori. Gli sviluppatori software possono ora crittografare i dati usando gli algoritmi di crittografia AES e 3DES senza modificare applicazioni esistenti.  
  
> [!IMPORTANT]  
> TDE non fornisce la crittografia per i dati scambiati fra il client e di PDW. Per ulteriori informazioni su come crittografare i dati tra il client e SQL Server PDW, vedere [il provisioning di un certificato](provision-certificate.md).  
>   
> Transparent Data Encryption crittografa i dati durante lo spostamento o in uso. Il traffico interno tra componenti PDW all'interno di SQL Server PDW non verrà crittografato. Dati archiviati temporaneamente nel buffer di memoria non vengono crittografati. Per limitare questo rischio, controllare l'accesso fisico e le connessioni a SQL Server PDW.  
  
Una volta protetto, il database può essere ripristinato usando il certificato corretto.  
  
> [!NOTE]  
> Quando si crea un certificato per TDE, è necessario immediatamente eseguirne il backup, con la chiave privata associata. Se il certificato non è più disponibile o se è necessario ripristinare o collegare il database a un altro server, è necessario disporre di copie di backup del certificato e della chiave privata, altrimenti non sarà possibile aprire il database. Il certificato di crittografia deve essere mantenuto anche se la funzionalità TDE non è più abilitata nel database. Anche se il database non è crittografato, è possibile che parti del log delle transazioni restino comunque protette e che il certificato sia necessario per alcune operazioni per l'esecuzione del backup completo del database. Un certificato che ha superato la data di scadenza può ancora essere usato per crittografare e decrittografare dati con TDE.  
  
La crittografia del file di database viene eseguita a livello di pagina. Le pagine di un database crittografato sono crittografate prima di essere scritte sul disco e decrittografate quando vengono lette in memoria. L'uso di TDE non comporta un aumento delle dimensioni del database crittografato.  
  
La figura seguente mostra la gerarchia delle chiavi per la crittografia TDE:  
  
![Visualizza la gerarchia descritta nell'argomento. ] (media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>Uso della crittografia dati trasparente  
Per usare TDE, eseguire le operazioni seguenti: I primi tre passaggi sono solo una volta, durante la preparazione di SQL Server PDW per il supporto di Transparent Data Encryption.  
  
1.  Creare una chiave master nel database master.  
  
2.  Utilizzare **sp_pdw_database_encryption** per abilitare TDE in SQL Server PDW. Questa operazione consente di modificare i database temporanei per garantire la protezione dei dati temporanei future e avrà esito negativo se si è tentato quando sono presenti sessioni attive che hanno tabelle temporanee. **sp_pdw_database_encryption** attiva la maschera dati utente nei registri di sistema PDW. (Per ulteriori informazioni sulla maschera dati utente nei registri di sistema PDW, vedere [sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md).)  
  
3.  Utilizzare [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) per creare le credenziali che è possono eseguire l'autenticazione e scrittura per la condivisione in cui verrà archiviato il backup del certificato. Se esiste una credenziale per il server di archiviazione previsto, è possono utilizzare le credenziali esistenti.  
  
4.  Nel database master, creare un certificato protetto dalla chiave master.  
  
5.  Il certificato per la condivisione di archiviazione di backup.  
  
6.  Nel database utente, creare una chiave di crittografia del database e proteggerla mediante il certificato viene archiviato nel database master.  
  
7.  Utilizzare il `ALTER DATABASE` istruzione per crittografare il database tramite Transparent Data Encryption.  
  
L'esempio seguente illustra la crittografia di `AdventureWorksPDW2012` database con un certificato denominato `MyServerCert`, creato in SQL Server PDW.  
  
**Primo passaggio: Abilitare TDE in SQL Server PDW.** Questo è necessario solo una volta.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
-- Add a credential that can write to the share  
-- A credential created for a backup can be used if you wish  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
**Secondo: Creare ed eseguire il backup di un certificato nel database master.** Questo è solo obbligatorio una sola volta. È possibile disporre di un certificato separato per ogni database (scelta consigliata) oppure è possibile proteggere più database con un certificato.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';  
GO  
  
-- Back up the certificate with private key  
BACKUP CERTIFICATE MyServerCert   
    TO FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'  
    WITH PRIVATE KEY   
    (   
        FILE = '\\SECURE_SERVER\cert\MyServerCert.key',  
        ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>'   
    )   
GO  
```  
  
**: Creare la chiave DEK e dell'ultima, Utilizzare ALTER DATABASE per crittografare un database utente.** Ciò viene ripetuto per ogni database protetto con TDE.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_128  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
  
ALTER DATABASE AdventureWorksPDW2012 SET ENCRYPTION ON;  
GO  
```  
  
Le operazioni di crittografia e decrittografia sono pianificate sui thread di background da SQL Server. Per visualizzare lo stato di queste operazioni, è possibile usare le viste del catalogo e le viste a gestione dinamica nell'elenco illustrato di seguito in questo argomento.  
  
> [!CAUTION]  
> I file di backup dei database in cui è abilitata la funzionalità TDE vengono crittografati anche tramite la chiave di crittografia del database. Di conseguenza, quando questi backup vengono ripristinati, è necessario disporre del certificato che protegge la chiave di crittografia del database. Pertanto, oltre ad eseguire il backup del database, è necessario assicurarsi di conservare un backup dei certificati server per impedire la perdita di dati. Se il certificato non è più disponibile, si verificherà la perdita di dati.  
  
## <a name="commands-and-functions"></a>Comandi e funzioni  
Affinché vengano accettati dalle istruzioni indicate di seguito, è necessario che i certificati TDE siano crittografati mediante la chiave master del database.  
  
Nella tabella seguente sono inclusi collegamenti e spiegazioni delle funzioni e dei comandi correlati a TDE.  
  
|Comando o funzione|Scopo|  
|-----------------------|-----------|  
|[CREARE UNA CHIAVE DI CRITTOGRAFIA DEL DATABASE](../t-sql/statements/create-database-encryption-key-transact-sql.md)|Consente di creare una chiave usata per crittografare un database.|  
|[ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Consente di modificare la chiave usata per crittografare un database.|  
|[DROP DATABASE ENCRYPTION KEY](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Consente di rimuovere la chiave usata per crittografare un database.|  
|[ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md)|Descrive l'opzione **ALTER DATABASE** , usata per abilitare TDE.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>Viste del catalogo e viste a gestione dinamica  
Nella tabella seguente vengono illustrate le viste del catalogo e le viste a gestione dinamica di TDE.  
  
|Vista del catalogo e vista a gestione dinamica|Scopo|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Vista del catalogo che consente di visualizzare le informazioni del database.|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Vista del catalogo che consente di visualizzare i certificati di un database.|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|Vista a gestione dinamica che fornisce informazioni per ogni nodo, le chiavi di crittografia utilizzato in un database e lo stato di crittografia di un database.|  
  
## <a name="permissions"></a>Autorizzazioni  
Ogni funzionalità e comando di TDE ha requisiti specifici relativi alle autorizzazioni, descritti nelle tabelle precedenti.  
  
La visualizzazione dei metadati interessati da TDE richiede il `CONTROL SERVER` autorizzazione.  
  
## <a name="considerations"></a>Considerazioni  
Durante un'analisi di una nuova crittografia di un database, le operazioni di manutenzione per il database sono disabilitate.  
  
È possibile trovare lo stato di crittografia del database utilizzando il **sys.dm_pdw_nodes_database_encryption_keys** vista a gestione dinamica. Per ulteriori informazioni, vedere il *viste del catalogo e viste a gestione dinamica* in precedenza in questo argomento).  
  
### <a name="restrictions"></a>Restrizioni  
Le operazioni seguenti non sono consentite durante il `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, o `ALTER DATABASE...SET ENCRYPTION` istruzioni.  
  
-   Eliminazione del database.  
  
-   Utilizzando un `ALTER DATABASE` comando.  
  
-   Per avviare un backup di database.  
  
-   Avvio di un ripristino del database.  
  
Le seguenti operazioni o condizioni impediscono il `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, o `ALTER DATABASE...SET ENCRYPTION` istruzioni.  
  
-   Un `ALTER DATABASE` comando è in esecuzione.  
  
-   Un backup dei dati è in corso di esecuzione.  
  
Durante la creazione dei file di database, l'inizializzazione immediata dei file non è disponibile se è abilitata la crittografia TDE.  
  
### <a name="areas-not-protected-by-tde"></a>Non è protette da TDE aree  
Transparent Data Encryption non protegge le tabelle esterne.  
  
TDE non fornisce protezione sessioni di diagnostica. Prestare attenzione agli utenti non per le query con parametri sensibili, mentre le sessioni di diagnostica sono in uso. Sessioni di diagnostica che rivelano informazioni riservate devono essere eliminate non appena non sono più necessari.  
  
Dati protetti con TDE viene decrittografati quando viene inserita nella memoria di SQL Server PDW. Quando si verificano determinati problemi nel dispositivo, vengono creati i dump di memoria. Dump file rappresentano il contenuto della memoria al momento dell'aspetto problema e può contenere dati sensibili in un formato non crittografato. Prima di tali elementi sono condivisi con altri utenti, è necessario esaminare il contenuto del dump della memoria.  
  
Il database master non è protetto con TDE. Anche se il database master non contiene dati dell'utente, tali informazioni includono informazioni quali nomi account di accesso.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Crittografia trasparente dei dati e log delle transazioni  
Abilitazione di un database utilizzare questo tipo ha l'effetto di azzeramento la parte rimanente del log delle transazioni virtuale per forzare il log delle transazioni virtuale successivo. Ciò garantisce che non rimanga alcun testo non crittografato nei log delle transazioni dopo che il database viene impostato per la crittografia. È possibile determinare lo stato della crittografia del file di log in ogni nodo PDW visualizzando il `encryption_state` colonna il `sys.dm_pdw_nodes_database_encryption_keys` visualizzazione, come nel seguente esempio:  
  
```sql  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
           ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
Tutti i dati scritti nel log delle transazioni prima di una modifica della chiave di crittografia del database saranno crittografati usando la chiave di crittografia del database precedente.  
  
### <a name="pdw-activity-logs"></a>Log attività PDW  
SQL Server PDW gestisce un set di registri previsto per la risoluzione dei problemi. Si noti, non si tratta del log delle transazioni, il log degli errori di SQL Server o il registro eventi di Windows. Questi log attività PDW possono contenere istruzioni complete in testo non crittografato, alcuni dei quali può contenere i dati utente. Sono esempi tipici **inserire** e **aggiornamento** istruzioni. Mascheramento dei dati utente possa essere esplicitamente attivata o disattivata tramite **sp_pdw_log_user_data_masking**. Abilitazione di crittografia in SQL Server PDW automaticamente consente di attivare il mascheramento dei dati utente nei log attività PDW per proteggerli. **sp_pdw_log_user_data_masking** consente inoltre al fine di mascherare istruzioni se non si utilizza Transparent Data Encryption, ma non è consigliabile in quanto riduce notevolmente la capacità del Team di supporto di Microsoft di analizzare i problemi.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparent Data Encryption e database di sistema tempdb  
Il database di sistema tempdb viene crittografato durante la crittografia è abilitata tramite [sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md). Ciò è necessario prima di qualsiasi database può utilizzare Transparent Data Encryption. Potrebbe essere un effetto sulle prestazioni per database non crittografati presenti nella stessa istanza di SQL Server PDW.  
  
## <a name="key-management"></a>Gestione chiavi  
La chiave di crittografia del database (DEK) è protetto per i certificati archiviati nel database master. Questi certificati sono protetti dalla chiave master del database (DMK) del database master. La DMK deve essere protetto dalla chiave master del servizio (SMK) per poter essere usato per TDE.  
  
Il sistema può accedere alle chiavi senza intervento umano (ad esempio fornire una password). Se il certificato non è disponibile, il sistema genera un errore per segnalare che la chiave di Decrittografia non possono essere decrittografati fino a quando non è disponibile il certificato appropriato.  
  
Quando si sposta un database da un dispositivo a un altro, il certificato utilizzato per proteggere il ' necessario ripristinare innanzitutto chiave DEK nel server di destinazione. Il database può quindi essere ripristinato come di consueto. Per ulteriori informazioni, vedere la documentazione di SQL Server standard, all'indirizzo [spostare un Database protetto con TDE in un altro Server SQL](http://technet.microsoft.com/library/ff773063.aspx).  
  
I certificati utilizzati per crittografare DEK devono essere mantenuti fino a quando sono presenti backup dei database che li utilizzano. Backup del certificato deve includere la chiave privata del certificato, perché senza la chiave privata non può essere utilizzato un certificato per il ripristino di database. Questi backup chiave privata del certificato vengono archiviati in un file separato, protetto da password che devono essere fornite per il ripristino di certificato.  
  
## <a name="restoring-the-master-database"></a>Ripristino del Database master  
Il database master può essere ripristinato utilizzando **DWConfig**, come parte del ripristino di emergenza.  
  
-   Se il nodo di controllo non è stato modificato, ovvero che se il database master viene ripristinato nel dispositivo stesso e invariato da cui è stato eseguito il backup del database master, la DMK e tutti i certificati possono essere lette senza un'ulteriore azione.  
  
-   Se il database master viene ripristinato in un dispositivo diverso o se il nodo di controllo è stato modificato dopo il backup del database master, saranno necessario passaggi aggiuntivi per rigenerare la DMK.  
  
    1.  Aprire la DMK:  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  Aggiungere la crittografia dal SMK:  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  Riavviare il dispositivo.  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>L'aggiornamento e la sostituzione di macchine virtuali  
Se una DMK esiste nel dispositivo in cui è stato eseguito l'aggiornamento o sostituire VM, è necessario specificare la password DMK come parametro.  
  
Esempio di azione di aggiornamento. Sostituire `**********` con la password DMK.  
  
`setup.exe /Action=ProvisionUpgrade … DMKPassword='**********'  `  
  
Esempio di azione di macchina virtuale di sostituzione.  
  
`setup.exe /Action=ReplaceVM … DMKPassword='**********'  `  
  
Durante l'aggiornamento, se un database utente verrà crittografato e la password DMK non viene specificata, l'azione di aggiornamento avrà esito negativo. Durante la sostituzione, se la password corretta non è disponibile quando esiste una DMK, l'operazione verrà ignorato il passaggio di recupero DMK. Tutti gli altri passaggi verranno completati alla fine dell'azione di sostituzione VM, tuttavia, l'azione segnalerà un errore alla fine per indicare che sono necessari passaggi aggiuntivi. Nei registri di installazione (si trova **\ProgramData\Microsoft\Microsoft SQL Server Parallel Data Warehouse\100\Logs\Setup\\\Detail-Setup < timestamp >**), verrà visualizzato l'avviso seguente verso la fine.  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!  `
  
. Eseguire manualmente tali istruzioni in PDW e riavviare dispositivo dopo che per eseguire il ripristino DMK:  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
Utilizzare i passaggi nel **ripristino del Database master** per recuperare il database di paragrafo e quindi riavviare il dispositivo.  
  
Se la DMK esistenti prima ma non è stata recuperata dopo l'azione, verrà generato il seguente messaggio di errore quando viene eseguita una query di un database.  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>Impatto sulle prestazioni  
L'impatto sulle prestazioni di TDE varia con il tipo di dati che disponibili, modalità di archiviazione e il tipo di attività del carico di lavoro in SQL Server PDW. Quando protetto da TDE, il / o di lettura e quindi la decrittografia dei dati o la crittografia e quindi la scrittura dei dati è un'attività con utilizzo intensivo della CPU e avrà impatto maggiore quando vengono eseguite altre attività con utilizzo intensivo della CPU nello stesso momento. Poiché Transparent Data Encryption crittografa `tempdb`, TDE può influenzare le prestazioni dei database che non sono crittografati. Per ottenere un'idea precisa delle prestazioni, è consigliabile testare l'intero sistema con l'attività di dati e query.  
  
## <a name="related-content"></a>Contenuto correlato  
I collegamenti seguenti contengono informazioni generali su come SQL Server gestisce la crittografia. Questi argomenti consentono di comprendere la crittografia di SQL Server, ma in questi argomenti non dispongono di informazioni specifiche di SQL Server PDW e vengono illustrate le funzionalità che non sono presenti in SQL Server PDW.  
  
-   [Crittografia di SQL Server](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [Gerarchia di crittografia](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [Chiavi di crittografia del database e di SQL Server](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md)  
[CREAZIONE DELLA CHIAVE MASTER](../t-sql/statements/create-master-key-transact-sql.md)  
[CREARE UNA CHIAVE DI CRITTOGRAFIA DEL DATABASE](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
