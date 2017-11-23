---
title: CREATE STATISTICS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATISTICS
- STATISTICS_TSQL
- CREATE STATISTICS
- CREATE_STATISTICS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], creating
- indexed views [SQL Server], statistics
- FULLSCAN option
- CREATE STATISTICS statement
- filtered statistics [SQL Server]
- creating statistics [SQL Server]
- NORECOMPUTE clause
ms.assetid: b23e2f6b-076c-4e6d-9281-764bdb616ad2
caps.latest.revision: "105"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3e1f234dc76b6b231fc3f1d0f258937e70035a65
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-statistics-transact-sql"></a>CREATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crea le statistiche di ottimizzazione delle query in una o più colonne di una tabella, una vista indicizzata o una tabella esterna. Per la maggior parte delle query, Query Optimizer genera già le statistiche necessarie per un piano di query di alta qualità. In alcuni casi, è necessario creare statistiche aggiuntive con CREATE STATISTICS o modificare la progettazione delle query per ottenere prestazioni migliori di esecuzione delle query.  
  
 Per ulteriori informazioni, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create statistics on an external table  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WITH FULLSCAN ] ;  
  
-- Create statistics on a regular table or indexed view  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH   
        [ [ FULLSCAN   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | SAMPLE number { PERCENT | ROWS }   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | STATS_STREAM = stats_stream ] ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ]  
    ] ;  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE STATISTICS statistics_name   
    ON [ database_name . [schema_name ] . | schema_name. ] table_name   
    ( column_name  [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH {  
           FULLSCAN   
           | SAMPLE number PERCENT   
      }  
    ]  
[;]  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome_statistiche*  
 Nome delle statistiche da creare.  
  
 *table_or_indexed_view_name*  
 È il nome della tabella, vista indicizzata o tabella esterna in cui creare le statistiche. Per creare statistiche in un altro database, specificare un nome di tabella completo.  
  
 *colonna [,... n]*  
 Uno o più colonne da includere nelle statistiche. Le colonne devono essere in ordine di priorità da sinistra a destra. Solo la prima colonna consente di creare l'istogramma. Tutte le colonne vengono utilizzate per le statistiche sulla correlazione tra colonne denominate densità.  
  
 È possibile specificare qualsiasi colonna utilizzabile come colonna chiave di indice, con le eccezioni seguenti:  
  
-   **XML**, full-text, le colonne FILESTREAM non possono essere specificato.  
  
-   È possibile specificare colonne calcolate solo se le opzioni del database ARITHABORT e QUOTED_IDENTIFIER sono impostate su ON.  
  
-   È possibile specificare colonne di tipo CLR definito dall'utente se il tipo supporta l'ordinamento binario. È possibile specificare colonne calcolate definite come chiamate di metodi da una colonna con tipo definito dall'utente se tali metodi sono contrassegnati come deterministici.  
  
 DOVE \<filter_predicate > specifica un'espressione per la selezione di un subset di righe da includere quando si crea l'oggetto statistiche. Le statistiche create con un predicato del filtro vengono definite statistiche filtrate. Il predicato del filtro utilizza una logica di confronto semplice e non può fare riferimento a una colonna calcolata, una colonna di tipo definito dall'utente, una colonna di tipo di dati spaziali o **hierarchyID** colonna tipo di dati. I confronti in cui vengono utilizzati valori letterali NULL non sono consentiti con gli operatori di confronto. In alternativa, utilizzare gli operatori IS NULL e IS NOT NULL.  
  
 Di seguito sono riportati alcuni esempi di predicati di filtro per la tabella Production.BillOfMaterials:  
  
 `WHERE StartDate > '20000101' AND EndDate <= '20000630'`  
  
 `WHERE ComponentID IN (533, 324, 753)`  
  
 `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
  
 Per ulteriori informazioni sui predicati di filtro, vedere [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).  
  
 FULLSCAN  
 Calcolare le statistiche analizzando tutte le righe. FULLSCAN e SAMPLE 100 PERCENT generano gli stessi risultati. Non è possibile utilizzare FULLSCAN con l'opzione SAMPLE.  
  
 Se omessa, utilizza il campionamento per creare le statistiche di SQL Server e determina le dimensioni di esempio che sono necessario per creare un piano di query di alta qualità  
  
 ESEMPIO *numero* {% | RIGHE}  
 Specifica la percentuale approssimativa o il numero di righe presenti nella tabella o nella vista indicizzata utilizzate da Query Optimizer durante la creazione delle statistiche. Per PERCENT, *numero* può essere compreso tra 0 e 100, mentre per le righe, *numero* può essere compreso tra 0 al numero totale di righe. La percentuale effettiva o il numero di righe campionate da Query Optimizer potrebbero non corrispondere alla percentuale o al numero specificato. Query Optimizer analizza ad esempio tutte le righe in una pagina di dati.  
  
 SAMPLE è utile per i casi speciali in cui il piano di query, basato sul campionamento predefinito, non è ottimale. Nella maggior parte delle situazioni, non è necessario specificare SAMPLE perché Query Optimizer utilizza già il campionamento e determina le dimensioni del campione statisticamente significative per impostazione predefinita, come richiesto per creare piani di query di alta qualità.  
  
 Questa opzione non può essere utilizzata quando viene specificata l'opzione FULLSCAN. Se non si specifica né SAMPLE né FULLSCAN, Query Optimizer utilizza i dati campionati e calcola le dimensioni del campione per impostazione predefinita.  
  
 Si sconsiglia di specificare 0 PERCENT o 0 ROWS. Se si specifica 0 PERCENT o ROWS, l'oggetto statistiche viene creato ma non conterrà i dati delle statistiche.  
 
 PERSIST_SAMPLE_PERCENT = {ON | OFF}  
 Quando **ON**, le statistiche verranno mantenute la percentuale di campionamento di creazione per gli aggiornamenti successivi che non specificano in modo esplicito una percentuale di campionamento. Quando **OFF**, verrà reimpostata la percentuale di campionamento delle statistiche per il campionamento predefinito nei successivi aggiornamenti che non specificano in modo esplicito una percentuale di campionamento. Il valore predefinito è **OFF**. 
 
 **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4) tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (a partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU1).    
  
 STATS_STREAM  **=**  *stats_stream*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 NORECOMPUTE  
 Disabilitare le statistiche automatiche AUTO_UPDATE_STATISTICS, opzione di aggiornamento per *nome_statistiche*. Se si specifica questa opzione, query optimizer completa gli aggiornamenti delle statistiche in corso per *nome_statistiche* e disabilita gli aggiornamenti futuri.  
  
 Per riabilitare gli aggiornamenti delle statistiche, rimuovere le statistiche con [DROP STATISTICS](../../t-sql/statements/drop-statistics-transact-sql.md) e quindi eseguire CREATE STATISTICS senza l'opzione NORECOMPUTE.  
  
> [!WARNING]  
>  L'utilizzo di questa opzione può produrre piani di query non ottimali. È consigliabile limitare l'utilizzo di questa opzione e riservarne l'applicazione a un amministratore del sistema qualificato.  
  
 Per ulteriori informazioni sull'opzione AUTO_UPDATE_STATISTICS, vedere [opzioni ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Per ulteriori informazioni sulla disabilitazione e riabilitazione degli aggiornamenti delle statistiche, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
 INCREMENTAL = { ON | OFF }  
 Quando **ON**, le statistiche create sono di tipo per le statistiche della partizione. Quando **OFF**, statistiche sono combinate per tutte le partizioni. Il valore predefinito è **OFF**.  
  
 Se le statistiche per partizione non sono supportate, viene generato un errore. Le statistiche incrementali non sono supportate per i seguenti tipi di statistiche:  
  
-   Statistiche create con indici che non hanno il partizionamento allineato con la tabella di base.  
  
-   Statistiche create per i database secondari leggibili Always On.  
  
-   Statistiche create per i database di sola lettura.  
  
-   Statistiche create per gli indici filtrati.  
  
-   Statistiche create per le viste.  
  
-   Statistiche create per le tabelle interne.  
  
-   Statistiche create con indici spaziali o indici XML.  
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Richiede una delle seguenti autorizzazioni:  
  
-   ALTER TABLE  
  
-   Utente è proprietario della tabella  
  
-   L'appartenenza di **db_ddladmin** ruolo predefinito del database  
  
## <a name="general-remarks"></a>Osservazioni generali  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]può utilizzare tempdb per ordinare le righe campionate prima compilazione di statistiche.  
  
### <a name="statistics-for-external-tables"></a>Statistiche per le tabelle esterne  
 Quando si creano statistiche di tabella esterna, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Importa nella tabella esterna in una variabile temporanea [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella e quindi crea le statistiche. Per le statistiche di esempi, vengono importate solo le righe campionate. Se si dispone di una tabella esterna di grandi dimensioni, sarà molto più veloce usare il campionamento predefinito anziché l'opzione di analisi completa.  
  
### <a name="statistics-with-a-filtered-condition"></a>Statistiche con una condizione filtrata  
 Le statistiche filtrate possono migliorare le prestazioni di esecuzione delle query che effettuano la selezione da subset ben definiti di dati. Le statistiche filtrate utilizzano un predicato del filtro nella clausola WHERE per selezionare il subset di dati incluso nelle statistiche.  
  
### <a name="when-to-use-create-statistics"></a>Quando utilizzare CREATE STATISTICS  
 Per ulteriori informazioni sull'utilizzo di CREATE STATISTICS, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
### <a name="referencing-dependencies-for-filtered-statistics"></a>Dipendenze di riferimento per le statistiche filtrate  
 Il [Sys. sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) vista del catalogo tiene traccia di ogni colonna nel predicato delle statistiche filtrate come una dipendenza di riferimento. Tenere presente le operazioni eseguite sulle colonne della tabella prima di creare statistiche filtrate poiché non è possibile eliminare, rinominare o modificare la definizione di una colonna della tabella definita in un predicato delle statistiche filtrate.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
*  Aggiornamento delle statistiche non è supportata nelle tabelle esterne. Per aggiornare le statistiche in una tabella esterna, eliminare e ricreare le statistiche.  
*  È possibile elencare fino a 64 colonne per ogni oggetto statistiche.
  
## <a name="examples"></a>Esempi  

### <a name="examples-use-the-adventureworks-database"></a>Esempi utilizzano il database AdventureWorks.  

### <a name="a-using-create-statistics-with-sample-number-percent"></a>A. Utilizzo di CREATE STATISTICS con l'opzione SAMPLE number PERCENT  
 Nell'esempio seguente vengono create le statistiche `ContactMail1` utilizzando un campionamento casuale del 5% delle colonne `BusinessEntityID` e `EmailPromotion` della tabella `Contact` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```t-sql  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
```  
  
### <a name="b-using-create-statistics-with-fullscan-and-norecompute"></a>B. Utilizzo di CREATE STATISTICS con le opzioni FULLSCAN e NORECOMPUTE  
 Nell'esempio seguente vengono create le statistiche `ContactMail2` per tutte le righe nelle colonne `BusinessEntityID` e `EmailPromotion` della tabella `Contact` e viene disabilitato il ricalcolo automatico delle statistiche.  
  
```t-sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, NORECOMPUTE;  
```  
  
### <a name="c-using-create-statistics-to-create-filtered-statistics"></a>C. Utilizzo di CREATE STATISTICS per creare statistiche filtrate  
 Nell'esempio seguente vengono create le statistiche filtrate `ContactPromotion1`. [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilizza come campione il 50% dei dati, quindi seleziona le righe in cui `EmailPromotion` è uguale a 2.  
  
```t-sql  
CREATE STATISTICS ContactPromotion1  
    ON Person.Person (BusinessEntityID, LastName, EmailPromotion)  
WHERE EmailPromotion = 2  
WITH SAMPLE 50 PERCENT;  
GO  
```  
  
### <a name="d-create-statistics-on-an-external-table"></a>D. Creare statistiche per una tabella esterna  
 La decisione sola che quando si creano statistiche in una tabella esterna, oltre a fornire l'elenco di colonne, è necessario è se si desidera creare le statistiche tramite le righe di dati campione o analizzando tutte le righe.  
  
 Poiché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiederà più importazioni di dati della tabella esterna in una tabella temporanea per creare le statistiche, l'opzione di analisi completa. Per una tabella di grandi dimensioni, il metodo di campionamento predefinito è in genere sufficiente.  
  
```t-sql  
--Create statistics on an external table and use default sampling.  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
  
--Create statistics on an external table and scan all the rows  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  

### <a name="e-using-create-statistics-with-fullscan-and-persistsamplepercent"></a>E. Utilizzo di CREATE STATISTICS con le opzioni FULLSCAN e PERSIST_SAMPLE_PERCENT  
 Nell'esempio seguente viene creata la `ContactMail2` statistiche per tutte le righe il `BusinessEntityID` e `EmailPromotion` colonne di `Contact` tabella e imposta una percentuale di campionamento pari al 100% per tutti gli aggiornamenti successivi che eseguire in modo esplicito non specificare un campionamento percentuale.  
  
```t-sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, PERSIST_SAMPLE_PERCENT = ON;  
```  
  
### <a name="examples-using-adventureworksdw-database"></a>Esempi di utilizzo di database AdventureWorksDW. 
  
### <a name="f-create-statistics-on-two-columns"></a>F. Creazione di statistiche su due colonne  
 Nell'esempio seguente viene creata la `CustomerStats1` statistiche, in base al `CustomerKey` e `EmailAddress` colonne di `DimCustomer` tabella. Le statistiche vengono create in base a un campione statisticamente significativo delle righe di `Customer` tabella.  
  
```t-sql  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
```  
  
### <a name="g-create-statistics-by-using-a-full-scan"></a>G. Creare statistiche tramite un'analisi completa  
 Nell'esempio seguente viene creata la `CustomerStatsFullScan` statistiche, in base a tutte le righe nell'analisi di `DimCustomer` tabella.  
  
```t-sql  
CREATE STATISTICS CustomerStatsFullScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  
  
### <a name="h-create-statistics-by-specifying-the-sample-percentage"></a>H. Creare statistiche specificando la percentuale di esempio  
 Nell'esempio seguente viene creata la `CustomerStatsSampleScan` statistiche, l'analisi del 50% delle righe in base il `DimCustomer` tabella.  
  
```t-sql  
CREATE STATISTICS CustomerStatsSampleScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH SAMPLE 50 PERCENT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Statistiche](../../relational-databases/statistics/statistics.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Sys. stats_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)  
  
  

