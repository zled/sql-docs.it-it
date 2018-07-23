---
title: 'Articolo aggiornato: documentazione di SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione per SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: f1e3d0fd2b63ac3eb9ab0d66b14df15dad0c15ee
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926822"
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Articoli nuovi e aggiornati di recente: documentazione di SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Come contribuire alla documentazione di SQL Server](sql-server-docs-contribute.md)
2. [Supplemento alla privacy di SQL Server](sql-server-privacy.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Note sulla versione di SQL Server 2012 Service Pack](#TitleNum_1)
2. [Note sulla versione di SQL Server 2016](#TitleNum_2)
3. [Documentazione di SQL Server](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2012-service-pack-release-notessql-server-2012-sp4-release-notesmd"></a>1. &nbsp; [Note sulla versione di SQL Server 2012 Service Pack](sql-server-2012-sp4-release-notes.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 57.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ce108992ea942b4a11f30d67a1a52d7f26868caa a6269ba2cb2d3b3b54aebf5087dc4d513e476a96  (PR=5676  ,  Filename=sql-server-2012-sp4-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- **Partizionamento soft-NUMA automatico**: con SQL 2014 SP2 viene introdotto il partizionamento [Soft-NUMA](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx) automatico quando il flag di traccia 8079 è abilitato a livello del server. Quando il flag di traccia 8079 viene abilitato durante l'avvio, SQL Server 2014 SP2 interroga il layout di hardware e configura automaticamente soft-NUMA nei sistemi che segnalano 8 o più CPU per nodo NUMA. Il comportamento soft-NUMA automatico supporta l'Hyper-Threading (HT/processore logico). Il partizionamento e la creazione di nodi aggiuntivi ridimensionano l'elaborazione in background aumentando il numero di listener tramite scalabilità e le funzionalità di crittografia e di rete. È consigliabile testare le prestazioni del carico di lavoro con la configurazione soft-NUMA automatica prima di attivarlo nell'ambiente di produzione.

**Note sulla versione di Service Pack 3**


**Pagine di download**

- [SQL Server 2012 SP3 Feature Pack](http://go.microsoft.com/fwlink/?linkid=615935)
- [SQL Server 2012 SP3 Express](http://go.microsoft.com/fwlink/?linkid=692144)

Per informazioni più dettagliate per identificare il percorso e il nome del file da scaricare in base alla versione attualmente installata, vedere la sezione "Scegliere il file corretto da scaricare" in [Note sulla versione di SQL Server 2012 Service Pack 3](https://support.microsoft.com/help/3072779/sql-server-2012-service-pack-3-release-information).

**Note sulla versione di Service Pack 2**


**Pagine di download**

- [SQL Server 2012 SP2 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=401008)
- [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)

Usare la tabella seguente per identificare la posizione e il nome del file da scaricare in base alla versione attualmente installata. Le pagine per il download includono informazioni sui requisiti di sistema e istruzioni di base per l'installazione.

|Versione attualmente installata|Operazione da eseguire|File da scaricare e installare|



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-2016-release-notessql-server-2016-release-notesmd"></a>2. &nbsp; [Note sulla versione di SQL Server 2016](sql-server-2016-release-notes.md)

*Aggiornamento: 27/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1) | [Successivo](#TitleNum_3))

<!-- Source markdown line 25.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a15210866acf524dae49f3a7fd7957c9ffa6a78a 7257cb2017779242cbb8fa2b562f4b102502e942  (PR=5695  ,  Filename=sql-server-2016-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->



  Questo articolo descrive le limitazioni e i problemi relativi alle versioni di SQL Server 2016, inclusi i Service Pack. Per informazioni sulle novità, vedere [Novità di SQL Server 2016](https://docs.microsoft.com/sql/sql-server/what-s-new-in-sql-server-2016).

- Scaricare SQL Server 2016 da **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
- Macchina virtuale di Azure piccola: se si ha un account Azure,  fare clic **[qui](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** per creare rapidamente una macchina virtuale in cui è già installato SQL Server 2016 SP1.
- Download di SSMS: per ottenere la versione più recente di SQL Server Management Studio, vedere **[Scaricare SQL Server Management Studio (SSMS)]**.

**<a name="bkmk_2016sp2"></a>SQL Server 2016 Service Pack 2 (SP2)**


SQL Server 2016 SP2 include tutti gli aggiornamenti cumulativi rilasciati dopo la versione 2016 SP1, fino a CU8 compreso.

- [Microsoft SQL Server 2016 Service Pack 2 (SP2)](https://go.microsoft.com/fwlink/?linkid=869608)
- Per un elenco completo degli aggiornamenti, vedere [Informazioni sulla versione Service Pack 2 di SQL Server 2016](https://support.microsoft.com/help/4052908/sql-server-2016-service-pack-2-release-information)



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-documentationsql-server-technical-documentationmd"></a>3. &nbsp; [Documentazione di SQL Server](sql-server-technical-documentation.md)

*Aggiornamento: 27/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2))

<!-- Source markdown line 77.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0262010ba39785a6d46b42f8469fb17701f13008 c69a83236391d039381a93c65ebbb2efa53e11b8  (PR=5695  ,  Filename=sql-server-technical-documentation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->




<!-- : : : m-r -->
**Provare SQL Server**
- Download da Evaluation Center: [scaricare SQL Server per Windows](http://go.microsoft.com/fwlink/?LinkID=829477)
- Download da Evaluation Center: scaricare SQL Server Management Studio (SSMS)
- Download da Evaluation Center: scaricare SQL Server Data Tools (SSDT)
- Creare una macchina virtuale: [ottenere una macchina virtuale con SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)





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

