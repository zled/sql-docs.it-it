---
title: INSERT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INSERT_TSQL
- INSERT
dev_langs:
- TSQL
helpviewer_keywords:
- inserting multiple rows
- user-defined types [SQL Server], inserting values
- DML [SQL Server], INSERT statement
- bulk load [SQL Server]
- row additions [SQL Server], INSERT statement
- inserting rows
- table value constructor [SQL Server]
- adding data
- INSERT statement [SQL Server], about INSERT statement
- INSERT statement [SQL Server]
- UDTs [SQL Server], inserting values
- adding rows
- INSERT INTO statement
- data manipulation language [SQL Server], INSERT statement
- inserting data
ms.assetid: 1054c76e-0fd5-4131-8c07-a6c5d024af50
caps.latest.revision: 136
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ef8387c2bbbc109ad7ec325e4faf632a983d96c9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="insert-transact-sql"></a>INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Consente di aggiungere una o più righe a una tabella o a una vista in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per esempi, vedere [esempi](#InsertExamples).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  

[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ ( column_list ) ]   
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
  table_or_view_name  
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  
```  
  
```  
-- External tool only syntax  

INSERT   
{  
    [BULK]  
    [ database_name . [ schema_name ] . | schema_name . ]  
    [ table_name | view_name ]  
    ( <column_definition> )  
    [ WITH (  
        [ [ , ] CHECK_CONSTRAINTS ]  
        [ [ , ] FIRE_TRIGGERS ]  
        [ [ , ] KEEP_NULLS ]  
        [ [ , ] KILOBYTES_PER_BATCH = kilobytes_per_batch ]  
        [ [ , ] ROWS_PER_BATCH = rows_per_batch ]  
        [ [ , ] ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) ]  
        [ [ , ] TABLOCK ]  
    ) ]  
}  
  
