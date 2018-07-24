---
title: BACKUP DATABASE (Parallel Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 73c8d465-b36b-4727-b9f3-368e98677c64
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 41ad9d69b045a149bf6adad58f16f881ccc5d98e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38004764"
---
# <a name="backup-database-parallel-data-warehouse"></a>BACKUP DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Crea un backup di un database [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] e archivia il backup all'esterno dell'appliance in un percorso di rete specificato dall'utente. Usare questa istruzione con [RESTORE DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md) per il ripristino di emergenza o per copiare un database da un'appliance all'altra.  
  
 **Prima di iniziare**, vedere "Acquisire e configurare un server di backup" in [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 In [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sono disponibili due tipi di backup. Un *backup di database completo* è un backup di un intero database [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Un *backup di database differenziale* include solo le modifiche apportate dall'ultimo backup completo. Il backup di un database utente include gli utenti del database e i ruoli del database. Il backup del database master include gli account di accesso.  
  
 Per altre informazioni sui backup di database [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], vedere "Backup e ripristino" in [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      Create a full backup of a user database or the master database.  
BACKUP DATABASE database_name  
    TO DISK = '\\UNC_path\backup_directory'  
    [ WITH [ ( ]  <with_options> [ ,...n ]  [ ) ] ]  
[;]  
  
Create a differential backup of a user database.  
BACKUP DATABASE database_name  
    TO DISK = '\\UNC_path\backup_directory'  
    WITH [ ( ] DIFFERENTIAL   
    [ , <with_options> [ ,...n ] [ ) ]  
[;]  
  
<with_options> ::=  
    DESCRIPTION = 'text'  
    | NAME = 'backup_name'  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database in cui creare un backup. Il database può essere il database master o un database utente.  
  
 TO DISK = '\\\\*UNC_path*\\*backup_directory*'  
 Il percorso di rete e la directory in cui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] scrive i file di backup. Ad esempio, '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'.  
  
-   Il percorso del nome della directory di backup deve esistere già e deve essere specificato come percorso UNC completo.  
  
-   La directory di backup, *backup_directory*, non deve essere presente prima di eseguire il comando di backup. La directory di backup viene creata da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
-   Il percorso della directory di backup non può essere un percorso locale e non può essere il percorso di uno dei nodi di appliance [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
-   La lunghezza massima del percorso UNC e del nome della directory di backup è di 200 caratteri.  
  
-   Il server o l'host deve essere specificato come indirizzo IP.  Non è possibile specificarlo come nome host o nome server.  
  
 DESCRIPTION = **'***text***'**  
 Specifica una descrizione testuale del backup. La lunghezza massima del testo è di 255 caratteri.  
  
 La descrizione viene archiviata nei metadati e verrà visualizzata quando l'intestazione del backup viene ripristinata con RESTORE HEADERONLY.  
  
 NAME = **'***backup _name***'**  
 Specifica il nome del backup. Il nome del backup può essere diverso dal nome del database.  
  
-   I nomi possono essere composti da un massimo di 128 caratteri.  
  
-   Non è possibile includere un percorso.  
  
-   Deve iniziare con una lettera o un numero oppure con un carattere di sottolineatura (_). I caratteri speciali consentiti sono il carattere di sottolineatura (\_), il trattino (-) o lo spazio ( ). I nomi di backup non possono terminare con uno spazio.  
  
-   L'istruzione avrà esito negativo se *backup_name* esiste già nel percorso specificato.  
  
 Questo nome viene archiviato nei metadati e verrà visualizzato quando l'intestazione del backup viene ripristinata con RESTORE HEADERONLY.  
  
 DIFFERENTIAL  
 Specifica di eseguire un backup differenziale di un database utente. Se omesso, il valore predefinito è un backup completo del database. Il nome del backup differenziale non deve necessariamente corrispondere al nome del backup completo. Per tenere traccia del backup differenziale e del backup completo corrispondente, può essere utile usare lo stesso nome con l'aggiunta di 'compl' o 'diff'.  
  
 Ad esempio  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerFull';`  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerDiff' WITH DIFFERENTIAL;`  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione **BACKUP DATABASE** o l'appartenenza nel ruolo predefinito del database **db_backupoperator**. Il backup del database master può essere eseguito solo da un utente standard aggiunto al ruolo predefinito del database **db_backupoperator**. Il backup del database master può essere eseguito solo da **sa**, l'amministratore dell'infrastruttura, o dai membri del ruolo predefinito del server **sysadmin**.  
  
 Richiede un account di Windows con l'autorizzazione per accedere, creare e scrivere nella directory di backup. È anche necessario archiviare il nome e la password dell'account di Windows in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Per aggiungere queste credenziali di rete in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare la stored procedure [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
 Per altre informazioni sulla gestione delle credenziali in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], vedere la sezione [Sicurezza](#Security).  
  
## <a name="error-handling"></a>Gestione degli errori  
 Gli errori di BACKUP DATABASE si verificano nelle condizioni seguenti:  
  
-   Le autorizzazioni utente non sono sufficienti per eseguire un backup.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non ha le autorizzazioni corrette per il percorso di rete in cui verrà archiviato il backup.  
  
-   Il database non esiste.  
  
-   La directory di destinazione esiste già nella condivisione di rete.  
  
-   La condivisione di rete di destinazione non è disponibile.  
  
-   La condivisione di rete di destinazione non ha spazio sufficiente per il backup. Il comando BACKUP DATABASE non conferma l'esistenza di spazio su disco sufficiente prima di avviare il backup e rende possibile la generazione di un errore di spazio su disco insufficiente durante l'esecuzione di BACKUP DATABASE. Quando si verifica un errore di spazio su disco insufficiente, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] esegue il rollback del comando BACKUP DATABASE. Per ridurre le dimensioni del database, eseguire [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)  
  
-   Tentativo di avviare un backup in una transazione.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Prima di eseguire un backup del database, usare [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) per ridurre le dimensioni del database. 
 
 Un backup di [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] viene archiviato come set di file multipli all'interno della stessa directory.  
  
 Un backup differenziale richiede in genere meno tempo rispetto a un backup completo e può essere eseguito più di frequente. Quando più copie di backup differenziale si basano sullo stesso backup completo, ogni backup differenziale include tutte le modifiche del backup differenziale precedente.  
  
 Se si annulla un comando BACKUP, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] rimuoverà la directory di destinazione e i file creati per il backup. Se [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] perde la connettività di rete alla condivisione, non è possibile completare il rollback.  
  
 I backup completi e differenziali vengono archiviati in directory distinte. Le convenzioni di denominazione non vengono applicate per specificare che un backup completo e un backup differenziale sono collegati. È possibile tenerne traccia attraverso le proprie convenzioni di denominazione. In alternativa, è possibile tenerne traccia usando l'opzione WITH DESCRIPTION per aggiungere una descrizione e quindi usando l'istruzione RESTORE HEADERONLY per recuperare la descrizione.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Non è possibile eseguire un backup differenziale del database master. Sono supportati solo i backup completi del database master.  
  
 I file di backup sono archiviati in un formato adatto esclusivamente al ripristino del backup in un'appliance [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] tramite l'istruzione [RESTORE DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md).  
  
 Il backup con l'istruzione BACKUP DATABASE non può essere usato per trasferire i dati o le informazioni utente in database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMP. Per questa funzionalità, è possibile usare la funzione di copia della tabella remota. Per altre informazioni, vedere "Copia della tabella remota" in [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] usa la tecnologia di backup [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il backup e il ripristino dei database. Le opzioni di backup [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono preconfigurate per l'utilizzo della compressione dei backup. Non è possibile impostare opzioni di backup come la compressione, il checksum, la dimensione blocco e il conteggio buffer.  
  
 È possibile eseguire nell'appliance un solo backup o ripristino di database in qualsiasi momento. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] metterà in coda i comandi di backup o ripristino fino a quando non viene completato il comando di backup o ripristino corrente.  
  
 L'appliance di destinazione per il ripristino del backup deve avere almeno un numero di nodi di calcolo equivalente a quello dell'appliance di origine. La destinazione può avere un numero di nodi di calcolo maggiore dell'appliance di origine, ma non può avere un numero di nodi di calcolo minore.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non tiene traccia del percorso e dei nomi di backup poiché i backup sono archiviati all'esterno dell'appliance.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] tiene traccia dell'esito positivo o negativo dei backup del database.  
  
 È possibile eseguire un backup differenziale solo se l'ultimo backup completo è stato eseguito correttamente. Ad esempio, si supponga che il lunedì venga creato un backup completo del database Sales e che il backup venga eseguito correttamente. Il martedì si crea un backup completo del database Sales e il backup non viene eseguito correttamente. Dopo questo errore, non sarà possibile creare un backup differenziale basato sul backup completo di lunedì. Prima di creare un backup differenziale è necessario aver già creato un backup completo.  
  
## <a name="metadata"></a>Metadati  
 Queste DMV contengono informazioni su tutte le operazioni di backup, ripristino e caricamento. Le informazioni vengono mantenute tra un riavvio di sistema e l'altro.  
  
-   [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md)  
  
## <a name="performance"></a>restazioni  
 Per eseguire un backup, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] esegue prima il backup dei metadati e quindi esegue un backup parallelo dei dati di database archiviati nei nodi di calcolo. I dati vengono copiati direttamente da ogni nodo di calcolo nella directory di backup. Per ottenere le migliori prestazioni per lo spostamento dei dati dai nodi di calcolo alla directory di backup, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] controlla il numero di nodi di calcolo che copiano i dati contemporaneamente.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco ExclusiveUpdate nell'oggetto DATABASE.  
  
##  <a name="Security"></a> Sicurezza  
 I backup di [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non vengono archiviati nell'appliance. Pertanto, il team IT è responsabile della gestione di tutti gli aspetti della sicurezza dei backup. Questi aspetti includono ad esempio la gestione della sicurezza dei dati di backup, del server usato per l'archiviazione dei backup e dell'infrastruttura di rete che connette il server di backup all'appliance [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 **Gestire le credenziali di rete**  
  
 L'accesso di rete alla directory di backup è basato sulla sicurezza di condivisione dei file di Windows standard. Prima di eseguire un backup, è necessario creare o impostare un account di Windows che verrà usato per l'autenticazione di [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nella directory di backup. L'account di Windows deve avere le autorizzazioni per accedere, creare e scrivere nella directory di backup.  
  
> [!IMPORTANT]  
>  Per ridurre i rischi di sicurezza dei dati, è consigliabile impostare un account di Windows dedicato esclusivamente all'esecuzione delle operazioni di backup e ripristino. Concedere all'account le autorizzazioni solo per il percorso di backup.  
  
 È necessario archiviare nome utente e password in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] eseguendo la stored procedure [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md). [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] usa Gestione credenziali di Windows per archiviare e crittografare i nomi utente e le password nel nodo di controllo e nei nodi di calcolo. Con il comando BACKUP DATABASE non viene eseguito il backup delle credenziali.  
  
 Per rimuovere le credenziali di rete da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], vedere [sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
 Per visualizzare un elenco di tutte le credenziali di rete archiviate in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare la DMV [sys.dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-add-network-credentials-for-the-backup-location"></a>A. Aggiungere le credenziali di rete per il percorso di backup  
 Per creare un backup, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] deve avere l'autorizzazione di lettura/scrittura per la directory di backup. L'esempio seguente illustra come aggiungere le credenziali per un utente. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] memorizzerà queste credenziali che verranno usate per le operazioni di backup e ripristino.  
  
> [!IMPORTANT]  
>  Per motivi di sicurezza, è consigliabile creare un account di dominio dedicato esclusivamente all'esecuzione dei backup.  
  
```  
EXEC sp_pdw_add_network_credentials 'xxx.xxx.xxx.xxx', 'domain1\backupuser', '*****';  
```  
  
### <a name="b-remove-network-credentials-for-the-backup-location"></a>B. Rimuovere le credenziali di rete per il percorso di backup  
 L'esempio seguente illustra come rimuovere le credenziali per un utente di dominio da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
```  
EXEC sp_pdw_remove_network_credentials 'xxx.xxx.xxx.xxx';  
```  
  
### <a name="c-create-a-full-backup-of-a-user-database"></a>C. Creare un backup completo di un database utente  
 L'esempio seguente crea un backup completo del database utente Invoices. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] crea la directory Invoices2013 e salva i file di backup nella directory \\\10.192.63.147\backups\yearly\Invoices2013Full.  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="d-create-a-differential-backup-of-a-user-database"></a>D. Creare un backup differenziale di un database utente  
 L'esempio seguente crea un backup differenziale che include tutte le modifiche apportate dopo l'ultimo backup completo del database Invoices. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] crea la directory \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff in cui vengono archiviati i file. La descrizione 'Invoices 2013 differential backup' viene memorizzata con la descrizione dell'intestazione del backup.  
  
 Il backup differenziale viene eseguito correttamente solo se l'ultimo backup completo di Invoices è stato completato correttamente.  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH DIFFERENTIAL,   
    DESCRIPTION = 'Invoices 2013 differential backup';  
```  
  
### <a name="e-create-a-full-backup-of-the-master-database"></a>E. Creare un backup completo di un database master  
 L'esempio seguente crea un backup completo del database master e lo archivia nella directory '\\\10.192.63.147\backups\2013\daily\20130722\master'.  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master';  
```  
  
### <a name="f-create-a-backup-of-appliance-login-information"></a>F. Creare un backup delle informazioni di accesso dell'appliance  
 Il database master archivia le informazioni di accesso dell'appliance. Per eseguire il backup delle informazioni di accesso dell'appliance è necessario eseguire il backup del database master.  
  
 L'esempio seguente crea un backup completo del database master.  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master'  
WITH (   
    DESCRIPTION = 'Master Backup 20130722',  
    NAME = 'login-backup'  
)  
;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RESTORE DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
  
