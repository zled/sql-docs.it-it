---
title: 'Articolo aggiornato: documentazione di SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione per SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 7f1c64e11e1bec44a558cec10c3d1f90f4951dfd
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>Articoli nuovi e aggiornati di recente: documentazione di SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **18/07/2017** &nbsp; - &nbsp; **11/09/2017**
- *Area di interesse:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [SQL Server 2008 R2 SP2 Release Notes](sql-server-2008-r2-sp2-release-notes.md)
2. [Note sulla versione di SQL Server 2012](sql-server-2012-release-notes.md)
3. [SQL Server 2012 SP1 Release Notes](sql-server-2012-sp1-release-notes.md)
4. [SQL Server 2012 SP2 Release Notes](sql-server-2012-sp2-release-notes.md)
5. [Note sulla versione di SQL Server 2012 SP3](sql-server-2012-sp3-release-notes.md)
6. [SQL Server 2014 Release Notes](sql-server-2014-release-notes.md)
7. [Help Viewer e contenuto offline per SQL Server](sql-server-help-installation.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Novità di SQL Server 2016](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-whats-new-in-sql-server-2016what-s-new-in-sql-server-2016md"></a>1. &nbsp;[Novità di SQL Server 2016](what-s-new-in-sql-server-2016.md)

*Aggiornamento: 08/09/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 34.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e5bc0c05f120289f09a535400a4d521e4113ae55 0607d0a9af1c9a8dd9d3d7b0606895ff23bbffdc  (PR=0  ,  Filename=what-s-new-in-sql-server-2016.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



- È possibile scaricare **gratuitamente** [**SQL Server 2016 Developer Edition**](https://www.microsoft.com/en-us/cloud-platform/sql-server-editions-developers).
- Scaricare la versione più recente di [SQL Server Management Studio (SSMS)](/sql-docs/docs/ssms/download-sql-server-management-studio-ssms).
- Se si ha un account di Azure, accedere a una [macchina virtuale con SQL Server 2016 già installato](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/).

**Motore di database di SQL Server 2016**

- È ora possibile configurare **più file di database tempDB** durante l'installazione e la configurazione di SQL Server.
- La nuova funzionalità **Query Store** consente di archiviare i testi delle query, i piani di esecuzione e le metriche delle prestazioni all'interno del database, in modo da poter monitorare e risolvere facilmente i problemi di prestazioni. In un dashboard vengono visualizzate le query che usano la quantità maggiore di tempo, di memoria o di risorse della CPU.
- Le **tabelle temporali** sono tabelle cronologiche nelle quali vengono registrate tutte le modifiche dei dati, incluse data e ora in cui si sono verificate.
- Il nuovo **supporto di JSON** incorporato in SQL Server supporta importazioni, esportazioni, l'analisi e l'archiviazione JSON.
- Il nuovo motore di query **PolyBase** consente di integrare SQL Server con dati esterni in Hadoop o nell'archivio BLOB di Azure. È possibile importare ed esportare i dati, oltre a eseguire query.
- La nuova funzionalità **Stretch Database** consente di archiviare i dati in modo dinamico e sicuro da un database di SQL Server locale a un database SQL di Azure nel cloud. SQL Server consente di eseguire automaticamente query su dati locali e remoti nei database collegati.
- **OLTP in memoria:**
    - Sono ora supportati i vincoli FOREIGN KEY, UNIQUE e CHECK e le stored procedure compilate native OR, NOT, SELECT DISTINCT, OUTER JOIN, nonché sottoquery in SELECT.
    - Sono supportate tabelle fino a 2 TB (da 256 GB).
    - Sono disponibili miglioramenti per l'indice columnstore per l'ordinamento e il supporto di gruppi di disponibilità AlwaysOn.
- Nuove funzionalità di sicurezza:
    - **Always Encrypted:** quando questa funzionalità è abilitata, solo l'applicazione con la chiave di crittografia può accedere ai dati sensibili crittografati nel database di SQL Server 2016. La chiave non viene mai passata a SQL Server.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+12): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5+0): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5+1): documentazione di **Motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19+82): documentazione di **Integration Services per SQL**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1+8): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12+1): documentazione di **Database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+1): documentazione di **Reporting Services per SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1): documentazione di **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+2): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1+4): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (4+1): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0+1): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



