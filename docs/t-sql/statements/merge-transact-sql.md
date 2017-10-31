---
title: MERGE (Transact-SQL) | Documenti Microsoft
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
- MERGE
- MERGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating data [SQL Server]
- modifying data [SQL Server], MERGE statement
- MERGE statement [SQL Server]
- adding data
- DML [SQL Server], MERGE statement
- table modifications [SQL Server], MERGE statement
- data manipulation language [SQL Server], MERGE statement
- inserting data
ms.assetid: c17996d6-56a6-482f-80d8-086a3423eecc
caps.latest.revision: 76
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d071a0137d39abb638131df391c72eae75292c08
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="merge-transact-sql"></a>MERGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esegue operazioni di inserimento, aggiornamento o eliminazione in una tabella di destinazione in base ai risultati di un join con una tabella di origine. È possibile ad esempio sincronizzare due tabelle inserendo, aggiornando o eliminando righe in una tabella in base alle differenze trovate nell'altra tabella.  
  
 **Suggerimento per le prestazioni:** il comportamento condizionale descritto per l'istruzione MERGE funziona meglio quando le due tabelle hanno una combinazione complessa di caratteristiche corrispondenti. Ad esempio, inserire una riga se non esiste o aggiornare la riga se corrisponde. Quando si aggiorna semplicemente una tabella in base alle righe di un'altra tabella, è possibile ottenere prestazioni e scalabilità migliori se si usano le istruzioni INSERT, UPDATE e DELETE di base. Esempio:  
  
```  
INSERT tbl_A (col, col2)  
SELECT col, col2   
FROM tbl_B   
WHERE NOT EXISTS (SELECT col FROM tbl_A A2 WHERE A2.col = tbl_B.col);  
```  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ WITH <common_table_expression> [,...n] ]  
MERGE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ INTO ] <target_table> [ WITH ( <merge_hint> ) ] [ [ AS ] table_alias ]  
    USING <table_source>   
    ON <merge_search_condition>  
    [ WHEN MATCHED [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ WHEN NOT MATCHED [ BY TARGET ] [ AND <clause_search_condition> ]  
        THEN <merge_not_matched> ]  
    [ WHEN NOT MATCHED BY SOURCE [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ <output_clause> ]  
    [ OPTION ( <query_hint> [ ,...n ] ) ]      
;  
  
<target_table> ::=  
{   
    [ database_name . schema_name . | schema_name . ]  
  target_table  
}  
  
<merge_hint>::=  
{  
    { [ <table_hint_limited> [ ,...n ] ]  
    [ [ , ] INDEX ( index_val [ ,...n ] ) ] }  
}  
  
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ] [ <tablesample_clause> ]   
        [ WITH ( table_hint [ [ , ]...n ] ) ]   
  | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
  | user_defined_function [ [ AS ] table_alias ]  
  | OPENXML <openxml_clause>   
  | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]   
  | <joined_table>   
  | <pivoted_table>   
  | <unpivoted_table>   
}  
  
<merge_search_condition> ::=  
    <search_condition>  
  
<merge_matched>::=  
    { UPDATE SET <set_clause> | DELETE }  
  
<set_clause>::=  
SET  
  { column_name = { expression | DEFAULT | NULL }  
  | { udt_column_name.{ { property_name = expression  
                        | field_name = expression }  
                        | method_name ( argument [ ,...n ] ) }  
    }  
  | column_name { .WRITE ( expression , @Offset , @Length ) }  
  | @variable = expression  
  | @variable = column = expression  
  | column_name { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable = column { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  } [ ,...n ]   
  
<merge_not_matched>::=  
{  
    INSERT [ ( column_list ) ]   
        { VALUES ( values_list )  
        | DEFAULT VALUES }  
}  
  
<clause_search_condition> ::=  
    <search_condition>  
  
<search condition> ::=  
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '< contains_search_condition >' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery ) }   
  
<output_clause>::=  
{  
    [ OUTPUT <dml_select_list> INTO { @table_variable | output_table }  
        [ (column_list) ] ]  
    [ OUTPUT <dml_select_list> ]  
}  
  
