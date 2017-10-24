---
title: BACKUP (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BACKUP_TSQL
- BACKUP
- BACKUP_DATABASE_TSQL
- BACKUP_LOG_TSQL
- BACKUP LOG
- BACKUP DATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], BACKUP statement
- backing up filegroups [SQL Server]
- backup file formats [SQL Server]
- backups [SQL Server]
- database backups [SQL Server], BACKUP statement
- multifamily media sets [SQL Server]
- mirrored media sets [SQL Server]
- backing up files [SQL Server]
- backup sets [SQL Server], BACKUP statement
- backup compression [SQL Server], BACKUP statement
- BACKUP statement
- backups [SQL Server], BACKUP statement
- backup history tables [SQL Server]
- transaction log backups [SQL Server], BACKUP LOG statement
- READ_WRITE_FILEGROUPS option
- BACKUP DATABASE statement
- concurrency [SQL Server], backups
- backing up databases [SQL Server]
- passwords [SQL Server], backups
- security [SQL Server], backups
- media families [SQL Server]
- BACKUP LOG statement
- backing up transaction logs [SQL Server]
- stripe sets [SQL Server]
- cross-platform backups
ms.assetid: 89a4658a-62f1-4289-8982-f072229720a1
caps.latest.revision: 275
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: 3654be2e02163cd8069a95eb5e82d4649cec1ab5
ms.contentlocale: it-it
ms.lasthandoff: 09/14/2017

---
# <a name="backup-transact-sql"></a>BACKUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue il backup completo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database per creare un backup del database, o uno o più file o filegroup del database per creare un file di backup (BACKUP DATABASE). Se, inoltre, si utilizza il modello di recupero con registrazione completa o il modello di recupero con registrazione minima delle operazioni bulk, esegue il backup del log delle transazioni del database per creare un backup del log (BACKUP LOG).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
``` 
Backing Up a Whole Database   
BACKUP DATABASE { database_name | @database_name_var }   
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { DIFFERENTIAL | <general_WITH_options> [ ,...n ] } ]  
[;]  
  
Backing Up Specific Files or Filegroups  
BACKUP DATABASE { database_name | @database_name_var }   
 <file_or_filegroup> [ ,...n ]   
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { DIFFERENTIAL | <general_WITH_options> [ ,...n ] } ]  
[;]  
  
Creating a Partial Backup  
BACKUP DATABASE { database_name | @database_name_var }   
 READ_WRITE_FILEGROUPS [ , <read_only_filegroup> [ ,...n ] ]  
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { DIFFERENTIAL | <general_WITH_options> [ ,...n ] } ]  
[;]  
  
Backing Up the Transaction Log (full and bulk-logged recovery models)  
BACKUP LOG { database_name | @database_name_var }   
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { <general_WITH_options> | \<log-specific_optionspec> } [ ,...n ] ]  
[;]  
  
<backup_device>::=   
 {  
   { logical_device_name | @logical_device_name_var }   
 | { DISK | TAPE | URL} =   
     { 'physical_device_name' | @physical_device_name_var }  
 }   
  
<MIRROR TO clause>::=  
 MIRROR TO <backup_device> [ ,...n ]  
  
<file_or_filegroup>::=  
 {  
   FILE = { logical_file_name | @logical_file_name_var }   
 | FILEGROUP = { logical_filegroup_name | @logical_filegroup_name_var }  
 }   
  
<read_only_filegroup>::=  
FILEGROUP = { logical_filegroup_name | @logical_filegroup_name_var }  
  
<general_WITH_options> [ ,...n ]::=   
--Backup Set Options  
   COPY_ONLY   
 | { COMPRESSION | NO_COMPRESSION }   
 | DESCRIPTION = { 'text' | @text_variable }   
 | NAME = { backup_set_name | @backup_set_name_var }   
 | CREDENTIAL  
 | ENCRYPTION  
 | FILE_SNAPSHOT  
 | { EXPIREDATE = { 'date' | @date_var }   
        | RETAINDAYS = { days | @days_var } }   
  
--Media Set Options  
   { NOINIT | INIT }   
 | { NOSKIP | SKIP }   
 | { NOFORMAT | FORMAT }   
 | MEDIADESCRIPTION = { 'text' | @text_variable }   
 | MEDIANAME = { media_name | @media_name_variable }   
 | BLOCKSIZE = { blocksize | @blocksize_variable }   
  
--Data Transfer Options  
   BUFFERCOUNT = { buffercount | @buffercount_variable }   
 | MAXTRANSFERSIZE = { maxtransfersize | @maxtransfersize_variable }  
  
--Error Management Options  
   { NO_CHECKSUM | CHECKSUM }  
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Compatibility Options  
   RESTART   
  
--Monitoring Options  
   STATS [ = percentage ]   
  
--Tape Options  
   { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }   
  
--Log-specific Options  
   { NORECOVERY | STANDBY = undo_file_name }  
 | NO_TRUNCATE  
  
--Encryption Options  
 ENCRYPTION (ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY } , encryptor_options ) <encryptor_options> ::=   
   SERVER CERTIFICATE = Encryptor_Name | SERVER ASYMMETRIC KEY = Encryptor_Name   
```  
  
## <a name="arguments"></a>Argomenti  
 DATABASE  
 Specifica un backup completo del database. Se viene specificato un elenco di file e di filegroup, il backup viene eseguito solo per tali file e filegroup. Durante un backup completo o differenziale del database, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito il backup di una parte del log delle transazioni sufficiente per generare un database consistente quando viene ripristinato il backup.  
  
 Quando si ripristina un backup creato da BACKUP DATABASE (una *backup dei dati*), viene ripristinato l'intero backup. Solo un backup del log può essere ripristinato fino a un'ora o fino a una transazione specifica all'interno del backup.  
  
> [!NOTE]  
>  Solo un backup completo del database può essere eseguito il **master** database.  
  
 LOG  
 Specifica il backup solo del log delle transazioni. Il backup del log viene eseguito dal punto dell'ultimo backup del log completato correttamente fino alla fine corrente del log. Prima che sia possibile creare il primo backup del log, è necessario creare un backup completo.  
  
 È possibile ripristinare un backup del log in un momento specifico o di una transazione all'interno del backup specificando WITH STOPAT, STOPATMARK o STOPBEFOREMARK nel [RESTORE LOG](../../t-sql/statements/restore-statements-transact-sql.md) istruzione.  
  
> [!NOTE]  
>  Dopo un tipico backup del log, alcuni record del log delle transazioni diventano inattivi, a meno che non si specifichi WITH NO_TRUNCATE o COPY_ONLY. Il log viene troncato dopo che tutti i record in uno o più file di log virtuali diventano inattivi. Se il log non viene troncato dopo i backup del log di routine, è possibile che una causa imprevista provochi un ritardo nel troncamento del log. Per altre informazioni, vedere  
  
 { *database_name* | **@**database_name_var *}   
 Nome del database di cui viene eseguito il backup del log delle transazioni oppure il backup parziale o completo del database. Se specificato come variabile (**@***database_name_var*), questo nome può essere specificato come costante stringa (** @ ** * database_name_var***=***nome del database*) o come una variabile di tipo carattere, ad eccezione di **ntext** o **testo** tipi di dati.  
  
> [!NOTE]  
>  Non è possibile eseguire il backup del database mirror in una relazione di mirroring di database.  
  
\<file_or_filegroup > [ **,**... *n* ]  
 Utilizzato solo con BACKUP DATABASE, specifica un file o filegroup di database da includere in un backup del file oppure un file o filegroup di sola lettura da includere in un backup parziale.  
  
 FILE ** = ** { *nome_file_logico*| **@***logical_file_name_var* }  
 Nome logico di un file o di una variabile il cui valore equivale al nome logico di un file da includere nel backup.  
  
 FILEGROUP ** = ** { *nome_filegroup_logico*| **@***logical_filegroup_name_var* }  
 Nome logico di un filegroup o di una variabile il cui valore equivale al nome logico di un filegroup da includere nel backup. Con il modello di recupero con registrazione minima, il backup dei filegroup è consentito solo per i filegroup di sola lettura.  
  
