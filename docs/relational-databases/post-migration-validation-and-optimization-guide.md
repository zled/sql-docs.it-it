---
title: Guida di ottimizzazione e convalida post-migrazione | Documenti Microsoft
ms.custom: 
ms.date: 5/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-migration validation and optimization
- guide, post-migration validation and optimization
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
caps.latest.revision: 3
author: pelopes
ms.author: harinid
manager: 
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: d81eabfa1bdb5736bbf6f53ed34c2e1ac157e782
ms.contentlocale: it-it
ms.lasthandoff: 05/25/2017

---
# <a name="post-migration-validation-and-optimization-guide"></a>Guida di ottimizzazione e convalida post-migrazione
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]post-migrazione passaggio è molto importante per la riconciliazione di qualsiasi accuratezza dei dati e la completezza, nonché rilevare problemi di prestazioni con il carico di lavoro.

# <a name="common-performance-scenarios"></a>Scenari comuni di prestazioni 
Di seguito sono riportati alcuni degli scenari comuni di prestazioni rilevati dopo la migrazione a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] piattaforma e come risolverli. Sono inclusi gli scenari sono specifdic a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazione (versioni precedenti a versioni più recenti), nonché la piattaforma esterna (ad esempio Oracle, DB2, MySQL e Sybase) per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazione.

## <a name="Parameter Sniffing"></a>Sensibilità allo sniffing dei parametri

**Si applica a:** piattaforma esterna (ad esempio Oracle, DB2, MySQL e Sybase) per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazione.

> [!NOTE]
> Per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazioni, se il problema era presente nell'origine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la migrazione a una versione più recente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] come-sarà non specifico per questo scenario. 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Compila i piani di query nelle stored procedure utilizzando lo sniffing dei parametri di input che la distribuzione dei dati di input in fase di compilazione prima, la generazione di un piano con parametri e riutilizzabile, ottimizzato per. Anche se non le stored procedure, la maggior parte delle istruzioni che generano piani semplici verranno parametri. Dopo che viene prima memorizzato nella cache un piano, un'esecuzione futura esegue il mapping a un piano precedentemente memorizzata nella cache.
Un potenziale problema si verifica quando la prima compilazione potrebbe non avere utilizzato i set di parametri più comuni per il carico di lavoro normale. Per i diversi parametri, lo stesso piano di esecuzione diventa inefficiente.

### <a name="steps-to-resolve"></a>Procedura di risoluzione

1.    Utilizzare il `RECOMPILE` hint. Un piano viene calcolato ogni volta che adattata a ogni valore del parametro.
2.    Riscrivere la stored procedure per utilizzare l'opzione `(OPTIMIZE FOR(<input parameter> = <value>))`. Decidere quale valore utilizzare che soddisfano la maggior parte del carico di lavoro pertinenti, creazione e gestione di un piano che diventa efficiente per il valore con parametri.
3.    Riscrivere la stored procedure utilizzando la variabile locale all'interno della routine. Ora di query optimizer utilizza il vettore di densità per le stime, risultante nello stesso piano indipendentemente dal valore del parametro.
4.    Riscrivere la stored procedure per utilizzare l'opzione `(OPTIMIZE FOR UNKNOWN)`. Stesso effetto utilizzando la tecnica di variabile locale.
5.    Riscrivere la query per utilizzare l'hint `DISABLE_PARAMETER_SNIFFING`. Lo stesso effetto delle utilizzando la tecnica di variabile locale per disabilitare completamente lo sniffing dei parametri, a meno che non `OPTION(RECOMPILE)`, `WITH RECOMPILE` o `OPTIMIZE FOR <value>` viene utilizzato.

> [!TIP] 
> Usare il [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] funzionalità di pianificazione di analisi per identificare rapidamente se si tratta di un problema. Sono disponibili altre informazioni [qui](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-query-performance-troubleshooting-made-easier/).

## <a name="Missing indexes"></a>Indici mancanti

**Si applica a:** piattaforma esterna (ad esempio Oracle, DB2, MySQL e Sybase) e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazione.

Gli indici non corretto o mancanti determina i/o aggiuntivo che fa riferimento alla memoria aggiuntiva e della CPU da sprecati. Ciò potrebbe essere perché il profilo di carico di lavoro è stato modificato, ad esempio utilizzando diversi predicati, invalidando esistente della struttura di indicizzazione. Evidenza di una strategia di indicizzazione scarsa o le modifiche nel profilo di carico di lavoro includono:
-   Cerca duplicato, ridondante, utilizzato raramente e gli indici inutilizzati completamente.
-   Particolare attenzione con gli indici inutilizzati con gli aggiornamenti.

### <a name="steps-to-resolve"></a>Procedura di risoluzione

1.    Utilizzare il piano di esecuzione grafico per i riferimenti a indice mancante.
2.    L'indicizzazione di suggerimenti generati da [Ottimizzazione guidata motore di Database](../tools/dta/tutorial-database-engine-tuning-advisor.md).
3.    Utilizzo di [DMV di indici mancanti](../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) o tramite il [Dashboard delle prestazioni di SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=29063).
4.    Utilizzare gli script di pre-esistenti che possono utilizzare le DMV esistente per consentono di comprendere tutti gli indici mancanti, duplicati, ridondanti, raramente utilizzati e inutilizzati completamente, ma anche se qualsiasi riferimento di indice è suggerisce/hard-coded in procedure esistenti e funzioni nel database. 

