---
title: sp_describe_undeclared_parameters (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_describe_undeclared_parameters
- sp_describe_undeclared_parameters_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_describe_undeclared_parameters
ms.assetid: 6f016da6-dfee-4228-8b0d-7cd8e7d5a354
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9168e7a06ce377c6c1d47456197f8e513b2b58fb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdescribeundeclaredparameters-transact-sql"></a>sp_describe_undeclared_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un set di risultati che contiene metadati sui parametri non dichiarati in un [!INCLUDE[tsql](../../includes/tsql-md.md)] batch. Considera ogni parametro che viene utilizzata la  **@tsql**  batch, ma non dichiarato in  **@params** . Viene restituito un set di risultati che contiene una riga per ognuno di questi parametri, con le informazioni sul tipo dedotte per quel parametro. La procedura restituisce un risultato vuoto se il  **@tsql**  batch di input non ha alcun parametro, ad eccezione di quelli dichiarati in  **@params** .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] alla [versione corrente](http://msdn.microsoft.com/library/bb500435.aspx)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_describe_undeclared_parameters   
    [ @tsql = ] 'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' data type ] [, ...n]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@tsql =** ] **'***SQL_batch transact***'**  
 Una o più istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. *SQL_batch Transact* potrebbe essere **nvarchar (***n***)** o **nvarchar (max)**.  
  
 [  **@params =** ] **N'***parametri***'**  
 @paramsfornisce una stringa di dichiarazione per i parametri per il [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, in modo simile a sp_executesql modo funziona. *I parametri* potrebbe essere **nvarchar (***n***)** o **nvarchar (max)**.  
  
 Stringa che contiene le definizioni di tutti i parametri che sono stati incorporati in *Transact SQL_batch*. La stringa deve essere una costante o una variabile Unicode. Ogni definizione di parametro è costituita da un nome del parametro e da un tipo di dati. n è un segnaposto che indica definizioni di parametro aggiuntive. Se l'istruzione Transact-SQL o il batch nell'istruzione non contiene parametri, @params non è obbligatorio. Il valore predefinito per questo parametro è NULL.  
  
 Datatype  
 Tipo di dati del parametro.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **sp_describe_undeclared_parameters** restituisce restituiscono sempre lo stato pari a zero in caso di esito positivo. Se la procedura genera un errore e la routine viene chiamata come RPC, lo stato restituito viene popolato dal tipo di errore, come descritto nella colonna error_type di Sys.dm exec_describe_first_result_set. Se la procedura viene chiamata da [!INCLUDE[tsql](../../includes/tsql-md.md)], il valore restituito è sempre zero, anche in caso di errore.  
  
## <a name="result-sets"></a>Set di risultati  
 **sp_describe_undeclared_parameters** restituisce il set di risultati seguente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int non NULL.**|Contiene la posizione ordinale del parametro nel set di risultati. La posizione del primo parametro viene specificata come 1.|  
|**name**|**sysname non NULL.**|Contiene il nome del parametro.|  
|**suggested_system_type_id**|**int non NULL.**|Contiene il **system_type_id** del tipo di dati del parametro, come specificato in sys. Types.<br /><br /> Per i tipi CLR, anche se il **system_type_name** colonna restituisce NULL, questa colonna restituisce il valore 240.|  
|**suggested_system_type_name**|**nvarchar (256) NULL**|Contiene il nome del tipo di dati. Include gli argomenti, quali lunghezza, precisione e scala, specificati per il tipo di dati del parametro. Se il tipo di dati è un tipo di alias definito dall'utente, il tipo di sistema sottostante viene specificato qui. Se il tipo di dati è un tipo CLR definito dall'utente, in questa colonna viene restituito NULL. Se non è possibile dedurre il tipo del parametro, viene restituito NULL.|  
|**suggested_max_length**|**smallint non NULL.**|Vedere sys. Columns. per **max_length** descrizione della colonna.|  
|**suggested_precision**|**tinyint non NULL.**|Vedere sys. Columns. per la descrizione della colonna PRECISION.|  
|**suggested_scale**|**tinyint non NULL.**|Vedere sys. Columns. per la descrizione della colonna SCALE.|  
|**suggested_user_type_id**|**int NULL**|Per i tipi di alias e CLR, contiene il valore user_type_id del tipo di dati della colonna come specificato in sys.types. In caso contrario, è NULL.|  
|**suggested_user_type_database**|**sysname NULL**|Per i tipi di alias e CLR, contiene il nome del database in cui è definito il tipo. In caso contrario, è NULL.|  
|**suggested_user_type_schema**|**sysname NULL**|Per i tipi di alias e CLR, contiene il nome dello schema in cui è definito il tipo. In caso contrario, è NULL.|  
|**suggested_user_type_name**|**sysname NULL**|Per i tipi di alias e CLR, contiene il nome del tipo. In caso contrario, è NULL.|  
|**suggested_assembly_qualified_type_name**|**nvarchar (4000) NULL**|Per i tipi CLR, restituisce il nome dell'assembly e la classe che definisce il tipo. In caso contrario, è NULL.|  
|**suggested_xml_collection_id**|**int NULL**|Contiene il valore xml_collection_id del tipo di dati del parametro, come specificato in sys. Columns. Questa colonna restituisce NULL se il tipo restituito non è associato a una raccolta XML Schema.|  
|**suggested_xml_collection_database**|**sysname NULL**|Contiene il database in cui viene definita la raccolta XML Schema associata a questo tipo. Questa colonna restituisce NULL se il tipo restituito non è associato a una raccolta XML Schema.|  
|**suggested_xml_collection_schema**|**sysname NULL**|Contiene lo schema in cui viene definita la raccolta XML Schema associata a questo tipo. Questa colonna restituisce NULL se il tipo restituito non è associato a una raccolta XML Schema.|  
|**suggested_xml_collection_name**|**sysname NULL**|Contiene il nome della raccolta XML Schema associata a questo tipo. Questa colonna restituisce NULL se il tipo restituito non è associato a una raccolta XML Schema.|  
|**suggested_is_xml_document**|**bit non NULL.**|Restituisce 1 se il tipo restituito è XML ed è garantito che il tipo sia un documento XML. In caso contrario, restituisce 0.|  
|**suggested_is_case_sensitive**|**bit non NULL.**|Restituisce 1 se la colonna è di un tipo string che fa distinzione tra maiuscole e minuscole e 0 in caso contrario.|  
|**suggested_is_fixed_length_clr_type**|**bit non NULL.**|Restituisce 1 se la colonna è di un tipo CLR a lunghezza fissa e 0 in caso contrario.|  
|**suggested_is_input**|**bit non NULL.**|Restituisce 1 se il parametro viene utilizzato in qualsiasi posizione, a eccezione del lato sinistro di un'assegnazione. In caso contrario, restituisce 0.|  
|**suggested_is_output**|**bit non NULL.**|Restituisce 1 se il parametro viene utilizzato sul lato sinistro di un'assegnazione o se viene passato a un parametro di output di una stored procedure. In caso contrario, restituisce 0.|  
|**formal_parameter_name**|**sysname NULL**|Se il parametro è un argomento per una stored procedure o una funzione definita dall'utente, restituisce il nome del parametro formale corrispondente. In caso contrario, viene restituito NULL.|  
|**suggested_tds_type_id**|**int non NULL.**|Per uso interno.|  
|**suggested_tds_length**|**int non NULL.**|Per uso interno.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_describe_undeclared_parameters** restituisce restituiscono sempre lo stato pari a zero.  
  
 Lo scenario più comune si verifica quando a un'applicazione viene fornita un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] che potrebbe contenere parametri e li deve elaborare in qualche modo. Un esempio è un'interfaccia utente (quale ODBCTest o RowsetViewer) in cui l'utente fornisce una query con sintassi del parametro ODBC. L'applicazione deve individuare in modo dinamico il numero di parametri che verranno richiesti singolarmente all'utente.  
  
 Un altro esempio è dato dalla situazione in cui, senza l'input dell'utente, un'applicazione deve eseguire in ciclo i parametri e ottenere i relativi dati da altri percorsi, ad esempio una tabella. In questo caso non è necessario passare immediatamente tutte le informazioni sui parametri, ma è possibile ottenerle dal provider e acquisire i dati dalla tabella. Codice che usa **sp_describe_undeclared_parameters** è più generico ed è meno probabile che richiedono la modifica se la struttura dei dati in un secondo momento.  
  
 **sp_describe_undeclared_parameters** restituisce un errore nei casi seguenti.  
  
-   Se l'input @tsql non è un valido [!INCLUDE[tsql](../../includes/tsql-md.md)] batch. Validità è determinata tramite l'analisi di [!INCLUDE[tsql](../../includes/tsql-md.md)] batch. Eventuali errori generati dal batch durante l'ottimizzazione della query o durante l'esecuzione non vengono considerati per determinare se il [!INCLUDE[tsql](../../includes/tsql-md.md)] batch è valido.  
  
-   Se @params non è NULL e contiene una stringa che non è una stringa di dichiarazione sintatticamente valida per i parametri o se contiene una stringa che dichiara qualsiasi parametro più di una volta.  
  
-   Se l'input [!INCLUDE[tsql](../../includes/tsql-md.md)] batch dichiara una variabile locale con lo stesso nome dichiarato un parametro @params.  
  
-   L'istruzione crea qualsiasi tabella temporanea.  
  
 Se @tsql non ha alcun parametro, a eccezione di quelli dichiarati @params, la procedura restituisce un set di risultati vuoto.  
  
## <a name="parameter-selection-algorithm"></a>Algoritmo di selezione dei parametri  
 Per una query con parametri non dichiarati, la deduzione del tipo di dati per i parametri non dichiarati si svolge in tre passaggi.  
  
 **Passaggio 1**  
  
 Il primo passaggio della deduzione del tipo di dati per una query con parametri non dichiarati consiste nel trovare i tipi di dati di tutte le sottoespressioni i cui tipi di dati non dipendono dai parametri non dichiarati. È possibile determinare il tipo per le espressioni seguenti:  
  
-   Colonne, costanti, variabili e parametri dichiarati.  
  
-   Risultati di una chiamata a una funzione definita dall'utente.  
  
-   Espressione con tipi di dati che non dipendono dai parametri non dichiarati per tutti gli input.  
  
 Si consideri, ad esempio, la query `SELECT dbo.tbl(@p1) + c1 FROM t1 WHERE c2 = @p2 + 2`. Le espressioni dbo.tbl (@p1) + c1 e c2 hanno tipi di dati e di espressione @p1 e @p2 + 2 non.  
  
 Dopo questo passaggio, se un'espressione, che non sia una chiamata a una funzione definita dall'utente, dispone di due argomenti senza tipi di dati, si verifica un errore durante la deduzione dei tipi. In tutti gli esempi seguenti si verificano errori:  
  
```  
SELECT * FROM t1 WHERE @p1 = @p2  
SELECT * FROM t1 WHERE c1 = @p1 + @p2  
SELECT * FROM t1 WHERE @p1 = SUBSTRING(@p2, 2, 3)  
```  
  
 Nell'esempio seguente non viene generato alcun errore:  
  
```  
SELECT * FROM t1 WHERE @p1 = dbo.tbl(c1, @p2, @p3)  
```  
  
 **Passaggio 2**  
  
 Per un determinato parametro non dichiarato @p, l'algoritmo di deduzione del tipo Cerca l'espressione più interna E (@p) che contiene @p ed è uno dei seguenti:  
  
-   Argomento per un operatore di confronto o assegnazione.  
  
-   Argomento per una funzione definita dall'utente, incluse funzioni definite dall'utente con valori di tabella, procedura o metodo.  
  
-   Un argomento a un **valori** clausola di un **inserire** istruzione.  
  
-   Un argomento a un **CAST** o **CONVERTIRE**.  
  
 L'algoritmo di deduzione del tipo consente di trovare un tipo di dati di destinazione TT (@p) per E (@p). I tipi di dati di destinazione per gli esempi precedenti sono i seguenti:  
  
-   Tipo di dati dell'altro lato dell'operatore di confronto o assegnazione.  
  
-   Tipo di dati dichiarato del parametro a cui viene passato questo argomento.  
  
-   Tipo di dati della colonna in cui viene inserito questo valore.  
  
-   Tipo di dati nel quale l'istruzione esegue il cast o la conversione.  
  
 Si consideri, ad esempio, la query `SELECT * FROM t WHERE @p1 = dbo.tbl(@p2 + c1)`. E quindi (@p1) = @p1, E (@p2) = @p2 + c1, TT (@p1) è il tipo di dati restituito dichiarato di dbo.tbl e TT (@p2) è il tipo di dati del parametro dichiarato per dbo.tbl.  
  
 Se @p non è contenuta in alcuna espressione elencata all'inizio del passaggio 2, l'algoritmo di deduzione del tipo determina che E (@p) è il più grande espressione scalare che contiene @p, e non l'algoritmo di deduzione del tipo calcolo di un tipo di dati di destinazione TT (@p) per E (@p). Ad esempio, se la query è SELECT `@p + 2` E quindi (@p) = @p + 2, ed è presente alcun TT (@p).  
  
 **Passaggio 3**  
  
 Ora che E (@p) e TT (@p) vengono identificati, l'algoritmo di deduzione dei tipi deduce un tipo di dati per @p in uno dei due modi seguenti:  
  
-   Deduzione semplice  
  
     Se E (@p) = @p e TT (@p) esiste, ad esempio, se @p è direttamente un argomento a una delle espressioni elencate all'inizio del passaggio 2, l'algoritmo di deduzione dei tipi deduce il tipo di dati di @p da TT (@p). Esempio:  
  
    ```  
    SELECT * FROM t WHERE c1 = @p1 AND @p2 = dbo.tbl(@p3)  
    ```  
  
     Il tipo di dati per @p1, @p2, e @p3 sarà il tipo di dati di c1, il tipo di dati restituito di dbo.tbl e il tipo di dati di parametro per dbo.tbl rispettivamente.  
  
     Un caso speciale, se @p è un argomento a un \<, >, \<= o > = (operatore), la deduzione semplice non si applicano le regole. L'algoritmo di deduzione dei tipi utilizzerà le regole della deduzione generale illustrate nella sezione successiva. Se ad esempio c1 è una colonna del tipo di dati char(30), si considerino le due query seguenti:  
  
    ```  
    SELECT * FROM t WHERE c1 = @p  
    SELECT * FROM t WHERE c1 > @p  
    ```  
  
     Nel primo caso, l'algoritmo di deduzione dei tipi deduce **char (30)** come tipo di dati per @p in base alle regole di precedenza in questo argomento. Nel secondo caso, l'algoritmo di deduzione dei tipi deduce **varchar(8000)** secondo le regole della deduzione generale nella sezione successiva.  
  
-   Deduzione generale  
  
     Se la deduzione semplice non è applicabile, si considerino i tipi di dati seguenti per i parametri non dichiarati:  
  
    -   Tipi di dati integer (**bit**, **tinyint**, **smallint**, **int**, **bigint**)  
  
    -   Tipi di dati Money (**smallmoney**, **money**)  
  
    -   Tipi di dati a virgola mobile (**float**, **reale**)  
  
    -   **Numeric (38, 19)** -non vengono considerati altri tipi di dati numerici o decimali.  
  
    -   **varchar(8000)**, **varchar (max)**, **nvarchar (4000)**, e **nvarchar (max)** - altri tipi di dati string (ad esempio **testo**, **char (8000)**, **nvarchar (30)**e così via) non sono considerati.  
  
    -   **varbinary (8000)** e **varbinary (max)** -non vengono considerati altri tipi di dati binari (ad esempio **immagine**, **binary(8000)**,  **varbinary(30)**, ecc.).  
  
    -   **Data**, **Time (7)**, **smalldatetime**, **datetime**, **datetime2 (7)**, **datetimeoffset(7)**  - Altro data e ora e tipi, ad esempio **time(4)**, non sono considerati.  
  
    -   **sql_variant**  
  
    -   **xml**  
  
    -   I tipi CLR definiti dal sistema (**hierarchyid**, **geometry**, **geography**)  
  
    -   Tipi CLR definiti dall'utente  
  
### <a name="selection-criteria"></a>Criteri di selezione  
 Di tutti i tipi di dati candidati, qualsiasi tipo di dati che renderebbe non valida la query viene rifiutato. Dei tipi di dati candidati rimanenti, l'algoritmo di deduzione dei tipi ne seleziona uno in base alle regole seguenti.  
  
1.  Il tipo di dati che produce il numero più piccolo di conversioni implicite in E (@p) sia selezionata. Se un particolare tipo di dati produce un tipo di dati per E (@p) che è diverso da TT (@p), l'algoritmo di deduzione del tipo considera come una conversione implicita aggiuntiva dal tipo di dati di E (@p) a TT (@p).  
  
     Esempio:  
  
    ```  
    SELECT * FROM t WHERE Col_Int = Col_Int + @p  
    ```  
  
     In questo caso, E (@p) è Col_Int + @p e TT (@p) è **int**. **int** scelto per @p perché non produce conversioni implicite. Qualsiasi altra scelta del tipo di dati produce almeno una conversione implicita.  
  
2.  Se più tipi di dati hanno un valore equivalente per il numero più piccolo di conversioni, viene utilizzato il tipo di dati con la precedenza maggiore. Ad esempio:  
  
    ```  
    SELECT * FROM t WHERE Col_Int = Col_smallint + @p  
    ```  
  
     In questo caso, **int** e **smallint** producono una conversione. Ogni altro tipo di dati produce più di una conversione. Poiché **int** ha la precedenza su **smallint**, **int** viene utilizzato per @p. Per ulteriori informazioni sulla precedenza tipo di dati, vedere [precedenza tipo di dati &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
     Questa regola è applicabile solo in presenza di una conversione implicita tra ogni tipo di dati con valori equivalenti in base alla regola 1 e il tipo di dati con la precedenza maggiore. In assenza di una conversione implicita, la deduzione dei tipi di dati genera un errore. Ad esempio nella query `SELECT @p FROM t`, ha esito negativo di deduzione del tipo di dati poiché qualsiasi tipo di dati per @p sarebbe ugualmente appropriato. Ad esempio, non vi è alcuna conversione implicita da **int** a **xml**.  
  
3.  Se due tipi di dati simili collegare in base alla regola 1, ad esempio **varchar(8000)** e **varchar (max)**, minore sarà il tipo di dati (**varchar(8000)**) viene scelto. Lo stesso principio si applica a **nvarchar** e **varbinary** tipi di dati.  
  
4.  Ai fini della regola 1, l'algoritmo di deduzione dei tipi preferisce alcune conversioni ad altre. Le conversioni dalla migliore alla peggiore sono:  
  
    1.  Conversione tra lo stesso tipo di dati di base di lunghezza diversa.  
  
    2.  Conversione tra versione stessi tipi di dati a lunghezza fissa e a lunghezza variabile (ad esempio, **char** a **varchar**).  
  
    3.  Conversione tra **NULL** e **int**.  
  
    4.  Qualsiasi altra conversione.  
  
 Ad esempio, per la query `SELECT * FROM t WHERE [Col_varchar(30)] > @p`, **varchar(8000)** è selezionata perché è consigliabile conversione (a). Per la query `SELECT * FROM t WHERE [Col_char(30)] > @p`, **varchar(8000)** viene ancora scelto perché causa una conversione del tipo (b) e perché un'altra scelta (ad esempio **varchar(4000)**) causerebbe una conversione del tipo (d).  
  
 Come esempio finale, data una query `SELECT NULL + @p`, **int** scelto per @p perché comporta una conversione del tipo (c).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione per eseguire il @tsql argomento.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni quali il tipo di dati previsto per i parametri `@id` e `@name` non dichiarati.  
  
```  
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR name = @name'  
  
```  
  
 Quando il parametro `@id` viene specificato come un riferimento `@params`, il parametro `@id` viene omesso dal set di risultati e solo il parametro `@name` viene descritto.  
  
```  
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR NAME = @name',  
@params = N'@id int'  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_describe_first_result_set &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [Sys.dm exec_describe_first_result_set &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [Sys.dm exec_describe_first_result_set_for_object &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)  
  
  
