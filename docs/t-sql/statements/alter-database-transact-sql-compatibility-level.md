---
title: "MODIFICARE il livello di compatibilità DATABASE (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
ms.assetid: ca5fd220-d5ea-4182-8950-55d4101a86f6
caps.latest.revision: 89
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7b65511b09f2a94d30c39c1f97ed88cfbfab855b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-compatibility-level"></a>Livello di compatibilità di ALTER DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  
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
  
|Product|Versione del motore di database|Designazione di livello di compatibilità|Valori del livello di compatibilità supportato|  
|-------------|-----------------------------|-------------------------------------|------------------------------------------|  
|[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|14|140|140, 130, 120, 110, 100|
|[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|12|130|140, 130, 120, 110, 100|  
|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|13|130|130, 120, 110, 100|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|12|120|120, 110, 100|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|11|110|110, 100, 90|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|10.5|100|100, 90, 80|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|10|100|100, 90, 80|  
|SQL Server 2005|9|90|90, 80|  
|SQL Server 2000|8|80|80|  
  
> [!NOTE]  
>  **Database SQL di Azure** V12 è stato rilasciato nel dicembre 2014. Un aspetto di tale versione è che i database appena creati sono il livello di compatibilità impostato su 120. Nel 2015 SQL Database ha iniziato il supporto per il livello 130, anche se il valore predefinito è rimasta 120.  
> 
> A partire da **mid-giugno 2016**, nel Database di SQL Azure, il livello di compatibilità predefinito sono 130 anziché 120 per **appena creato** database. I database esistenti creati prima di medie-giugno 2016 non sono interessati e mantengono il livello di compatibilità corrente (100, 110 e 120). 
> 
> Se si desidera livello 130 per il database, in genere, ma è necessario preferire livello 110 **la stima della cardinalità** algoritmo, vedere [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md), in particolare la parola chiave LEGACY_CARDINALITY_ESTIMATION = ON.  
>  
>  Per informazioni dettagliate su come valutare le variazioni delle prestazioni delle query più importanti, tra i due livelli di compatibilità nel Database di SQL Azure, vedere [migliorate le prestazioni delle Query con 130 livello di compatibilità in Database SQL di Azure](http://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).


 Eseguire la query seguente per determinare la versione di [!INCLUDE[ssDE](../../includes/ssde-md.md)] che si è connessi.  
  
```tsql  
SELECT SERVERPROPERTY('ProductVersion');  
```  
  
> [!NOTE]  
>  Non tutte le funzionalità che variano in base al livello di compatibilità sono supportate in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  

 Per determinare il livello di compatibilità corrente, eseguire una query di **compatibility_level** colonna di [Sys. Databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
```tsql  
SELECT name, compatibility_level FROM sys.databases;  
```  
  
## <a name="remarks"></a>Osservazioni  
 Per tutte le installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il livello di compatibilità predefinito è impostato per la versione di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. I database sono impostati per questo livello, a meno che il **modello** database con un livello di compatibilità inferiore. Quando un database viene aggiornato da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il database mantiene il livello di compatibilità esistente se è almeno minimo consentito per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'aggiornamento di un database con un livello di compatibilità inferiore a quello consentito, imposta il database per la compatibilità più bassa livello è consentita. Questo comportamento si applica sia ai database di sistema che ai database utente. Utilizzare **ALTER DATABASE** per modificare il livello di compatibilità del database. Per visualizzare il livello di compatibilità corrente di un database, eseguire una query di **compatibility_level** colonna il **Sys. Databases** vista del catalogo.  

  
## <a name="using-compatibility-level-for-backward-compatibility"></a>Utilizzo del livello di compatibilità per garantire la compatibilità con le versioni precedenti  
 Il livello di compatibilità influisce solo sul comportamento del database specificato e non dell'intero server. Il livello di compatibilità garantisce solo una compatibilità parziale con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A partire dalla modalità di compatibilità 130, le nuove funzionalità che influiscono sulla piano di query sono stati aggiunti solo la nuova modalità di compatibilità. Questa operazione è stata eseguita per ridurre al minimo il rischio durante gli aggiornamenti che sono causati da un calo delle prestazioni a causa di modifiche del piano di query. Dal punto di vista dell'applicazione, l'obiettivo è ancora essere a livello di compatibilità più recente per ereditare alcune delle nuove funzionalità, nonché i miglioramenti delle prestazioni eseguiti nello spazio Query optimizer, ma a tale scopo, in modo controllato. Utilizzare il livello di compatibilità come strumento di migrazione provvisoria per risolvere i problemi correlati alle differenze tra le versioni delle funzioni controllate dall'impostazione del livello di compatibilità pertinente. Per ulteriori informazioni, vedere le procedure consigliate aggiornamento avanti in questo articolo.  
  
 Se esistenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le applicazioni sono interessate da differenze funzionali introdotte nella versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], convertire l'applicazione per integrarsi perfettamente con la nuova modalità di compatibilità. Utilizzare quindi **ALTER DATABASE** per modificare il livello di compatibilità impostandolo su 130. La nuova impostazione di compatibilità per un database diventa effettivo quando un **USE Database** viene eseguita o viene elaborato un nuovo account di accesso con il database come database predefinito.  
  
## <a name="best-practices"></a>Procedure consigliate  
 Se si modifica il livello di compatibilità mentre gli utenti sono connessi al database, è possibile che vengano restituiti set di risultati non corretti per le query attive. Se ad esempio si modifica il livello di compatibilità durante la compilazione di un piano di query, è possibile che il piano compilato sia basato sui livelli di compatibilità sia vecchi che nuovi, con conseguente restituzione di un piano non corretto e di risultati potenzialmente non accurati. Il problema potrebbe essere inoltre aggravato dal fatto che il piano venga inserito nella cache dei piani e riutilizzato per query successive. Per evitare risultati di query non accurati, è consigliabile utilizzare la procedura seguente per modificare il livello di compatibilità di un database:  
  
1.  Impostare il database in modalità di accesso utente singolo utilizzando ALTER DATABASE SET SINGLE_USER.  
  
2.  Modificare il livello di compatibilità del database.  
  
3.  Impostare il database in modalità di accesso multiutente utilizzando ALTER DATABASE SET MULTI_USER.  
  
4.  Per ulteriori informazioni sull'impostazione della modalità di accesso di un database, vedere [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="compatibility-levels-and-stored-procedures"></a>Livelli di compatibilità e stored procedure  
 Quando si esegue una stored procedure, viene utilizzato il livello di compatibilità corrente del database in cui la procedura è definita. Se si modifica l'impostazione di compatibilità di un database, tutte le relative stored procedure vengono ricompilate automaticamente per riflettere tale modifica.  

## <a name="differences-between-compatibility-level-130-and-level-140"></a>Differenze tra il livello di compatibilità 130 e 140 livello  
In questa sezione vengono descritti i nuovi comportamenti introdotti con livello di compatibilità 140.

|Impostazione a livello di compatibilità 130 minore o uguale|Impostazione a livello di compatibilità di 140|  
|--------------------------------------------------|-----------------------------------------|  
|Stime della cardinalità per le istruzioni che fanno riferimento a istruzioni multiple con valori di tabella le funzioni utilizzano un'ipotesi di riga fissa.|Stime della cardinalità per le istruzioni idonee che fanno riferimento a istruzioni multiple con valori di tabella funzioni utilizzerà la cardinalità effettiva dell'output della funzione.  Questa opzione è abilitata tramite **esecuzione interleaved** per le funzioni a istruzioni multiple con valori di tabella.|
|Le query in modalità batch che richiedono memoria sufficiente concedono dimensioni che comporterà spill su disco potrebbe continuare la presenza di problemi in esecuzioni consecutive.|Query in modalità batch che richiedono le dimensioni di concessione di memoria insufficiente che comporterà spill su disco potrebbe avere prestazioni migliorate in esecuzioni consecutive.  Questa opzione è abilitata tramite **commenti e suggerimenti di concessioni di memoria in modalità batch** che aggiornerà le dimensioni della concessione di memoria di un piano memorizzato nella cache se spill si sono verificati per gli operatori in modalità batch. |
|Le query in modalità batch che richiedono una quantità di memoria eccessiva dimensioni che comporta problemi di concorrenza può continuare ad avere problemi in esecuzioni consecutive della concessione.|Le query in modalità batch che richiedono una quantità di memoria eccessiva concedono potrebbero concorrenza in esecuzioni consecutive hanno migliorato le dimensioni che comporta problemi di concorrenza.  Questa opzione è abilitata tramite **commenti e suggerimenti di concessioni di memoria in modalità batch** che verranno aggiornate le dimensioni della concessione di memoria di un piano memorizzato nella cache, se originariamente è stata richiesta una quantità eccessiva.|
|Le query in modalità batch contenenti gli operatori di join sono idonee per tre algoritmi di join fisico, tra cui ciclo nidificato, hash join e join di tipo merge.  Se le stime della cardinalità non sono corrette per gli input di join, è possibile selezionare un algoritmo di join appropriato.  In questo caso, le prestazioni ne risentiranno e l'algoritmo di join appropriato rimarrà in uso fino a quando non viene ricompilato il piano memorizzato nella cache.|È un operatore di join aggiuntiva denominato **join adattivo**. Se le stime della cardinalità non sono corrette per l'input di compilazione outer join, è possibile selezionare un algoritmo di join appropriato.  Se l'istruzione è idoneo per un join adattivo in questo caso, verrà utilizzato un ciclo annidato per gli input di join più piccoli e un hash join verrà utilizzato per gli input di join più grandi in modo dinamico senza richiedere la ricompilazione. |
|Piani semplici riferimento gli indici Columnstore non sono idonei per l'esecuzione in modalità batch. |Un semplice piano gli indici Columnstore di riferimento verrà eliminato a favore di un piano idoneo per l'esecuzione in modalità batch.|
|L'operatore UDX sp_execute_external_script può essere eseguito solo in modalità riga.|L'operatore UDX sp_execute_external_script è idoneo per l'esecuzione in modalità batch.|  
|Più istruzioni TVF non dispone di esecuzione interleave |Esecuzione interleave per TVF con più istruzioni migliorare la qualità del piano. |

Correzioni che sono stati con il flag di traccia 4199 nelle versioni precedenti di SQL Server precedenti a SQL Server 2017 sono ora abilitate per impostazione predefinita. Con la modalità di compatibilità 140. Flag di traccia 4199 continuerà a essere applicabile per nuove correzioni di query optimizer che vengono rilasciate dopo SQL Server 2017. Per informazioni sui Flag di traccia 4199, vedere [Flag di traccia 4199](https://support.microsoft.com/en-us/kb/974006).  
  
## <a name="differences-between-compatibility-level-120-and-level-130"></a>Differenze tra il livello di compatibilità 120 e 130 livello  
In questa sezione vengono descritti i nuovi comportamenti introdotti con livello di compatibilità 130.   

  
|Impostazione a livello di compatibilità 120 minore o uguale|Impostazione a livello di compatibilità di 130|  
|--------------------------------------------------|-----------------------------------------|  
|L'inserimento in un'istruzione Insert select è a thread singolo.|L'inserimento in un'istruzione Insert select su multi-thread o disporre di un piano parallelo.|  
|Le query in una tabella con ottimizzazione per la memoria vengono eseguite a thread singolo.|Le query in una tabella con ottimizzazione per la memoria è ora possono avere piani paralleli.|  
|Strumento di stima della cardinalità di SQL 2014 introdotto **CardinalityEstimationModelVersion = "120"**|Cardinalità ulteriore piano miglioramenti di stima (CE) con la 130 modello di stima della cardinalità visibile da una Query. **CardinalityEstimationModelVersion = "130"**|  
|Modalità batch e cambia la modalità di riga con gli indici Columnstore<br /><br /> Ordina in una tabella con indice Columnstore è in modalità riga<br /><br /> Aggregazioni funzione finestra operano in modalità a riga, ad esempio ritardo o responsabile<br /><br /> Query sulle tabelle Columnstore con più clausole distinte usati in modalità riga<br /><br /> Query in esecuzione in MAXDOP 1 o con un piano seriale eseguito in modalità riga | Modalità batch e cambia la modalità di riga con gli indici Columnstore<br /><br /> Ordina in una tabella con un indice Columnstore è ora in modalità batch<br /><br /> Aggregazioni finestra ora operano in modalità batch, ad esempio ritardo o LEAD<br /><br /> Query su tabelle Columnstore con più clausole distinte operano in modalità Batch<br /><br /> Le query in esecuzione in Maxdop1 o con un piano seriale eseguito in modalità Batch|  
| Le statistiche possono essere aggiornate automaticamente. | La logica che aggiorna automaticamente le statistiche è più aggressiva in tabelle di grandi dimensioni.  In pratica, questo dovrebbe ridurre i casi in cui i clienti hanno registrato i problemi di prestazioni per le query in cui le righe appena inserite vengono eseguita una query di frequente, ma in cui le statistiche non sia state aggiornate per includere tali valori. |  
| Traccia 2371 è impostata su OFF per impostazione predefinita in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. | [Traccia 2371](https://blogs.msdn.microsoft.com/psssql/2016/10/04/default-auto-statistics-update-threshold-change-for-sql-server-2016/) è impostata su ON per impostazione predefinita in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Flag di traccia 2371 indica l'aggiornamento statistiche automatico per un subset più piccolo ancora convocazione di righe, in una tabella con un elevato numero di righe di esempio. <br/> <br/> Un miglioramento consiste nell'includere nell'esempio di più righe che sono state inserite di recente. <br/> <br/> Un altro miglioramento è per consentire le query di esecuzione durante il processo di aggiornamento delle statistiche è in esecuzione, anziché bloccare la query. |  
| Per il livello 120, le statistiche vengono campionate da un *singolo*-thread di processo. | Per il livello 130, le statistiche vengono campionate da un *più*-thread di processo. |  
| 253 chiavi esterne in ingresso è il limite. | Una tabella può fare riferimento fino a 10.000 chiavi esterne in ingresso o riferimenti simile. Per informazioni sulle restrizioni, vedere [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md). |  
|Gli algoritmi di hash MD2, MD4, MD5, SHA e SHA1 deprecati sono consentiti.|Sono consentiti solo gli algoritmi di hash SHA2_256 e SHA2_512.|  
  
  
Flag di correzioni che sono stati nella finestra di traccia 4199 nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] sono ora abilitati per impostazione predefinita. Con la modalità di compatibilità 130. Flag di traccia 4199 sarà comunque applicabile per nuove correzioni di query optimizer che vengono rilasciate dopo [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Per utilizzare query optimizer precedente in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è necessario selezionare il livello di compatibilità 110. Per informazioni sui Flag di traccia 4199, vedere [Flag di traccia 4199](https://support.microsoft.com/en-us/kb/974006).  
  
## <a name="differences-between-lower-compatibility-levels-and-level-120"></a>Differenze tra i livelli di compatibilità inferiori e il livello 120  
 Questa sezione descrive i nuovi comportamenti introdotti con il livello di compatibilità 120.  
  
|Livello di compatibilità 110 o inferiore|Livello di compatibilità 120|  
|--------------------------------------------------|-----------------------------------------|  
|Viene utilizzata la versione precedente di Query Optimizer.|In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] sono stati apportati miglioramenti sostanziali al componente per la creazione e l'ottimizzazione dei piani di query. Questa nuova funzionalità di Query Optimizer dipende dall'utilizzo del livello di compatibilità del database 120. Per sfruttare al meglio questi miglioramenti, sarebbe opportuno sviluppare le nuove applicazioni di database utilizzando il livello di compatibilità del database 120. Le applicazioni di cui si esegue la migrazione da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere testate con attenzione per assicurarsi che le prestazioni vengano mantenute o migliorate. Se si verifica un calo delle prestazioni, è possibile impostare il livello di compatibilità del database su 110 o su un valore inferiore per utilizzare la metodologia precedente di Query Optimizer.<br /><br /> Il livello di compatibilità 120 del database utilizza un nuovo strumento di stima della cardinalità ottimizzato per i carichi di lavoro OLTP e di data warehouse più recenti. Prima di impostare il livello di compatibilità del database su 110 a causa di problemi di prestazioni, vedere le indicazioni contenute nella sezione piani di Query del [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [novità nel motore di Database](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md) argomento.|  
|Livelli di compatibilità inferiori a 120, l'impostazione della lingua viene ignorata durante la conversione di un **data** valore in un valore stringa. Si noti che questo comportamento è specifico solo per il **data** tipo. Vedere l'esempio B nella sezione esempi riportata di seguito.|L'impostazione della lingua non viene ignorato durante la conversione di un **data** valore in un valore stringa.|  
|I riferimenti ricorsivi sul lato destro di una clausola EXCEPT creano un ciclo infinito. Esempio C, nella sezione esempi riportata di seguito viene illustrato questo comportamento.|I riferimenti ricorsivi in una clausola EXCEPT generano un errore in conformità allo standard ANSI SQL.|  
|Una CTE ricorsiva consente i nomi di colonna duplicati.|Una CTE ricorsiva non consente i nomi di colonna duplicati.|  
|I trigger disabilitati vengono abilitati se i trigger vengono modificati.|La modifica di un trigger non cambia lo stato (abilitato o disabilitato) del trigger.|  
|La clausola della tabella OUTPUT INTO ignora IDENTITY_INSERT SETTING = OFF e consente l'inserimento di valori espliciti.|Non è possibile inserire valori espliciti per un colonna Identity in una tabella se IDENTITY_INSERT è impostato su OFF.|  
|Quando il contenimento del database è impostato su parziale, la convalida del campo $action nella clausola OUTPUT di un'istruzione MERGE può restituire un errore di regole di confronto.|Le regole di confronto dei valori restituiti dalla clausola $action di un'istruzione MERGE sono le regole di confronto del database anziché le regole di confronto del server e non viene restituito alcun errore di conflitto tra regole di confronto.|  
|Oggetto **SELECT INTO** sempre istruzione crea un'operazione di inserimento a thread singolo.|Oggetto **SELECT INTO** istruzione è possibile creare un'operazione di inserimento parallela. Quando si inserisce un numero elevato di righe, con un'operazione parallela è possibile migliorare le prestazioni.|  
  
## <a name="differences-between-lower-compatibility-levels-and-levels-110-and-120"></a>Differenze tra i livelli di compatibilità inferiori e i livelli 110 e 120  
 Questa sezione descrive i nuovi comportamenti introdotti con il livello di compatibilità 110.   Questa sezione si applica al livello 120.  
  
|Livello di compatibilità 100 o inferiore|Impostazione del livello di compatibilità 110 o inferiore|  
|--------------------------------------------------|--------------------------------------------------|  
|Gli oggetti di database CLR (Common Language Runtime) vengono eseguiti con la versione 4 di CLR. Non sono tuttavia presenti alcune modifiche del comportamento introdotte con la versione 4 di CLR. Per ulteriori informazioni, vedere [novità di integrazione con CLR](../../relational-databases/clr-integration/clr-integration-what-s-new.md).|Gli oggetti di database CLR vengono eseguiti con la versione 4 di CLR.|  
|Le funzioni XQuery **lunghezza della stringa** e **sottostringa** considerano ciascun surrogato come due caratteri.|Le funzioni XQuery **lunghezza della stringa** e **sottostringa** considerano ciascun surrogato come un carattere.|  
|L'operatore PIVOT è consentito in una query ricorsiva dell'espressione di tabella comune. La query tuttavia restituisce risultati non corretti quando sono presenti più righe per raggruppamento.|L'operatore PIVOT non è consentito in una query ricorsiva dell'espressione di tabella comune. Viene restituito un errore.|  
|L'algoritmo RC4 è supportato solo per motivi di compatibilità con le versioni precedenti. È possibile crittografare il nuovo materiale usando RC4 o RC4_128 solo quando il livello di compatibilità del database è 90 o 100. (Non consigliato.) In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.|Il nuovo materiale non può essere crittografato utilizzando RC4 o RC4_128. Usare un algoritmo più recente, ad esempio uno degli algoritmi AES. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.|  
|Lo stile predefinito per le operazioni CAST e CONVERT su **ora** e **datetime2** tipi di dati è 121, tranne quando uno dei due tipi viene utilizzato in un'espressione di colonna calcolata. Per le colonne calcolate, lo stile predefinito è 0. Questo comportamento influisce sulle colonne calcolate quando vengono create o usate nelle query con parametrizzazione automatica o nelle definizioni dei vincoli.<br /><br /> Nell'esempio D nella sezione esempi riportata di seguito viene illustrata la differenza tra gli stili 0 e 121. Non viene illustrato il comportamento descritto sopra. Per ulteriori informazioni sugli stili di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).|In compatibilità livello 110, lo stile predefinito per le operazioni CAST e CONVERT su **ora** e **datetime2** tipi di dati è sempre 121. Se la query si basa sul comportamento obsoleto, usare un livello di compatibilità inferiore a 110 oppure specificare in modo esplicito lo stile 0 nella query interessata.<br /><br /> L'aggiornamento del database al livello di compatibilità 110 non comporta la modifica dei dati utente archiviati su disco. È necessario correggere manualmente questi dati nel modo opportuno. Se ad esempio si usa SELECT INTO per creare una tabella da un'origine che contiene un'espressione di colonna calcolata descritta in precedenza, vengono archiviati i dati (con stile 0), non la definizione della colonna calcolata. Sarà necessario aggiornare manualmente questi dati in base allo stile 121.|  
|Tutte le colonne delle tabelle remote di tipo **smalldatetime** cui viene fatto riferimento in una vista partizionata vengono mappate come **datetime**. Colonne corrispondenti delle tabelle locali (nella stessa posizione ordinale nell'elenco di selezione) devono essere di tipo **datetime**.|Tutte le colonne delle tabelle remote di tipo **smalldatetime** cui viene fatto riferimento in una vista partizionata vengono mappate come **smalldatetime**. Colonne corrispondenti delle tabelle locali (nella stessa posizione ordinale nell'elenco di selezione) devono essere di tipo **smalldatetime**.<br /><br /> Dopo aver effettuato l'aggiornamento al livello di compatibilità 110, la vista partizionata distribuita avrà esito negativo poiché i tipi di dati non corrisponderanno. È possibile risolvere il problema, modificare il tipo di dati della tabella remota di **datetime** o l'impostazione di compatibilità minore o uguale a livello del database locale e 100.|  
|Tramite la funzione SOUNDEX vengono implementate le regole seguenti:<br /><br /> 1) maiuscole H o W maiuscola vengono ignorate se separa due consonanti aventi lo stesso numero nel codice SOUNDEX.<br /><br /> 2) se i primi 2 caratteri di *character_expression* hanno lo stesso numero nel codice SOUNDEX, entrambi i caratteri sono inclusi. Altrimenti, se il numero di un set di consonanti affiancate è uguale nel codice SOUNDEX, vengono escluse tutte le consonanti eccetto la prima.|Tramite la funzione SOUNDEX vengono implementate le regole seguenti:<br /><br /> 1) se maiuscole H o W maiuscola separare due consonanti aventi lo stesso numero nel codice SOUNDEX, la consonante a destra viene ignorata<br /><br /> 2) se un set di consonanti side-by-side con un numero è uguale nel codice SOUNDEX, tutti gli elementi vengono escluse eccetto la prima.<br /><br /> <br /><br /> Le regole aggiuntive potrebbero generare una differenza tra i valori calcolati dalla funzione SOUNDEX e quelli calcolati con livelli di compatibilità precedenti. Dopo aver effettuato l'aggiornamento al livello di compatibilità 110, potrebbe essere necessario ricompilare gli indici, gli heap o i vincoli CHECK in cui viene usata la funzione SOUNDEX. Per ulteriori informazioni, vedere [SOUNDEX &#40; Transact-SQL &#41;](../../t-sql/functions/soundex-transact-sql.md)|  
  
## <a name="differences-between-compatibility-level-90-and-level-100"></a>Differenze tra i livelli di compatibilità 90 e 100  
 In questa sezione vengono descritti i nuovi comportamenti introdotti con il livello di compatibilità 100.  
  
|Livello di compatibilità 90|Livello di compatibilità 100|Probabilità di impatto|  
|----------------------------------------|-----------------------------------------|---------------------------|  
|L'impostazione QUOTED_IDENTIFER è sempre impostata su ON per le funzioni con valori di tabella composte da più istruzioni quando tali funzioni vengono create indipendentemente dall'impostazione del livello di sessione.|L'impostazione della sessione QUOTED IDENTIFIER viene applicata quando vengono create funzioni con valori di tabella composte da più istruzioni.|Media|  
|Quando si crea o modifica una funzione di partizione, **datetime** e **smalldatetime** valori letterali nella funzione vengono valutati presupponendo che l'impostazione della lingua US_English.|L'impostazione della lingua corrente viene utilizzata per valutare **datetime** e **smalldatetime** valori letterali nella funzione di partizione.|Media|  
|La clausola FOR BROWSE è consentita (e ignorata) nelle istruzioni INSERT e SELECT INTO.|La clausola FOR BROWSE non è consentita nelle istruzioni INSERT e SELECT INTO.|Media|  
|Nella clausola OUTPUT sono consentiti predicati full-text.|I predicati full-text non sono consentiti nella clausola OUTPUT.|Basso|  
|Le funzioni CREATE FULLTEXT STOPLIST, ALTER FULLTEXT STOPLIST e DROP FULLTEXT STOPLIST non sono supportate. Per impostazione predefinita, ai nuovi indici full-text viene associato automaticamente l'elenco di parole non significative di sistema.|Le funzioni CREATE FULLTEXT STOPLIST, ALTER FULLTEXT STOPLIST e DROP FULLTEXT STOPLIST sono supportate.|Basso|  
|MERGE non viene applicata come parola chiave riservata.|MERGE è una parola chiave completamente riservata. L'istruzione MERGE è supportata con i livelli di compatibilità 100 e 90.|Basso|  
|Utilizzo di \<dml_table_source > dell'argomento dell'istruzione INSERT genera un errore di sintassi.|È possibile acquisire i risultati di una clausola OUTPUT in un'istruzione INSERT, UPDATE, DELETE o MERGE nidificata e inserire tali risultati in una vista o tabella di destinazione. Questa operazione viene eseguita utilizzando il \<dml_table_source > dell'argomento dell'istruzione INSERT.|Basso|
|A meno che non sia specificato NOINDEX, DBCC CHECKDB o DBCC CHECKTABLE esegue controlli di consistenza sia fisica che logica in una singola tabella o vista indicizzata e in tutti i relativi indici non cluster e XML. Gli indici spaziali non sono supportati.|A meno che non sia specificato NOINDEX, DBCC CHECKDB o DBCC CHECKTABLE esegue controlli di consistenza sia fisica che logica in una singola tabella e in tutti i relativi indici non cluster. Per impostazione predefinita, tuttavia, negli indici XML, negli indici spaziali e nelle viste indicizzate vengono eseguiti solo controlli di consistenza fisica.<br /><br /> Se è specificato WITH EXTENDED_LOGICAL_CHECKS, vengono eseguiti controlli logici su viste indicizzate, indici XML e indici spaziali, laddove presenti. Per impostazione predefinita, i controlli di consistenza fisica vengono eseguiti prima di quelli di consistenza logica. Se viene specificato anche NOINDEX, vengono eseguiti solo i controlli logici.|Basso|  
|Quando una clausola OUTPUT viene utilizzata con un'istruzione DML (Data Manipulation Language) e si verifica un errore di run-time durante l'esecuzione di istruzioni, l'intera transazione viene terminata e ne viene eseguito il rollback.|Quando una clausola OUTPUT viene utilizzata con un'istruzione DML (Data Manipulation Language) e si verifica un errore di run-time durante l'esecuzione di istruzioni, il comportamento dipende dall'impostazione di SET XACT_ABORT. Se SET XACT_ABORT è OFF, un errore di interruzione dell'istruzione generato dall'istruzione DML tramite la clausola OUTPUT terminerà l'istruzione, ma l'esecuzione del batch continuerà e non verrà eseguito il rollback della transazione. Se SET XACT_ABORT è ON, tutti gli errori di run-time generati dall'istruzione DML tramite la clausola OUTPUT termineranno il batch e verrà eseguito il rollback della transazione.|Basso|  
|CUBE e ROLLUP non vengono applicate come parole chiave riservate.|CUBE e ROLLUP sono parole chiave riservate all'interno della clausola GROUP BY.|Basso|  
|Convalida di tipo Strict viene applicata agli elementi del codice XML **anyType** tipo.|La convalida LAX viene applicata agli elementi del **anyType** tipo. Per ulteriori informazioni, vedere [componenti jolly e convalida del contenuto](../../relational-databases/xml/wildcard-components-and-content-validation.md).|Basso|  
|Gli attributi speciali **xsi: nil** e **xsi: Type** non è possibile eseguire una query o modificati da istruzioni data manipulation language.<br /><br /> Ciò significa che `/e/@xsi:nil` ha esito negativo `/e/@*` ignora il **xsi: nil** e **xsi: Type** attributi. Tuttavia, `/e` restituisce il **xsi: nil** e **xsi: Type** attributi per la coerenza con `SELECT xmlCol`, anche se `xsi:nil = "false"`.|Gli attributi speciali **xsi: nil** e **xsi: Type** vengono archiviati come attributi regolari e può essere eseguita una query e modificato.<br /><br /> Ad esempio, l'esecuzione della query `SELECT x.query('a/b/@*')` restituisce tutti gli attributi inclusi **xsi: nil** e **xsi: Type**. Per escludere questi tipi nella query, sostituire `@*` con `@*[namespace-uri(.) != "` *inserire l'uri dello spazio dei nomi xsi* `"` e non `(local-name(.) = "type"` o`local-name(.) ="nil".`|Basso|  
|Una funzione definita dall'utente che converte un valore stringa costante XML in un tipo datetime di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene contrassegnata come deterministica.|Una funzione definita dall'utente che converte un valore stringa costante XML in un tipo datetime di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene contrassegnata come non deterministica.|Basso|  
|I tipi unione ed elenco XML non sono supportati completamente.|I tipi unione ed elenco sono supportati completamente, incluse le funzionalità seguenti.<br /><br /> Unione di elenco<br /><br /> Unione di unione<br /><br /> Elenco di tipi atomici<br /><br /> Elenco di unione|Bassa|  
|Le opzioni SET necessarie per un metodo xQuery non vengono convalidate quando il metodo è contenuto in una vista o in una funzione inline con valori di tabella.|Le opzioni SET necessarie per un metodo xQuery vengono convalidate quando il metodo è contenuto in una vista o in una funzione inline con valori di tabella. Se le opzioni SET del metodo non sono impostate correttamente, viene generato un errore.|Basso|  
|I valori di attributo XML contenenti caratteri di fine riga (ritorno a capo e avanzamento riga) non vengono normalizzati in base allo standard XML, ovvero vengono restituiti entrambi i caratteri anziché un singolo carattere di avanzamento riga.|I valori di attributo XML contenenti caratteri di fine riga (ritorno a capo e avanzamento riga) vengono normalizzati in base allo standard XML, ovvero tutte le interruzioni di riga in entità analizzate esterne (inclusa l'entità del documento) vengono normalizzate in fase di input traducendo sia la sequenza di due caratteri #xD #xA sia qualsiasi carattere #xD non seguito da #XA in un singolo carattere #xA.<br /><br /> Le applicazioni che utilizzano attributi per trasportare valori stringa contenenti caratteri di fine riga non riceveranno di nuovo tali caratteri quando questi vengono inviati. Per evitare il processo di normalizzazione, utilizzare entità di caratteri numerici XML per codificare tutti i caratteri di fine riga.|Basso|  
|Le proprietà di colonna ROWGUIDCOL e IDENTITY possono essere erroneamente denominate come un vincolo. L'istruzione `CREATE TABLE T (C1 int CONSTRAINT MyConstraint IDENTITY)`, ad esempio, viene eseguita correttamente, ma il nome del vincolo non viene mantenuto e non è accessibile per l'utente.|Le proprietà di colonna ROWGUIDCOL e IDENTITY non possono essere denominate come un vincolo. In caso contrario, verrà restituito l'errore 156.|Basso|  
|L'aggiornamento di colonne tramite un'assegnazione bidirezionale, ad esempio `UPDATE T1 SET @v = column_name = <expression>`, può produrre risultati imprevisti, in quanto è possibile che durante l'esecuzione dell'istruzione in altre clausole quali WHERE e ON venga utilizzato il valore attivo della variabile anziché il valore iniziale dell'istruzione. Ciò può comportare una modifica imprevista dei significati dei predicati per ciascuna riga.<br /><br /> Questo comportamento è applicabile solo quando il livello di compatibilità è impostato su 90.|L'aggiornamento di colonne tramite un'assegnazione bidirezionale produce i risultati previsti, in quanto durante l'esecuzione dell'istruzione è possibile accedere solo al valore iniziale dell'istruzione per la colonna.|Basso|  
|Vedere l'esempio E nella sezione esempi riportata di seguito.|Vedere l'esempio F nella sezione esempi riportata di seguito.|Basso|  
|La funzione ODBC {fn CONVERT()} utilizza il formato di data predefinito della lingua specifica. Per alcune lingue il formato predefinito è AGM, che può comportare errori di conversione quando la funzione CONVERT() è combinata con altre funzioni, ad esempio {fn CURDATE()}, che prevedono l'utilizzo del formato AMG.|La funzione ODBC {fn CONVERT()} utilizza lo stile 121, un formato AMG indipendente dalla lingua, per la conversione nei tipi di dati ODBC SQL_TIMESTAMP, SQL_DATE, SQL_TIME, SQLDATE, SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP.|Basso|  
|Le funzioni intrinseche datetime, ad esempio DATEPART, non richiedono che i valori di input di tipo stringa siano valori letterali datetime validi. La funzione SELECT DATEPART (year, '2007/05-30'), ad esempio, viene compilata correttamente.|Le funzioni intrinseche datetime, ad esempio DATEPART, richiedono che i valori di input di tipo stringa siano valori letterali datetime validi. Quando si utilizza un valore letterale datetime non valido, viene restituito l'errore 241.|Basso|  
  
## <a name="reserved-keywords"></a>Parole chiave riservate  
 L'impostazione di compatibilità determina anche le parole chiave riservate dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Nella tabella seguente sono elencate le parole chiave riservate introdotte per ogni livello di compatibilità.  
  
|Livello di compatibilità|Parole chiave riservate|  
|----------------------------------|-----------------------|  
|130|Per essere determinato.|  
|120|nessuna.|  
|110|WITHIN GROUP, TRY_CONVERT, SEMANTICKEYPHRASETABLE, SEMANTICSIMILARITYDETAILSTABLE, SEMANTICSIMILARITYTABLE|  
|100|CUBE, MERGE, ROLLUP|  
|90|EXTERNAL, PIVOT, UNPIVOT, REVERT, TABLESAMPLE|  
  
 A un determinato livello di compatibilità, le parole chiave riservate includono tutte le parole chiave introdotte per tale livello e per quelli precedenti. Pertanto, ad esempio, per le applicazioni con livello 110 tutte le parole chiave elencate nella tabella precedente sono parole chiave riservate. Per i livelli di compatibilità inferiori, le parole chiave del livello 100 rimangono nomi di oggetti validi ma le funzionalità del linguaggio di livello 110 corrispondenti a tale parole chiave non sono disponibili.  
  
 Una volta introdotta, una parola chiave rimane riservata. La parola chiave riservata PIVOT, ad esempio, introdotta per il livello di compatibilità 90, è riservata per i livelli 100, 110 e 120.  
  
 Se per un'applicazione si utilizza un identificatore che rappresenta una parola chiave riservata nel livello di compatibilità relativo, viene generato un errore. Per risolvere il problema, racchiudere l'identificatore tra una parentesi (**[]**) o virgolette (**""**), ad esempio, per aggiornare un'applicazione che utilizza l'identificatore **esterno** a livello di compatibilità 90, è possibile modificare l'identificatore per uno **[EXTERNAL]** o **"EXTERNAL"**.  
  
 Per altre informazioni, vedere [Parole chiave riservate &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-compatibility-level"></a>A. Modifica del livello di compatibilità  
 L'esempio seguente modifica il livello di compatibilità di [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database `110,` [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 110;  
GO  
```  
  
 L'esempio seguente restituisce il livello di compatibilità del database corrente.  
  
```tsql  
SELECT name, compatibility_level   
FROM sys.databases   
WHERE name = db_name();  
```  
  
### <a name="b-ignoring--the-set-language-statement-except-under-compatibility-level-120"></a>B. Ignorando l'istruzione SET LANGUAGE tranne con il livello di compatibilità 120  
 La query seguente ignora l'istruzione SET LANGUAGE tranne con il livello di compatibilità 120.  
  
```tsql  
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
  
```tsql  
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
 In questo esempio mostra la differenza tra gli stili 0 e 121. Per ulteriori informazioni sugli stili di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
```tsql  
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
  
```tsql  
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
  
```tsql  
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
  
  

