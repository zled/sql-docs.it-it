---
title: Aggiornato - esempio per i documenti del Server SQL | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per esempio per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: samples
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.author: genemi
ms.workload: sample
ms.openlocfilehash: 363cb5dde93c628317a977082fe8697af890d51c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sample-for-sql-server"></a>Nuovi e aggiornati: esempio per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-09-28** &nbsp; - a - &nbsp; **2017-02-12**
- *Area di interesse:* &nbsp; **esempio per SQL Server**.




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

1. [Catalogo del database WideWorldImporters](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-wideworldimporters-database-catalogworld-wide-importersdatabase-catalog-oltpmd"></a>1. &nbsp;[Catalogo del database WideWorldImporters](world-wide-importers/database-catalog-oltp.md)

*Ultimo aggiornamento: 2017-11-20* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 136.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c055d0483699f06b8766ac2c999101934c14c55c 6975d5a3d1ade7b0ce34bd165bc0e9ef49299ba2  (PR=4032  ,  Filename=database-catalog-oltp.md  ,  Dirpath=docs\sample\world-wide-importers\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->



Laddove possibile, il database collocates tabelle che sono in genere sottoposti a query insieme nello stesso schema per ridurre al minimo la complessità di join.

Lo schema del database è stato generato codice basato su una serie di tabelle di metadati in un altro database WWI_Preparation. In questo modo WideWorldImporters un livello molto elevato di coerenza di progettazione, denominazione coerenza e completezza. Per informazioni dettagliate su come è stato generato lo schema, vedere il codice sorgente: [wide-world-utilità di importazione/wwi-database-script](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

**Progettazione tabella**


- Tutte le tabelle dispongono di chiavi primarie di singola colonna per la semplicità di join.
- Tutti gli schemi, tabelle, colonne, indici e vincoli check presentano una descrizione estesa di proprietà che può essere usato per identificare lo scopo dell'oggetto o colonna. Le tabelle con ottimizzazione per la memoria sono un'eccezione perché attualmente non supportano le proprietà estese.
- Tutte le chiavi esterne vengono indicizzate automaticamente a meno che non è un altro indice non cluster con lo stesso componente a sinistra.
- La numerazione automatica nelle tabelle è basata su sequenze. Queste sequenze sono più facili da utilizzare tra i server collegati e di ambienti simili rispetto alle colonne di identità. Le tabelle con ottimizzazione per la memoria utilizzano le colonne IDENTITY, poiché non supportate in SQL Server 2016.
- Una singola sequenza (TransactionID) viene utilizzata per queste tabelle: CustomerTransactions SupplierTransactions e StockItemTransactions. Viene descritto come un set di tabelle può avere un'unica sequenza.
- Alcune colonne presentano valori predefiniti appropriati.

**Schemi di sicurezza**


Per la sicurezza, WideWorldImporters non consente alle applicazioni esterne accedere direttamente gli schemi di dati. Per isolare l'accesso, WideWorldImporters utilizza gli schemi di accesso di sicurezza che non contengono dati, ma contengono viste e stored procedure. Le applicazioni esterne utilizzano gli schemi di sicurezza per recuperare i dati che sono autorizzati a visualizzare.  In questo modo, gli utenti possono eseguire solo le viste e stored procedure negli schemi di accesso protetto







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3 + 14): **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87 + 0): **Analitica Platform System per SQL** documenti](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5 + 4): **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0 + 1): **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2 + 2): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10 + 9): **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2 + 4): **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornati (4 + 2): **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0 + 1): **esempi per SQL** documenti](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21 + 0): **operazioni SQL Studio** documenti](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5 + 1): **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0 + 2): **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): **dati Migration Assistant (DMA) per SQL** documenti](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