<dml_select_list>::=  
    { <column_name> | scalar_expression }   
        [ [AS] column_alias_identifier ] [ ,...n ]  
  
<column_name> ::=  
    { DELETED | INSERTED | from_table_name } . { * | column_name }  
    | $action  
```  
  
## <a name="arguments"></a>Argomenti  
 CON \<common_table_expression >  
 Specifica la vista o il set di risultati denominato temporaneo, noto anche come espressione di tabella comune, definito nell'ambito di un'istruzione MERGE. Il set di risultati deriva da una query semplice e l'istruzione MERGE vi fa riferimento. Per ulteriori informazioni, vedere [con common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 TOP ( *espressione* ) [%]  
 Specifica il numero o la percentuale di righe interessate. *espressione* può essere un numero o una percentuale di righe. Le righe cui viene fatto riferimento nell'espressione TOP non vengono disposte in alcun ordine. Per ulteriori informazioni, vedere [torna all'inizio &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 La clausola TOP viene applicata dopo l'unione in join dell'intera tabella di origine con l'intera tabella di destinazione e dopo la rimozione delle righe unite in join non qualificate per un'azione di inserimento, aggiornamento o eliminazione. La clausola TOP riduce ulteriormente il numero di righe unite in join in base al valore specificato e l'azione di inserimento, aggiornamento o eliminazione viene applicata alle righe unite in join rimanenti in modo non ordinato. Ciò significa che le righe vengono distribuite tra le azioni definite nelle clausole WHEN senza alcun ordine. La specifica della clausola TOP (10), ad esempio, influisce su 10 righe, 7 delle quali possono essere aggiornate e 3 inserite oppure 1 riga può essere eliminata, 5 aggiornate e 4 inserite e così via.  
  
 Poiché l'istruzione MERGE esegue un'analisi completa di entrambe le tabelle di origine e di destinazione, l'utilizzo della clausola TOP per modificare una tabella di grandi dimensioni creando più batch può influire sulle prestazioni di I/O. In questo scenario è importante assicurare che tutti i batch successivi vengano destinati a nuove righe.  
  
 *database_name*  
 È il nome del database in cui *target_table* si trova.  
  
 *schema_name*  
 È il nome dello schema a cui *target_table* appartiene.  
  
 *target_table*  
 Tabella o vista in cui le righe di dati da \<table_source > vengono confrontati in base alle \<clause_search_condition >. *target_table* è la destinazione di istruzioni insert, update o le operazioni di eliminazione specificate dalle clausole WHEN dell'istruzione MERGE.  
  
 Se *target_table* è una vista, qualsiasi azione eseguita su tale devono soddisfare le condizioni per l'aggiornamento delle viste. Per ulteriori informazioni, vedere [modificare dati tramite una vista](../../relational-databases/views/modify-data-through-a-view.md).  
  
 *target_table* non può essere una tabella remota. *target_table* non può includere regole in cui è definite.  
  
 [COME] *table_alias*  
 Nome alternativo utilizzato per fare riferimento a una tabella.  
  
 UTILIZZANDO \<table_source >  
 Specifica l'origine dati che corrisponde alle righe di dati in *target_table* in base a \<merge_search condition >. Il risultato di questa corrispondenza determina le azioni che le clausole WHEN dell'istruzione MERGE devono eseguire. \<table_source > può essere una tabella remota o una tabella derivata che accede a tabelle remote. 
  
 \<table_source > può essere una tabella derivata che utilizza il [!INCLUDE[tsql](../../includes/tsql-md.md)] [il costruttore di valori di tabella](../../t-sql/queries/table-value-constructor-transact-sql.md) per creare una tabella specificando più righe.  
  
 Per ulteriori informazioni sulla sintassi e gli argomenti di questa clausola, vedere [FROM &#40; Transact-SQL &#41; ](../../t-sql/queries/from-transact-sql.md).  
  
 ON \<merge_search_condition >  
 Specifica le condizioni in cui \<table_source > è unita in join con *target_table* per determinare dove corrispondono. 
  
> [!CAUTION]  
>  È importante specificare solo le colonne della tabella di destinazione utilizzate ai fini della corrispondenza, ovvero specificare colonne della tabella di destinazione confrontate con quella corrispondente della tabella di origine. Non tentare di migliorare le prestazioni relative all'esecuzione delle query filtrando le righe della tabella di destinazione nella clausola ON, specificando ad esempio `AND NOT target_table.column_x = value`. Questa operazione potrebbe comportare la restituzione di risultati imprevisti e non corretti.  
  
 Quando esiste una corrispondenza quindi \<merge_matched >  
 Specifica che tutte le righe di *target_table* che corrispondono alle righe restituite da \<table_source > ON \<merge_search_condition > e soddisfano qualsiasi condizione di ricerca aggiuntivi, vengono aggiornati o eliminati in base al \<merge_matched > clausola.  
  
 Nell'istruzione MERGE possono essere presenti al massimo due clausole WHEN MATCHED. Se vengono specificate due clausole, quindi la prima clausola deve essere accompagnata da un AND \<search_condition > clausola. Per ogni riga specificata, la seconda clausola WHEN MATCHED viene applicata solo nel caso in cui non venga applicata la prima. Se sono presenti due clausole WHEN MATCHED, è necessario che una specifichi un'azione UPDATE e l'altra un'azione DELETE. Se viene specificato UPDATE nel \<merge_matched > clausola e più di una riga di \<table_source > corrisponde a una riga in *target_table* in base a \<merge_search_condition >, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]restituisce un errore. L'istruzione MERGE non può aggiornare la stessa riga più di una volta né aggiornare ed eliminare la stessa riga.  
  
 Quando non MATCHED [BY TARGET] THEN \<merge_not_matched >  
 Specifica che una riga viene inserita in *target_table* per ogni riga restituita da \<table_source > ON \<merge_search_condition > che non corrisponde una riga in *target_table*, ma che soddisfa una condizione di ricerca aggiuntivi, se presente. I valori da inserire vengono specificati per il \<merge_not_matched > clausola. Nell'istruzione MERGE può essere presente solo una clausola WHEN NOT MATCHED.  
  
 WHEN NOT MATCHED BY SOURCE quindi \<merge_matched >  
 Specifica che tutte le righe di *target_table* che non corrispondono alle righe restituite da \<table_source > ON \<merge_search_condition >, e che soddisfano qualsiasi condizione di ricerca aggiuntiva vengono aggiornata una o deleted in base al \<merge_matched > clausola.  
  
 Nell'istruzione MERGE possono essere presenti al massimo due clausole WHEN NOT MATCHED BY SOURCE. Se vengono specificate due clausole, quindi la prima clausola deve essere accompagnata da un AND \<clause_search_condition > clausola. Per ogni riga specificata, la seconda clausola WHEN NOT MATCHED BY SOURCE viene applicata solo nel caso in cui non venga applicata la prima. Se sono presenti due clausole WHEN NOT MATCHED BY SOURCE, è necessario che una specifichi un'azione UPDATE e l'altra un'azione DELETE. Possono fare riferimento solo a colonne della tabella di destinazione \<clause_search_condition >.  
  
 Quando viene restituita alcuna riga da \<table_source >, non è possibile accedere alle colonne nella tabella di origine. Se l'azione update o delete specificata nel \<merge_matched > clausola fa riferimento alle colonne nella tabella di origine, viene restituito l'errore 207 (nome di colonna non valida). La clausola `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` può provocare, ad esempio, un errore nell'istruzione poiché non è possibile accedere a `Col1` nella tabella di origine.  
  
 E \<clause_search_condition >  
 Specifica qualsiasi condizione di ricerca valida. Per ulteriori informazioni, vedere [condizione di ricerca &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
 \<table_hint_limited >  
 Specifica uno o più hint di tabella applicati alla tabella di destinazione per ogni azione di inserimento, aggiornamento o eliminazione eseguita dall'istruzione MERGE. La parola chiave WITH e le parentesi sono obbligatorie.  
  
 Le opzioni NOLOCK e READUNCOMMITTED non sono consentite. Per ulteriori informazioni sugli hint di tabella, vedere [hint di tabella &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 La specifica di un hint TABLOCK in una tabella di destinazione di un'istruzione INSERT equivale alla specifica dell'hint TABLOCKX poiché determina l'acquisizione di un blocco esclusivo sulla tabella. Quando viene specificato, FORCESEEK viene applicato all'istanza implicita della tabella di destinazione unita in join con la tabella di origine.  
  
> [!CAUTION]  
>  La specifica di READPAST con WHEN NOT MATCHED [BY TARGET] THEN INSERT può provocare l'esecuzione di operazioni INSERT che violano i vincoli UNIQUE.  
  
 INDEX ( index_val [ ,...n ] )  
 Specifica il nome o l'ID di uno o più indici della tabella di destinazione per eseguire un join implicito con la tabella di origine. Per altre informazioni, vedere [Hint di tabella &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 \<output_clause >  
 Restituisce una riga per ogni riga *target_table* che viene aggiornato, inserite o eliminate, in nessun ordine particolare. **$action** può essere specificato nella clausola output. **$action** è una colonna di tipo **nvarchar (10)** che restituisce uno dei tre valori per ogni riga: 'INSERT', 'UPDATE' o 'DELETE', in base all'azione eseguita su tale riga. Per ulteriori informazioni sugli argomenti di questa clausola, vedere [clausola OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
 OPZIONE ( \<query_hint > [,... n])  
 Specifica che vengono utilizzati hint di ottimizzazione per personalizzare il modo in cui il Motore di database elabora l'istruzione. Per altre informazioni, vedere [Hint per la query &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
 \<merge_matched >  
 Specifica l'aggiornamento o eliminazione di azione che viene applicato a tutte le righe di *target_table* che non corrispondono alle righe restituite da \<table_source > ON \<merge_search_condition >, e che soddisfano una condizione di ricerca aggiuntiva.  
  
 AGGIORNAMENTO impostato \<set_clause >  
 Specifica l'elenco di colonne o di nomi di variabile da aggiornare nella tabella di destinazione e i valori in base ai quali eseguire l'aggiornamento.  
  
 Per ulteriori informazioni sugli argomenti di questa clausola, vedere [UPDATE &#40; Transact-SQL &#41; ](../../t-sql/queries/update-transact-sql.md). Non è consentito impostare una variabile sullo stesso valore di una colonna.  
  
 DELETE  
 Specifica che le righe corrispondenti alle righe di *target_table* vengono eliminati.  
  
 \<merge_not_matched >  
 Specifica i valori da inserire nella tabella di destinazione.  
  
 (*column_list*)  
 Elenco di una o più colonne della tabella di destinazione in cui inserire i dati. Le colonne devono essere specificate come un nome costituito da una sola parte. *column_list* deve essere racchiuso tra parentesi e delimitato da virgole.  
  
 VALORI ( *elenco_valori*)  
 Elenco delimitato da virgole di costanti, variabili o espressioni che restituiscono valori da inserire nella tabella di destinazione. Le espressioni non possono contenere un'istruzione EXECUTE.  
  
 DEFAULT VALUES  
 Forza l'immissione nella riga inserita dei valori predefiniti associati a ogni colonna.  
  
 Per ulteriori informazioni su questa clausola, vedere [INSERT &#40; Transact-SQL &#41; ](../../t-sql/statements/insert-transact-sql.md).  
  
 \<condizione di ricerca >  
 Specifica le condizioni di ricerca utilizzate per specificare \<merge_search_condition > o \<clause_search_condition >. Per ulteriori informazioni sugli argomenti di questa clausola, vedere [condizione di ricerca &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 È necessario specificare almeno una delle tre clausole MATCHED, le quali possono essere tuttavia specificate in qualsiasi ordine. Non è possibile aggiornare una variabile più di una volta nella stessa clausola MATCHED.  
  
 Tutte le azioni di inserimento, aggiornamento o eliminazione specificate nella tabella di destinazione dall'istruzione MERGE sono limitate da qualsiasi vincolo definito sulla tabella, inclusi vincoli di integrità referenziale di propagazione. Se IGNORE_DUP_KEY è impostato su ON per qualsiasi indice univoco nella tabella di destinazione, MERGE ignora questa impostazione.  
  
 Nell'istruzione MERGE è necessario utilizzare un punto e virgola (;) come carattere di terminazione. In caso contrario, viene generato l'errore 10713.  
  
 Quando utilizzato dopo MERGE, [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md) restituisce il numero totale di righe inserite, aggiornate ed eliminate al client.  
  
 MERGE è una parola chiave completamente riservata se il livello di compatibilità del database è impostato su 100 o un valore più elevato. Sebbene l'istruzione MERGE sia disponibile per i livelli di compatibilità del database 90 e 100, se il livello di compatibilità è impostato su 90 la parola chiave non è completamente riservata.  
  
 Il **MERGE** istruzione non deve essere utilizzata quando si utilizza in coda di replica di aggiornamento. Il **MERGE** e trigger per l'aggiornamento in coda non sono compatibili. Sostituire il **MERGE** istruzione con un'istruzione insert o un'istruzione update.  
  
## <a name="trigger-implementation"></a>Implementazione dei trigger  
 Per ogni azione di inserimento, aggiornamento o eliminazione specificata nell'istruzione MERGE, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono attivati i trigger AFTER corrispondenti definiti nella tabella di destinazione, senza garantire l'ordine di attivazione dei trigger per le azioni. I trigger definiti per la stessa azione rispettano l'ordine specificato dall'utente. Per ulteriori informazioni sull'impostazione dell'ordine di attivazione di trigger, vedere [specificare primo e ultimo trigger](../../relational-databases/triggers/specify-first-and-last-triggers.md).  
  
 Se per la tabella di destinazione è abilitato un trigger INSTEAD OF definito nella tabella stessa per un'azione di inserimento, aggiornamento o eliminazione eseguita da un'istruzione MERGE, è necessario che per tale tabella sia abilitato un trigger INSTEAD OF per tutte le azioni specificate nell'istruzione MERGE.  
  
 Se sono presenti INSTEAD OF UPDATE o definire trigger INSTEAD OF DELETE in *target_table*, non vengono eseguite le operazioni update o delete. Al contrario, viene attivato il trigger e **inserito** e **eliminato** tabelle vengono popolate di conseguenza.  
  
 Se sono presenti trigger INSERT definito nella INSTEAD OF *target_table*, non viene eseguita l'operazione di inserimento. Al contrario, viene attivato il trigger e **inserito** tabella viene popolata di conseguenza.  
  
## <a name="permissions"></a>Permissions  
 È necessario disporre dell'autorizzazione SELECT per la tabella di origine e dell'autorizzazione INSERT, UPDATE o DELETE per quella di destinazione. Per ulteriori informazioni, vedere la sezione autorizzazioni nel [selezionare](../../t-sql/queries/select-transact-sql.md), [inserire](../../t-sql/statements/insert-transact-sql.md), [aggiornamento](../../t-sql/queries/update-transact-sql.md), e [eliminare](../../t-sql/statements/delete-transact-sql.md) argomenti.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-merge-to-perform-insert-and-update-operations-on-a-table-in-a-single-statement"></a>A. Utilizzo di MERGE per eseguire operazioni INSERT e UPDATE in una tabella in un'unica istruzione  
 Uno scenario comune prevede l'aggiornamento di una o più colonne di una tabella nel caso in cui sia presente una riga corrispondente oppure l'inserimento dei dati come nuova riga nel caso in cui la riga corrispondente non sia presente. Questa operazione viene eseguita in genere passando i parametri a una stored procedure contenente le istruzioni UPDATE e INSERT appropriate. Con l'istruzione MERGE è possibile eseguire entrambe le attività in un'unica istruzione. Nell'esempio seguente viene illustrata una stored procedure nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] che contiene un'istruzione INSERT e un'istruzione UPDATE. La stored procedure viene quindi modificata per eseguire le operazioni equivalenti utilizzando una singola istruzione MERGE.  
  
```  
CREATE PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
-- Update the row if it exists.      
    UPDATE Production.UnitMeasure  
