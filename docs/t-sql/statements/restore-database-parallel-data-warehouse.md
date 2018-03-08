---
title: RIPRISTINARE il DATABASE (Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
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
ms.assetid: d915bfc1-e392-4a3a-9d94-08682cf3c864
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ba8aa12f38fce6ac00f88f0015008da25a59b88
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="restore-database-parallel-data-warehouse"></a>RIPRISTINO di DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Ripristina un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database utente da un backup di database per un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] accessorio. Il database viene ripristinato da un backup creato in precedenza per il [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] [BACKUP DATABASE &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/backup-database-parallel-data-warehouse.md) comando. Utilizzare il backup e ripristinare le operazioni per creare un piano di ripristino di emergenza o spostare i database da un dispositivo a un'altra.  
  
> [!NOTE]  
>  Ripristino master include informazioni di accesso dello strumento di ripristino. Per ripristinare il master, utilizzare il [ripristinare il Database master &#40; Transact-SQL &#41; ](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md) nella pagina di **Configuration Manager** strumento. Un amministratore con accesso al nodo di controllo è possibile eseguire questa operazione.  
  
 Per ulteriori informazioni su [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] backup dei database, vedere "Backup e ripristino" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Specifica per ripristinare un database utente a un database denominato *database_name*. Il database ripristinato può avere un nome diverso da quello del database di origine che è stato eseguito il backup. *database_name* non può già esistere come database sul dispositivo di destinazione. Per ulteriori informazioni su consentiti i nomi di database, vedere "Regole di denominazione degli oggetti" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Ripristino di un database utente viene ripristinato un backup completo del database e, facoltativamente, ripristina un backup differenziale al dispositivo. Un ripristino di un database utente include il ripristino gli utenti del database e i ruoli del database.  
  
 FROM DISK = '\\\\*UNC_path*\\*backup_directory*'  
 Il percorso di rete e la directory da cui [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] verranno ripristinati i file di backup. Ad esempio, FROM DISK = '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'.  
  
 *backup_directory*  
 Specifica il nome di una directory che contiene il backup completo o differenziale. Ad esempio, è possibile eseguire un'operazione RESTORE HEADERONLY in un backup completo o differenziale.  
  
 *full_backup_directory*  
 Specifica il nome di una directory che contiene il backup completo.  
  
 *differential_backup_directory*  
 Specifica il nome della directory che contiene il backup differenziale.  
  
-   La directory di backup e di percorso deve esistere e deve essere specificata come un nome completo percorso UNC universal naming convention (UNC).  
  
-   Il percorso della directory di backup non può essere un percorso locale e non può essere un percorso in uno qualsiasi del [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nodi dello strumento.  
  
-   La lunghezza massima del percorso UNC e il nome di directory di backup è 200 caratteri.  
  
-   Ai server host deve essere specificato come un indirizzo IP.  
  
 RESTORE HEADERONLY  
 Specifica per restituire solo le informazioni di intestazione per il backup di database di un utente. Tra gli altri campi, l'intestazione include la descrizione del backup e il nome del backup. Il nome del backup non è necessario essere lo stesso nome di directory in cui archiviare i file di backup.  
  
 Risultati di RESTORE HEADERONLY vengono creati dopo il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risultati RESTORE HEADERONLY. Il risultato ha più di 50 colonne, che non utilizzate dalla [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Per una descrizione delle colonne di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risultati RESTORE HEADERONLY, vedere [RESTORE HEADERONLY &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-headeronly-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **CREATE ANY DATABASE** autorizzazione.  
  
 Richiede un account di Windows che dispone dell'autorizzazione per accedere e leggere dalla directory di backup. È inoltre necessario archiviare il nome dell'account Windows e la password in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
1.  Per verificare le credenziali sono già presenti, utilizzare [sys.dm_pdw_network_credentials &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
2.  Per aggiungere o aggiornare le credenziali, utilizzare [sp_pdw_add_network_credentials &#40; SQL Data Warehouse &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
3.  Per rimuovere le credenziali da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare [sp_pdw_remove_network_credentials &#40; SQL Data Warehouse &#41; ](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
## <a name="error-handling"></a>Gestione degli errori  
 Il comando RESTORE DATABASE produce gli errori nelle condizioni seguenti:  
  
-   Il nome del database da ripristinare già esiste nel dispositivo di destinazione. Per evitare questo problema, scegliere un nome di database univoco oppure eliminare il database esistente prima di eseguire il ripristino.  
  
-   È un set di file di backup nella directory di backup non valido.  
  
-   Le autorizzazioni di accesso non sono sufficienti per ripristinare un database.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]non dispone delle autorizzazioni corrette per il percorso di rete in cui si trovano i file di backup.  
  
-   Il percorso di rete per la directory di backup non esiste o non è disponibile.  
  
-   Vi è spazio su disco insufficiente nel nodi di calcolo o nel nodo di controllo. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]non conferma l'esistenza di spazio su disco sufficiente nel dispositivo prima di avviare il ripristino. Pertanto, è possibile generare un errore di timeout di spazio su disco durante l'esecuzione dell'istruzione RESTORE DATABASE. Quando si verifica lo spazio su disco insufficiente, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] esegue il rollback del ripristino.  
  
-   Il dispositivo di destinazione a cui si intende ripristinare il database ha meno nodi di calcolo più il dispositivo di origine da cui è stato eseguito il backup database.  
  
-   Il ripristino di database viene tentato dall'interno di una transazione.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Registra l'esito positivo del ripristino di database. Prima di ripristinare un backup differenziale del database, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] verifica il ripristino completo del database è stata completata.  
  
 Dopo un ripristino, il database utente avrà il livello di compatibilità del database 120. Questo vale per tutti i database indipendentemente dal livello di compatibilità originale.  
  
 **Ripristino in un'applicazione con un numero maggiore di nodi di calcolo**  
Eseguire [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) dopo il ripristino di un database da un dispositivo più piccolo al più grande poiché aumenta la ridistribuzione del log delle transazioni.  

Ripristino di un backup in un'applicazione con un numero maggiore di nodi di calcolo aumenta la dimensione allocata database proporzionalmente al numero di nodi di calcolo.  
  
Ad esempio, quando un 60 GB database ripristino da un dispositivo 2 nodi (30 GB per ogni nodo) in un'applicazione di 6 nodi, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] crea un database di 180 GB (6 nodi con 30 GB per ogni nodo) nel dispositivo 6-nodo. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]inizialmente il database viene ripristinato a 2 nodi in modo che corrisponda alla configurazione dell'origine e quindi vengono ridistribuiti i dati da tutti i nodi di 6.  
  
 Dopo la ridistribuzione ogni nodo di calcolo contiene meno dati effettivi e più spazio rispetto a ogni nodo di calcolo nel dispositivo di origine più piccolo. Utilizzare lo spazio aggiuntivo per aggiungere ulteriori dati al database. Se le dimensioni del database ripristinato sono superiore al necessario, è possibile utilizzare [ALTER DATABASE &#40; Parallel Data Warehouse &#41; ](../../t-sql/statements/alter-database-parallel-data-warehouse.md) per compattare le dimensioni dei file di database.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Per queste limitazioni e restrizioni, il dispositivo di origine è il dispositivo da cui è stato creato il backup del database e il dispositivo di destinazione è il dispositivo a cui verrà ripristinato il database.  
  
 Ripristino di un database non vengono rigenerate automaticamente le statistiche.  
  
 Istruzione di un solo RESTORE DATABASE o BACKUP del DATABASE può essere eseguiti nel dispositivo in qualsiasi momento. Se più istruzioni backup e ripristino vengono eseguite simultaneamente, il dispositivo verrà inserirli in una coda ed elaborarle uno alla volta.  
  
 È possibile solo ripristinare un backup del database per un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] dispositivo di destinazione con lo stesso numero o più nodi di calcolo rispetto del dispositivo di origine. Il dispositivo di destinazione non può avere un minor numero di nodi di calcolo più il dispositivo di origine.  
  
 È possibile ripristinare un backup creato su un dispositivo che dispone di hardware di SQL Server 2012 PDW in un'applicazione che dispone di hardware di SQL Server 2008 R2. Ciò vale anche se il dispositivo è in esecuzione il software di SQL Server 2012 PDW e originariamente acquistato con l'hardware di SQL Server 2008 R2 PDW.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Accetta un blocco esclusivo sull'oggetto di DATABASE.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-restore-examples"></a>A. Esempi di ripristino semplici  
 Nell'esempio seguente consente di ripristinare un backup completo per il `SalesInvoices2013` database. Cui sono archiviati i file di backup di \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full directory. Il database SalesInvoices2013 non può già esistere nel dispositivo di destinazione o questo comando avrà esito negativo con un errore.  
  
```  
RESTORE DATABASE SalesInvoices2013  
FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="b-restore-a-full-and-differential-backup"></a>B. Ripristinare un backup completo e differenziale  
 Nell'esempio seguente ripristina una procedura completa, quindi un backup differenziale di database SalesInvoices2013  
  
 Il backup completo del database viene ripristinato dal backup completo che viene archiviato nel '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full' directory. Se il ripristino viene completato correttamente, viene ripristinato il backup differenziale per il database SalesInvoices2013.  Cui è archiviato il backup differenziale di '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff' directory.  
  
```  
RESTORE DATABASE SalesInvoices2013  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH BASE = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
  
```  
  
### <a name="c-restoring-the-backup-header"></a>C. Ripristino dell'intestazione del backup  
 In questo esempio consente di ripristinare le informazioni di intestazione per il backup di database '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'. I risultati del comando in una riga di informazioni per il backup Invoices2013Full.  
  
```  
RESTORE HEADERONLY  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
```  
  
 È possibile utilizzare le informazioni di intestazione per controllare il contenuto di un backup o per assicurarsi che il dispositivo di destinazione ripristino sia compatibile con il dispositivo di backup di origine prima di tentare di ripristinare il backup.  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP DATABASE &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md)  
  
  
