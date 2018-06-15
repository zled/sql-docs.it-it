---
title: RESTORE DATABASE (Parallel Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d915bfc1-e392-4a3a-9d94-08682cf3c864
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed7e6aeb0630a20ee39d512fc17dfe24040737f2
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33702515"
---
# <a name="restore-database-parallel-data-warehouse"></a>RESTORE DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Ripristina un database utente [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] da un backup di database a un'appliance [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Il database viene ripristinato da un backup creato in precedenza dal comando [BACKUP DATABASE &#40;Parallel Data Warehouse&#41; ](../../t-sql/statements/backup-database-parallel-data-warehouse.md) di [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Usare le operazioni di backup e ripristino per creare un piano di ripristino di emergenza o per spostare i database da un'appliance a un'altra.  
  
> [!NOTE]  
>  Il ripristino del database master include il ripristino delle informazioni di accesso all'appliance. Per ripristinare il database master, usare la pagina [Ripristinare il database master &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md) nello strumento **Configuration Manager**. Questa operazione può essere eseguita da un amministratore con accesso al nodo di controllo.  
  
 Per altre informazioni sui backup di database [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], vedere la sezione relativa a backup e ripristino nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      Restore the master database  
-- Use the Configuration Manager tool.  
  
Restore a full user database backup.  
RESTORE DATABASE database_name   
    FROM DISK = '\\UNC_path\full_backup_directory'  
[;]  
  
Restore a full user database backup and then a differential backup.  
RESTORE DATABASE database_name  
    FROM DISK = '\\UNC_path\differential_backup_directory'   
    WITH [ ( ] BASE = '\\UNC_path\full_backup_directory' [ ) ]   
[;]  
  
Restore header information for a full or differential user database backup.  
RESTORE HEADERONLY   
    FROM DISK = '\\UNC_path\backup_directory'  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 RESTORE DATABASE *database_name*  
 Specifica il ripristino di un database utente in un database denominato *database_name*. Il database ripristinato può avere un nome diverso da quello del database di origine di cui è stato eseguito il backup. *database_name* non può essere un database già esistente nell'appliance di destinazione. Per altri dettagli sui nomi consentiti per i database, vedere la sezione relativa alle regole di denominazione degli oggetti nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Il ripristino di un database utente implica il ripristino di un backup completo del database e, facoltativamente, di un backup differenziale nell'appliance. Il ripristino di un database utente include il ripristino degli utenti e dei ruoli del database.  
  
 FROM DISK = '\\\\*UNC_path*\\*backup_directory*'  
 Il percorso di rete e la directory da cui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ripristina i file di backup. Ad esempio, FROM DISK = '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'.  
  
 *backup_directory*  
 Specifica il nome della directory che contiene il backup completo o differenziale. È ad esempio possibile eseguire un'operazione RESTORE HEADERONLY per un backup completo o differenziale.  
  
 *full_backup_directory*  
 Specifica il nome della directory che contiene il backup completo.  
  
 *differential_backup_directory*  
 Specifica il nome della directory che contiene il backup differenziale.  
  
-   Il percorso e la directory di backup devono essere già esistenti e devono essere specificati sotto forma di percorso UNC completo.  
  
-   Il percorso della directory di backup non può essere un percorso locale e non può essere il percorso di uno dei nodi di appliance [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
-   La lunghezza massima del percorso UNC e del nome della directory di backup è di 200 caratteri.  
  
-   Il server o l'host deve essere specificato come indirizzo IP.  
  
 RESTORE HEADERONLY  
 Specifica la restituzione sollo delle informazioni di intestazione per un backup del database utente. Tra gli altri campi, l'intestazione include la descrizione in formato testo del backup e il nome del backup stesso. Il nome del backup non deve necessariamente corrispondere al nome della directory in cui sono archiviati i file di backup.  
  
 I risultati di RESTORE HEADERONLY seguono il modello dei risultati di RESTORE HEADERONLY di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il risultato ha più di 50 colonne, che non vengono usate tutte da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Per una descrizione delle colonne nei risultati di RESTORE HEADERONLY di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione **CREATE ANY DATABASE**.  
  
 È necessario un account di Windows con l'autorizzazione di accesso e lettura per la directory di backup. È anche necessario archiviare il nome e la password dell'account di Windows in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
1.  Per verificare le credenziali già presenti, usare [sys.dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
2.  Per aggiungere credenziali o aggiornare quelle esistenti, usare [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
3.  Per rimuovere credenziali da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare [sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
## <a name="error-handling"></a>Gestione degli errori  
 Il comando RESTORE DATABASE genera errori nelle condizioni seguenti:  
  
-   Il nome del database da ripristinare esiste già nell'appliance di destinazione. Per evitare questo problema, scegliere un nome di database univoco oppure rilasciare il database esistente prima di eseguire il ripristino.  
  
-   Nella directory di backup è presente un set di file di backup non valido.  
  
-   Le autorizzazioni di accesso non sono sufficienti per il ripristino di un database.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non ha le autorizzazioni corrette per il percorso di rete in cui si trovano i file di backup.  
  
-   Il percorso di rete della directory di backup non esiste o non è disponibile.  
  
-   Lo spazio su disco è insufficiente nei nodi di calcolo o nel nodo di controllo. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non conferma la disponibilità di spazio su disco sufficiente nell'appliance prima dell'avvio del ripristino. È quindi possibile che venga generato un errore di spazio su disco insufficiente durante l'esecuzione dell'istruzione RESTORE DATABASE. Quando si verifica l'errore di spazio su disco insufficiente, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] esegue il rollback del ripristino.  
  
-   L'appliance di destinazione in cui il database è in corso di ripristino ha un numero di nodi di calcolo inferiore a quello dell'appliance di origine da cui è stato eseguito il backup del database.  
  
-   Viene tentato il ripristino del database dall'interno di una transazione.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] tiene traccia dell'esito positivo del ripristino dei database. Prima di ripristinare un backup differenziale del database, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] verifica che il ripristino completo del database sia stato completato.  
  
 Dopo un ripristino, il database utente ha un livello di compatibilità pari a 120. Questo vale per tutti i database, indipendentemente dal livello di compatibilità originale.  
  
 **Ripristino in un'appliance con un numero maggiore di nodi di calcolo**  
Eseguire [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) dopo il ripristino di un database da un'appliance più piccola a una più grande, poiché la ridistribuzione aumenta le dimensioni del log delle transazioni.  

Il ripristino di un backup in un'appliance con un numero maggiore di nodi di calcolo aumenta la dimensione allocata al database proporzionalmente al numero di nodi di calcolo.  
  
Se ad esempio si ripristina un database da 60 GB da un'appliance da 2 nodi (30 GB per nodo) in un'appliance da 6 nodi, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] crea un database di 180 GB (6 nodi con 30 GB per nodo) nell'appliance da 6 nodi. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] inizialmente ripristina il database in 2 nodi, in modo che corrisponda alla configurazione dell'origine, e quindi ridistribuisce i dati in tutti i 6 nodi.  
  
 Dopo la ridistribuzione, ogni nodo di calcolo contiene meno dati effettivi e più spazio disponibile rispetto a ogni nodo di calcolo nell'appliance di origine di dimensioni inferiori. Usare lo spazio aggiuntivo per l'aggiunta di altri dati al database. Se le dimensioni del database ripristinato sono maggiori del necessario, è possibile usare [ALTER DATABASE &#40;Parallel Data Warehouse&#41; ](../../t-sql/statements/alter-database-parallel-data-warehouse.md) per compattare le dimensioni dei file del database stesso.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 In questa sezione, per appliance di origine si intende l'appliance da cui è stato creato il backup del database e per appliance di destinazione si intende l'appliance in cui viene ripristinato il database.  
  
 Il ripristino di un database non implica la rigenerazione automatica delle statistiche.  
  
 In qualsiasi momento, nell'appliance può essere in esecuzione una sola istruzione RESTORE DATABASE o BACKUP DATABASE. Se vengono inviate contemporaneamente più istruzioni di backup e ripristino, l'appliance le inserisce in una coda e le elabora una alla volta.  
  
 È possibile ripristinare un backup del database solo in un'appliance di destinazione [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] con un numero di nodi di calcolo uguale o maggiore a quello dell'appliance di origine. L'appliance di destinazione non può avere un numero di nodi di calcolo minore dell'appliance di origine.  
  
 Non è possibile ripristinare un backup creato in un'appliance con hardware SQL Server 2012 PDW in un'appliance con hardware SQL Server 2008 R2. Ciò vale anche se l'appliance è stata originariamente acquistata con hardware SQL Server 2008 R2 PDW e ora esegue software SQL Server 2012 PDW.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco esclusivo per l'oggetto DATABASE.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-restore-examples"></a>A. Esempi di RESTORE semplici  
 L'esempio seguente ripristina un backup completo nel database `SalesInvoices2013`. I file di backup sono archiviati nella directory \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full. Nell'appliance di destinazione non può essere già presente un database SalesInvoices2013. In caso contrario, questo comando avrà esito negativo e genererà un errore.  
  
```  
RESTORE DATABASE SalesInvoices2013  
FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="b-restore-a-full-and-differential-backup"></a>B. Ripristinare un backup completo e un backup differenziale  
 L'esempio seguente ripristina un backup completo e quindi un backup differenziale nel database SalesInvoices2013  
  
 Il backup completo del database viene ripristinato usando il backup completo archiviato nella directory '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'. Se il ripristino viene completato correttamente, viene ripristinato il backup differenziale nel database SalesInvoices2013.  Il backup differenziale è archiviato nella directory \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff.  
  
```  
RESTORE DATABASE SalesInvoices2013  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH BASE = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
  
```  
  
### <a name="c-restoring-the-backup-header"></a>C. Ripristino dell'intestazione del backup  
 Questo esempio ripristina le informazioni di intestazione per il backup del database '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'. Il comando ha come risultato una riga di informazioni per il backup Invoices2013Full.  
  
```  
RESTORE HEADERONLY  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
```  
  
 È possibile usare le informazioni di intestazione per controllare il contenuto di un backup o per assicurarsi che l'appliance di ripristino di destinazione sia compatibile con l'appliance di backup di origine prima di tentare il ripristino del backup.  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md)  
  
  