SET Name = @Name  
WHERE UnitMeasureCode = @UnitMeasureCode  
-- Insert the row if the UPDATE statement failed.  
IF (@@ROWCOUNT = 0 )  
BEGIN  
    INSERT INTO Production.UnitMeasure (UnitMeasureCode, Name)  
    VALUES (@UnitMeasureCode, @Name)  
END  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Test Value';  
SELECT UnitMeasureCode, Name FROM Production.UnitMeasure  
WHERE UnitMeasureCode = 'ABC';  
GO  
  
-- Rewrite the procedure to perform the same operations using the 
-- MERGE statement.  
-- Create a temporary table to hold the updated or inserted values 
-- from the OUTPUT clause.  
CREATE TABLE #MyTempTable  
    (ExistingCode nchar(3),  
     ExistingName nvarchar(50),  
     ExistingDate datetime,  
     ActionTaken nvarchar(10),  
     NewCode nchar(3),  
     NewName nvarchar(50),  
     NewDate datetime  
    );  
GO  
ALTER PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
  
    MERGE Production.UnitMeasure AS target  
    USING (SELECT @UnitMeasureCode, @Name) AS source (UnitMeasureCode, Name)  
    ON (target.UnitMeasureCode = source.UnitMeasureCode)  
    WHEN MATCHED THEN   
        UPDATE SET Name = source.Name  
