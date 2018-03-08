---
title: "MODIFICARE il livello di compatibilità DATABASE (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 01/30/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COMPATIBILITY_LEVEL_TSQL
- COMPATIBILITY_LEVEL
dev_langs:
- TSQL
helpviewer_keywords:
- 80 compatibility level
- ALTER DATABASE statement, compatibility levels
- 90 compatibility level
- compatibility levels [SQL Server]
- 100 compatibility level
- db compatibility level
- db compat level
ms.assetid: ca5fd220-d5ea-4182-8950-55d4101a86f6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 750578d028077079b051a08cc2a0ed4276983cda
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="alter-database-transact-sql-compatibility-level"></a>ALTER DATABASE (Transact-SQL) Compatibility Level
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Imposta aspetti specifici del comportamento del database in modo che risultino compatibili con la versione specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre opzioni di ALTER DATABASE, vedere [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER DATABASE database_name   
SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database da modificare.  
  
 COMPATIBILITY_LEVEL {140 | 130 | 120 | 110 | 100 | 90 | 80}  
 Versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con cui il database deve risultare compatibile. È possibile configurare i valori di livello di compatibilità seguenti:  
  
|Prodotto|Versione del motore di database|Designazione di livello di compatibilità|Valori del livello di compatibilità supportato|  
|-------------|-----------------------------|-------------------------------------|------------------------------------------|  
|[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|14|140|140, 130, 120, 110, 100|
|[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|12|130|140, 130, 120, 110, 100|  
|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|13|130|130, 120, 110, 100|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|12|120|120, 110, 100|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|11|110|110, 100, 90|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|10.5|100|100, 90, 80|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|10|100|100, 90, 80|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|9|90|90, 80|  
|SQL Server 2000|8|80|80|  
  
> [!NOTE]  
> **Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]**  V12 è stato rilasciato nel dicembre 2014. Un aspetto di tale versione è che i database appena creati sono il livello di compatibilità impostato su 120. Nel 2015 SQL Database ha iniziato il supporto per il livello 130, anche se il valore predefinito è rimasta 120.  
> 
> A partire da **mid-giugno 2016**nella [!INCLUDE[ssSDS](../../includes/sssds-md.md)], il livello di compatibilità predefinito sono 130 anziché 120 per **appena creato** database. I database esistenti creati prima di medie-giugno 2016 non sono interessati e mantengono il livello di compatibilità corrente (100, 110 e 120). 
> 
> Se si desidera livello 130 per il database, in genere, ma è necessario preferire livello 110 **la stima della cardinalità** algoritmo, vedere [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md), in particolare la parola chiave `LEGACY_CARDINALITY_ESTIMATION = ON`.  
>  
>  Per informazioni dettagliate su come valutare le variazioni delle prestazioni delle query più importanti, tra i due livelli di compatibilità [!INCLUDE[ssSDS](../../includes/sssds-md.md)], vedere [migliorate le prestazioni delle Query con 130 livello di compatibilità in Database SQL di Azure](http://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).


 Eseguire la query seguente per determinare la versione del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a cui si è connessi.   
  
```sql  
SELECT SERVERPROPERTY('ProductVersion');  
```  
  
> [!NOTE]  
> Non tutte le funzionalità che variano in base al livello di compatibilità sono supportate in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  

 Per determinare il livello di compatibilità corrente, eseguire una query sulla colonna **compatibility_level** di [Sys. Databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
```sql  
SELECT name, compatibility_level FROM sys.databases;  
```  
  
## <a name="remarks"></a>Osservazioni  
Per tutte le installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il livello di compatibilità predefinito è impostato per la versione di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. I database sono impostati per questo livello, a meno che il **modello** database con un livello di compatibilità inferiore. Quando un database viene aggiornato da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il database mantiene il livello di compatibilità esistente se è almeno minimo consentito per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'aggiornamento di un database con un livello di compatibilità inferiore a quello consentito, imposta il database per la compatibilità più bassa livello è consentita. Questo comportamento si applica sia ai database di sistema che ai database utente. Utilizzare **ALTER DATABASE** per modificare il livello di compatibilità del database. Per visualizzare il livello di compatibilità corrente di un database, eseguire una query di **compatibility_level** colonna il [Sys. Databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista del catalogo.  
  
## <a name="using-compatibility-level-for-backward-compatibility"></a>Utilizzo del livello di compatibilità per garantire la compatibilità con le versioni precedenti  
 Il livello di compatibilità influisce solo sul comportamento del database specificato e non dell'intero server. Garantisce solo una compatibilità parziale con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A partire dalla modalità di compatibilità 130, le nuove funzionalità che influiscono sul piano di query sono presenti solo per la nuova modalità di compatibilità. Questa operazione è stata eseguita per ridurre al minimo il rischio causato da un calo delle prestazioni a causa di modifiche al piano di query durante gli aggiornamenti. Dal punto di vista dell'applicazione, l'obiettivo è ancora essere a livello di compatibilità più recente ereditando alcune delle nuove funzionalità, nonché i miglioramenti delle prestazioni eseguiti nello spazio del Query optimizer, ma in modo controllato. Utilizzare il livello di compatibilità come strumento di migrazione provvisoria per risolvere i problemi correlati alle differenze tra le versioni delle funzioni controllate dall'impostazione del livello di compatibilità pertinente. Per ulteriori informazioni, vedere le procedure consigliate aggiornamento avanti in questo articolo.  
  
 Se esistenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le applicazioni sono interessate da differenze funzionali introdotte nella versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], convertire l'applicazione per integrarsi perfettamente con la nuova modalità di compatibilità. Utilizzare quindi `ALTER DATABASE` per modificare il livello di compatibilità impostandolo su 130. La nuova impostazione di compatibilità per un database diventa effettivo quando un `USE <database>` viene eseguita o viene elaborato un nuovo account di accesso con il database come database predefinito.  
 
> [!IMPORTANT]
> Non più disponibile la funzionalità introdotta in un determinato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione non è protetto dal livello di compatibilità.
> 
> Ad esempio, il `FASTFIRSTROW` hint è stato rimosso in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e sostituiti con il `OPTION (FAST n )` hint. Impostare il livello di compatibilità 110 non ripristina l'hint non più supportata.
> Per ulteriori informazioni sulla funzionalità non più supportate, vedere [funzionalità di motore di Database non più disponibili in SQL Server 2016](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md), [funzionalità di motore di Database non più disponibili in SQL Server 2014](http://msdn.microsoft.com/library/ms144262(v=sql.120)), [Non più supportate funzionalità del motore di Database in SQL Server 2012](http://msdn.microsoft.com/library/ms144262(v=sql.110)), e [non più supportate funzionalità del motore di Database in SQL Server 2008](http://msdn.microsoft.com/library/ms144262(v=sql.100)).

> [!IMPORTANT]
> Modifiche di rilievo introdotte in un determinato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione **potrebbe** non è protetto dal livello di compatibilità. [!INCLUDE[tsql](../../includes/tsql-md.md)]comportamento in genere è protetto dal livello di compatibilità. Tuttavia, gli oggetti di sistema modificato o rimosso sono **non** protetto dal livello di compatibilità.
>
> Un esempio di una modifica di rilievo **protetti** per compatibilità livello è una conversione implicita da datetime a tipi di dati datetime2. Con il livello di compatibilità database 130, mostrano precisione migliorata prendendo il numero di millisecondi frazionari, risultante diversi i valori convertiti. Per ripristinare il comportamento di conversione precedente, impostare il livello di compatibilità del database o inferiore a 120.
>
> Esempi di modifiche di rilievo **non protetto** per compatibilità livello sono:
> -  Nomi di colonna in oggetti di sistema. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] la colonna *single_pages_kb* in sys.dm os_sys_info è stato rinominato in *pages_kb*. Indipendentemente dal livello di compatibilità, la query `SELECT single_pages_kb FROM sys.dm_os_sys_info` genererà l'errore 207 (nome di colonna non valida).
> -  Oggetti di sistema rimosso. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] il `sp_dboption` è stato rimosso. Indipendentemente dal livello di compatibilità, l'istruzione `EXEC sp_dboption 'AdventureWorks2016CTP3', 'autoshrink', 'FALSE';` genererà l'errore 2812 (Impossibile trovare la stored procedure 'sp_dboption').
>
> Per ulteriori informazioni sulle modifiche importanti, vedere [modifiche di rilievo alle funzionalità del motore di Database in SQL Server 2017](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2017.md), [modifiche di rilievo alle funzionalità del motore di Database in SQL Server 2016](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md), [ Le modifiche di rilievo al Database del motore funzionalità in SQL Server 2014](http://msdn.microsoft.com/library/ms143179(v=sql.120)), [modifiche di rilievo apportate alle funzionalità del motore di Database in SQL Server 2012](http://msdn.microsoft.com/library/ms143179(v=sql.110)), e [modifiche di rilievo apportate alle funzionalità del motore di Database in SQL Server 2008](http://msdn.microsoft.com/library/ms143179(v=sql.100)).
  
## <a name="best-practices"></a>Procedure consigliate  
Per il flusso di lavoro consigliato per l'aggiornamento del livello di compatibilità, vedere [Modificare la modalità di compatibilità del database e usare il Query Store](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
## <a name="compatibility-levels-and-stored-procedures"></a>Livelli di compatibilità e stored procedure  
 Quando si esegue una stored procedure, viene utilizzato il livello di compatibilità corrente del database in cui la procedura è definita. Se si modifica l'impostazione di compatibilità di un database, tutte le relative stored procedure vengono ricompilate automaticamente al fine di riflettere tale modifica.  

## <a name="differences-between-compatibility-level-130-and-level-140"></a>Differenze tra il livello di compatibilità 130 e 140  
In questa sezione vengono descritti i nuovi comportamenti introdotti con livello di compatibilità 140.

|Impostazione a livello di compatibilità minore o uguale a 130|Impostazione a livello di compatibilità 140|   
|--------------------------------------------------|-----------------------------------------|  
|Le stime della cardinalità per le istruzioni che fanno riferimento a funzioni tabella con istruzioni multiple utilizzano un'ipotesi basata su un numero di righe fisso.|Le stime della cardinalità per le istruzioni idonee che fanno riferimento a funzioni tabella con istruzioni multiple utilizzano la cardinalità effettiva dell'output della funzione. Questa opzione è abilitata tramite **esecuzione interleaved** per le funzioni tabella con istruzioni multiple.|
|Le query in modalità batch che richiedono memoria sufficiente concedono dimensioni che comporterà spill su disco potrebbe continuare la presenza di problemi in esecuzioni consecutive.|Query in modalità batch che richiedono le dimensioni di concessione di memoria insufficiente che comporterà spill su disco potrebbe avere prestazioni migliorate in esecuzioni consecutive. Questa opzione è abilitata tramite **commenti e suggerimenti di concessioni di memoria in modalità batch** che aggiornerà le dimensioni della concessione di memoria di un piano memorizzato nella cache se spill si sono verificati per gli operatori in modalità batch. |
|Le query in modalità batch che richiedono una quantità di memoria eccessiva dimensioni che comporta problemi di concorrenza può continuare ad avere problemi in esecuzioni consecutive della concessione.|Le query in modalità batch che richiedono una quantità di memoria eccessiva concedono potrebbero concorrenza in esecuzioni consecutive hanno migliorato le dimensioni che comporta problemi di concorrenza. Questa opzione è abilitata tramite **commenti e suggerimenti di concessioni di memoria in modalità batch** che verranno aggiornate le dimensioni della concessione di memoria di un piano memorizzato nella cache, se originariamente è stata richiesta una quantità eccessiva.|
|Le query in modalità batch contenenti gli operatori di join sono idonee per tre algoritmi di join fisico, tra cui ciclo nidificato, hash join e join di tipo merge. Se le stime della cardinalità non sono corrette per gli input di join, è possibile selezionare un algoritmo di join appropriato. In questo caso, le prestazioni ne risentiranno e l'algoritmo di join appropriato rimarrà in uso fino a quando non viene ricompilato il piano memorizzato nella cache.|È un operatore di join aggiuntiva denominato **join adattivo**. Se le stime della cardinalità non sono corrette per l'input di compilazione outer join, è possibile selezionare un algoritmo di join appropriato. Se l'istruzione è idoneo per un join adattivo in questo caso, verrà utilizzato un ciclo annidato per gli input di join più piccoli e un hash join verrà utilizzato per gli input di join più grandi in modo dinamico senza richiedere la ricompilazione. |
|I piani semplici con riferimento agli indici Columnstore non sono idonei per l'esecuzione in modalità batch. |I piani semplici con riferimento agli indici Columnstore verranno eliminati in favore di un piano idoneo per l'esecuzione in modalità batch.|
|Il `sp_execute_external_script` UDX-operatore può essere eseguito solo in modalità riga.|Il `sp_execute_external_script` UDX-operatore è idoneo per l'esecuzione in modalità batch.|  
|Funzioni a istruzioni multiple con valori di tabella (TVF) non dispone di esecuzione interleave |Esecuzione interleave per TVF con più istruzioni migliorare la qualità del piano. |

Correzioni che sono stati con il flag di traccia 4199 nelle versioni precedenti di SQL Server precedenti a SQL Server 2017 sono ora abilitate per impostazione predefinita. Con la modalità di compatibilità 140. Flag di traccia 4199 continuerà a essere applicabile per nuove correzioni di query optimizer che vengono rilasciate dopo SQL Server 2017. Per informazioni sui Flag di traccia 4199, vedere [Flag di traccia 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md#4199).  
  
## <a name="differences-between-compatibility-level-120-and-level-130"></a>Differenze tra il livello di compatibilità 120 e 130 livello  
In questa sezione vengono descritti i nuovi comportamenti introdotti con livello di compatibilità 130.   

|Impostazione a livello di compatibilità 120 minore o uguale|Impostazione a livello di compatibilità di 130|  
|--------------------------------------------------|-----------------------------------------|  
|L'inserimento in un'istruzione Insert select è a thread singolo.|L'inserimento in un'istruzione Insert select può essere multi-thread o disporre di un piano parallelo.|  
|Le query in una tabella con ottimizzazione per la memoria vengono eseguite a thread singolo.|Le query in una tabella con ottimizzazione per la memoria è ora possono avere piani paralleli.|  
|Strumento di stima della cardinalità di SQL 2014 introdotto **CardinalityEstimationModelVersion = "120"**|Cardinalità ulteriore piano miglioramenti di stima (CE) con la 130 modello di stima della cardinalità visibile da una Query. **CardinalityEstimationModelVersion="130"**|  
|Modalità batch e cambia la modalità di riga con gli indici Columnstore<br /><br /> Ordina in una tabella con indice Columnstore è in modalità riga<br /><br /> Aggregazioni funzione finestra operano in modalità a riga, ad esempio `LAG` o`LEAD`<br /><br /> Query sulle tabelle Columnstore con più clausole distinte usati in modalità riga<br /><br /> Query in esecuzione in MAXDOP 1 o con un piano seriale eseguito in modalità riga | Modalità batch e cambia la modalità di riga con gli indici Columnstore<br /><br /> Ordina in una tabella con un indice Columnstore è ora in modalità batch<br /><br /> Aggregazioni finestra ora eseguita in modalità batch, ad esempio `LAG` o`LEAD`<br /><br /> Query su tabelle Columnstore con più clausole distinte operano in modalità Batch<br /><br /> Le query in esecuzione in Maxdop1 o con un piano seriale eseguito in modalità Batch|  
| Le statistiche possono essere aggiornate automaticamente. | La logica che aggiorna automaticamente le statistiche è più aggressiva in tabelle di grandi dimensioni.  In pratica, questo dovrebbe ridurre i casi in cui i clienti registrano problemi di prestazioni per le query in cui le righe appena inserite non sono considerate dalle statistiche (statistiche non aggiornate). |  
| Il flag di traccia 2371 è impostato su OFF per impostazione predefinita in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. | [Il flag di traccia 2371](https://blogs.msdn.microsoft.com/psssql/2016/10/04/default-auto-statistics-update-threshold-change-for-sql-server-2016/) è impostato su ON per impostazione predefinita in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Il flag di traccia 2371 indica l'aggiornamento statistiche automatico per un subset più piccolo in una tabella con un elevato numero di righe. <br/> <br/> Un miglioramento consiste nell'includere nel campione alcune righe inserite di recente. <br/> <br/> Un altro miglioramento è quello di consentire le query di esecuzione durante il processo di aggiornamento delle statistiche, anziché bloccare la query. |  
| Per il livello 120, le statistiche vengono campionate da un *singolo*-thread di processo. | Per il livello 130, le statistiche vengono campionate da un *più*-thread di processo. |  
| Il limite di chiavi esterne in ingresso è 253. | Una tabella può fare riferimento fino a 10.000 chiavi esterne in ingresso. Per informazioni sulle restrizioni, vedere [Creare relazioni con chiavi estene](../../relational-databases/tables/create-foreign-key-relationships.md). |  
|Gli algoritmi di hash MD2, MD4, MD5, SHA e SHA1 deprecati sono consentiti.|Sono consentiti solo gli algoritmi di hash SHA2_256 e SHA2_512.|
||[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] include miglioramenti in alcune conversioni di tipi di dati e alcune operazioni (per lo più comune). Per informazioni dettagliate, vedere [SQL Server 2016 miglioramenti nella gestione di alcuni tipi di dati e operazioni meno frequenti](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon).|
  
Flag di correzioni che sono stati nella finestra di traccia 4199 nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] sono ora abilitati per impostazione predefinita. Con la modalità di compatibilità 130. Flag di traccia 4199 sarà comunque applicabile per nuove correzioni di query optimizer che vengono rilasciate dopo [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Per utilizzare query optimizer precedente in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è necessario selezionare il livello di compatibilità 110. Per informazioni sui Flag di traccia 4199, vedere [Flag di traccia 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md#4199).  
  
## <a name="differences-between-lower-compatibility-levels-and-level-120"></a>Differenze tra i livelli di compatibilità inferiori e il livello 120  
 Questa sezione descrive i nuovi comportamenti introdotti con il livello di compatibilità 120.  
  
|Livello di compatibilità 110 o inferiore|Livello di compatibilità 120|  
|--------------------------------------------------|-----------------------------------------|  
|Viene utilizzata la versione precedente di Query Optimizer.|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] include miglioramenti sostanziali al componente che crea e consente di ottimizzare i piani di query. Questa nuova funzionalità di Query Optimizer dipende dall'utilizzo del livello di compatibilità del database 120. Per sfruttare al meglio questi miglioramenti, sarebbe opportuno sviluppare le nuove applicazioni di database utilizzando il livello di compatibilità del database 120. Le applicazioni di cui si esegue la migrazione da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere testate con attenzione per assicurarsi che le prestazioni vengano mantenute o migliorate. Se si verifica un calo delle prestazioni, è possibile impostare il livello di compatibilità del database su 110 o su un valore inferiore per utilizzare la metodologia precedente di Query Optimizer.<br /><br /> Il livello di compatibilità 120 del database utilizza un nuovo strumento di stima della cardinalità ottimizzato per i carichi di lavoro OLTP e di data warehouse più recenti. Prima di impostare il livello di compatibilità del database su 110 a causa di problemi di prestazioni, vedere le indicazioni contenute nella sezione piani di Query del [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [novità nel motore di Database](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md) argomento.|  
|Nei livelli di compatibilità minori di 120 l'impostazione della lingua viene ignorata durante la conversione di una **data** in un valore stringa. Si noti che questo comportamento è specifico solo per il tipo **data**. Vedere l'esempio B nella sezione esempi riportata di seguito.|L'impostazione della lingua non viene ignorata durante la conversione di una **data** in un valore stringa.|  
|I riferimenti ricorsivi sul lato destro di un `EXCEPT` clausola creano un ciclo infinito. Esempio C, nella sezione esempi riportata di seguito viene illustrato questo comportamento.|Riferimenti ricorsivi in una `EXCEPT` clausola genera un errore in conformità allo standard ANSI SQL.|  
|Espressione di tabella comune ricorsiva (CTE) consente ai nomi di colonna duplicati.|Una CTE ricorsiva non consente i nomi di colonna duplicati.|  
|I trigger disabilitati vengono abilitati se i trigger vengono modificati.|La modifica di un trigger non cambia lo stato (abilitato o disabilitato) del trigger.|  
|La clausola OUTPUT INTO tabella ignora il `IDENTITY_INSERT SETTING = OFF` e consente l'inserimento di valori espliciti.|Non è possibile inserire valori espliciti per una colonna identity in una tabella quando `IDENTITY_INSERT` è impostata su OFF.|  
|Quando il contenimento del database è impostato su parziale, convalida il `$action` campo il `OUTPUT` clausola di un `MERGE` istruzione può restituire un errore di regole di confronto.|Le regole di confronto dei valori restituiti dal `$action` clausola di un `MERGE` istruzione sia le regole di confronto del database anziché le regole di confronto del server e non viene restituito un errore di conflitto tra regole di confronto.|  
|Tramite un'istruzione `SELECT INTO` viene sempre creata un'operazione di inserimento a thread singolo.|Tramite un'istruzione `SELECT INTO` è possibile creare un'operazione di inserimento parallela. Quando si inserisce un numero elevato di righe, con un'operazione parallela è possibile migliorare le prestazioni.|  
  
## <a name="differences-between-lower-compatibility-levels-and-levels-110-and-120"></a>Differenze tra i livelli di compatibilità inferiori e i livelli 110 e 120  
 Questa sezione descrive i nuovi comportamenti introdotti con il livello di compatibilità 110.   Questa sezione si applica al livello 120.  
  
|Livello di compatibilità 100 o inferiore|Impostazione del livello di compatibilità 110 o inferiore|  
|--------------------------------------------------|--------------------------------------------------|  
|Gli oggetti di database CLR (Common Language Runtime) vengono eseguiti con la versione 4 di CLR. Non sono tuttavia presenti alcune modifiche del comportamento introdotte con la versione 4 di CLR. Per ulteriori informazioni, vedere [novità di integrazione con CLR](../../relational-databases/clr-integration/clr-integration-what-s-new.md).|Gli oggetti di database CLR vengono eseguiti con la versione 4 di CLR.|  
|Le funzioni XQuery **lunghezza della stringa** e **sottostringa** considerano ciascun surrogato come due caratteri.|Le funzioni XQuery **lunghezza della stringa** e **sottostringa** considerano ciascun surrogato come un carattere.|  
|`PIVOT`è consentito in una query di espressione tabella comune ricorsiva. La query tuttavia restituisce risultati non corretti quando sono presenti più righe per raggruppamento.|`PIVOT`non è consentito in una query di espressione tabella comune ricorsiva. Viene restituito un errore.|  
|L'algoritmo RC4 è supportato solo per motivi di compatibilità con le versioni precedenti. È possibile crittografare il nuovo materiale usando RC4 o RC4_128 solo quando il livello di compatibilità del database è 90 o 100. (Non consigliato.) In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.|Il nuovo materiale non può essere crittografato utilizzando RC4 o RC4_128. Usare un algoritmo più recente, ad esempio uno degli algoritmi AES. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.|  
|Lo stile predefinito per `CAST` e `CONVERT` operazioni su **ora** e **datetime2** tipi di dati è 121, tranne quando uno dei due tipi viene utilizzato in un'espressione di colonna calcolata. Per le colonne calcolate, lo stile predefinito è 0. Questo comportamento influisce sulle colonne calcolate quando vengono create o usate nelle query con parametrizzazione automatica o nelle definizioni dei vincoli.<br /><br /> Nell'esempio D nella sezione esempi riportata di seguito viene illustrata la differenza tra gli stili 0 e 121. Non viene illustrato il comportamento descritto sopra. Per ulteriori informazioni sugli stili di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).|Con il livello di compatibilità 110, lo stile predefinito per `CAST` e `CONVERT` operazioni su **ora** e **datetime2** tipi di dati è sempre 121. Se la query si basa sul comportamento obsoleto, usare un livello di compatibilità inferiore a 110 oppure specificare in modo esplicito lo stile 0 nella query interessata.<br /><br /> L'aggiornamento del database al livello di compatibilità 110 non comporta la modifica dei dati utente archiviati su disco. È necessario correggere manualmente questi dati nel modo opportuno. Ad esempio, se è stato utilizzato `SELECT INTO` per creare una tabella da un'origine che contiene un'espressione di colonna calcolata descritta in precedenza, verrebbero archiviati i dati (con stile 0) anziché la definizione della colonna calcolata. Sarà necessario aggiornare manualmente questi dati in base allo stile 121.|  
|Tutte le colonne delle tabelle remote di tipo **smalldatetime** cui viene fatto riferimento in una vista partizionata vengono mappate come **datetime**. Colonne corrispondenti delle tabelle locali (nella stessa posizione ordinale nell'elenco di selezione) devono essere di tipo **datetime**.|Tutte le colonne delle tabelle remote di tipo **smalldatetime** cui viene fatto riferimento in una vista partizionata vengono mappate come **smalldatetime**. Colonne corrispondenti delle tabelle locali (nella stessa posizione ordinale nell'elenco di selezione) devono essere di tipo **smalldatetime**.<br /><br /> Dopo aver effettuato l'aggiornamento al livello di compatibilità 110, la vista partizionata distribuita avrà esito negativo poiché i tipi di dati non corrisponderanno. È possibile risolvere il problema, modificare il tipo di dati della tabella remota di **datetime** o l'impostazione di compatibilità minore o uguale a livello del database locale e 100.|  
|`SOUNDEX`funzione implementa le regole seguenti:<br /><br /> 1) maiuscole H o W maiuscola vengono ignorati quando si separa due consonanti aventi lo stesso numero nel `SOUNDEX` codice.<br /><br /> 2) se i primi 2 caratteri di *character_expression* hanno lo stesso numero `SOUNDEX` codice, sono inclusi sia i caratteri. Else, se un set di consonanti side-by-side presenti stesso numero di `SOUNDEX` codice, tutti gli elementi vengono escluse eccetto la prima.|`SOUNDEX`funzione implementa le regole seguenti:<br /><br /> 1) se H maiuscola o maiuscole W separa due consonanti aventi lo stesso numero `SOUNDEX` codice, la consonante a destra viene ignorato<br /><br /> 2) se un set di consonanti side-by-side presenti stesso numero di `SOUNDEX` codice, tutti gli elementi vengono escluse eccetto la prima.<br /><br /> <br /><br /> Le regole aggiuntive potrebbero generare i valori calcolati dal `SOUNDEX` funzione diverso da quelli calcolati con livelli di compatibilità precedenti. Dopo l'aggiornamento a livello di compatibilità 110, potrebbe essere necessario ricompilare gli indici, gli heap o vincoli CHECK che utilizzano il `SOUNDEX` (funzione). Per ulteriori informazioni, vedere [SOUNDEX &#40; Transact-SQL &#41;](../../t-sql/functions/soundex-transact-sql.md)|  
  
