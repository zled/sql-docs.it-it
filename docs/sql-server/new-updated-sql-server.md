---
title: 'Articolo aggiornato: documentazione di SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione per SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: 
ms.component: sql-non-specified
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.author: genemi
ms.openlocfilehash: 77a97d94d005b43bf4c1a313a15a501cbe74a216
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Articoli nuovi e aggiornati di recente: documentazione di SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Partner di sviluppo per SQL Server](partner-dev-sql-server.md)
2. [Partner di disponibilità elevata e ripristino di emergenza per SQL Server](partner-hadr-sql-server.md)
3. [Partner di gestione per SQL Server](partner-management-sql-server.md)
4. [Partner di monitoraggio per SQL Server](partner-monitor-sql-server.md)
5. [Note sulla versione di SQL Server 2012 SP4](sql-server-2012-sp4-release-notes.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Note sulla versione di SQL Server 2017](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd"></a>1. &nbsp; [Note sulla versione di SQL Server 2017](sql-server-2017-release-notes.md)

*Aggiornamento: 20/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 37.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c9ac7e027e32b17bb9b54a4a878f70a70404f1cb 5b1aa8dc715fbb08d82b241f1e47f6e443b3e2fc  (PR=4032  ,  Filename=sql-server-2017-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->



- **Soluzione alternativa:** riavviare il computer e verificare se la condivisione di rete FILESTREAM è disponibile. Se la condivisione non è ancora disponibile, eseguire la procedura seguente:

    1. In Gestione configurazione SQL Server fare clic con il pulsante destro del mouse sull'istanza di SQL Server e scegliere **Proprietà**.
    2. Nella scheda **FILESTREAM** deselezionare **Abilita FILESTREAM per l'accesso tramite il flusso di I/O dei file** e quindi fare clic su **Applica**.
    3. Selezionare di nuovo **Abilita FILESTREAM per l'accesso tramite il flusso di I/O dei file** con il nome di condivisione originale e fare clic su **Applica**.

**Master Data Services (MDS)**

- **Problema e impatto sul cliente:** nella pagina delle autorizzazioni utente, quando si concede l'autorizzazione a livello radice nella visualizzazione albero entità, viene visualizzato l'errore seguente: `"The model permission cannot be saved. The object guid is not valid"`

- **Soluzioni alternative:**
  - Concedere l'autorizzazione per i nodi figlio nella visualizzazione albero anziché a livello radice.
  - o
  - Eseguire lo script descritto in questo blog del team MDS relativo all'[errore durante l'applicazione di autorizzazioni a livello di entità](http://sqlblog.com/blogs/mds_team/archive/2017/09/05/sql-server-2016-sp1-cu4-regression-error-while-applying-permission-on-entity-level-quick-workaround.aspx)

**Analysis Services**

- **Problema e impatto per i clienti:** i connettori dati per le origini seguenti non sono ancora disponibili per i modelli tabulari a livello di compatibilità 1400.
  - Amazon Redshift
  - IBM Netezza
  - Impala
- **Soluzione alternativa:** nessuna.

- **Problema e impatto sul cliente:** i modelli di query diretta al livello di compatibilità 1400 con prospettive possono avere esito negativo nell'esecuzione di query o nell'individuazione dei metadati.
- **Soluzione alternativa:** rimuovere le prospettive ed eseguire di nuovo la distribuzione.







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


