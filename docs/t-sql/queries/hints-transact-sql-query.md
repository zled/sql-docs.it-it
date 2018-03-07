---
title: Eseguire una query hint (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Query_Hint_TSQL
- Query_TSQL
- Query
- Query Hint
- MAX_GRANT_PERCENT
- MAX_GRANT_PERCENT_TSQL
- MIN_GRANT_PERCENT
- MIN_GRANT_PERCENT_TSQL
- EXTERNALPUSHDOWN
- EXTERNALPUSHDOWN_TSQL
- NOLOCK_TSQL
- MAXDOP_TSQL
- USE_HINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REPORT PLAN query hint
- FORCE ORDER query hint
- HASH JOIN query hint
- query hints [SQL Server]
- OPTIMIZE FOR query hint
- FORCESCAN query hint
- RECOMPILE query hint
- MAXRECURSION query hint
- MERGE JOIN query hint
- HASH GROUP query hint
- KEEP PLAN query hint
- UNION query hint
- FORCESEEK query hint
- ORDER GROUP query hint
- LOOP JOIN query hint
- KEEPFIXED PLAN query hint
- FAST query hint
- MAXDOP query hint
- PARAMETERIZATION query hint
- hints [SQL Server], query
- JOIN query hint
- USE PLAN query hint
- EXPAND VIEWS query hint
- MAX_GRANT_PERCENT query hint
- MIN_GRANT_PERCENT query hint
- EXTERNALPUSHDOWN query hint
- USE HINT query hint
ms.assetid: 66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0a3c74aa7b1da86c6d0ac54025d337700019465d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="hints-transact-sql---query"></a>Hints (Transact-SQL) - Query
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gli hint per la query specificano che gli hint indicati devono essere utilizzati in tutta la query e influiscono su tutti gli operatori dell'istruzione. Se la query principale include l'operatore UNION, la clausola OPTION può essere specificata solo nell'ultima query che prevede un'operazione di tipo UNION. Hint per la query vengono specificati come parte di [clausola OPTION](../../t-sql/queries/option-clause-transact-sql.md). Se in seguito alla presenza di uno o più hint per la query non viene creato un piano valido da Query Optimizer, viene generato l'errore 8622.  
  
> [!CAUTION]  
>  Poiché Query Optimizer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in genere seleziona il piano di esecuzione migliore per una query, è consigliabile utilizzare hint solo se strettamente necessario e sempre da parte di sviluppatori e amministratori esperti di database.  
  
 **Si applica a:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [INSERT](../../t-sql/statements/insert-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 [MERGE](../../t-sql/statements/merge-transact-sql.md)  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
<query_hint > ::=   
{ { HASH | ORDER } GROUP   
  | { CONCAT | HASH | MERGE } UNION   
  | { LOOP | MERGE | HASH } JOIN   
  | EXPAND VIEWS   
  | FAST number_rows   
  | FORCE ORDER   
  | { FORCE | DISABLE } EXTERNALPUSHDOWN  
  | IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
  | KEEP PLAN   
  | KEEPFIXED PLAN  
  | MAX_GRANT_PERCENT = percent  
  | MIN_GRANT_PERCENT = percent  
  | MAXDOP number_of_processors   
  | MAXRECURSION number   
  | NO_PERFORMANCE_SPOOL   
  | OPTIMIZE FOR ( @variable_name { UNKNOWN | = literal_constant } [ , ...n ] )  
  | OPTIMIZE FOR UNKNOWN  
  | PARAMETERIZATION { SIMPLE | FORCED }  
  | RECOMPILE  
  | ROBUST PLAN   
  | USE HINT ( '<hint_name>' [ , ...n ] )
  | USE PLAN N'xml_plan'  | TABLE HINT ( exposed_object_name [ , <table_hint> [ [, ]...n ] ] )  
}  
  
<table_hint> ::=  
[ NOEXPAND ] {   
    INDEX ( index_value [ ,...n ] ) | INDEX = ( index_value )  
  | FORCESEEK [( index_value ( index_column_name [,... ] ) ) ]  
  | FORCESCAN  
  | HOLDLOCK   
  | NOLOCK   
  | NOWAIT  
  | PAGLOCK   
  | READCOMMITTED   
  | READCOMMITTEDLOCK   
  | READPAST   
  | READUNCOMMITTED   
  | REPEATABLEREAD   
  | ROWLOCK   
  | SERIALIZABLE   
  | SNAPSHOT  
  | SPATIAL_WINDOW_MAX_CELLS = integer  
  | TABLOCK   
  | TABLOCKX   
  | UPDLOCK   
  | XLOCK  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 { HASH | ORDER } GROUP  
 Specifica che nelle funzioni di aggregazione elencate nella clausola GROUP BY o DISTINCT della query devono essere utilizzate operazioni di hashing o di ordinamento.  
  
 { MERGE | HASH | CONCAT } UNION  
 Specifica che per tutte le operazioni UNION vengono eseguite operazioni di unione, hashing o concatenazione dei set UNION. Se viene specificato più di un hint UNION, Query Optimizer seleziona la strategia meno onerosa tra gli hint specificati.  
  
 { LOOP | MERGE | HASH } JOIN  
 Specifica che tutte le operazioni JOIN vengono eseguite da LOOP JOIN, MERGE JOIN o HASH JOIN nell'intera query. Se vengono specificati più hint di join, Query Optimizer seleziona la strategia di join meno onerosa tra i join consentiti.  
  
 Se nella stessa query un hint di join viene specificato nella clausola FROM anche per una particolare coppia di tabelle, tale hint risulta prioritario rispetto all'unione in join delle due tabelle. Gli hint per la query devono essere comunque rispettati. L'hint di join della coppia di tabelle pertanto consente di limitare solo la selezione dei metodi di join consentiti nell'hint per la query. Per ulteriori informazioni, vedere [hint di Join &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-join.md).  
  
 EXPAND VIEWS  
 Specifica che le viste indicizzate vengono espanse e che in Query Optimizer non viene presa in considerazione alcuna vista indicizzata per la sostituzione di una parte della query. Una vista viene espansa quando nel testo della query il nome della vista viene sostituito dalla definizione della vista stessa.  
  
 Con questo hint per la query viene praticamente disabilitato l'utilizzo diretto di viste indicizzate e di relativi indici nel piano di query.  
  
 La vista indicizzata non viene espansa solo se la vista fa riferimento direttamente nella sezione SELECT della query e WITH (NOEXPAND) o WITH (NOEXPAND, INDEX ( *index_value* [**, *... n* ])) è specificato. Per ulteriori informazioni sull'hint per la query WITH (NOEXPAND), vedere [FROM](../../t-sql/queries/from-transact-sql.md).  
  
 L'hint influisce solo sulle viste nella sezione SELECT delle istruzioni, comprese le sezioni delle istruzioni INSERT, UPDATE, MERGE e DELETE.  
  
 FAST *number_rows*  
 Specifica che la query è ottimizzata per il recupero rapido del primo *number_rows.* Si tratta di un numero intero non negativo. Dopo il primo *number_rows* vengono restituiti, l'esecuzione continua, la query produce un set di risultati completo.  
  
 FORCE ORDER  
 Specifica che l'ordine di join indicato dalla sintassi della query viene conservato durante l'ottimizzazione della query. L'utilizzo dell'hint FORCE ORDER non ha alcun effetto sulla possibile inversione dei ruoli in Query Optimizer.  
  
> [!NOTE]  
>  In un'istruzione MERGE, l'accesso alla tabella di origine viene eseguito prima della tabella di destinazione come ordine di join predefinito, a meno che non sia specificata la clausola WHEN SOURCE NOT MATCHED. Specificando FORCE ORDER viene conservato questo comportamento predefinito.  
  
 {FORCE | DISABILITARE} EXTERNALPUSHDOWN NON È  
 Forzare o disabilitare la distribuzione del calcolo di qualificazione di espressioni in Hadoop. Si applica solo alle query con PolyBase. Non determinerà verso il basso nell'archiviazione di Azure.  
  
 KEEP PLAN  
 Forza in Query Optimizer l'impostazione di una soglia di ricompilazione stimata meno restrittiva per una query. La soglia di ricompilazione stimata è il punto in corrispondenza del quale una query viene automaticamente ricompilata quando in una tabella è stato apportato il numero stabilito di modifiche a livello di colonne indicizzate mediante l'esecuzione delle istruzioni UPDATE, DELETE, MERGE o INSERT. Specificando KEEP PLAN è possibile assicurarsi che una query non venga ricompilata troppo frequentemente in caso di più aggiornamenti di una tabella.  
  
 KEEPFIXED PLAN  
 Impedisce a Query Optimizer di ricompilare una query in seguito a modifiche alle statistiche. Specifica KEEPFIXED PLAN assicura che una query viene ricompilata solo se lo schema delle tabelle sottostanti viene modificato o se **sp_recompile** viene eseguita su tali tabelle.  
  
 IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Impedisce alla query l'utilizzo di un indice columnstore con ottimizzazione per la memoria non cluster. Se la query contiene l'hint per la query per evitare l'utilizzo dell'indice columnstore e un hint per l'indice per utilizzare un indice columnstore, gli hint sono in conflitto e la query restituisce un errore.  
  
 MAX_GRANT_PERCENT = *percent*  
 Dimensioni in percentuale di concessione di memoria massima. La query non è sicuramente supera questo limite. Il limite effettivo può essere inferiore se è inferiore rispetto a questa impostazione di resource governor. I valori validi sono compresi tra 0,0 e 100.0.  
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 MIN_GRANT_PERCENT = *percent*  
 Dimensioni in percentuale di concessione di memoria minima = % del limite predefinito. La query sarà disponibile per ottenere MAX (memoria necessaria, grant min), poiché almeno richiesta di memoria necessaria per avviare una query. I valori validi sono compresi tra 0,0 e 100.0.  
  
**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 MAXDOP *numero*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Esegue l'override di **massimo grado di parallelismo** opzione di configurazione di **sp_configure** e Resource Governor per la query che specifica tale opzione. L'hint per la query MAXDOP può superare il valore configurato con sp_configure. Se MAXDOP supera il valore configurato con Resource Governor il [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilizza il valore MAXDOP di Resource Governor, descritto in [ALTER WORKLOAD GROUP &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-workload-group-transact-sql.md). Tutte le regole semantiche utilizzate con la **massimo grado di parallelismo** opzione di configurazione sono applicabili quando si utilizza l'hint per la query MAXDOP. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
> [!WARNING]  
> Se MAXDOP è impostato su zero, il server sceglie il grado massimo di parallelismo.  
  
 MAXRECURSION *numero*  
 Specifica il numero massimo di ricorsioni consentito per questa query. *numero* è un numero intero non negativo compreso tra 0 e 32767. Se è specificato 0, non viene applicato alcun limite. Se questa opzione non viene specificata, il limite predefinito per il server è 100.  
  
 Se durante l'esecuzione della query viene raggiunto il valore specificato o predefinito per il limite MAXRECURSION, la query viene terminata e viene restituito un errore.  
  
 A causa di questo errore, verrà eseguito il rollback di tutti gli effetti dell'istruzione. Se l'istruzione è un'istruzione SELECT, è possibile che vengano restituiti risultati parziali oppure nessun risultato. È possibile che eventuali risultati parziali non includano tutte le righe nei livelli di ricorsione che superano il livello di ricorsione massimo specificato.  
  
 Per ulteriori informazioni, vedere [con common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 NO_PERFORMANCE_SPOOL  
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Impedisce che un operatore spool aggiungere ai piani di query (tranne i piani quando spool è necessario per garantire la semantica di aggiornamento valido). In alcuni scenari, l'operatore di spooling può ridurre le prestazioni. Ad esempio, lo spool utilizza tempdb e potrebbe verificarsi un conflitto di tempdb, esiste un caso di numerose query simultanee in esecuzione con le operazioni di spooling.  
  
 OPTIMIZE FOR (  *@variable_name*  {sconosciuto | = *literal_constant}* [ **,** ... *n* ] )  
 Imposta Query Optimizer in modo che utilizzi un valore specifico per una variabile locale quando la query viene compilata e ottimizzata. Il valore viene utilizzato solo durante l'ottimizzazione della query e non durante l'esecuzione.  
  
 *@variable_name*  
 Nome di una variabile locale utilizzata in una query alla quale è possibile assegnare un valore da utilizzare con l'hint per la query OPTIMIZE FOR.  
  
 *UNKNOWN*  
 Specifica che Query Optimizer utilizza dati statistici anziché il valore iniziale per determinare il valore per una variabile locale durante l'ottimizzazione della query.  
  
 *literal_constant*  
 È un valore letterale costante da assegnare  *@variable_name*  per l'utilizzo con l'hint di query OPTIMIZE FOR. *literal_constant* viene utilizzato solo durante l'ottimizzazione della query e non come valore di  *@variable_name*  durante l'esecuzione di query. *literal_constant* possono essere di qualsiasi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati di sistema che può essere espresso come valore letterale costante. Il tipo di dati *literal_constant* deve essere implicitamente convertibile nei dati di tipo che  *@variable_name*  riferimenti nella query.  
  
 OPTIMIZE FOR può annullare la funzionalità di rilevamento predefinita dei parametri di Query Optimizer oppure può essere utilizzato durante la creazione delle guide di piano. Per ulteriori informazioni, vedere [ricompilare una Stored Procedure](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md).  
  
 OPTIMIZE FOR UNKNOWN  
 Indica a Query Optimizer di utilizzare dati statistici anziché i valori iniziali per tutte le variabili locali quando la query viene compilata e ottimizzata, includendo parametri creati con parametrizzazione forzata.  
  
 Se OPTIMIZE FOR @variable_name = *literal_constant* e OPTIMIZE FOR UNKNOWN sono utilizzati nell'hint per la stessa query, query optimizer utilizzerà il *literal_constant* specificato per un valore specifico e SCONOSCIUTO per i valori di variabile rimanenti. I valori vengono utilizzati durante l'ottimizzazione della query e non durante l'esecuzione di questa.  
  
 PARAMETERIZATION { SIMPLE | FORCED }  
 Specifica le regole di parametrizzazione applicate da Query Optimizer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla query durante la compilazione di questa.  
  
> [!IMPORTANT]  
> L'hint per la query PARAMETERIZATION può essere specificato solo all'interno di una guida di piano e non direttamente all'interno di una query.  
  
 SIMPLE indica a Query Optimizer di tentare la parametrizzazione semplice. FORCED indica a Query Optimizer di tentare la parametrizzazione forzata. L'hint per la query PARAMETERIZATION viene utilizzato per sostituire l'impostazione corrente dell'opzione SET dell'hint di database PARAMETERIZATION all'interno di una guida di piano. Per ulteriori informazioni, vedere [specificare parametrizzazione delle Query da utilizzare le guide di piano](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md).  
  
 RECOMPILE  
 Indica a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] di eliminare il piano generato per la query dopo che questa è stata eseguita e forza Query Optimizer a ricompilare un piano di query alla successiva esecuzione della stessa query. RECOMPILE, non viene specificato il [!INCLUDE[ssDE](../../includes/ssde-md.md)] memorizza nella cache i piani di query e riutilizzati da. Durante la compilazione dei piani di query, l'hint per la query RECOMPILE utilizza i valori correnti delle variabili locali incluse nella query e, se la query è contenuta in una stored procedure, i valori correnti vengono passati ai parametri.  
  
 RECOMPILE rappresenta una valida alternativa alla creazione di una stored procedure che utilizza la clausola WITH RECOMPILE quando è necessario ricompilare solo un subset di query all'interno della stored procedure, anziché l'intera stored procedure. Per ulteriori informazioni, vedere [ricompilare una Stored Procedure](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md). RECOMPILE risulta utile anche durante la creazione delle guide di piano.  
  
 ROBUST PLAN  
 Impone in Query Optimizer l'applicazione di un piano che funziona anche con dimensioni di riga massime, eventualmente a scapito delle prestazioni. Quando la query viene elaborata, è possibile che tabelle e operatori intermedi debbano archiviare ed elaborare righe con dimensioni maggiori rispetto a qualsiasi riga di input. Talvolta le righe possono essere talmente estese che l'operatore specificato non è in grado di elaborarle. In questi casi, [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un errore durante l'esecuzione della query. Grazie alla clausola ROBUST PLAN, i piani di query in cui potrebbe verificarsi questo problema vengono ignorati da Query Optimizer.  
  
 Se non è possibile implementare tale piano, viene restituito un errore anziché posticipare il rilevamento dell'errore fino all'esecuzione della query. Le righe possono includere colonne di lunghezza variabile. In [!INCLUDE[ssDE](../../includes/ssde-md.md)] è consentito definire righe con dimensioni massime superiori alla capacità di elaborazione di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. In un'applicazione tuttavia vengono in genere archiviate righe le cui dimensioni effettive rientrano nei limiti della capacità di elaborazione di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Se in [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene rilevata una riga di lunghezza eccessiva, viene restituito un errore di esecuzione.  
 
<a name="use_hint"></a>HINT USE ( **'***hint_name***'** )  
 **Si applica a**: si applica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) e [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
 
 Fornisce uno o più hint aggiuntivi per il processore di query come specificato da un nome di hint **all'interno di virgolette singole**. 

 Sono supportati i nomi di hint seguenti:
 
*  'DISABLE_OPTIMIZED_NESTED_LOOP'  
 Indica al processore di query non è consigliabile usare un'operazione di ordinamento (ordinamento batch) per ottimizzato nested loop join durante la generazione di un piano di query. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2340.
*  'FORCE_LEGACY_CARDINALITY_ESTIMATION'  
 Impone a query optimizer di utilizzare [la stima della cardinalità](../../relational-databases/performance/cardinality-estimation-sql-server.md) modello di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e nelle versioni precedenti. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481 o [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) impostazione LEGACY_CARDINALITY_ESTIMATION = ON.
*  'ENABLE_QUERY_OPTIMIZER_HOTFIXES'  
 Consente di hotfix di query optimizer (modifiche rilasciate in aggiornamenti cumulativi di SQL Server e i Service Pack). Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4199 o [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) impostazione QUERY_OPTIMIZER_HOTFIXES = ON.
*  'DISABLE_PARAMETER_SNIFFING'  
 Indica a query optimizer di utilizzare una distribuzione dei dati media durante la compilazione di una query con uno o più parametri, rendere il piano di query indipendenti sul valore del parametro prima utilizzato quando la query è stata compilata. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4136 o [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) impostazione PARAMETER_SNIFFING = OFF.
*  'ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES'  
 Determina in SQL Server generare un piano con selettività minimo per la stima dei predicati e per i filtri per tenere conto per la correlazione. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4137 quando si utilizza il modello di stima della cardinalità di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni precedenti, e ha un effetto simile quando [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9471 viene utilizzato con cardinalità modello di stima di [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] o versione successiva.
*  'DISABLE_OPTIMIZER_ROWGOAL'  
 Determina in SQL Server generare un piano che non utilizza rettifiche di obiettivo di riga con le query che contengono la clausola TOP, OPTION (FAST N), o parole chiave è presente. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4138.
*  'ENABLE_HIST_AMENDMENT_FOR_ASC_KEYS'  
 Abilita generate automaticamente statistiche rapide (modifica istogramma) per qualsiasi colonna di indice iniziale per cui cardinalità è necessaria la stima. In fase di compilazione di query per tenere conto per il valore massimo o minimo effettivo di questa colonna verrà regolata l'istogramma usato per la stima della cardinalità. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4139. 
*  'ASSUME_JOIN_PREDICATE_DEPENDS_ON_FILTERS'  
 Determina in SQL Server generare un piano di query utilizzando il presupposto di indipendenza semplice anziché il presupposto di indipendenza di Base predefinito per i join, in query optimizer [la stima della cardinalità](../../relational-databases/performance/cardinality-estimation-sql-server.md) modello di [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] o versione successiva. Ciò equivale a [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9476. 
*  'FORCE_DEFAULT_CARDINALITY_ESTIMATION'  
 Impone a Query Optimizer di utilizzare [la stima della cardinalità](../../relational-databases/performance/cardinality-estimation-sql-server.md) modello che corrisponde al livello di compatibilità del database corrente. Utilizzare questo hint per eseguire l'override [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) impostazione LEGACY_CARDINALITY_ESTIMATION = ON o [flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481.
 
> [!TIP]
> I nomi di hint sono tra maiuscole e minuscole.
  
  L'elenco di tutti i nomi di HINT USE supportati può essere eseguita utilizzando la vista a gestione dinamica [sys.dm_exec_valid_use_hints ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md).
> [!IMPORTANT] 
> Alcuni suggerimenti HINT USE sia in conflitto con i flag di traccia abilitati a livello globale o le impostazioni di configurazione con ambito di livello di sessione o database. In questo caso, l'hint del livello di query (utilizzare HINT) ha sempre la precedenza. Se un HINT USE è in conflitto con un altro hint per la query o un flag di traccia abilitato a livello di query (ad esempio da QUERYTRACEON), SQL Server verrà generato un errore durante il tentativo di eseguire la query. 

 USE PLAN N**'***xml_plan***'**  
 Impone a query optimizer di utilizzare un piano di query esistente per una query specificato da **'***xml_plan***'**. USE PLAN non può essere specificato nelle istruzioni INSERT, UPDATE, MERGE o DELETE.  
  
HINT di tabella  **(* * * exposed_object_name* [ **,** \<table_hint > [[* *,**]...  *n*  ]] **)** Si applica l'hint di tabella specificato alla tabella o vista che corrisponde a *exposed_object_name*. È consigliabile utilizzare un hint di tabella come hint per la query solo nel contesto di un [Guida di piano](../../relational-databases/performance/plan-guides.md).  
  
 *exposed_object_name* può essere uno dei seguenti riferimenti:  
  
-   Quando viene utilizzato un alias per la tabella o vista nel [FROM](../../t-sql/queries/from-transact-sql.md) clausola di query, *exposed_object_name* è l'alias.  
  
-   Quando non viene utilizzato un alias, *exposed_object_name* è la corrispondenza esatta della tabella o della vista a cui fa riferimento nella clausola FROM. Se la tabella o la vista viene fatto riferimento utilizzando un nome in due parti, ad esempio *exposed_object_name* è lo stesso nome di due parti.  
  
 Quando *exposed_object_name* senza specificare anche un hint di tabella, tutti gli indici specificati nella query come parte di un hint di tabella per l'oggetto viene ignorato e l'utilizzo degli indici è determinato da query optimizer. È possibile utilizzare questa tecnica per eliminare l'effetto di un hint di tabella INDEX quando non è possibile modificare la query originale. Vedere l'esempio J.  
  
**\<table_hint >:: =** {[NOEXPAND] {indice ( *index_value* [,... *n* ] ) | INDICE = ( *index_value* ) | FORCESEEK [**(***index_value***(* * * index_column_name* [**,**...] **))** ]| FORCESCAN | HOLDLOCK | NOLOCK | NOWAIT | PAGLOCK | READCOMMITTED | READCOMMITTEDLOCK | READPAST | READUNCOMMITTED | REPEATABLEREAD | ROWLOCK | SERIALIZZABILE | SNAPSHOT | SPATIAL_WINDOW_MAX_CELLS | TABLOCK | TABLOCKX | UPDLOCK | XLOCK} è l'hint di tabella da applicare alla tabella o vista che corrisponde a *exposed_object_name* come hint per la query. Per una descrizione di questi hint, vedere [hint di tabella &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Gli hint di tabella diversi da INDEX, FORCESCAN e FORCESEEK non sono consentiti come hint per la query, a meno che la query non disponga già di una clausola WITH che specifica l'hint di tabella. Per altre informazioni, vedere la sezione Osservazioni.  
  
> [!CAUTION] 
> Se si specifica FORCESEEK con parametri, il numero di piani che possono essere considerati da Query Optimizer viene limitato più di quanto avvenga se si specifica FORCESEEK senza parametri. In questo caso potrebbe venire generato un errore "Impossibile generare il piano" con maggiore frequenza. In una versione futura, le modifiche interne a Query Optimizer potrebbero consentire di prendere in considerazione più piani.  
  
## <a name="remarks"></a>Osservazioni  
 Gli hint per la query non possono essere specificati in un'istruzione INSERT, eccetto quando una clausola SELECT viene utilizzata all'interno dell'istruzione.  
  
 È possibile specificare gli hint per la query solo nella query di livello principale e non nelle sottoquery. Quando un hint di tabella viene specificato come hint per la query, l'hint può essere specificato nella query di livello superiore o in una sottoquery; Tuttavia, il valore specificato per *exposed_object_name* nell'HINT di tabella clausola deve corrispondere esattamente al nome esposto nella query o sottoquery.  
  
## <a name="specifying-table-hints-as-query-hints"></a>Specifica di hint di tabella come hint per la query  
 È consigliabile utilizzare l'hint di tabella INDEX, FORCESCAN o FORCESEEK come hint per la query solo nel contesto di un [Guida di piano](../../relational-databases/performance/plan-guides.md). Le guide di piano sono utili quando non è possibile modificare la query originale, ad esempio perché si tratta di un'applicazione di terze parti. L'hint per la query specificato nella guida di piano viene aggiunto alla query prima della compilazione e dell'ottimizzazione. Per le query ad hoc, utilizzare la clausola TABLE HINT solo quando si testano istruzioni della guida di piano. Per tutte le altre query ad hoc, è consigliabile specificare tali hint solo come hint di tabella.  
  
 Se specificati come hint per la query, gli hint di tabella INDEX, FORCESCAN e FORCESEEK sono validi per gli oggetti seguenti:  
  
-   Tabelle  
  
-   Viste  
  
-   Viste indicizzate  
  
-   Espressioni di tabella comuni (l'hint deve essere specificato nell'istruzione SELECT il cui set di risultati popola l'espressione di tabella comune)  
  
-   DMV  
  
-   Sottoquery denominate  
  
 Gli hint di tabella INDEX, FORCESCAN e FORCESEEK possono essere specificati come hint per la query senza hint di tabella esistenti oppure possono essere utilizzati per sostituire uno o più hint INDEX, FORCESCAN o FORCESEEK esistenti nella query. Gli hint di tabella diversi da INDEX, FORCESCAN e FORCESEEK non sono consentiti come hint per la query, a meno che la query non disponga già di una clausola WITH che specifica l'hint di tabella. In questo caso è necessario specificare inoltre un hint corrispondente come un hint per la query utilizzando TABLE HINT nella clausola OPTION per mantenere la semantica della query. Ad esempio, se la query contiene l'hint di tabella NOLOCK, la clausola OPTION nel  **@hints**  parametro della Guida di piano deve contenere anche l'hint NOLOCK. Vedere l'esempio K. Quando un hint di tabella diverso da INDEX, FORCESCAN o FORCESEEK viene specificato utilizzando TABLE HINT nella clausola OPTION senza un hint per la query corrispondente, o viceversa, viene generato l'errore 8702, che indica che la clausola OPTION può comportare la modifica della semantica della query, e la query ha esito negativo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-merge-join"></a>A. Utilizzo di MERGE JOIN  
 Nell'esempio seguente specifica che l'operazione di JOIN nella query viene eseguita dal MERGE JOIN. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT *   
FROM Sales.Customer AS c  
INNER JOIN Sales.CustomerAddress AS ca ON c.CustomerID = ca.CustomerID  
WHERE TerritoryID = 5  
OPTION (MERGE JOIN);  
GO    
```  
  
### <a name="b-using-optimize-for"></a>B. Utilizzo di OPTIMIZE FOR  
 Nell'esempio seguente indica a query optimizer di utilizzare il valore `'Seattle'` per la variabile locale `@city_name` e di utilizzare dati statistici per determinare il valore per la variabile locale `@postal_code` quando l'ottimizzazione della query. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
DECLARE @city_name nvarchar(30);  
DECLARE @postal_code nvarchar(15);  
SET @city_name = 'Ascheim';  
SET @postal_code = 86171;  
SELECT * FROM Person.Address  
WHERE City = @city_name AND PostalCode = @postal_code  
OPTION ( OPTIMIZE FOR (@city_name = 'Seattle', @postal_code UNKNOWN) );  
GO  
```  
  
### <a name="c-using-maxrecursion"></a>C. Utilizzo di MAXRECURSION  
 È possibile utilizzare MAXRECURSION per evitare che un'espressione di tabella comune (CTE) ricorsiva non corretta provochi un ciclo infinito. Nell'esempio seguente è intenzionalmente crea un ciclo infinito e utilizza l'hint MAXRECURSION per limitare il numero di livelli di ricorsione a due. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
--Creates an infinite loop  
WITH cte (CustomerID, PersonID, StoreID) AS  
(  
    SELECT CustomerID, PersonID, StoreID  
    FROM Sales.Customer  
    WHERE PersonID IS NOT NULL  
  UNION ALL  
    SELECT cte.CustomerID, cte.PersonID, cte.StoreID  
    FROM cte   
    JOIN  Sales.Customer AS e   
        ON cte.PersonID = e.CustomerID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT CustomerID, PersonID, StoreID  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 Dopo la correzione dell'errore del codice, MAXRECURSION non è più necessario.  
  
### <a name="d-using-merge-union"></a>D. Utilizzo di MERGE UNION  
 Nell'esempio seguente viene utilizzato l'hint di query MERGE UNION. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT *  
FROM HumanResources.Employee AS e1  
UNION  
SELECT *  
FROM HumanResources.Employee AS e2  
OPTION (MERGE UNION);  
GO  
```  
  
### <a name="e-using-hash-group-and-fast"></a>E. Utilizzo di HASH GROUP e FAST  
 L'esempio seguente usa l'HASH GROUP e FAST hint per la query. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO    
```  
  
### <a name="f-using-maxdop"></a>F. Utilizzo di MAXDOP  
 Nell'esempio seguente viene utilizzato l'hint di query MAXDOP. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (MAXDOP 2);    
GO
```  
  
### <a name="g-using-index"></a>G. Utilizzo di INDEX  
 Nell'esempio seguente viene utilizzato l'hint INDEX. Nel primo esempio viene specificato un singolo indice. Nel secondo esempio vengono specificati più indici per un singolo riferimento alla tabella. In entrambi gli esempi, dal momento che l'hint INDEX è applicato a una tabella che utilizza un alias, anche la clausola TABLE HINT deve specificare lo stesso alias del nome dell'oggetto esposto. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide1',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX (IX_Employee_ManagerID)))';  
GO  
EXEC sp_create_plan_guide   
    @name = N'Guide2',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX(PK_Employee_EmployeeID, IX_Employee_ManagerID)))';  
GO    
```  
  
### <a name="h-using-forceseek"></a>H. Utilizzo di FORCESEEK  
 Nell'esempio seguente viene utilizzato l'hint di tabella FORCESEEK. Dal momento che l'hint INDEX è applicato a una tabella che utilizza un nome in due parti, anche la clausola TABLE HINT deve specificare lo stesso nome in due parti del nome dell'oggetto esposto. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide3',   
    @stmt = N'SELECT c.LastName, c.FirstName, HumanResources.Employee.Title  
              FROM HumanResources.Employee  
              JOIN Person.Contact AS c ON HumanResources.Employee.ContactID = c.ContactID  
              WHERE HumanResources.Employee.ManagerID = 3  
              ORDER BY c.LastName, c.FirstName;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT( HumanResources.Employee, FORCESEEK))';  
GO    
```  
  
### <a name="i-using-multiple-table-hints"></a>I. Utilizzo di più hint di tabella  
 Nell'esempio seguente vengono applicati l'hint INDEX a una tabella e l'hint FORCESEEK a un'altra. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide4',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX( IX_Employee_ManagerID))   
                       , TABLE HINT (c, FORCESEEK))';  
GO  
```  
  
### <a name="j-using-table-hint-to-override-an-existing-table-hint"></a>J. Utilizzo di TABLE HINT per eseguire l'override di un hint di tabella esistente  
 Nell'esempio seguente viene illustrato come utilizzare l'hint TABLE HINT senza specificare un hint per eseguire l'override del comportamento dell'hint di tabella INDEX specificato nella clausola FROM della query. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide5',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e WITH (INDEX (IX_Employee_ManagerID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e))';  
GO    
```  
  
### <a name="k-specifying-semantics-affecting-table-hints"></a>K. Specifica di hint di tabella che influiscono sulla semantica  
 Nell'esempio seguente sono contenuti due hint di tabella nella query: NOLOCK, che influisce sulla semantica, e INDEX, che non influisce sulla semantica. Per mantenere la semantica della query l’hint NOLOCK viene specificato nella clausola OPTIONS della guida di piano. Oltre all'hint NOLOCK, vengono specificati gli hint INDEX e FORCESEEK che sostituiscono l'hint INDEX che non influisce sulla semantica nella query quando l'istruzione viene compilata e ottimizzata. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide6',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX(IX_Employee_ManagerID), NOLOCK, FORCESEEK))';  
GO    
```  
  
 Nell'esempio seguente viene illustrato un metodo alternativo per mantenere la semantica della query e consentire a Query Optimizer di scegliere un indice diverso da quello specificato nell'hint di tabella. A tale scopo occorre specificare l'hint NOLOCK nella clausola OPTIONS (poiché influisce sulla semantica) e la parola chiave TABLE HINT con solo un riferimento alla tabella e nessun hint INDEX. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide7',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, NOLOCK))';  
GO  
```  
### <a name="l-using-use-hint"></a>L. Utilizzando l'HINT USE  
 Nell'esempio seguente viene utilizzato l'hint per la query RECOMPILE e utilizzare HINT. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (RECOMPILE, USE HINT ('ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES', 'DISABLE_PARAMETER_SNIFFING')); 
GO  
```  
    
## <a name="see-also"></a>Vedere anche  
 [Hints &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_control_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
 [Flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  
