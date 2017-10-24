---
title: RESTORE HEADERONLY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/07/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HEADERONLY
- RESTORE HEADERONLY
- RESTORE_HEADERONLY_TSQL
- HEADERONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup sets [SQL Server], header information
- headers [SQL Server]
- RESTORE HEADERONLY statement
- backup header information [SQL Server]
ms.assetid: 4b88e98c-49c4-4388-ab0e-476cc956977c
caps.latest.revision: 95
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 694c77c3d59b5565e6c5b25eaf946e9ebaa0e22f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---headeronly-transact-sql"></a>Istruzioni - RESTORE HEADERONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di risultati contenente tutte le informazioni sull'intestazione del backup per tutti i set di backup di un dispositivo specifico in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per una descrizione degli argomenti, vedere [argomenti RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RESTORE HEADERONLY   
FROM <backup_device>   
[ WITH   
 {  
--Backup Set Options  
   FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 Per una descrizione degli argomenti di RESTORE HEADERONLY, vedere [argomenti RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Set di risultati  
 Per ogni backup nel dispositivo specificato, il server invia una riga di informazioni sull'intestazione con le colonne riportate di seguito.  
  
> [!NOTE]  
>  RESTORE HEADERONLY esamina tutti i set di backup nei supporti. Pertanto, se si utilizzano unità nastro ad alta capacità, la generazione di questo set di risultati può richiedere tempo. Per ottenere una panoramica dei supporti senza visualizzare informazioni per ogni set di backup, utilizzare RESTORE LABELONLY oppure specificare FILE  **=**  *backup_set_file_number*.  
  
> [!NOTE]  
>  A causa della natura del [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format, è possibile set di backup di altri programmi software a occupare spazio sullo stesso supporto come [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di backup. Il set di risultati restituito da RESTORE HEADERONLY include una riga per ognuno degli altri set di backup.  
  
|Nome colonna|Tipo di dati|Descrizione per i set di backup SQL Server|  
|-----------------|---------------|--------------------------------------------|  
|**Nomebackup**|**nvarchar (128)**|Nome del set di backup.|  
|**BackupDescription**|**nvarchar(255)**|Descrizione del set di backup.|  
|**BackupType**|**smallint**|Tipo di backup:<br /><br /> **1** = database<br /><br /> **2** = log delle transazioni<br /><br /> **4** = file<br /><br /> **5** = database differenziale<br /><br /> **6** = file differenziale<br /><br /> **7** = parziale<br /><br /> **8** = parziale differenziale|  
|**ExpirationDate**|**datetime**|Data di scadenza del set di backup.|  
|**Compresso**|**BYTE(1)**|Specifica se il set di backup viene compresso utilizzando la compressione software:<br /><br /> **0** = No<br /><br /> **1** = Sì|  
|**Posizione**|**smallint**|Posizione del set di backup nel volume (da utilizzare con l'opzione FILE =).|  
|**DeviceType**|**tinyint**|Numero corrispondente a tipo di dispositivo utilizzato per l'operazione di backup.<br /><br /> Disco:<br /><br /> **2** = logica<br /><br /> **102** = fisico<br /><br /> Nastro:<br /><br /> **5** = logica<br /><br /> **105** = fisico<br /><br /> Dispositivo virtuale:<br /><br /> **7** = logica<br /><br /> **107** = fisico<br /><br /> Nomi dei dispositivi logici e i numeri presenti **backup_devices**; per ulteriori informazioni, vedere [backup_devices &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md).|  
|**UserName**|**nvarchar (128)**|Nome dell'utente che ha eseguito l'operazione di backup.|  
|**ServerName**|**nvarchar (128)**|Nome del server che ha scritto il set di backup.|  
|**DatabaseName**|**nvarchar (128)**|Nome del database di cui è stato eseguito il backup.|  
|**DatabaseVersion**|**int**|Versione del database da cui è stato creato il backup.|  
|**DatabaseCreationDate**|**datetime**|Data e ora di creazione del database.|  
|**BackupSize**|**Numeric(20,0)**|Dimensioni del backup in byte.|  
|**FirstLSN**|**Numeric(25,0)**|Numero di sequenza del file di log (LSN) del primo record di log nel set di backup.|  
|**LastLSN**|**Numeric(25,0)**|Numero di sequenza del file di log (LSN) del record di log successivo dopo il set di backup.|  
|**CheckpointLSN**|**Numeric(25,0)**|Numero di sequenza del file di log del checkpoint più recente al momento della creazione del backup.|  
|**DatabaseBackupLSN**|**Numeric(25,0)**|Numero di sequenza del file di log dell'operazione più recente di backup completo del database.<br /><br /> **DatabaseBackupLSN** è il "inizio del checkpoint" che viene attivato all'avvio del backup. Questo numero LSN coincide con **FirstLSN** se il backup viene eseguito quando il database è inattivo e non è configurata la replica.|  
|**BackupStartDate**|**datetime**|Data e ora di inizio dell'operazione di backup.|  
|**BackupFinishDate**|**datetime**|Data e ora di fine dell'operazione di backup.|  
|**SortOrder**|**smallint**|Tipo di ordinamento del server. Questa colonna è valida solo per i backup dei database. Disponibile per compatibilità con le versioni precedenti.|  
|**CodePage**|**smallint**|Tabella codici del server o set di caratteri utilizzato dal server.|  
|**UnicodeLocaleId**|**int**|Opzione di configurazione dell'ID delle impostazioni locali Unicode del server utilizzata per l'ordinamento dei dati di tipo carattere Unicode. Disponibile per compatibilità con le versioni precedenti.|  
|**UnicodeComparisonStyle**|**int**|Opzione di configurazione dello stile di confronto Unicode del server che consente di controllare ulteriormente l'ordinamento dei dati Unicode. Disponibile per compatibilità con le versioni precedenti.|  
|**Livello di compatibilità**|**tinyint**|Impostazione del livello di compatibilità del database da cui è stato creato il backup.|  
|**SoftwareVendorId**|**int**|Numero di identificazione del produttore del software. Per SQL Server, questo numero è **4608** (o esadecimale **0x1200**).|  
|**SoftwareVersionMajor**|**int**|Numero di versione principale del server in cui è stato creato il set di backup.|  
|**SoftwareVersionMinor**|**int**|Numero di versione secondario del server in cui è stato creato il set di backup.|  
|**SoftwareVersionBuild**|**int**|Numero di build del server in cui è stato creato il set di backup.|  
|**MachineName**|**nvarchar (128)**|Nome del computer in cui è stato eseguito il backup.|  
|**Flag**|**int**|Singoli flag di bit significati se impostato su **1**:<br /><br /> **1** = log di backup contiene operazioni bulk registrate.<br /><br /> **2** = backup snapshot.<br /><br /> **4** = database era di sola lettura quando il backup.<br /><br /> **8** = il database era in modalità utente singolo quando il backup.<br /><br /> **16** = backup contiene checksum di backup.<br /><br /> **32** = database era danneggiato al momento del backup, ma l'operazione di backup è stato richiesto di continuare nonostante gli errori.<br /><br /> **64** = backup della parte finale del log.<br /><br /> **128** = backup della parte finale del log con metadati incompleti.<br /><br /> **256** = backup della parte finale del log con NORECOVERY.<br /><br /> **Importante:** si consiglia invece di **flag** utilizzare le singole colonne booleane (elencate di seguito a partire da **HasBulkLoggedData** e terminando con  **IsCopyOnly**).|  
|**BindingID**|**uniqueidentifier**|ID di associazione per il database. Corrisponde a **sys.database_recovery_status***database_guid**. In caso di ripristino di un database viene assegnato un nuovo valore. Vedere anche **FamilyGUID** (sotto).|  
|**RecoveryForkID**|**uniqueidentifier**|ID per il fork di recupero finale. Questa colonna corrisponde a **last_recovery_fork_guid** nel [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) tabella.<br /><br /> Per i backup di dati, **RecoveryForkID** è uguale a **FirstRecoveryForkID**.|  
|**Confronto**|**nvarchar (128)**|Regole di confronto utilizzate dal database.|  
|**FamilyGUID**|**uniqueidentifier**|ID del database originale al momento della creazione. Il valore non cambia quando il database viene ripristinato.|  
|**HasBulkLoggedData**|**bit**|**1** = backup del log contenente operazioni bulk registrate.|  
|**IsSnapshot**|**bit**|**1** = backup snapshot.|  
|**IsReadOnly**|**bit**|**1** = database era di sola lettura quando il backup.|  
|**IsSingleUser**|**bit**|**1** = il database era utente singolo quando il backup.|  
|**HasBackupChecksums**|**bit**|**1** = backup contiene checksum di backup.|  
|**IsDamaged**|**bit**|**1** = database era danneggiato al momento del backup, ma l'operazione di backup è stato richiesto di continuare nonostante gli errori.|  
|**BeginsLogChain**|**bit**|**1** = questo è il primo di una catena continua di backup del log. Una catena di log inizia con il primo backup del log eseguito dopo la creazione del database oppure quando si passa dal modello di recupero con registrazione semplice al modello di recupero con registrazione completa o al modello di recupero con registrazione minima delle operazioni bulk.|  
|**HasIncompleteMetaData**|**bit**|**1** = backup della parte finale del log con metadati incompleti.<br /><br /> Per informazioni sui backup della parte finale del log con metadati di backup incompleti, vedere [backup della parte finale del Log &#40; SQL Server &#41; ](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).|  
|**IsForceOffline**|**bit**|**1** = backup eseguito con NORECOVERY; il database è stato portato offline dal backup.|  
|**IsCopyOnly**|**bit**|**1** = un sola copia di backup.<br /><br /> Un backup di sola copia non ha alcun effetto sulle procedure di backup e ripristino generali per il database. Per altre informazioni, vedere [Backup di sola copia &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).|  
|**FirstRecoveryForkID**|**uniqueidentifier**|ID per il fork di recupero iniziale. Questa colonna corrisponde a **first_recovery_fork_guid** nel [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) tabella.<br /><br /> Per i backup di dati, **FirstRecoveryForkID** è uguale a **RecoveryForkID**.|  
|**ForkPointLSN**|**Numeric(25,0)** NULL|Se **FirstRecoveryForkID** non è uguale a **RecoveryForkID**, il numero di sequenza del log del punto di fork. Negli altri casi il valore è NULL.|  
|**RecoveryModel**|**nvarchar(60)**|Modello di recupero del database. I possibili valori sono i seguenti:<br /><br /> FULL<br /><br /> BULK-LOGGED<br /><br /> SIMPLE|  
|**DifferentialBaseLSN**|**Numeric(25,0)** NULL|Per un backup differenziale basato su singolo, il valore è uguale al **FirstLSN** della base differenziale; le modifiche con valori LSN maggiori o uguali a **DifferentialBaseLSN** sono inclusi nel backup differenziale.<br /><br /> Per un backup differenziale basato su più backup, il valore è NULL e il valore LSN di base deve essere determinato a livello di file. Per altre informazioni, vedere [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).<br /><br /> Per i tipi di backup non differenziali il valore è sempre NULL.<br /><br /> Per altre informazioni, vedere [Backup differenziali &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
|**DifferentialBaseGUID**|**uniqueidentifier**|Per un backup differenziale basato su un solo backup, il valore è l'identificatore univoco della base differenziale.<br /><br /> Per i backup differenziali basati su più backup, il valore è NULL e la base differenziale deve essere determinata per ogni file.<br /><br /> Per i tipi di backup non differenziali il valore è NULL.|  
|**BackupTypeDescription**|**nvarchar(60)**|Tipo di backup in formato stringa. I possibili valori sono i seguenti:<br /><br /> DATABASE<br /><br /> TRANSACTION LOG<br /><br /> FILE OR FILEGROUP<br /><br /> DATABASE DIFFERENTIAL<br /><br /> FILE DIFFERENTIAL PARTIAL<br /><br /> PARTIAL DIFFERENTIAL|  
|**BackupSetGUID**|**uniqueidentifier** NULL|Identificatore univoco del set di backup, che lo identifica nei supporti.|  
|**CompressedBackupSize**|**bigint**|Numero totale di byte del set di backup. Per i backup non compressi, questo valore è identico **BackupSize**.<br /><br /> Per calcolare il rapporto di compressione, utilizzare **CompressedBackupSize** e **BackupSize**.<br /><br /> Durante un **msdb** esegue l'aggiornamento, questo valore è impostato per corrispondere al valore del **BackupSize** colonna.|  
|**contenimento**|**tinyint** non NULL.|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indica lo stato di indipendenza del database.<br /><br /> 0 = l'indipendenza del database è disabilitata<br /><br /> 1 = il database è in stato di indipendenza parziale|  
|**KeyAlgorithm**|**nvarchar(32)**|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) alla versione corrente.<br /><br /> Algoritmo utilizzato per crittografare il backup. NO_Encryption indica che il backup non è stato crittografato. Se non è possibile determinare il valore corretto, usare NULL.|  
|**EncryptorThumbprint**|**varbinary(20)**|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) alla versione corrente.<br /><br /> L'identificazione digitale del componente di crittografia che può essere utilizzato per trovare il certificato o la chiave asimmetrica nel database. Se il backup non è stato crittografato, questo valore è NULL.|  
|**EncryptorType**|**nvarchar(32)**|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) alla versione corrente.<br /><br /> Tipo di componente di crittografia: certificato o chiave asimmetrica. Se il backup non è stato crittografato, questo valore è NULL.|  
  
> [!NOTE]  
>  Se per i set di backup sono state definite password, tramite l'istruzione RESTORE HEADERONLY vengono visualizzate informazioni complete solo per il set di backup la cui password corrisponde al valore specificato nell'opzione PASSWORD del comando. Vengono inoltre visualizzate informazioni complete relative ai set di backup non protetti. Il **Nomebackup** colonna per l'altro backup protetto da password imposta nei supporti è impostata su ' * * * è protetto tramite Password\*\*\*', e tutte le altre colonne sono NULL.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 In un client è possibile utilizzare l'istruzione RESTORE HEADERONLY per il recupero delle informazioni di intestazione di tutti i backup di un dispositivo di backup specifico. Per ogni backup nel dispositivo di backup il server invia le informazioni di intestazione sotto forma di riga.  
  
## <a name="security"></a>Security  
 Per un'operazione di backup è possibile specificare password per un set di supporti o un set di backup oppure per entrambi. Se è stata impostata una password per un set di supporti o un set di backup, la password o le password corrette devono essere specificate nell'istruzione RESTORE. Queste password impediscono operazioni di ripristino non autorizzate e non autorizzato aggiunge set di backup ai supporti tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] strumenti. Tuttavia, la password non impedisce la sovrascrittura dei supporti tramite l'opzione FORMAT dell'istruzione BACKUP.  
  
> [!IMPORTANT]  
>  Il livello di protezione garantito da questa password è ridotto. Lo scopo è impedire un ripristino non corretto da parte di utenti autorizzati o non autorizzati mediante gli strumenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non impedisce la lettura dei dati di backup eseguita con altri mezzi o la sostituzione della password. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]La procedura consigliata per la protezione dei backup consiste nell'archiviare i nastri di backup in un luogo sicuro oppure eseguire il backup su disco i file protetti da elenchi di controllo di accesso (ACL). Gli elenchi di controllo di accesso devono essere impostati a livello della directory radice in cui vengono creati i backup.  
  
### <a name="permissions"></a>Permissions  
 Per ottenere informazioni su un set o dispositivo di backup è necessario disporre dell'autorizzazione CREATE DATABASE. Per altre informazioni, vedere [GRANT - autorizzazioni per database &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite le informazioni dell'intestazione per il file su disco `C:\AdventureWorks-FullBackup.bak`.  
  
```  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks-FullBackup.bak'   
WITH NOUNLOAD;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Informazioni sulla cronologia e sull'intestazione del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [Abilitare o disabilitare i checksum di Backup durante il Backup o ripristino &#40; SQL Server &#41;](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)   
 [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  