> [!TIP] 
> Esempi di tali script pre-esistente [la creazione dell'indice](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Creation) e [informazioni sugli indici](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Information). 

## <a name="Inability to use predicates"></a>Impossibilità di utilizzare predicati per filtrare i dati

**Si applica a:** piattaforma esterna (ad esempio Oracle, DB2, MySQL e Sybase) e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazione.

> [!NOTE]
> Per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazioni, se il problema era presente nell'origine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la migrazione a una versione più recente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] come-sarà non specifico per questo scenario.

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Query Optimizer può rendere conto di informazioni che sono noto in fase di compilazione. Se un carico di lavoro si basa sui predicati che possono essere nota solo in fase di esecuzione, quindi aumenta il rischio di una scelta del piano insoddisfacente. Per un piano di migliore qualità, devono essere predicati **SARGable**, o **S**ricerca **Arg**umento**in grado di**.

Alcuni esempi di predicati non SARGable:
-   Conversioni implicite dei dati, ad esempio VARCHAR, nvarchar, o INT a VARCHAR. Cercare gli avvisi di runtime CONVERT_IMPLICIT in piani di esecuzione effettivo. Conversione da un tipo a un altro può causare una perdita di precisione.
-   Le espressioni complesse di indeterminato, ad esempio `WHERE UnitPrice + 1 < 3.975`, ma non `WHERE UnitPrice < 320 * 200 * 32`.
-   Utilizzo delle funzioni, ad esempio espressioni `WHERE ABS(ProductID) = 771` o`WHERE UPPER(LastName) = 'Smith'`
-   Stringhe con un carattere jolly iniziale, ad esempio `WHERE LastName LIKE '%Smith'`, ma non `WHERE LastName LIKE 'Smith%'`.

### <a name="steps-to-resolve"></a>Procedura di risoluzione

1. Sempre dichiarare le variabili e i parametri come la destinazione desiderata [tipo di dati](../t-sql/data-types/data-types-transact-sql.md). 
  -   Questa operazione potrebbe comportare il confronto di qualsiasi costrutto di codice definito dall'utente che viene archiviato nel database (ad esempio stored procedure, funzioni definite dall'utente o viste) con le tabelle di sistema che includono informazioni sui tipi di dati utilizzati nelle tabelle sottostanti (ad esempio [Columns](../relational-databases/system-catalog-views/sys-columns-transact-sql.md)).
2. Se non è possibile attraversare tutto il codice per il precedente punto, per lo stesso scopo, modificare il tipo di dati della tabella in modo che corrisponda a qualsiasi dichiarazione di variabile o parametro.
3. Motivo out l'utilità dei costrutti indicati di seguito:
  -   Funzioni come predicati;
  -   Ricerche con caratteri jolly;
  -   Le espressioni complesse in base a colonne dati: valutare la necessità di creare colonne calcolate persistenti, che possono essere indicizzate;

> [!NOTE] 
> Tutti gli elementi possono essere eseguiti programmaticaly.

## <a name="Table Valued Functions"></a>Utilizzo delle funzioni con valori di tabella (rispetto a istruzioni multiple Inline)

**Si applica a:** piattaforma esterna (ad esempio Oracle, DB2, MySQL e Sybase) e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazione.

> [!NOTE]
> Per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] migrazioni, se il problema era presente nell'origine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la migrazione a una versione più recente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] come-sarà non specifico per questo scenario.

Le funzioni a valori di tabella restituisce un tipo di dati di tabella che può essere un'alternativa alle viste. Mentre le viste sono limitate a un singolo `SELECT` istruzione, funzioni definite dall'utente possono contenere istruzioni aggiuntive che consentono più logica di quella consentita nelle viste.

> [!IMPORTANT] 
> Poiché la tabella di output di un MSTVF (funzione con valori di più istruzioni tabella) non è stata creata in fase di compilazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query Optimizer si basa sull'euristica e le statistiche non effettive, per determinare le stime di riga. Anche se gli indici vengono aggiunti per le tabelle di base, questa Guida non sarà. Per MSTVFs, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizza una stima predefinita di 1 per il numero di righe previsto che venga restituito da un MSTVF (a partire da [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] corretti stima è 100 righe).

### <a name="steps-to-resolve"></a>Procedura di risoluzione
1.    Se il TVF multi-istruzione singola istruzione, convertire TVF Inline.

    ```tsql
    CREATE FUNCTION dbo.tfnGetRecentAddress(@ID int)
    RETURNS @tblAddress TABLE
    ([Address] VARCHAR(60) NOT NULL)
    AS
    BEGIN
      INSERT INTO @tblAddress ([Address])
      SELECT TOP 1 [AddressLine1]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    RETURN
    END
    ```
    Per 

    ```tsql
    CREATE FUNCTION dbo.tfnGetRecentAddress_inline(@ID int)
    RETURNS TABLE
    AS
    RETURN (
      SELECT TOP 1 [AddressLine1] AS [Address]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    )
    ```

2.    Se più complesse, utilizzare i risultati intermedi archiviati in tabelle con ottimizzazione per la memoria o tabelle temporanee.

##  <a name="Additional_Reading"></a> Ulteriori informazioni  
 [Procedure consigliate per l'archivio query](../relational-databases/performance/best-practice-with-the-query-store.md)  
[Tabelle con ottimizzazione per la memoria](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
[Funzioni definite dall'utente](../relational-databases/user-defined-functions/user-defined-functions.md)  
[Le variabili di tabella e riga stime - parte 1](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/11/30/table-variables-and-row-estimations-part-1/)  
[Le variabili di tabella e riga stime - parte 2](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/12/09/table-variables-and-row-estimations-part-2/)  
[Piano di esecuzione Caching e riutilizzo](../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse)