WHEN NOT MATCHED THEN  
    INSERT (UnitMeasureCode, Name)  
    VALUES (source.UnitMeasureCode, source.Name)  
    OUTPUT deleted.*, $action, inserted.* INTO #MyTempTable;  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'New Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'XYZ', @Name = 'Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Another Test Value';  
  
SELECT * FROM #MyTempTable;  
-- Cleanup   
DELETE FROM Production.UnitMeasure WHERE UnitMeasureCode IN ('ABC','XYZ');  
DROP TABLE #MyTempTable;  
GO  
```  
  
### <a name="b-using-merge-to-perform-update-and-delete-operations-on-a-table-in-a-single-statement"></a>B. Utilizzo di MERGE per eseguire operazioni UPDATE e DELETE in una tabella in un'unica istruzione  
 Nell'esempio seguente viene utilizzata l'istruzione MERGE per aggiornare la tabella `ProductInventory` nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] con frequenza giornaliera, in base agli ordini elaborati nella tabella `SalesOrderDetail`. La colonna `Quantity` della tabella `ProductInventory` viene aggiornata sottraendo il numero di ordini effettuati ogni giorno per ciascun prodotto nella tabella `SalesOrderDetail`. Se il numero di ordini per un prodotto riduce il livello delle scorte del prodotto a zero o a un valore inferiore, la riga relativa a tale prodotto viene eliminata dalla tabella `ProductInventory`.  
  
```  
CREATE PROCEDURE Production.usp_UpdateInventory  
    @OrderDate datetime  
