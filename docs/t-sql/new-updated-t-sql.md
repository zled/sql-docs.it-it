---
title: 'Aggiornamento: documentazione di T-SQL | Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione per Transact-SQL.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: t-sql
ms.date: 04/28/2018
ms.openlocfilehash: b1bc891bf7edc4cd82c38c8d647c279828190298
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32725623"
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Articoli nuovi e aggiornati di recente: documentazione di Transact-SQL



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **T-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


***Nessun nuovo articolo da visualizzare.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](#TitleNum_1)
2. [Istruzioni RESTORE (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-alter-database-scoped-configuration-transact-sqlstatementsalter-database-scoped-configuration-transact-sqlmd"></a>1. &nbsp; [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](statements/alter-database-scoped-configuration-transact-sql.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 150.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f6833910b664d0059a9073589807b195052325b3 bf969f123b22e6ebc650380a6905156f26ed6ca6  (PR=0  ,  Filename=alter-database-scoped-configuration-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



XTP_PROCEDURE_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**Si applica a**: *{Included-Content-Goes-Here}*

Abilita o disabilita la raccolta di statistiche di esecuzione a livello di modulo per i moduli T-SQL compilati in modo nativo nel database corrente. Il valore predefinito è OFF. Le statistiche di esecuzione vengono riflesse in [sys.dm_exec_procedure_stats].

Le statistiche di esecuzione a livello di modulo per i moduli T-SQL compilati in modo nativo vengono raccolte se questa opzione è ON o se la raccolta di statistiche è abilitata mediante [sp_xtp_control_proc_exec_stats].

XTP_QUERY_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**Si applica a**: *{Included-Content-Goes-Here}*

Abilita o disabilita la raccolta di statistiche di esecuzione a livello di istruzione per i moduli di T-SQL compilati in modo nativo nel database corrente. Il valore predefinito è OFF. Le statistiche di esecuzione vengono riflesse in [sys.dm_exec_query_stats] e in [Query Store].

Le statistiche di esecuzione a livello di istruzione per i moduli T-SQL compilati in modo nativo vengono raccolte se questa opzione è ON o se la raccolta di statistiche è abilitata mediante [sp_xtp_control_query_exec_stats].

Per informazioni dettagliate sul monitoraggio delle prestazioni dei moduli T-SQL compilati in modo nativo, vedere [Monitoraggio delle prestazioni di stored procedure compilate in modo nativo].



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-restore-statements-transact-sqlstatementsrestore-statements-transact-sqlmd"></a>2. &nbsp; [Istruzioni RESTORE (Transact-SQL)](statements/restore-statements-transact-sql.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1))

<!-- Source markdown line 339.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2902efb58bb964d3e9a0660956690d37f0397c00 36186a7cffd26ffa54a83e383ffd752dbc568a4d  (PR=0  ,  Filename=restore-statements-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Osservazioni generali - Istanza gestita di database SQL**


Nel caso di un ripristino asincrono, il ripristino continua anche se la connessione client si interrompe. Se la connessione è interrotta, è possibile controllare nella visualizzazione [sys.dm_operation_status] lo stato di un'operazione di ripristino (e lo stato di CREATE e DROP DATABASE).

Le seguenti opzioni di database sono impostate/sottoposte a override e non possono essere modificate in un secondo momento:

- NEW_BROKER (se il broker non è abilitato nel file con estensione bak)
- ENABLE_BROKER (se il broker non è abilitato nel file con estensione bak)
- AUTO_CLOSE=OFF (se un database nel file con estensione bak ha l'impostazione AUTO_CLOSE=ON)
- RECOVERY FULL (se un database nel file con estensione bak ha la modalità di ripristino SIMPLE o BULK_LOGGED)
- Il filegroup con ottimizzazione per la memoria viene aggiunto e denominato XTP se non era presente nel file con estensione bak di origine. Qualsiasi filegroup con ottimizzazione per la memoria esistente viene rinominato come XTP
- Le opzioni SINGLE_USER e RESTRICTED_USER vengono convertite in MULTI_USER

**Limitazioni - Istanza gestita di database SQL**

Si applicano le seguenti limitazioni:

- I file con estensione bak contenenti più set di backup non possono essere ripristinati.
- I file con estensione bak contenenti più file di log non possono essere ripristinati.
- Il ripristino non riesce se il file con estensione bak contiene dati FILESTREAM.
- Attualmente non è possibile ripristinare i backup contenenti database con oggetti in memoria attivi.
- Attualmente non è possibile ripristinare i backup contenenti database in cui sono stati presenti oggetti in memoria attivi.
- Attualmente non è possibile ripristinare i backup contenenti database in modalità di sola lettura. Questa limitazione verrà rimossa a breve.

Per altre informazioni, vedere [Istanza gestita].







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (11+6):&nbsp; documentazione di &nbsp;**Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (18+0): &nbsp; documentazione di &nbsp;**Analysis Services per SQL Server**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (218+14):**documentazione della**connessione a SQL Server](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (14+0):&nbsp; documentazione del &nbsp;**motore di database per SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (3+2): documentazione di &nbsp;&nbsp;**SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+3):&nbsp; documentazione di &nbsp;**Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (7+10):&nbsp; documentazione dei &nbsp;**database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+3):&nbsp; documentazione di &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (2+3):&nbsp; documentazione di &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (5+2):&nbsp; documentazione di &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+1): documentazione di &nbsp;&nbsp;**Tools per SQL Server**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0):**documentazione della**piattaforma di strumenti analitici per SQL Server](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)

