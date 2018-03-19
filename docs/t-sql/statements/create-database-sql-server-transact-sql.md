---
title: CREATE DATABASE (Transact-SQL di SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_TSQL
- DATABASE
- CONTAINMENT_TSQL
- CREATE DATABASE
- CREATE_DATABASE_TSQL
- CONTAINS_FILESTREAM_TSQL
- CONTAINS FILESTREAM
- CONTAINMENT
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], creating
- databases [SQL Server], creating
- model database [SQL Server], database creation
- mounted drives [SQL Server]
- CREATE DATABASE
- CREATE DATABASE statement
- file creation [SQL Server]
- creating databases
- containment
- filegroups [SQL Server], database creation
- database creation [SQL Server], CREATE DATABASE statement
- moving databases
- attaching databases [SQL Server], CREATE DATABASE...FOR ATTACH
ms.assetid: 29ddac46-7a0f-4151-bd94-75c1908c89f8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c6e52f8e36ed40e18c2aeab162a75c39f186c97
ms.sourcegitcommit: 82c9868b5bf95e5b0c68137ba434ddd37fc61072
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="create-database-sql-server-transact-sql"></a>CREATE DATABASE (Transact-SQL di SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo database e i file utilizzati per archiviare il database, uno snapshot del database oppure collega un database dai file scollegati di un database creato in precedenza.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  

Creazione di un database    

```  
CREATE DATABASE database_name   
[ CONTAINMENT = { NONE | PARTIAL } ]  
[ ON   
      [ PRIMARY ] <filespec> [ ,...n ]   
      [ , <filegroup> [ ,...n ] ]   
      [ LOG ON <filespec> [ ,...n ] ]   
]   
[ COLLATE collation_name ]  
[ WITH  <option> [,...n ] ]  
[;]  
  
<option> ::=  
{  
      FILESTREAM ( <filestream_option> [,...n ] )  
    | DEFAULT_FULLTEXT_LANGUAGE = { lcid | language_name | language_alias }  
    | DEFAULT_LANGUAGE = { lcid | language_name | language_alias }  
    | NESTED_TRIGGERS = { OFF | ON }  
    | TRANSFORM_NOISE_WORDS = { OFF | ON}  
    | TWO_DIGIT_YEAR_CUTOFF = <two_digit_year_cutoff>   
    | DB_CHAINING { OFF | ON }  
    | TRUSTWORTHY { OFF | ON }  
}  
  
<filestream_option> ::=  
{  
      NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
    | DIRECTORY_NAME = 'directory_name'   
}  
  
<filespec> ::=   
{  
(  
    NAME = logical_file_name ,  
    FILENAME = { 'os_file_name' | 'filestream_path' }   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB | % ] ]  
)  
}  
  
<filegroup> ::=   
{  
FILEGROUP filegroup name [ [ CONTAINS FILESTREAM ] [ DEFAULT ] | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    <filespec> [ ,...n ]  
}  
  
<service_broker_option> ::=  
{  
    ENABLE_BROKER  
  | NEW_BROKER  
  | ERROR_BROKER_CONVERSATIONS  
}  
  
```  
 
Collegare un database    

```  
CREATE DATABASE database_name   
    ON <filespec> [ ,...n ]   
    FOR { { ATTACH [ WITH <attach_database_option> [ , ...n ] ] }  
        | ATTACH_REBUILD_LOG }  
[;]  
  
<attach_database_option> ::=  
{  
      <service_broker_option>  
    | RESTRICTED_USER  
    | FILESTREAM ( DIRECTORY_NAME = { 'directory_name' | NULL } )  
}   
```  
  
Creare uno snapshot del database    

```  
CREATE DATABASE database_snapshot_name   
    ON   
    (  
        NAME = logical_file_name,  
        FILENAME = 'os_file_name'   
    ) [ ,...n ]   
    AS SNAPSHOT OF source_database_name  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del nuovo database. I nomi dei database devono essere univoci all'interno di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed essere conformi alle regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 *database_name* può essere composto da un massimo di 128 caratteri, eccetto i casi in cui non è stato specificato un nome logico per il file di log. Se non è stato specificato un nome logico per il file di log, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera *logical_file_name* e *os_file_name* per il log accodando un suffisso a *database_name*. Questo limita il numero di caratteri di *database_name* a 123 per fare in modo che il nome di file logico generato includa un massimo di 128 caratteri.  
  
 Se non è stato specificato alcun nome file di dati, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa *database_name* sia come *logical_file_name* che come *os_file_name*. Il percorso predefinito viene ottenuto dal Registro di sistema. Il percorso predefinito può essere modificato tramite **Proprietà server (pagina Impostazioni database)** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. La modifica del percorso predefinito richiede il riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 CONTAINMENT = { NONE | PARTIAL }  

**Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Viene specificato lo stato di indipendenza del database. NONE = Database non indipendente. PARTIAL = database parzialmente indipendente.  
  
 ON  
 Specifica che i file su disco utilizzati per archiviare le sezioni di dati del database (file di dati) vengono definiti in modo esplicito. ON è obbligatorio quando è seguito da un elenco di valori delimitato da virgole di elementi \<filespec> che definiscono i file di dati per il filegroup primario. L'elenco di file del filegroup primario può essere seguito da un elenco di valori delimitati da virgole facoltativo di elementi \<filegroup> che definiscono i filegroup utente e i relativi file.  
  
 PRIMARY  
 Specifica che l'elenco \<filespec> associato definisce il file primario. Il primo file specificato nella voce \<filespec> nel filegroup primario diventa il file primario. Un database può includere un solo file primario. Per altre informazioni, vedere [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 Se la parola chiave PRIMARY viene omessa, il primo file elencato nell'istruzione CREATE DATABASE diventa il file primario.  
  
 LOG ON  
 Specifica che i file su disco utilizzati per archiviare il log del database (file di log) vengono definiti in modo esplicito. LOG ON è seguito da un elenco di valori delimitati da virgole di elementi \<filespec> che definiscono i file di log. Se la parola chiave LOG ON viene omessa, viene creato automaticamente un singolo file di log con dimensioni pari al 25% della somma delle dimensioni di tutti i file di dati del database o pari a 512 KB, a seconda del valore maggiore. Questo file viene posizionato nel percorso predefinito del file di log. Per informazioni su questa posizione, vedere [Visualizzare o modificare i percorsi predefiniti per i file di dati e di log &#40;SQL Server Management Studio&#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
 Non è possibile specificare LOG ON in uno snapshot del database.  
  
 COLLATE *collation_name*  
 Specifica le regole di confronto predefinite per il database. È possibile usare nomi di regole di confronto di Windows o SQL. Se collation_name viene omesso, al database vengono assegnate le regole di confronto predefinite dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non è possibile specificare un nome di regole di confronto in uno snapshot del database.  
  
 Non è possibile specificare un nome di regole di confronto con le clausole FOR ATTACH o FOR ATTACH_REBUILD_LOG. Per informazioni sulla modifica delle regole di confronto di un database collegato, visitare il [sito Web Microsoft](http://go.microsoft.com/fwlink/?linkid=16419&kbid=325335).  
  
 Per altre informazioni sui nomi delle regole di confronto Windows e SQL, vedere [COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md).  
  
> [!NOTE]  
>  Le regole di confronto per i database indipendenti sono diverse rispetto a quelle dei database non indipendenti. Per altre informazioni, vedere [Regole di confronto dei database indipendenti](../../relational-databases/databases/contained-database-collations.md).  
  
 WITH \<option>  
 -   **\<filestream_options>** 
  
     NON_TRANSACTED_ACCESS = { **OFF** | READ_ONLY | FULL }  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
     Specifica il livello di accesso FILESTREAM non transazionale al database.  
  
    |valore|Description|  
    |-----------|-----------------|  
    |OFF|L'accesso non transazionale è disabilitato.|  
    |READONLY|I dati FILESTREAM di questo database possono essere letti da processi non transazionali.|  
    |FULL|L'accesso non transazionale completo a tabelle FileTable FILESTREAM è abilitato.|  
  
     DIRECTORY_NAME = \<directory_name> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     Nome di directory compatibile con Windows. Il nome deve essere univoco in tutti i nomi di Database_Directory nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il confronto di univocità non supporta la distinzione tra maiuscole e minuscole, indipendentemente dalle impostazioni delle regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È necessario impostare questa opzione prima di creare una tabella FileTable in questo database.  
  
 Le opzioni seguenti sono consentite solo quando CONTAINMENT è stato impostato su PARTIAL. Se l'opzione CONTAINMENT è impostata su NONE, si verificheranno errori.  
  
-   **DEFAULT_FULLTEXT_LANGUAGE = \<lcid> | \<language name> | \<language alias>**  
  
**Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default full-text language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) for a full description of this option.  
  
-   **DEFAULT_LANGUAGE = \<lcid> | \<language name> | \<language alias>**  
  
**Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) for a full description of this option.  
  
-   **NESTED_TRIGGERS = { OFF | ON}**  
  
**Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the nested triggers Server Configuration Option](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) for a full description of this option.  
  
-   **TRANSFORM_NOISE_WORDS = { OFF | ON}**  
  
**Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)for a full description of this option.  
  
-   **TWO_DIGIT_YEAR_CUTOFF = { 2049 | \<qualsiasi anno compreso tra il 1753 e il 9999> }**  
  
     Quattro cifre che rappresentano un anno. Il valore predefinito è 2049. Per una descrizione completa di questa opzione, vedere [Configurare l'opzione di configurazione del server two-digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).  
  
-   **DB_CHAINING { OFF | ON }**  
  
     Se l'opzione è impostata su ON, il database può essere l'origine o la destinazione di una catena di proprietà tra database.  
  
     Se l'opzione è impostata su OFF, il database non può partecipare alla catena di proprietà tra database. Il valore predefinito è OFF.  
  
    > [!IMPORTANT]  
    >  Questa impostazione viene riconosciuta dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando l'opzione del server cross db ownership chaining è impostata su 0 (OFF). Quando cross db ownership chaining è 1 (ON), tutti i database utente possono partecipare ai concatenamenti della proprietà tra database, a prescindere dal valore di questa opzione. Questa opzione viene impostata tramite [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
     Per impostare questa opzione è richiesta l'appartenenza al ruolo predefinito del server sysadmin. L'opzione DB_CHAINING non può essere impostata in questi database di sistema: master, model, tempdb.  
  
-   **TRUSTWORTHY { OFF | ON }**  
  
     Se l'opzione è impostata su ON, i moduli del database (ad esempio le viste, le funzioni definite dall'utente o le stored procedure) che utilizzano un contesto di rappresentazione possono accedere alle risorse esterne al database.  
  
     Se l'opzione è impostata su OFF, i moduli del database in un conteso di rappresentazione non possono accedere alle risorse esterne al database. Il valore predefinito è OFF.  
  
     L'opzione TRUSTWORTHY viene impostata su OFF ogni volta che il database viene collegato.  
  
     Per impostazione predefinita, in tutti i database di sistema, a eccezione del database msdb, TRUSTWORTHY è impostata su OFF. Per i database model e tempdb questo valore non può essere modificato. È consigliabile evitare di impostare l'opzione TRUSTWORTHY su ON per il database master.  
  
     Per impostare questa opzione è richiesta l'appartenenza al ruolo predefinito del server sysadmin.  
  
 FOR ATTACH [ WITH \< attach_database_option > ] Specifica che il database viene creato [collegando](../../relational-databases/databases/database-detach-and-attach-sql-server.md) un set di file esistente del sistema operativo. È necessario che una voce dell'elenco \<filespec> specifichi il file primario. Le altre voci \<filespec> obbligatorie sono quelle relative ai file con percorso diverso rispetto al percorso usato in fase di creazione del database o al momento dell'ultimo collegamento del database stesso. Per questi file è necessario specificare una voce \<filespec>.  
  
 FOR ATTACH richiede le seguenti condizioni:  
  
-   Tutti i file di dati (MDF e NDF) devono essere disponibili.  
  
-   Tutti i file di log esistenti devono essere disponibili.  
  
 Se un database in lettura/scrittura contiene un singolo file di log attualmente non disponibile, e il database è stato chiuso senza utenti o transazioni aperte prima dell'operazione di collegamento, FOR ATTACH ricompila automaticamente il file di log e aggiorna il file primario. Per un database in sola lettura, invece, non è possibile ricostruire il log perché il file primario non può essere aggiornato. Pertanto, quando si collega un database in sola lettura a un log non disponibile, è necessario specificare i file o i file di log nella clausola FOR ATTACH.  
  
> [!NOTE]  
>  Un database creato con una versione più recente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può essere collegato con versioni precedenti.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tutti i file full-text inclusi nel database che viene collegato verranno collegati insieme al database. Per specificare un nuovo percorso per il catalogo full-text, specificare la nuova posizione senza il nome del file del sistema operativo full-text. Per altre informazioni, vedere la sezione Esempi.  
  
 Il collegamento di un database contenente un'opzione FILESTREAM "directory name" a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiede a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di verificare che il nome Database_Directory sia univoco. Se non lo è, l'operazione di collegamento ha esito negativo e viene restituito l'errore "FILESTREAM Database_Directory name \<name> is not unique in this SQL Server instance" (FILESTREAM con nome Database_Directory <name> non univoco in questa istanza di SQL Server). Per evitare questo errore, è necessario passare il parametro facoltativo *directory_name* a questa operazione.  
  
 Non è possibile specificare FOR ATTACH in uno snapshot del database.  
  
 FOR ATTACH può specificare l'opzione RESTRICTED_USER. RESTRICTED_USER consente la connessione al database solo ai membri del ruolo predefinito del database db_owner e ai membri dei ruoli predefiniti del server dbcreator e sysadmin, senza tuttavia imporre un limite al numero di connessioni. Tentativi dagli utenti non qualificati vengono rifiutati.  
  
 Se il database usa [!INCLUDE[ssSB](../../includes/sssb-md.md)], usare WITH \<service_broker_option> nella clausola FOR ATTACH: 
  
 \<service_broker_option> Controlla il recapito dei messaggi di [!INCLUDE[ssSB](../../includes/sssb-md.md)] e l'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] per il database. È possibile specificare le opzioni di [!INCLUDE[ssSB](../../includes/sssb-md.md)] solo quando viene utilizzata la clausola FOR ATTACH.  
  
 ENABLE_BROKER  
 Indica che [!INCLUDE[ssSB](../../includes/sssb-md.md)] è abilitato per il database specificato. In altre parole, viene avviato il recapito dei messaggi e is_broker_enabled viene impostato su true nella vista del catalogo sys.databases. Il database mantiene l'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] esistente.  
  
 NEW_BROKER  
 Crea un nuovo valore di service_broker_guid sia in sys.databases che nel database ripristinato e termina tutti gli endpoint di conversazione con l'eliminazione. Service Broker è abilitato, ma agli endpoint di conversazione remoti non viene inviato alcun messaggio. Tutte le route che fanno riferimento all'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] precedente devono essere ricreate con il nuovo identificatore.  
  
 ERROR_BROKER_CONVERSATIONS  
 Termina tutte le conversazioni e restituisce un errore che indica che il database è collegato o ripristinato. Service Broker viene disabilitato fino al termine dell'operazione e quindi viene riabilitato. Il database mantiene l'identificatore di [!INCLUDE[ssSB](../../includes/sssb-md.md)] esistente.  
  
 Quando si collega un database replicato copiato anziché scollegato, è necessario considerare quanto segue:  
  
-   Se si collega il database alla stessa istanza del server e alla stessa versione del database originale, non sono necessari passaggi aggiuntivi.  
  
-   Se si collega il database alla stessa istanza del server ma si usa una versione aggiornata, dopo il completamento dell'operazione di collegamento è necessario eseguire [sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md) per aggiornare la replica.  
  
-   Se si collega il database a un'istanza del server diversa, indipendentemente dalla versione, dopo il completamento dell'operazione di collegamento è necessario eseguire [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) per rimuovere la replica.  
  
> [!NOTE]  
> Il collegamento supporta il formato di archiviazione **vardecimal**, ma è necessario aggiornare il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] almeno a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2. Non è possibile collegare un database con un formato di archiviazione vardecimal a una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni sul formato di archiviazione **vardecimal**, vedere [Compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
 Quando un database viene collegato per la prima volta a una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o ripristinato, nel server non è ancora archiviata una copia della chiave master del database, crittografata dalla chiave master del servizio. È necessario usare l'istruzione **OPEN MASTER KEY** per decrittografare la chiave master del database. Dopo aver decrittografato la DMK, è possibile usare l'istruzione **ALTER MASTER KEY REGENERATE** per abilitare la decrittografia automatica per le operazioni successive, in modo da fornire al server una copia della DMK crittografata con la chiave master del servizio (SMK). Quando un database è stato aggiornato da una versione precedente, la DMK deve essere rigenerata per usare l'algoritmo AES più recente. Per altre informazioni sulla rigenerazione della DMK, vedere [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md). Il tempo richiesto per rigenerare la chiave DMK e aggiornarla ad AES dipende dal numero di oggetti protetti dalla DMK. È necessario rigenerare la chiave DMK per l'aggiornamento ad AES una sola volta e l'operazione non influenza le rigenerazioni future che fanno parte di una strategia di rotazione della chiave. Per informazioni su come aggiornare un database tramite collegamento, vedere [Aggiornamento di un database usando le operazioni di scollegamento e collegamento &#40;Transact-SQL&#41;](../../relational-databases/databases/upgrade-a-database-using-detach-and-attach-transact-sql.md).  
  
> [!IMPORTANT]  
> È consigliabile non collegare database da origini sconosciute o non attendibili. Tali database possono contenere codice dannoso che potrebbe eseguire codice [!INCLUDE[tsql](../../includes/tsql-md.md)] indesiderato o causare errori modificando lo schema o la struttura fisica di database. Prima di usare un database da un'origine sconosciuta o non attendibile, eseguire [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sul database in un server non di produzione ed esaminare il codice contenuto nel database, ad esempio le stored procedure o altro codice definito dall'utente.  
  
> [!NOTE]  
> Le opzioni **TRUSTWORTHY** e **DB_CHAINING** non hanno effetto quando si collega un database.  
  
 FOR ATTACH_REBUILD_LOG  
 Specifica che il database viene creato collegando un set di file del sistema operativo già esistente. Questa opzione è limitata ai database in lettura/scrittura. È necessaria una voce *\<filespec>* che specifichi il file primario. Se uno o più file di log delle transazioni sono mancanti, il file di log viene ricostruito. Il log ATTACH_REBUILD_LOG crea automaticamente un nuovo file di log da 1 MB. Questo file viene posizionato nel percorso predefinito del file di log. Per informazioni su questa posizione, vedere [Visualizzare o modificare i percorsi predefiniti per i file di dati e di log &#40;SQL Server Management Studio&#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
> [!NOTE]  
>  Se i file di log sono disponibili, [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilizza questi file invece di ricompilare i file di log.  
  
 FOR ATTACH_REBUILD_LOG richiede le seguenti condizioni:  
  
-   Una chiusura normale del database.  
  
-   Tutti i file di dati (MDF e NDF) devono essere disponibili.  
  
> [!IMPORTANT]  
> Questa operazione interrompe la catena di backup del log. È consigliabile eseguire un backup completo del database al termine dell'operazione. Per altre informazioni, vedere [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
 In genere, l'opzione FOR ATTACH_REBUILD_LOG viene utilizzata quando si copia un database in lettura/scrittura con un log di grandi dimensioni in un altro server dove la copia verrà utilizzata principalmente, o esclusivamente, per operazioni di lettura e richiederà quindi una quantità minore di spazio di log rispetto al database originale.  
  
 Non è possibile specificare FOR ATTACH_REBUILD_LOG in uno snapshot del database.  
  
 Per altre informazioni sul collegamento e lo scollegamento di database, vedere [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
 \<filespec>  
 Controlla le proprietà del file.  
  
 NAME *logical_file_name*  
 Specifica il nome logico per il file. Il parametro NAME è necessario quando FILENAME è specificato, eccetto quando viene specificata una delle clausole FOR ATTACH. Non è possibile assegnare il nome PRIMARY a un filegroup FILESTREAM.  
  
 *logical_file_name*  
 Nome logico utilizzato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per fare riferimento al file. *Logical_file_name* deve essere univoco all'interno del database e conforme alle regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md). Il nome può essere un carattere o una costante Unicode oppure un identificatore normale o delimitato.  
  
 FILENAME { **'***os_file_name***'** | **'***filestream_path***'** }  
 Specifica il nome del file (fisico) del sistema operativo.  
  
 **'** *os_file_name* **'**  
 Percorso e nome di file utilizzato dal sistema operativo quando si crea il file. Il file deve risiedere in uno dei dispositivi seguenti: il server locale in cui è installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], una rete di archiviazione (SAN) o una rete basata su iSCSI. Il percorso specificato deve essere esistente prima dell'esecuzione dell'istruzione CREATE DATABASE. Per altre informazioni, vedere "Filegroup e file di database" nella sezione Osservazioni.  
  
 È possibile impostare i parametri SIZE, MAXSIZE e FILEGROWTH se è specificato un percorso UNC per il file.  
  
 Se il file si trova in una partizione non formattata, nell'argomento *os_file_name* è necessario specificare solo la lettera dell'unità di una partizione non formattata esistente. È possibile creare soltanto un file di dati su ogni partizione non formattata dal sistema operativo.  
  
 I file di dati non devono essere archiviati in file system compressi a meno che non si tratti di file secondari in sola lettura o il database non sia in sola lettura. I file di log non devono mai essere archiviati in file system compressi.  
  
 **'** *filestream_path* **'**  
 Per un filegroup FILESTREAM, FILENAME si riferisce a un percorso in cui verrà archiviato FILESTREAM. È necessario che il percorso fino all'ultima cartella esista già, mentre l'ultima cartella non deve essere presente. Se, ad esempio, si specifica il percorso C:\MyFiles\MyFilestreamData, C:\MyFiles deve esistere già prima di eseguire ALTER DATABASE, mentre la cartella MyFilestreamData non deve essere presente.  
  
 Il filegroup e il file (`<filespec>`) devono essere creati nella stessa istruzione.  
  
 Le proprietà SIZE e FILEGROWTH non si applicano a un filegroup FILESTREAM.  
  
 SIZE *size*  
 Specifica le dimensioni del file.  
  
 Non è possibile specificare SIZE quando *os_file_name* è specificato come percorso UNC. SIZE non si applica a un filegroup FILESTREAM.  
  
 *size*  
 Dimensioni iniziali del file.  
  
 Se non si specifica *size* per il file primario, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] usa le dimensioni del file primario del database modello. Le dimensioni predefinite del modello corrispondono a 8 MB (a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) o a 1 MB (per le versioni precedenti). Se si specifica un file di dati o un file di log secondario senza specificare *size* per il file, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] crea un file di 8 MB (a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) o di 1 MB (per le versioni precedenti). Le dimensioni specificate per il file di dati primario devono essere uguali almeno alle dimensioni del file primario del database model.  
  
 È possibile usare i suffissi per kilobyte (KB), megabyte (MB), gigabyte (GB) e terabyte (TB). Il valore predefinito è MB. Specificare un numero intero, ovvero non includere decimali. *Size* è un valore intero. Per i valori superiori a 2.147.483.647, usare le unità maggiori.  
  
 MAXSIZE *max_size*  
 Valore massimo fino a cui possono aumentare le dimensioni del file. Non è possibile specificare MAXSIZE quando *os_file_name* è specificato come percorso UNC.  
  
 *max_size*  
 Dimensioni massime del file. È possibile usare i suffissi KB, MB, GB e TB. Il valore predefinito è MB. Specificare un numero intero, ovvero non includere decimali. Se *max_size* viene omesso, le dimensioni del file aumentano fino all'esaurimento dello spazio su disco. *Max_size* è un valore intero. Per i valori superiori a 2.147.483.647, usare le unità maggiori.  
  
 UNLIMITED  
 Specifica che le dimensioni del file aumentano fino a quando il disco risulta pieno. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un file di log specificato con aumento delle dimensioni illimitato può raggiungere una dimensione massima di 2 TB, mentre un file di dati può raggiungere una dimensione massima di 16 TB.  
  
> [!NOTE]  
> Non vi sono dimensioni massime se questa opzione viene specificata per un contenitore FILESTREAM, il quale continua a crescere finché il disco non è pieno.  
  
 FILEGROWTH *growth_increment*  
 Specifica l'incremento automatico per l'aumento delle dimensioni del file. Il valore impostato per il parametro FILEGROWTH di un file non può essere superiore al valore del parametro MAXSIZE. Non è possibile specificare FILEGROWTH quando *os_file_name* è specificato come percorso UNC. FILEGROWTH non si applica a un filegroup FILESTREAM.  
  
 *growth_increment*  
 Quantità di spazio aggiunta al file ogni volta che è necessario spazio aggiuntivo.  
  
 È possibile specificare il valore in megabyte (MB), kilobyte (KB), gigabyte (GB) o terabyte (TB) oppure in forma di percentuale (%). Se si specifica un valore senza il suffisso MB, KB o %, il suffisso predefinito è MB. Se si utilizza il suffisso %, l'incremento corrisponde alla percentuale delle dimensioni del file specificata quando si verifica l'incremento. Le dimensioni specificate vengono arrotondate al blocco di 64 KB più prossimo e il valore minimo è 64 KB.  
  
 Un valore 0 indica che l'opzione per l'aumento automatico è disattivata e non è consentito spazio aggiuntivo.  
  
 Se FILEGROWTH viene omesso, i valori predefiniti sono:  
  
|Versione|Valori predefiniti|  
|-------------|--------------------|  
|Inizio [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|Dati 64 MB. File di log 64 MB.|  
|Inizio [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Dati 1 MB. File di log 10%.|  
|Prima di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Dati 10%. File di log 10%.|  
  
 \<filegroup>  
 Controlla le proprietà del filegroup. Non è possibile specificare il filegroup in uno snapshot del database.  
  
 FILEGROUP *filegroup_name*  
 Nome logico del filegroup.  
  
 *filegroup_name*  
 *filegroup_name* deve essere univoco nel database e deve essere diverso dai nomi PRIMARY e PRIMARY_LOG forniti dal sistema. Il nome può essere un carattere o una costante Unicode oppure un identificatore normale o delimitato. Il nome deve essere conforme alle regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 CONTAINS FILESTREAM  
 Specifica che tramite il filegroup vengono archiviati oggetti binari di grandi dimensioni (BLOB) nel file system.  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**Si applica a**: da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Specifica che il filegroup archivia i dati memory_optimized nel file system. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). È ammesso un solo filegroup MEMORY_OPTIMIZED_DATA per database. Per esempi di codice che creano un filegroup per l'archiviazione di dati ottimizzati per la memoria, vedere [Creazione di una tabella ottimizzata per la memoria e di una stored procedure compilata in modo nativo](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
 DEFAULT  
 Indica che il filegroup specificato è il filegroup predefinito nel database.  
  
 *database_snapshot_name*  
 Nome del nuovo snapshot del database. I nomi dei database devono essere univoci all'interno di un'istanza d [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e devono essere conformi alle regole per gli identificatori. *database_snapshot_name* può essere composto da un massimo di 128 caratteri.  
  
 ON **(** NAME **=***logical_file_name***,** FILENAME **='***os_file_name***')** [ **,**... *n* ]  
 Per la creazione di uno snapshot del database, specifica un elenco di file nel database di origine. Per il funzionamento dello snapshot, è necessario specificare tutti i file di dati singolarmente. I file di log non sono tuttavia consentiti per gli snapshot del database. I filegroup FILESTREAM non sono supportati dagli snapshot del database. Se un file di dati FILESTREAM è incluso in una clausola CREATE DATABASE ON, l'istruzione non verrà eseguita e sarà generato un errore.  
  
 Per le descrizioni di NAME e FILENAME e i rispettivi valori, vedere le descrizioni dei valori \<filespec> equivalenti.  
  
> [!NOTE]  
> Quando si crea uno snapshot del database, le altre opzioni \<filespec> e la parola chiave PRIMARY non sono consentite.  
  
 AS SNAPSHOT OF *source_database_name*  
 Specifica che il database in fase di creazione è uno snapshot del database di origine specificato da *source_database_name*. Lo snapshot e il database di origine devono essere archiviati nella stessa istanza.  
  
 Per altre informazioni, vedere "Snapshot di database" nella sezione Osservazioni.  
  
## <a name="remarks"></a>Remarks  
 Il backup del [database master](../../relational-databases/databases/master-database.md) deve essere eseguito ogni volta che si crea, si modifica o si rilascia un database utente.  
  
 L'istruzione CREATE DATABASE deve essere eseguita in modalità autocommit, la modalità predefinita per la gestione delle transazioni, e non è consentita in una transazione esplicita o implicita.  
  
 È possibile usare un'istruzione CREATE DATABASE per creare un database e i file che lo archiviano. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa l'istruzione CREATE DATABASE tramite i passaggi seguenti:  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa una copia del [database modello](../../relational-databases/databases/model-database.md) per inizializzare il database e i relativi metadati.  
  
2.  Un GUID di Service Broker viene assegnato al database.  
  
3.  Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] compila quindi la parte rimanente del database con pagine vuote, ad eccezione delle pagine con dati interni che registrano la modalità di utilizzo dello spazio nel database.  
  
 In un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]è possibile specificare al massimo 32.767 database.  
  
 Ogni database ha un proprietario che può eseguire attività particolari nel database. Il proprietario è l'utente che crea il database. Il proprietario del database può essere modificato tramite [sp_changedbowner](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md).  

Alcune funzionalità del database dipendono dalle caratteristiche o dalle funzionalità presenti nel file system per la disponibilità completa delle funzionalità del database. Ecco alcuni esempi di funzionalità che dipendono dal set di funzionalità del file system:
- DBCC CHECKDB
- FileStream
- Backup online tramite il Servizio Copia Shadow del volume e gli snapshot dei file
- Creazione di snapshot del database
- Filegroup di dati ottimizzati per la memoria
   
## <a name="database-files-and-filegroups"></a>Filegroup e file di database  
 Ogni database ha almeno due file, un *file primario* e un *file registro transazioni*, e almeno un filegroup. Per ogni database è possibile specificare un massimo di 32.767 file e 32.767 filegroup.  
  
 Durante la creazione di un database, creare file di dati di dimensioni corrispondenti alla quantità massima di dati che si prevede di includere nel database.  
  
 Per l'archiviazione dei file di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è consigliabile usare una rete di archiviazione (SAN), una rete basata su iSCSI o un disco collegato localmente, poiché questa configurazione ottimizza le prestazioni e l'affidabilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="database-snapshots"></a>Snapshot di database  
 È possibile usare l'istruzione CREATE DATABASE per creare una visualizzazione statica, di sola lettura, uno *snapshot* del *database di origine*. Uno snapshot del database è consistente dal punto di vista transazionale con il database di origine al momento della creazione dello snapshot. Un database di origine può avere più snapshot.  
  
> [!NOTE]  
> Quando si crea uno snapshot di database, l'istruzione CREATE DATABASE non può far riferimento a file di log, file offline, file di ripristino e file inattivi.  
  
 Se la creazione di uno snapshot di database ha esito negativo, lo snapshot diventa sospetto e deve essere eliminato. Per altre informazioni, vedere [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Ogni snapshot viene mantenuto fino a quando non viene eliminato tramite DROP DATABASE.  
  
 Per altre informazioni, vedere [Snapshot del database &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="database-options"></a>Opzioni di database  
 Quando si crea un database, vengono impostate automaticamente diverse opzioni. Per un elenco di queste opzioni, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="the-model-database-and-creating-new-databases"></a>Database modello e creazione di nuovi database  
 Tutti gli oggetti definiti dall'utente inclusi nel [database modello](../../relational-databases/databases/model-database.md) vengono copiati in tutti i nuovi database. È possibile aggiungere al database model qualsiasi oggetto che si desidera includere in tutti i database appena creati, ad esempio tabelle, viste, stored procedure, tipi di dati e così via.  
  
 Quando si specifica un'istruzione CREATE DATABASE *database_name* senza parametri di dimensione aggiuntivi, per il file di dati primario vengono usate le dimensioni del file primario nel database modello.  
  
 A meno che non si specifichi FOR ATTACH, ogni nuovo database eredita le impostazioni delle opzioni di database dal database model. Ad esempio, l'opzione di database auto shrink viene impostata su **true** nel database modello e in tutti i nuovi database creati. Se si modificano le opzioni nel database model, queste nuove impostazioni vengono utilizzate in tutti i nuovi database creati. La modifica delle operazioni nel database model non ha effetto sui database esistenti. Se viene specificata l'opzione FOR ATTACH nell'istruzione CREATE DATABASE, i nuovi database ereditano le impostazioni delle opzioni di database dal database originale.  
  
## <a name="viewing-database-information"></a>Visualizzazione delle informazioni sui database  
 Per restituire informazioni su database, file e filegroup, è possibile usare viste del catalogo, funzioni di sistema e stored procedure di sistema. Per altre informazioni, vedere [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CREATE DATABASE, CREATE ANY DATABASE o ALTER ANY DATABASE.  
  
 Per mantenere il controllo sull'utilizzo del disco per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'autorizzazione per la creazione dei database è in genere limitata a pochi account di accesso.  
  
 Nell'esempio seguente viene fornita l'autorizzazione per creare un database per l'utente del database Fay.  
  
```sql  
USE master;  
GO  
GRANT CREATE DATABASE TO [Fay];  
GO  
```  
  
### <a name="permissions-on-data-and-log-files"></a>Autorizzazioni per i file di dati e di log  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono impostate autorizzazioni specifiche per i file di dati e di log in ogni database. Le autorizzazioni seguenti vengono impostate quando le operazioni elencate di seguito vengono eseguite in un database.  
  
|||  
|-|-|  
|Data creazione|Modifica per l'aggiunta di un nuovo file|  
|Collegamento|Esecuzione del backup|  
|Scollegamento|Ripristino|  
  
 Con le autorizzazioni è possibile evitare che vengano accidentalmente alterati i file che si trovano in una directory con autorizzazioni aperte.  
  
> [!NOTE]  
> In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] non vengono impostate autorizzazioni per i file di dati e di log.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-database-without-specifying-files"></a>A. Creazione di un database senza specificare i file  
 Nell'esempio seguente viene creato il database `mytest` insieme al file di log delle transazioni e al file primario corrispondenti. Poiché l'istruzione non specifica elementi \<filespec>, le dimensioni del file di database primario corrispondono a quelle del file primario del database modello. Il file di log delle transazioni viene impostato sul valore più grande tra 512 KB o il 25% delle dimensioni del file di dati primario. Poiché MAXSIZE non è specificato, le dimensioni dei file possono aumentare fino a riempire lo spazio disponibile su disco. In questo esempio viene inoltre illustrato come eliminare l'eventuale database denominato `mytest` prima di creare il database `mytest`.  
  
```sql  
USE master;  
GO  
IF DB_ID (N'mytest') IS NOT NULL
DROP DATABASE mytest;
GO
CREATE DATABASE mytest;  
GO  
-- Verify the database files and sizes  
SELECT name, size, size*1.0/128 AS [Size in MBs]   
FROM sys.master_files  
WHERE name = N'mytest';  
GO  
```  
  
### <a name="b-creating-a-database-that-specifies-the-data-and-transaction-log-files"></a>B. Creazione di un database che specifica i file di dati e i file di log delle transazioni  
 Nell'esempio seguente viene creato il database `Sales`. Dal momento che la parola chiave PRIMARY non è specificata, il primo file, cioè `Sales_dat`, corrisponde al file primario. Poiché nel parametro SIZE non viene specificato il suffisso MB o KB per le dimensioni del file `Sales_dat` , viene utilizzato MB e le dimensioni del file vengono allocate in megabyte. Il backup del database `Sales_log` vengono allocate in megabyte perché nel parametro `MB` è stato specificato in modo esplicito il suffisso `SIZE` .  
  
```sql  
USE master;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="c-creating-a-database-by-specifying-multiple-data-and-transaction-log-files"></a>C. Creazione di un database specificando più file di dati e più file di log delle transazioni  
 Nell'esempio seguente viene creato il database `Archive` che include tre file di dati da `100-MB` e due file del log delle transazioni da `100-MB`. Il file primario è il primo file dell'elenco e viene specificato in modo esplicito con la parola chiave `PRIMARY`. I file di log delle transazioni vengono specificati dopo le parole chiave `LOG ON`. Si notino le estensioni utilizzate per i file nell'opzione `FILENAME`: `.mdf` per i file di dati primari, `.ndf` per i file di dati secondari e `.ldf` per i file di log delle transazioni. In questo esempio il database viene collocato nell'unità `D:` anziché con il database `master`.  
  
```sql  
USE master;  
GO  
CREATE DATABASE Archive   
ON  
PRIMARY    
    (NAME = Arch1,  
    FILENAME = 'D:\SalesData\archdat1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch2,  
    FILENAME = 'D:\SalesData\archdat2.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch3,  
    FILENAME = 'D:\SalesData\archdat3.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20)  
LOG ON   
   (NAME = Archlog1,  
    FILENAME = 'D:\SalesData\archlog1.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
   (NAME = Archlog2,  
    FILENAME = 'D:\SalesData\archlog2.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20) ;  
GO  
```  
  
### <a name="d-creating-a-database-that-has-filegroups"></a>D. Creazione di un database con filegroup  
 Nell'esempio seguente viene creato il database `Sales` che include i filegroup seguenti:  
  
-   Il filegroup primario con i file `Spri1_dat` e `Spri2_dat`. Gli incrementi specificati nel parametro FILEGROWTH per tali file corrispondono al `15%`.  
  
-   Un filegroup `SalesGroup1` con i file `SGrp1Fi1` e `SGrp1Fi2`.  
  
-   Un filegroup `SalesGroup2` con i file `SGrp2Fi1` e `SGrp2Fi2`.  
  
 In questo esempio i file di dati e di log vengono collocati in dischi diversi al fine di migliorare le prestazioni.  
  
```sql  
USE master;  
GO  
CREATE DATABASE Sales  
ON PRIMARY  
( NAME = SPri1_dat,  
    FILENAME = 'D:\SalesData\SPri1dat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
( NAME = SPri2_dat,  
    FILENAME = 'D:\SalesData\SPri2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
FILEGROUP SalesGroup1  
( NAME = SGrp1Fi1_dat,  
    FILENAME = 'D:\SalesData\SG1Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp1Fi2_dat,  
    FILENAME = 'D:\SalesData\SG1Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
FILEGROUP SalesGroup2  
( NAME = SGrp2Fi1_dat,  
    FILENAME = 'D:\SalesData\SG2Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp2Fi2_dat,  
    FILENAME = 'D:\SalesData\SG2Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'E:\SalesLog\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="e-attaching-a-database"></a>E. Collegamento di un database  
 Nell'esempio seguente viene scollegato il database `Archive` creato nell'esempio D, quindi viene collegato tramite la clausola `FOR ATTACH`. `Archive` è stato definito in modo da avere più dati e file di log. Tuttavia, poiché il percorso dei file non è stato modificato dopo la creazione, deve essere specificato solo il file primario nella clausola `FOR ATTACH`. A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], tutti i file full-text inclusi nel database in fase di collegamento verranno collegati assieme al database.  
  
```sql  
USE master;  
GO  
sp_detach_db Archive;  
GO  
CREATE DATABASE Archive  
      ON (FILENAME = 'D:\SalesData\archdat1.mdf')   
      FOR ATTACH ;  
GO  
```  
  
### <a name="f-creating-a-database-snapshot"></a>F. Creazione di uno snapshot del database  
 L'esempio seguente crea lo snapshot di database `sales_snapshot0600`. Poiché uno snapshot di database è in sola lettura, non è possibile specificare un file di log. In conformità con la sintassi, viene specificato ogni file nel database di origine, mentre i filegroup non vengono specificati.  
  
 Il database di origine per questo esempio è il database `Sales` creato nell'esempio D.  
  
```sql  
USE master;  
GO  
CREATE DATABASE sales_snapshot0600 ON  
    ( NAME = SPri1_dat, FILENAME = 'D:\SalesData\SPri1dat_0600.ss'),  
    ( NAME = SPri2_dat, FILENAME = 'D:\SalesData\SPri2dt_0600.ss'),  
    ( NAME = SGrp1Fi1_dat, FILENAME = 'D:\SalesData\SG1Fi1dt_0600.ss'),  
    ( NAME = SGrp1Fi2_dat, FILENAME = 'D:\SalesData\SG1Fi2dt_0600.ss'),  
    ( NAME = SGrp2Fi1_dat, FILENAME = 'D:\SalesData\SG2Fi1dt_0600.ss'),  
    ( NAME = SGrp2Fi2_dat, FILENAME = 'D:\SalesData\SG2Fi2dt_0600.ss')  
AS SNAPSHOT OF Sales ;  
GO  
```  
  
### <a name="g-creating-a-database-and-specifying-a-collation-name-and-options"></a>G. Creazione di un database e specifica di un nome delle regole di confronto e delle opzioni  
 Nell'esempio seguente viene creato il database `MyOptionsTest`. Viene specificato un nome delle regole di confronto e le opzioni `TRUSTYWORTHY` e `DB_CHAINING` vengono impostate su `ON`.  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE French_CI_AI  
WITH TRUSTWORTHY ON, DB_CHAINING ON;  
GO  
--Verifying collation and option settings.  
SELECT name, collation_name, is_trustworthy_on, is_db_chaining_on  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
```  
  
### <a name="h-attaching-a-full-text-catalog-that-has-been-moved"></a>H. Collegamento di un catalogo full-text che è stato spostato  
 Nell'esempio seguente viene collegato il catalogo full-text `AdvWksFtCat` insieme ai file di log e di dati di `AdventureWorks2012`. In questo esempio, il catalogo full-text viene spostato dalla posizione predefinita in una nuova posizione `c:\myFTCatalogs`. I file di dati e di log rimangono nelle posizioni predefinite.  
  
```sql  
USE master;  
GO  
--Detach the AdventureWorks2012 database  
sp_detach_db AdventureWorks2012;  
GO  
-- Physically move the full text catalog to the new location.  
--Attach the AdventureWorks2012 database and specify the new location of the full-text catalog.  
CREATE DATABASE AdventureWorks2012 ON   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_data.mdf'),   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf'),  
    (FILENAME = 'c:\myFTCatalogs\AdvWksFtCat')  
FOR ATTACH;  
GO  
```  
  
### <a name="i-creating-a-database-that-specifies-a-row-filegroup-and-two-filestream-filegroups"></a>I. Creazione di un database che specifica un filegroup di righe e due filegroup FILESTREAM  
 Nell'esempio seguente viene creato il database `FileStreamDB`. Il database viene creato con un filegroup di righe e due filegroup FILESTREAM. Ogni filegroup contiene un file:  
  
-   `FileStreamDB_data` contiene dati delle righe. Contiene un file, `FileStreamDB_data.mdf`, con il percorso predefinito.  
  
-   `FileStreamPhotos` contiene dati FILESTREAM. Contiene due contenitori di dati FILESTREAM, `FSPhotos` nel percorso `C:\MyFSfolder\Photos` e `FSPhotos2` nel percorso `D:\MyFSfolder\Photos`. È contrassegnato come filegroup FILESTREAM predefinito.  
  
-   `FileStreamResumes` contiene dati FILESTREAM. Contiene un contenitore di dati FILESTREAM, ossia `FSResumes` nel percorso `C:\MyFSfolder\Resumes`.  
  
```sql  
USE master;  
GO  
-- Get the SQL Server data path.  
DECLARE @data_path nvarchar(256);  
SET @data_path = (SELECT SUBSTRING(physical_name, 1, CHARINDEX(N'master.mdf', LOWER(physical_name)) - 1)  
                  FROM master.sys.master_files  
                  WHERE database_id = 1 AND file_id = 1);  
  
 -- Execute the CREATE DATABASE statement.   
EXECUTE ('CREATE DATABASE FileStreamDB  
ON PRIMARY   
    (  
    NAME = FileStreamDB_data   
    ,FILENAME = ''' + @data_path + 'FileStreamDB_data.mdf''  
    ,SIZE = 10MB  
    ,MAXSIZE = 50MB  
    ,FILEGROWTH = 15%  
    ),  
FILEGROUP FileStreamPhotos CONTAINS FILESTREAM DEFAULT  
    (  
    NAME = FSPhotos  
    ,FILENAME = ''C:\MyFSfolder\Photos''  
-- SIZE and FILEGROWTH should not be specified here.  
-- If they are specified an error will be raised.  
, MAXSIZE = 5000 MB  
    ),  
    (  
      NAME = FSPhotos2  
      , FILENAME = ''D:\MyFSfolder\Photos''  
      , MAXSIZE = 10000 MB  
     ),  
FILEGROUP FileStreamResumes CONTAINS FILESTREAM  
    (  
    NAME = FileStreamResumes  
    ,FILENAME = ''C:\MyFSfolder\Resumes''  
    )   
LOG ON  
    (  
    NAME = FileStream_log  
    ,FILENAME = ''' + @data_path + 'FileStreamDB_log.ldf''  
    ,SIZE = 5MB  
    ,MAXSIZE = 25MB  
    ,FILEGROWTH = 5MB  
    )'  
);  
GO  
```  
  
### <a name="j-creating-a-database-that-has-a-filestream-filegroup-with-multiple-files"></a>J. Creazione di un database contenente un filegroup FILESTREAM con più file  
 Nell'esempio seguente viene creato il database `BlobStore1`. Il database viene creato con un filegroup di righe e un filegroup FILESTREAM, `FS`. Nel filegroup FILESTREAM sono contenuti due file, vale a dire `FS1` e `FS2`. Successivamente il database viene modificato con l'aggiunta di un terzo file, `FS3`, al filegroup FILESTREAM.  
  
```sql  
USE master;  
GO  
  
CREATE DATABASE [BlobStore1]  
CONTAINMENT = NONE  
ON PRIMARY   
(   
    NAME = N'BlobStore1',   
    FILENAME = N'C:\BlobStore\BlobStore1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = UNLIMITED,  
    FILEGROWTH = 1MB  
),   
FILEGROUP [FS] CONTAINS FILESTREAM DEFAULT   
(  
    NAME = N'FS1',  
    FILENAME = N'C:\BlobStore\FS1',  
    MAXSIZE = UNLIMITED  
),   
(  
    NAME = N'FS2',  
    FILENAME = N'C:\BlobStore\FS2',  
    MAXSIZE = 100MB  
)  
LOG ON   
(  
    NAME = N'BlobStore1_log',  
    FILENAME = N'C:\BlobStore\BlobStore1_log.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 1GB,  
    FILEGROWTH = 1MB  
);  
GO  
  
ALTER DATABASE [BlobStore1]  
ADD FILE  
(  
    NAME = N'FS3',  
    FILENAME = N'C:\BlobStore\FS3',  
    MAXSIZE = 100MB  
)  
TO FILEGROUP [FS];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_changedbowner &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Snapshot del database &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)   
 [Spostare file del database](../../relational-databases/databases/move-database-files.md)   
 [Database](../../relational-databases/databases/databases.md)   
 [Dati BLOB &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)  