AS  
MERGE Production.ProductInventory AS target  
USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
    JOIN Sales.SalesOrderHeader AS soh  
    ON sod.SalesOrderID = soh.SalesOrderID  
    AND soh.OrderDate = @OrderDate  
    GROUP BY ProductID) AS source (ProductID, OrderQty)  
ON (target.ProductID = source.ProductID)  
WHEN MATCHED AND target.Quantity - source.OrderQty <= 0  
    THEN DELETE  
WHEN MATCHED   
    THEN UPDATE SET target.Quantity = target.Quantity - source.OrderQty,   
                    target.ModifiedDate = GETDATE()  
OUTPUT $action, Inserted.ProductID, Inserted.Quantity, 
    Inserted.ModifiedDate, Deleted.ProductID,  
    Deleted.Quantity, Deleted.ModifiedDate;  
GO  
  
EXECUTE Production.usp_UpdateInventory '20030501'  
```  
  
### <a name="c-using-merge-to-perform-update-and-insert-operations-on-a-target-table-by-using-a-derived-source-table"></a>C. Utilizzo di MERGE per eseguire operazioni UPDATE e INSERT in una tabella di destinazione utilizzando una tabella di origine derivata  
 Nell'esempio seguente viene utilizzata l'istruzione MERGE per modificare la tabella `SalesReason` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] eseguendo l'aggiornamento o l'inserimento di righe. Quando il valore di `NewName` nella tabella di origine corrisponde a un valore della colonna `Name` nella tabella di destinazione (`SalesReason`), la colonna `ReasonType` viene aggiornata nella tabella di destinazione. Quando il valore di `NewName` non corrisponde, la riga di origine viene inserita nella tabella di destinazione. La tabella di origine è una tabella derivata che utilizza il costruttore di valori di tabella [!INCLUDE[tsql](../../includes/tsql-md.md)] per specificare più righe per la tabella di origine. Per ulteriori informazioni sull'utilizzo del costruttore di valori di tabella in una tabella derivata, vedere [il costruttore di valori di tabella &#40; Transact-SQL &#41; ](../../t-sql/queries/table-value-constructor-transact-sql.md). Nell'esempio viene inoltre illustrato come archiviare i risultati della clausola OUTPUT in una variabile di tabella e viene fornito un riepilogo dei risultati dell'istruzione MERGE mediante l'esecuzione di un'operazione di selezione semplice che restituisce il numero di righe inserite e aggiornate.  
  
```  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), 
              ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