## <a name="differences-between-compatibility-level-90-and-level-100"></a>Differenze tra i livelli di compatibilità 90 e 100  
 In questa sezione vengono descritti i nuovi comportamenti introdotti con il livello di compatibilità 100.  
  
|Livello di compatibilità 90|Livello di compatibilità 100|Probabilità di impatto|  
|----------------------------------------|-----------------------------------------|---------------------------|  
|L'impostazione QUOTED_IDENTIFER è sempre impostata su ON per le funzioni con valori di tabella composte da più istruzioni quando tali funzioni vengono create indipendentemente dall'impostazione del livello di sessione.|L'impostazione della sessione QUOTED IDENTIFIER viene applicata quando vengono create funzioni con valori di tabella composte da più istruzioni.|Media|  
|Quando si crea o modifica una funzione di partizione, **datetime** e **smalldatetime** valori letterali nella funzione vengono valutati presupponendo che l'impostazione della lingua US_English.|L'impostazione della lingua corrente viene utilizzata per valutare **datetime** e **smalldatetime** valori letterali nella funzione di partizione.|Media|  
|Il `FOR BROWSE` clausola consentita (e ignorata) nelle `INSERT` e `SELECT INTO` istruzioni.|Il `FOR BROWSE` clausola non è consentita `INSERT` e `SELECT INTO` istruzioni.|Media|  
|I predicati full-text sono consentiti nel `OUTPUT` clausola.|I predicati full-text non sono consentiti nel `OUTPUT` clausola.|Basso|  
|`CREATE FULLTEXT STOPLIST`, `ALTER FULLTEXT STOPLIST`, e `DROP FULLTEXT STOPLIST` non sono supportati. Per impostazione predefinita, ai nuovi indici full-text viene associato automaticamente l'elenco di parole non significative di sistema.|`CREATE FULLTEXT STOPLIST`, `ALTER FULLTEXT STOPLIST`, e `DROP FULLTEXT STOPLIST` sono supportati.|Basso|  
|`MERGE`non viene applicata come parola chiave riservata.|MERGE è una parola chiave completamente riservata. Il `MERGE` istruzione è supportata con i livelli di compatibilità 90 e 100.|Basso|  
|Utilizzo di \<dml_table_source > dell'argomento dell'istruzione INSERT genera un errore di sintassi.|È possibile acquisire i risultati di una clausola OUTPUT in un'istruzione INSERT, UPDATE, DELETE o MERGE nidificata e inserire tali risultati in una vista o tabella di destinazione. Questa operazione viene eseguita utilizzando il \<dml_table_source > dell'argomento dell'istruzione INSERT.|Basso|
|A meno che non `NOINDEX` è specificato, `DBCC CHECKDB` o `DBCC CHECKTABLE` esegue controlli di consistenza logica e fisica in una singola tabella o vista indicizzata e in tutti i relativi indici non cluster sia gli indici XML. Gli indici spaziali non sono supportati.|A meno che non `NOINDEX` è specificato, `DBCC CHECKDB` o `DBCC CHECKTABLE` esegue i controlli di consistenza logica e fisica su una singola tabella e tutti i relativi indici non cluster. Per impostazione predefinita, tuttavia, negli indici XML, negli indici spaziali e nelle viste indicizzate vengono eseguiti solo controlli di consistenza fisica.<br /><br /> Se `WITH EXTENDED_LOGICAL_CHECKS` viene specificato, vengono eseguiti controlli logici su viste indicizzate, indici XML e indici spaziali, se presente. Per impostazione predefinita, i controlli di consistenza fisica vengono eseguiti prima di quelli di consistenza logica. Se `NOINDEX` viene anche specificato, vengono eseguiti solo i controlli logici.|Basso|  
|Quando una clausola OUTPUT viene utilizzata con un'istruzione DML (Data Manipulation Language) e si verifica un errore di run-time durante l'esecuzione di istruzioni, l'intera transazione viene terminata e ne viene eseguito il rollback.|Quando un `OUTPUT` clausola viene utilizzata con un'istruzione data manipulation language (DML) e si verifica un errore di run-time durante l'esecuzione dell'istruzione, il comportamento dipende il `SET XACT_ABORT` impostazione. Se `SET XACT_ABORT` è impostata su OFF, un errore di interruzione istruzione generato dall'istruzione DML usando il `OUTPUT` clausola terminerà l'istruzione, ma continua l'esecuzione del batch e non è eseguire il rollback della transazione. Se `SET XACT_ABORT` è impostata su ON, tutti gli errori di run-time generati dall'istruzione DML tramite la clausola OUTPUT termineranno il batch e viene eseguito il rollback della transazione.|Basso|  
|CUBE e ROLLUP non vengono applicate come parole chiave riservate.|`CUBE`e `ROLLUP` sono parole chiave riservate all'interno della clausola GROUP BY.|Basso|  
|La convalida di tipo Strict viene applicata agli elementi del codice XML **anyType** tipo.|La convalida LAX viene applicata agli elementi del **anyType** tipo. Per ulteriori informazioni, vedere [Componenti jolly e convalida del contenuto](../../relational-databases/xml/wildcard-components-and-content-validation.md).|Basso|  
|Gli attributi speciali **xsi: nil** e **xsi: Type** non è possibile eseguire una query o modificati da istruzioni data manipulation language.<br /><br /> Ciò significa che `/e/@xsi:nil` ha esito negativo `/e/@*` ignora il **xsi: nil** e **xsi: Type** attributi. Tuttavia, `/e` restituisce il **xsi: nil** e **xsi: Type** attributi per la coerenza con `SELECT xmlCol`, anche se `xsi:nil = "false"`.|Gli attributi speciali **xsi: nil** e **xsi: Type** vengono archiviati come attributi regolari e può essere eseguita una query e modificato.<br /><br /> Ad esempio, l'esecuzione della query `SELECT x.query('a/b/@*')` restituisce tutti gli attributi inclusi **xsi: nil** e **xsi: Type**. Per escludere questi tipi nella query, sostituire `@*` con `@*[namespace-uri(.) != "` *inserire l'uri dello spazio dei nomi xsi* `"` e non `(local-name(.) = "type"` o`local-name(.) ="nil".`|Basso|  
|Una funzione definita dall'utente che converte un valore stringa costante XML in un tipo datetime di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene contrassegnata come deterministica.|Una funzione definita dall'utente che converte un valore stringa costante XML in un tipo datetime di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene contrassegnata come non deterministica.|Basso|  
|I tipi unione ed elenco XML non sono supportati completamente.|I tipi unione ed elenco sono supportati completamente, incluse le funzionalità seguenti.<br /><br /> Unione di elenco<br /><br /> Unione di unione<br /><br /> Elenco di tipi atomici<br /><br /> Elenco di unione|Bassa|  
|Le opzioni SET necessarie per un metodo xQuery non vengono convalidate quando il metodo è contenuto in una vista o in una funzione inline con valori di tabella.|Le opzioni SET necessarie per un metodo xQuery vengono convalidate quando il metodo è contenuto in una vista o in una funzione inline con valori di tabella. Se le opzioni SET del metodo non sono impostate correttamente, viene generato un errore.|Basso|  
|I valori di attributo XML contenenti caratteri di fine riga (ritorno a capo e avanzamento riga) non vengono normalizzati in base allo standard XML, ovvero vengono restituiti entrambi i caratteri anziché un singolo carattere di avanzamento riga.|I valori di attributo XML contenenti caratteri di fine riga (ritorno a capo e avanzamento riga) vengono normalizzati in base allo standard XML, ovvero tutte le interruzioni di riga in entità analizzate esterne (inclusa l'entità del documento) vengono normalizzate in fase di input traducendo sia la sequenza di due caratteri #xD #xA sia qualsiasi carattere #xD non seguito da #XA in un singolo carattere #xA.<br /><br /> Le applicazioni che utilizzano attributi per trasportare valori stringa contenenti caratteri di fine riga non riceveranno di nuovo tali caratteri quando questi vengono inviati. Per evitare il processo di normalizzazione, utilizzare entità di caratteri numerici XML per codificare tutti i caratteri di fine riga.|Basso|  
|Le proprietà della colonna `ROWGUIDCOL` e `IDENTITY` possono essere erroneamente denominate come vincolo. L'istruzione `CREATE TABLE T (C1 int CONSTRAINT MyConstraint IDENTITY)`, ad esempio, viene eseguita correttamente, ma il nome del vincolo non viene mantenuto e non è accessibile per l'utente.|Le proprietà della colonna `ROWGUIDCOL` e `IDENTITY` non può essere rinominato come vincolo. In caso contrario, verrà restituito l'errore 156.|Basso|  
|L'aggiornamento delle colonne tramite un'assegnazione bidirezionale, ad esempio `UPDATE T1 SET @v = column_name = <expression>` può produrre risultati imprevisti perché il valore della variabile in tempo reale può essere utilizzato in altre clausole, ad esempio il `WHER`E e `ON` clausola durante l'esecuzione di istruzione anziché il valore iniziale dell'istruzione. Ciò può comportare una modifica imprevista dei significati dei predicati per ciascuna riga.<br /><br /> Questo comportamento è applicabile solo quando il livello di compatibilità è impostato su 90.|L'aggiornamento di colonne tramite un'assegnazione bidirezionale produce i risultati previsti, in quanto durante l'esecuzione dell'istruzione è possibile accedere solo al valore iniziale dell'istruzione per la colonna.|Basso|  
|Vedere l'esempio E nella sezione esempi riportata di seguito.|Vedere l'esempio F nella sezione esempi riportata di seguito.|Basso|  
|La funzione ODBC {fn CONVERT()} utilizza il formato di data predefinito della lingua specifica. Per alcuni linguaggi, il formato predefinito è AGM, che possono causare errori di conversione quando Convert () viene combinato con altre funzioni, ad esempio `{fn CURDATE()}`, che prevede un formato AMG.|La funzione ODBC `{fn CONVERT()}` utilizza stile 121 (un formato AMG indipendente dalla lingua) se la conversione in dati ODBC i tipi di SQL_TIMESTAMP, SQL_DATE, SQL_TIME, SQLDATE, SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP.|Basso|  
|Le funzioni intrinseche datetime, ad esempio DATEPART, non richiedono che i valori di input di tipo stringa siano valori letterali datetime validi. Ad esempio, `SELECT DATEPART (year, '2007/05-30')` viene compilato correttamente.|Le funzioni intrinseche DateTime, ad esempio `DATEPART` richiedono valori di input di stringa a valori letterali datetime validi. Quando si utilizza un valore letterale datetime non valido, viene restituito l'errore 241.|Basso|  
  
## <a name="reserved-keywords"></a>Parole chiave riservate  
 L'impostazione di compatibilità determina anche le parole chiave riservate dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Nella tabella seguente sono elencate le parole chiave riservate introdotte per ogni livello di compatibilità.  
  
|Livello di compatibilità|Parole chiave riservate|  
|----------------------------------|-----------------------|  
|130|Da determinare.|  
|120|Nessuno|  
|110|WITHIN GROUP, TRY_CONVERT, SEMANTICKEYPHRASETABLE, SEMANTICSIMILARITYDETAILSTABLE, SEMANTICSIMILARITYTABLE|  
|100|CUBE, MERGE, ROLLUP|  
|90|EXTERNAL, PIVOT, UNPIVOT, REVERT, TABLESAMPLE|  
  
 A un determinato livello di compatibilità, le parole chiave riservate includono tutte le parole chiave introdotte per tale livello e per quelli precedenti. Pertanto, ad esempio, per le applicazioni con livello 110 tutte le parole chiave elencate nella tabella precedente sono parole chiave riservate. Per i livelli di compatibilità inferiori, le parole chiave del livello 100 rimangono nomi di oggetti validi ma le funzionalità del linguaggio di livello 110 corrispondenti a tale parole chiave non sono disponibili.  
  
 Una volta introdotta, una parola chiave rimane riservata. La parola chiave riservata PIVOT, ad esempio, introdotta per il livello di compatibilità 90, è riservata per i livelli 100, 110 e 120.  
  
 Se per un'applicazione si utilizza un identificatore che rappresenta una parola chiave riservata nel livello di compatibilità relativo, viene generato un errore. Per risolvere il problema, racchiudere l'identificatore tra una parentesi (**[]**) o virgolette (**""**), ad esempio, per aggiornare un'applicazione che utilizza l'identificatore **esterno** a livello di compatibilità 90, è possibile modificare l'identificatore per uno **[EXTERNAL]** o **"EXTERNAL"**.  
  
 Per altre informazioni, vedere [Parole chiave riservate &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-compatibility-level"></a>A. Modifica del livello di compatibilità  
 L'esempio seguente modifica il livello di compatibilità del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] a `110,` [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].   
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 110;  
GO  
```  
  
 L'esempio seguente restituisce il livello di compatibilità del database corrente.  
  
```sql  
SELECT name, compatibility_level   
FROM sys.databases   
WHERE name = db_name();  
```  
  
### <a name="b-ignoring--the-set-language-statement-except-under-compatibility-level-120"></a>B. Ignorando l'istruzione SET LANGUAGE tranne con il livello di compatibilità 120  
 La query seguente ignora l'istruzione SET LANGUAGE tranne nel caso di livello di compatibilità 120.  
  
```sql  
SET DATEFORMAT dmy;   
DECLARE @t2 date = '12/5/2011' ;  
SET LANGUAGE dutch;   
SELECT CONVERT(varchar(11), @t2, 106);   
  
-- Results when the compatibility level is less than 120.   
12 May 2011   
  
-- Results when the compatibility level is set to 120).  
12 mei 2011  
```  
  
### <a name="c"></a>C.  
 Per impostazione a livello di compatibilità 110 o inferiore, i riferimenti ricorsivi sul lato destro di una clausola EXCEPT creano un ciclo infinito.  
  
```sql  
WITH   
cte AS (SELECT * FROM (VALUES (1),(2),(3)) v (a)),  
r   
AS (SELECT a FROM Table1  
UNION ALL  
(SELECT a FROM Table1 EXCEPT SELECT a FROM r) )   
SELECT a   
FROM r;  
  
```  
  
### <a name="d"></a>D.  
 Questo esempio mostra la differenza tra gli stili 0 e 121. Per ulteriori informazioni sugli stili di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
```sql  
CREATE TABLE t1 (c1 time(7), c2 datetime2);   
  
INSERT t1 (c1,c2) VALUES (GETDATE(), GETDATE());  
  
SELECT CONVERT(nvarchar(16),c1,0) AS TimeStyle0  
       ,CONVERT(nvarchar(16),c1,121)AS TimeStyle121  
       ,CONVERT(nvarchar(32),c2,0) AS Datetime2Style0  
       ,CONVERT(nvarchar(32),c2,121)AS Datetime2Style121  
FROM t1;  
  
-- Returns values such as the following.  
TimeStyle0       TimeStyle121       
Datetime2Style0      Datetime2Style121  
---------------- ----------------   
-------------------- --------------------------  
3:15PM           15:15:35.8100000   
Jun  7 2011  3:15PM  2011-06-07 15:15:35.8130000  
```  
  
### <a name="e"></a>E.  
 L'assegnazione di variabile è consentita in un'istruzione contenente un operatore UNION di livello principale, ma restituisce risultati imprevisti. Nelle istruzioni seguenti, ad esempio, alla variabile locale `@v` è assegnato il valore della colonna `BusinessEntityID` dall'unione di due tabelle. Per definizione, quando l'istruzione SELECT restituisce più valori, alla variabile viene assegnato l'ultimo valore restituito. In questo caso, alla variabile viene assegnato correttamente l'ultimo valore, ma viene restituito anche il set di risultati dell'istruzione SELECT UNION.  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET compatibility_level = 90;  
GO  
USE AdventureWorks2012;  
GO  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM HumanResources.Employee  
UNION ALL  
SELECT @v = BusinessEntityID FROM HumanResources.EmployeeAddress;  
SELECT @v;  
```  
  
### <a name="f"></a>F.  
 L'assegnazione di variabile non è consentita in un'istruzione contenente un operatore UNION di livello principale. In caso contrario, verrà restituito l'errore 10734. Per risolvere questo errore, riscrivere la query come illustrato nell'esempio seguente.  
  
```sql  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM   
    (SELECT BusinessEntityID FROM HumanResources.Employee  
     UNION ALL  
     SELECT BusinessEntityID FROM HumanResources.EmployeeAddress) AS Test;  
SELECT @v;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Parole chiave riservate &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
 [Visualizzare o modificare il livello di compatibilità di un database](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) 
  