[; ] <column_definition> ::=  
 column_name <data_type>  
    [ COLLATE collation_name ]  
    [ NULL | NOT NULL ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

INSERT INTO [ database_name . [ schema_name ] . | schema_name . ] table_name   
    [ ( column_name [ ,...n ] ) ]  
    {   
      VALUES ( { NULL | expression } )  
      | SELECT <select_criteria>  
    }  
    [ OPTION ( <query_option> [ ,...n ] ) ]  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 CON \<common_table_expression >  
 Specifica il set di risultati denominato temporaneo, noto anche come espressione di tabella comune, definito nell'ambito dell'istruzione INSERT. Il set di risultati deriva da un'istruzione SELECT. Per ulteriori informazioni, vedere [con common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 TOP (*espressione*) [%]  
 Specifica il numero o la percentuale di righe casuali che verranno inserite. Il valore di*expression* può essere specificato come numero o come percentuale di righe. Per ulteriori informazioni, vedere [torna all'inizio &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 INTO  
 Parola chiave facoltativa che può essere specificata tra INSERT e la tabella di destinazione.  
  
 *nome_server*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nome del server collegato in cui si trova la tabella o la vista. *nome_server* può essere specificato come un [server collegato](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) nome, o tramite il [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) (funzione).  
  
 Quando *nome_server* è specificato come un server collegato, *database_name* e *schema_name* sono necessari. Quando *nome_server* viene specificato con OPENDATASOURCE, *database_name* e *schema_name* potrebbe non essere applicabile a tutte le origini dati ed è soggetta alle funzionalità di OLE DB provider che accede all'oggetto remoto.  
  
 *database_name*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nome del database.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella o la vista.  
  
 *view_name table_or*  
 Nome della tabella o della vista in cui si desidera inserire i dati.  
  
 Oggetto [tabella](../../t-sql/data-types/table-transact-sql.md) variabile, nel relativo ambito, può essere utilizzata come origine della tabella in un'istruzione INSERT.  
  
 La vista a cui fa riferimento *table_or_view_name* deve essere aggiornabile e fare riferimento esattamente a una tabella di base nella clausola FROM della vista. Ad esempio, è necessario utilizzare un'istruzione INSERT in una visualizzazione di più tabelle un *column_list* che fa riferimento solo le colonne da una tabella di base. Per ulteriori informazioni sulle viste aggiornabili, vedere [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 È il [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) o [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) (funzione). L'utilizzo di queste funzioni è soggetto alle funzionalità del provider OLE DB che accede all'oggetto remoto.  
  
 CON ( \<table_hint_limited > [... *n* ] )  
 Specifica uno o più hint di tabella consentiti per una tabella di destinazione. La parola chiave WITH e le parentesi sono obbligatorie.  
  
 Le opzioni READPAST, NOLOCK e READUNCOMMITTED non sono consentite. Per ulteriori informazioni sugli hint di tabella, vedere [hint di tabella &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
> [!IMPORTANT]  
>  La funzionalità che consente di specificare gli hint HOLDLOCK, SERIALIZABLE, READCOMMITTED, REPEATABLEREAD o UPDLOCK su tabelle specificate come destinazione di istruzioni INSERT verrà rimossa a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questi hint non influiscono sulle prestazioni delle istruzioni INSERT. Evitarne l'utilizzo in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui sono attualmente implementati.  
  
 La specifica di un hint TABLOCK in una tabella di destinazione di un'istruzione INSERT equivale alla specifica dell'hint TABLOCKX poiché determina l'acquisizione di un blocco esclusivo sulla tabella.  
  
 (*column_list*)  
 Elenco di una o più colonne in cui inserire i dati. *column_list* deve essere racchiuso tra parentesi e delimitato da virgole.  
  
 Se non si trova in una colonna *column_list*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] deve essere in grado di fornire un valore in base alla definizione della colonna; in caso contrario, la riga non può essere caricata. Nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene fornito automaticamente un valore se la colonna soddisfa i requisiti seguenti:  
  
-   Dispone di una proprietà IDENTITY. Viene utilizzato il valore Identity incrementale successivo.  
  
-   Include un valore predefinito. Viene utilizzato il valore predefinito della colonna.  
  
-   È un **timestamp** tipo di dati. Viene utilizzato il valore timestamp corrente.  
  
-   Ammette i valori Null. Viene utilizzato un valore Null.  
  
-   Colonna calcolata. Viene utilizzato il valore calcolato.  
  
*column_list* deve essere utilizzato quando vengono inseriti valori espliciti in una colonna identity e l'opzione SET IDENTITY_INSERT deve essere impostata su ON per la tabella.  
  
Clausola OUTPUT  
 Restituisce le righe inserite come parte dell'operazione di inserimento. I risultati possono essere restituiti all'applicazione di elaborazione o possono essere inseriti in una tabella o in una variabile di tabella per essere elaborati ulteriormente.  
  
 Il [clausola OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) non è supportata in istruzioni DML che fanno riferimento a viste partizionate locali, le viste partizionate distribuite o tabelle remote oppure in istruzioni INSERT che contengono un *execute_statement*. La clausola OUTPUT INTO non è supportata nelle istruzioni INSERT che contengono un \<dml_table_source > clausola. 
  
 VALUES  
 Parola chiave che introduce l'elenco o gli elenchi di valori dei dati da inserire. Deve essere presente un valore di dati per ogni colonna *column_list*, se specificato, o nella tabella. L'elenco di valori deve essere racchiuso tra parentesi.  
  
 Se i valori nell'elenco dei valori non sono nello stesso ordine delle colonne nella tabella o non è un valore per ogni colonna nella tabella, *column_list* deve essere utilizzata per specificare in modo esplicito la colonna che archivia ogni valore in ingresso.  
  
 È possibile utilizzare il costruttore di riga di [!INCLUDE[tsql](../../includes/tsql-md.md)], denominato anche costruttore di valori di tabella, per specificare più righe in una singola istruzione INSERT. Il costruttore di riga è costituito da una singola clausola VALUES con più elenchi di valori racchiusi tra parentesi e separati da una virgola. Per ulteriori informazioni, vedere [il costruttore di valori di tabella &#40; Transact-SQL &#41; ](../../t-sql/queries/table-value-constructor-transact-sql.md).  
  
 DEFAULT  
 Forza il caricamento nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] del valore predefinito di una colonna. Se per la colonna non è disponibile alcun valore predefinito e la colonna ammette valori NULL, viene inserito un valore NULL. Per una colonna definita con il **timestamp** del tipo di dati, viene inserito il valore timestamp successivo. DEFAULT non è un valore valido per una colonna Identity.  
  
 *espressione*  
 Costante, variabile o espressione. L'espressione non può contenere un'istruzione EXECUTE.  
  
 Quando si fa riferimento a tipi di dati carattere Unicode **nchar**, **nvarchar**, e **ntext**, '*espressione*' deve essere preceduto dal lettera maiuscola ' N' '. Se la lettera "N" non è specificata, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la stringa viene convertita in base alla tabella codici corrispondente alle regole di confronto predefinite del database o della colonna. Tutti i caratteri non trovati nella tabella codici vengono persi.  
  
 *argomento derived_table*  
 Qualsiasi istruzione SELECT valida che restituisce righe di dati da caricare nella tabella. L'istruzione SELECT non può contenere un'espressione di tabella comune.  
  
 *execute_statement*  
 Qualsiasi istruzione EXECUTE valida che restituisce dati con le istruzioni SELECT o READTEXT. Per altre informazioni, vedere [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md).  
  
 Le opzioni RESULT SETS dell'istruzione EXECUTE non possono essere specificate in un'istruzione INSERT...EXEC.  
  
 Se *execute_statement* viene utilizzata con INSERT, ogni set di risultati deve essere compatibile con le colonne nella tabella o in *column_list*.  
  
 *execute_statement* può essere utilizzato per eseguire le stored procedure nel server stesso o un server remoto. Viene eseguita la procedura nel server remoto e i set di risultati vengono restituiti al server locale e caricati nella tabella relativa. In una transazione distribuita, *execute_statement* non è possibile emettere in un server collegato loopback quando la connessione dispone di più set di risultati attivi (MARS) abilitato.  
  
 Se *execute_statement* restituisce i dati con l'istruzione READTEXT, ogni istruzione READTEXT può restituire un massimo di 1 MB (1024 KB) dei dati. *execute_statement* può anche essere utilizzato con procedure estese. *execute_statement* inserisce i dati restituiti dal thread principale della procedura estesa; tuttavia, non vengono inseriti output dei thread diverso dal thread principale.  
  
 Un parametro con valori di tabella non può essere specificato come destinazione di un'istruzione INSERT EXEC, ma può essere specificato come origine nella stringa INSERT EXEC o nella stored procedure. Per altre informazioni, vedere [Usare parametri con valori di tabella &#40;Motore di database&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
 \<dml_table_source >  
 Specifica che le righe inserite nella tabella di destinazione sono quelle restituite dalla clausola OUTPUT di un'istruzione INSERT, UPDATE, DELETE o MERGE, facoltativamente filtrate da una clausola WHERE. Se \<dml_table_source > è specificato, la destinazione dell'istruzione INSERT esterna deve soddisfare le restrizioni seguenti: 
  
-   Deve essere una tabella di base e non una vista.  
  
-   Non può essere una tabella remota.  
  
-   Non può includere trigger definiti.  
  
-   Non può partecipare ad alcuna relazione di chiave primaria/chiave esterna.  
  
-   Non può partecipare alla replica di tipo merge né a sottoscrizioni aggiornabili per la replica transazionale.  
  
 Il livello di compatibilità del database deve essere impostato su 100 o più. Per ulteriori informazioni, vedere [clausola OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
 \<select_list >  
 Elenco delimitato da virgole che specifica le colonne restituite dalla clausola OUTPUT da inserire. Le colonne in \<select_list > devono essere compatibili con le colonne in cui vengono inseriti i valori. \<select_list > non può fare riferimento a funzioni di aggregazione né a TEXTPTR. 
  
> [!NOTE]  
>  Qualsiasi variabile elencata nell'elenco di selezione fare riferimento a valori originali, indipendentemente dalle eventuali modifiche apportate a essi in \<dml_statement_with_output_clause >.  
  
 \<dml_statement_with_output_clause >  
 Istruzione INSERT, UPDATE, DELETE o MERGE valida che restituisce le righe interessate in una clausola OUTPUT. L'istruzione non può contenere una clausola WITH e non può avere come destinazione tabelle remote o viste partizionate. Se si specifica UPDATE o DELETE, non può trattarsi di un'istruzione UPDATE o DELETE basata su cursori. Non è possibile fare riferimento alle righe di origine come istruzioni DML nidificate.  
  
 DOVE \<search_condition >  
 È qualsiasi clausola WHERE contenente un valore valido \<search_condition > che filtra le righe restituite da \<dml_statement_with_output_clause >. Per ulteriori informazioni, vedere [condizione di ricerca &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md). Quando utilizzato in questo contesto, \<search_condition > non può contenere sottoquery, funzioni scalari definite dall'utente che eseguono l'accesso ai dati, le funzioni di aggregazione, TEXTPTR o predicati di ricerca full-text. 
  
 DEFAULT VALUES  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Forza l'inserimento nella nuova riga dei valori predefiniti associati a ogni colonna.  
  
 BULK  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Utilizzato dagli strumenti esterni per caricare un flusso di dati binario. Questa opzione non deve essere utilizzato con gli strumenti, ad esempio [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SQLCMD, OSQL o accesso ai dati application programming interface, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 FIRE_TRIGGERS  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che gli eventuali trigger di inserimento definiti nella tabella di destinazione vengano eseguiti durante l'operazione di caricamento del flusso di dati binario. Per altre informazioni, vedere [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
 CHECK_CONSTRAINTS  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che tutti i vincoli sulla tabella o sulla vista di destinazione devono essere controllati durante l'operazione di caricamento del flusso di dati binario. Per altre informazioni, vedere [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
 KEEPNULLS  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica che le colonne vuote devono mantenere un valore null durante l'operazione di caricamento del flusso di dati binario. Per altre informazioni, vedere [Mantenere i valori Null o usare i valori predefiniti durante l'importazione in blocco &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).  
  
 KILOBYTES_PER_BATCH = kilobytes_per_batch  
 Specifica il numero approssimativo di kilobyte (KB) di dati per ogni batch come *kilobytes_per_batch*. Per altre informazioni, vedere [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
 ROWS_PER_BATCH =*rows_per_batch*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indica il numero approssimativo di righe di dati nel flusso di dati binario. Per altre informazioni, vedere [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
>  [!NOTE]
>  Se non viene fornito un elenco di colonne, viene generato un errore di sintassi.  

## <a name="remarks"></a>Osservazioni  
Per informazioni specifiche per l'inserimento di dati in tabelle SQL graph, vedere [INSERT (SQL grafico)](../../t-sql/statements/insert-sql-graph.md). 

## <a name="best-practices"></a>Procedure consigliate  
 Utilizzo di @@ROWCOUNT inserito di funzione per restituire il numero di righe per l'applicazione client. Per ulteriori informazioni, vedere [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md).  
  
### <a name="best-practices-for-bulk-importing-data"></a>Procedure consigliate per l'importazione bulk di dati  
  
#### <a name="using-insert-intoselect-to-bulk-import-data-with-minimal-logging"></a>Utilizzo di INSERT INTO...SELECT per eseguire l'importazione bulk dei dati con registrazione minima  
 È possibile utilizzare `INSERT INTO <target_table> SELECT <columns> FROM <source_table>` per trasferire in modo efficiente un numero elevato di righe da una tabella, ad esempio una tabella di gestione temporanea, in un'altra tabella con registrazione minima. La registrazione minima può migliorare le prestazioni dell'istruzione e ridurre la possibilità che l'operazione riempia lo spazio del log delle transazioni disponibile durante la transazione.  
  
 Per utilizzare la registrazione minima con questa istruzione, sono necessari i requisiti seguenti:  
  
-   Il modello di recupero del database deve essere impostato sul modello con registrazione minima o con registrazione minima delle operazioni bulk.  
  
-   La tabella di destinazione deve essere un heap vuoto o non vuoto.  
  
-   La tabella di destinazione non deve essere utilizzata nella replica.  
  
-   L'hint TABLOCK deve essere specificato per la tabella di destinazione.  
  
Per le righe inserite in un heap come risultato di un'azione di inserimento in un'istruzione MERGE può essere eseguita la registrazione minima.  
  
 A differenza dell'istruzione BULK INSERT, che contiene un blocco di aggiornamento bulk meno restrittivo, l'istruzione INSERT INTO…SELECT con l'hint TABLOCK contiene un blocco esclusivo (X) sulla tabella che non consente di inserire righe utilizzando operazioni di inserimento parallele.  
  
#### <a name="using-openrowset-and-bulk-to-bulk-import-data"></a>Utilizzo di OPENROWSET e BULK per l'importazione bulk dei dati  
 La funzione OPENROWSET può accettare gli hint di tabella seguenti i quali supportano le ottimizzazioni per il caricamento bulk con l'istruzione INSERT:  
  
-   L'hint TABLOCK può ridurre al minimo il numero di record del log per l'operazione di inserimento. Per il database è necessario impostare il modello di recupero con registrazione minima o con registrazione minima delle operazioni bulk. La tabella di destinazione non può inoltre essere utilizzata nella replica. Per ulteriori informazioni, vedere [Prerequisites for Minimal Logging in Bulk Import](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
-   Il controllo dei vincoli FOREIGN KEY e CHECK può essere disabilitato temporaneamente specificando l'hint IGNORE_CONSTRAINTS.  
  
-   L'esecuzione dei trigger può essere disabilitata temporaneamente specificando l'hint IGNORE_TRIGGERS.  
  
-   L'hint KEEPDEFAULTS consente l'inserimento del valore predefinito di una colonna di tabella, se disponibile, al posto del valore NULL quando nel record di dati non è presente un valore per la colonna.  
  
-   L'hint KEEPIDENTITY consente l'utilizzo dei valori Identity presenti nel file di dati importato per la colonna Identity nella tabella di destinazione.  
  
Queste ottimizzazioni sono simili a quelle disponibili con il comando BULK INSERT. Per altre informazioni, vedere [Hint di tabella &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
## <a name="data-types"></a>Tipi di dati  
 Quando si inseriscono righe, considerare il comportamento dei tipi di dati seguenti:  
  
-   Se un valore viene caricato in colonne con un **char**, **varchar**, o **varbinary** tipo di dati, il riempimento o il troncamento degli spazi vuoti finali (spazi per  **Char** e **varchar**, gli zeri per **varbinary**) è determinato dall'impostazione SET ANSI_PADDING definita per la colonna quando la tabella è stata creata. Per altre informazioni, vedere [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
     Nella tabella seguente vengono descritte le operazioni predefinite per SET ANSI_PADDING OFF.  
  
    |Tipo di dati|Operazione predefinita|  
    |---------------|-----------------------|  
    |**char**|Il valore viene riempito con spazi fino alla larghezza di colonna specificata.|  
    |**varchar**|Gli spazi finali vengono rimossi fino all'ultimo carattere diverso dallo spazio o fino al carattere di spazio singolo per le stringhe composte da soli spazi.|  
    |**varbinary**|Gli zero finali vengono rimossi.|  
  
-   Se una stringa vuota (' ') viene caricata in una colonna con un **varchar** o **testo** tipo di dati, l'operazione predefinita consiste nel caricare una stringa di lunghezza zero.  
  
-   Inserisce un valore null in un **testo** o **immagine** colonna non può essere un puntatore di testo valido né di preallocare una pagina di testo da 8 KB.  
  
-   Le colonne create con la **uniqueidentifier** archivio di tipo di dati formattati in modo speciale valori binari a 16 byte. A differenza delle colonne identity, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] non genera automaticamente valori per le colonne con il **uniqueidentifier** tipo di dati. Durante un'operazione di inserimento variabili con dati di un tipo di **uniqueidentifier** e costanti stringa nel formato *xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx* (36 caratteri inclusi i segni meno, in cui *x* è una cifra esadecimale compresa nell'intervallo 0-9 o a-f) può essere utilizzato per **uniqueidentifier** colonne. Ad esempio, 6F9619FF-8B86-D011-B42D-00C04FC964FF è un valore valido per un **uniqueidentifier** variabile o una colonna. Utilizzare il [NEWID ()](../../t-sql/functions/newid-transact-sql.md) funzione per ottenere un ID univoco globale (GUID).  
  
### <a name="inserting-values-into-user-defined-type-columns"></a>Inserimento di valori in colonne di tipo definito dall'utente  
 Per inserire valori in colonne di tipo definito dall'utente è possibile effettuare una delle operazioni indicate di seguito:  
  
-   Specificare un valore del tipo definito dall'utente.  
  
-   Specificando un valore in un tipo di dati di sistema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a condizione che i tipi definiti dall'utente supportino la conversione implicita o esplicita da quel tipo. Nell'esempio seguente viene illustrato come inserire un valore in una colonna di tipo definito dall'utente `Point`, convertendo in modo esplicito da una stringa.  
  
    ```  
    INSERT INTO Cities (Location)  
    VALUES ( CONVERT(Point, '12.3:46.2') );  
    ```  
  
     È inoltre possibile specificare un valore binario senza eseguirne la conversione esplicita, perché tutti i tipi definiti dall'utente possono essere convertiti in modo implicito dal tipo binario.  
  
-   Chiamare una funzione definita dall'utente che restituisce un valore con il tipo definito dall'utente. Nell'esempio seguente viene utilizzata la funzione definita dall'utente `CreateNewPoint()` per creare un nuovo valore con il tipo definito dall'utente `Point` e inserire tale valore nella tabella `Cities`.  
  
    ```  
    INSERT INTO Cities (Location)  
    VALUES ( dbo.CreateNewPoint(x, y) );  
    ```  
  
## <a name="error-handling"></a>Gestione degli errori  
 È possibile implementare la gestione degli errori per l'istruzione INSERT specificando l'istruzione in un costrutto TRY…CATCH.  
  
 Se un'istruzione INSERT viola un vincolo o una regola oppure il valore non è compatibile con il tipo di dati della colonna, l'istruzione ha esito negativo e viene restituito un messaggio di errore.  
  
 Se l'istruzione INSERT carica più righe tramite SELECT o EXECUTE e i valori caricati violano una regola o un vincolo, l'istruzione viene arrestata e non viene caricata alcuna riga.  
  
 Quando un'istruzione INSERT rileva un errore aritmetico (overflow, divisione per zero o errore di dominio) durante la valutazione di un'espressione, l'errore viene gestito dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] come se l'opzione SET ARITHABORT fosse impostata su ON. Il batch viene arrestato e viene restituito un messaggio di errore. Quando un'istruzione INSERT, DELETE o UPDATE rileva un errore aritmetico (un errore di overflow, una divisione per zero o un errore di dominio) durante la valutazione di un'espressione, se SET ARITHABORT e SET ANSI_WARNINGS sono impostate su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inserisce o aggiorna un valore Null. Se la colonna di destinazione non ammette valori Null, l'operazione di inserimento o aggiornamento ha esito negativo e viene generato un errore per l'utente.  
  
## <a name="interoperability"></a>Interoperabilità  
 Se viene definito un trigger INSTEAD OF nelle azioni INSERT eseguite su una tabella o vista, viene eseguito il trigger anziché l'istruzione INSERT. Per ulteriori informazioni sui trigger INSTEAD OF, vedere [CREATE TRIGGER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Quando si inseriscono valori in tabelle remote e non tutti i valori per tutte le colonne vengono specificati, è necessario identificare le colonne in cui devono essere inseriti i valori specificati.  
  
 Quando TOP viene utilizzato con INSERT, le righe a cui viene fatto riferimento non vengono disposte in alcun ordine e non è possibile specificare la clausola ORDER BY direttamente in tali istruzioni. Se è necessario utilizzare TOP per inserire righe in un ordine cronologico significativo, è necessario utilizzare questa clausola insieme a una clausola ORDER BY specificata in un'istruzione sub-SELECT. Vedere la sezione Esempi più avanti in questo argomento.
 
Le query INSERT che utilizzano SELEZIONANO con ORDER BY per popolare le garanzie di righe come vengono calcolati i valori identity, ma non l'ordine in cui vengono inserite le righe.    
  
## <a name="logging-behavior"></a>Comportamento di registrazione  
 L'istruzione INSERT è sempre completamente registrata tranne quando si utilizza la funzione OPENROWSET con la parola chiave BULK o quando si utilizza `INSERT INTO <target_table> SELECT <columns> FROM <source_table>`. Per queste operazioni è possibile eseguire la registrazione minima. Per ulteriori informazioni, vedere la sezione "Procedure consigliate per il caricamento bulk dei dati" più indietro in questo argomento.  
  
## <a name="security"></a>Security  
 Durante una connessione a un server collegato, il server mittente fornisce un nome di account di accesso e una password per connettersi al server ricevente per suo conto. Per far funzionare la connessione, è necessario creare un mapping di account di accesso tra i server collegati utilizzando [sp_addlinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md).  
  
 Quando si utilizza OPENROWSET(BULK…), è essenziale comprendere il modo in cui la rappresentazione viene gestita da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere "Considerazioni sulla sicurezza" in [importazione Bulk dei dati per l'utilizzo di BULK INSERT o OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione INSERT per la tabella di destinazione.  
  
 INSERIMENTO di autorizzazioni per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server, il **db_owner** e **db_datawriter** fissa ruoli del database e il proprietario della tabella. I membri del **sysadmin**, **db_owner**e **db_securityadmin** ruoli e il proprietario della tabella possono trasferire autorizzazioni ad altri utenti.  
  
 Per eseguire INSERT con l'opzione BULK della funzione OPENROWSET, è necessario essere un membro del **sysadmin** ruolo predefinito del server o il **bulkadmin** ruolo predefinito del server.  
  
##  <a name="InsertExamples"></a> Esempi  
  
|Category|Elementi di sintassi inclusi|  
|--------------|------------------------------|  
|[Sintassi di base](#BasicSyntax)|INSERT • costruttore di valori di tabella|  
|[La gestione dei valori di colonna](#ColumnValues)|IDENTITY • NEWID • valori predefiniti • tipi definiti dall'utente|  
|[Inserimento di dati da altre tabelle](#OtherTables)|INSERT…SELECT • INSERT…EXECUTE • espressione di tabella comune WITH • TOP • OFFSET FETCH|  
|[Specifica di oggetti di destinazione diversi dalle tabelle standard](#TargetObjects)|Viste • variabili di tabella|  
|[Inserimento di righe in una tabella remota](#RemoteTables)|Server collegato • funzione per set di righe OPENQUERY • funzione per set di righe OPENDATASOURCE|  
|[Caricamento bulk di dati da tabelle o file di dati](#BulkLoad)|INSERT…SELECT • funzione OPENROWSET|  
|[Override del comportamento predefinito di query optimizer tramite hint](#TableHints)|Hint di tabella|  
|[Acquisizione dei risultati dell'istruzione INSERT](#CaptureResults)|Clausola OUTPUT|  
  
###  <a name="BasicSyntax"></a>Sintassi di base  
 Negli esempi contenuti in questa sezione vengono illustrate le funzionalità di base dell'istruzione INSERT tramite la sintassi minima richiesta.  
  
#### <a name="a-inserting-a-single-row-of-data"></a>A. Inserimento di una sola riga di dati  
 Nell'esempio seguente viene inserita una riga nella tabella `Production.UnitMeasure` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Le colonne nella tabella sono `UnitMeasureCode`, `Name` e `ModifiedDate`. Poiché i valori per tutte le colonne vengono specificati ed elencati nello stesso ordine delle colonne nella tabella, i nomi di colonna non sono necessario specificare nell'elenco delle colonne*.*  
  
```  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT', N'Feet', '20080414');  
```  
  
#### <a name="b-inserting-multiple-rows-of-data"></a>B. Inserimento di più righe di dati  
 L'esempio seguente usa il [il costruttore di valori di tabella](../../t-sql/queries/table-value-constructor-transact-sql.md) per inserire tre righe nella `Production.UnitMeasure` tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database in un'unica istruzione INSERT. Poiché i valori per tutte le colonne vengono specificati ed elencati nello stesso ordine delle colonne nella tabella, non è necessario specificare i nomi delle colonne nell'elenco delle colonne.  
  
```  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT2', N'Square Feet ', '20080923'), (N'Y', N'Yards', '20080923')
    , (N'Y3', N'Cubic Yards', '20080923');  
```  
  
#### <a name="c-inserting-data-that-is-not-in-the-same-order-as-the-table-columns"></a>C. Inserimento di dati in un ordine diverso rispetto alle colonne della tabella  
 Nell'esempio seguente viene utilizzato un elenco di colonne per specificare in modo esplicito i valori inseriti in ogni colonna. L'ordine delle colonne nel `Production.UnitMeasure` tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database `UnitMeasureCode`, `Name`, `ModifiedDate`; tuttavia, le colonne non sono elencate in tale ordine nel *column_list*.  
  
```  
INSERT INTO Production.UnitMeasure (Name, UnitMeasureCode,  
    ModifiedDate)  
VALUES (N'Square Yards', N'Y2', GETDATE());  
```  
  
###  <a name="ColumnValues"></a>La gestione dei valori di colonna  
 Negli esempi contenuti in questa sezione vengono illustrati i metodi di inserimento dei valori nelle colonne che sono definite con una proprietà IDENTITY, il valore predefinito, o sono definite con tipi di dati, ad esempio **uniqueidentifier** o le colonne di tipo definito dall'utente.  
  
#### <a name="d-inserting-data-into-a-table-with-columns-that-have-default-values"></a>D. Inserimento di dati in una tabella con colonne che presentano valori predefiniti  
 Nell'esempio seguente viene illustrato l'inserimento di righe in una tabella con colonne per cui viene generato automaticamente un valore o è specificato un valore predefinito. `Column_1` è una colonna calcolata che genera automaticamente un valore concatenando una stringa con il valore inserito in `column_2`. `Column_2` è definito con un vincolo predefinito. Se per questa colonna non viene specificato alcun valore, viene utilizzato quello predefinito. `Column_3`viene definito con il **rowversion** tipo di dati, che genera automaticamente un numero binario incrementale univoco. `Column_4` non genera automaticamente alcun valore. Quando non viene specificato alcun valore per questa colonna, viene inserito un valore NULL. Le istruzioni INSERT inseriscono righe che contengono valori solo per alcune delle colonne. Nell'ultima istruzione INSERT non viene specificata alcuna colonna e solo i valori predefiniti vengono inseriti tramite la clausola DEFAULT VALUES.  
  
```  
CREATE TABLE dbo.T1   
(  
    column_1 AS 'Computed column ' + column_2,   
    column_2 varchar(30)   
        CONSTRAINT default_name DEFAULT ('my column default'),  
    column_3 rowversion,  
    column_4 varchar(40) NULL  
);  
GO  
INSERT INTO dbo.T1 (column_4)   
    VALUES ('Explicit value');  
INSERT INTO dbo.T1 (column_2, column_4)   
    VALUES ('Explicit value', 'Explicit value');  
INSERT INTO dbo.T1 (column_2)   
    VALUES ('Explicit value');  
INSERT INTO T1 DEFAULT VALUES;   
GO  
SELECT column_1, column_2, column_3, column_4  
FROM dbo.T1;  
GO  
```  
  
#### <a name="e-inserting-data-into-a-table-with-an-identity-column"></a>E. Inserimento di dati in una tabella con una colonna Identity  
 Nell'esempio seguente vengono illustrati diversi metodi per l'inserimento di dati in una colonna Identity. Le prime due istruzioni INSERT consentono di generare valori Identity per le nuove righe. La terza istruzione INSERT ignora la proprietà IDENTITY per la colonna con l'istruzione SET IDENTITY_INSERT e inserisce un valore esplicito nella colonna Identity.  
  
```  
CREATE TABLE dbo.T1 ( column_1 int IDENTITY, column_2 VARCHAR(30));  
GO  
INSERT T1 VALUES ('Row #1');  
INSERT T1 (column_2) VALUES ('Row #2');  
GO  
SET IDENTITY_INSERT T1 ON;  
GO  
INSERT INTO T1 (column_1,column_2)   
    VALUES (-99, 'Explicit identity value');  
GO  
SELECT column_1, column_2  
FROM T1;  
GO  
```  
  
#### <a name="f-inserting-data-into-a-uniqueidentifier-column-by-using-newid"></a>F. Inserimento di dati in una colonna uniqueidentifier tramite NEWID()  
 L'esempio seguente usa il [NEWID](../../t-sql/functions/newid-transact-sql.md)funzione () per ottenere un GUID per `column_2`. A differenza delle colonne identity, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] non genera automaticamente valori per le colonne con il [uniqueidentifier](../../t-sql/data-types/uniqueidentifier-transact-sql.md) il tipo di dati, come illustrato nella seconda `INSERT` istruzione.  
  
```  
CREATE TABLE dbo.T1   
(  
    column_1 int IDENTITY,   
    column_2 uniqueidentifier,  
);  
GO  
INSERT INTO dbo.T1 (column_2)   
    VALUES (NEWID());  
INSERT INTO T1 DEFAULT VALUES;   
GO  
SELECT column_1, column_2  
FROM dbo.T1;  
  
```  
  
#### <a name="g-inserting-data-into-user-defined-type-columns"></a>G. Inserimento di dati in colonne di tipo definito dall'utente  
 Le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti consentono di inserire tre righe nella colonna `PointValue` della tabella `Points`. Questa colonna viene utilizzato un [tipo CLR definito dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) (UDT). Il tipo di dati `Point` è costituito da valori integer X e Y esposti come proprietà del tipo definito dall'utente. È necessario utilizzare la funzione CAST o CONVERT per eseguire il cast dei valori X e Y delimitati da virgole al tipo `Point`. Le prime due istruzioni utilizzano la funzione CONVERT per convertire un valore stringa per il `Point` tipo e la terza istruzione utilizza la funzione CAST. Per ulteriori informazioni, vedere [gestione dei dati di tipo definito dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-manipulating-udt-data.md).  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
###  <a name="OtherTables"></a>Inserimento di dati da altre tabelle  
 Negli esempi contenuti in questa sezione vengono illustrati i metodi per l'inserimento di righe da una tabella in un'altra.  
  
#### <a name="h-using-the-select-and-execute-options-to-insert-data-from-other-tables"></a>H. Utilizzo delle opzioni SELECT ed EXECUTE per inserire dati da altre tabelle  
 Nell'esempio seguente viene illustrato come inserire dati da una tabella in un'altra tramite l'istruzione INSERT…SELECT o INSERT…EXECUTE. Ogni metodo è basato su un'istruzione SELECT su più tabelle, in cui l'elenco di colonne include un'espressione e un valore letterale.  
  
 La prima istruzione INSERT utilizza un'istruzione SELECT per recuperare i dati dalle tabelle di origine (`Employee`, `SalesPerson`, e `Person`) nei [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database e archiviare il set di risultati nel `EmployeeSales` tabella. Nella seconda istruzione INSERT viene utilizzata la clausola EXECUTE per chiamare una stored procedure che contiene l'istruzione SELECT. Nella terza istruzione INSERT viene utilizzata la clausola EXECUTE per fare riferimento all'istruzione SELECT come stringa letterale.  
  
```  
CREATE TABLE dbo.EmployeeSales  
( DataSource   varchar(20) NOT NULL,  
  BusinessEntityID   varchar(11) NOT NULL,  
  LastName     varchar(40) NOT NULL,  
  SalesDollars money NOT NULL  
);  
GO  
CREATE PROCEDURE dbo.uspGetEmployeeSales   
AS   
    SET NOCOUNT ON;  
    SELECT 'PROCEDURE', sp.BusinessEntityID, c.LastName,   
        sp.SalesYTD   
    FROM Sales.SalesPerson AS sp    
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY sp.BusinessEntityID, c.LastName;  
GO  
--INSERT...SELECT example  
INSERT INTO dbo.EmployeeSales  
    SELECT 'SELECT', sp.BusinessEntityID, c.LastName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY sp.BusinessEntityID, c.LastName;  
GO  
--INSERT...EXECUTE procedure example  
INSERT INTO dbo.EmployeeSales   
EXECUTE dbo.uspGetEmployeeSales;  
GO  
--INSERT...EXECUTE('string') example  
INSERT INTO dbo.EmployeeSales   
EXECUTE   
('  
SELECT ''EXEC STRING'', sp.BusinessEntityID, c.LastName,   
    sp.SalesYTD   
    FROM Sales.SalesPerson AS sp   
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE ''2%''  
    ORDER BY sp.BusinessEntityID, c.LastName  
');  
GO  
--Show results.  
SELECT DataSource,BusinessEntityID,LastName,SalesDollars  
FROM dbo.EmployeeSales;  
```  
  
#### <a name="i-using-with-common-table-expression-to-define-the-data-inserted"></a>I. Utilizzo dell'espressione di tabella comune WITH per la definizione dei dati inseriti  
 Nell'esempio seguente viene creata la tabella `NewEmployee` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Le righe di una o più tabelle da inserire nella tabella `EmployeeTemp` vengono definite tramite un'espressione di tabella comune (`NewEmployee`). L'istruzione INSERT fa riferimento alle colonne nell'espressione di tabella comune.  
  
```  
CREATE TABLE HumanResources.NewEmployee  
(  
    EmployeeID int NOT NULL,  
    LastName nvarchar(50) NOT NULL,  
    FirstName nvarchar(50) NOT NULL,  
    PhoneNumber Phone NULL,  
    AddressLine1 nvarchar(60) NOT NULL,  
    City nvarchar(30) NOT NULL,  
    State nchar(3) NOT NULL,   
    PostalCode nvarchar(15) NOT NULL,  
    CurrentFlag Flag  
);  
GO  
WITH EmployeeTemp (EmpID, LastName, FirstName, Phone,   
                   Address, City, StateProvince,   
                   PostalCode, CurrentFlag)  
AS (SELECT   
       e.BusinessEntityID, c.LastName, c.FirstName, pp.PhoneNumber,  
       a.AddressLine1, a.City, sp.StateProvinceCode,   
       a.PostalCode, e.CurrentFlag  
    FROM HumanResources.Employee e  
        INNER JOIN Person.BusinessEntityAddress AS bea  
        ON e.BusinessEntityID = bea.BusinessEntityID  
        INNER JOIN Person.Address AS a  
        ON bea.AddressID = a.AddressID  
        INNER JOIN Person.PersonPhone AS pp  
        ON e.BusinessEntityID = pp.BusinessEntityID  
        INNER JOIN Person.StateProvince AS sp  
        ON a.StateProvinceID = sp.StateProvinceID  
        INNER JOIN Person.Person as c  
        ON e.BusinessEntityID = c.BusinessEntityID  
    )  
INSERT INTO HumanResources.NewEmployee   
    SELECT EmpID, LastName, FirstName, Phone,   
           Address, City, StateProvince, PostalCode, CurrentFlag  
    FROM EmployeeTemp;  
GO  
```  
  
#### <a name="j-using-top-to-limit-the-data-inserted-from-the-source-table"></a>J. Utilizzo della clausola TOP per limitare i dati inseriti dalla tabella di origine  
 Nell'esempio seguente viene creata la tabella `EmployeeSales` e vengono inseriti il nome e i dati di vendita da inizio anno per i primi 5 dipendenti casuali presenti nella tabella `HumanResources.Employee` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. L'istruzione INSERT sceglie 5 righe qualsiasi tra quelle restituite dall'istruzione `SELECT`. La clausola OUTPUT consente di visualizzare le righe inserite nella tabella `EmployeeSales`. Si noti che la clausola ORDER BY nell'istruzione SELECT non viene utilizzata per determinare i primi 5 dipendenti.  
  
```  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   nvarchar(11) NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  YearlySales  money NOT NULL  
 );  
GO  
INSERT TOP(5)INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, 
        inserted.LastName, inserted.YearlySales  
    SELECT sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
```  
  
 Se è necessario utilizzare TOP per inserire righe in un ordine cronologico significativo, è necessario utilizzare questa clausola insieme a ORDER BY in un'istruzione sub-SELECT, come illustrato nell'esempio seguente. La clausola OUTPUT consente di visualizzare le righe inserite nella tabella `EmployeeSales`. Si noti che i primi 5 dipendenti vengono ora inseriti in base ai risultati della clausola ORDER BY anziché alle righe casuali.  
  
```  
INSERT INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, 
        inserted.LastName, inserted.YearlySales  
    SELECT TOP (5) sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
```  
  
###  <a name="TargetObjects"></a>Specifica di oggetti di destinazione diversi dalle tabelle Standard  
 Negli esempi contenuti in questa sezione viene illustrato come inserire righe specificando una vista o una variabile di tabella.  
  
#### <a name="k-inserting-data-by-specifying-a-view"></a>K. Inserimento di dati specificando una vista  
 Nell'esempio seguente viene specificato il nome di una vista come oggetto di destinazione. La nuova riga, tuttavia, viene inserita nella tabella di base sottostante. L'ordine dei valori nell'istruzione `INSERT` deve corrispondere all'ordine delle colonne della vista. Per ulteriori informazioni, vedere [modificare dati tramite una vista](../../relational-databases/views/modify-data-through-a-view.md).  
  
```  
CREATE TABLE T1 ( column_1 int, column_2 varchar(30));  
GO  
CREATE VIEW V1 AS   
SELECT column_2, column_1   
FROM T1;  
GO  
INSERT INTO V1   
    VALUES ('Row 1',1);  
GO  
SELECT column_1, column_2   
FROM T1;  
GO  
SELECT column_1, column_2  
FROM V1;  
GO  
```  
  
#### <a name="l-inserting-data-into-a-table-variable"></a>L. Inserimento di dati in una variabile di tabella  
 Nell'esempio seguente viene specificata una variabile di tabella come oggetto di destinazione nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
-- Create the table variable.  
DECLARE @MyTableVar table(  
    LocationID int NOT NULL,  
    CostRate smallmoney NOT NULL,  
    NewCostRate AS CostRate * 1.5,  
    ModifiedDate datetime);  
  
-- Insert values into the table variable.  
INSERT INTO @MyTableVar (LocationID, CostRate, ModifiedDate)  
    SELECT LocationID, CostRate, GETDATE() 
    FROM Production.Location  
    WHERE CostRate > 0;  
  
-- View the table variable result set.  
SELECT * FROM @MyTableVar;  
GO  
```  
  
###  <a name="RemoteTables"></a>Inserimento di righe in una tabella remota  
 In questa sezione viene illustrato come inserire righe in una tabella di destinazione remota tramite un [server collegato](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) o [funzione rowset](../../t-sql/functions/rowset-functions-transact-sql.md) fare riferimento alla tabella remota.  
  
#### <a name="m-inserting-data-into-a-remote-table-by-using-a-linked-server"></a>M. Inserimento di dati in una tabella remota tramite un server collegato  
 Nell'esempio seguente vengono inserite righe in una tabella remota. L'esempio inizia creando un collegamento all'origine dati remota tramite [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Il nome del server collegato, `MyLinkServer`, viene quindi specificato come parte del nome dell'oggetto in quattro parti nel formato *Object*.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' 
-- or 'server_nameinstance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI',   
    @datasrc = N'server_name',  
    @catalog = N'AdventureWorks2012';  
GO  
```  
  
```  
-- Specify the remote data source in the FROM clause using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
INSERT INTO MyLinkServer.AdventureWorks2012.HumanResources.Department (Name, GroupName)  
VALUES (N'Public Relations', N'Executive General and Administration');  
GO  
```  
  
#### <a name="n-inserting-data-into-a-remote-table-by-using-the-openquery-function"></a>N. Inserimento di dati in una tabella remota tramite una funzione OPENQUERY  
 Nell'esempio seguente viene inserita una riga in una tabella remota specificando la [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) funzione set di righe. Viene utilizzato il nome del server collegato creato nell'esempio precedente.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
INSERT OPENQUERY (MyLinkServer, 
    'SELECT Name, GroupName 
     FROM AdventureWorks2012.HumanResources.Department')  
VALUES ('Environmental Impact', 'Engineering');  
GO  
```  
  
#### <a name="o-inserting-data-into-a-remote-table-by-using-the-opendatasource-function"></a>O. Inserimento di dati in una tabella remota tramite una funzione OPENDATASOURCE  
 Nell'esempio seguente viene inserita una riga in una tabella remota specificando la [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) funzione set di righe. Specificare un nome server valido per l'origine dati utilizzando il formato *nome_server* o *server_name\instance_name*.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
-- Use the OPENDATASOURCE function to specify the remote data source.  
-- Specify a valid server name for Data Source using the format 
-- server_name or server_nameinstance_name.  
  
INSERT INTO OPENDATASOURCE('SQLNCLI',  
    'Data Source= <server_name>; Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Department (Name, GroupName)  
    VALUES (N'Standards and Methods', 'Quality Assurance');  
GO  
```  
  
#### <a name="p-inserting-into-an-external-table-created-using-polybase"></a>P. Inserimento in una tabella esterna creata con PolyBase  
 Esportare dati da SQL Server in Hadoop o Archiviazione di Azure. Prima di tutto creare una tabella esterna che punta al file o alla directory di destinazione. Usare quindi INSERT INTO per esportare i dati da una tabella di SQL Server locale a un'origine dati esterna. L'istruzione INSERT INTO crea il file o la directory di destinazione, se non esiste, e i risultati dell'istruzione SELECT vengono esportati nel percorso specificato nel formato di file specificato.  Per altre informazioni, vedere [Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)(Introduzione a PolyBase).  
  
**Si applica a**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
-- Create an external table.   
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
        [FirstName] char(25) NOT NULL,   
        [LastName] char(25) NOT NULL,   
        [YearlyIncome] float NULL,   
        [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
        LOCATION='/old_data/2009/customerdata.tbl',  
        DATA_SOURCE = HadoopHDP2,  
        FILE_FORMAT = TextFileFormat,  
        REJECT_TYPE = VALUE,  
        REJECT_VALUE = 0  
);  
  
-- Export data: Move old data to Hadoop while keeping 
-- it query-able via external table.  

INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  
  
###  <a name="BulkLoad"></a>Caricamento bulk di dati da tabelle o file di dati  
 Negli esempi di questa sezione vengono illustrati due metodi per eseguire il caricamento bulk dei dati in una tabella tramite l'istruzione INSERT.  
  
#### <a name="q-inserting-data-into-a-heap-with-minimal-logging"></a>Q. Inserimento di dati in un heap con registrazione minima  
 Nell'esempio seguente viene creata una nuova tabella (heap) in cui vengono inseriti dati da un'altra tabella con registrazione minima. L'esempio presuppone che il modello di recupero del database `AdventureWorks2012` sia impostato su FULL. Per assicurare l'utilizzo della registrazione minima, il modello di recupero del database `AdventureWorks2012` viene impostato su BULK_LOGGED prima che le righe vengano inserite e reimpostato su FULL dopo l'istruzione INSERT INTO...SELECT. Inoltre, viene specificato l'hint TABLOCK per la tabella di destinazione `Sales.SalesHistory`. In tal modo, si assicura l'utilizzo da parte dell'istruzione di uno spazio minimo nel log delle transazioni con risultati efficienti.  
  
```  
-- Create the target heap.  
CREATE TABLE Sales.SalesHistory(  
    SalesOrderID int NOT NULL,  
    SalesOrderDetailID int NOT NULL,  
    CarrierTrackingNumber nvarchar(25) NULL,  
    OrderQty smallint NOT NULL,  
    ProductID int NOT NULL,  
    SpecialOfferID int NOT NULL,  
    UnitPrice money NOT NULL,  
    UnitPriceDiscount money NOT NULL,  
    LineTotal money NOT NULL,  
    rowguid uniqueidentifier ROWGUIDCOL  NOT NULL,  
    ModifiedDate datetime NOT NULL );  
GO  
-- Temporarily set the recovery model to BULK_LOGGED.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY BULK_LOGGED;  
GO  
-- Transfer data from Sales.SalesOrderDetail to Sales.SalesHistory  
INSERT INTO Sales.SalesHistory WITH (TABLOCK)  
    (SalesOrderID,   
     SalesOrderDetailID,  
     CarrierTrackingNumber,   
     OrderQty,   
     ProductID,   
     SpecialOfferID,   
     UnitPrice,   
     UnitPriceDiscount,  
     LineTotal,   
     rowguid,   
     ModifiedDate)  
SELECT * FROM Sales.SalesOrderDetail;  
GO  
-- Reset the recovery model.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL;  
GO  
```  
  
#### <a name="r-using-the-openrowset-function-with-bulk-to-bulk-load-data-into-a-table"></a>R. Utilizzo della funzione OPENROWSET con BULK per eseguire il caricamento bulk dei dati in una tabella  
 Nell'esempio seguente vengono inserite righe da un file di dati in una tabella specificando la funzione OPENROWSET. Per l'ottimizzazione delle prestazioni, viene specificato l'hint di tabella IGNORE_TRIGGERS. Per ulteriori esempi, vedere [importazione Bulk dei dati per l'utilizzo di BULK INSERT o OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
INSERT INTO HumanResources.Department WITH (IGNORE_TRIGGERS) (Name, GroupName)  
SELECT b.Name, b.GroupName   
FROM OPENROWSET (  
    BULK 'C:SQLFilesDepartmentData.txt',  
    FORMATFILE = 'C:SQLFilesBulkloadFormatFile.xml',  
    ROWS_PER_BATCH = 15000)AS b ;  
```  
  
###  <a name="TableHints"></a>Override del comportamento predefinito di Query Optimizer tramite hint  
 Negli esempi riportati in questa sezione viene illustrato come utilizzare [hint di tabella](../../t-sql/queries/hints-transact-sql-table.md) per ignorare temporaneamente il comportamento predefinito di query optimizer durante l'elaborazione dell'istruzione INSERT.  
  
> [!CAUTION]  
>  Poiché Query Optimizer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente in genere di selezionare il piano di esecuzione migliore per una query, gli hint devono essere usati solo se strettamente necessari ed esclusivamente da sviluppatori e amministratori di database esperti.  
  
#### <a name="s-using-the-tablock-hint-to-specify-a-locking-method"></a>S. Utilizzo dell'hint TABLOCK per specificare un metodo di blocco  
 Nell'esempio seguente viene impostata l'acquisizione di un blocco esclusivo (X) sulla tabella Production.Location. Tale blocco viene mantenuto attivo fino al termine dell'istruzione INSERT.  
  
**Si applica a**: [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].  
  
```  
INSERT INTO Production.Location WITH (XLOCK)  
(Name, CostRate, Availability)  
VALUES ( N'Final Inventory', 15.00, 80.00);  
```  
  
###  <a name="CaptureResults"></a>Acquisizione dei risultati dell'istruzione INSERT  
 Negli esempi riportati in questa sezione viene illustrato come utilizzare il [clausola OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) per restituire informazioni da o espressioni basate su, ogni riga interessata da un'istruzione INSERT. Questi risultati possono essere restituiti all'applicazione di elaborazione per l'utilizzo nei messaggi di errore, l'archiviazione e altri scopi simili dell'applicazione.  
  
#### <a name="t-using-output-with-an-insert-statement"></a>T. Utilizzo di OUTPUT con un'istruzione INSERT  
 Nell'esempio seguente viene inserita una riga nella tabella `ScrapReason` e viene utilizzata la clausola `OUTPUT` per restituire i risultati dell'istruzione alla variabile di tabella `@MyTableVar`. Poiché la colonna `ScrapReasonID` è definita con una proprietà `IDENTITY`, per tale colonna non viene specificato un valore nell'istruzione `INSERT`. Si noti tuttavia che il valore generato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] per tale colonna viene restituito nella clausola `OUTPUT` nella colonna `INSERTED.ScrapReasonID`.  
  
```  
DECLARE @MyTableVar table( NewScrapReasonID smallint,  
                           Name varchar(50),  
                           ModifiedDate datetime);  
INSERT Production.ScrapReason  
    OUTPUT INSERTED.ScrapReasonID, INSERTED.Name, INSERTED.ModifiedDate  
        INTO @MyTableVar  
VALUES (N'Operator error', GETDATE());  
  
--Display the result set of the table variable.  
SELECT NewScrapReasonID, Name, ModifiedDate FROM @MyTableVar;  
--Display the result set of the table.  
SELECT ScrapReasonID, Name, ModifiedDate   
FROM Production.ScrapReason;  
```  
  
#### <a name="u-using-output-with-identity-and-computed-columns"></a>U. Utilizzo della clausola OUTPUT con colonne Identity e calcolate  
 Nell'esempio seguente viene creata la tabella `EmployeeSales` in cui vengono quindi inserite diverse righe tramite un'istruzione INSERT con un'istruzione SELECT per il recupero dei dati dalle tabelle di origine. La tabella `EmployeeSales` include una colonna Identity (`EmployeeID`) e una colonna calcolata (`ProjectedSales`). Poiché questi valori vengono generati dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante l'operazione di inserimento, nessuna di queste colonne può essere definita in `@MyTableVar`.  
  
```  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   int IDENTITY (1,5)NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  CurrentSales money NOT NULL,  
  ProjectedSales AS CurrentSales * 1.10   
);  
GO  
DECLARE @MyTableVar table(  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  CurrentSales money NOT NULL  
  );  
  
INSERT INTO dbo.EmployeeSales (LastName, FirstName, CurrentSales)  
  OUTPUT INSERTED.LastName,   
         INSERTED.FirstName,   
         INSERTED.CurrentSales  
  INTO @MyTableVar  
    SELECT c.LastName, c.FirstName, sp.SalesYTD  
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY c.LastName, c.FirstName;  
  
SELECT LastName, FirstName, CurrentSales  
FROM @MyTableVar;  
GO  
SELECT EmployeeID, LastName, FirstName, CurrentSales, ProjectedSales  
FROM dbo.EmployeeSales;  
```  
  
#### <a name="v-inserting-data-returned-from-an-output-clause"></a>V. Inserimento dei dati restituiti da una clausola OUTPUT  
 Nell'esempio seguente vengono acquisiti i dati restituiti dalla clausola OUTPUT di un'istruzione MERGE e tali dati vengono inseriti in un'altra tabella. L'istruzione MERGE consente di aggiornare quotidianamente la colonna `Quantity` della tabella `ProductInventory`, in base agli ordini elaborati nella tabella `SalesOrderDetail` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Vengono inoltre eliminate le righe dei prodotti le cui scorte vengono azzerate. In questo esempio vengono acquisite le righe eliminate, che vengono inserite in un'altra tabella, `ZeroInventory`, in cui viene tenuta traccia dei prodotti senza scorte.  
  
```  
--Create ZeroInventory table.  
CREATE TABLE Production.ZeroInventory (DeletedProductID int, RemovedOnDate DateTime);  
GO  
  
INSERT INTO Production.ZeroInventory (DeletedProductID, RemovedOnDate)  
SELECT ProductID, GETDATE()  
FROM  
(   MERGE Production.ProductInventory AS pi  
    USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
           JOIN Sales.SalesOrderHeader AS soh  
           ON sod.SalesOrderID = soh.SalesOrderID  
           AND soh.OrderDate = '20070401'  
           GROUP BY ProductID) AS src (ProductID, OrderQty)  
    ON (pi.ProductID = src.ProductID)  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0  
        THEN DELETE  
    WHEN MATCHED  
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    OUTPUT $action, deleted.ProductID) AS Changes (Action, ProductID)  
WHERE Action = 'DELETE';  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were inserted';  
GO  
SELECT DeletedProductID, RemovedOnDate FROM Production.ZeroInventory;  
```  

#### <a name="w-inserting-data-using-the-select-option"></a>W. Inserimento di dati tramite l'opzione SELECT  
 Nell'esempio seguente viene illustrato come inserire più righe di dati tramite un'istruzione INSERT con un'opzione di seleziona. Il primo `INSERT` istruzione utilizza un `SELECT` istruzione direttamente per recuperare dati dalla tabella di origine, quindi per archiviare il risultato impostare nella `EmployeeTitles` tabella.  
  
```  
CREATE TABLE EmployeeTitles  
( EmployeeKey   INT NOT NULL,  
  LastName     varchar(40) NOT NULL,  
  Title      varchar(50) NOT NULL  
);  
INSERT INTO EmployeeTitles  
    SELECT EmployeeKey, LastName, Title   
    FROM ssawPDW.dbo.DimEmployee  
    WHERE EndDate IS NULL;  
```  
  
#### <a name="x-specifying-a-label-with-the-insert-statement"></a>X. Specificare un'etichetta con l'istruzione INSERT  
 Nell'esempio seguente viene illustrato l'utilizzo di un'etichetta con un'istruzione INSERT.  
  
```  
-- Uses AdventureWorks  
  
INSERT INTO DimCurrency   
VALUES (500, N'C1', N'Currency1')  
OPTION ( LABEL = N'label1' );  
```  
  
#### <a name="y-using-a-label-and-a-query-hint-with-the-insert-statement"></a>Y. Utilizzo di un'etichetta e un hint per la query con l'istruzione INSERT  
 Questa query Mostra la sintassi di base per l'utilizzo di un'etichetta e un hint di join della query con l'istruzione INSERT. Dopo che la query viene inviata al nodo di controllo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in esecuzione nei nodi di calcolo, verrà applicata la strategia di join hash quando genera il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] piano di query. Per ulteriori informazioni sull'hint di join e come utilizzare la clausola OPTION, vedere [opzione (SQL Server PDW)](http://msdn.microsoft.com/en-us/72bbce98-305b-42fa-a19f-d89620621ecc).  
  
```  
-- Uses AdventureWorks  
  
INSERT INTO DimCustomer (CustomerKey, CustomerAlternateKey, 
    FirstName, MiddleName, LastName )   
SELECT ProspectiveBuyerKey, ProspectAlternateKey, 
    FirstName, MiddleName, LastName  
FROM ProspectiveBuyer p JOIN DimGeography g ON p.PostalCode = g.PostalCode  
WHERE g.CountryRegionCode = 'FR'  
OPTION ( LABEL = 'Add French Prospects', HASH JOIN);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [IDENTITY &#40;proprietà&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [UNIONE &#40; Transact-SQL &#41;](../../t-sql/statements/merge-transact-sql.md)   
 [Clausola OUTPUT &#40; Transact-SQL &#41;](../../t-sql/queries/output-clause-transact-sql.md)   
 [Usare le tabelle inserite ed eliminate](../../relational-databases/triggers/use-the-inserted-and-deleted-tables.md)  
  
  




