---
title: Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell&quot;URL | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 06e3118f67db6f01dad0344b42024534081433fb
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento sono inclusi i suggerimenti per la risoluzione dei problemi e le procedure consigliate relativi al backup e ripristino di SQL Server nel servizio BLOB di Windows Azure.  
  
 Per ulteriori informazioni sull'utilizzo del servizio di archiviazione BLOB di Windows Azure per le operazioni di backup e ripristino di SQL Server, vedere:  
  
-   [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione BLOB di Windows Azure](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Gestione dei backup  
 Nell'elenco seguente sono inclusi i consigli generali sulla gestione dei backup:  
  
-   Per evitare la sovrascrittura accidentale dei BLOB, è consigliabile l'utilizzo di un nome file univoco per ogni backup.  
  
-   Quando si crea un contenitore, è consigliabile impostare il livello di accesso su **privato**, in modo che solo gli utenti o account che possono fornire le informazioni di autenticazione richieste possano leggere o scrivere i BLOB nel contenitore.  
  
-   Per i database di SQL Server in un'istanza di SQL Server in esecuzione in una macchina virtuale di Windows Azure, utilizzare un account di archiviazione nella stessa area della macchina virtuale per evitare i costi di trasferimento dei dati tra le aree. L'utilizzo della stessa area garantisce anche prestazioni ottimali per le operazioni di backup e ripristino.  
  
-   Un'attività di backup non completata correttamente può generare un file di backup non valido. Sono consigliate l'identificazione periodica dei backup non completati e l'eliminazione dei file BLOB. Per altre informazioni, vedere [Eliminazione dei file BLOB di backup con lease attivi](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)  
  
-   L'utilizzo dell'opzione **WITH COMPRESSION** durante il backup consente di ridurre i costi di archiviazione e quelli delle transazioni di archiviazione. Inoltre, tramite questa opzione è possibile diminuire il tempo necessario per completare il processo di backup.  
  
## <a name="handling-large-files"></a>Gestione di file di grandi dimensioni  
  
-   Nell'operazione di backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzati più thread per ottimizzare il trasferimento dei dati ai servizi di archiviazione BLOB di Windows Azure.  Le prestazioni, tuttavia, dipendono da vari fattori, ad esempio la larghezza di banda del fornitore di software indipendente e le dimensioni del database. Se si intende eseguire il backup di database o filegroup di grandi dimensioni da un database di SQL Server locale, si consiglia di eseguire innanzitutto alcuni test della velocità effettiva. I [contratti di servizio della risorsa di archiviazione](http://azure.microsoft.com/support/legal/sla/storage/v1_0/) di Azure presentano tempi di elaborazione massimi per i BLOB che è possibile prendere in considerazione.  
  
-   L'uso dell'opzione **WITH COMPRESSION** come consigliato nella sezione **Gestione dei backup** è molto importante quando si esegue il backup di file di grandi dimensioni.  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Risoluzione dei problemi di backup nell'URL e di ripristino dallo stesso  
 Di seguito sono elencate alcune modalità rapide per la risoluzione di errori durante l'esecuzione del backup nel servizio di archiviazione BLOB di Windows Azure o del ripristino dallo stesso.  
  
 Per evitare errori a causa di opzioni o limitazioni non supportate, esaminare l'elenco delle limitazioni e le informazioni sul supporto dei comandi BACKUP e RESTORE nell'articolo [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
 **Errori di autenticazione:**  
  
-   WITH CREDENTIAL è una nuova opzione ed è necessaria per le operazioni di backup nel servizio di archiviazione BLOB di Windows Azure e di ripristino dallo stesso. Di seguito sono riportati i possibili errori correlati alle credenziali:  
  
     Le credenziali specificate nel comando **BACKUP** o **RESTORE** non esistono. Per evitare questo problema, è possibile includere istruzioni T-SQL per creare le credenziali qualora non siano presenti nell'istruzione di backup. Di seguito è riportato un esempio pratico:  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   Le credenziali esistono, ma all'account di accesso utilizzato per eseguire il comando di backup non sono associate autorizzazioni per accedere alle credenziali. Usare un account di accesso nel ruolo **db_backupoperator** con autorizzazioni **Modifica qualsiasi credenziale** .  
  
-   Verificare il nome dell'account di archiviazione e i valori di chiave. Le informazioni archiviate nelle credenziali devono corrispondere ai valori delle proprietà dell'account di archiviazione di Windows Azure utilizzati nelle operazioni di backup e ripristino.  
  
 **Errori di backup:**  
  
-   L'esecuzione di backup paralleli nello stesso BLOB comporta il mancato completamento di uno dei backup con conseguente errore **Inizializzazione non riuscita** .  
  
-   Utilizzare i log degli errori seguenti per facilitare la risoluzione degli errori di backup:  
  
    -   Impostare il flag di traccia 3051 per abilitare la registrazione in un log degli errori specifico con il formato seguente in:  
  
         BackupToUrl-\<nomeist>-\<nomedb>-azione-\<PID.log Dove \<azione> è uno dei valori seguenti:  
  
        -   **DB**  
  
        -   **FILELISTONLY**  
  
        -   **LABELONLY**  
  
        -   **HEADERONLY**  
  
        -   **VERIFYONLY**  
  
    -   Inoltre, è possibile trovare informazioni esaminando i registri denominati "SQLBackupToUrl" presenti in Registro eventi di Windows - Applicazione.  
  
-   Quando si esegue il ripristino da un backup compresso, è possibile che venga visualizzato l'errore seguente:  
  
    -   **Si è verificata un'eccezione SqlException 3284. Gravità: 16, Stato: 5**  
        **Il contrassegno di file del messaggio nel dispositivo 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' non è allineato. Eseguire nuovamente l'istruzione RESTORE con le stesse dimensioni del blocco utilizzate per creare il set di backup: '65536' potrebbe essere un possibile valore.**  
  
         Per risolvere il problema, eseguire nuovamente l'istruzione **BACKUP** con il valore **BLOCKSIZE = 65536** specificato.  
  
-   Errore durante il backup a causa di BLOB con lease attivi: l'attività di backup non completata può generare BLOB con lease attivi.  
  
     Se si tenta di nuovo un'istruzione di backup, quest'ultimo potrebbe non essere completato e potrebbe essere visualizzato un errore simile al seguente:  
  
     **Il backup nell'URL ha ricevuto un'eccezione dall'endpoint remoto. Messaggio eccezione: Il server remoto ha restituito un errore: (412) Attualmente esiste un lease nel BLOB ma nella richiesta non è stato specificato alcun ID lease**.  
  
     Se un'istruzione RESTORE viene tentata in un file BLOB di backup con un lease attivo, l'operazione di ripristino non viene completata e viene visualizzato un errore simile al seguente:  
  
     **Messaggio eccezione: Il server remoto ha restituito un errore: (409) Conflitto.**  
  
     Quando si verifica un errore di questo tipo, i file BLOB devono essere eliminati. Per altre informazioni su questo scenario e su come risolvere il problema, vedere [Eliminazione dei file BLOB di backup con lease attivi](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)  
  
## <a name="proxy-errors"></a>Errori del proxy  
 Se si utilizzano server proxy per accedere a Internet, è possibile che si verifichino i problemi indicati di seguito:  
  
 **Limitazione della connessione da parte dei server proxy**  
  
 Nei server proxy possono essere presenti impostazioni che limitano il numero di connessioni al minuto. Il backup su URL è un processo multithread e pertanto può superare il limite. In questo caso, il server proxy termina la connessione. Per risolvere il problema, modificare le impostazioni del proxy in modo che non venga utilizzato in SQL Server.   Di seguito sono riportati alcuni esempi di tipi o messaggi di errore visualizzati nel log degli errori:  
  
-   Impossibile scrivere su "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak": Il backup su URL ha ricevuto un'eccezione dall'endpoint remoto. Messaggio di eccezione: Impossibile leggere dati dalla connessione del trasporto. La connessione è stata chiusa.  
  
-   Errore di I/O irreversibile nel file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak": Impossibile recuperare l'errore dall'endpoint remoto.  
  
     Messaggio 3013, livello 16, stato 1, riga 2  
  
     Interruzione anomala di BACKUP DATABASE in corso.  
  
-   BackupIoRequest::ReportIoError: errore di scrittura nel dispositivo di backup "http://storageaccount.blob.core.window.net/container/BackupAzurefile.bak". Errore del sistema operativo: Il backup nell'URL ha ricevuto un'eccezione dall'endpoint remoto. Messaggio di eccezione: Impossibile leggere dati dalla connessione del trasporto. La connessione è stata chiusa.  
  
 Se si abilita la registrazione dettagliata mediante il flag di traccia 3051, è inoltre possibile che nei log venga visualizzato il messaggio seguente:  
  
 Codice di stato HTTP 502. Messaggio di stato HTTP: errore del proxy (Il numero di richieste HTTP al minuto supera il limite configurato. Contattare l'amministratore di ISA Server).  )  
  
 **Impostazioni proxy predefinite non rilevate:**  
  
 Talvolta le impostazioni predefinite non vengono rilevate, causando errori di autenticazione del proxy come quello indicato di seguito:*Errore di I/O irreversibile nel file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak": Impossibile recuperare l'errore dall'endpoint remoto. Messaggio di eccezione: Errore del server remoto: (407)* **Richiesta autenticazione proxy**.  
  
 Per risolvere il problema, creare un file di configurazione che consenta al processo di backup su URL di utilizzare le impostazioni predefinite del proxy effettuando i passaggi indicati di seguito.  
  
1.  Creare un file di configurazione denominato BackuptoURL.exe.config con il seguente codice XML:  
  
    ```  
    \<?xml version ="1.0"?>  
    <configuration>   
                    \<system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    \</system.net>  
    </configuration>  
  
    ```  
  
2.  Inserire il file di configurazione nella cartella Binn dell'istanza di SQL Server. Ad esempio, se SQL Server viene installato nell'unità C del computer, inserire il file di configurazione in: *C:\Programmi\Microsoft SQL Server\MSSQL13.\<NomeIstanza\MSSQL\Binn*.  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristino da backup archiviati in Microsoft Azure](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)
  