> [!NOTE]  
>  Prendere in considerazione l'utilizzo di backup dei file quando i requisiti relativi alle prestazioni e le dimensioni del database rendono poco conveniente il backup del database.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare più file e filegroup in un elenco delimitato da virgole. Il numero di file e filegroup che è possibile specificare è illimitato. 
  
 Per ulteriori informazioni, vedere: [backup completo del File &#40; SQL Server &#41; ](../../relational-databases/backup-restore/full-file-backups-sql-server.md) e [eseguire il backup dei file e filegroup &#40; SQL Server &#41; ](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md).  
  
 READ_WRITE_FILEGROUPS [ **,** FILEGROUP = { *nome_filegroup_logico*| **@***logical_filegroup_name_var* } [ **,**... *n* ] ]  
 Specifica un backup parziale. Un backup parziale include tutti i file di lettura/scrittura contenuti in un database, ovvero il filegroup primario, qualsiasi filegroup di lettura/scrittura secondario e tutti i file o filegroup di sola lettura specificati.  
  
 READ_WRITE_FILEGROUPS  
 Specifica che il backup di tutti i filegroup di lettura/scrittura deve essere incluso nel backup parziale. Se il database è di sola lettura, READ_WRITE_FILEGROUPS include solo il filegroup primario.  
  
> [!IMPORTANT]  
>  Se i filegroup di lettura/scrittura vengono indicati in modo esplicito utilizzando FILEGROUP anziché READ_WRITE_FILEGROUPS, viene creato un backup del file.  
  
 FILEGROUP = { *nome_filegroup_logico*| **@***logical_filegroup_name_var* }  
Nome logico di un filegroup di sola lettura o di una variabile il cui valore equivale al nome logico di un filegroup di sola lettura da includere nel backup parziale. Per ulteriori informazioni, vedere "\<file_or_filegroup >," più indietro in questo argomento.
  
 *n*  
 Segnaposto che indica la possibilità di specificare più filegroup di sola lettura in un elenco delimitato da virgole.  
  
 Per ulteriori informazioni sui backup parziali, vedere [backup parziali &#40; SQL Server &#41; ](../../relational-databases/backup-restore/partial-backups-sql-server.md).  
  
PER \<dispositivo_backup > [ **,**... * n * ] Indica che l'accompagna set di [dispositivi di backup](../../relational-databases/backup-restore/backup-devices-sql-server.md) è un set di supporti senza mirroring o il primo mirror in un set (per cui una o più MIRROR TO di supporti con mirroring le clausole vengono dichiarate).  
  
\<dispositivo_backup > specifica un dispositivo di backup logico o fisico da utilizzare per l'operazione di backup.  
  
 { *logical_device_name* | **@***logical_device_name_var* }  
 Nome logico del dispositivo di backup in cui viene eseguito il backup del database. Il nome logico deve essere conforme alle regole per gli identificatori. Se specificato come variabile (@*logical_device_name_var*), il nome di dispositivo di backup può essere specificato come costante stringa (@*logical_device_name_var* ** = ** nome dispositivo di backup logico) oppure come variabile di qualsiasi tipo di dati stringa di caratteri, ad eccezione del **ntext** o **testo** tipi di dati.  
  
 {DISCO | NASTRO | URL} ** = ** { **'***physical_device_name***'**  |  ** @ ** *physical_device_name_var* }  
 Specifica un file su disco o su nastro o un servizio di archiviazione Blob di Windows Azure. Il formato dell'URL viene utilizzato per la creazione di backup per il servizio di archiviazione Windows Azure. Per ulteriori informazioni ed esempi, vedere [SQL Server Backup e ripristino con il servizio di archiviazione Blob di Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). Per un'esercitazione, vedere [esercitazione: Backup di SQL Server e il ripristino in Windows Azure Blob Storage Service](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
> [!IMPORTANT]  
>  Con [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 finché [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], è possibile eseguire solo backup in un singolo dispositivo per il backup su URL. Per eseguire il backup per più dispositivi per il backup su URL, è necessario usare [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ed è necessario utilizzare i token di firma di accesso condiviso (SAS). Per esempi di creazione di una firma di accesso condiviso, vedere [SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md) e [semplificando la creazione delle credenziali SQL con i token di firma di accesso condiviso (SAS) nell'archiviazione di Azure con Powershell](http://blogs.msdn.com/b/sqlcat/archive/2015/03/21/simplifying-creation-sql-credentials-with-shared-access-signature-sas-keys-on-azure-storage-containers-with-powershell.aspx).  
  
**URL si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 alla [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
 Non è necessario che un dispositivo disco sia presente prima che venga specificato in un'istruzione BACKUP. Se il dispositivo fisico è presente e si omette l'opzione INIT nell'istruzione BACKUP, il backup viene accodato al dispositivo.  
  
 Per altre informazioni, vedere [Dispositivi di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
> [!NOTE]  
>  L'opzione TAPE verrà rimossa in una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare fino a 64 dispositivi di backup in un elenco delimitato da virgole.  
  
MIRROR TO \<dispositivo_backup > [ **,**... * n * ] Specifica un set di fino a tre dispositivi di backup secondari, ognuno dei quali mirror dei dispositivi di backup specificati nella clausola TO. La clausola MIRROR TO deve specificare lo stesso tipo e numero di dispositivi di backup indicati nella clausola TO. Il numero massimo di clausole MIRROR TO è tre.  
  
 Questa opzione è disponibile solo nella Enterprise Edition di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Con la clausola MIRROR TO = DISK, l'istruzione BACKUP determina automaticamente le dimensioni del blocco appropriate per i dispositivi disco. Per ulteriori informazioni sulle dimensioni del blocco, vedere "BLOCKSIZE" più avanti in questo argomento.  
  
\<dispositivo_backup > vedere "\<dispositivo_backup >," più indietro in questa sezione.
  
 *n*  
 Segnaposto che indica la possibilità di specificare fino a 64 dispositivi di backup in un elenco delimitato da virgole. Il numero di dispositivi specificato nella clausola MIRROR TO deve essere uguale al numero di dispositivi indicato nella clausola TO.  
  
 Per ulteriori informazioni, vedere "Gruppi di supporti in set di supporti con mirroring" nella sezione "Osservazioni" più avanti in questo argomento.  
  
 [ *Avanti mirror to* ]  
 Segnaposto che indica che una singola istruzione BACKUP può contenere fino a tre clausole MIRROR TO oltre alla singola clausola TO.  
  
### <a name="with-options"></a>Opzioni WITH  
 Opzioni da utilizzare con un'operazione di backup.  
  
 CREDENTIAL  
 Viene utilizzata solo quando si crea un backup nel servizio di archiviazione BLOB di Windows Azure.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 alla [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
 FILE_SNAPSHOT  
 Utilizzato per creare uno snapshot dei file di database di Azure, se tutti i file di database di SQL Server vengono archiviati utilizzando il servizio di archiviazione Blob di Azure. Per ulteriori informazioni, vedere [file di dati di SQL Server in Microsoft Azure](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Backup di snapshot accetta gli snapshot di Azure dei file di database (file di log e dati) in uno stato coerente. Un set coerente di snapshot di Azure vengono registrati nel file di backup sia costituiscono una copia di backup. L'unica differenza tra **BACKUP DATABASE per URL con FILE_SNAPSHOT** e **BACKUP LOG per URL con FILE_SNAPSHOT** è che quest'ultimo un troncamento del log delle transazioni durante il primo non. Con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il Backup dello Snapshot, dopo il backup completo iniziale che è richiesto dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire la catena di backup, solo un backup del log singola transazione è obbligatorio per ripristinare un database al punto nel tempo del backup del log delle transazioni. Inoltre, solo due backup del log delle transazioni necessario ripristinare un database a un punto nel tempo che intercorre tra l'ora dei backup del log delle transazioni.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
 DIFFERENTIAL  
 Opzione utilizzata solo con BACKUP DATABASE, che indica che il backup del database o del file deve includere solo le parti del database o del file modificate dopo l'ultimo backup completo. Un backup differenziale occupa in genere meno spazio rispetto a un backup completo. Utilizzare questa opzione per evitare di applicare tutti i singoli backup del log eseguiti dopo l'ultimo backup completo.  
  
> [!NOTE]  
>  Per impostazione predefinita, BACKUP DATABASE crea un backup completo.  
  
 Per altre informazioni, vedere [Backup differenziali &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md).  
  
 ENCRYPTION  
 Utilizzato per specificare la crittografia per il backup. È possibile specificare un algoritmo di crittografia con cui crittografare il backup oppure specificare "NO_ENCRYPION" per non eseguire alcuna crittografia del backup. La crittografia è consigliabile per la sicurezza dei file di backup. Gli algoritmi che si possono specificare sono:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Se si sceglie di crittografare è necessario specificare il componente di crittografia utilizzando le relative opzioni:  
  
-   SERVER CERTIFICATE = Encryptor_Name  
  
-   SERVER ASYMMETRIC KEY = Encryptor_Name  
  
    > [!WARNING]  
    >  Quando viene utilizzata la crittografia in combinazione con l'argomento FILE_SNAPSHOT, il file di metadati viene crittografato utilizzando l'algoritmo di crittografia specificato e il sistema verifica che TDE è stata completata per il database. Nessuna crittografia aggiuntiva avviene per i dati stessi. Il backup non riesce se il database non è stato crittografato o se la crittografia non è stata completata prima dell'istruzione di backup è stato rilasciato.  
  
**Opzioni Set di backup**  
  
Queste opzioni riguardano il set di backup creato dall'operazione di backup.  
  
> [!NOTE]  
>  Per specificare un set di backup per un'operazione di ripristino, utilizzare il FILE ** = ** * \<backup_set_file_number >* opzione. Per ulteriori informazioni su come specificare un set di backup, vedere "Specifica di un Set di Backup" in [argomenti RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).
  
 COPY_ONLY  
 Specifica che il backup è un *backup di sola copia*, che non influisce sulla normale sequenza di backup. Un backup di sola copia viene creato indipendentemente dai normali backup pianificati regolarmente. Un backup di sola copia non ha alcun impatto sulle procedure generali di backup e ripristino per il database.  
  
 I backup di sola copia devono essere utilizzati nelle situazioni in cui un backup è necessario per uno scopo specifico, ad esempio un backup del log prima di un ripristino di file online. In genere, un backup del log di sola copia viene utilizzato una sola volta e quindi eliminato.  
  
-   Se utilizzata con BACKUP DATABASE, l'opzione COPY_ONLY crea un backup completo che non può essere utilizzato come base differenziale. La mappa di bit differenziale non viene aggiornata e i backup differenziali ignorano il backup di sola copia. I backup differenziali successivi utilizzano come base il backup completo convenzionale più recente.  
  
    > [!IMPORTANT]  
    >  Se le opzioni DIFFERENTIAL e COPY_ONLY vengono utilizzate insieme, COPY_ONLY viene ignorata e viene creato un backup differenziale.  
  
-   Se utilizzata con BACKUP LOG, l'opzione COPY_ONLY crea un *backup del log di sola copia*, che non tronca il log delle transazioni. Il backup del log di sola copia non ha alcun effetto sulla catena di log e viene ignorato dagli altri backup del log.  
  
Per altre informazioni, vedere [Backup di sola copia &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).  
  
{ COMPRESSION | NO_COMPRESSION }  
In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] e versioni successive, specifica se [compressione dei backup](../../relational-databases/backup-restore/backup-compression-sql-server.md) viene eseguita su questo backup, ignorando l'impostazione predefinita a livello di server.  
  
In fase di installazione, la compressione backup è disattivata per impostazione predefinita. Ma questa impostazione predefinita può essere modificata impostando il [valore predefinito di compressione backup](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md) opzione di configurazione del server. Per informazioni sulla visualizzazione del valore corrente di questa opzione, vedere [visualizzare o modificare le proprietà del Server &#40; SQL Server &#41; ](../../database-engine/configure-windows/view-or-change-server-properties-sql-server.md).  
  
COMPRESSION  
Abilita in modo esplicito la compressione dei backup.  
  
NO_COMPRESSION  
Disabilita in modo esplicito la compressione dei backup.  
  
DESCRIPTION **=** { **'***testo***'** | **@***variabile_testo* }  
Specifica il testo in formato libero che descrive il set di backup. La stringa può essere composta da un massimo di 255 caratteri.  
  
NOME ** = ** { *nome_set_backup*| **@***backup_set_var* }  
Specifica il nome del set di backup. I nomi possono essere composti da un massimo di 128 caratteri. Se si omette NAME, al set di backup non viene assegnato alcun nome specifico.  
  
{EXPIREDATE **='***data***'**| RETAINDAYS ** = ** *giorni* }  
Indica quando è possibile sovrascrivere il set di backup per il backup specifico. Se si utilizzano entrambe le opzioni, RETAINDAYS ha la precedenza rispetto a EXPIREDATE.  
  
Se nessuna delle due opzioni vengano specificata, la data di scadenza è determinata dal **mediaretention** impostazione di configurazione. Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)sia installato il servizio WMI.  
  
> [!IMPORTANT]  
>  Queste opzioni impediscono esclusivamente la sovrascrittura di file da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile cancellare i nastri con altri metodi e i file su disco possono essere eliminati tramite il sistema operativo. Per ulteriori informazioni sulla verifica della scadenza, vedere le opzioni SKIP e FORMAT in questo argomento.  
  
EXPIREDATE ** = ** { **'***data***'** |  ** @ ** *date_var* }  
 Specifica quando il set di backup scade e può essere sovrascritto. Se specificato come variabile (@*date_var*), la data deve seguire il sistema nella configurazione **datetime** formattare ed essere specificati come uno dei seguenti:  
  
-   Costante stringa (@*date_var* ** = ** Data)  
-   Una variabile di tipo carattere (tranne che per il **ntext** o **testo** tipi di dati)  
-   Oggetto **smalldatetime**  
-   Oggetto **datetime** variabile  
  
Esempio:  
  
-   `'Dec 31, 2020 11:59 PM'`  
-   `'1/1/2021'`  
  
Per informazioni su come specificare **datetime** valori, vedere [tipi data e ora](../../t-sql/data-types/date-and-time-types.md).  
  
> [!NOTE]  
>  Per ignorare la data di scadenza, utilizzare l'opzione SKIP.  
  
RETAINDAYS ** = ** { *giorni*| **@***days_var* }  
 Specifica il numero di giorni che devono trascorrere prima che il set di supporti di backup possa essere sovrascritto. Se specificato come variabile (**@***days_var*), deve essere specificato come intero.  
  
**Opzioni Set di supporti**  
  
Queste opzioni vengono applicate all'intero set di supporti.  
  
{ **NOINIT** | INIT}  
 Determina se l'operazione di backup accoda i dati ai set di backup esistenti nei supporti di backup o sovrascrive tali set. L'impostazione predefinita consiste nell'accodare i dati al set di backup più recente presente nel supporto (NOINIT).  
  
> [!NOTE]  
>  Per informazioni sulle interazioni tra { **NOINIT** | INIT} e { **NOSKIP** | SKIP}, vedere "la sezione Osservazioni", più avanti in questo argomento.  
  
NOINIT  
 Indica che il set di backup viene accodato nel set di supporti specificato, mantenendo i set di backup esistenti. Se per il set di supporti è stata definita una password, è necessario specificare la password corretta. NOINIT è l'opzione predefinita.  
  
Per altre informazioni, vedere [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  
  
INIT  
 Specifica che tutti i set di backup devono essere sovrascritti, mantenendo però l'intestazione supporto. Se si specifica INIT, vengono sovrascritti tutti i set di backup presenti nel dispositivo, se le condizioni lo consentono. Per impostazione predefinita, l'istruzione BACKUP controlla se esistono le condizioni seguenti e non sovrascrive i supporti di backup in presenza di una di tali condizioni:  
  
-   Vi sono set di backup non ancora scaduti. Per ulteriori informazioni, vedere le opzioni EXPIREDATE e RETAINDAYS.  
-   Il nome del set di backup specificato nell'istruzione BACKUP, se indicato, non corrisponde al nome nei supporti di backup. Per ulteriori informazioni, vedere l'opzione NAME in precedenza in questa sezione.  
  
Per ignorare questi controlli, utilizzare l'opzione SKIP.  
  
Per altre informazioni, vedere [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  
  
{ **NOSKIP** | SKIP}  
Determina se un'operazione di backup deve controllare la data e l'ora di scadenza dei set di backup nei supporti prima di sovrascriverli.  
  
> [!NOTE]  
>  Per informazioni sulle interazioni tra { **NOINIT** | INIT} e { **NOSKIP** | SKIP}, vedere "la sezione Osservazioni", più avanti in questo argomento.  
  
NOSKIP  
Imposta il controllo della data di scadenza di tutti i set di backup nei supporti da eseguire durante l'operazione BACKUP prima di consentire la sovrascrittura dei set. Questo è il comportamento predefinito.  
  
SKIP  
Disabilita la verifica del nome e della scadenza dei set di backup, eseguita in genere dall'istruzione BACKUP per impedire la sovrascrittura dei set di backup. Per informazioni sulle interazioni tra { INIT | NOINIT } e { NOSKIP | SKIP }, vedere la sezione "Osservazioni" più avanti in questo argomento.  
Per visualizzare le date di scadenza dei set di backup, eseguire una query di **expiration_date** colonna il [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) tabella di cronologia.  
  
{ **NOFORMAT** | FORMATO}  
Specifica se l'intestazione supporto deve essere scritta nei volumi utilizzati per l'operazione di backup, sovrascrivendo eventuali intestazioni supporti e set di backup esistenti.  
  
NOFORMAT  
Indica che l'operazione di backup deve mantenere l'intestazione supporto e i set di backup esistenti nei volumi dei supporti utilizzati per l'operazione di backup stessa. Questo è il comportamento predefinito.  
  
FORMAT  
Specifica che deve essere creato un nuovo set di supporti. FORMAT comporta la scrittura di una nuova intestazione supporto in tutti i volumi dei supporti utilizzati per l'operazione di backup. Il contenuto esistente del volume non è più valido, in quanto tutte le intestazioni supporti e i set di backup esistenti vengono sovrascritti.  
  
> [!IMPORTANT]  
>  Utilizzare FORMAT con cautela. La formattazione di un volume di un set di supporti rende inutilizzabile l'intero set di supporti. Se, ad esempio, si inizializza un singolo nastro appartenente a un set di supporti con striping esistente, l'intero set di supporti diventa inutilizzabile.  
  
L'utilizzo dell'opzione FORMAT implica l'utilizzo di SKIP. Non è quindi necessario specificare SKIP in modo esplicito.  
  
MEDIADESCRIPTION ** = ** { *testo* | **@***variabile_testo* }  
Specifica la descrizione di testo in formato libero del set di supporti, composta da un massimo di 255 caratteri.  
  
MEDIANAME ** = ** { *nome_supporto* | **@***variabile_nome_supporto* }  
Specifica il nome dei supporti per l'intero set di supporti di backup. Il nome dei supporti deve essere composto da un massimo di 128 caratteri. Se si specifica MEDIANAME, il nome deve corrispondere al nome dei supporti precedentemente specificato già esistente nei volumi di backup. Se si omette MEDIANAME oppure si specifica l'opzione SKIP, non viene eseguita alcuna verifica del nome dei supporti.  
  
BLOCKSIZE ** = ** { *blocksize* | **@***blocksize_variable* }  
Specifica le dimensioni fisiche del blocco, in byte. Le dimensioni supportate sono 512, 1024, 2048, 4096, 8192, 16384, 32768 e 65536 (64 KB) byte. Il valore predefinito è 65536 per i dispositivi nastro e 512 negli altri casi. Questa opzione non è in genere necessaria, in quanto vengono selezionate automaticamente le dimensioni del blocco più appropriate per il dispositivo. L'impostazione esplicita delle dimensioni del blocco ha la priorità sulla selezione automatica.  
  
Se si esegue un backup che si desidera copiare in e ripristinare da un CD-ROM, specificare BLOCKSIZE=2048.  
  
> [!NOTE]  
>  In genere, questa opzione influisce sulle prestazioni solo durante la scrittura nei dispositivi nastro.  
  
**Opzioni di trasferimento di dati**  
  
BUFFERCOUNT ** = ** { *buffercount* | **@***buffercount_variable* }  
Specifica il numero totale di buffer di I/O da utilizzare per l'operazione di backup. È possibile specificare qualsiasi numero intero positivo. Un numero elevato di buffer può tuttavia causare errori di memoria insufficiente dovuti a spazio degli indirizzi virtuali non adeguato nel processo Sqlservr.exe.  
  
Lo spazio totale utilizzato dai buffer viene determinato da: *buffercount***\****maxtransfersize*.  
  
> [!NOTE]  
>  Per informazioni importanti sull'utilizzo dell'opzione BUFFERCOUNT, vedere il [opzione di trasferimento dati BufferCount non corretta può causare condizione OOM](http://blogs.msdn.com/b/sqlserverfaq/archive/2010/05/06/incorrect-buffercount-data-transfer-option-can-lead-to-oom-condition.aspx) blog.  
  
MAXTRANSFERSIZE ** = ** { *maxtransfersize* | **@***maxtransfersize_variable* }  
 Specifica le dimensioni massime, in byte, per il trasferimento tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i supporti di backup. I valori possibili sono i multipli di 65536 byte (64 KB) fino a 4194304 byte (4 MB).  
> [!NOTE]  
>  Durante la creazione di backup utilizzando il servizio Writer SQL, se il database è configurato FILESTREAM o include gruppi di File OLTP In memoria, la `MAXTRANSFERSIZE` in fase di ripristino deve essere maggiore o uguale al `MAXTRANSFERSIZE` che è stato utilizzato quando il è stato creato il backup. 
  
**Opzioni di gestione di errori**  
  
Queste opzioni consentono di determinare se i checksum di backup sono abilitati per l'operazione di backup e se l'operazione si arresta quando viene rilevato un errore.  
  
{ **NO_CHECKSUM** | CHECKSUM}  
 Determina se i checksum del backup sono abilitati.  
  
NO_CHECKSUM  
Disabilita in modo esplicito la generazione di valori di checksum per il backup e la convalida dei valori di checksum delle pagine. Questo è il comportamento predefinito.  
  
CHECKSUM  
Specifica che l'operazione di backup verifica di ogni pagina per checksum e pagine incomplete, se abilitati e disponibili e genera un checksum per l'intero backup.  
  
L'utilizzo di checksum di backup può influire sul carico di lavoro e sulla velocità effettiva del backup.  
  
Per ulteriori informazioni, vedere [possibili supporti errori durante il Backup e il ripristino &#40; SQL Server &#41; ](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md).  
  
{ **STOP_ON_ERROR** | CONTINUE_AFTER_ERROR}  
Determina se un'operazione di backup viene arrestata o prosegue in seguito a un errore checksum della pagina.  
  
STOP_ON_ERROR  
Imposta l'interruzione dell'istruzione BACKUP in presenza di errori checksum della pagina. Questo è il comportamento predefinito.  
  
CONTINUE_AFTER_ERROR  
Imposta il proseguimento dell'istruzione BACKUP anche in caso di errori, ad esempio checksum non validi o pagine incomplete.  
  
Se non è possibile eseguire il backup della parte finale del log utilizzando il NO_TRUNCATE opzione quando il database è danneggiato, è possibile tentare un [backup del log della parte finale del log](../../relational-databases/backup-restore/tail-log-backups-sql-server.md) specificando CONTINUE_AFTER_ERROR anziché NO_TRUNCATE.  
  
Per ulteriori informazioni, vedere [possibili supporti errori durante il Backup e il ripristino &#40; SQL Server &#41; ](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md).  
  
**Opzioni di compatibilità**  
  
RESTART  
A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], non ha alcun effetto. L'opzione è accettata in questa versione per compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Opzioni di monitoraggio**  
  
STATISTICHE [ ** = ** *percentuale* ]  
 Viene visualizzato un messaggio ogni volta che un altro *percentuale* completa e viene utilizzato per misurare lo stato di avanzamento. Se *percentuale* viene omesso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene visualizzato un messaggio dopo ogni 10% è stata completata.  
  
L'opzione STATS segnala la percentuale di completamento in base alla soglia specificata per l'intervallo successivo. Si tratta approssimativamente della percentuale specificata. Con l'impostazione STATS=10, ad esempio, se la percentuale di completamento corrisponde al 40%, potrebbe venire indicata una percentuale uguale al 43%. Per i set di backup di grandi dimensioni ciò non rappresenta un problema, perché la percentuale di completamento aumenta molto lentamente tra le varie chiamate di I/O completate.  
  
**Opzioni relative al nastro**  
  
Queste opzioni vengono utilizzate solo per i dispositivi nastro. Se non si utilizza un dispositivo nastro, queste opzioni vengono ignorate.  
  
{ **REWIND** | NOREWIND }  
REWIND  
 Specifica che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene rilasciato e riavvolto. REWIND è l'opzione predefinita.  
  
NOREWIND  
Specifica che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve mantenere il nastro aperto dopo l'operazione di backup. È possibile utilizzare questa opzione per migliorare le prestazioni quando si eseguono più operazioni di backup sullo stesso nastro.  
  
L'opzione NOREWIND implica l'utilizzo di NOUNLOAD e queste opzioni non sono compatibili all'interno di una singola istruzione BACKUP.  
  
> [!NOTE]  
>  Se si utilizza l'opzione NOREWIND, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene la proprietà dell'unità nastro fino a quando un'istruzione BACKUP o RESTORE eseguita nello stesso processo non utilizza l'opzione REWIND o UNLOAD oppure fino alla chiusura dell'istanza del server. Ciò impedisce ad altri processi di accedere al nastro. Per informazioni su come visualizzare un elenco dei nastri aperti e chiudere un nastro aperto, vedere [dispositivi di Backup &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
{ **SCARICAMENTO** | UTILIZZO DI NOUNLOAD}  
> [!NOTE]  
>  UNLOAD/NOUNLOAD è un'impostazione di sessione che rimane valida per l'intera durata della sessione o finché non viene reimpostata tramite la specifica di un'impostazione alternativa.  
  
UNLOAD  
 Specifica che il nastro viene riavvolto e scaricato automaticamente al termine del backup. L'opzione UNLOAD è l'impostazione predefinita all'avvio di una sessione. 
  
NOUNLOAD  
 Specifica che dopo l'operazione di BACKUP il nastro rimane caricato sull'unità nastro.  
  
> [!NOTE]  
>  Per un backup in un dispositivo di backup su nastro, l'opzione BLOCKSIZE influisce sulle prestazioni dell'operazione di backup. In genere, questa opzione influisce sulle prestazioni solo durante la scrittura nei dispositivi nastro.  
  
**Opzioni specifiche dei log**  
  
Queste opzioni vengono utilizzate solo con BACKUP LOG.  
  
> [!NOTE]  
>  Se non si desidera eseguire un backup del log, utilizzare il modello di recupero con registrazione minima. Per altre informazioni, vedere [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
{NORECOVERY | STANDBY ** = ** *nome_file_ripristino* }  
  NORECOVERY  
  Consente di eseguire il backup della parte finale del log lasciando il database nello stato RESTORING. L'opzione NORECOVERY risulta utile quando si esegue il failover in un database secondario o per salvare la parte finale del log prima di un'operazione RESTORE.  
  
  Utilizzare insieme le opzioni NO_TRUNCATE e NORECOVERY per eseguire un backup del log senza troncamento del log e quindi portare il database nello stato RESTORING in modo atomico.  
  
  STANDBY ** = ** *standby_file_name*  
  Consente di eseguire il backup della parte finale del log lasciando il database nello stato STANDBY e di sola lettura. La clausola STANDBY scrive i dati di standby (esecuzione del rollback ma con la possibilità di ulteriori ripristini). L'utilizzo dell'opzione STANDBY equivale all'esecuzione di BACKUP LOG WITH NORECOVERY seguita da RESTORE WITH STANDBY.  
  
  Utilizzare la modalità standby richiede un file standby, specificato da *standby_file_name*, il cui percorso è archiviato nel registro del database. Se il file specificato esiste già, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] lo sovrascrive. Se il file non esiste, viene creato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Il file standby diventa un elemento integrante del database.  
  
  In questo file vengono memorizzate le modifiche di cui è stato eseguito il rollback, che devono essere annullate se è necessario eseguire successivamente operazioni RESTORE LOG. Lo spazio su disco a disposizione deve essere sufficiente per contenere il file standby, le cui dimensioni aumenteranno in quanto dovrà includere tutte le pagine distinte del database modificate dal rollback delle transazioni per le quali non è stato eseguito il commit.  
  
NO_TRUNCATE  
Specifica che il non registro troncati e fa sì che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] tentativo di backup, indipendentemente dallo stato del database. È pertanto possibile che un backup creato con NO_TRUNCATE contenga metadati incompleti. Questa opzione consente l'esecuzione del backup del log quando il database è danneggiato.  
  
L'opzione NO_TRUNCATE per BACKUP LOG equivale a specificare sia COPY_ONLY che CONTINUE_AFTER_ERROR.  
  
Se non si utilizza l'opzione NO_TRUNCATE, il database deve essere ONLINE. Se lo stato del database corrisponde a SUSPENDED, è possibile creare un backup specificando NO_TRUNCATE. Se tuttavia lo stato del database è OFFLINE o EMERGENCY, l'esecuzione dell'istruzione BACKUP non è consentita nemmeno con NO_TRUNCATE. Per informazioni sugli stati del database, vedere [stati del Database](../../relational-databases/databases/database-states.md).  
  
## <a name="about-working-with-sql-server-backups"></a>Informazioni sull'utilizzo di backup di SQL Server  
 In questa sezione vengono presentati i seguenti concetti di backup fondamentali:  
  
 [Tipi di backup](#Backup_Types)  
 [Troncamento del Log delle transazioni](#Tlog_Truncation)  
 [Formattare i supporti di Backup](#Formatting_Media)  
 [Utilizzo di set di supporti e dispositivi di Backup](#Backup_Devices_and_Media_Sets)  
 [Ripristino dei backup SQL Server](#Restoring_Backups)  
  
> [!NOTE]  
>  Per un'introduzione al backup in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Panoramica del Backup &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
###  <a name="Backup_Types"></a>Tipi di backup  
 I tipi di backup supportati dipendono dal modello di recupero del database utilizzato, in base a quanto indicato di seguito.  
  
-   Tutti i modelli di recupero supportano backup completi e differenziali dei dati.  
  
    |Ambito del backup|Tipi di backup|  
    |---------------------|------------------|  
    |Database intero|[Backup dei database](../../relational-databases/backup-restore/full-database-backups-sql-server.md) coprire l'intero database.<br /><br /> Facoltativamente, ogni backup del database può essere utilizzato come base di una serie di uno o più [backup differenziali del database](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
    |Database parziale|[I backup parziali](../../relational-databases/backup-restore/partial-backups-sql-server.md) copertura di lettura/scrittura filegroup e, possibilmente, uno o più file di sola lettura o filegroup.<br /><br /> Facoltativamente, ogni backup parziale può essere utilizzato come base di una serie di uno o più [i backup parziali differenziali](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
    |File o filegroup|[Backup dei file](../../relational-databases/backup-restore/full-file-backups-sql-server.md) riguardare uno o più file o filegroup e sono rilevanti solo per i database che contengono più filegroup. Se si utilizza il modello di recupero con registrazione minima, i backup dei file sono in genere limitati ai filegroup di sola lettura secondari.<br /> Facoltativamente, ogni backup di file può essere utilizzato come base di una serie di uno o più [backup differenziali di file](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
  
-   Sotto il modello di recupero con registrazione completa o il modello di recupero di massa, backup convenzionali anche includere sequenziale *backup del log delle transazioni* (o *i backup del log*), che sono necessari. Ogni backup del log viene eseguito sulla parte del log delle transazioni attiva al momento della creazione del backup e include tutti i record del log di cui non è stato eseguito il backup nei backup del log precedenti.  
  
     Per ridurre al minimo il rischio di perdita di dati, aumentando tuttavia il numero di operazioni amministrative, è consigliabile pianificare backup del log frequenti. La pianificazione di backup differenziali nei periodi intermedi tra i backup completi consente di ridurre i tempi di ripristino limitando il numero di backup del log da ripristinare in seguito al ripristino dei dati.  
  
     È consigliabile archiviare i backup dei log in un volume distinto rispetto ai backup dei database.  
  
    > [!NOTE]  
    >  Prima che sia possibile creare il primo backup del log, è necessario creare un backup completo.  
  
-   Oggetto *backup di sola copia* è un backup completo speciale o un backup del log che è indipendente dalla normale sequenza di backup convenzionali. Per creare un backup di sola copia, specificare l'opzione COPY_ONLY nell'istruzione BACKUP. Per altre informazioni, vedere [Backup di sola copia &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).  
  
###  <a name="Tlog_Truncation"></a>Troncamento del Log delle transazioni  
 Per evitare di esaurire lo spazio nel log delle transazioni di un database, è essenziale eseguire backup di routine. Con il modello di recupero con registrazione minima il troncamento del log si verifica automaticamente dopo il backup del database, mentre con il modello di recupero con registrazione completa si verifica dopo il backup del log delle transazioni. A volte, tuttavia, il processo di troncamento può essere ritardato. Per informazioni sui fattori che possono ritardare il troncamento del log, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
> [!NOTE]  
>  Le opzioni BACKUP LOG WITH NO_LOG e WITH TRUNCATE_ONLY non sono più supportate. Se si utilizza il modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk ed è necessario rimuovere la catena dei backup del log da un database, passare al modello di recupero con registrazione minima. Per altre informazioni, vedere [Visualizzare o modificare il modello di recupero di un database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
###  <a name="Formatting_Media"></a>Formattare i supporti di Backup  
 I supporti di backup vengono formattati tramite l'istruzione BACKUP esclusivamente quando si verifica una delle condizioni seguenti:  
  
-   Viene specificata l'opzione FORMAT.  
-   I supporti sono vuoti.  
-   Viene eseguita un'operazione di scrittura in un nastro di continuità.  
  
###  <a name="Backup_Devices_and_Media_Sets"></a>Utilizzo di set di supporti e dispositivi di Backup  
  
#### <a name="backup-devices-in-a-striped-media-set-a-stripe-set"></a>Dispositivi di backup in un set di supporti con striping (set di striping)  
 Oggetto *striping* è un set di file su disco in cui i dati vengono suddivisi in blocchi e distribuiti in un ordine prestabilito. Il numero di dispositivi di backup utilizzati in un set di striping deve rimanere invariato, a meno che i supporti non vengano reinizializzati tramite FORMAT.  
  
 Nell'esempio seguente un backup del database [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] viene scritto in un nuovo set di supporti con striping che utilizza tre file su disco.  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO DISK='X:\SQLServerBackups\AdventureWorks1.bak',   
DISK='Y:\SQLServerBackups\AdventureWorks2.bak',   
DISK='Z:\SQLServerBackups\AdventureWorks3.bak'  
WITH FORMAT,  
   MEDIANAME = 'AdventureWorksStripedSet0',  
   MEDIADESCRIPTION = 'Striped media set for AdventureWorks2012 database;  
GO  
```  
  
 Dopo avere definito un dispositivo di backup come parte di un set di striping, non è possibile utilizzarlo per il backup su un singolo dispositivo, a meno che non si specifichi FORMAT. In modo analogo, non è possibile utilizzare un dispositivo di backup contenente backup senza striping in un set di striping, a meno che non si specifichi l'opzione FORMAT. Utilizzare l'opzione FORMAT per dividere un set di backup di striping.  
  
 Se viene specificato né MEDIANAME né MEDIADESCRIPTION viene scritta un'intestazione supporto, corrispondente all'elemento vuoto il campo di intestazione supporto è vuoto.  
  
#### <a name="working-with-a-mirrored-media-set"></a>Utilizzo di un set di supporti con mirroring  
 In genere, i backup vengono eseguiti senza mirroring e le istruzioni BACKUP includono solo una clausola TO. Ogni set di supporti, tuttavia, può contenere uno totale di quattro mirror. Per un set di supporti con mirroring, l'operazione di backup scrive in più gruppi di dispositivi di backup. Ogni gruppo di dispositivi di backup comprende un solo mirror all'interno del set di supporti con mirroring. Ogni mirror deve utilizzare la stessa quantità e lo stesso tipo di dispositivi di backup fisici, configurati con le stesse proprietà.  
  
 Per eseguire il backup in un set di supporti con mirroring, è necessario che siano presenti tutti i mirror. Per eseguire il backup in un set di backup con mirroring, specificare la clausola TO per indicare il primo mirror e quindi una clausola MIRROR TO per ogni mirror aggiuntivo.  
  
 Per un set di supporti con mirroring, ogni clausola MIRROR TO deve includere lo stesso numero e lo stesso tipo di dispositivi indicati nella clausola TO. Nell'esempio seguente viene eseguita la scrittura in un set di supporti con mirroring contenente due mirror, utilizzando tre dispositivi per ogni mirror:  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO DISK='X:\SQLServerBackups\AdventureWorks1a.bak',   
DISK='Y:\SQLServerBackups\AdventureWorks2a.bak',   
DISK='Z:\SQLServerBackups\AdventureWorks3a.bak'  
MIRROR TO DISK='X:\SQLServerBackups\AdventureWorks1b.bak',   
DISK='Y:\SQLServerBackups\AdventureWorks2b.bak',   
DISK='Z:\SQLServerBackups\AdventureWorks3b.bak';  
GO  
```  
  
> [!IMPORTANT]  
>  Questo esempio è progettato in modo da poter essere testato nel sistema locale. In pratica, l'esecuzione di un backup su più dispositivi nella stessa unità influirebbe negativamente sulle prestazioni ed eliminerebbe la ridondanza per cui sono progettati i set di supporti con mirroring.  
  
##### <a name="media-families-in-mirrored-media-sets"></a>Gruppi di supporti in set di supporti con mirroring  
 Ogni dispositivo di backup specificato nella clausola TO di un'istruzione BACKUP corrisponde a un gruppo di supporti. Se, ad esempio, nella clausola TO sono indicati tre dispositivi, l'istruzione BACKUP scrive i dati in tre gruppi di supporti. In un set di supporti con mirroring ogni mirror deve contenere una copia di ogni gruppo di supporti. Per questo motivo, il numero di dispositivi deve essere identico in ogni mirror.  
  
 Se per ogni mirror vengono specificati più dispositivi, l'ordine dei dispositivi nell'elenco determina il gruppo di supporti scritto in ogni dispositivo specifico. In ognuno degli elenchi di dispositivi, ad esempio, il secondo dispositivo corrisponde al secondo gruppo di supporti. Nella tabella seguente viene illustrata la corrispondenza tra i dispositivi e i gruppi di supporti inclusi nell'esempio precedente.  
  
|Mirror|1 gruppo di supporti|Gruppo di supporti 2|Gruppo di supporti 3|  
|------------|--------------------|--------------------|--------------------|  
|0|`Z:\AdventureWorks1a.bak`|`Z:\AdventureWorks2a.bak`|`Z:\AdventureWorks3a.bak`|  
|1|`Z:\AdventureWorks1b.bak`|`Z:\AdventureWorks2b.bak`|`Z:\AdventureWorks3b.bak`|  
  
 Di ogni gruppo di supporti è necessario eseguire il backup sempre nello stesso dispositivo all'interno di un mirror specifico. Per questo motivo, ogni volta che si utilizza un set di supporti esistente, è necessario elencare i dispositivi di ogni mirror in base allo stesso ordine in cui sono stati specificati al momento della creazione del set di supporti.  
  
 Per altre informazioni sui set di supporti con mirroring, vedere [Set di supporti di backup con mirroring &#40;SQL Server&#41;](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md). Per ulteriori informazioni sui set di supporti e i gruppi di supporti in generale, vedere [set di supporti, gruppi di supporti e set di Backup &#40; SQL Server &#41; ](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  
  
###  <a name="Restoring_Backups"></a>Ripristino dei backup SQL Server  
 Per ripristinare un database e, facoltativamente, recuperarlo per portarlo online oppure per ripristinare un file o filegroup, utilizzare il [!INCLUDE[tsql](../../includes/tsql-md.md)] [ripristinare](../../t-sql/statements/restore-statements-transact-sql.md) istruzione o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **ripristinare** attività. Per ulteriori informazioni vedere [e panoramica sul ripristino del recupero &#40; SQL Server &#41; ](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
##  <a name="Additional_Considerations"></a>Considerazioni aggiuntive sulle opzioni di BACKUP  
  
###  <a name="Interactions_SKIP_etc"></a>Interazione tra SKIP, NOSKIP, INIT e NOINIT  
 La tabella seguente descrive le interazioni tra le { **NOINIT** | INIT} e { **NOSKIP** | Opzioni SKIP}.  
  
> [!NOTE]  
>  Se il nastro è vuoto oppure il file di backup su disco non esiste, tutte le interazioni comportano la scrittura di un'intestazione supporto prima di continuare l'operazione. Se i supporti non sono vuoti e non è presente un'intestazione supporto valida, viene segnalata la presenza di supporti MTF non validi e l'operazione di backup viene interrotta.  
  
||NOINIT|INIT|  
|------|------------|----------|  
|NOSKIP|Se il volume contiene un'intestazione supporto valida, consente di verificare che il nome del supporto corrisponda al valore di MEDIANAME, se specificato. Se il nome corrisponde, il set di backup viene accodato, mantenendo tutti i set di backup esistenti.<br /> Se il volume non contiene un'intestazione supporto valida, viene generato un errore.|Se il volume contiene un'intestazione supporto valida, vengono effettuati i controlli seguenti:<br /> -Se è stato specificato MEDIANAME, verifica che il nome di file multimediale specificato corrisponda multimediale name.* * l'intestazione supporto<br /> -Consente di verificare che non esistono alcun set di backup non scaduti nel supporto. In caso contrario, il backup viene interrotto.<br /> Se i controlli hanno esito positivo, gli eventuali set di backup presenti nel supporto vengono sovrascritti, mantenendo solo l'intestazione.<br /> Se il volume non contiene un'intestazione supporto valida, ne viene generata automaticamente una con i valori specificati per MEDIANAME e MEDIADESCRIPTION, se disponibili.|  
|SKIP|Se il volume contiene un'intestazione supporto valida, il set di backup viene accodato, mantenendo tutti i set di backup esistenti.|Se il volume contiene un valore valido * intestazione supporto, sovrascrive qualsiasi set di backup nei supporti, mantenendo solo l'intestazione.<br /> Se il supporto è vuoto, viene generata un'intestazione utilizzando i valori specificati per MEDIANAME e MEDIADESCRIPTION, se disponibili.|  
  
 * Validità include il numero di versione MTF e altre informazioni sull'intestazione. Se la versione specificata non è supportata o ha un valore imprevisto, viene generato un errore.  
  
 * * L'utente deve appartenere al appropriato ruolo predefinito del database o del server per eseguire un'operazione di backup.  
  
## <a name="compatibility"></a>Compatibilità  
  
> [!CAUTION]  
>  I backup creati nella versione più recente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non possono essere ripristinati nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 L'istruzione BACKUP supporta l'opzione RESTART per garantire la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'opzione RESTART non ha tuttavia alcun effetto.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 È possibile accodare i backup di database o log in qualsiasi disco o dispositivo nastro, in modo che il database e i relativi log delle transazioni possano essere mantenuti nella stessa posizione fisica.  
  
 Non è possibile utilizzare l'istruzione BACKUP in una transazione esplicita o implicita.  
  
 È possibile eseguire operazioni di backup tra piattaforme diverse e anche tra tipi di processore diversi, a condizione che le regole di confronto del database siano supportate dal sistema operativo.  
  
> [!NOTE]  
>  Per impostazione predefinita, per ogni operazione di backup eseguita in modo corretto viene aggiunta una voce al log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e al registro eventi di sistema. Se il backup del log viene eseguito di frequente, questi messaggi possono aumentare rapidamente, provocando la creazione di log degli errori di dimensioni elevate e rendendo difficile l'individuazione di altri messaggi. In questi casi è possibile eliminare tali voci di log utilizzando il flag di traccia 3226 se nessuno degli script dipende da esse. Per altre informazioni, vedere [Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).  
  
## <a name="interoperability"></a>Interoperabilità  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito un processo di backup online per consentire l'esecuzione del backup di un database mentre il database è ancora in uso. Durante un backup, è possibile eseguire la maggior parte delle operazioni, ad esempio istruzioni INSERT, UPDATE o DELETE.  
  
 Le operazioni di cui non è consentita l'esecuzione durante un backup del database o del log delle transazioni sono le seguenti:  
  
-   Operazioni di gestione dei file, come l'istruzione ALTER DATABASE con l'opzione ADD FILE o REMOVE FILE.  
  
-   Compattazione di database o file, incluse operazioni di compattazione automatica.  
  
Se un'operazione di backup si sovrappone a un'operazione di compattazione o di gestione dei file, viene generato un conflitto. Indipendentemente dall'operazione iniziata per prima tra quelle in conflitto, la seconda operazione attende il timeout del blocco impostato dalla prima operazione. Il periodo di timeout dipende da un'impostazione di timeout di sessione. Se il blocco viene rilasciato entro il periodo di timeout, la seconda operazione continua. Se il periodo di timeout scade, la seconda operazione non viene eseguita.  
  
## <a name="metadata"></a>Metadati  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono incluse le tabelle di cronologia di backup seguenti, utilizzate per tenere traccia delle attività di backup:  
  
-   [backupfile &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
-   [backupfilegroup &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
-   [backupmediafamily &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
-   [backupmediaset &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
-   [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
Quando viene eseguito un ripristino, se il set di backup non è già stato registrato nel **msdb** database, la cronologia di backup tabelle potrebbero essere state modificate.  
  
## <a name="security"></a>Security  
 A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], **PASSWORD** e **MEDIAPASSWORD** non sono più disponibili le opzioni per la creazione di backup. È comunque possibile ripristinare backup creati con password.  
  
### <a name="permissions"></a>Permissions  
 Le autorizzazioni BACKUP DATABASE e BACKUP LOG vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** e dei ruoli predefiniti del database **db_owner** e **db_backupoperator** .  
  
 Eventuali problemi correlati alla proprietà e alle autorizzazioni sul file fisico del dispositivo di backup possono interferire con l'operazione di backup. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia possibile leggere e scrivere sul dispositivo e che l'account utilizzato per eseguire il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponga delle autorizzazioni di scrittura. Le autorizzazioni di accesso ai file, tuttavia, non vengono controllate dalla stored procedure [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)che aggiunge una voce per un dispositivo di backup nelle tabelle di sistema. Di conseguenza, i problemi relativi all'accesso e alla proprietà del file fisico del dispositivo di backup potrebbero emergere solo in fase di accesso alla risorsa fisica durante un tentativo di backup o ripristino.  
  
##  <a name="examples"></a> Esempi  
 In questa sezione sono disponibili gli esempi seguenti:  
  
-   A. [Backup di un database completo](#backing_up_db)  
-   B. [Backup del database e log](#backing_up_db_and_log)  
-   C. [Creazione di un backup completo del file dei filegroup secondari](#full_file_backup)  
-   D. [Creazione di un backup di file differenziale dei filegroup secondari](#differential_file_backup)  
-   E. [Creazione e il backup su un singolo supporti con mirroring impostato](#create_single_family_mirrored_media_set)  
-   F. [Creazione e il backup su un supporti con mirroring con più gruppi impostato](#create_multifamily_mirrored_media_set)  
-   G [set di supporti con mirroring di backup esistente](#existing_mirrored_media_set)  
-   H. [Creazione di un backup compresso in un nuovo set di supporti](#creating_compressed_backup_new_media_set)  
-   I.  [Esecuzione del backup il servizio di archiviazione Blob di Microsoft Azure](#url)  
  
> [!NOTE]  
>  Ulteriori esempi sono inclusi negli argomenti relativi alle procedure di backup. Per altre informazioni, vedere [Panoramica del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
###  <a name="backing_up_db"></a> A. Backup di un database completo  
 Nell'esempio seguente viene eseguito il backup di [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database in un file su disco.  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH FORMAT;  
GO  
```  
  
###  <a name="backing_up_db_and_log"></a> B. Backup del database e del log  
 Nell'esempio seguente viene eseguito il backup del database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], per il quale viene utilizzato per impostazione predefinita il modello di recupero con registrazione minima. Per consentire il backup del log, il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] viene modificato per l'utilizzo del modello di recupero con registrazione completa.  
  
 Successivamente, l'esempio Usa [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md) per creare una logica [dispositivo di backup](../../relational-databases/backup-restore/backup-devices-sql-server.md) per il backup dei dati, `AdvWorksData`e crea un altro dispositivo di backup logico per il backup del log, `AdvWorksLog`.  
  
 Nell'esempio viene infine creato un backup completo del database in `AdvWorksData` e, dopo un periodo dedicato alle attività di aggiornamento, viene eseguito il backup del log in `AdvWorksLog`.  
  
```sql  
-- To permit log backups, before the full database backup, modify the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
   SET RECOVERY FULL;  
GO  
-- Create AdvWorksData and AdvWorksLog logical backup devices.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'AdvWorksData',   
'Z:\SQLServerBackups\AdvWorksData.bak';  
GO  
EXEC sp_addumpdevice 'disk', 'AdvWorksLog',   
'X:\SQLServerBackups\AdvWorksLog.bak';  
GO  
  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012 TO AdvWorksData;  
GO  
-- Back up the AdventureWorks2012 log.  
BACKUP LOG AdventureWorks2012  
   TO AdvWorksLog;  
GO  
```  
  
> [!NOTE]  
>  Per i database di produzione, eseguire il backup del log regolarmente. La frequenza dei backup del log dovrà essere tale da consentire una protezione sufficiente per evitare perdite di dati.  
  
###  <a name="full_file_backup"></a> C. Creazione di un backup completo dei filegroup secondari  
 Nell'esempio seguente viene creato un backup completo di ogni file presente in entrambi i filegroup secondari.  
  
```sql  
--Back up the files in SalesGroup1:  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'Z:\SQLServerBackups\SalesFiles.bck';  
GO  
```  
  
###  <a name="differential_file_backup"></a> D. Creazione di un backup differenziale dei filegroup secondari  
 Nell'esempio seguente viene creato un backup differenziale di ogni file presente in entrambi i filegroup secondari.  
  
```sql  
--Back up the files in SalesGroup1:  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'Z:\SQLServerBackups\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
###  <a name="create_single_family_mirrored_media_set"></a> E. Creazione di un set di supporti con mirroring con un singolo gruppo di supporti ed esecuzione di un backup in tale set  
 Nell'esempio seguente viene creato un set di supporti con mirroring contenente un singolo gruppo di supporti e quattro mirror, quindi viene eseguito il backup del database [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] in tali supporti.  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0'  
MIRROR TO TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2'  
MIRROR TO TAPE = '\\.\tape3'  
WITH  
   FORMAT,  
   MEDIANAME = 'AdventureWorksSet0';  
```  
  
###  <a name="create_multifamily_mirrored_media_set"></a> F. Creazione di un set di supporti con mirroring con più gruppi di supporti ed esecuzione di un backup in tale set  
 Nell'esempio seguente viene creato un set di supporti con mirroring in cui ogni mirror è composto da due gruppi di supporti. Viene quindi eseguito il backup del database [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] in entrambi i mirror.  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
   FORMAT,  
   MEDIANAME = 'AdventureWorksSet1';  
```  
  
###  <a name="existing_mirrored_media_set"></a>G. Backup in un set di supporti con mirroring esistente  
 Nell'esempio seguente un set di backup viene accodato al set di supporti creato nell'esempio precedente.  
  
```sql  
BACKUP LOG AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH   
   NOINIT,  
   MEDIANAME = 'AdventureWorksSet1';  
```  
  
> [!NOTE]  
>  L'opzione predefinita NOINIT viene specificata in modo esplicito nell'istruzione per maggiore chiarezza.  
  
###  <a name="creating_compressed_backup_new_media_set"></a>H. Creazione di un backup compresso in un nuovo set di supporti  
 Nell'esempio seguente vengono formattati i supporti, creando un nuovo set di supporti, e viene eseguito un backup compresso completo del database [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)].  
  
```sql  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   COMPRESSION;  
```  

###  <a name="url"></a>I. Eseguire il backup nel servizio di archiviazione BLOB di Microsoft Azure 
Nell'esempio viene eseguito un backup completo del database `Sales` al servizio di archiviazione Blob di Microsoft Azure.  Il nome dell'account di archiviazione è `mystorageaccount`, mentre  il nome del contenitore è `myfirstcontainer`.  Sono stati creati criteri di accesso archiviati con diritti di lettura, scrittura ed elenco.  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credenziale, `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`, è stato creato utilizzando una firma di accesso condiviso associata a criteri di accesso archiviati.  Per informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup per il servizio di archiviazione Blob di Windows Azure, vedere [SQL Server Backup e ripristino con il servizio di archiviazione Blob di Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) e [Backup di SQL Server nell'URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md).

```sql  
BACKUP DATABASE Sales
TO URL = 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_20160726.bak'
WITH STATS = 5;
```

  
## <a name="see-also"></a>Vedere anche  
 [Dispositivi di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Backup della parte finale del log &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [DBCC SQLPERF &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_helpfile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_helpfilegroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Ripristino a fasi di database con tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/piecemeal-restore-of-databases-with-memory-optimized-tables.md)  
  
  

