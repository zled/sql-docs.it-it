---
title: Documentazione aggiornata del motore di database | Microsoft Docs
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione per il motore di database.
services: na
documentationcenter: 
author: MightyPen
manager: craigg
editor: barbkess
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: cbf472ba2b8d2d7abad095992895b56940a82d92
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="new-and-recently-updated-database-engine-docs"></a>Documentazione del motore di database nuova e aggiornata di recente



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **motore di database**.




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

1. [Opzione di configurazione del server optimize for ad hoc workloads](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-optimize-for-ad-hoc-workloads-server-configuration-optionconfigure-windowsoptimize-for-ad-hoc-workloads-server-configuration-optionmd"></a>1. &nbsp; [Opzione di configurazione del server Ottimizza per carichi di lavoro ad hoc](configure-windows/optimize-for-ad-hoc-workloads-server-configuration-option.md)

*Aggiornamento: 20/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 38.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6ca71358f13780b930e6fd10e431d4df2bb96441 221306c4554ebd383ab68ed67cdaeca390f57106  (PR=4032  ,  Filename=optimize-for-ad-hoc-workloads-server-configuration-option.md  ,  Dirpath=docs\database-engine\configure-windows\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->



**Indicazioni**

Se il numero di piani a uso singolo occupa una parte significativa della memoria di ..!NCLUDE-NotShown--ssDEnoversion--../../includes/ssdenoversion-md.md)] in un server OLTP e questi piani sono piani ad-hoc, usare questa opzione server per ridurre l'uso della memoria con questi oggetti.
Per trovare il numero di piani a uso singolo memorizzati nella cache, eseguire la query seguente:

```
SELECT objtype, cacheobjtype,
  AVG(usecounts) AS Avg_UseCount,
  SUM(refcounts) AS AllRefObjects,
  SUM(CAST(size_in_bytes AS bigint))/1024/1024 AS Size_MB
FROM sys.dm_exec_cached_plans
WHERE objtype = 'Adhoc' AND usecounts = 1
GROUP BY objtype, cacheobjtype;
```

> [!IMPORTANT]
> L'impostazione dell'opzione **optimize for ad hoc workloads** su 1 influisce solo sui nuovi piani, mentre non si applica ai piani già presenti nella cache dei piani.
> Per influire immediatamente sui piani di query già memorizzati nella cache, è necessario cancellare il contenuto della cache dei piani usando [ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE--../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) oppure riavviare ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)].







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


