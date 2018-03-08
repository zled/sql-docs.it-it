---
title: BACKUP DATABASE (Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c8d465-b36b-4727-b9f3-368e98677c64
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc87423b3444daf6d44f590c283b52ce948da193
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="backup-database-parallel-data-warehouse"></a>BACKUP DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Crea una copia di backup di un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database e archiviato il backup di disattivare il dispositivo in un percorso di rete specificato dall'utente. Utilizzare questa istruzione con [Ripristina DATABASE &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/restore-database-parallel-data-warehouse.md) per il ripristino di emergenza o copiare un database da un dispositivo a un'altra.  
  
 **Prima di iniziare**, vedere "Acquisire e configurare un Backup del Server" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Esistono due tipi di backup in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Oggetto *backup completo del database* è un backup di un intero [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database. Oggetto *backup differenziale del database* include solo le modifiche apportate dopo l'ultimo backup completo. Un backup di un database utente include gli utenti del database e i ruoli del database. Un backup del database master include gli account di accesso.  
  
 Per ulteriori informazioni su [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] backup dei database, vedere "Backup e ripristino" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Il nome del database in cui creare un backup. Il database può essere il database master o un database utente.  
  
 SUL disco = '\\\\*UNC_path*\\*backup_directory*'  
 Il percorso di rete e la directory a cui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] verranno scritti i file di backup. Ad esempio, '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'.  
  
-   Il percorso del nome di directory di backup deve essere già presente e deve essere specificato come un nome completo percorso UNC universal naming convention (UNC).  
  
-   La directory di backup, *backup_directory*, non deve essere presente prima di eseguire il comando di backup. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]verrà creata la directory di backup.  
  