```  
  
### <a name="d-inserting-the-results-of-the-merge-statement-into-another-table"></a>D. Inserimento dei risultati dell'istruzione MERGE in un'altra tabella  
 Nell'esempio seguente vengono acquisiti i dati restituiti dalla clausola OUTPUT di un'istruzione MERGE e tali dati vengono inseriti in un'altra tabella. L'istruzione MERGE consente di aggiornare la colonna `Quantity` della tabella `ProductInventory` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], in base agli ordini elaborati nella tabella `SalesOrderDetail`. In questo esempio vengono acquisite le righe aggiornate, inserite successivamente in un'altra tabella utilizzata per tenere traccia delle modifiche apportate alle scorte.  
  
```  
CREATE TABLE Production.UpdatedInventory  
    (ProductID INT NOT NULL, LocationID int, NewQty int, PreviousQty int,  
     CONSTRAINT PK_Inventory PRIMARY KEY CLUSTERED (ProductID, LocationID));  
GO  
INSERT INTO Production.UpdatedInventory  
SELECT ProductID, LocationID, NewQty, PreviousQty   
FROM  
(    MERGE Production.ProductInventory AS pi  
     USING (SELECT ProductID, SUM(OrderQty)   
            FROM Sales.SalesOrderDetail AS sod  
            JOIN Sales.SalesOrderHeader AS soh  
            ON sod.SalesOrderID = soh.SalesOrderID  
            AND soh.OrderDate BETWEEN '20030701' AND '20030731'  
            GROUP BY ProductID) AS src (ProductID, OrderQty)  
     ON pi.ProductID = src.ProductID  
    WHEN MATCHED AND pi.Quantity - src.OrderQty >= 0   
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0   
        THEN DELETE  
    OUTPUT $action, Inserted.ProductID, Inserted.LocationID, 
        Inserted.Quantity AS NewQty, Deleted.Quantity AS PreviousQty)  
 AS Changes (Action, ProductID, LocationID, NewQty, PreviousQty) 
 WHERE Action = 'UPDATE';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Clausola OUTPUT &#40; Transact-SQL &#41;](../../t-sql/queries/output-clause-transact-sql.md)   
 [UNIRE i pacchetti di Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Il costruttore di valori di tabella &#40; Transact-SQL &#41;](../../t-sql/queries/table-value-constructor-transact-sql.md)  
  
  


