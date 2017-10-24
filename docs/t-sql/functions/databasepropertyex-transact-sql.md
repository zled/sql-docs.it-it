---
title: DATABASEPROPERTYEX (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASEPROPERTYEX
- DATABASEPROPERTYEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DATABASEPROPERTYEX function
- displaying database properties
- database properties [SQL Server]
ms.assetid: 8a9e0ffb-28b5-4640-95b2-a54e3e5ad941
caps.latest.revision: 84
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 737aed43128be71a53c8087be11176bc4e364e8a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="databasepropertyex-transact-sql"></a>DATABASEPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce l'impostazione corrente dell'opzione o proprietà del database specificato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATABASEPROPERTYEX ( database , property )  
```  
  
## <a name="arguments"></a>Argomenti  
*database*  
È un'espressione che rappresenta il nome del database per cui restituire le informazioni sulle proprietà denominate. *database* è **nvarchar (128)**.  
Per [!INCLUDE[ssSDS](../../includes/sssds-md.md)] deve essere il nome del database corrente. Restituisce NULL per tutte le proprietà se viene specificato un nome di database diverso.
  
*proprietà*  
Espressione che rappresenta il nome della proprietà del database da restituire. *proprietà* è **varchar (128)**, e può essere uno dei valori seguenti. Il tipo restituito è **sql_variant**. Nella tabella seguente viene indicato il tipo di dati di base per ogni valore di questo argomento.
  
> [!NOTE]  
>  Se il database non è avviato, le proprietà recuperate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante l'accesso diretto al database anziché mediante il recupero del valore dai metadati restituiranno NULL, ovvero se l'opzione AUTO_CLOSE è stata impostata su ON nel database oppure il database è offline.  
  
|Proprietà|Description|Valore restituito|  
|---|---|---|
|Confronto|Nome delle regole di confronto predefinite per il database.|Nome delle regole di confronto.<br /><br /> NULL = Database non in linea.<br /><br /> Tipo di dati di base: **nvarchar (128)**|  
|ComparisonStyle|Stile di confronto di Windows per le regole di confronto. ComparisonStyle è una mappa di bit calcolata utilizzando i seguenti valori per gli stili di possibili.<br /><br /> Ignora maiuscole / minuscole: 1<br /><br /> Ignora accento: 2<br /><br /> Ignora Kana: 65536<br /><br /> Ignora larghezza: 131072<br /><br /> <br /><br /> Il valore predefinito 196609, ad esempio, è il risultato della combinazione delle opzioni Ignora maiuscole/minuscole, Ignora Kana e Ignora larghezza.|Restituisce lo stile di confronto.<br /><br /> Restituisce 0 per tutte le regole di confronto binarie.<br /><br /> Tipo di dati di base: **int**|  
|Edizione|Edizione o livello di servizio del database.|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].<br /><br /> <br /><br /> Web = database Web Edition<br /><br /> Business = database Business Edition<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium<br /><br /> System (per il database master)<br /><br /> NULL = Database non in linea.<br /><br /> Tipo di dati di base: **nvarchar**(64)|  
|IsAnsiNullDefault|Il database segue le regole ISO per il supporto dei valori Null.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAnsiNullsEnabled|Tutti i confronti con un valore Null restituiscono unknown.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAnsiPaddingEnabled|Le stringhe vengono riempite in modo che abbiano tutte la stessa lunghezza prima dell'esecuzione di confronti o inserimenti.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAnsiWarningsEnabled|Se si verificano condizioni di errore standard, vengono visualizzati messaggi di errore o di avviso.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsArithmeticAbortEnabled|Le query vengono interrotte se durante l'esecuzione si verifica un errore di overflow o di divisione per zero.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAutoClose|Il database viene chiuso correttamente e le risorse corrispondenti vengono liberate dopo la disconnessione dell'ultimo utente.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAutoCreateStatistics|In Query Optimizer vengono create statistiche di colonna singola, se necessario, per migliorare le prestazioni di esecuzione delle query.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAutoCreateStatisticsIncremental|Le statistiche di colonna singola create automaticamente sono, quando possibile, incrementali.|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAutoShrink|I file di database sono sottoposti periodicamente a compattazione automatica.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsAutoUpdateStatistics|Query Optimizer aggiorna le statistiche esistenti che potrebbero essere obsolete quando queste vengono utilizzate in una query.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|
|IsClone|Database è una copia di sola dello schema e le statistiche di un database utente.|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Service Pack 2.<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**| 
|IsCloseCursorsOnCommitEnabled|I cursori aperti durante l'esecuzione del commit di una transazione vengono chiusi.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsFulltextEnabled|Il database è abilitato per l'indicizzazione full-text e semantica.|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**<br /><br /> **Nota:** il valore di questa proprietà non ha alcun effetto. I database utente sono sempre abilitati per la ricerca full-text. Questa colonna verrà rimossa a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non utilizzarla in un nuovo progetto di sviluppo e modificare non appena possibile le applicazioni in cui tali colonne sono implementate.|  
|IsInStandBy|Il database è online in sola lettura e consente il ripristino di log.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsLocalCursorsDefault|Le dichiarazioni del cursore hanno come impostazione predefinita LOCAL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsMemoryOptimizedElevateToSnapshotEnabled|Le tabelle con ottimizzazione per la memoria sono accessibili tramite l'isolamento SNAPSHOT quando l'impostazione della sessione HIGH TRANSACTION ISOLATION LEVEL è impostata su un livello di isolamento inferiore, READ COMMITTED o READ UNCOMMITTED.|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Tipo di dati di base: **int**|  
|IsMergePublished|Se la replica è installata, è possibile pubblicare le tabelle di un database per l'esecuzione di una replica di tipo merge.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsNullConcat|Un operando di concatenazione Null produce un valore NULL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsNumericRoundAbortEnabled|In corrispondenza di una perdita di precisione nelle espressioni, vengono generati errori.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsParameterizationForced|L'opzione SET dell'hint di database PARAMETERIZATION è impostata su FORCED.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido|  
|IsQuotedIdentifiersEnabled|Per gli identificatori è possibile utilizzare virgolette doppie.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsPublished|Se la replica è installata, è possibile pubblicare le tabelle del database per l'esecuzione di una replica snapshot o transazionale.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsRecursiveTriggersEnabled|L'attivazione ricorsiva dei trigger è abilitata.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsSubscribed|Il database è sottoscritto a una pubblicazione.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsSyncWithBackup|Indica se il database è un database pubblicato o di distribuzione e se è possibile ripristinarlo senza ripercussioni sulla replica transazionale.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsTornPageDetectionEnabled|In [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] vengono rilevate le operazioni di I/O non completate a causa di un'interruzione dell'alimentazione o di altri malfunzionamenti del sistema.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido<br /><br /> Tipo di dati di base: **int**|  
|IsXTPSupported|Indica se il database supporta OLTP In memoria, ad esempio, la creazione e l'uso di tabelle con ottimizzazione per la memoria e moduli compilati in modo nativo.<br /><br /> Specifiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> IsXTPSupported è indipendente dell'esistenza di tutti i filegroup MEMORY_OPTIMIZED_DATA, che è necessario per la creazione di oggetti di OLTP In memoria.|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> **Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avvio [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido, un errore o non applicabile<br /><br /> Tipo di dati di base: **int**|  
|LCID|Identificatore delle impostazioni locali (LCID) di Windows per le regole di confronto.|Valore LCID, in formato decimale.<br /><br /> Tipo di dati di base: **int**|  
|MaxSizeInBytes|Dimensioni massime del database in byte.|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].<br /><br /> <br /><br /> 1073741824<br /><br /> 5368709120<br /><br /> 10737418240<br /><br /> 21474836480<br /><br /> 32212254720<br /><br /> 42949672960<br /><br /> 53687091200<br /><br /> NULL = database non avviato<br /><br /> Tipo di dati di base: **bigint**|  
|Recupero|Modello di recupero per il database.|FULL = Modello di recupero con registrazione completa<br /><br /> BULK_LOGGED = Modello di recupero con registrazione minima delle operazioni bulk<br /><br /> SIMPLE = Modello di recupero con registrazione minima<br /><br /> Tipo di dati di base: **nvarchar (128)**|  
|ServiceObjective|Viene descritto il livello di prestazioni del database in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] o [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|I possibili valori sono i seguenti:<br /><br /> Null = database non avviato<br /><br /> Shared (per le edizioni Web/Business)<br /><br /> Basic<br /><br /> S0<br /><br /> S1<br /><br /> S2<br /><br /> S3<br /><br /> P1<br /><br /> P2<br /><br /> P3<br /><br /> ElasticPool<br /><br /> System (per il database master)<br /><br /> Tipo di dati di base: **nvarchar(32)**|  
|ServiceObjectiveId|ID dell'obiettivo di servizio in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|**uniqueidentifier** che identifica l'obiettivo di servizio.|  
|SQLSortOrder|ID del tipo di ordinamento supportato nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|0 = Il database utilizza le regole di confronto di Windows<br /><br /> >0 = ID del tipo di ordinamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> NULL = Input non valido oppure database non avviato<br /><br /> Tipo di dati di base: **tinyint**|  
|Stato|Stato del database.|ONLINE = Il database è disponibile per le query.<br /><br /> **Nota:** lo stato ONLINE può essere restituito mentre il database viene aperto e non è ancora recuperato. Per identificare quando un database possono essere accettate connessioni, eseguire una query la proprietà delle regole di confronto di **DATABASEPROPERTYEX**. Nel database possono essere accettate connessioni quando tramite le regole di confronto del database viene restituito un valore non Null. Always On database, eseguire una query di Sys.dm hadr_database_replica_states database_state o database_state_desc colonne.<br /><br /> OFFLINE = Il database è stato portato offline in modo esplicito.<br /><br /> RESTORING = Il database è in fase di ripristino.<br /><br /> RECOVERING = Il database è in fase di recupero e non è ancora disponibile per le query.<br /><br /> SUSPECT = Non è possibile recuperare il database.<br /><br /> EMERGENCY = Il database è in modalità di emergenza e pertanto in modalità di accesso in sola lettura. L'accesso è limitato ai membri del ruolo sysadmin.<br /><br /> Tipo di dati di base: **nvarchar (128)**|  
|Updateability|Indica se è possibile modificare i dati.|READ_ONLY = È possibile leggere i file, ma non modificarli.<br /><br /> READ_WRITE = È possibile leggere e modificare i file.<br /><br /> Tipo di dati di base: **nvarchar (128)**|  
|UserAccess|Specifica gli utenti autorizzati ad accedere al database.|SINGLE_USER = Solo un utente db_owner, dbcreator o sysadmin alla volta<br /><br /> RESTRICTED_USER = Solo i membri dei ruoli db_owner, dbcreator e sysadmin<br /><br /> MULTI_USER = Tutti gli utenti<br /><br /> Tipo di dati di base: **nvarchar (128)**|  
|Versione|Numero di versione interno del codice [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con cui è stato creato il database. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|Numero di versione = Database aperto.<br /><br /> NULL = Database non in linea.<br /><br /> Tipo di dati di base: **int**|  
  
## <a name="return-types"></a>Tipi restituiti
**sql_variant**
  
## <a name="exceptions"></a>Eccezioni  
Restituisce NULL in caso di errore o se un chiamante non dispone dell'autorizzazione necessaria per visualizzare l'oggetto.
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come OBJECT_ID possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Osservazioni  
DATABASEPROPERTYEX restituisce un'impostazione della proprietà alla volta. Per visualizzare più impostazioni della proprietà, utilizzare il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-retrieving-the-status-of-the-autoshrink-database-option"></a>A. Recupero dello stato dell'opzione AUTO_SHRINK del database  
Nell'esempio seguente viene restituito lo stato dell'opzione AUTO_SHRINK per il database `AdventureWorks`.
  
```sql
SELECT DATABASEPROPERTYEX('AdventureWorks2014', 'IsAutoShrink');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)] Indica che l'opzione AUTO_SHRINK è disattivata.
  
```sql
------------------  
0  
```  
  
### <a name="b-retrieving-the-default-collation-for-a-database"></a>B. Recupero delle regole di confronto predefinite per un database  
L'esempio seguente restituisce i diversi attributi del `AdventureWorks` database.
  
```sql
SELECT   
    DATABASEPROPERTYEX('AdventureWorks2014', 'Collation') AS Collation,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'Edition') AS Edition,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'ServiceObjective') AS ServiceObjective,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'MaxSizeInBytes') AS MaxSizeInBytes  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Collation                     Edition        ServiceObjective  MaxSizeInBytes  
----------------------------  -------------  ----------------  --------------  
SQL_Latin1_General_CP1_CI_AS  DataWarehouse  DW1000            5368709120  
```  
  
## <a name="see-also"></a>Vedere anche
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[Stati del database](../../relational-databases/databases/database-states.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)
  
  