-   Il percorso della directory di backup non può essere un percorso locale e non può essere un percorso in uno qualsiasi del [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nodi dello strumento.  
  
-   La lunghezza massima del percorso UNC e il nome di directory di backup è 200 caratteri.  
  
-   Ai server host deve essere specificato come un indirizzo IP.  È possibile specificare, come il nome host o server.  
  
 Descrizione = **'***testo***'**  
 Specifica una descrizione testuale del backup. La lunghezza massima del testo è di 255 caratteri.  
  
 La descrizione viene archiviata nei metadati e verrà visualizzata quando l'intestazione del backup viene ripristinato con RESTORE HEADERONLY.  
  
 NOME = **'***Name backup***'**  
 Specifica il nome del backup. Il nome del backup può essere diverso dal nome del database.  
  
-   I nomi possono essere composti da un massimo di 128 caratteri.  
  
-   Non è possibile includere un percorso.  
  
-   Deve iniziare con una lettera o un numero di caratteri o un carattere di sottolineatura (_). Caratteri speciali consentiti sono il carattere di sottolineatura (\_), trattino (-) o spazio (). I nomi di backup non possono terminare con un carattere di spazio.  
  
-   L'istruzione avrà esito negativo se *backup_name* esiste già nel percorso specificato.  
  
 Questo nome viene archiviato nei metadati e verrà visualizzato quando l'intestazione del backup viene ripristinato con RESTORE HEADERONLY.  
  
 DIFFERENTIAL  
 Consente di eseguire un backup differenziale di un database utente. Se omesso, il valore predefinito è un backup completo del database. Il nome del backup differenziale non deve necessariamente corrispondere al nome del backup completo. Per tenere traccia dei backup differenziale e il relativo backup completo corrispondente, utilizzare lo stesso nome con 'full' o 'diff' aggiunto.  
  
 Esempio:  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerFull';`  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerDiff' WITH DIFFERENTIAL;`  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **BACKUP DATABASE** autorizzazione o l'appartenenza di **db_backupoperator** ruolo predefinito del database. Il database master non può essere sottoposti a backup, ma da un utente regolare che è stato aggiunto per il **db_backupoperator** ruolo predefinito del database. Solo essere eseguito il backup del database master da **sa**, l'amministratore dell'infrastruttura o i membri del **sysadmin** ruolo predefinito del server.  
  
 Richiede un account di Windows che dispone dell'autorizzazione per accedere, creare e scrivere nella directory di backup. È inoltre necessario archiviare il nome dell'account Windows e la password in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Per aggiungere le credenziali di rete per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il [sp_pdw_add_network_credentials &#40; SQL Data Warehouse &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) stored procedure.  
  
 Per ulteriori informazioni sulla gestione delle credenziali in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], vedere il [sicurezza](#Security) sezione.  
  
## <a name="error-handling"></a>Gestione degli errori  
 Errori di DATABASE di BACKUP nelle condizioni seguenti:  
  
-   Le autorizzazioni utente non sono sufficienti per eseguire un backup.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]non dispone delle autorizzazioni corrette per il percorso di rete in cui verrà archiviato il backup.  
  
-   Il database non esiste.  
  
-   La directory di destinazione esiste già nella condivisione di rete.  
  
-   La condivisione di rete di destinazione non è disponibile.  
  
-   La condivisione di rete di destinazione non dispone di sufficiente spazio per il backup. Il comando di DATABASE di BACKUP non conferma l'esistenza di spazio su disco sufficiente prima di avviare il backup, che consente di generare un errore di timeout di spazio su disco durante l'esecuzione del BACKUP del DATABASE. Quando si verifica lo spazio su disco insufficiente, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] rollback del comando BACKUP DATABASE. Per ridurre le dimensioni del database, eseguire [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)  
  
-   Tentativo di avviare un backup in una transazione.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Prima di eseguire un backup del database, utilizzare [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) ridurre le dimensioni del database. 
 
 Oggetto [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] backup viene archiviato come un set di più file all'interno della stessa directory.  
  
 Un backup differenziale è in genere richiede meno tempo rispetto a un backup completo e può essere eseguito più di frequente. Quando più copie di backup differenziale si basano su stesso backup completo, ogni backup differenziale include tutte le modifiche nel backup differenziale precedente.  
  
 Se si annulla un comando BACKUP, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] rimuoverà la directory di destinazione e i file creati per il backup. Se [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] perde la connettività di rete alla condivisione, non è possibile completare il rollback.  
  
 Backup completi e differenziali vengono archiviati in directory distinte. Convenzioni di denominazione non vengono applicate per la specifica di un backup completo e un backup differenziale raggruppati insieme. È possibile rilevare questo tramite le convenzioni di denominazione. In alternativa, è possibile rilevare questa l'opzione per aggiungere una descrizione con descrizione, quindi utilizzando l'istruzione RESTORE HEADERONLY per recuperare la descrizione.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 È possibile eseguire un backup differenziale del database master. Sono supportati solo i backup completi del database master.  
  
 I file di backup vengono archiviati in un formato adatto solo per il ripristino del backup per un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] dispositivo usando il [Ripristina DATABASE &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/restore-database-parallel-data-warehouse.md) istruzione.  
  
 Il backup con l'istruzione BACKUP DATABASE non può essere utilizzato per trasferire le informazioni utente o di dati in SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. A tale scopo, è possibile utilizzare la funzionalità di copia della tabella remota. Per ulteriori informazioni, vedere "Copia della tabella remota" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tecnologia di backup e ripristino di database di backup. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]opzioni di backup sono preconfigurate per utilizzare la compressione dei backup. È possibile impostare le opzioni di backup, ad esempio la compressione, checksum, dimensione del blocco e il numero di buffer.  
  
 Solo un backup del database o ripristino possa eseguire nel dispositivo in qualsiasi momento. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]verranno messi in coda i comandi backup o ripristino fino al corrente backup o il comando restore è stata completata.  
  
 Il dispositivo di destinazione per il ripristino del backup deve avere almeno un numero di nodi di calcolo del dispositivo di origine. La destinazione può presentare più nodi di calcolo più il dispositivo di origine, ma non può avere meno nodi di calcolo.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]non tiene traccia del percorso e i nomi di backup poiché i backup vengono archiviati disattivato il dispositivo.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]registrare l'esito positivo o negativo dei backup del database.  
  
 Un backup differenziale è consentito solo se l'ultimo backup completo è stata completata correttamente. Si supponga, ad esempio, che il lunedì si crea un backup completo del database Sales e completamento corretto del backup. Quindi martedì creare un backup completo del database Sales e si verifica un errore. Dopo questo errore, è quindi possibile creare un backup differenziale basato su backup completo di lunedì. È innanzitutto necessario creare un backup completo riuscito prima di creare un backup differenziale.  
  
## <a name="metadata"></a>Metadati  
 Queste viste a gestione dinamica contengono informazioni su tutti i backup, ripristino e operazioni di caricamento. Le informazioni persiste tra i riavvii del sistema.  
  
-   [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md)  
  
## <a name="performance"></a>restazioni  
 Per eseguire un backup, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] esegue il primo backup i metadati e quindi si esegue il backup dei dati di database archiviati nei nodi di calcolo parallelo. La directory di backup, i dati vengono copiati direttamente da ogni nodi di calcolo. Per ottenere prestazioni ottimali per lo spostamento dei dati dei nodi di calcolo per la directory di backup, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] controlla il numero di nodi di calcolo che sono la copia dei dati contemporaneamente.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco ExclusiveUpdate sull'oggetto di DATABASE.  
  
##  <a name="Security"></a> Sicurezza  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]backup non vengono archiviati nel dispositivo. Pertanto, il team IT è responsabile per la gestione di tutti gli aspetti della sicurezza del backup. Ad esempio, sono inclusi gestione la sicurezza dei dati di backup, la sicurezza del server utilizzato per archiviare i backup e la sicurezza dell'infrastruttura di rete che si connette il server di backup per il [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] dello strumento.  
  
 **Gestire le credenziali di rete**  
  
 Accesso alla rete per la directory di backup è basato su standard Windows condivisione file security. Prima di eseguire un backup, è necessario creare o designare un account di Windows che verrà utilizzato per l'autenticazione [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] alla directory di backup. Questo account di windows deve disporre dell'autorizzazione per accedere, creare e scrivere nella directory di backup.  
  
> [!IMPORTANT]  
>  Per ridurre i rischi di sicurezza con i dati, è consigliabile che definisce un account di Windows solo scopo di operazioni di backup e di operazioni di ripristino. Consente questo account dispone delle autorizzazioni per il percorso di backup e non altrove.  
  
 È necessario archiviare il nome utente e password in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] eseguendo il [sp_pdw_add_network_credentials &#40; SQL Data Warehouse &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) stored procedure. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Usa Gestione credenziali di Windows per archiviare e crittografare i nomi utente e password nel nodo di controllo e i nodi di calcolo. Le credenziali non vengono eseguito il backup con il comando BACKUP DATABASE.  
  
 Per rimuovere le credenziali di rete da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], vedere [sp_pdw_remove_network_credentials &#40; SQL Data Warehouse &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
 Per elencare tutte le credenziali di rete archiviati in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il [sys.dm_pdw_network_credentials &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) vista a gestione dinamica.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-add-network-credentials-for-the-backup-location"></a>A. Aggiungere le credenziali di rete per il percorso di backup  
 Per creare un backup, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] necessario disporre dell'autorizzazione di lettura/scrittura alla directory di backup. Nell'esempio seguente viene illustrato come aggiungere le credenziali per un utente. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]verrà memorizzare queste credenziali e utilizzarle per backup e le operazioni di ripristino.  
  
> [!IMPORTANT]  
>  Per motivi di sicurezza, è consigliabile creare un account di dominio solo scopo di eseguire i backup.  
  
```  
EXEC sp_pdw_add_network_credentials 'xxx.xxx.xxx.xxx', 'domain1\backupuser', '*****';  
```  
  
### <a name="b-remove-network-credentials-for-the-backup-location"></a>B. Rimuovere le credenziali di rete per il percorso di backup  
 Nell'esempio seguente viene illustrato come rimuovere le credenziali per un utente di dominio da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
```  
EXEC sp_pdw_remove_network_credentials 'xxx.xxx.xxx.xxx';  
```  
  
### <a name="c-create-a-full-backup-of-a-user-database"></a>C. Creare un backup completo di un database utente  
 L'esempio seguente crea un backup completo del database utente fatture. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]verrà creata la directory Invoices2013 e salverà i file di backup per il \\\10.192.63.147\backups\yearly\Invoices2013Full directory.  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="d-create-a-differential-backup-of-a-user-database"></a>D. Creare un backup differenziale di un database utente  
 L'esempio seguente crea un backup differenziale, che include tutte le modifiche apportate dopo l'ultimo backup completo del database le fatture. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]verrà creato il \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff directory a cui verranno archiviati i file. La descrizione 'backup differenziale 2013 fatture' verrà archiviata con le informazioni di intestazione per il backup.  
  
 Il backup differenziale verrà eseguito correttamente solo se l'ultimo backup completo di fatture è stata completata correttamente.  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH DIFFERENTIAL,   
    DESCRIPTION = 'Invoices 2013 differential backup';  
```  
  
### <a name="e-create-a-full-backup-of-the-master-database"></a>E. Creare un backup completo del database master  
 Nell'esempio seguente crea un backup completo del database master e lo archivia nella directory '\\\10.192.63.147\backups\2013\daily\20130722\master'.  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master';  
```  
  
### <a name="f-create-a-backup-of-appliance-login-information"></a>F. Creare un backup delle informazioni di accesso di dispositivo.  
 Il database master archivia le informazioni di accesso del dispositivo. Per le informazioni di accesso del dispositivo di backup è necessario backup master.  
  
 Nell'esempio seguente viene creato un backup completo del database master.  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master'  
WITH (   
    DESCRIPTION = 'Master Backup 20130722',  
    NAME = 'login-backup'  
)  
;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristina DATABASE &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
  
